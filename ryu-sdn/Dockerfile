FROM ubuntu:noble

RUN apt update
# install mininet
RUN apt install mininet openvswitch-switch -y
RUN apt install iproute2 -y
RUN apt install iputils-ping -y
# install python3.9
RUN apt install software-properties-common -y
RUN add-apt-repository ppa:deadsnakes/ppa -y
RUN apt update
RUN apt install python3.9 -y
RUN apt install python3.9-distutils -y
RUN apt install python3-pip -y
# install RYU
RUN python3.9 -m pip uninstall setuptools -y
RUN python3.9 -m pip install setuptools==59.5.0 --root-user-action=ignore
RUN python3.9 -m pip install cffi --root-user-action=ignore
RUN python3.9 -m pip install eventlet==0.30.0 --root-user-action=ignore
RUN python3.9 -m pip install ryu --root-user-action=ignore