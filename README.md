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

### GPIO Mappings between SPI and QSPI

Based on the structure of `spi_bus_config_t` found in
[spi_common.h](https://github.com/espressif/esp-idf/blob/master/components/esp_driver_spi/include/driver/spi_common.h):

- `mosi_io_num` is `data0_io_num`
- `miso_io_num` is `data1_io_num`
- `quadwp_io_num` is `data2_io_num`
- `quadhd_io_num` is `data3_io_num`

### QSPI GPIOs for MCUs

| Signal | ESP32-S3 (SPI2) | ESP32-C6 (SPI2) |
| :----- | :-------------: | :-------------: |
| CS     |              10 |              10 |
| CLK    |              12 |               6 |
| DAT0   |              11 |               7 |
| DAT1   |              13 |               2 |
| DAT2   |              14 |               5 |
| DAT3   |               9 |               4 |

## References

- [ESP SPI Slave HD (Half Duplex) Mode
  Protocol](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/api-reference/protocols/esp_spi_slave_protocol.html)
- [ESP-IDF Issue
  (Closed)](https://github.com/espressif/esp-idf/issues/9823) about
  using the example in QSPI mode
- [ESP-IDF Issue (Closed)](https://github.com/espressif/esp-idf/issues/12187) about using QPI mode
- [SPI Slave Half Duplex](https://docs.espressif.com/projects/esp-idf/en/latest/esp32c6/api-reference/peripherals/spi_slave_hd.html) documentation and API
