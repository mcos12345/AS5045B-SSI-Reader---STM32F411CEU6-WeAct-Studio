# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Planned
- USB CDC interface for configuration
- CAN bus support
- Multi-encoder support
- Qt GUI for calibration and monitoring

## [1.0.0] - 2024-01-30

### Added
- Initial release
- AS5045B SSI driver with differential interface
- MAX3485 transceiver support
- FreeRTOS integration with 1 kHz sampling
- Adaptive IIR filtering with FPU
- Thread-safe architecture with mutex protection
- Advanced diagnostics and statistics
- Retry logic and error handling
- Auto-calibration of timings
- Comprehensive documentation
- Unit and integration tests
- PlatformIO and Makefile support
- Example projects

### Features
- SSI reading up to 1 MHz
- Position accuracy: 12-bit (0.088°)
- Read time: < 20 µs
- Jitter: < 1 µs @ 1 kHz
- Error rate: < 0.01%

### Documentation
- Hardware setup guide
- Software architecture document
- API reference
- Timing analysis
- Troubleshooting guide

## [0.1.0] - 2024-01-15

### Added
- Basic SSI driver prototype
- GPIO bit-banging implementation
- Simple position reading

---

[Unreleased]: https://github.com/yourusername/as5045b-ssi-stm32f411/compare/v1.0.0...HEAD
[1.0.0]: https://github.com/yourusername/as5045b-ssi-stm32f411/releases/tag/v1.0.0
[0.1.0]: https://github.com/yourusername/as5045b-ssi-stm32f411/releases/tag/v0.1.0
