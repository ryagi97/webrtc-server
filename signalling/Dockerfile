FROM rust:1.84

# install dependencies
RUN cargo install cargo-c

# Add sources
WORKDIR /usr/src/
ADD https://gitlab.freedesktop.org/gstreamer/gst-plugins-rs.git#0.9 . 

# Build signalling server
WORKDIR /usr/src/gst-plugins-rs/net/webrtc/signalling
RUN cargo build --bin gst-webrtc-signalling-server --release

# Run server
ENV WEBRTCSINK_SIGNALLING_SERVER_LOG=debug
CMD cargo run --bin gst-webrtc-signalling-server --release