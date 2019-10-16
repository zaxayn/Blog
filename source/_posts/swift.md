---
title: Swift
date: 2019-10-16 08:00:00
tags: [swift]
---

# 资源

官方文档：[Swift Docs](https://docs.swift.org/swift-book/)
感谢社区翻译的中文版：[Swift 中文](https://swiftgg.gitbook.io/swift/)

## [基础部分](https://swiftgg.gitbook.io/swift/swift-jiao-cheng/01_the_basics)

1.Swift 还增加了 Objective-C 中没有的高阶数据类型比如`元组（Tuple）`,元组可以让你创建或者传递一组数据，比如作为函数的返回值时，你可以用一个元组可以返回多个值。

2.`类型注解`需要在常量或者变量名后面加上一个`冒号和空格`，然后加上类型名称。

>一般来说你很少需要写类型注解。如果你在声明常量或者变量的时候赋了一个初始值，Swift 可以推断出这个常量或者变量的类型，请参考 类型安全和类型推断。

3.Swift `并不强制`要求你在每条语句的`结尾处使用分号`。

4.Swift 提供了8、16、32和64位的有符号和无符号整数类型。这些整数类型和 C 语言的命名方式很像，比如8位无符号整数类型是 UInt8，32位有符号整数类型是 Int32 。就像 Swift 的其他类型一样，整数类型采用大写命名法。

5.浮点数是`有小数部分`的数字，Double 表示64位浮点数，Float 表示32位浮点数。

6.类型别名（type aliases）就是给`现有类型定义另一个名字`
```
typealias AudioSample = UInt16
var maxAmplitudeFound = AudioSample.min
// maxAmplitudeFound 现在是 0
```

7.元组（tuples）把多个值组合成一个复合值。`元组内的值可以是任意类型`，并不要求是相同类型。(404, "Not Found") 元组把一个 Int 值和一个 String 值组合起来表示 HTTP 状态码的两个部分：一个数字和一个人类可读的描述。这个元组可以被描述为“一个类型为 (Int, String) 的元组”。

8.如果你只需要一部分元组值，分解的时候`可以把要忽略的部分用下划线（_）标记`
```
let (justTheStatusCode, _) = http404Error
print("The status code is \(justTheStatusCode)")
// 输出“The status code is 404”
```
>作为函数返回值时，元组非常有用。一个用来获取网页的函数可能会返回一个 (Int, String) 元组来描述是否获取成功。和只能返回一个类型的值比较起来，一个包含两个不同类型值的元组可以让函数的返回信息更有用。请参考 函数参数与返回值。

9.可选类型表示两种可能： 有值， 你可以解析可选类型访问这个值， 或者根本没有值.
```
var serverResponseCode: Int? = 404
// serverResponseCode 包含一个可选的 Int 值 404
serverResponseCode = nil
// serverResponseCode 现在不包含值
```
>nil 不能用于非可选的常量和变量。

10.一个 do 语句创建了一个新的包含作用域，使得错误能被传播到一个或多个 catch 从句。
```
func canThrowAnError() throws {
    // 这个函数有可能抛出错误
}
```
一个函数可以通过`在声明中`添加 throws 关键词来抛出错误消息。当你的函数能抛出错误消息时，你应该在表达式中`前置 try 关键词`
```
do {
    try canThrowAnError()
    // 没有错误消息抛出
} catch {
    // 有一个错误消息抛出
}
```

11.if let 使用可选绑定（optional binding）来判断可选类型是否包含值
```
if let actualNumber = Int(possibleNumber) {
    print("\'\(possibleNumber)\' has an integer value of \(actualNumber)")
} else {
    print("\'\(possibleNumber)\' could not be converted to an integer")
}
// 输出“'123' has an integer value of 123”
```
“如果 Int(possibleNumber) 返回的可选 Int 包含一个值，创建一个叫做 actualNumber 的新常量并将可选包含的值赋给它。”

12.使用断言进行调试
```
let age = -3
assert(age >= 0, "A person's age cannot be less than zero")
// 因为 age < 0，所以断言会触发
```
在这个例子中，只有 age >= 0 为 true 时，即 age 的值非负的时候，代码才会继续执行。如果 age 的值是负数，就像代码中那样，age >= 0 为 false，断言被触发，终止应用。