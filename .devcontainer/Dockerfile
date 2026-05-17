FROM debian:bookworm-slim

COPY install.sh /app/install.sh

WORKDIR /app

RUN apt-get update && apt-get install -y --no-install-recommends \
    bash git curl wget unzip tzdata openssl ca-certificates iproute2 \
    && rm -rf /var/lib/apt/lists/*

# Enable BBR congestion control for lower latency gaming
RUN echo 'net.core.default_qdisc=fq' >> /etc/sysctl.d/99-bbr.conf && \
    echo 'net.ipv4.tcp_congestion_control=bbr' >> /etc/sysctl.d/99-bbr.conf && \
    echo 'net.ipv4.tcp_fastopen=3' >> /etc/sysctl.d/99-bbr.conf && \
    echo 'net.ipv4.tcp_low_latency=1' >> /etc/sysctl.d/99-bbr.conf && \
    echo 'net.ipv4.tcp_nodelay=1' >> /etc/sysctl.d/99-bbr.conf && \
    echo 'net.core.rmem_max=26214400' >> /etc/sysctl.d/99-bbr.conf && \
    echo 'net.core.wmem_max=26214400' >> /etc/sysctl.d/99-bbr.conf && \
    echo 'net.ipv4.tcp_rmem=4096 87380 26214400' >> /etc/sysctl.d/99-bbr.conf && \
    echo 'net.ipv4.tcp_wmem=4096 65536 26214400' >> /etc/sysctl.d/99-bbr.conf

RUN chmod +x /app/install.sh && /app/install.sh
COPY config.json /etc/config.json

# Print all VLESS links on shell attach
RUN cat >> /etc/bash.bashrc << 'EOF'

echo ""
echo "╔══════════════════════════════════════════════════════╗"
echo "║           🎮 GHTUN - GAMING OPTIMIZED               ║"
echo "║        BBR • TCP Fast Open • Low Latency             ║"
echo "╚══════════════════════════════════════════════════════╝"
echo ""
echo "📡 VLESS LINKS (copy to your client):"
echo ""
BASE="vless://550e8400-e29b-41d4-a716-446655440000"
SNI="${CODESPACE_NAME}-443.app.github.dev"
PARAMS="?encryption=none&security=tls&type=xhttp&mode=packet-up&path=%2F"

echo "1)  ${BASE}@63.141.252.203:443${PARAMS}&sni=${SNI}#ghtun-US1"
echo "2)  ${BASE}@142.54.178.211:443${PARAMS}&sni=${SNI}#ghtun-US2"
echo "3)  ${BASE}@204.12.196.34:443${PARAMS}&sni=${SNI}#ghtun-US3"
echo "4)  ${BASE}@50.7.87.2:443${PARAMS}&sni=${SNI}#ghtun-US4"
echo "5)  ${BASE}@50.7.87.5:443${PARAMS}&sni=${SNI}#ghtun-US5"
echo "6)  ${BASE}@50.7.87.4:443${PARAMS}&sni=${SNI}#ghtun-US6"
echo "7)  ${BASE}@50.7.87.3:443${PARAMS}&sni=${SNI}#ghtun-US7"
echo "8)  ${BASE}@138.201.54.122:443${PARAMS}&sni=${SNI}#ghtun-DE1"
echo "9)  ${BASE}@94.130.50.12:443${PARAMS}&sni=${SNI}#ghtun-DE2"
echo "10) ${BASE}@94.130.13.19:443${PARAMS}&sni=${SNI}#ghtun-DE3"
echo "11) ${BASE}@85.10.207.48:443${PARAMS}&sni=${SNI}#ghtun-DE4"
echo ""
EOF

CMD ["/usr/local/bin/xray", "-c", "/etc/config.json"]
