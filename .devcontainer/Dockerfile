FROM debian:bookworm-slim

COPY install.sh /app/install.sh

WORKDIR /app

RUN apt-get update && apt-get install -y --no-install-recommends \
    bash git curl wget unzip tzdata openssl ca-certificates \
    && rm -rf /var/lib/apt/lists/*

RUN chmod +x /app/install.sh && /app/install.sh
COPY config.json /etc/config.json

RUN echo 'echo ""' >> /etc/bash.bashrc
RUN echo 'echo "╔══════════════════════════════════════════════╗"' >> /etc/bash.bashrc
RUN echo 'echo "║      🎮 GHTUN - GAMING OPTIMIZED            ║"' >> /etc/bash.bashrc
RUN echo 'echo "╚══════════════════════════════════════════════╝"' >> /etc/bash.bashrc
RUN echo 'echo ""' >> /etc/bash.bashrc
RUN echo 'SNI="${CODESPACE_NAME}-443.app.github.dev"' >> /etc/bash.bashrc
RUN echo 'BASE="vless://550e8400-e29b-41d4-a716-446655440000"' >> /etc/bash.bashrc
RUN echo 'P="?encryption=none&security=tls&type=xhttp&mode=packet-up&path=%2F"' >> /etc/bash.bashrc
RUN echo 'echo " 1) ${BASE}@63.141.252.203:443${P}&sni=${SNI}#ghtun-US1"' >> /etc/bash.bashrc
RUN echo 'echo " 2) ${BASE}@142.54.178.211:443${P}&sni=${SNI}#ghtun-US2"' >> /etc/bash.bashrc
RUN echo 'echo " 3) ${BASE}@204.12.196.34:443${P}&sni=${SNI}#ghtun-US3"' >> /etc/bash.bashrc
RUN echo 'echo " 4) ${BASE}@50.7.87.2:443${P}&sni=${SNI}#ghtun-US4"' >> /etc/bash.bashrc
RUN echo 'echo " 5) ${BASE}@50.7.87.5:443${P}&sni=${SNI}#ghtun-US5"' >> /etc/bash.bashrc
RUN echo 'echo " 6) ${BASE}@50.7.87.4:443${P}&sni=${SNI}#ghtun-US6"' >> /etc/bash.bashrc
RUN echo 'echo " 7) ${BASE}@50.7.87.3:443${P}&sni=${SNI}#ghtun-US7"' >> /etc/bash.bashrc
RUN echo 'echo " 8) ${BASE}@138.201.54.122:443${P}&sni=${SNI}#ghtun-DE1"' >> /etc/bash.bashrc
RUN echo 'echo " 9) ${BASE}@94.130.50.12:443${P}&sni=${SNI}#ghtun-DE2"' >> /etc/bash.bashrc
RUN echo 'echo "10) ${BASE}@94.130.13.19:443${P}&sni=${SNI}#ghtun-DE3"' >> /etc/bash.bashrc
RUN echo 'echo "11) ${BASE}@85.10.207.48:443${P}&sni=${SNI}#ghtun-DE4"' >> /etc/bash.bashrc
RUN echo 'echo ""' >> /etc/bash.bashrc

CMD ["/usr/local/bin/xray", "-c", "/etc/config.json"]
