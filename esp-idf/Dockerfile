# Container used for Espressif IoT Development Framework, mainly flashing and compiling project
# TODO:
#   - fix path of compile_commands.json for lsp completions or run clangd inside container

from debian:bullseye-slim

ARG USERID
ARG GROUPID

RUN groupadd -g GROUPID dev && useradd -u USERID -g GROUPID -m dev

RUN apt update && apt install git wget flex bison gperf python3 \
      python3-pip python3-venv cmake ninja-build ccache \
      libffi-dev libssl-dev dfu-util libusb-1.0-0 -y
