FROM python:3.9-alpine

RUN pip install eventlet==0.30.0
RUN pip install ryu

ENTRYPOINT [ "ryu-manager" ]
