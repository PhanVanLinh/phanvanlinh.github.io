---
layout: post
category: "android"
title:  "Android Studio Tips"
tags: [java]
---


1. Change Logcat color

Preferences (Settings) -> Editor -> Color & Fonts -> Android Logcat và thay đổi foreground color cho từng kiểu log.

Assert #BA68C8
Debug #2196F3
Error #F44336
Info #4CAF50
Verbose #BBBBBB
Warning #FF9800


2. Search for command

CMD + Shift + a (Windows/Linux Ctrl + shift + a)

Giả sử bạn muốn close tab hiện tại nhưng bạn không biết làm cách nào. Hãy type close và bạn sẽ tìm thấy phím tắt hoặc command tương ứng.

3. Lựa chọn giữa những copy/pastes (quản lý clipboard)

CMD + Shift + V (Windows/Linux Ctrl + Shift + V)
Mặc định sẽ có 5 nội dung cho bạn lựa chọn



Độ sâu của clipboard stack được cấu hình trong Limits section trên Editor page của Settings. Khi đạt max số lựa chọn thì phần tử cũ nhất sẽ được remove.

4. Open a class

MacOSX: Cmd + O
Windows/Linux : Ctrl + N

5. Open file

Mac OSX: Cmd + Shift + O
Windows/Linux: Ctrl + Shift + N

6. Go to implementation

Mac: Cmd + Option + b
Windows/Linux: Ctrl + Alt + b

Giả sử bạn có một interface, đặt con trỏ tại interface name và click Go to implementation sẽ nhảy sang classes mà bạn implement interface đó.

7. Go to declaration

Mac: Cmd + b
Window/Linux: Ctrl + b

Cho phép bạn đi tới định nghĩa của 1 class, method hoặc variable.

8. Go to Type declaration

Mac: Ctrl + Shift + b
Windows/Linux: Ctrl + Shift + b

Giả sử bạn định nghĩa:

Employee employee = new Employee("Michal");

Khi bạn đặt con trỏ vào employee và chọn shortcut, bạn sẽ được đến trực tiếp class Employee

9. Go to super

Mac: Cmd + u
Window/ Linux: Ctrl + u

Ví dụ bạn override 1 method. Khi đặt con trỏ tại method name và click Go to super thì sẽ tới method của parent