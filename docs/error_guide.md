# ALPR Parking Management System: Error Guide Document

This error guide provides detailed troubleshooting steps for common issues encountered while setting up, running, or maintaining the Automatic License Plate Recognition (ALPR) Parking Management System. Each entry includes the error message, a clear explanation, and actionable solutions to ensure smooth operation. This document is tailored to the system's deep learning and computer vision components, leveraging TensorFlow, OpenCV, and related libraries.

## General Troubleshooting Tips

- **Environment Check**: Ensure your Python environment (e.g., virtualenv or conda) is activated before running scripts.
- **Dependency Versions**: Verify compatibility between TensorFlow, CUDA, cuDNN, and other libraries as per the [README.md](README.md).
- **Logs**: Enable detailed logging (`logging.basicConfig(level=logging.DEBUG)`) to diagnose issues.
- **Restart**: Restart your IDE or Jupyter Notebook after major changes to clear cached states.

## Error Catalog

### 1. Module Not Found Error

- **Error Message**: `No module named 'xxxxxx'`
- **Description**: Occurs when a required Python module (e.g., `typeguard`, `cv2`) is missing from your environment.
- **Solution**:
  - Install the missing module using pip:

    ```bash
    pip install xxxxxx
    ```

  - **Example**: For `No module named typeguard`, run:

    ```bash
    pip install typeguard
    ```

  - **Note**: The module name may differ from the package name (e.g., `opencv-python` for `cv2`). Check the package documentation or `requirements.txt`.

### 2. AttributeError with Matplotlib

- **Error Message**: `AttributeError: module 'sip' has no attribute 'setapi'`
- **Description**: Caused by an incompatible Matplotlib version with your Python setup, often due to SIP API changes.
- **Solution**:
  - Downgrade Matplotlib to version 3.2:

    ```bash
    pip install matplotlib==3.2
    ```

  - Verify the installation with `pip show matplotlib`.

### 3. NumPy Array Size Mismatch

- **Error Message**: `ValueError: numpy.ndarray size changed, may indicate binary incompatibility. Expected 88 from C header, got 80 from PyObject`
- **Description**: Indicates a binary incompatibility between NumPy and other libraries (e.g., pycocotools) due to mismatched builds.
- **Solution**:
  - Reinstall pycocotools to resolve the conflict:

    ```bash
    pip uninstall pycocotools -y
    pip install pycocotools
    ```

  - Ensure NumPy version aligns with your TensorFlow setup (check `requirements.txt`).

### 4. Invalid Image Dimensions

- **Error Message**: `ValueError: 'images' must have either 3 or 4 dimensions`
- **Description**: Occurs when input images lack the expected dimensions, often due to an unavailable webcam or incorrect file paths.
- **Solution**:
  - If using a webcam, restart your Jupyter Notebook to reinitialize the camera.
  - For images, verify the file path and name:
    - Example: Ensure `data/plates/image.jpg` exists and is accessible.
  - Convert images to the required format (e.g., RGB) using OpenCV:

    ```python
    import cv2
    img = cv2.imread('image.jpg')
    if img is None or len(img.shape) not in (3, 4):
        raise ValueError("Invalid image dimensions")
    ```

### 5. Unspecified OpenCV Function Error

- **Error Message**: `error: (-2:Unspecified error) The function is not implemented. Rebuild the library with Windows, GTK+ 2.x or Cocoa support. If you are on Ubuntu or Debian, install libgtk2.0-dev and pkg-config, then re-run cmake or configure script in function 'cvDestroyAllWindows'`
- **Description**: Indicates OpenCV was built without GUI support, causing failures in window-related functions.
- **Solution**:
  - Uninstall the headless version and install the full OpenCV package:

    ```bash
    pip uninstall opencv-python-headless -y
    pip install opencv-python --upgrade
    ```

  - On Ubuntu/Debian, install dependencies:

    ```bash
    sudo apt-get install libgtk2.0-dev pkg-config
    ```

  - Rebuild OpenCV if using a custom installation.

### 6. ModuleNotFoundError at Command Line

- **Error Message**: `ModuleNotFoundError: No module named 'cv2'`
- **Description**: Occurs when running scripts from the command line without an activated environment, preventing access to installed packages.
- **Solution**:
  - Activate your virtual environment before execution:
    - **Virtualenv**: `source venv/bin/activate` (Linux/macOS) or `venv\Scripts\activate` (Windows).
    - **Conda**: `conda activate alpr_env`.
  - Run the script again:

    ```bash
    python script.py
    ```

### 7. GPU Ignored During Training

- **Error Message**: Only CPU is used, GPU is ignored.
- **Description**: Happens when CUDA or cuDNN versions are incompatible with TensorFlow.
- **Solution**:
  - Check and install compatible CUDA/cuDNN versions:
    - Windows: Follow [TensorFlow Windows Source Install](https://www.tensorflow.org/install/source_windows).
    - Linux/macOS: Follow [TensorFlow Source Install](https://www.tensorflow.org/install/source).
  - Verify with `nvidia-smi` and ensure TensorFlow detects the GPU:

    ```python
    import tensorflow as tf
    print(tf.config.list_physical_devices('GPU'))
    ```

### 8. CUDA/CUDNN Memory Allocation Failure

- **Error Message**: `CUBLAS_STATUS_ALLOC_FAILED` or `CUDNN_STATUS_ALLOC_FAILED`
- **Description**: Indicates insufficient VRAM, typically due to multiple Python processes or Jupyter Notebook instances.
- **Solution**:
  - Terminate all Python processes and stop the Jupyter Notebook server:

    ```bash
    pkill -f python
    jupyter notebook stop
    ```

  - Clear VRAM and retry the training command:

    ```bash
    python train.py --data_dir data/processed/
    ```

  - Reduce batch size or use model pruning if memory constraints persist.

## Advanced Troubleshooting

- **Dependency Conflicts**: Use `pip check` to identify conflicts and resolve with `pip install --force-reinstall package-name`.
- **Performance Issues**: Profile code with `cProfile` to identify bottlenecks.
- **Custom Errors**: For unlisted errors, inspect stack traces, check library versions, and consult [OpenCV Docs](https://docs.opencv.org/) or [TensorFlow Docs](https://www.tensorflow.org/).

## Contributing to the Error Guide

- Report new errors via GitHub Issues with full stack traces.
- Submit pull requests with documented solutions, following this guide’s structure.

## References

- [OpenCV Documentation](https://docs.opencv.org/)
- [TensorFlow Documentation](https://www.tensorflow.org/)

## License

MIT License - see the [LICENSE](../LICENSE) file for details.
