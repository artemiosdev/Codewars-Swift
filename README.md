<!--
<h1><a href="https://www.codewars.com/users/artemiosdev">Codewars</a><img src="images/codewars.gif" height="44" align="right"></h1>
-->

<h1><a href="https://www.codewars.com/users/artemiosdev">Codewars</a><a href="https://gph.is/st/mqqDGdx"><img src="https://git.io/JMd4a" height="44" align="right"></a></h1>

<div>
<a href="https://codewars.com/users/artemiosdev"><img src="https://www.codewars.com/users/artemiosdev/badges/large" align="left"></img></a>
</div>
<br>
<hr>
<br>



### 8 kyu

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

### [Stringy Strings](https://www.codewars.com/kata/563b74ddd19a3ad462000054)

Write me a function stringy that takes a size and returns a string of alternating '1s' and '0s'.

The string should start with a 1.

A string with size 6 should return : `'101010'.

With size 4 should return : `'1010'`.

With size 12 should return : `'101010101010'`.

The size will always be positive and will only use whole numbers.

My solution:
```swift
func stringy(_ size: Int) -> String {
    var result = [String]()
    var i = 0
    while i < size {
        i += 1
        result.append("\(i % 2)")
    }
    return result.joined()
}

print(stringy(1)) // "1"
print(stringy(2)) // "10"
print(stringy(3)) // "101"
```

Other solutions:
```swift
func stringy(_ size: Int) -> String {
    if size % 2 == 0 {
        return String(repeating: "10", count: size / 2)
    } else {
        return "1" + String(repeating: "01", count: size / 2)
    }
}
```

```swift
func stringy(_ size: Int) -> String {
    var newString = ""
    for i in 1...size {
        newString += "\(i % 2)"
    }
    return newString
}
```


---

### [Is he gonna survive?](https://www.codewars.com/kata/59ca8246d751df55cc00014c)

A hero is on his way to the castle to complete his mission. However, he's been told that the castle is surrounded with a couple of powerful dragons! each dragon takes 2 bullets to be defeated, our hero has no idea how many bullets he should carry.. Assuming he's gonna grab a specific given number of bullets and move forward to fight another specific given number of dragons, will he survive?

Return True if yes, False otherwise 

My solution:
```swift
func hero(bullets: Int, dragons: Int) -> Bool {
    return bullets >= dragons * 2
}

print(hero(bullets: 4, dragons: 2)) // true
print(hero(bullets: 1, dragons: 3)) // false
print(hero(bullets: 11, dragons: 5)) // true
```

---

### [Get Planet Name By ID](https://www.codewars.com/kata/515e188a311df01cba000003)

The function is not returning the correct values. Can you figure out why?

Example (Input --> Output ):

`3 --> "Earth"`

My solution:
```swift
func getPlanetName(_ id: Int) -> String {
  var name:String
  switch id {
    case 1: 
      name = "Mercury"
    case 2: 
      name = "Venus"
    case 3: 
      name = "Earth"
    case 4: 
      name = "Mars"
    case 5: 
      name = "Jupiter"
    case 6: 
      name = "Saturn"
    case 7: 
      name = "Uranus"
    case 8: 
      name = "Neptune"
    default:
      name = ""
  } 
  return name
}
```

----

### [Quarter of the year](https://www.codewars.com/kata/5ce9c1000bab0b001134f5af)

Given a month as an integer from 1 to 12, return to which quarter of the year it belongs as an integer number.

For example: month 2 (February), is part of the first quarter; month 6 (June), is part of the second quarter; and month 11 (November), is part of the fourth quarter.

Constraint:

`1 <= month <= 12`

My solution:
```swift
func quarter(of month: Int) -> Int {
     switch month {
    case 1...3: return 1
    case 4...6: return 2
    case 7...9: return 3
    case 10...12: return 4
    default: print("error")
    }
  return month
}

print(quarter(of: 8)) // 3
print(quarter(of: 3)) // 1
print(quarter(of: 11)) // 4
```

Other solutions:
```swift
func quarter(of month: Int) -> Int {
    let months = [
        1: [1, 2, 3],
        2: [4, 5, 6],
        3: [7, 8, 9],
        4: [10, 11, 12]
    ]
    for (key, values) in months where values.contains(month) {
        return key
    }
    return 0
}
```

---

### [A wolf in sheep's clothing](https://www.codewars.com/kata/5c8bfa44b9d1192e1ebd3d15)

Warn the sheep in front of the wolf that it is about to be eaten. Remember that you are standing at the front of the queue which is at the end of the array:

`[sheep, sheep, sheep, sheep, sheep, wolf, sheep, sheep]      (YOU ARE HERE AT THE FRONT OF THE QUEUE)`

   `7      6      5      4      3            2      1`

If the wolf is the closest animal to you, return "Pls go away and stop eating my sheep". Otherwise, return "Oi! Sheep number N! You are about to be eaten by a wolf!" where N is the sheep's position in the queue.

Note: there will always be exactly one wolf in the array.

Examples:

`Input: ["sheep", "sheep", "sheep", "wolf", "sheep"]`

`Output: "Oi! Sheep number 1! You are about to be eaten by a wolf!"`

`Input: ["sheep", "sheep", "wolf"]`

`Output: "Pls go away and stop eating my sheep"`

My solution:
```swift
func warnTheSheep(_ queue: [String]) -> String {
    var alertString = ""
    let numberWolf = Array(queue.reversed()).firstIndex(where: { $0 == "wolf" })!
    if numberWolf > 0 {
        alertString = "Oi! Sheep number \(numberWolf)! You are about to be eaten by a wolf!"
    } else {
        alertString = "Pls go away and stop eating my sheep"
    }
    return alertString
}
```

Other solutions:
```swift
func warnTheSheep(_ queue: [String]) -> String {
    let num = queue.count - queue.firstIndex(of: "wolf")! - 1
    return num == 0
    ? "Pls go away and stop eating my sheep"
    : "Oi! Sheep number \(num)! You are about to be eaten by a wolf!"
}
```

```swift
func warnTheSheep(_ queue: [String]) -> String {
    let wolfIndex = queue.firstIndex(of: "wolf") ?? 0
    return queue.last == "wolf"
    ? "Pls go away and stop eating my sheep"
    : "Oi! Sheep number \(queue.count - wolfIndex - 1)! You are about to be eaten by a wolf!"
}

warnTheSheep(["sheep", "sheep", "sheep", "sheep", "sheep", "wolf", "sheep", "sheep"])
// "Oi! Sheep number 2! You are about to be eaten by a wolf!"

warnTheSheep(["sheep", "wolf", "sheep", "sheep", "sheep", "sheep", "sheep"])
// "Oi! Sheep number 5! You are about to be eaten by a wolf!"

warnTheSheep(["sheep", "sheep", "wolf"]) // "Pls go away and stop eating my sheep"

warnTheSheep(["wolf"]) // "Pls go away and stop eating my sheep"
```

---

### []()



My solution:
```swift

```

Other solutions:
```swift

```



