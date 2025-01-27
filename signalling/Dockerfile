FROM rust:1.84 AS builder

# install dependencies
RUN cargo install cargo-c

# Add sources
WORKDIR /usr/src/
ADD https://gitlab.freedesktop.org/gstreamer/gst-plugins-rs.git#0.9 . 

# Build signalling server in a build directory
WORKDIR /usr/src/gst-plugins-rs/net/webrtc/signalling
RUN cargo build --bin gst-webrtc-signalling-server --target-dir build/ --release

# Copy build target to production image
FROM gcr.io/distroless/cc
COPY --from=builder /usr/src/gst-plugins-rs/net/webrtc/signalling/build/release/gst-webrtc-signalling-server  /
CMD ["./gst-webrtc-signalling-server"]
