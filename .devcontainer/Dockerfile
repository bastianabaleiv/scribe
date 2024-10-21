FROM nvidia/cuda:12.2.0-base-ubuntu22.04

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

RUN apt-get update && apt-get install -y --no-install-recommends \
        python3-pip \
        python3-dev \
        python3-venv \
        ffmpeg \
        htop \
        nano \
        openssh-client \
        git && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN pip install --no-cache-dir virtualenv

ENV VIRTUAL_ENV=/opt/venv
RUN python3 -m venv $VIRTUAL_ENV
ENV PATH="$VIRTUAL_ENV/bin:$PATH"
    
WORKDIR /usr/workspace

COPY requirements.txt /usr/workspace/requirements.txt
RUN pip3 install -r /usr/workspace/requirements.txt

CMD ["jupyter", "lab", "--ip=0.0.0.0", "--no-browser", "--allow-root"]