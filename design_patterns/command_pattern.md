---
title: 命令模式及其在Apache IoTDB中的应用
description: 如何在IoTDB中新增一个功能
---

## 命令模式原理

### 模式动机

在软件设计中，我们经常需要向某些对象发送请求，但是 并不知道请求的接收者是谁，也不知道被请求的操作是哪 个，我们只需在程序运行时指定具体的请求接收者即可，此时，可以使用命令模式来进行设计，使得请求发送者与请求接收者消除彼此之间的耦合，让对象间的调用关系更加灵活。



命令模式可以对发送者和接收者完全解耦，发送者与接收者之间没有直接引用关系，发送请求的对象只需要知道如何发送请求，而不必道如何完成请求。这就是命令模式的模式动机。

### 模式定义与结构

命令模式(Command Pattern)：将一个请求封装为一个对象，从而使我们可用不同的请求对客户进行参数化；对请求排队或者记录请求日志，以及支持可撤销的操作。命 令模式是一种对象行为型模式，其别名为动作(Action)模式或事务(Transaction)模式。



命令模式包含如下角色： 

- Command: 抽象命令类
- ConcreteCommand: 具体命令类
- Invoker: 调用者
- Receiver: 接收者
- Client: 客户类



![](\picture\command_pattern.png)



### 模式分析

- 命令模式的本质是对命令进行封装，将发出命令的责任和执行命令的责任分割开。 
- 每一个命令都是一个操作：请求的一方发出请求，要求 执行一个操作；接收的一方收到请求，并执行操作。 
- 命令模式允许请求的一方和接收的一方独立开来，使得请求的一方不必知道接收请求的一方的接口，更不必知道请求是怎么被接收，以及操作是否被执行、何时被执行，以及是怎么被执行的。
- 命令模式使请求本身成为一个对象，这个对象和其他对象一样可以被存储和传递。 
- 命令模式的关键在于引入了抽象命令接口，且发送者针对抽象命令接口编程，只有实现了抽象命令接口的具体命令才能与接收者相关联。

#### 优点

- 降低系统的耦合度
- 新的命令可以很容易地加入到系统中
- 可以比较容易地设计一个命令队列和宏命令（组合命令）
- 可以方便地实现对请求地Undo和Redo

#### 缺点

使用命令模式可能会导致某些系统有过多的具体命令类。因为针对每一个命令都需要设计一个具体命令类，因此某些系统可能需要大量具体命令类，这将影响命令模式的使用。



### 适用场景

- 系统需要将请求的调用者和接受者进行解耦，使得调用者和接收者不直接交互
- 系统需要在不同的时间指定请求，将请求排队和执行请求
- 系统需要支持命令的Undo和Redo
- 系统需要将一组操作组合在一起，即支持宏命令。



## Apache IoTDB中的Plan

### 逻辑计划



### 物理计划
