## stage-1
FROM ubuntu:22.04 as nopCommerce
RUN apt update && apt install unzip -y
ARG DOWNLOAD_URL=https://github.com/nopSolutions/nopCommerce/releases/download/release-4.60.2/nopCommerce_4.60.2_NoSource_linux_x64.zip
ADD ${DOWNLOAD_URL} /nopCommerce/nopCommerce_4.60.2_NoSource_linux_x64.zip
RUN cd /nopCommerce && unzip nopCommerce_4.60.2_NoSource_linux_x64.zip && \
mkdir bin logs && rm nopCommerce_4.60.2_NoSource_linux_x64.zip

## stage-2
FROM mcr.microsoft.com/dotnet/sdk:7.0
LABEL author="manu" organization="khaja.tech" project="nop"
ARG DIRECTORY=/nop
WORKDIR ${DIRECTORY}
COPY --from=nopCommerce  /nopCommerce ${DIRECTORY}
EXPOSE 5000
ENV ASNETCORE_URLS="http://0.0.0.0:5000"
CMD ["dotnet","Nop.Web.dll","--urls","http://0.0.0.0:5000"]



## reference
FROM mcr.microsoft.com/dotnet/sdk:7.0
LABEL author="manu" organization="khaja.tech" project="nop"
ADD https://github.com/nopSolutions/nopCommerce/releases/download/release-4.60.2/nopCommerce_4.60.2_NoSource_linux_x64.zip /nop/nopCommerce_4.60.2_NoSource_linux_x64.zip
WORKDIR /nop
RUN apt update && apt install unzip -y && \
    unzip /nop/nopCommerce_4.60.2_NoSource_linux_x64.zip && \
    mkdir /nop/bin && mkdir /nop/logs
EXPOSE 5000
CMD [ "dotnet", "Nop.Web.dll","--urls", "http://0.0.0.0:5000" ]




## dotnet build 
#stage1
FROM mcr.microsoft.com/dotnet/sdk:7.0 as build
LABEL author="manu" organization="khaja.tech" project="nop"
RUN git clone https://github.com/nopSolutions/nopCommerce.git
RUN cd /nopCommerce && dotnet build ./src/NopCommerce.sln 
RUN cd /nopCommerce && dotnet publish ./src/Presentation/Nop.Web/Nop.Web.csproj -c Release -o /nop

# stage2
FROM mcr.microsoft.com/dotnet/sdk:7.0 as runnner
LABEL author="manu" organization="khaja.tech" project="nop"
ARG user=manu
ARG group=manu
ARG gid=1000
ARG uid=1000
ARG HOME_DIR=/nop
RUN groupadd -g ${gid} ${group} && \
    useradd -d "$HOME_DIR" -u ${uid} -g ${gid} -m -s /bin/bash ${user}
USER ${user}
WORKDIR "/nop"
COPY --from=build --chown=${user}:${group} /nop ${HOME_DIR}
RUN mkdir bin logs
EXPOSE 5000
ENV ASPNETCORE_URLS="http://0.0.0.0:5000"
CMD [ "dotnet", "Nop.Web.dll" ]