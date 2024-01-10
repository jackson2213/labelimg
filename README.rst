LabelImg
========

.. image:: https://img.shields.io/pypi/v/labelimg.svg
        :target: https://pypi.python.org/pypi/labelimg

.. image:: https://img.shields.io/travis/tzutalin/labelImg.svg
        :target: https://travis-ci.org/tzutalin/labelImg

.. image:: https://img.shields.io/badge/lang-en-blue.svg
        :target: https://github.com/tzutalin/labelImg/blob/master/README.zh.rst

.. image:: https://img.shields.io/badge/lang-zh-green.svg
        :target: https://github.com/tzutalin/labelImg/blob/master/readme/README.zh.rst

.. image:: https://img.shields.io/badge/lang-zh--TW-green.svg
    :target: (https://github.com/jonatasemidio/multilanguage-readme-pattern/blob/master/README.pt-br.md

LabelImg is a graphical image annotation tool.

It is written in Python and uses Qt for its graphical interface.

Annotations are saved as XML files in PASCAL VOC format, the format used
by `ImageNet <http://www.image-net.org/>`__.  Besides, it also supports YOLO and CreateML formats.

.. image:: https://raw.githubusercontent.com/tzutalin/labelImg/master/demo/demo3.jpg
     :alt: Demo Image

.. image:: https://raw.githubusercontent.com/tzutalin/labelImg/master/demo/demo.jpg
     :alt: Demo Image

`Watch a demo video <https://youtu.be/p0nR2YsCY_U>`__


change log
------------------
1. remove predifine class, add auto check save dir classes.txt file and load label
2. change auto save model is true
3. remove change save dir and set auto save label to open dir

Installation
------------------

Get from PyPI but only support python3.0 or above
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
This is the simplest (one-command) install method on modern Linux distributions such as Ubuntu and Fedora.

.. code:: shell

    pip3 install labelImg
    labelImg
    labelImg [IMAGE_PATH] [PRE-DEFINED CLASS FILE]


Build from source
~~~~~~~~~~~~~~~~~

Ubuntu Linux
^^^^^^^^^^^^

Python 3 + PySide6

.. code:: shell

    pip install -r requirements/requirements-linux-python3.txt
    make pyside6
    python3 labelImg.py
    python3 labelImg.py [IMAGE_PATH] [PRE-DEFINED CLASS FILE]

macOS
^^^^^

Python 3 + PySide6

.. code:: shell

    pip3 install pyside6 lxml
    make pyside6
    python3 labelImg.py
    python3 labelImg.py [IMAGE_PATH] [PRE-DEFINED CLASS FILE]


Python 3 Virtualenv (Recommended)

Virtualenv can avoid a lot of the QT / Python version issues

.. code:: shell

    brew install python3
    pip3 install pipenv
    pipenv run pip install pyside6 lxml
    pipenv run make pyside6
    pipenv run python3 labelImg.py
    [Optional] rm -rf build dist; python setup.py py2app -A;mv "dist/labelImg.app" /Applications

Note: The Last command gives you a nice .app file with a new SVG Icon in your /Applications folder. You can consider using the script: build-tools/build-for-macos.sh


Windows
^^^^^^^

Open cmd and go to the `labelImg <#labelimg>`__ directory

.. code:: shell

    pip install pyside6 lxml
    pyside6-rcc -o libs/resources.py resources.qrc
    python labelImg.py
    python labelImg.py [IMAGE_PATH] [PRE-DEFINED CLASS FILE]

Windows + Anaconda
^^^^^^^^^^^^^^^^^^

Open the Anaconda Prompt and go to the `labelImg <#labelimg>`__ directory

.. code:: shell

    conda install pyside6
    conda install -c anaconda lxml
    pyside6-rcc -o libs/resources.py resources.qrc
    python labelImg.py
    python labelImg.py [IMAGE_PATH] [PRE-DEFINED CLASS FILE]

You can pull the image which has all of the installed and required dependencies. `Watch a demo video <https://youtu.be/nw1GexJzbCI>`__

Usage
-----

Steps (PascalVOC)
~~~~~~~~~~~~~~~~~

1. Build and launch using the instructions above.
2. Click 'Change default saved annotation folder' in Menu/File
3. Click 'Open Dir'
4. Click 'Create RectBox'
5. Click and release left mouse to select a region to annotate the rect
   box
6. You can use right mouse to drag the rect box to copy or move it

The annotation will be saved to the folder you specify.

You can refer to the below hotkeys to speed up your workflow.

Steps (YOLO)
~~~~~~~~~~~~

1. In ``data/predefined_classes.txt`` define the list of classes that will be used for your training.

2. Build and launch using the instructions above.

3. Right below "Save" button in the toolbar, click "PascalVOC" button to switch to YOLO format.

4. You may use Open/OpenDIR to process single or multiple images. When finished with a single image, click save.

A txt file of YOLO format will be saved in the same folder as your image with same name. A file named "classes.txt" is saved to that folder too. "classes.txt" defines the list of class names that your YOLO label refers to.

Note:

- Your label list shall not change in the middle of processing a list of images. When you save an image, classes.txt will also get updated, while previous annotations will not be updated.

- You shouldn't use "default class" function when saving to YOLO format, it will not be referred.

- When saving as YOLO format, "difficult" flag is discarded.



Hotkeys
~~~~~~~

+--------------------+--------------------------------------------+
| Ctrl + u           | Load all of the images from a directory    |
+--------------------+--------------------------------------------+
| Ctrl + r           | Change the default annotation target dir   |
+--------------------+--------------------------------------------+
| Ctrl + s           | Save                                       |
+--------------------+--------------------------------------------+
| Ctrl + d           | Copy the current label and rect box        |
+--------------------+--------------------------------------------+
| Ctrl + Shift + d   | Delete the current image                   |
+--------------------+--------------------------------------------+
| Space              | Flag the current image as verified         |
+--------------------+--------------------------------------------+
| w                  | Create a rect box                          |
+--------------------+--------------------------------------------+
| d                  | Next image                                 |
+--------------------+--------------------------------------------+
| a                  | Previous image                             |
+--------------------+--------------------------------------------+
| del                | Delete the selected rect box               |
+--------------------+--------------------------------------------+
| Ctrl++             | Zoom in                                    |
+--------------------+--------------------------------------------+
| Ctrl--             | Zoom out                                   |
+--------------------+--------------------------------------------+
| ↑→↓←               | Keyboard arrows to move selected rect box  |
+--------------------+--------------------------------------------+

**Verify Image:**

When pressing space, the user can flag the image as verified, a green background will appear.
This is used when creating a dataset automatically, the user can then through all the pictures and flag them instead of annotate them.

**Difficult:**

The difficult field is set to 1 indicates that the object has been annotated as "difficult", for example, an object which is clearly visible but difficult to recognize without substantial use of context.
According to your deep neural network implementation, you can include or exclude difficult objects during training.

How to reset the settings
~~~~~~~~~~~~~~~~~~~~~~~~~

In case there are issues with loading the classes, you can either:

1. From the top menu of the labelimg click on Menu/File/Reset All
2. Remove the `.labelImgSettings.pkl` from your home directory. In Linux and Mac you can do:
    `rm ~/.labelImgSettings.pkl`


How to contribute
~~~~~~~~~~~~~~~~~

Send a pull request

License
~~~~~~~
`Free software: MIT license <https://github.com/tzutalin/labelImg/blob/master/LICENSE>`_

Citation: Tzutalin. LabelImg. Git code (2015). https://github.com/tzutalin/labelImg

Related and additional tools
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. `ImageNet Utils <https://github.com/tzutalin/ImageNet_Utils>`__ to
   download image, create a label text for machine learning, etc
2. `Use Docker to run labelImg <https://hub.docker.com/r/tzutalin/py2qt4>`__
3. `Generating the PASCAL VOC TFRecord files <https://github.com/tensorflow/models/blob/4f32535fe7040bb1e429ad0e3c948a492a89482d/research/object_detection/g3doc/preparing_inputs.md#generating-the-pascal-voc-tfrecord-files>`__
4. `App Icon based on Icon by Nick Roach (GPL) <https://www.elegantthemes.com/>`__
5. `Setup python development in vscode <https://tzutalin.blogspot.com/2019/04/set-up-visual-studio-code-for-python-in.html>`__
6. `The link of this project on iHub platform <https://code.ihub.org.cn/projects/260/repository/labelImg>`__
7. `Convert annotation files to CSV format or format for Google Cloud AutoML <https://github.com/tzutalin/labelImg/tree/master/tools>`__

Stargazers over time
~~~~~~~~~~~~~~~~~~~~

.. image:: https://starchart.cc/tzutalin/labelImg.svg

build
~~~~~~~~~~~~~~~~~~~~
pyinstaller  --hidden-import=lxml  --hidden-import=PySide6 -F -n "labelImg" -c labelImg.py -p ./libs -p


