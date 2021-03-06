# 《Head first设计模式》笔记

## 一、策略模式

### 1. 内容

对于一个描述鸭子的Duck类，有不同的子类，不同的子类的行为比如Fly和Quack的行为是不一样的。书中举例Fly可能分为FlyWithWings和FlyNoWay两种方式，Quack则可能有Quack、Squeak和MuteQuack三种方式。对于这种变化的行为，设计模式更倾向于把这类行为从Duck中剥离出来。因此对Duck类将这些行为从类的成员方法修改为接口，作为Duck的成员来委托执行Fly和Quack行为。在Duck类中只留下行为的基类接口，行为基类可以继承出不同的子类，在初始化出一个Duck的实例对象的时候，可以为这些行为基类对象初始化出合适的行为子类对象。更灵活的方式还可以在初始化的时候创建一个默认的行为方式，然后通过Duck的成员函数去为行为接口设置不同的行为子类。

### 2. 思考

这种设计模式的灵活性从何而来？

灵活性是相对而言的，那么这种设计模式相对的实现有应该是一个Duck基类，不同种类的Duck继承于这个子类，并各自实现其Fly和Quack方法。

而对于策略模式，在基类Duck中，行为从成员函数变成了成员，该对象通过组合的方式成为Duck的一部分。此刻行为本身也成为类，子类对象为行为提供了多态。

行为的多态由原本Duck的多态实现变成了Duck的组成部分描述行为的对象来提供，这中间通过行为接口多了一层间接，也就因此多了一些灵活度。在我的理解里，可以把类似Fly和Quack行为理解成一个人的胳膊，不用策略模式就像是不同的人有不同的胳膊，每个人的胳膊都连在躯干上，而用策略模式手就像是芭比娃娃的胳膊，可以通过组合装到不同的身上。策略模式很像是给胳膊加上了接口，可以更灵活地把不同的胳膊装到不同的芭比娃娃身上。

这种设计模式基于的一个抽象思考方式是Duck的行为也可以构成一个对象，行为也就是处理对象的方法也可以成为组成对象的一部分，而不是只能是成员函数。记住，操作对象对方式也可以成为组成对象的一部分。

### 3. 策略模式适用的场景

对象的某个成员函数如果可能有非常大的变化空间，可以把该成员函数描述的行为抽象成一个虚基类，成为该对象的成员。然后在改成员被实例化的时候给这个成员对象初始化成合适的子类对象。

