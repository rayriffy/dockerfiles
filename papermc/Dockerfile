FROM alpine:3.21 AS base

ARG MC_VERSION

WORKDIR /app

# Install dependencies
RUN apk add --no-cache curl jq openjdk21-jre

# Download latest jar
RUN LATEST_BUILD=$(curl -s https://api.papermc.io/v2/projects/paper/versions/${MC_VERSION}/builds | \
    jq -r '.builds | map(select(.channel == "default") | .build) | .[-1]') && \
    JAR_NAME=paper-${MC_VERSION}-${LATEST_BUILD}.jar && \
    PAPERMC_URL="https://api.papermc.io/v2/projects/paper/versions/${MC_VERSION}/builds/${LATEST_BUILD}/downloads/${JAR_NAME}" && \
    curl -o server.jar $PAPERMC_URL

# Auto-accept EULA
RUN echo "eula=true" > eula.txt

# Run PaperMC
CMD ["java", "-jar", "server.jar", "nogui"]
