FROM rust:1.67.1 as build
COPY . /hello_cargo
WORKDIR /hello_cargo

RUN --mount=type=cache,target=/usr/local/cargo/registry --mount=type=cache,target=/root/target cargo build --release

FROM debian:buster-slim as runtime
COPY --from=build /hello_cargo/target/release/hello_cargo .
CMD ["./hello_cargo"]
