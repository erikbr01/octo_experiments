FROM tensorflow/tensorflow:2.15.0-gpu

# user setup
ARG USERNAME=user-name-goes-here
ARG USER_UID=1000
ARG USER_GID=$USER_UID

# Install additional dependencies
RUN apt-get update && apt-get install -y \
    git \
    vim \
    wget \
    unzip

WORKDIR /workspace/octo

RUN pip install -e .
RUN pip install -r requirements.txt

WORKDIR /workspace

# Create the user - this is necessary such that created files on the host machine are not owned by root but by the user
# which allows for easier access to the files on the host machine.
RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    #
    # [Optional] Add sudo support. Omit if you don't need to install software after connecting.
    && apt-get update \
    && apt-get install -y sudo \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

# ********************************************************
# * Anything else you want to do like clean up goes here *
# ********************************************************

# Set the default user. Omit if you want to keep the default as root.
USER $USERNAME
