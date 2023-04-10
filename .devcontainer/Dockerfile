FROM gcr.io/kaggle-gpu-images/python:latest

ARG UID
ARG GID

ENV UID=${UID:-1000}
ENV GID=${GID:-1000}

RUN pip install --upgrade pip

RUN pip install mlflow \
    boto3 \
    flake8 \
    pep8-naming \
    black \
    isort

# install fish shell
RUN apt-add-repository ppa:fish-shell/release-3 -y && \
    apt-get update && \
    apt-get install -y fish

# change uid and gid of user jupyter
RUN groupmod -g ${GID} jupyter && \
    usermod -u ${UID} -g ${GID} jupyter

# add user to sudoers
RUN echo "jupyter ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

USER jupyter

# install oh-my-fish
RUN curl -L https://get.oh-my.fish > /tmp/install && \
    fish /tmp/install --noninteractive --path=~/.local/share/omf --config=~/.config/omf && \
    rm /tmp/install

# install agnoster theme
RUN fish -c "omf install agnoster" && \
    fish -c "omf theme agnoster"

# change default shell to fish
SHELL ["/usr/bin/fish", "-c"]
