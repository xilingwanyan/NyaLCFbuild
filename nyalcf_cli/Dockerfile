# nyalcf_cli/Dockerfile
ARG DART_VERSION=stable
FROM dart:${DART_VERSION} as builder

WORKDIR /app

COPY pubspec.* ./
RUN dart pub get

COPY . .

RUN dart compile exe bin/nyalcf_cli.dart -o nyalcf_cli-linux-arm64

FROM scratch
COPY --from=builder /app/nyalcf_cli-linux-arm64 /