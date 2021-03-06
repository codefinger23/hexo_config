---
title: JS高程 第六章 面向对象程序设计
date: 2017-10-19 23:29:57
tags: [读书笔记, JavaScript高级程序设计]
---
> 本章讲述了在JavaScript中的面向对象编程，讲解了JavaScript通过自定义引用类型来实现类似类的概念，并通过借用构造函数与原型链实现继承。

<!--more-->

## 理解对象

面向对象编程最基本的就是自定义的类，也就是具有相同属性数据的集合体。在JavaScript中创建自定义对象的方式是通过Object类型，然后再为这个对象添加属性。对象的每个属性在创建时都带有一些特征值，JavaScript通过这些特征值来定义他们的行为。

### 属性类型

#### 数据属性

- [[Configurable]] 表示属性能否修改。默认值为true
- [[Enumerable]] 表示属性能否枚举，即通过for-in循环发现。默认值为true
- [[Writable]] 表示能否修改属性值。默认值为true
- [[Value]] 存储属性的数据值，读取属性值从这个位置读，写入属性时把新值保存在这个位置，默认值为undefined

可以通过Object.defineProperty()方法修改属性的默认特性

#### 访问器属性

- [[Configurable]] 表示属性能否修改。默认值为true
- [[Enumerable]] 表示属性是否可枚举。默认值为true
- [[Get]] 读取属性值时调用的函数。默认值为undefined
- [[Set]] 写属性值时调用的函数。默认值为undefined

通过getter与setter方法控制属性的访问权限，如不设置getter则属性不可读，不设置setter，则属性不可写

### 定义多个属性

可以通过Object.defineProperties() 方法一次定义对象的多个属性方法而不再需要一个一个调用Object.defineProperty()来改写

### 读取属性特性

通过Object.getOwnPropertyDescriptor()方法可以取得给定属性的描述符。返回值时一个对象，如果属性时访问器属性，则对象的属性为configurable,enumerable,get,set；如果时数据属性，这个对象的属性为configurable,enumerable,writable,value。

## 创建对象

虽然Object构造函数或对象字面量都可以用来创建单个对象，但这些方式有个明显的缺点：使用同一个接口创建多个对象，会产生大量的重复代码。为解决这个问题，首先引入工厂模式的变体。

### 工厂模式

通过工厂模式创建对象，可以减少大量的重复代码，但是工厂模式创建的代码不具有统一的类型，在进行判断对象类型的时候，所以需要另外的模式来创建。

### 构造函数模式

ECMAScript中的构造函数可以用来创建特定类型的对象。如Object和Array这样的原生类型，也可以创建自定义的构造函数。

构造函数与工厂模式的不同之处有

- 没有显示的创建对象，需要创建时进行new操作
- 直接将属性和方法赋给了this对象
- 没有return语句

这种方式调用构造函数会经过以下四个步骤

1. 创建一个新对象
2. 将构造函数的作用域赋给新对象
3. 执行构造函数中的代码
4. 返回新对象

创建自定义构造函数意味着将来可以将它的实例标识为一种特定的类型；这正是构造函数胜过工厂模式的地方。这种方式定义的构造函数时定义在全局对象中的。

#### 将构造函数当作函数

构造函数与其他函数的唯一区别就在于调用它们的方式不同。不过构造函数也是函数，不存在定义构造函数的特殊语法。任何函数，只要通过new操作符来调用，那么它就可以作为构造函数。

#### 构造函数的问题

构造函数的主要问题就是，每个方法都要在实例上重新创建，而实际上，这些方法并没有不同，也就是可以共享的，这就引进了另外一种创建模式

### 原型模式

前文已经说过，我们创建的每个函数都有一个prototype属性，这个属性时一个指针，只想一个对象，这个对象的用途时包含可以由特定类型的所有实例共享的属性和方法。如果按照字面意思来理解，那么prototype就是通过调用构造函数而创建的那个对象实例的原型函数。使用原型函数的好处在于可以让所有对象共享它所包含的属性和方法。也即是不必在构造函数中定义对象实例的信息，而是将这些信息添加到原型对象中，以此达到共享的目的。

#### 理解原型对象

只要创建一个函数，就会为这个函数创建prototype属性，这个属性指向函数的原型对象。默认情况下，原型对象自动获得一个constructor属性，这个属性指向prototype睡醒所在函数的指针。

上述说起来复杂，其实就是简单的双向关联，将原型对象与构造函数关联起来。每当代码读取某个对象的某个属性时，都会执行一次搜索，，目标是具有给定名字的属性。搜索首先从对象的实例开始。如果在实例中找到了具有给定名字的属性，则返回该属性的值；如果没有找到，则继续搜索指针指向的原型函数，如果在原型函数中找到了目标属性则返回，如果最终没有找到，则会报错。

> hasOwnProperty() 方法可以判断属性是否存在于实例中，存在则返回true
> hasPropertyProperty() 方法可以判断属性是否存在于原型中，存在则返回true

#### 原型与in操作符

使用in操作符的两种方式：单独使用和在for-in循环中使用。单独使用时会在通过对象能够访问给定属性时放回true，无论该属性是在实例中还是在原型对象中。

in操作符只能在对象属性可访问、可枚举时才会返回，屏蔽了原型中不可枚举的属性，要取得对象所有可枚举的实例属性，可以通过Object.keys()方法，该方法接收一个对象作为参数，返回包含所有可枚举属性的字符串数组。

#### 更简单的原型语法

不必为每添加一个方法就敲一遍Object.prototype。可以直接通过字面量赋值重写整个原型对象，但是这种方式也断开了原型对象与构造函数的关联，此时可以通过覆盖自动生成constructor属性来重新连接，因为之前曾经提过，在访问原型对象时，就是通过constructor属性来实现原型对象与构造函数的关联。

#### 原型的动态性

在原型对象中添加的属性与方法时被所有实例共享的，重写原型对象虽然很方便，但是在调用构造函数时也就访问不到我们重写的原型函数，所以在使用构造函数且重写原型对象时，而通过构造函数实例化对象在重写之后，重写的原型对象并不能生效。

#### 原型对象的问题

我们提过所有的原型对象都是共享的，而这也是造成问题的原型，所有的原型对象都变成了共享，虽然可以通过在实例中重写同名属性来覆盖原型中的属性，但这不是我们实例化的愿望相悖，所以最好的办法时组合使用构造函数与原型模式

### 组合使用构造函数模式和原型模式

构造函数模式用来定义实例属性，原型模式用来定义方法与共享属性。每个实例都有自己的一份实例属性副本，又共享对方法的引用，最大限度的节省了内存。

这种混合使用构造函数与原型模式的模式，时目前在ECMAScript中使用最广泛，认同度最高的一种创建自定义类型的方法，可以说，这是用来定义引用类型的一种默认模式。

### 动态原型模式

对立的构造函数和原型可能对造成面向对象语言的困惑，因为一般面向对象语言中，都是在一个函数中完成了共享方法和独立属性。动态原型模式就是将所有信息封装在构造函数总，通过在构造函数中初始化原型，解决了构造函数与原型独立的问题。通过在构造函数中使用if语句，判断是否已经初始化原型，如果没有初始化，则进行原型初始化，如果初始化过，就直接使用，已经是相当完美的方法。

### 寄生构造函数

寄生构造函数其实就是在使用构造函数的基础之上包含了工厂模式，返回通过用工厂模式创建的对象替换直接构造函数的对象，这种方式其实就是通过构造函数使用工厂模式，实例化的对象与构造函数也没有关系，是一种很蛋疼的方法，个人觉得多用于解耦与兼容。

### 稳妥构造函数模式

道格拉斯·克罗克福德发明了JavaScript中的稳妥对象概念。所谓稳妥对象，指的是没有公共属性，而且其方法也不引用this的对象。最适合在一些安全的环境中使用，或者防止数据被其他应用程序改动。稳妥构造函数和寄生构造函数类似，不同之处在于两点

- 新创建的对象实例方法不引用this
- 不适用new操作符调用构造函数

## 继承

许多面向对象语言都支持两种继承方式：接口继承和实现继承。接口继承只继承方法签名，而实现继承则继承实际的方法，如前所述，JavaScript没有函数签名，所以ECMAScript中无法实现接口继承，只支持实现继承。ECMAScript的实现继承主要通过原型链来实现

### 原型链

本章前面讲过，解释器在查找一个实例的时候先在实例中查找是否存在目标属性，如果没有则在原型对象中查找，而此时，如果我们让原型对象等于另外一个对象的实例，那么依旧会遵循这个规则，在实例中查找，再到原型中查找，通过原型指向实例来实现一个原型链。

#### 原型的默认类型

所有的原型默认类型都是Object，也就是说，其实我们一开始创建的原型对象，其实就是Object的一个实例。

#### 原型与实例的关系

通过两种凡是来确定原型与实例的关系

- 通过instanceof操作符，只要是再原型链中出现过指定的构造函数，就会返回true
- 通过isPrototypeOf方法，只要再原型链中出现过的原型，都可以说是该原型链所派生的实例的原型

#### 谨慎定义方法

给原型添加方法的代码需要放在替换原型之后，原因我们之前说过，如果再之前添加方法，则添加到自动创建的那个原型中去了。。

#### 原型链的问题

之前就说过的，原型链中的方法和属性是被共享的，所以这种方式实例的对象，所有属性其实都是共享的，而没有专属的对象，这与我们使用继承的初衷不符。这是我们就可以通过借用超类型的构造函数来实现实例属性

### 借用构造函数

通过在子类型的内部调用超类型的构造函数，利用在构造函数中继承实例属性，也是一种可行方案。

但是仅仅借用构造函数，所有的方法又变成了实例化的，无法共享，所以最终还是要组合是有构造和原型链

### 组合继承

组合继承就是将原型链和借用构造函数组合在一起，通过借用超类型的构造函数来继承实例化的属性，通过原型链来继承共享属性，是JavaScript中最为的行用的继承模式，而且也可以通过instanceof和isPrototypeOf来识别基于组合继承的对象，这种方式存在的问题是无论如何都会调用两次超类型的构造函数，一次是创建子类型的原型实例，一次是再子类型构造函数中调用。

### 原型式继承

道格拉斯·克罗克福德在2006年介绍了一种实现继承的方法，这种方法没有严格意义上使用构造函数。而是通过已有对象创建新对象的方式，通过在构造函数中实例化一个类型，然后将这个类型的原型对象指向传入的对象，最后返回这个创建的对象，从本质上来讲，对传入的对象完成了浅复制，让实例化的对象继承了传入的对象。

### 寄生式继承

寄生式继承与寄生构造函和工厂模式类似，就是创建一个仅用于封装集成过程的函数，然后在函数内部增强对象行为，然后再返回这个对象。

> 需要注意寄生式继承添加的方法会由于不能函数复用而降低效率

### 寄生组合式继承

组合继承是JavaScript最常用的继承模式；为了避免组合式继承调用多次构造函数的问题。基本思路就是不必为了指定子类型的原型而调用超类型的构造函数，我们所需要的无非就是超类型原型的一个副本而已。本质上就是使用寄生式继承来继承超类型的原型，然后将结果指定给子类型的原型，这个过程中就可以增强原型的行为。

## 小结

ECMAScript支持面向对象编程，但是不是用类或者接口。对象可以再代码执行过程中创建和增强，因此具有动态性而非严格意义上的实体。再没有类的情况下，可以采用下列模式创建对象。

- 工厂模式，利用函数创建对象，返回增加了属性和方法的对象
- 构造函数模式， 可以创建自定义引用类型，是有new操作符创建实例，但是不共享所有属性和方法
- 原型模式，同样可以创建自定义引用类型，但是所有属性和方法都会共享，合理的方式是通过构造函数模式创建实例属性，原型模式创建共享属性和方法

JavaScript中主要通过原型链实现继承。通过将原型指向某一类型的实例而串起来的原型链，这种方式会造成所有方法的共享，可以通过借用超类型的构造函数来定义实例属性和方法，通过这种组合继承是最为常用的继承模式，除此之外还有其他继承模式

- 原型式继承，通过指定对象的浅复制来生成新对象
- 寄生式继承，和原型式继承类似，可以解决组合继承由于多次调用超类型构造函数带来的效率问题
- 寄生组合式继承，集合寄生式继承和组合继承，是最有效的继承方式