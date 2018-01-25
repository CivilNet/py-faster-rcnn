FROM nvidia/cuda:8.0-cudnn6-runtime-ubuntu16.04
LABEL maintainer "Gemfield <gemfield@civilnet.cn>"

RUN mv /etc/apt/sources.list.d/cuda.list /etc/apt/sources.list.d/cuda.list.gemfield && \
        apt-get update && apt-get install -y --no-install-recommends \
        python3-pip \
        python3-setuptools \
        python3-tk \
        vim \
        python3-yaml && \
    rm -rf /var/lib/apt/lists/*

RUN ln -s /usr/bin/python3 /usr/bin/python

RUN pip3 install numpy scikit-image protobuf easydict && rm -rf /root/.cache

ENV GEMFIELD=/opt/gemfield
ENV FRCN_ROOT=${GEMFIELD}/py-faster-rcnn/lib
ENV PYCAFFE_ROOT=${GEMFIELD}/py-faster-rcnn/caffe-fast-rcnn/python

COPY files/gemfield ${GEMFIELD}
WORKDIR ${GEMFIELD}/py-faster-rcnn

ENV PYTHONPATH $PYTHONPATH:${FRCN_ROOT}/rpn:${FRCN_ROOT}/datasets:${FRCN_ROOT}/pycocotools:${GEMFIELD}/cv2/lib/python3.5/dist-packages:${PYCAFFE_ROOT}
ENV LD_LIBRARY_PATH $LD_LIBRARY_PATH:${GEMFIELD}/gemfield:${GEMFIELD}/cv2/lib/
