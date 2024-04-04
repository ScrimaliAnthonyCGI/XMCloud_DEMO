# escape=`

#
# Basic Windows node.js image for use as a parent image in the solution.
#

ARG PARENT_IMAGE
FROM $PARENT_IMAGE

ARG NODEJS_VERSION=16.15.1

USER ContainerAdministrator
WORKDIR /build
RUN cmd.exe curl.exe -sS -L -o node.zip https://nodejs.org/dist/v%NODEJS_VERSION%/node-v%NODEJS_VERSION%-win-x64.zip


RUN cmd.exe tar.exe -xf node.zip -C C:\

RUN cmd.exe move /build/node-v%NODEJS_VERSION%-win-x64 /build/node
RUN cmd.exe del node.zip

RUN SETX /M PATH "%PATH%;C:\node\"
RUN cmd.exe icacls.exe C:\node\ /grant "Authenticated Users":(F) /t
USER ContainerUser