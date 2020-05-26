
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
    && sudo sudo apt-get update \
    && sudo apt-get install -y default-jre \
    && mkdir -p /home/vscode/share/java \
    && wget  https://repo1.maven.org/maven2/org/openapitools/openapi-generator-cli/4.3.1/openapi-generator-cli-4.3.1.jar -O /home/vscode/share/java/openapi-generator-cli.jar \
    && git clone https://github.com/go-task/task 
    
# Update this to "on" or "off" as appropriate
ENV GO111MODULE=on

# Switch back to dialog for any ad-hoc use of apt-get
#ENV DEBIAN_FRONTEND=dialog