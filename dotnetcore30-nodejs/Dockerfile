FROM mcr.microsoft.com/dotnet/core/sdk:3.0 as base
SHELL ["/bin/bash", "-o", "pipefail", "-c"]
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
    curl=* \
    unzip=* \
    && rm -rf /var/lib/apt/lists/*
RUN curl -sL https://deb.nodesource.com/setup_13.x | bash - \
    && apt-get update && apt-get install -y --no-install-recommends \
    nodejs=* \
    && rm -rf /var/lib/apt/lists/*