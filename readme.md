# OpenCV Utilities

[![Latest Version](https://img.shields.io/pypi/v/opencvutils.svg)](https://pypi.python.org/pypi/opencvutils/)

[![License](https://img.shields.io/pypi/l/opencvutils.svg)](https://pypi.python.org/pypi/opencvutils/)

This is a set of OpenCV utilities that should make working with OpenCV a
little easier. I forked this and added somethings for a class I taught in Spring
2018. You should probably use Adrian's library, link below.

**Original Author:** Adrian Rosebrock

**Original Name:** [imutils](https://github.com/jrosebr1/imutils)

## Install

The preferred way to install is using `pip`:

    pip install opencvutils

### Other Libraries

You will need both `numpy` and `opencv3` for this to work. Use your os
package manager to install. Unfortunately this is not fast, `numpy`
install involves compiling things, so go grab a coffee or something
while you wait.

for macOS (please be aware, the `brew` people keep changing this!):

    pip install numpy
    brew install opencv

## Development

To submit git pulls, clone the repository and set it up as follows:

    git clone https://github.com/walchko/opencvutils
    cd opencvutils
    pip install -e .

## Documentation

See the [Jupyter
Notebooks](https://github.com/walchko/opencvutils/tree/master/docs) for
examples of how to use this library. It contains a lot of common image
manipulations.

### Video Encoding

You can make a video like this:

```python
import cv2
from opencvutils.Camera import SaveVideo

shape = (240,320)  # rows (height), cols (width)
sv = SaveVideo()

# you can change the default encoder using a four_cc
# string, but not all of them work!
# sv.encoder('H264')
# sv.encoder('MP4V')
# sv.encoder('x264')

sv.open(filename, shape[1], shape[0])  # order is backwards from opencv!!!

for i in range(100):
    ret, img = camera.read()  # grab image
    sv.write(img)

sv.release()
```

### Scripts

``` {.sourceCode .bash
pi@raspberry ~ $ mjpeg_server.py -h
    usage: mjpeg_server.py [-h] [-v] [-p PORT] [-c CAMERA] [-t TYPE]
                                             [-s SIZE SIZE]

    A simple mjpeg server Example: mjpeg-server -p 8080 --camera 4

    optional arguments:
    -h, --help            show this help message and exit
    -v, --version         show program's version number and exit
    -p PORT, --port PORT  mjpeg publisher port, default is 9000
    -c CAMERA, --camera CAMERA
                                                set opencv camera number, ex. -c 1
    -t TYPE, --type TYPE  set camera type, either pi or cv, ex. -t pi
    -s SIZE SIZE, --size SIZE SIZE
                                                set size
```

Then you could do:

    pi@raspberry ~ $ mjpeg_server.py -t pi -s 640 480

now navigate to your computer (hostname:9000) and you should see the
mjpg stream. Note, if you changed the port number with the `-p` arg,
then use that port number.

# Change Log

| Data       | Version| Notes                                     |
|------------|--------|-------------------------------------------|
| 2018-07-19 |  0.9.4 |  simple clean-up and updating some things |
| 2017-10-29 |  0.9.3 |  bug fixes |
| 2017-04-09 |  0.9.0 |  initial python 3 support |
| 2017-03-31 |  0.7.0 |  refactored and got rid of things I don't need |
| 2017-01-29 |  0.6.0 |  added video capture (video and images) program |
| 2016-12-30 |  0.5.3 |  typo fix |
| 2016-12-30 |  0.5.1 |  refactored |
| 2016-12-11 |  0.5.0 |  published to PyPi |

# MIT License

Copyright (c) 2016 Kevin J. Walchko

Copyright (c) 2014 Adrian Rosebrock

Permission is hereby granted, free of charge, to any person obtaining a
copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be included
in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
