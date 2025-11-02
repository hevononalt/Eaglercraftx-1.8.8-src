FROM mcr.microsoft.com/devcontainers/base:ubuntu

# Install basic desktop + VNC + noVNC
RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y \
    xfce4 xfce4-goodies x11vnc novnc websockify \
    wget supervisor && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# Create a VNC passwordless user session
RUN mkdir -p /root/.vnc && \
    x11vnc -storepasswd 1234 /root/.vnc/passwd

# Setup Supervisor to run desktop + VNC + noVNC
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf

EXPOSE 6080
CMD ["/usr/bin/supervisord"]
