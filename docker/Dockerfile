FROM node:14-alpine

ARG version=latest

RUN npm install -g @mockoon/cli@$version
COPY runner.sh mockoon-runner.sh

# Do not run as root.
RUN adduser --shell /bin/sh --disabled-password --gecos "" mockoon
RUN chown -R mockoon mockoon-runner.sh
USER mockoon

ENTRYPOINT ["sh", "mockoon-runner.sh"]
# Usage: docker run --mount type=bind,source="$(pwd)"/dataFile.json,target=/data,readonly -p <port>:<port> mockoon-test -d data -n <env_name>