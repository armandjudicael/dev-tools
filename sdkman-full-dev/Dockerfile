FROM ubuntu:22.04

# Environment setup
ENV DEBIAN_FRONTEND=noninteractive
ENV SDKMAN_DIR=/root/.sdkman
ENV JAVA_VERSIONS="8.0.392-tem 11.0.21-tem 17.0.9-tem 21.0.1-tem 25.ea.4-open"
ENV TOOLS="maven gradle kotlin scala"

# Install dependencies
RUN apt update && apt install -y curl unzip zip bash

# Install SDKMAN
RUN curl -s "https://get.sdkman.io" | bash

# Install Java versions
RUN bash -c "source $SDKMAN_DIR/bin/sdkman-init.sh && \
    for version in $JAVA_VERSIONS; do sdk install java \$version; done && \
    sdk default java 17.0.9-tem"

# Install Dev Tools (Maven, Gradle, Kotlin, Scala)
RUN bash -c "source $SDKMAN_DIR/bin/sdkman-init.sh && \
    for tool in $TOOLS; do sdk install \$tool; done"

# Load SDKMAN automatically in each shell
RUN echo 'source "$SDKMAN_DIR/bin/sdkman-init.sh"' >> /root/.bashrc

# Default command
CMD ["bash"]
