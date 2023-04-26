FROM ubuntu
MAINTAINER tets
ENV DOTNET_VERSION=7.0.0
ENV DOTNET_ROOT=$HOME/.dotnet
ENV PATH=$PATH:$HOME/.dotnet
ENV PATH=$PATH:$HOME/.dotnet/tools
RUN apt update -y
RUN apt upgrade -y
RUN apt install wget -y
RUN wget https://dot.net/v1/dotnet-install.sh -O dotnet-install.sh
RUN chmod +x ./dotnet-install.sh
RUN ./dotnet-install.sh --version latest
RUN ./dotnet-install.sh --version latest --runtime aspnetcore
RUN ./dotnet-install.sh --channel 7.0
ENV DOTNET_VERSION=7.0.0
ENV DOTNET_ROOT=$HOME/.dotnet
#ENV PATH=$PATH:$HOME/.dotnet:$HOME/.dotnet/tools
ENV PATH=$PATH:$HOME/.dotnet
ENV PATH=$PATH:$HOME/.dotnet/tools
RUN DOTNET_SYSTEM_GLOBALIZATION_INVARIANT=1
RUN dotnet restore --use-current-runtime
COPY aspnetapp/. .
RUN dotnet restore --use-current-runtime
RUN dotnet publish -c Release -o published
RUN dotnet published/aspnetapp.dll --urls http://0.0.0.0:5000
RUN apt install curl -y

