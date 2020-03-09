---
title: "(obs) sourcetree를 통해 본 model and view 구현"
date: 2020-03-02 00:00:00 -0000
---

```cpp
// 우선 SourceTree는 QListView의 상속이다.
class SourceTree : public QListView
```

```cpp
// 생성자에서 SourceTreeModel을 model로 지정한다.
SourceTree::SourceTree(QWidget *parent_) : QListView(parent_)
{
	SourceTreeModel *stm_ = new SourceTreeModel(this);
	setModel(stm_);
```

```cpp
// item의 delegate지정은 여기서
// 정확히 delegate는 아님. item하나하나를 widget화 해서 구현함.
setIndexWidget(index, new SourceTreeItem(this, stm->items[i]));
```