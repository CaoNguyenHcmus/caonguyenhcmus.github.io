Note: This note will be update into network tonight
----
meta-object system
# signals-slots
# introspection (sự tự xét, sự xem xét nội tâm, nội quan)
Nếu mình curious thì đọc phần này nha

Rapid Dialog Design
====
TODO: Using Qt Designer to create the Go to Cell dialog (Xem hình nha)
Creating a dialog always involes the same fundamental steps:
1. Create and initilaize the child widgets
2. Put the child widget in the layouts.
3. Set the tab order.
4. Establish signal-slot connections.
5. Implement the dialog'' custom slots.

Lúc mình tạo giao diện:
1. để *default* property to "true" có nghĩa là gì?
bằng với setDefault(true), The default button là nút sẽ được nhấn khi user nhấn phím *Enter*
2. để *enabled* property to "false" có nghĩa là gì?
==> Disable the OK button. Nút nhấn sẽ bị biến thành màu xám và nó sẽ không đáp ứng với user interaction

Hint: Nhớ lại Chapter 2. Creating Dialogs
findButton->setDefault(true);
findButton->setEnabled(false);

3. chọn Edit --> Edit Buddies(F4), xong thì chọn lại mode cũ Edit --> Edit Widgets (F3)
chọn cái label và kéo mũi tên màu đỏ qua cái QLineEdit
Thằng buddy widget chấp nhận focus vào ô Text khi người ta nhấn shortcut key (Ctrl + shortcut key) (the label''s buddy)
Hint: label->setBuddy(lineEdit);

----
Layout:
Nhấn Ctrl thay vì Shift như trong tài liệu nha. Chọn 2 đối tượng sau đó Layouts: Horizontal Layout nha
Ta nên layout các đối tượng bên trong trước. Sau đó layout cái background sau. Chọn resize để fit size.

----
Tab order Edit --> Edit Tab Order...
Cái này dùng để check khi mình nhấn phím Tab sẽ nhảy từ đâu qua đâu.
Mình preview cái menu sau đó nhấn phím Tab để check nha

----
4 Establish signal-slot connections

