<h1><a href="https://www.codewars.com/users/artemiosdev">Codewars</a><img src="images/codewars.gif" height="44" align="right"></h1>

<a href="https://codewars.com/users/artemiosdev"><img src="https://codewars.com/users/artemiosdev/badges/micro" align="left"></img></a>

## 8 kyu

### [Sum The Strings](https://www.codewars.com/kata/5966e33c4e686b508700002d/swift)

Create a function that takes 2 integers in form of a string as an input, and outputs the sum (also as a string):

Example: `(Input1, Input2 -->Output)`

Notes:

- If either input is an empty string, consider it as zero.

- Inputs and the expected output will never exceed the signed 32-bit integer limit (2^31 - 1)

My solution:
```swift
func sum_str(_ a:String, _ b:String) -> String {
    let a = Int(a) ?? 0
    let b = Int(b) ?? 0
    let result = a + b
    return String(result)
}

print(sum_str(".","-9")) // -9
print(sum_str("8","-8")) // 0
print(sum_str("2","-")) // 2
print(sum_str(",","+")) // 0
```

Other solutions:
```swift
func sum_str(_ a:String, _ b:String) -> String {
    return String((Int(a) ?? 0) + (Int(b) ?? 0))
}
```

```swift
func sum_str(_ a:String, _ b:String) -> String {
    return String(convertStringToInt(a) + convertStringToInt(b))
}

func convertStringToInt(_ str: String) -> Int {
  return (str as NSString).integerValue
}
```

---

### [Multiplication table for number](https://www.codewars.com/kata/5a2fd38b55519ed98f0000ce/swift)

Your goal is to return multiplication table for number that is always an integer from 1 to 10.

My solution:
```swift
func multi_table(_ number: Int) -> String {
        var arrayResults: [String] = []
    for i in 1...10 {
        arrayResults.append("\(i) * \(number) = \(i * number)")
    }
    let result = arrayResults.joined(separator:"\n")
    return result
}
print(multi_table(5))
```

Other solutions:
```swift
func multi_table(_ number: Int) -> String {
    (1...10).map {"\($0) * \(number) = \($0 * number)"}.joined(separator: "\n")
}
print(multi_table(5))
```

```bash
1 * 5 = 5
2 * 5 = 10
3 * 5 = 15
4 * 5 = 20
5 * 5 = 25
6 * 5 = 30
7 * 5 = 35
8 * 5 = 40
9 * 5 = 45
10 * 5 = 50
```

---

### [Gravity Flip](https://www.codewars.com/kata/5f70c883e10f9e0001c89673/swift)

Examples (input -> output):

`'R', [3, 2, 1, 2]      ->  [1, 2, 2, 3]`

`'L', [1, 4, 5, 3, 5 ]  ->  [5, 5, 4, 3, 1]`

My solution:
```swift
func flip(_ direction: String, _ a: [Int]) -> [Int] {
    guard a.count > 1 else { return a }
    var newArray: [Int] = []
    if direction == "R" {
        newArray = a.sorted { $0 < $1 }
    } else if direction == "L" {
        newArray = a.sorted { $0 > $1 }
    }
    return newArray
}

print(flip("R", [3, 2, 1, 2]))    // [1, 2, 2, 3]
print(flip("L", [1, 4, 5, 3, 5])) // [5, 5, 4, 3, 1])
```

Mетод `.sort` сортирует оригинальный массив, а метод `sorted()` возвращает новый отсортированный массив, никак не изменяя старый.

---

### 



My solution:
```swift

```

Other solutions:
```swift

```

```swift

```

```bash

```

---

### 



My solution:
```swift

```

Other solutions:
```swift

```

```swift

```

```bash

```

---