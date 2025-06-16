# Exo for Jetson with Torch

This repository contains modified versions of [exo-pytorch](https://github.com/exo-explore/exo) and [xotorch](https://github.com/exo-explore/xotorch) that have been adapted to work on NVIDIA Jetson devices.

## Supported Jetson Models

The following Jetson models are specifically supported:

- Jetson AGX Orin 32GB
- Jetson Orin Nano
- Jetson Orin NX

## Repository Contents

- **Exo-pytorch**: A modified version of the Exo framework that works on Jetson devices
- **xotorch**: A modified version of xotorch that works on Jetson devices

## Modifications for Jetson Support

### Exo-pytorch Modifications

The original Exo framework has been modified to properly detect and utilize Jetson hardware:

- Added detection for multiple Jetson models in `device_capabilities.py`:
  - Jetson AGX Orin 32GB
  - Jetson Orin Nano
  - Jetson Orin NX
- Added appropriate FLOPS values for each Jetson model
- Implemented optimized memory information handling for Jetson devices

### xotorch Modifications

Similar modifications have been made to xotorch:

- Added detection for multiple Jetson models
- Added appropriate FLOPS values for each Jetson model
- Implemented optimized memory information handling
- Added caching mechanisms to improve performance
- Added fallback mechanisms to ensure proper TFLOPS display

## Installation

### Prerequisites

- NVIDIA Jetson device (tested on Jetson AGX Orin 32GB, Jetson Orin Nano, and Jetson Orin NX)
- Python 3.9+
- CUDA toolkit

### Installing Exo-pytorch

```bash
cd Exo-pytorch/exo-pt
python -m venv .venv
source .venv/bin/activate
pip install -e .
```

### Installing xotorch

```bash
cd xotorch-main
python -m venv .venv
source .venv/bin/activate
pip install -e .
```

## Usage

### Running Exo-pytorch

```bash
cd Exo-pytorch/exo-pt
source .venv/bin/activate
exo
```

### Running xotorch

```bash
cd xotorch-main
source .venv/bin/activate
xot
```

## Troubleshooting

### Debug Logs

Both frameworks have been configured to write debug information to a log file:

```bash
cat ~/xotorch_debug.log
```

This log file contains detailed information about device detection, FLOPS values, and other relevant data that can help diagnose issues.

### Common Issues

#### TFLOPS Not Displaying Correctly

If TFLOPS values are not displaying correctly:

1. Check the debug log file for device detection information
2. Verify that the Jetson device is being correctly identified
3. Ensure that the FLOPS values are being correctly retrieved from the CHIP_FLOPS dictionary

#### Performance Issues

If you experience performance issues:

1. Make sure you're using the latest version of the code
2. Check the debug log file for any warnings or errors
3. Try setting the `DEBUG` environment variable to 0 to disable debug logging
4. If using a specific Jetson model (Nano, NX, etc.), ensure it's being correctly identified in the logs

#### Module Not Found Errors

If you encounter "Module not found" errors:

1. Make sure you've activated the correct virtual environment
2. Try reinstalling the package with `pip install -e .`
3. Check that all dependencies are installed

## Contributing

Contributions to improve Jetson support are welcome! Please feel free to submit pull requests or open issues if you encounter any problems.

## License

This repository is licensed under the same license as the original Exo and xotorch projects.