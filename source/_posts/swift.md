---
title: Swift
date: 2019-10-16 08:00:00
tags: [swift]
---

# 资源

官方文档：[Swift Docs](https://docs.swift.org/swift-book/)
中文社区翻译版：[Swift 文档](https://swiftgg.gitbook.io/swift/)

## 基础部分 [&](https://swiftgg.gitbook.io/swift/swift-jiao-cheng/01_the_basics)

1.Swift 包含了 C 和 Objective-C 上所有基础数据类型，Int 表示整型值； Double 和 Float 表示浮点型值； Bool 是布尔型值；String 是文本型数据。 Swift 还提供了三个基本的集合类型，Array、Set 和 Dictionary。

2.Swift 用字符串插值（string interpolation）的方式把常量名或者变量名当做占位符加入到长字符串中。
```
print("The current value of friendlyWelcome is \(friendlyWelcome)")
// 输出“The current value of friendlyWelcome is Bonjour!”
```
3.Double 表示64位浮点数。Float 表示32位浮点数，精度要求不高的话可以使用此类型。

4.一个二进制数，前缀是 0b，一个十六进制数，前缀是 0x。
```
let decimalInteger = 17
let binaryInteger = 0b10001       // 二进制的17
let octalInteger = 0o21           // 八进制的17
let hexadecimalInteger = 0x11     // 十六进制的17
```

5.typealias 给现有类型定义另一个名字
```
typealias AudioSample = UInt16
var maxAmplitudeFound = AudioSample.min
// maxAmplitudeFound 现在是 0
```

6.元组（tuples）,复合值，可以是任何类型，[&](https://swiftgg.gitbook.io/swift/swift-jiao-cheng/01_the_basics#tuples)
```
let http404Error = (404, "Not Found")
// http404Error 的类型是 (Int, String)，值是 (404, "Not Found")
```

7.可选类型和nil, if let（可选绑定）, 隐式解析可选类型 [&](https://swiftgg.gitbook.io/swift/swift-jiao-cheng/01_the_basics#implicityly-unwrapped-optionals)


8.错误处理：throws do catch
```
func makeASandwich() throws {
    // ...
}

do {
    try makeASandwich()
    eatASandwich()
} catch SandwichError.outOfCleanDishes {
    washDishes()
} catch SandwichError.missingIngredients(let ingredients) {
    buyGroceries(ingredients)
}
```

9.assert 断言, 如果断言为真，则代码继续执行。如果结果假，程序执行结束。
```
let age = -3
assert(age >= 0, "A person's age cannot be less than zero")
// 因为 age < 0，所以断言会触发
```