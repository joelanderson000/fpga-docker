FROM fpga-base:debian as install
LABEL com.halfmanhalftaco.fpga.temp=1
ADD Quartus-web-13.0.1.232-linux.tar /quartus
RUN mkdir -p /opt/quartus && /quartus/setup.sh --mode unattended --installdir /opt/quartus

FROM fpga-base:debian
COPY --from=install /opt/quartus /opt/quartus
CMD ["/opt/quartus/quartus/bin/quartus"]
ARG TOOL
LABEL com.halfmanhalftaco.fpga.tool=$TOOL