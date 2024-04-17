# SPI Half-Duplex Example

This is an example of using SPI on ESP32 in half-duplex mode to
transfer data between an ESP32-S3 (master) and ESP32-C6 (slave). It is
based on the ESP-IDF [SPI Half-Duplex
Example](https://github.com/espressif/esp-idf/tree/master/examples/peripherals/spi_slave_hd).

This is intended to be a reference for implementing transfers using
QSPI.

## GPIO Configuration

### For SPI

For SPI, the following values should be set in `spi_bus_config_t`:
- `sclk_io_num` (SCLK)
- `mosi_io_num` (MOSI)
- `miso_io_num` (MISO)

### For QSPI

For QSPI, the following values should be set in `spi_bus_config_t`:
- `sclk_io_num` (SCLK)
- `data0_io_num` (DAT0)
- `data1_io_num` (DAT1)
- `data2_io_num` (DAT2)
- `data3_io_num` (DAT3)

## References

- [ESP SPI Slave HD (Half Duplex) Mode
  Protocol](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/api-reference/protocols/esp_spi_slave_protocol.html)
- [ESP-IDF Issue
  (Closed)](https://github.com/espressif/esp-idf/issues/9823) about
  using the example in QSPI mode
- [ESP-IDF SPI Slave Driver
  Documentation](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/api-reference/peripherals/spi_slave.html)
