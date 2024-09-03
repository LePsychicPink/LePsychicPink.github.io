---
title: Concept of PySide6(PyQt)
date: 2024-09-04 01:20:39
tags: python
categories: programming
---

Using YouTube Video from [freeCodeCamp](https://www.youtube.com/watch?v=Z1N9JzNax2k&t=15000s) as reference

UI creation can be done by `QtWidget` and `QML`, and this post is using **Qt**.

## Requirement

- Python3
- Pyside6
- Qt Designer

## Step 1 - Code understanding

### Level 1

Here is the most basic code to create an empty window of python application with ui

```Python
from PySide6.QtWidgets import QApplication, QWidget

import sys # mean nothing here but important if we need to handle command line argument

app = QApplication(sys.argv)

window = QWidget()
window.show() # calling the window to show because it is hidden in default

app.exec() # start the event loop
```

And we will get sth like this
![](1.png)

### Level 2

To add a simple button, here is the code

```Python
from PySide6.QtWidgets import QApplication, QWidget, QMainWindow,QPushButton

import sys

app = QApplication(sys.argv)

window = QMainWindow()
window.setWindowTitle('title1')

button = QPushButton()
button.setText('button1')

window.setCentralWidget(button)
window.show()

app.exec()
```

![](2.png)

### Level 3

To organize it better, we group the widget setting into a class

```Python
from PySide6.QtWidgets import QApplication, QWidget, QMainWindow,QPushButton

import sys

class ButtonHolder(QMainWindow): ## class ButtonHolder inherit QMainWindow
    def __init__(self):
        super().__init__()
        self.setWindowTitle('title1')
        button = QPushButton('button1')
        self.setCentralWidget(button)

app = QApplication(sys.argv)
window = ButtonHolder()
window.show()
app.exec()
```

this actually perform the same with above

### Level 4

To make it even more organized, we separate them into files
`button_holder.py`

```Python
from PySide6.QtWidgets import QWidget, QMainWindow,QPushButton

class ButtonHolder(QMainWindow):
    def __init__(self):
        super().__init__()
        self.setWindowTitle('title1')
        button = QPushButton('button1')
        self.setCentralWidget(button)
```

`main.py`

```Python
import sys

from PySide6.QtWidgets import QApplication
from button_holder import ButtonHolder # import the class ButtonHolder from button_holder.py

app = QApplication(sys.argv)
window = ButtonHolder()
window.show()
app.exec()
```

## Step 2 - Signals and Slot

### QPushbutton - Level 1

`clicked` is a signal emitted by QPushButton (Actually it parent QAbstractButton)

```Python
from PySide6.QtWidgets import QApplication, QWidget, QMainWindow,QPushButton

import sys

def button_clicked():
    print('button clicked')

class ButtonHolder(QMainWindow):
    def __init__(self):
        super().__init__()
        self.setWindowTitle('title1')
        button = QPushButton('button1')
        button.clicked.connect(button_clicked) # new statement trigger button_clicked() function to print things
        self.setCentralWidget(button)


app = QApplication(sys.argv)
window = ButtonHolder()
window.show()
app.exec()
```

### QPushbutton - Level 2

Base on the [official doc](https://doc.qt.io/qt-6/qabstractbutton.html), we can know that button can also save it state to the function `button_clicked`

```Python
from PySide6.QtWidgets import QApplication, QWidget, QMainWindow,QPushButton

import sys

def button_clicked(checked): # notice that checked it received as a input which comes from clicked
    print('button clicked' ,checked)

class ButtonHolder(QMainWindow):
    def __init__(self):
        super().__init__()
        self.setWindowTitle('title1')
        button = QPushButton('button1')
        button.setCheckable(True)
        button.clicked.connect(button_clicked)
        self.setCentralWidget(button)


app = QApplication(sys.argv)
window = ButtonHolder()
window.show()
app.exec()
```

### Slider

`Slider` have a `valueChanged` as a signal like button's `clicked`

```Python
from PySide6.QtCore import Qt
from PySide6.QtWidgets import QApplication, QWidget, QMainWindow, QSlider

def slider_change(value):
    print('slider moved' ,value)

app = QApplication()
slider = QSlider(Qt.Horizontal)
slider.setMinimum(1)
slider.setMaximum(100)
slider.setValue(25)
slider.valueChanged.connect(slider_change)
slider.show()
app.exec()
```

## Step 3 - Layout

Put things together.
`widgetholder.py`

```Python
from PySide6.QtCore import Qt
from PySide6.QtWidgets import QWidget, QMainWindow, QSlider, QPushButton, QHBoxLayout, QVBoxLayout

class WidgetHolder(QWidget):
    def __init__(self):
        super().__init__()
        self.setWindowTitle('title1')
        button = QPushButton('button1')
        button.clicked.connect(self.button_clicked) # remember to add self because you are calling function of this class
        slider = QSlider(Qt.Horizontal)
        slider.setMinimum(1)
        slider.setMaximum(100)
        slider.setValue(25)
        slider.valueChanged.connect(self.slider_change)
        layout = QVBoxLayout()
        #layout = QHBoxLayout() # depends on how you want to set the layout
        layout.addWidget(button)
        layout.addWidget(slider)
        self.setLayout(layout)

    def slider_change(self,value): # remember to add self to declare function belong to the class
        print('slider moved' ,value)

    def button_clicked(self):
        print('button clicked')
```

`main.py`

```Python
from PySide6.QtWidgets import QApplication
import sys
from widgetholder import WidgetHolder

app = QApplication(sys.argv)
window = WidgetHolder()
window.show()
app.exec()
```
