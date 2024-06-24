# BombCat Project

## 1.介绍
炸弹猫是一款常见的桌游。以抽到炸弹且无法拆解作为失败条件。

## 2.基本逻辑

### 2.1.基本框架
* 在炸弹猫中，我们创建两个类，一个为`Card`类，负责记录所有的牌型；另一个为`Player`类，负责代表玩家的状态和手牌情况。
* 对于游戏进行，创建另一个类，为`Game`类，包含了玩家和当前牌堆情况。
* 目前为文档编写阶段，不进行编程工作。ui开发暂定为使用Qt.

### 2.2.`Card`类的要求
在`Card`类中，需要包含以下成员：
* `std::string`类型的`name`
* `std::string`类型的描述
* `int`类型的`id`

等。

需要包含以下函数：
* `void function()`实现卡牌功能。其中参数自定。

等。

注意父子类和纯虚函数的使用。

### 2.3.`Player`类的要求

在`Player`类中，需要包含以下成员：
* `std::vector<Card>`类型的`hand`，用于记录玩家当前手牌
* `int`类型的`id`，用于记录玩家的唯一编号。从`0`开始。
* `bool`类型的`isVisible`，用于记录玩家是否可见自己的手牌，用于特殊牌`诅咒`。默认为`true`。

等。

### 2.4.`Game`类的要求
在`Game`类中，需要包含以下成员：
* `std::vector<Player>`类型的`players`
* `std::vector<Card>`类型的`deck`，用于记录牌堆状况
* `bool`类型的`direction`，用于记录目前的顺序。以`true`为逆时针，默认为`true`。

等。

**注意：** 共有和私有由负责人员自行决定。

## 3.目前任务（2024/6/24 - 2024/6/30）

1. 完成文档的内容补充。

2. 完成卡牌的功能描述。目前需要完成的卡牌有：
    * 拆除
    * 炸弹
    * **涉及玩家的牌**：交换、帮助、预见未来（$\times 3、\times 5$）、改变未来（观星）、切洗、下翻。
    * **设计轮次**：跳过、反转、攻击。

3. 下阶段要完成：
   * 指向攻击
   * 超级跳跃（跳过所有叠加回合）
    
    请注意代码的可复用性。

## 4.代码规范

### 4.1.命名规范
- 所有命名使用英文单词（不要使用拼音）或其缩写，以及一些常用的简写变量。

#### 举例：
- 类名：每个单词的首字母大写
- 变量和函数名：使用驼峰格式
- 除非特殊情况，否则头文件开头使用 `#pragma once`

### 4.2.示例代码
#### 一些具体的注意点
- 大括号位置：`if`、`else`、`for`、`while` 等在同一行末尾；函数定义末尾的大括号在下一行。
- 缩进：每一级4个空格缩进。
- 每个两元运算符（即 `X op Y` 形式中的 `op`）左右各有空格，比如 `+`, `>=`, `=` 等。
- 所有不会被修改的参数需要按照const引用的方式传递（`int`, `double` 等基本类型可以直接传递，不需要使用const引用）。

#### 例如下示例中，`DIYClass` 的用法
```cpp
int Student::getScore(int classId, const vector<Class> &allClasses) const {
    if (classId < 0 || classId >= numClasses) {
        // 无效的课程 ID
        return 0;
    } else {
        vector<Class>::Iterator cl;
        // 遍历所有课程，找到特定class id的课程分数
        for (cl = allClasses.begin(); cl != allClasses.end(); ++cl) {
            if (cl->id == classId) {
                return cl->getScore(this);
            }
        }
        // 未找回该 class
        return -1;
    }
}
```

### 4.3.函数头格式
- 函数注释要能表示函数具体行为，要能涵盖每个参数的含义和作用，解释返回值的含义。

#### 例如：
```cpp
// getScore 接受课程号(classId)作为参数，返回对应课程的分数
// 未找到时返回-1
int Student::getScore(int classId, const vector<Class> &allClasses) const {
    // ...
}
```

### 4.4.函数长度要求
- 原则上每个函数不超过50行。





