# Use the Zephyr Build Docker image as the base
FROM zephyrprojectrtos/zephyr-build:v0.26.15

# Set environment variables
ENV ZEPHYR_TOOLCHAIN_VARIANT=zephyr
ENV ZEPHYR_SDK_INSTALL_DIR=/opt/zephyr-sdk
# Initialize west and update the modules in /west
WORKDIR /west
RUN west init && west update && cd /west/tools/net-tools && make

ENV ZEPHYR_BASE=/west/zephyr