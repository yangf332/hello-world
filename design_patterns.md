设计模式
====================

### 
* 类与类之间有6种关系，其耦合度依次增强
  - 依赖 - - -> 不知道另一个类的属性和方法  参数、局部变量 
  - 关联 <----> 知道另一个类的属性和方法   成员变量
  - 聚合 <>--->                        成员变量
  - 组合 <.>--> 整体与部分
  - 继承 ----|>
  - 实现 - - -|>   
* 面向对象设计原则
  - 单一职责原则（Single Responsibility Principle）
  - 里氏替换原则（Liskov Substitution Principle）
  - 依赖倒置原则（Dependence Inversion Principle）
  - 接口隔离原则（Interface Segregation Principle）
  - 迪米特法则（Law Of Demeter）
  - 开闭原则（Open Close Principle）
  
### 23种设计模式

#### 创建型
* 单例模式
  - 定义：确保一个类只有一个实例，而且自行实例化并向整个系统提供这个实例
  - 优点：节省内存、全局访问、避免频繁的对象创建销毁
* 工厂方法模式
  - 简单工厂模式封装了对象实例化过程，去除客户端对具体产品的依赖，但违反了开闭原则
  - 为解决上个问题，工厂方法模式把对象实例化过程放在子类中实现
  - 新问题，将实例化哪个类的逻辑判断重新丢给了客户端。这个可以用反射解决
  - 新问题，类多多
* 抽象工厂模式
  - 是工厂方法的升级版。创建一组产品（产品族）
  - 问题：要增加一个新产品，几乎所有的工厂类都需要修改
* 建造者模式
  - 用来创建更复杂的对象，将创建过程独立为一个新指挥者类
* 原型模式
  - 提供一个方法复制自身


#### 行为类
* 模版方法
  - 父类写算法、步骤、流程；子类写每步骤具体实现
  - 子类影响父类，违反了里氏替换原则
* 中介者模式
  - 避免过度耦合。将多对多改为一对一关系
  - 问题：单点故障
* 观察者模式
  - 一个有添加、删除对象方法的类，而且可以循环调用所有添加对象的同一方法进行状态更新
  - 问题：轻度关联；观察者较多时，性能问题
* 访问者模式
* 命令模式
  - 调用者-》命令-》执行者；把调用者与执行者分开，同时可对中间命令环节执行排队或日志记录
* 职责链模式
  - 将请求发给一个连接多个对象的链，一环一环直到找到处理请求的对象
  - 问题：代码多，耦合高
* 策略模式
  - 用组合代替继承；方便切换策略；
  - 问题：要对客户端暴露所有策略类
* 迭代器模式
* 解释器模式
* 备忘录模式
* 状态模式

#### 结构型
* 代理模式
* 享元模式
* 外观模式
* 装饰者模式
  - 动态添加功能
* 组合模式
* 桥接模式
  - 一个实体有多个分类维度（不同颜色、不同形状等），可以分离为多个类，并使用组合方式

    
### 设计模式定义
     1	Abstract Factory（抽象工厂模式）：提供一个创建一系列相关或相互依赖对象的接口，而无需指定它们具体的类。
     2	Adapter（适配器模式）：将一个类的接口转换成客户希望的另外一个接口。Adapter模式使得原本由于接口不兼容而不能一起工作的那些类可以一起工作。     3	Bridge（桥接模式）：将抽象部分与它的实现部分分离，使它们都可以独立地变化。
     4	Builder（建造者模式）：将一个复杂对象的构建与它的表示分离，使得同样的构建过程可以创建不同的表示。
     5	Chain of Responsibility（责任链模式）：为解除请求的发送者和接收者之间耦合，而使多个对象都有机会处理这个请求。将这些对象连成一条链，并沿着这条链传递该请求，直到有一个对象处理它。
     6	Command（命令模式）：将一个请求封装为一个对象，从而使你可用不同的请求对客户进行参数化；对请求排队或记录请求日志，以及支持可取消的操作。
     7	Composite（组合模式）：将对象组合成树形结构以表示“部分-整体”的层次结构。它使得客户对单个对象和复合对象的使用具有一致性。
     8	Decorator（装饰模式）：动态地给一个对象添加一些额外的职责。就扩展功能而言， 它比生成子类方式更为灵活。
     9	Facade（外观模式）：为子系统中的一组接口提供一个一致的界面，Facade模式定义了一个高层接口，这个接口使得这一子系统更加容易使用。
    10	Factory Method（工厂模式）：定义一个用于创建对象的接口，让子类决定将哪一个类实例化。Factory Method使一个类的实例化延迟到其子类。
    11	Flyweight（享元模式）：运用共享技术有效地支持大量细粒度的对象。
    12	Interpreter（解析器模式）：给定一个语言, 定义它的文法的一种表示，并定义一个解释器, 该解释器使用该表示来解释语言中的句子。
    13	Iterator（迭代器模式）：提供一种方法顺序访问一个聚合对象中各个元素，而又不需暴露该对象的内部表示。
    14	Mediator（中介模式）：用一个中介对象来封装一系列的对象交互。中介者使各对象不需要显式地相互引用，从而使其耦合松散，而且可以独立地改变它们之间的交互。
    15	Memento（备忘录模式）：在不破坏封装性的前提下，捕获一个对象的内部状态，并在该对象之外保存这个状态。这样以后就可将该对象恢复到保存的状态。
    16	Observer（观察者模式）：定义对象间的一种一对多的依赖关系,以便当一个对象的状态发生改变时,所有依赖于它的对象都得到通知并自动刷新。
    17	Prototype（原型模式）：用原型实例指定创建对象的种类，并且通过拷贝这个原型来创建新的对象。
    18	Proxy（代理模式）：为其他对象提供一个代理以控制对这个对象的访问。
    19	Singleton（单例模式）：保证一个类仅有一个实例，并提供一个访问它的全局访问点。 单例模式是最简单的设计模式之一，但是对于Java的开发者来说，它却有很多缺陷。在九月的专栏中，David Geary探讨了单例模式以及在面对多线程（multi-threading）、类装载器（class loaders）和序列化（serialization）时如何处理这些缺陷。
    20	State（状态模式）：允许一个对象在其内部状态改变时改变它的行为。对象看起来似乎修改了它所属的类。
    21	Strategy（策略模式）：定义一系列的算法,把它们一个个封装起来, 并且使它们可相互替换。本模式使得算法的变化可独立于使用它的客户。
    22	Template Method（模板方法模式）：定义一个操作中的算法的骨架，而将一些步骤延迟到子类中。Template Method使得子类可以不改变一个算法的结构即可重定义该算法的某些特定步骤。
    23	Visitor（访问者模式）：表示一个作用于某对象结构中的各元素的操作。它使你可以在不改变各元素的类的前提下定义作用于这些元素的新操作。    

#### 案例
* 工厂方法

````
  $engine = new Engine();
  $wheel = new Wheel();
  // 客户端只使用car，不需要知道engine和wheel
  $car = new Car($engine, $wheel);
  // 工厂方法
  class Factory
  {
    public function create()
    {
      $car = new Car(new Engine(), new Wheel());
      return $car;
    }
  }
  // 客户端不知道engine和wheel了
  $factory = new Factory();
  $car = $factory->create();
````


### 相关资料

1. http://blog.csdn.net/zhengzhb/article/category/926691/2
2. http://baike.baidu.com/link?url=YQjWaxNboyW5L9yHV97lOynPaKOMeqiE_a8a5KxZT3c470VpZLKpJn5gaxSxCzMh0S2vJ4UyZP0XOINSZAhi3K


