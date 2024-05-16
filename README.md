# OpenALPR

OpenALPR is an open-source Automatic License Plate Recognition (ALPR) library written in C++ with bindings for C#, Java, Node.js, Go, and Python. The library analyzes images and video streams to identify license plates and outputs the text representation of any license plate characters.

Check out a live online demo here: [OpenALPR Demo](http://www.openalpr.com/demo-image.html)

## User Guide

OpenALPR includes a command-line utility. Simply typing `alpr [image file path]` is enough to get started recognizing license plate images.

For example:
user@mac:~/openalpr$ alpr ./samplecar.png

plate0: top 10 results -- Processing Time = 58.1879ms.
- PE3R2X confidence: 88.9371
- PE32X confidence: 78.1385
- PE3R2 confidence: 77.5444
- PE3R2Y confidence: 76.1448
- P63R2X confidence: 72.9016
- FE3R2X confidence: 72.1147
- PE32 confidence: 66.7458
- PE32Y confidence: 65.3462
- P632X confidence: 62.1031
- P63R2 confidence: 61.5089

Detailed command line usage:
user@mac:~/openalpr$ alpr --help

USAGE:
alpr [-c <country_code>] [--config <config_file>] [-n <topN>] [--seek <integer_ms>] [-p <pattern code>] [--clock] [-d] [-j] [--] [--version] [-h] <image_file_path>

Options:
-c <country_code>, --country <country_code>
Country code to identify (either us for USA or eu for Europe). Default=us

--config <config_file>
Path to the openalpr.conf file

-n <topN>, --topn <topN>
Max number of possible plate numbers to return. Default=10

--seek <integer_ms>
Seek to the specified millisecond in a video file. Default=0

-p <pattern code>, --pattern <pattern code>
Attempt to match the plate number against a plate pattern (e.g., md for Maryland, ca for California)

--clock
Measure/print the total time to process image and all plates. Default=off

-d, --detect_region
Attempt to detect the region of the plate image. [Experimental] Default=off

-j, --json
Output recognition results in JSON format. Default=off

--, --ignore_rest
Ignores the rest of the labeled arguments following this flag.

--version
Displays version information and exits.

-h, --help
Displays usage information and exits.

<image_file_path>
Image containing license plates

OpenAlpr Command Line Utility


## Binaries

Pre-compiled Windows binaries can be downloaded on the [releases page](https://github.com/openalpr/openalpr/releases).

## macOS Installation

To install OpenALPR on macOS, follow these steps:

1. Clone the OpenALPR repository:
    ```bash
    git clone https://github.com/<your-username>/openalpr.git
    cd openalpr
    ```

2. Install the required dependencies using Homebrew:
    ```bash
    brew install cmake tesseract leptonica log4cplus opencv
    ```

3. Build and install OpenALPR:
    ```bash
    mkdir build
    cd build
    cmake ..
    make
    sudo make install
    ```

## Documentation

Detailed documentation is available at [doc.openalpr.com](http://doc.openalpr.com/).

## Integrating the Library

OpenALPR is written in C++ and has bindings for C#, Python, Node.js, Go, and Java. Please see this guide for examples showing how to run OpenALPR in your application: [OpenALPR Bindings Guide](http://doc.openalpr.com/bindings.html).

## Compiling

OpenALPR compiles and runs on Linux, macOS, and Windows. 

OpenALPR requires the following additional libraries:
- Tesseract OCR v3.0.4 or later (https://github.com/tesseract-ocr/tesseract)
- OpenCV v2.4.8 or later (http://opencv.org/)

Please follow these detailed compilation guides for your respective operating system:
- [Windows](https://github.com/openalpr/openalpr/wiki/Compilation-instructions-(Windows))
- [Ubuntu Linux](https://github.com/openalpr/openalpr/wiki/Compilation-instructions-(Ubuntu-Linux))
- [macOS](https://github.com/openalpr/openalpr/wiki/Compilation-instructions-(OS-X))

If all went well, there should be an executable named `alpr` along with `libopenalpr-static.a` and `libopenalpr.so` that can be linked into your project.

## Docker

```shell
# Build docker image
docker build -t openalpr https://github.com/openalpr/openalpr.git
# Download test image
wget http://plates.openalpr.com/h786poj.jpg
# Run alpr on image
docker run -it --rm -v $(pwd):/data:ro openalpr -c eu h786poj.jpg

Questions
Please post questions or comments to the Google group list: OpenALPR Google Group.

Contributions
Improvements to the OpenALPR library are always welcome. Please review the OpenALPR design description and get started.

License
Affero GPLv3: http://www.gnu.org/licenses/agpl-3.0.html

Commercial-friendly licensing available. Contact: info@openalpr.com