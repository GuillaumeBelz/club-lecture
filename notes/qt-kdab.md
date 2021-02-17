
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

## 6. Qt Creator: How to Display Scope

## 7. Images

- local file
- ressource
- online
- size
- `progress`
- border image, scale modes
- animated image

## 8. Item transformations

- position relative to parent
- opacity
- scaling
- rotation
- `transformOrigin`

## 9. Custom transformations

- `transform: list<Transform>`
- `Rotation`
- `Scale`
- `Translate`
- `Matrix4x4`

## 10. Anchor layout

- for size and position
- can be used with size

## 11. Binding loop

## 12. Color and Gradients

- named color
- `"#rrggbb"` ou ``"#aarrggbb"`
- `Qt.rgba(int, int, int, int)`
- `Gradient` et `GradientStop`













## 48. QObject ownership

- by C++ or JS engine
- QQmlEngine::setObjectOwnership = QQmlEngine::CppOwnership or QQmlEngine::JavaScriptOwnership
- default = by C++ or JS
- **exception : QObject* parent-less returned by `Q_INVOKABLE` functions have JavaScriptOwnership**

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





