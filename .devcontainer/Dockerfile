
FROM marcocipri/vscode-remote-dev-go:1.0.0

# Avoid warnings by switching to noninteractive
ENV DEBIAN_FRONTEND=noninteractive

# This Dockerfile adds a non-root user with sudo access. Use the "remoteUser"
# property in devcontainer.json to use it. On Linux, the container user's GID/UIDs
# will be updated to match your local UID/GID (when using the dockerFile property).
# See https://aka.ms/vscode-remote/containers/non-root-user for details.
ARG USERNAME=vscode

USER $USERNAME

# Install gocode-gomod
RUN export CHSH=no \
    && sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)" \
    && sed -i 's/robbyrussell/agnoster/g' /home/vscode/.zshrc \
    && sed -i 's/(git)/(git go golang)/g' /home/vscode/.zshrc

# Update this to "on" or "off" as appropriate
ENV GO111MODULE=auto

# Switch back to dialog for any ad-hoc use of apt-get
ENV DEBIAN_FRONTEND=dialog