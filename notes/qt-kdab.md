
# Introduction to Qt/QML (KDAB)

## 1. Introduction

- structure of courses
- UI in QML, buisness logic in C++
- hello world
```js
import QtQuick 2.0

Text {
    text: "hello world"
}
```

- Run as script. See https://www.ics.com/blog/whole-shebang-running-qml-files-directly.
```js
// file: example.qml
#! env qml
import ...

// bash
./example.qml
```

## 2. Short history of Qt

QML principes :
- intuitive UI
- designer orienté
- rapid prototype and production
- easy deployment

## 3. Structure of QML file

- zorder

## 4. Property Binding

## 5. Understand QML properties





## 49. Creating new elements from C++

- subclass QObject or QQuickItem (C++)
- register type (C++). `qmlRegisterType`
- import module (QML)
- use the item (QML)

## 50. Creatign new element from C++

- painted items (QQuickPaintedItem + paint). Create texture and draw in it with QPainter.
- sene graph items (QQuickItem + updatePaintNode)
- raw OpenGL items (QQuickFrameBufferObject + createRender)
- same as non GUI classes (QObject + signals/slots + invokable)

```cpp
// .h
class EllipseItem : public QQuickPaintedItem ...
    void paint(QPainter* painter) override;

// .cpp
void ElipseItem::paint(QPainter* painter) {
    painter->save();
    ... init paintRect
    painter->drawElipse(paintRect);
    painter->restore();
}
```





