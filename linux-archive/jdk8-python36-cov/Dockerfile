FROM ukhydrographicoffice/aardvarkcov:2019.12 as coverity

FROM adoptopenjdk:8-jdk-hotspot
SHELL ["/bin/bash", "-o", "pipefail", "-c"]
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash - \
    && curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add - \
    && echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list \
    && apt-get update && apt-get install -y --no-install-recommends \
    git=* \
    nodejs=* \
    openssh-client=* \
    pbzip2=* \
    python3-pip=* \
    python3.6=* \
    unzip=* \
    wget=* \
    yarn=* \
    build-essential=* \
    python3.6-dev=* \
  && rm -rf /var/lib/apt/lists/* \
  && pip3 install --no-cache-dir setuptools==41.6.0 wheel==0.33.6 \
  && pip3 install --no-cache-dir awscli==1.16.277 \
  && curl -L -O https://amazon-ecr-credential-helper-releases.s3.us-east-2.amazonaws.com/0.4.0/linux-amd64/docker-credential-ecr-login \
  && chmod +x ./docker-credential-ecr-login \
  && mv ./docker-credential-ecr-login /usr/local/bin/
COPY --from=coverity /usr/local/bin/cov-analysis-linux64-2019.12 /usr/local/bin/cov-analysis-linux64-2019.12
ENV COVERITY_TOOL_HOME=/usr/local/bin/cov-analysis-linux64-2019.12
ENV PATH=${PATH}:${COVERITY_TOOL_HOME}/bin
