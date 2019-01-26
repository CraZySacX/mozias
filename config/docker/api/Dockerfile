FROM ekidd/rust-musl-builder:nightly AS builder
ADD . ./
RUN sudo chown -R rust:rust /home/rust
RUN cargo build --release

FROM alpine:latest
RUN mkdir -p /opt/mozias-api/bin
RUN mkdir -p /root/.config/mozias-api
RUN apk add --no-cache ca-certificates
COPY --from=builder \
    /home/rust/src/target/x86_64-unknown-linux-musl/release/mozias-api \
    /opt/mozias-api/bin/
COPY --from=builder \
    /home/rust/src/Rocket.toml \
    /
EXPOSE 8000
CMD ["/opt/mozias-api/bin/mozias-api"]