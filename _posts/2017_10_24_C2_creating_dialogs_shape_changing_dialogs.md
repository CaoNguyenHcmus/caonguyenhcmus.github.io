----
layout: post
title: Chapter 2: Creating Dialogs (prj: sortdialog)
----



Knowhow Input Widgets > Combo Box
----
Add phần tử vào trong Combo Box bằng hàm addItem()
Xem hàm setColumnRange() để biết cách sử dụng.


Establish connections between widgets in form by using Qt Designer
----
Qt Designer allows us to establish connections between widgets that are part of the same form. We need to establish two connections.

Click *Edit|Edit Signals/Slots* to enter Qt Designer's connection mode. Connections are represented by blue arrows between the form's widgets, as shown in Figure 2.15, and they are also listed in Qt Designer's signal/slot editor window. To establish a connection between two widgets, click the sender widget and drag the red arrow line to the receiver widget, then release. This pops up a dialog that allows you to choose the signal and the slot to connect.
Example: Click vào button và thoát widget or dialog

*Change using namespace (Qt defaut) to using multiple inheritance for easy access to *data members* *
----
defaut:
```
#if 0
namespace Ui {
class sortdialog;
}
#endif
```
from
```
class sortdialog : public QDialog{....}
```
to
```
class sortdialog : public QDialog, public Ui::sortdialog{....}
```

Know-how điều chỉnh độ rộng của layout fit với nội dung trong dialog khi nhấn nút More
----
layout()->setSizeConstraint(QLayout::SetFixedSize);
Truoc do cac thanh phan phai dc set la hide() sau do', khi nhan button More. se emit signal va signal nay dc set sử dụng *Edit|Edit Signals/Slots*
```
Object::connect(moreButton, SIGNAL(toggled(bool)), secondaryGroupBox, SLOT(setVisible(bool)));
```

DEBUG: Nếu khởi động chương trình nên mà bị đứng thì có thể do hàm constructor
----
Ví dụ nếu comment //ch = ch.unicode() + 1;
Thì chương trình sẽ bị đứng luôn do nó bị đứng trong vòng lặp vô hạn. Vòng lặp này nằm trong hàm constructor.

Refer more more in document to know shape-changing dialogs.
----
The other common type of shape-changing dialogs, multi-page dialogs, are even easier to create in Qt, either in
code or using Qt Designer. Such dialogs can be built in many different ways.
# A QTabWidget can be used in its own right. It provides a tab bar that controls a built-in QStackedWidget.
# A QListWidget and a QStackedWidget can be used together, with the QListWidget's current item
determining which page the QStackedWidget shows, by connecting the
QListWidget::currentRowChanged() signal to the QStackedWidget::setCurrentIndex() slot.
# A QTreeWidget can be used with a QStackedWidget in a similar way to a QListWidget.
We cover the QStackedWidget class in Chapter 6.

Others: Dynamic Dialogs
----
QUiLoader
findChild

 [?] Q_FOREACH (QGroupBox* groupBox, this->findChildren<QGroupBox*>())
 Q_FOREACH
 findChildren
 https://www.dvratil.cz/2015/06/qt-containers-and-c11-range-based-loops/
