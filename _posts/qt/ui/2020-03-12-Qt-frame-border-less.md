---
title: "Qt - UI : Frameless(Borderless) Widget 만들기"
permalink: /qt/frameless/ # link 직접 지정
toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-03-12 00:00:00 -0000
last_modified_at: 2020-05-28 00:00:00 -0000
---

> * [Github](https://github.com/8bitscoding/VS_Frameless_Widget)

```cpp
// Frameless.h
#pragma once

#include <QtWidgets/QMainWindow>
#include "ui_Frameless.h"

class Frameless : public QMainWindow
{
	Q_OBJECT

public:
	Frameless(QWidget *parent = Q_NULLPTR);

private:
	Ui::FramelessClass ui;

public:
	bool nativeEvent(const QByteArray &eventType, void *message, long *result);
	bool event(QEvent *event);
	void mousePressEvent(QMouseEvent *e);
};
```

```cpp
// Frameless.cpp
#include "Frameless.h"
#include "qdebug.h"
#include "windows.h"
#include "windowsx.h"
#include "qevent.h"

Frameless::Frameless(QWidget *parent)
	: QMainWindow(parent)
{
	ui.setupUi(this);
	ui.newTitlebarLayout->setMenuBar(ui.menuBar);

	// 이 방법말고
	//HWND hwnd = (HWND)this->winId();
	//DWORD style = ::GetWindowLong(hwnd, GWL_STYLE);
	//::SetWindowLong(hwnd, GWL_STYLE, style | WS_MAXIMIZEBOX | WS_THICKFRAME | WS_CAPTION);

	// 이 방법이 더 낫다
	//setWindowFlags(Qt::Window | Qt::FramelessWindowHint | Qt::WindowMinMaxButtonsHint | Qt::CustomizeWindowHint);
	//setAttribute(Qt::WA_NoSystemBackground, true);
	//setAttribute(Qt::WA_TranslucentBackground); 

	// 최종(이걸 추천)
	setWindowFlags(Qt::Window | Qt::FramelessWindowHint);
	setAttribute(Qt::WA_OpaquePaintEvent, false);
	setAttribute(Qt::WA_PaintOnScreen, true);
	setAttribute(Qt::WA_DontCreateNativeAncestors, true);
	setAttribute(Qt::WA_NativeWindow, true);
	setAttribute(Qt::WA_NoSystemBackground, true);
	setAttribute(Qt::WA_MSWindowsUseDirect3D, true);
	setAutoFillBackground(false);
}

bool Frameless::nativeEvent(const QByteArray &eventType, void *message, long *result)
{
	if (eventType != "windows_generic_MSG") {
		return QWidget::nativeEvent(eventType, message, result);
	}

	const MSG *msg = reinterpret_cast<MSG *>(message);

	// 마우스를 처리하고 싶다면?
	// long x = GET_X_LPARAM(msg->lParam);
	// long y = GET_Y_LPARAM(msg->lParam);

	switch (msg->message) {
		// make frameless window
		case WM_NCCALCSIZE: {
			//this kills the window frame and title bar we added with
			//WS_THICKFRAME and WS_CAPTION
			if (false)
				return QWidget::nativeEvent(eventType, message, result);
			// 여기가 타이틀바를 그리는 부분이긴 한데, 여길 막으면(return하면) 안됨.
			// 이런식으로 강제로 타이틀바를 그리는 것을 막으면 듀얼모니터 환경에서 모니터간 이동시 UI가 깨질 수 있다
			//*result = 0;
			//return true;
		}
		default: {
			return QWidget::nativeEvent(eventType, message, result);
		}
	}
}

void Frameless::mousePressEvent(QMouseEvent *e)
{
	int x = e->pos().x();
	int y = e->pos().y();
	QSize size = this->size();

	qDebug() << "\n\n" << x << y << "\n\n";
	qDebug() << "\n\n" << size.width() << size.height() << "\n\n";

	if (e->button() == Qt::LeftButton) {
		ReleaseCapture();
		if (x < 50 && y > size.height() - 50) {
			this->setCursor(QCursor(Qt::SizeBDiagCursor));
			SendMessage(HWND(winId()), WM_NCLBUTTONDOWN, HTBOTTOMLEFT, 0);
		}
		else if (x > size.width() - 50 && y > size.height() - 50) {
			this->setCursor(QCursor(Qt::SizeFDiagCursor));
			SendMessage(HWND(winId()), WM_NCLBUTTONDOWN, HTBOTTOMRIGHT, 0);
		}
		else if (x < 50) {
			this->setCursor(QCursor(Qt::SizeHorCursor));
			SendMessage(HWND(winId()), WM_NCLBUTTONDOWN, HTLEFT, 0);
		}
		else if (y > size.height() - 50) {
			this->setCursor(QCursor(Qt::SizeVerCursor));
			SendMessage(HWND(winId()), WM_NCLBUTTONDOWN, HTBOTTOM, 0);
		}
		else if (x > size.width() - 50) {
			this->setCursor(QCursor(Qt::SizeHorCursor));
			SendMessage(HWND(winId()), WM_NCLBUTTONDOWN, HTRIGHT, 0);
		}
		else if (y < 50) {		// 여기가 titlebar가 된다.
			SendMessage(HWND(winId()), WM_NCLBUTTONDOWN, HTCAPTION, 0);
		}
	}
}

bool Frameless::event(QEvent *event)
{

	QPoint widgetCursorPos = QWidget::mapFromGlobal(QCursor::pos());

	int x = widgetCursorPos.x();
	int y = widgetCursorPos.y();
	QSize size = this->size();

	switch (event->type())
	{
	case QEvent::MouseButtonPress:
		ReleaseCapture();
		if (x < 50 && y > size.height() - 50) {
				this->setCursor(QCursor(Qt::SizeBDiagCursor));
				SendMessage(HWND(winId()), WM_NCLBUTTONDOWN, HTBOTTOMLEFT, 0);
			}
			else if (x > size.width() - 50 && y > size.height() - 50) {
				this->setCursor(QCursor(Qt::SizeFDiagCursor));
				SendMessage(HWND(winId()), WM_NCLBUTTONDOWN, HTBOTTOMRIGHT, 0);
			}
			else if (x < 50) {
				this->setCursor(QCursor(Qt::SizeHorCursor));
				SendMessage(HWND(winId()), WM_NCLBUTTONDOWN, HTLEFT, 0);
			}
			else if (y > size.height() - 50) {
				this->setCursor(QCursor(Qt::SizeVerCursor));
				SendMessage(HWND(winId()), WM_NCLBUTTONDOWN, HTBOTTOM, 0);
			}
			else if (x > size.width() - 50) {
				this->setCursor(QCursor(Qt::SizeHorCursor));
				SendMessage(HWND(winId()), WM_NCLBUTTONDOWN, HTRIGHT, 0);
			}
			else if (y < 50) {		// 여기가 titlebar가 된다.
				SendMessage(HWND(winId()), WM_NCLBUTTONDOWN, HTCAPTION, 0);
			}
		}
		return true;
		break;
	// 참고로 DbouleClick Event는 동작하지 않음, 참고할 것.
	// 더블클릭 처리하고 싶다면 Timer(QSingleshot)를 쓸것
	case QEvent::HoverEnter:
	case QEvent::HoverMove:
		qDebug() << "\n\n HoverEnter \n\n";
		qDebug() << "\n\n" << widgetCursorPos.x() << widgetCursorPos.y() << "\n\n";
		if (x < 50 && y > size.height() - 50) {
			this->setCursor(QCursor(Qt::SizeBDiagCursor));
		}
		else if (x > size.width() - 50 && y > size.height() - 50) {
			this->setCursor(QCursor(Qt::SizeFDiagCursor));
		}
		else if (x < 50) {
			this->setCursor(QCursor(Qt::SizeHorCursor));
		}
		else if (y > size.height() - 50) {
			this->setCursor(QCursor(Qt::SizeVerCursor));
		}
		else if (x > size.width() - 50) {
			this->setCursor(QCursor(Qt::SizeHorCursor));
		}
		else {
			this->setCursor(QCursor(Qt::ArrowCursor));
		}
		return true;
		break;
	case QEvent::HoverLeave:
		qDebug() << "\n\n HoverLeave \n\n";
		this->setCursor(QCursor(Qt::ArrowCursor));
		return true;
		break;

	default:
		break;
	}

	return QWidget::event(event);
}
```

---

* [가장확실한 Example](https://github.com/Jorgen-VikingGod/Qt-Frameless-Window-DarkStyle)

> * [참고사이트1](https://github.com/deimos1877/BorderlessWindow)
> * [참고사이트2](https://github.com/JJPPeters/clTEM/blob/9d2f52f0ce556b1e1f4b70ac40cbfebc438d6f23/src/gui/controls/borderlessdialog.cpp)
> * [참고사이트3](https://github.com/Jorgen-VikingGod/Qt-Frameless-Window-DarkStyle)

사실 참고사이트에서 내가 많이 수정했기때문에 정말 참고용으로만 볼 것