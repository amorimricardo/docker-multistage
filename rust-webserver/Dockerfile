ARG RUST_VERSION=1.80.1
ARG APP_NAME=webserver

FROM rust:${RUST_VERSION}-alpine AS build
ARG APP_NAME
WORKDIR /app

# Copy the source code into the container.
COPY . .

# Build the application.
RUN cargo build --release --bin ${APP_NAME}

#give permission to run the binary
RUN chmod +x /app/target/release/${APP_NAME}



FROM alpine:3.18 AS final
ARG APP_NAME
EXPOSE 7878

# Copy the executable from the "build" stage.
COPY --from=build /app/target/release/${APP_NAME} /bin/server

# What the container should run when it is started.
CMD ["/bin/server"]