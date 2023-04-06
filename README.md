<!--
<h1><a href="https://www.codewars.com/users/artemiosdev">Codewars</a><img src="images/codewars.gif" height="44" align="right"></h1>
-->

<h1><a href="https://www.codewars.com/users/artemiosdev">Codewars</a><a href="https://gph.is/st/mqqDGdx"><img src="https://git.io/JMd4a" height="44" align="right"></a></h1>

<div>
<a href="https://codewars.com/users/artemiosdev"><img src="https://www.codewars.com/users/artemiosdev/badges/large" align="left"></img></a>
<br>
</div>
<br>
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

Use [joined](https://developer.apple.com/documentation/swift/array/joined()) - Returns the elements of this sequence of sequences, concatenated.

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

### [Expressions Matter](https://www.codewars.com/kata/5ae62fcf252e66d44d00008e)

Given three integers `a ,b ,c`, return the largest number obtained after inserting the following operators and brackets: `+, *, ()`

In other words , try every combination of `a,b,c` with `[*+()]` , and return the Maximum Obtained

Example:

With the numbers are 1, 2 and 3 , here are some ways of placing signs and brackets:

```bash
1 * (2 + 3) = 5
1 * 2 * 3 = 6
1 + 2 * 3 = 7
(1 + 2) * 3 = 9
```

So the maximum value that you can obtain is 9.

Notes:

- The numbers are always positive.
- The numbers are in the range (1  ≤  a, b, c  ≤  10).
- You can use the same operation more than once.
- It's not necessary to place all the signs and brackets.
- Repetition in numbers may occur .
- You cannot swap the operands. For instance, in the given example you cannot get expression `(1 + 3) * 2 = 8`

**Input >> Output Examples:**

`expressionsMatter(1,2,3)  ==>  return 9`

Explanation:
After placing signs and brackets, the Maximum value obtained from the expression `(1+2) * 3 = 9`.

or 

`expressionsMatter(1,1,1)  ==>  return 3`
Explanation:
After placing signs, the Maximum value obtained from the expression is `1 + 1 + 1 = 3`.

or 

`expressionsMatter(9,1,1)  ==>  return 18`

`9 * (1+1) = 18`

My solution:
```swift
func expressionMatter(_ a: Int, _ b: Int, _ c: Int) -> Int {
    var results: [Int] = []
    results.append(a * (b + c))
    results.append(a * b * c)
    results.append(a + b * c)
    results.append((a + b) * c)
    results.append(a + b + c)
    return results.max()!
}

print(expressionMatter(2, 1, 2)) // 6
print(expressionMatter(2, 1, 1)) // 4
print(expressionMatter(1, 1, 1)) // 3
print(expressionMatter(1, 2, 3)) // 9
print(expressionMatter(1, 3, 1)) // 5
print(expressionMatter(2, 2, 2)) // 8
```

Other solutions:
```swift
func expressionMatter(_ a: Int, _ b: Int, _ c: Int) -> Int {
  return max(a + b + c, (a + b) * c, a * (b + c),  a * b * c)
}
```

```swift
func expressionMatter(_ a: Int, _ b: Int, _ c: Int) -> Int {
    let possibleValues = [
      a * (b + c),
      a * b * c,
      a + b * c,
      a * b + c,
      (a + b) * c,
      a + b + c
    ]
    return possibleValues.max() ?? 3
}
```

---

### [Century From Year](https://www.codewars.com/kata/5a3fe3dde1ce0e8ed6000097)

The first century spans from the year 1 up to and including the year 100, the second century - from the year 101 up to and including the year 200, etc.

Task:
Given a year, return the century it is in.

Examples:

```bash
1705 --> 18
1900 --> 19
1601 --> 17
2000 --> 20
```

My solution:
```swift
func century(_ year: Int) -> Int {
    if year < 100 {
        return 1
    } else if year % 100 == 0 {
        return year / 100
    }
    return (year / 100) + 1
}
```

Other solutions:
```swift
func century(_ year: Int) -> Int {
    let century = year % 100 == 0 ? (year / 100) : (year / 100) + 1
    return century
}
```

---

### [Reversed sequence](https://www.codewars.com/kata/5a00e05cc374cb34d100000d)

Build a function that returns an array of integers from n to 1 where n>0.

Example : `n=5 --> [5,4,3,2,1]`

My solution:
```swift
func reverseSeq(n: Int) -> [Int] {
    var result: [Int] = []
    for i in 1...n {
        result.append(i)
    }
    return result.reversed()
}
print(reverseSeq(n: 5)) //  [5,4,3,2,1]
```

Other solutions:
```swift
func reverseSeq(n: Int) -> [Int] {
  return (1...n).reversed()
}
// or
// подробнее func reversed() -> [Self.Element]
// 0(n)

func reverseSeq(n: Int) -> [Int] {
  let r = 1...n
  return r.reversed()
}
```

---

### [Get Nth Even Number](https://www.codewars.com/kata/5933a1f8552bc2750a0000ed)

Return the Nth Even Number

Example(Input --> Output)

```bash
1 --> 0 (the first even number is 0)
3 --> 4 (the 3rd even number is 4 (0, 2, 4))
100 --> 198
1298734 --> 2597466
```

The input will not be 0.

My solution:
```swift
func nthEven(_ n: Int) -> Int {
    return 2 * n - 2
}

print(nthEven(1))  // 0
print(nthEven(2))  // 2
print(nthEven(3))  // 4
print(nthEven(100))  // 198
print(nthEven(1298734))  // 2597466
```

---

### [Find the first non-consecutive number](https://www.codewars.com/kata/58f8a3a27a5c28d92e000144)

Your task is to find the first element of an array that is not consecutive.

By not consecutive we mean not exactly 1 larger than the previous element of the array.

E.g. If we have an array `[1,2,3,4,6,7,8]` then 1 then 2 then 3 then 4 are all consecutive but 6 is not, so that's the first non-consecutive number.

If the whole array is consecutive then `return null^2`.

The array will always have at least 2 elements^1 and all elements will be numbers. The numbers will also all be unique and in ascending order. The numbers could be positive or negative and the first non-consecutive could be either to

My solution:

```swift
func firstNonConsecutive (_ arr: [Int]) -> Int? {
    let sortedArray = arr.sorted()
    var result = sortedArray.first ?? 0
    for i in sortedArray {
        if i - result > 1 {
            result = i
            return result
        }
        result = i
    }
    if result == sortedArray.last {
        return nil
    } else {
        return result
    }
}
```

Other solutions:
```swift
func firstNonConsecutive (_ arr: [Int]) -> Int? {
    for i in 1..<arr.count where arr[i] - arr[i-1] > 1 {
        return arr[i]
    }
    return nil
}

print(firstNonConsecutive([1,2,3,4,6,7,8]))  // 6
```

---

### [Difference of Volumes of Cuboids](https://www.codewars.com/kata/58cb43f4256836ed95000f97)

In this simple exercise, you will create a program that will take two lists of integers, a and b. Each list will consist of 3 positive integers above 0, representing the dimensions of cuboids a and b. You must find the difference of the cuboids' volumes regardless of which is bigger.

For example, if the parameters passed are `([2, 2, 3], [5, 4, 1])`, the volume of a is 12 and the volume of b is 20. Therefore, the function should return 8.


My solution:
```swift
func findDifference(_ a: [Int], _ b: [Int]) -> Int {
    var sum1 = 1
    var sum2 = 1
    
    for i in a {
        sum1 *= i
    }
    for i in b {
        sum2 *= i
    }
    
    if sum1 >= sum2{
        return sum1 - sum2
    } else {
        return sum2 - sum1
    }
}
findDifference([3, 2, 5], [1, 4, 4]) // 14
findDifference([9, 7, 2], [5, 2, 2]) // 106
```

Use [reduce(_:_:)](https://developer.apple.com/documentation/swift/array/reduce(_:_:)) - Returns the result of combining the elements of the sequence using the given closure.

Other solutions:
```swift
func findDifference(_ a: [Int], _ b: [Int]) -> Int {
    return a.reduce(1,*) - b.reduce(1,*)
}
```

---

### [Simple multiplication](https://www.codewars.com/kata/583710ccaa6717322c000105)

This kata is about multiplying a given number by 8 if it is an even number and by 9 otherwise.

My solution:
```swift
func simpleMultiplication(_ num: Int) -> Int {
  return num % 2 == 0 ? num * 8 : num * 9
}
```

Other solutions:
```swift
func simpleMultiplication(_ num: Int) -> Int{
        return num * (num % 2 + 8)
}

// or

func simpleMultiplication(_ num: Int) -> Int {
  num.isMultiple(of: 2) ? num * 8 : num * 9 
}
```

---

### [Switch it Up!](https://www.codewars.com/kata/5808dcb8f0ed42ae34000031)

When provided with a number between 0-9, return it in words.

My solution:
```swift
func switchItUp(_ number: Int) -> String {
    switch number {
    case 0:
        return "Zero"
    case 1:
        return "One"
    case 2:
        return "Two"
    case 3:
        return "Three"
    case 4:
        return "Four"
    case 5:
        return "Five"
    case 6:
        return "Six"
    case 7:
        return "Seven"
    case 8:
        return "Eight"
    case 9:
        return "Nine"
    default:
        return "Wrong input"
    }
}

print(switchItUp(8)) // Eight
```

Other solutions:
```swift
func switchItUp(_ number: Int) -> String {
    let array = ["Zero", "One", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight", "Nine"]
    return array[number]
}
```

```swift
import Foundation 

func switchItUp(_ number: Int) -> String {
  let formatter = NumberFormatter()
  formatter.numberStyle = NumberFormatter.Style.spellOut
  return formatter.string(from: NSNumber(value: number))!.capitalized
}
```

```swift
import Foundation

func switchItUp(_ number: Int) -> String {
  return NumberFormatter.localizedString(from: number as NSNumber, number: .spellOut).capitalized
}
```

---

### [Beginner - Lost Without a Map](https://www.codewars.com/kata/57f781872e3d8ca2a000007e)

Given an array of integers, return a new array with each value doubled.

For example:

`[1, 2, 3] --> [2, 4, 6]`

My solution:
```swift
func maps(a : Array<Int>) -> Array<Int> {
    var array: [Int] = []
    for index in a {
        let newNumber = index + index
        array.append(newNumber)
    }
    return array
}
```

Other solutions:
```swift
func maps(a : Array<Int>) -> Array<Int> {
    return a.map { $0 * 2}
}
```

```swift
func maps(a : Array<Int>) -> Array<Int> {
  var result: [Int] = []
  for n in a {
     result.append(n*2)
  }
  return result
}
```

```swift
func maps(a : Array<Int>) -> Array<Int> {
  var b = a;
  for i in 0 ..< a.count {
    b[i] = a[i] * 2
  }
  return b;
}
```

---

### [Beginner - Reduce but Grow](https://www.codewars.com/kata/57f780909f7e8e3183000078)

Given a non-empty array of integers, return the result of multiplying the values together in order. Example:

`[1, 2, 3, 4] => 1 * 2 * 3 * 4 = 24`

My solution:
```swift
func grow(_ arr: [Int]) -> Int {
    var b = 1
    arr.forEach { index in
        b *= index
    }
    return b;
}
```

Other solutions:
```swift
func grow(_ arr: [Int]) -> Int {
  return arr.reduce(1,*)
}
```

```swift
func grow(_ arr: [Int]) -> Int {
    var product = 1
    for num in arr {
        product *= num
    }
    return product
}
```

---

### [To square(root) or not to square(root)](https://www.codewars.com/kata/57f6ad55cca6e045d2000627)

Write a method, that will get an integer array as parameter and will process every number from this array.

Return a new array with processing every number of the input-array like this:

If the number has an integer square root, take this, otherwise square the number.

Example

`[4,3,9,7,2,1] -> [2,9,3,49,4,1]`

Notes
The input array will always contain only positive numbers, and will never be empty or null.

My solution:
```swift
import Foundation

func squareOrSquareRoot(_ input: [Int]) -> [Int] {
      return input.map {
        let n = sqrt(Double($0))
        return n == Double(Int(n)) ? Int(n) : $0 * $0
    }
}

print(squareOrSquareRoot([4, 3, 9, 7, 2, 1])) // [2, 9, 3, 49, 4, 1]
```

Use [truncatingRemainder(dividingBy:)](https://developer.apple.com/documentation/swift/double/truncatingremainder(dividingby:)) - Returns the remainder of this value divided by the given value using truncating division.

Other solutions:
```swift
import Foundation

func squareOrSquareRoot(_ input: [Int]) -> [Int] {
    return input.map { i in
        let r = sqrt(Double(i))
        return r.truncatingRemainder(dividingBy: 1).isZero ? Int(r) : i * i
    }
}
```

Use [floor()](https://www.educative.io/answers/what-is-the-floor-function-in-swift)

```swift
func squareOrSquareRoot(_ input: [Int]) -> [Int] {
    var result = [Int]()
    for item in input {
        let square = Double(item).squareRoot()
        if floor(square) == square {
            result.append(Int(square))
        } else {
            result.append(item * item)
        }
    }
    return result
}
```

---

### [Sum Mixed Array](https://www.codewars.com/kata/57eaeb9578748ff92a000009)

Given an array of integers as strings and numbers, return the sum of the array values as if all were numbers.

Return your answer as a number.

My solution:
```swift
func sumMix(_ arr: [Any]) -> Int {
  var sum = 0
  for item in arr {
    if let test = item as? String {
      sum += Int(test)!
    } else {
        sum += item as! Int
    }
  }
  return sum
}

print(sumMix([9, 3, "7", "3"])) // 22
```

Other solutions:
```swift
func sumMix(_ arr: [Any]) -> Int {
    return arr.reduce(0) { $0 + (Int("\($1)") ?? 0) }
}
```

[compactMap(_:)](https://developer.apple.com/documentation/swift/sequence/compactmap(_:)) - Returns an array containing the non-nil results of calling the given transformation with each element of this sequence.

```swift
func sumMix(_ arr: [Any]) -> Int {
  return arr
          .compactMap { Int("\($0)") }
          .reduce(0,+)
}
```

```swift
func sumMix(_ arr: [Any]) -> Int {
  return arr.map{ $0 as? Int ?? Int($0 as? String ?? "0")! }.reduce(0, +)
}
```

---

### [Fake Binary](https://www.codewars.com/kata/57eae65a4321032ce000002d)

Given a string of digits, you should replace any digit below 5 with '0' and any digit 5 and above with '1'. Return the resulting string.

Note: input will never be an empty string

My solution:
```swift
func fakeBin(digits: String) -> String {
  var newString: String = ""
  for char in digits {
    if let number = Int(String(char)) {
      if(number < 5) {
        newString += "0"
      } else {
        newString += "1"
      }
    }
  }
  return newString
}
fakeBin(digits: "45385593107843568") // 01011110001100111
```

Other solutions:
```swift
func fakeBin(digits: String) -> String {
  return digits.map({$0 < "5" ? "0" : "1"}).joined()
}
```

```swift
func fakeBin(digits: String) -> String {
    digits.reduce("") { $0 + ("01234".contains($1) ? "0" : "1") }
    
// or
// digits.reduce("") { $0 + ($1 < "5" ? "0" : "1") }
}
```

---

### [You only need one - Beginner](https://www.codewars.com/kata/57cc975ed542d3148f00015b)

You will be given an array `a` and a value `x`. All you need to do is check whether the provided array contains the value.

The type of `a` and `x` can be `String` or `Int`.

Return true if the array contains the value, false if not.

My solution:
```swift
func check<T: Equatable>(_ a: [T], _ x: T) -> Bool {
    if a.contains(x) {
        return true
    } else {
        return false
    }
}
print(check(["t", "e", "s", "t"], "e")) //true
```

Other solutions:
```swift
func check<T: Equatable>(_ a: [T], _ x: T) -> Bool {
    return a.contains(x)
}

// or
func check<T: Equatable>(_ a: [T], _ x: T) -> Bool {
    return a.contains(where: { $0 == x})
}
```

---

### [Calculate BMI](https://www.codewars.com/kata/57a429e253ba3381850000fb)

Write function bmi that calculates body mass index (`bmi = weight / (height * height)`).

```bash
if bmi <= 18.5 return "Underweight"
if bmi <= 25.0 return "Normal"
if bmi <= 30.0 return "Overweight"
if bmi > 30 return "Obese"
```

My solution:
```swift
func bmi(_ weight: Int, _ height: Double) -> String {
    let bmiValue = Double(weight) / (height * height)
    var stringResult = ""
    if bmiValue <= 18.5 { stringResult = "Underweight" }
    else if bmiValue <= 25.0 { stringResult = "Normal" }
    else if bmiValue <= 30.0 { stringResult = "Overweight" }
    else if bmiValue > 30 { stringResult = "Obese"}
    return stringResult
}
```

Other solutions:
```swift
enum BMIKind: CustomStringConvertible {
    case underweight
    case normal
    case overweight
    case obese
    
    var description: String {
        switch self {
        case .underweight:
            return "Underweight"
        case .normal:
            return "Normal"
        case .overweight:
            return "Overweight"
        case .obese:
            return "Obese"
        }
    }

    init(bmiIndex: Double) {
        if bmiIndex <= 18.5 {
            self = .underweight
        } else if bmiIndex <= 25.0 {
            self = .normal
        } else if bmiIndex <= 30.0 {
            self = .overweight
        } else {
            self = .obese
        }
    }
}

struct BMIIndex {
    var rawValue: Double
    init(weight: Int, height: Double) {
        rawValue = Double(weight) / (height * height)
    }
}

func bmi(_ weight: Int, _ height: Double) -> String {
    let bmiIndex = BMIIndex(weight: weight, height: height)
    let bmiKind = BMIKind(bmiIndex: bmiIndex.rawValue)
    return bmiKind.description
}
```

---

### [String repeat](https://www.codewars.com/kata/57a0e5c372292dd76d000d7e)

Write a function that accepts an integer `n` and a string `s` as parameters, and returns a string of s repeated exactly `n` times.

Examples (input -> output)

```bash
6, "I"     -> "IIIIII"
5, "Hello" -> "HelloHelloHelloHelloHello"
```

My solution:
```swift
func repeatStr(_ n: Int, _ string: String) -> String {
    var repeatString = ""
    if n > 0 {
        for _ in 1...n {
            repeatString += string
        }
    }
    return repeatString
}

print(repeatStr(3, "Hello")) // HelloHelloHello
```

Other solutions:
```swift

func repeatStr(_ n: Int, _ string: String) -> String {
  return String(repeating: string, count: n)
}
```

---

### [Grasshopper - Personalized Message](https://www.codewars.com/kata/5772da22b89313a4d50012f7)

Create a function that gives a personalized greeting. This function takes two parameters: name and owner.

Use conditionals to return the proper message:

case	return

`name equals owner	-> 'Hello boss'`
`otherwise	-> 'Hello guest'`

My solution:
```swift
func great(_ name: String, _ owner: String) -> String {
    if name == owner {
        return "Hello boss"
    } else {
        return "Hello guest"
    }
}

print(great("Daniel", "Daniel")) // Hello boss
print(great("Greg", "Daniel")) // Hello guest
```

Other solutions:
```swift
func great(_ name: String, _ owner: String) -> String {
  return "Hello \(name == owner ? "boss" : "guest")"
}
```

```swift
func great(_ name: String, _ owner: String) -> String {
  return name == owner ? "Hello boss" : "Hello guest"
}
```

---

### [Sum of positive](https://www.codewars.com/kata/5715eaedb436cf5606000381)

You get an array of numbers, return the sum of all of the positives ones.

Example `[1,-4,7,12] => 1 + 7 + 12 = 20`

Note: if there is nothing to sum, the sum is default to 0.

My solution:
```swift
func sumOfPositives (_ numbers: [Int] ) -> Int {
    var result: Int = 0
  for index in numbers {
    if index > 0 {
      result += index
    } else {
      continue
    }
  }
    return result
}
sumOfPositives([1,2,3,4,5]) // 15
sumOfPositives([1,-2,3,4,5]) // 13
```

Other solutions:
```swift
func sumOfPositives (_ numbers: [Int] ) -> Int {
    var x = 0
    numbers.forEach {
        if $0 > 0 {
            x += $0
        }
    }
    return x
}
```

```swift
func sumOfPositives (_ numbers: [Int] ) -> Int {
    return numbers.filter{ $0 > 0 }.reduce(0, +)
}
```

```swift
func sumOfPositives (_ numbers: [Int] ) -> Int {
    return numbers.reduce (0) {$0 + max($1, 0)}
}
```

---

### [Count the Monkeys!](https://www.codewars.com/kata/56f69d9f9400f508fb000ba7)

Given the number `n`, populate an array with all numbers up to and including that number, but excluding zero.

For example(Input --> Output):

`10 --> [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]`

` 1 --> [1]`

My solution:
```swift
func monkeyCount(_ n: Int) -> [Int] {
    var results: [Int] = []
    for i in 1...n {
        results.append(i)
    }
    return results
}

monkeyCount(5) // [1, 2, 3, 4, 5]
```

Other solutions:
```swift
func monkeyCount(_ n: Int) -> [Int] {
  guard n > 0 else {return []}
    return Array(1...n)
}
```

```swift
func monkeyCount(_ n: Int) -> [Int] {
    return n > 0 ? [Int](1...n) : []
}
```

```swift
func monkeyCount(_ n: Int) -> [Int] {
  let monkeys = 1...n
  return [Int](monkeys)
}
```

---

### [Opposite number](https://www.codewars.com/kata/56dec885c54a926dcd001095)

Very simple, given an integer or a floating-point number, find its opposite.

Examples:

```bash
1: -1
14: -14
-34: 34
```

Use [abs(_:)](https://developer.apple.com/documentation/swift/abs(_:))

My solution:
```swift
func opposite(number: Double) -> Double {
  var result: Double = 0.0
  if number > 0 {
    result = -number
  } else {
    result = abs(number)
  }
  return result
}
```

Other solutions:
```swift
func opposite(number: Double) -> Double {
  return -number
}
```

---

### [Subtract the Sum](https://www.codewars.com/kata/56c5847f27be2c3db20009c3)

Complete the function which get an input number `n` such that `n >= 10` and `n < 10000`, then:

1. Sum all the digits of `n`.
2. Subtract the sum from `n`, and it is your new `n`.
3. If the new `n` is in the list below return the associated fruit, otherwise return back to task 1.

Example
```bash
n = 325
sum = 3+2+5 = 10
n = 325-10 = 315 (not in the list)
sum = 3+1+5 = 9
n = 315-9 = 306 (not in the list)
sum = 3+0+6 = 9
n =306-9 = 297 (not in the list)
.
.
.
```

...until you find the first n in the list below.

Use [compactMap(_:)](https://developer.apple.com/documentation/swift/sequence/compactmap(_:)) - Returns an array containing the non-nil results of calling the given transformation with each element of this sequence.

[.wholeNumberValue](https://developer.apple.com/documentation/swift/character/wholenumbervalue) - The numeric value this character represents, if it represents a whole number.

My solution:
```swift
func subtractSum(_ n: Int) -> String {
      let number = n - "\(n)".compactMap { Int(String($0)) }.reduce(0, +)
    switch number {
    case 9, 18, 27, 36, 45, 54, 63, 72, 81, 90, 99:
        return "apple"
    case 4, 6, 25, 29, 48, 50, 71, 73, 92, 94, 96:
        return "banana"
    case 20, 22, 41, 43, 62, 64, 66, 85, 87, 89:
        return "cherry"
    case 11, 13, 34, 55, 57, 59, 78, 80:
        return "cucumber"
    case 15, 17, 19, 38, 40, 61, 82, 84, 86:
        return "grape"
    case 1, 3, 24, 26, 47, 49, 68, 70, 91, 93:
        return "kiwi"
    case 5, 7, 28, 30, 32, 51, 53, 74, 76, 95, 97:
        return "melon"
    case 14, 16, 35, 37, 39, 58, 60, 83:
        return "orange"
    case 2, 21, 23, 42, 44, 46, 65, 67, 69, 88:
        return "pear"
    case 8, 10, 12, 31, 33, 52, 56, 75, 77, 79, 98, 100:
        return "pineapple"
    default:
        return subtractSum(number)
    }
}
```


Other solutions:
```swift
func subtractSum1(_ n: Int) -> String {
    let strN = String(n)
    let sum = strN.compactMap{$0.wholeNumberValue}.reduce(0, +)
    var subSum = n - sum
    
    while subSum >= 100 {
        var strN2 = String(subSum)
        var sum2 = strN2.compactMap{$0.wholeNumberValue}.reduce(0, +)
        
        subSum -= sum2
        
    }
    
    switch subSum {
    case 1,3,24,26,47,49,68,70,91,93: return "kiwi"
    case 2,21,23,42,44,46,65,67,69,88: return "pear"
    case 4,6,25,29,48,50,71,73,92,94,96: return "banana"
    case 5,7,28,30,32,51,53,74,76,95,97: return "melon"
    case 8,10,12,31,33,52,56,75,77,79,98,100: return "pineapple"
    case 9,18,27,36,45,54,63,72,81,90,99: return "apple"
    case 11,13,34,55,57,59,78,80: return "cucumber"
    case 14,16,35,37,39,58,60,83: return "orange"
    case 15,17,19,38,40,61,82,84,86: return "grape"
    case 20,22,41,43,62,64,66,85,87,89: return "cheryy"
    default: return ""
    }
}
```

```swift
func subtractSum(_ n: Int) -> String {
    let id: Int = n - "\(n)".compactMap { Int("\($0)") }.reduce(0, { $0 + $1 })
    return fruits[id] != nil ? fruits[id]! : subtractSum(id)
}

let fruits: [Int:String] = [
    1: "kiwi",
    2: "pear",
    3: "kiwi",
    4: "banana",
    5: "melon",
    6: "banana",
    7: "melon",
    8: "pineapple",
    9: "apple",
    10: "pineapple",
    11: "cucumber",
    12: "pineapple",
    13: "cucumber",
    14: "orange",
    15: "grape",
    16: "orange",
    17: "grape",
    18: "apple",
    19: "grape",
    20: "cherry",
    21: "pear",
    22: "cherry",
    23: "pear",
    24: "kiwi",
    25: "banana",
    26: "kiwi",
    27: "apple",
    28: "melon",
    29: "banana",
    30: "melon",
    31: "pineapple",
    32: "melon",
    33: "pineapple",
    34: "cucumber",
    35: "orange",
    36: "apple",
    37: "orange",
    38: "grape",
    39: "orange",
    40: "grape",
    41: "cherry",
    42: "pear",
    43: "cherry",
    44: "pear",
    45: "apple",
    46: "pear",
    47: "kiwi",
    48: "banana",
    49: "kiwi",
    50: "banana",
    51: "melon",
    52: "pineapple",
    53: "melon",
    54: "apple",
    55: "cucumber",
    56: "pineapple",
    57: "cucumber",
    58: "orange",
    59: "cucumber",
    60: "orange",
    61: "grape",
    62: "cherry",
    63: "apple",
    64: "cherry",
    65: "pear",
    66: "cherry",
    67: "pear",
    68: "kiwi",
    69: "pear",
    70: "kiwi",
    71: "banana",
    72: "apple",
    73: "banana",
    74: "melon",
    75: "pineapple",
    76: "melon",
    77: "pineapple",
    78: "cucumber",
    79: "pineapple",
    80: "cucumber",
    81: "apple",
    82: "grape",
    83: "orange",
    84: "grape",
    85: "cherry",
    86: "grape",
    87: "cherry",
    88: "pear",
    89: "cherry",
    90: "apple",
    91: "kiwi",
    92: "banana",
    93: "kiwi",
    94: "banana",
    95: "melon",
    96: "banana",
    97: "melon",
    98: "pineapple",
    99: "apple",
    100: "pineapple"
]
```

```swift
func subtractSum(_ n: Int) -> String {
    var count = n
    var sum = 0
    var newN = n
    var str = ""
    while newN > 0 {
        sum = String(count).compactMap( { $0.wholeNumberValue }).reduce(0, +)
        newN = newN - sum
        count = newN
        if newN > 0 && newN <= 100 {
            switch newN {
            case 1, 3, 24, 26, 47, 49, 68, 70, 91, 93: str = "kiwi"
            case 2, 21, 23, 42, 44, 46, 65, 67, 69, 88: str = "pear"
            case 4, 6, 25, 29, 48, 50, 71, 73, 92, 94, 96: str = "banana"
            case 5, 7, 28, 30, 32, 51, 53, 74, 76, 95, 97: str = "melon"
            case 8, 10, 12, 31, 33, 52, 56, 75, 77, 79, 98, 100: str = "pineapple"
            case 9, 18, 27, 36, 45, 54, 63, 72, 81, 90, 99: str = "apple"
            case 11, 13, 34, 55, 57, 59, 78, 80: str = "cucumber"
            case 14, 16, 35, 37, 39, 58, 60, 83: str = "orange"
            case 15, 17, 19, 38, 40, 61, 82, 84, 86: str = "grape"
            case 20, 22, 41, 43, 62, 64, 66, 85, 87, 89: str = "cherry"
            default: str = ""
            }
        }
    }
    return str
}
```

---

### [Transportation on vacation](https://www.codewars.com/kata/568d0dd208ee69389d000016)

Every day you rent the car costs $40. If you rent the car for 7 or more days, you get $50 off your total. Alternatively, if you rent the car for 3 or more days, you get $20 off your total.

Write a code that gives out the total amount for different days(d).

My solution:
```swift
func RentalCarCost(_ days: Int) -> Int {
    var result: Int = 0
    if days < 3 {
        result = days * 40
   }
    if days >= 3 && days < 7 {
         result = days * 40 - 20
    }
    if days >= 7 {
        result = days * 40 - 50
    }
    return result
}

RentalCarCost(1) // 40
RentalCarCost(2) // 80
RentalCarCost(3) // 100
RentalCarCost(4) // 140
RentalCarCost(5) // 180
RentalCarCost(7) // 230
```

Other solutions:
```swift
func RentalCarCost(_ days: Int) -> Int {
        let rentCostPerDay = 40
        var total = days * rentCostPerDay
        
        if days >= 7 {
            total -= 50
        } else if days >= 3 {
            total -= 20
        }
        return total
}
```

---

### [Get the mean of an array](https://www.codewars.com/kata/563e320cee5dddcf77000158)

Return the average of the given array rounded down to its nearest integer.

The array will never be empty.

My solution:
```swift
func getAverage(_ marks: [Int]) -> Int { 
  return marks.reduce(.zero, +) / marks.count
  // or
  // return marks.reduce(0) {($0 + $1)} / marks.count
}
getAverage([1,2,3,4,5,]) // 3
```

Other solutions:
```swift
func getAverage(_ marks: [Int]) -> Int {
    var sum = 0
    var count = 0
    for i in marks {
        sum += i
        count += 1
    }
    var average = sum / count
    return average //TODO : calculate the downwar rounded average of the marks array
}
```

---

### [Grasshopper - Terminal game move function](https://www.codewars.com/kata/563a631f7cbbc236cf0000c2)

Create a function for the terminal game that takes the current position of the hero and the roll (1-6) and return the new position.

Example:
`move(3, 6) should equal 15`

My solution:
```swift
func move(_ p: Int, _ r: Int) -> Int {
    return p + (r * 2)
}
```

---

### [Beginner Series #2 Clock](https://www.codewars.com/kata/55f9bca8ecaa9eac7100004a)

Clock shows `h` hours, `m` minutes and `s` seconds after midnight.

Your task is to write a function which returns the time since midnight in milliseconds.

Example:

```bash
h = 0
m = 1
s = 1
result = 61000
```

Input constraints:

```bash
0 <= h <= 23
0 <= m <= 59
0 <= s <= 59
```

My solution:
```swift
func past(_ h: Int, _ m: Int, _ s: Int) -> Int {
    return (h * 60 * 60 + m * 60 + s) * 1000
}
past(0, 1, 1) // 61000
past(1, 1, 1) // 3661000
```

---

### [Grasshopper - Summation](https://www.codewars.com/kata/55d24f55d7dd296eb9000030)

Write a program that finds the summation of every number from 1 to num. The number will always be a positive integer greater than 0.

For example (Input -> Output):

```bash
2 -> 3 (1 + 2)
8 -> 36 (1 + 2 + 3 + 4 + 5 + 6 + 7 + 8)
```

My solution:
```swift
func summation(_ n: Int) -> Int {
    return n * ( n + 1 ) / 2
    // or
    // return (1...n).reduce(0){ $0 + $1 }
}

summation(1) // 1
summation(8) // 36
summation(22) // 253
```

```swift
func summation(_ n: Int) -> Int {
         var answer = 0
         for number in 1...n { answer = answer + number }
         return answer
}
```

---

### [Grasshopper - Grade book](https://www.codewars.com/kata/55cbd4ba903825f7970000f5)

Complete the function so that it finds the average of the three scores passed to it and returns the letter value associated with that grade.

```bash
Numerical Score	Letter Grade
90 <= score <= 100  ->	'A'
80 <= score < 90  ->	'B'
70 <= score < 80  ->	'C'
60 <= score < 70  ->	'D'
0 <= score < 60  ->	'F'
```

Tested values are all between 0 and 100. Theres is no need to check for negative values or values greater than 100.

My solution:
```swift
func getGrade(_ s1: Int, _ s2: Int, _ s3: Int) -> String {
    let score = (s1 + s2 + s3) / 3
    var result: String = ""
    if score >= 90 && score <= 100 {
        result = "A"
    }
    if score >= 80 && score < 90 {
        result = "B"
    }
    if score >= 70 && score < 80 {
        result = "C"
    }
    if score >= 60 && score < 70 {
        result = "D"
    }
    if score < 60 {
        result = "F"
    }
    return result
}

getGrade(95,90,93) // A
getGrade(82,85,87) // B
getGrade(75,70,79) // C
getGrade(65,70,59) // D
getGrade(58,59,60) // F
```

Other solutions:
```swift
func getGrade(_ s1: Int, _ s2: Int, _ s3: Int) -> String {
  var sum = (s1 + s2 + s3) / 3
  switch sum {
    case 90...100:
      return "A"
    case 80..<90:
      return "B"
    case 70..<80:
      return "C"
    case 60..<70:
      return "D"
    default:
      return "F"
  }
}
```

---

### [Grasshopper - Check for factor](https://www.codewars.com/kata/55cbc3586671f6aa070000fb)

This function should test if the factor is a factor of base.

Return `true` if it is a factor or `false` if it is not.

Factors are numbers you can multiply together to get another number.

2 and 3 are factors of 6 because: `2 * 3 = 6`

You can find a factor by dividing numbers. If the remainder is 0 then the number is a factor.
You can use the mod operator (%) in most languages to check for a remainder
For example 2 is not a factor of 7 because: `7 % 2 = 1`

Note: base is a non-negative number, factor is a positive number.

Проверка с оператором целочисленного деления (a % b) показывает, какое количество b помещается внутри a, и возвращает остаток деления a на b. 

Чтобы получить результат деления a % b, оператор % вычисляет следующее выражение и возвращает остаток:

`a = (b × множитель) + остаток`

где множитель показывает, сколько раз целых `b` содержится в `a`.

Подставляя в это выражение 9 и 4, получим:

`9 = (4 × 2) + 1`

My solution:
```swift
func checkForFactor(_ base: Int, _ factor: Int) -> Bool {
    return base % factor == 0
    // or
    // return base.isMultiple(of: factor)
}

checkForFactor(10, 2)    // true
checkForFactor(24612, 3) // true
checkForFactor(9, 2)     // false
checkForFactor(653, 7)   // false
```

```swift
let checkForFactor: (_ base: Int, _ factor: Int) -> Bool = { $0 % $1 == 0 }
```

---

### [Grasshopper - Messi Goals](https://www.codewars.com/kata/55ca77fa094a2af31f00002a)

My solution:
```swift
var laLigaGoals = 43
var championLeagueGoals = 10
var copaDelReyGoals = 5

var totalGoals = laLigaGoals + championLeagueGoals + copaDelReyGoals
```

---

### [Returning Strings](https://www.codewars.com/kata/55a70521798b14d4750000a4)

My solution:
```swift
func greet(_ name: String) -> String {
  return "Hello, \(name) how are you doing today?"
}
```

---

### [Dollars and Cents](https://www.codewars.com/kata/55902c5eaa8069a5b4000083)

`3.1 needs to become $3.10`

My solution:
```swift
func formatMoney(_ val:Double) -> String {
    return String(format: "$%.02f", val)
}

formatMoney(0) // $0.00
formatMoney(3) // $3.00
formatMoney(5.1000000) // $5.10
formatMoney(123456789.166666) // $123456789.17
```

---

### [Convert number to reversed array of digits](https://www.codewars.com/kata/5583090cbe83f4fd8c000051)

Given a random non-negative number, you have to return the digits of this number within an array in reverse order.

Example (Input => Output):

`35231 => [1,3,2,5,3]`

`0 => [0]`

My solution:
```swift
func digitize(_ num: Int) -> [Int] {
    guard num > 0 else {
        return [0]
    }
    var result: [Int] = []
    var i = num
    while i != 0 {
    // добавляет в конец пустого массива
        result.append(i % 10)
        i = i / 10
    }
    return result
}

digitize(348597) // [7,9,5,8,4,3]
```

Other solutions:
```swift
func digitize(_ num:Int) -> [Int] {
  return "\(num)".map{$0.wholeNumberValue!}.reversed()
  
//  or
//  return String(num).compactMap { Int(String($0)) }.reversed()

//  return String(num).compactMap {$0.wholeNumberValue}.reversed()
}
```

---

### [Is n divisible by x and y?](https://www.codewars.com/kata/5545f109004975ea66000086)

Create a function that checks if a number `n` is divisible by two numbers `x AND y`. All inputs are positive, non-zero numbers.

Examples:
```bash
1) n =   3, x = 1, y = 3 =>  true because   3 is divisible by 1 and 3
2) n =  12, x = 2, y = 6 =>  true because  12 is divisible by 2 and 6
3) n = 100, x = 5, y = 3 => false because 100 is not divisible by 3
4) n =  12, x = 7, y = 5 => false because  12 is neither divisible by 7 nor 5
```

My solution:
```swift
func isDivisible(_ n: Int, _ x: Int, _ y: Int) -> Bool {
    if n % x == 0 && n % y == 0 {
        return true
    }
    return false
}

print(isDivisible(100, 5, 10)) // true
print(isDivisible(100, 5, 3)) // false
```

Other solutions:
```swift
func isDivisible(_ n: Int, _ x: Int, _ y: Int) -> Bool {
    return n.isMultiple(of: x) && n.isMultiple(of: y)
}
```

---

### [Convert a Boolean to a String](https://www.codewars.com/kata/551b4501ac0447318f0009cd)

My solution:
```swift
func booleanToString(_ b: Bool) -> String {
  return "\(b)"
  
  // or
  // return String(b)
}
```

Other solutions:
```swift
let booleanToString: (Bool) -> String = { "\($0)" }
```

---

### [Enumerable Magic #25 - Take the First N Elements](https://www.codewars.com/kata/545afd0761aa4c3055001386)

Create a function take that takes an Array Int and an Int, n, and returns an Array Int containing the first up to n elements from the array.

My solution:
```swift
func take(_ arr: [Int], _ n: Int) -> [Int] {
    var result: [Int] = []
    var count = 0
    for index in arr {
        if count < n {
            count += 1
            result.append(index)
        }
    }
    return result
}

take([0, 1, 2, 3, 5, 8, 13], 3) // [0, 1, 2]
take([0, 1, 2, 3, 5, 8, 13], 0) // []
```

Other solutions:
```swift
func take(_ arr: [Int], _ n: Int) -> [Int] {
    return Array(arr.prefix(n))
}
```

```swift
func take(_ arr: [Int], _ n: Int) -> [Int] {
  return arr.count > n ? Array(arr[0..<n]) : arr
}
```

---

### [Even or Odd](https://www.codewars.com/kata/53da3dbb4a5168369a0000fe)

Create a function that takes an integer as an argument and returns "Even" for even numbers or "Odd" for odd numbers.

My solution:
```swift
func evenOrOdd(_ number:Int) -> String {
  if number % 2 == 0 {
    return "Even"
  }
  return "Odd"
}
```

Other solutions:
```swift
func evenOrOdd(_ number:Int) -> String {
  return number % 2 == 0 ? "Even" : "Odd"
}
```

```swift
func evenOrOdd(_ n: Int) -> String {
    return n.isMultiple(of: 2) ? "Even" : "Odd"
}
```

---

### [Convert boolean values to strings 'Yes' or 'No'.](https://www.codewars.com/kata/53369039d7ab3ac506000467)

```swift
func boolToWord(_ bool: Bool) -> String {
  return bool ? "Yes" : "No"
}
```

---

### [Convert a Number to a String!](https://www.codewars.com/kata/5265326f5fda8eb1160004c8)

```swift
func numberToString(number: Int) -> String { 
  return "\(number)"
  // or
  // return number.description
  // return String(number)
}
```

---

### [Kata Example Twist](https://www.codewars.com/kata/525c1a07bb6dda6944000031)

Add the value "codewars" to the array websites/Websites 1,000 times.

```swift
var websites = Array(repeating: "codewars", count: 1000)
```

---

### [Function 1 - hello world](https://www.codewars.com/kata/523b4ff7adca849afe000035)

```swift
func greet() -> String {
  return "hello world!"
}
```

---

### [Reversed Strings](https://www.codewars.com/kata/5168bb5dfe9a00b126000018)

Complete the solution so that it reverses the string passed into it.

```bash
'world'  =>  'dlrow'
'word'   =>  'drow'
```

My solution:
```swift
func reverse(_ str: String) -> String {
    let reversedWord = String(str.reversed())
    return reversedWord
}

reverse("hello") // "olleh"
reverse("rat") // "tar"
```

---

### [Square(n) Sum](https://www.codewars.com/kata/515e271a311df0350d00000f)

Complete the square sum function so that it squares each number passed into it and then sums the results together.

My solution:
```swift
func squareSum(_ vals: [Int]) -> Int {
    var result: Int = 0
    for index in vals {
        let mult = index * index
        result += mult
    }
    return result
}

squareSum([1, 2]) //  5
squareSum([3, 4]) // 25
```

Other solutions:
```swift
func squareSum(_ vals: [Int]) -> Int {
  return vals.reduce(0) { $0 + $1 * $1 }
}
```

```swift
func squareSum(_ vals:[Int]) -> Int {
  return vals.map{ $0 * $0 }.reduce(0, +)
}
```

## 7kue

---

### [Valid Parentheses](https://www.codewars.com/kata/6411b91a5e71b915d237332d)

Write a function that takes a string of parentheses, and determines if the order of the parentheses is valid. The function should return true if the string is valid, and false if it's invalid.

Examples

```bash
"()"              =>  true
")(()))"          =>  false
"("               =>  false
"(())((()())())"  =>  true
```

Constraints

`0 <= length of input <= 100`

All inputs will be strings, consisting only of characters ( and ).
Empty strings are considered balanced (and therefore valid), and will be tested.

My solution:
```swift
func validParentheses(_ str: String) -> Bool {
    var answer = 0
    for i in str {
        answer = i == "(" ? answer + 1 : answer - 1
        if answer < 0 {
            return false
        }
    }
    return answer == 0
}

validParentheses("()") // true
validParentheses("((()))") // true
validParentheses(")()()(") // false
validParentheses("((((") // false
validParentheses("))))") // false
validParentheses("()()()") // true
```

Other solutions:

```swift
func validParentheses(_ str: String) -> Bool {
 var counter = 0
    
    for element in str {
        if element == "(" {
            counter += 1
        } else if element == ")" {
            counter -= 1
        }
        if counter < 0 {
            return false
        }
    }
    return counter == 0
}
```

```swift
func validParentheses(_ str: String) -> Bool {
    var openParentheses: [Character] = []
    for character in str {
        if character == "("{
            openParentheses.append(character)
        } else if character == ")" {
            guard openParentheses.last == "(" else { return false }
            openParentheses.removeLast()
        }
    }
    return openParentheses.isEmpty
}
```

Нет необходимости вставлять закрывающие скобки в стек. В нашем стеке будут храниться только открывающие скобки.
Используйте словарь для хранения закрывающих скобок в качестве ключей и открывающих скобок в качестве значений. Мы будем использовать это для сопоставления скобок.

Если стек пуст и если символ является открывающей скобкой, добавьте его в стек.
Если символ является закрывающей скобкой и он совпадает с открывающей скобкой в верхней части стека, удалите скобку из верхней части стека.

Если символ является закрывающей скобкой, и он не совпадает с открывающей скобкой в верхней части стека, верните значение false. Логика: Соответствующая открывающая скобка не существует, и поэтому она недопустима.

В противном случае добавьте открывающую скобку к стеку.
В конце мы возвращаем true, если в стеке не осталось открывающих скобок.

```swift
// variable solution with different brackets
func validParentheses(_ str: String) -> Bool {
    var stack: [Character] = []
    let bracketMatch: [Character: Character] = [")": "(", "}": "{", "]": "["]
    for char in str {
        if let last = stack.last, last == bracketMatch[char] {
            stack.removeLast()
        } else {
            switch char {
            case ")", "}", "]":
                return false
            default:
                stack.append(char)
            }
        }
    }
    return stack.count == 0
}
```

---

### [The 'spiraling' box](https://www.codewars.com/kata/63b84f54693cb10065687ae5)

Given two positive integers m (width) and n (height), fill a two-dimensional list (or array) of size m-by-n in the following way:

- All the elements in the first and last row and column are 1.
- All the elements in the second and second-last row and column are 2, excluding the elements from step 1.
- All the elements in the third and third-last row and column are 3, excluding the elements from the previous steps.

Given `m = 10`, `n = 9`, your function should return

```bash
[[1, 1, 1, 1, 1, 1, 1, 1, 1, 1],
 [1, 2, 2, 2, 2, 2, 2, 2, 2, 1],
 [1, 2, 3, 3, 3, 3, 3, 3, 2, 1], 
 [1, 2, 3, 4, 4, 4, 4, 3, 2, 1], 
 [1, 2, 3, 4, 5, 5, 4, 3, 2, 1], 
 [1, 2, 3, 4, 4, 4, 4, 3, 2, 1], 
 [1, 2, 3, 3, 3, 3, 3, 3, 2, 1], 
 [1, 2, 2, 2, 2, 2, 2, 2, 2, 1], 
 [1, 1, 1, 1, 1, 1, 1, 1, 1, 1]]
```

My solution:
```swift
func createBox(_ m: Int, _ n: Int) -> [[Int]] {
    var matrix = Array(repeating: Array(repeating: 0, count: m), count: n)
    for i in 0..<n {
        for j in 0..<m {
            let minIndex = min(i,j,n-i-1,m-j-1)
            matrix[i][j] = minIndex+1
        }
    }
    return matrix
}

print(createBox(5, 8))
// [[1, 1, 1, 1, 1], 
// [1, 2, 2, 2, 1], 
// [1, 2, 3, 2, 1], 
// [1, 2, 3, 2, 1], 
// [1, 2, 3, 2, 1], 
// [1, 2, 3, 2, 1], 
// [1, 2, 2, 2, 1], 
// [1, 1, 1, 1, 1]]
```

Other solutions:
```swift
func createBox(_ m: Int, _ n: Int) -> [[Int]] {
  (0..<n).map { i in (0..<m).map { j in min(i, j, n - i - 1, m - j - 1) + 1 } }
}
```

---

### [Functional Addition](https://www.codewars.com/kata/538835ae443aae6e03000547)

Create a function `add(n) / Add(n)` which returns a function that always adds n to any number

```bash
addOne = add(1)
addOne(3) // 4
```

My solution:
```swift
func add(_ n: Int) -> ((Int) -> Int) { 
  func Add(_ y: Int) -> Int {
    return n + y
  }
  return Add
}

add(1)(3) // 4, "add(1)(3) does not equal 4")
add(2)(2) // 4, "add(2)(2) does not equal 4")
```

Other solutions:
```swift
func add(_ n: Int) -> ((Int) -> Int) { 
	return { return $0 + n }
}
```


---

### [Disemvowel Trolls](https://www.codewars.com/kata/52fba66badcd10859f00097e)

Your task is to write a function that takes a string and return a new string with all vowels removed.

For example, the string `This website is for losers LOL!` would become `Ths wbst s fr lsrs LL!`.

Note: for this kata `y` isn't considered a vowel.

My solution:
```swift
func disemvowel(_ s: String) -> String {
    var result = ""
    for index in s {
        switch index {
        case "a":
            continue
        case "A":
            continue
        case "e":
            continue
        case "E":
            continue
        case "i":
            continue
        case "I":
            continue
        case "o" :
            continue
        case "O":
            continue
        case "u":
            continue
        case "U":
            continue
        default:
            result.append(index)
        }
    }
    return result
}
disemvowel("This website is for losers LOL!") // Ths wbst s fr lsrs LL!
```

[replacingOccurrences(of:with:)](https://developer.apple.com/documentation/foundation/nsstring/1412937-replacingoccurrences) - Returns a new string in which all occurrences of a target string in the receiver are replaced by another given string.

In "of" he's specifying the chars he wants to replace, replacing them with "" (empty string, so, nothing) and than he's specifing in the options that the chars to remove have to be read as a regularExpression and that they are NOT case sensitive, so even uppercased vowels char will be removed.

Other solutions:
```swift
func disemvowel(_ s: String) -> String {
  return s.replacingOccurrences(of: "[aeiou]", with: "", options: [.regularExpression, .caseInsensitive])
}
```

```swift
let vowels = Set("aeiouAEIOU")

func disemvowel(_ s: String) -> String {
    return s.filter { !vowels.contains($0) }
}

// or
func disemvowel(_ s: String) -> String {
  let vowels: [Character] = ["a", "e", "i", "o", "u", "A", "E", "I", "O", "U"]
  
  return String(s.characters.filter { !vowels.contains($0) })
}
```

---

### [Jaden Casing Strings](https://www.codewars.com/kata/5390bac347d09b7da40006f6)

Преобразовать строку, где каждое слово с заглавной буквы

My solution:
```swift
import Foundation

extension String {
    func toJadenCase() -> String {
      var toJadenCase: String {self.capitalized}
      return toJadenCase
    }
}
// "How can mirrors be real if our eyes aren't real",
// "How Can Mirrors Be Real If Our Eyes Aren't Real"
```

Other solutions:
```swift
import Foundation

extension String {
    func toJadenCase() -> String {
      let arr = self.components(separatedBy: " ")
      let cArr = arr.map { $0.prefix(1).uppercased() + $0.lowercased().dropFirst() }
      return cArr.joined(separator: " ")
    }
}
```


---

### [Credit Card Mask](https://www.codewars.com/kata/5412509bd436bd33920011bc)

Your task is to write a function maskify, which changes all but the last four characters into `#`.

Examples

```bash
maskify("4556364607935616") // should return "############5616"
maskify("64607935616")      // should return "#######5616"
maskify("1")                // should return "1"
maskify("")                 // should return ""

// "What was the name of your first pet?"
maskify("Skippy")                                   // should return "##ippy"
maskify("Nananananananananananananananana Batman!") // should return "####################################man!"
```

[init(repeating:count:)](https://developer.apple.com/documentation/swift/string/2427723-init) - Creates a new string representing the given string repeated the specified number of times.

[suffix(_:)](https://developer.apple.com/documentation/swift/array/suffix(_:)) - Returns a subsequence, up to the given maximum length, containing the final elements of the collection

My solution:

```swift
func maskify(_ string:String) -> String {
  if string.count < 5 {
    return string
  }  else {
    return String(repeating: "#", count: string.count - 4) + String(string.suffix(4))
  }
}

maskify("4556364607935616") // ############5616
```

```swift
func maskify(_ string: String) -> String {
    guard string.count > 4 else { return string }
    return .init(repeating: "#", count: string.count-4) + string.suffix(4)
}
```

[repeatElement(_:count:)](https://developer.apple.com/documentation/swift/1641513-repeatelement) - Creates a collection containing the specified number of the given element.

Other solutions:
```swift
func maskify(_ string: String) -> String {
    guard string.count > 4 else { return string }
    var str = "", i = 0
    while i < string.count - 4 {
        str += repeatElement("#", count: i).repeatedValue
        i = i + 1
    }
    return str + string.suffix(4)
}
```

[enumerated()](https://developer.apple.com/documentation/swift/array/enumerated()) - Returns a sequence of pairs (n, x), where n represents a consecutive integer starting at zero and x represents an element of the sequence.

```swift
import Foundation

func maskify(_ string:String) -> String {
  string.enumerated().map { $0 < string.count - 4 ? "#" : "\($1)"}.joined()
}
```


---

### [Triangular Treasure](https://www.codewars.com/kata/525e5a1cb735154b320002c8)

You need to return the nth triangular number. You should return 0 for out of range values:

Треугольные числа называются так из-за равносторонней треугольной формы, которую они занимают, когда расположены точками.

For example: (Input --> Output)

```
0 --> 0
2 --> 3
3 --> 6
-10 --> 0
```

My solution:
```swift
func triangular(_ n: Int) -> Int{
    if n <= 0 {
        return 0
    }
    var counter = 0
    for i in 0...n {
        counter += i
    }
    return counter
}

triangular(3) // 6
triangular(4) // 10
triangular(-10) // 0
triangular(5) // 15
```

Other solutions:
```swift
func triangular(_ n: Int) -> Int{
    if  n < 0 {
        return 0
    }
    let sum = n * (n + 1) / 2
    return sum
}

triangular(3) // 6
triangular(4) // 10
triangular(-10) // 0
```

```swift
func triangular(_ n: Int) -> Int{
 return n > 0 ? (1...n).reduce(0,+) : 0
}
triangular(3) // 6 -> 0 + 1 + 2 + 3
triangular(4) // 10 -> 0 + 1 + 2 + 3 + 4
```

```swift
func triangular(_ n: Int) -> Int{
  if (n < 0){
   return 0
  }
  return n + triangular(n - 1)
}
```


---

### [Binary Calculator](https://www.codewars.com/kata/546ba103f0cf8f7982000df4)

Вам нужно написать функцию, которая будет получать две строки (n1 и n2), каждая из которых представляет целое число, в виде двоичного числа. Будет предоставлен третий параметр (o) в виде строки, представляющей один из следующих операторов: сложение, вычитание, умножение. Ваша задача состоит в том, чтобы написать функцию вычисления так, чтобы она выполняла арифметические действия, а возвращаемый результат должен быть строкой, представляющей двоичный результат.

```bash
1 + 1 === 10
10 + 10 === 100
1 - 10 === -1
10 - 100 === -10
```

Отрицательным двоичным числам обычно предшествует несколько единиц. Для этой ката отрицательные числа могут быть представлены отрицательным символом в начале строки.

My solution:
```swift
enum Operator {
    case ADD, SUBTRACT, MULTIPLY
}

func calculate(_ a: String, _ b: String, _ op: Operator) -> String {
    guard let a = Int(a, radix: 2), let b = Int(b, radix: 2) else { return "Error"}
    
    let result: Int
    
    switch op {
    case .ADD:
        result = a + b
    case .SUBTRACT:
        result = a - b
    case .MULTIPLY:
        result = a * b
    }
    
    return String(result, radix: 2)
}
calculate("1", "1", .ADD) // 10
calculate("10", "10", .ADD) // 100
calculate("1", "1", .MULTIPLY) // 1
calculate("10", "10", .MULTIPLY) // 100
calculate("10", "10", .SUBTRACT) // 0
calculate("100", "10", .SUBTRACT) // 10

// Radix — это основание счисления, здесь 2 означает двоичное число
// из десятичной в двоичную
let y = String(1, radix: 2) // 1
let x = String(2, radix: 2) // 10
let z = String(3, radix: 2) // 11
let l = String(4, radix: 2) // 100
// из двоичной в десячичную
let v = Int("1", radix: 2) // 1
let b = Int("10", radix: 2) // 2
let m = Int("11", radix: 2) // 3
```

---

### [Counting in the Amazon](https://www.codewars.com/kata/55b95c76e08bd5eef100001e)

The Arara are an isolated tribe found in the Amazon who count in pairs. For example one to eight is as follows:

```bash
1 = anane
2 = adak
3 = adak anane
4 = adak adak
5 = adak adak anane
6 = adak adak adak
7 = adak adak adak anane
8 = adak adak adak adak
```

Take a given number and return the Arara's equivalent.

My solution:
```swift
func countArare(_ n: Int) -> String {
  return n <= 0 ? "" :
    n == 1 ? "anane" :
    n == 2 ? "adak" :
    "adak " + countArare(n-2)
}
countArare(1) // "anane"
countArare(2) // "adak"
countArare(3) // "adak anane"
countArare(5) // "adak adak anane"
```

[joined(separator:)](https://developer.apple.com/documentation/swift/array/joined(separator:)-7uber) - Returns the concatenated elements of this sequence of sequences, inserting the given separator between each element. Работает с Array

Other solutions:
```swift
func countArare(_ n: Int) -> String {
    guard n > 0 else { return "" }
    var pairs = Array(repeating: "adak", count: n / 2)
    if n % 2 == 1 {
      pairs.append("anane")
    }
    return pairs.joined(separator: " ")
}
```

```swift
func countArare(_ n: Int) -> String {
  return (Array(repeating: "adak", count: n / 2) + Array(repeating: "anane", count: n % 2)).joined(separator:" ")
}
```

---

### [Don't give me five!](https://www.codewars.com/kata/5813d19765d81c592200001a)

Вы получаете начало и числовой конец, и должны вернуть количество всех чисел в этом диапозоне включительно, кроме числа 5.

`1,9 -> 1,2,3,4,6,7,8,9 -> Result 8`

`4,17 -> 4,6,7,8,9,10,11,12,13,14,16,17 -> Result 12`

My solution:
```swift
func dontGiveMeFive(_ start: Int, _ end: Int) -> Int {
    var count = 0;
    for i in start...end {
        if String(i).contains("5") {
            continue
        }
        else {
            count = count + 1
        }
    }
    return count
}
dontGiveMeFive(1,9) // 8
dontGiveMeFive(4,17) // 12
```

Other solutions:
```swift
func dontGiveMeFive(_ start: Int, _ end: Int) -> Int {
    return (start...end).filter { !String($0).contains("5") }.count
}
```

```swift
let dontGiveMeFive: (Int, Int) -> Int = {
    ($0...$1).filter { !"\($0)".contains("5") }.count
}
```

---

### [Drying Potatoes](https://www.codewars.com/kata/58ce8725c835848ad6000007)

Write function potatoes (содержание воды в картофеле) with

- int parameter `p0` - initial percent of water-
- int parameter `w0` - initial weight -
- int parameter `p1` - final percent of water -
potatoesshould return the final weight coming out of the oven w1 truncated as an int.

Example: 
`potatoes(99, 100, 98) --> 50`

My solution:
```swift
func potatoes (_ p0: Int, _ w0: Int, _ p1: Int) -> Int {
    return w0 * (100 - p0) / (100 - p1)
}
dotest(99, 100, 98) // 50
dotest(82, 127, 80) // 114
```

---

### [Easy wallpaper](https://www.codewars.com/kata/567501aec64b81e252000003)

Джон знает, что прямоугольная комната имеет длину l метров, ширину w метров и высоту h метров. Стандартная ширина рулонов, которые он хочет купить, составляет 52 сантиметра. Длина рулона 10 метров. И на случай ошибки или просчета, купить длину на 15% больше, чем та, которая ему нужна.

`wallpaper(4.0, 3.5, 3.0) should return "ten"`

`wallpaper(0.0, 3.5, 3.0) should return "zero"`

`Площадь стен = периметр комнаты * на высоту потолка`

`P = (a + b) х 2`, где a и b – это ширина и длина комнаты. 

Чтобы получить площадь стен, нужно периметр комнаты умножить на высоту стен.

`Высота стен = P х h`, где h - высота стен.

My solution:
```swift
func wallpaper(_ l: Double, _  w: Double,_  h: Double) -> String {
    let numbers = ["zero", "one", "two", "three", "four", "five",
               "six", "seven", "eight", "nine", "ten",
               "eleven", "twelve", "thirteen", "fourteen", "fifteen",
               "sixteen", "seventeen", "eighteen", "nineteen", "twenty"]
    let rolls: Int = Int(ceil(((2 * h * (l + w)) / 0.52 / 10.00) * 1.15))
    // or
    //     let area: Double = (2 * w * h) + (2 * l * h)
    //let rolls: Int = Int(ceil(area/0.52/10.00 * 1.15))
    return l * w * h == 0 ? "zero" : numbers[rolls]
}
```

Other solutions:
```swift
func wallpaper(_ l: Double, _  w: Double,_  h: Double) -> String {
    let numbers = ["zero", "one", "two", "three", "four", "five",
               "six", "seven", "eight", "nine", "ten",
               "eleven", "twelve", "thirteen", "fourteen", "fifteen",
               "sixteen", "seventeen", "eighteen", "nineteen", "twenty"]
    guard l * w * h > 0 else { return "zero" }
    let wallpaperRolls = ((2 * h * (l + w)) / 0.52 / 10) * 1.15
    return numbers[Int(wallpaperRolls.rounded(.up))]
}
```

---

### [Functional Addition](https://www.codewars.com/kata/538835ae443aae6e03000547)

Create a function `add(n)/Add(n)` which returns a function that always adds n to any number

My solution:
```swift
func add(_ n: Int) -> ((Int) -> Int) { 
  func Add( _ number: Int) -> Int {
    return n + number
  }
  return Add
}
```

Other solutions:
```swift
func add(_ n: Int) -> ((Int) -> Int) { 
	return { return $0 + n }
	// or 
	//  { $0 + n }
}
```

---

### [Lost number in number sequence](https://www.codewars.com/kata/595aa94353e43a8746000120)

Дана упорядоченная последовательность чисел от 1 до N. Из нее удалили один номер. И дана перемешанная последовательность из оставшихся цифр. Найдите номер, который был удален. 

Начальная последовательность массива: `[1,2,3,4,5,6,7,8,9]`. Смешанный массив с одним удаленным числом: `[3,2,4,6,7,8,1,9]`. Ваша функция должна возвращать `int 5`. Если из начального массива не было удалено ни одного числа, ваша функция должна вернуть `int 0`. Примечание `N` может быть равно 1 или меньше (массив будет `[]`)

My solution:
```swift
func findDeletedNumber(_ array: [Int], _ mixArray: [Int]) -> Int {
    return array.reduce(0, +) - mixArray.reduce(0, +)
}

findDeletedNumber([1,2,3,4,5,6,7,8,9],[3,2,4,6,7,8,1,9]) // 5
```

Other solutions:
```swift
func findDeletedNumber(_ array: [Int], _ mixArray: [Int]) -> Int {
    guard !array.isEmpty, !mixArray.isEmpty else {
        return 0
    }
    for i in 0..<array.count {
        if !mixArray.contains(array[i]){
            return array[i]
        }
    }
    return 0
}
```

```swift
func findDeletedNumber(_ array: [Int], _ mixArray: [Int]) -> Int {
  for item in array {
    if !mixArray.contains(item) {
      return item
    }
  }
  return 0
}
```

---

### [Mumbling](https://www.codewars.com/kata/5667e8f4e3f572a8f2000039)

Дана строка, вернуть новую строку с увеличением числа каждой буквы в зависимости от числа букв и их положения в строке.

```bash
accum("abcd") -> "A-Bb-Ccc-Dddd"
accum("RqaEzty") -> "R-Qq-Aaa-Eeee-Zzzzz-Tttttt-Yyyyyyy"
accum("cwAt") -> "C-Ww-Aaa-Tttt"
```

My solution:
```swift
func accum(_ s: String) -> String {
  let array = Array(s.lowercased())
  var result = ""
  for i in 0..<array.count {
    for j in 0...i {
        result += j == 0
          ? String(array[i]).uppercased()
          : String(array[i])
    }
    if i < array.count - 1 { result += "-" }
  }
  return result
}
accum("abcd") // A-Bb-Ccc-Dddd
```

Other solutions:
```swift
func accum(_ str: String) -> String {
    return str.enumerated().map {
        repeatElement(String($1), count: $0 + 1).joined().capitalized
    }
        .joined(separator: "-")
// or
//     return str.enumerated().map { String(repeating: $1, count: $0 + 1)
//    .capitalized }.joined(separator: "-")

}
```

---

### [Sum of angles](https://www.codewars.com/kata/5a03b3f6a1c9040084001765)

Найдите сумму внутренних углов (в градусах) n-стороннего простого многоугольника. N будет больше 2. Сумма углов.

My solution:
```swift
func angle(_ n: Int) -> Int {
    return 180 * (n - 2)
}

angle(3) // 180
angle(4) // 360
```

---

### [Sum of two lowest positive integers](https://www.codewars.com/kata/558fc85d8fd1938afb000014)

Создайте функцию, которая возвращает сумму двух наименьших положительных чисел для заданного массива минимум из 4 положительных целых чисел. Не будут переданы числа с плавающей запятой или неположительные целые числа. Например, когда массив передается как `[19, 5, 42, 2, 77]`, вывод должен быть `7`

My solution:
```swift
// The solution using Array.sorted() is O(nlog(n))
func sumOfTwoSmallestIntegersIn(_ array: [Int]) -> Int {
    var sortedNumbers: [Int] = array.sorted(by:({$0 < $1}))
    if sortedNumbers.count < 2 {
        return sortedNumbers[0]
    }
    return sortedNumbers[0] + sortedNumbers[1]
}

sumOfTwoSmallestIntegersIn([5, 8, 12, 18, 22]) // 13
sumOfTwoSmallestIntegersIn([5]) // 5
sumOfTwoSmallestIntegersIn([7, 15, 12, 18, 22]) // 19
```

Other solutions:
```swift
// O(n) solution
func sumOfTwoSmallestIntegersIn(_ array: [Int]) -> Int {
    if array.count < 2 { return array[0] }
    var min1 = Int.max
    var min2 = Int.max
    array.forEach {
        if $0 < min1 {
            min2 = min1
            min1 = $0
        } else if $0 < min2 {
            min2 = $0
        }
    }
    return min1 + min2
}
```

```swift
func sumOfTwoSmallestIntegersIn(_ array: [Int]) -> Int {
   if array.count < 2 { return array[0] }
   let result = array.filter({ $0 >= 0 }).sorted()
   return result[0] + result[1]
}
```

```swift
// The solution using Array.sorted() is O(nlog(n))
func sumOfTwoSmallestIntegersIn(_ array: [Int]) -> Int {
    if array.count < 2 { return array[0] }
    let sort = array.sorted()
    return sort[0] + sort[1]
}
```

---


### [Sum of integers in string](https://www.codewars.com/kata/598f76a44f613e0e0b000026)

Вычислить сумму целых чисел внутри строки. Например, в строке `The30quick20brown10f0x1203jumps914ov3r1349the102l4zy dog` сумма целых чисел равна `3635`.

Примечание: будут проверяться только положительные целые числа.

My solution:
```swift
func sumOfIntegersInString(_ string: String) -> Int {
    var result = 0
    var number = ""
  
    for (index, element) in string.enumerated() {
        if element.isNumber {
            number += String(element)
            if index == string.count - 1 {
                result += Int(number) ?? 0
            }
        } else {
            result += Int(number) ?? 0
            number = ""
        }
    }
    return result
}
```

Other solutions:
```swift
func sumOfIntegersInString(_ string: String) -> Int {
    var sum: Int = 0
    var numberStr: String = ""
    for character in string {
        if character.isNumber {
            numberStr += String(character)
        }
        else {
            if let number = Int(numberStr) {
                sum += number
                numberStr = ""
            }
        }
    }
    
    if !numberStr.isEmpty {
        if let number = Int(numberStr) {sum += number}
    }
    return sum
}

```

```swift
func sumOfIntegersInString(_ string: String) -> Int {
    string.components(separatedBy: CharacterSet.decimalDigits.inverted).compactMap{ Int($0) }.reduce(0, +)
}
```

```swift
func sumOfIntegersInString(_ string: String) -> Int {
    return string.split { !$0.isNumber }.compactMap { Int($0) }.reduce(0, +)
}
```

```swift
func sumOfIntegersInString(_ string: String) -> Int {
  string
    .map { "0123456789".contains($0) ? "\($0)" : " " }
    .joined()
    .components(separatedBy: " ")
    .compactMap { Int(String($0)) }
    .reduce(0, +)
}
```

---

### [Odder Than the Rest](https://www.codewars.com/kata/5983cba828b2f1fd55000114)

Cоздайте функцию `oddOne`, которая принимает `[Int]` в качестве входных данных и выводит индекс, в котором расположено единственное нечетное число. Этот метод должен работать с массивами с отрицательными числами. Если в массиве нет нечетных чисел, метод должен вывести nil.

My solution:
```swift
func oddOne(_ arr: [Int]) -> Int? {
    for (index, element) in arr.enumerated() {
        if element % 2 != 0 {
            return index
        }
    }
    return nil
}
oddOne([2,4,6,7,10]) // => 3
oddOne([2,16,98,10,13,78]) // => 4
oddOne([4,-8,98,-12,-7,90,100]) // => 4
oddOne([2,4,6,8]) // => nil
```

Other solutions:
```swift
// Complexity: O(n), where n is the length of the collection

func oddOne(_ arr: [Int]) -> Int? {
    return arr.firstIndex { $0 % 2 != 0 }
}
```

---

### [Billiards triangle](https://www.codewars.com/kata/5bb3e299484fcd5dbb002912)

Помните треугольник шаров в бильярде? Для построения классического треугольника (5 уровней) нужно 15 шаров. Из 3-х шаров можно построить двухуровневый треугольник

Напишите функцию, которая принимает количество шаров (≥ 1) и вычисляет, на скольких уровнях можно построить треугольник.

```bash
pyramid(1) == 1
pyramid(3) == 2
pyramid(6) == 3
pyramid(10) == 4
pyramid(15) == 5
```

My solution:
```swift
func pyramid(_ balls: Int) -> Int{
  var balls = balls
  var level = 0
  while balls > level {
    level += 1
    balls -= level
  }
  return level
}
```

---

### [Count the Digit](https://www.codewars.com/kata/566fc12495810954b1000030)

Take an integer `n (n >= 0)` and a digit `d (0 <= d <= 9)` as an integer.

Square all numbers `k (0 <= k <= n)` between 0 and n.

Count the numbers of digits d used in the writing of all the `k**2`.

Implement the function taking n and d as parameters and returning this count

Examples:

```bash
n = 10, d = 1 
the k*k are 0, 1, 4, 9, 16, 25, 36, 49, 64, 81, 100
We are using the digit 1 in: 1, 16, 81, 100. The total count is then 4.

The function, when given n = 25 and d = 1 as argument, should return 11 since
the k*k that contain the digit 1 are:
1, 16, 81, 100, 121, 144, 169, 196, 361, 441.
So there are 11 digits 1 for the squares of numbers between 0 and 25.
Note that 121 has twice the digit 1.
```

My solution:
```swift
func nbDig(_ n: Int, _ d: Int) -> Int {
    return (0...n).map{ String($0 * $0).filter{ $0 == Character("\(d)") }}.flatMap{$0}.count
}

nbDig(10, 1)
```

Other solutions:
```swift
func nbDig(_ n: Int, _ d: Int) -> Int {
  var count = 0
  for x in 0...n {
    var cube = x * x
    repeat {
      if cube % 10 == d {
        count += 1
      }
      cube = cube / 10
    } while cube >= 1
  }
  return count
}
```

---

### [Descending Order](https://www.codewars.com/kata/5467e4d82edf8bbf40000155)

Ваша задача состоит в том, чтобы создать функцию, которая может принимать любое неотрицательное целое число в качестве аргумента и возвращать его с цифрами в порядке убывания. По сути, переставьте цифры, чтобы получить максимально возможное число. 

```bash
Input: 42145 Output: 54421
Input: 145263 Output: 654321
Input: 123456789 Output: 987654321
```

My solution:
```swift
func descendingOrder(of number: Int) -> Int {
    return Int(String("\(number)".sorted(by:>))) ?? 0
    //    return Int(String("\(number)".sorted { $0 > $1 } )) ?? 0
}

descendingOrder(of: 0) // 0
descendingOrder(of: 15) // 51
descendingOrder(of: 123456789) // 987654321
```

Other solutions:
```swift
func descendingOrder(of number: Int) -> Int {
    let numberAsString = String(number)
    let orderedNumbers = String(numberAsString.sorted().reversed())
    
    return Int(orderedNumbers)!
}
```

---

### [Going to the cinema](https://www.codewars.com/kata/562f91ff6a8b77dfe900006e)

My solution:
```swift

func movie(card: Double, ticket: Double, perc: Double) -> Int {
  var amount = 0
  var fullPrice = Double(0)
  var priceForTicketWithCard = Double(ticket)
  var totalPriceWithCard = Double(0)
  while ceil(totalPriceWithCard + card) >= ceil(fullPrice) {
      fullPrice += ticket
      priceForTicketWithCard = priceForTicketWithCard * perc
      totalPriceWithCard += priceForTicketWithCard
      amount += 1
  }
  return amount
}

movie(card: 500, ticket: 15, perc: 0.9) // 43
movie(card: 100, ticket: 10, perc: 0.95) // 24
```

---

### [Heron's formula](https://www.codewars.com/kata/57aa218e72292d98d500240f)

Write function heron which calculates the area of a triangle with sides a, b, and c

**[Формула Герона для площади треугольника](https://2mb.ru/matematika/geometriya/formula-gerona-dlya-ploshhadi-treugolnika/)**

Output should have 2 digits precision

My solution:
```swift
func heron(_ a: Double, _ b: Double, _ c: Double) -> Double {
    let s = (a + b + c) / 2
    let area = sqrt( s * (s - a) * (s - b) * (s - c) )
    return (area * 100).rounded() / 100
}
heron(5, 6, 7) // 14.7
```

Other solutions:
```swift
func heron(_ a: Double, _ b: Double, _ c: Double) -> Double {
    let s = (a + b + c ) / 2 // 9
    let root = sqrt(s * (s - a) * (s - b) * (s - c)) * 100 // 1469.693845669907
    let result = Double(round(root) / 100) // 14.7
    return result
}
```

---

### [Moves in squared strings (I)](https://www.codewars.com/kata/56dbe0e313c2f63be4000b25)

This kata is the first of a sequence of four about "Squared Strings".

You are given a string of `n` lines, each substring being `n` characters long: For example:

`s = "abcd\nefgh\nijkl\nmnop"`

We will study some transformations of this square of strings.

- Vertical mirror: vert_mirror (or vertMirror or vert-mirror)

`vert_mirror(s) => "dcba\nhgfe\nlkji\nponm"`

- Horizontal mirror: hor_mirror (or horMirror or hor-mirror)

`hor_mirror(s) => "mnop\nijkl\nefgh\nabcd"`

or printed:

```bash
vertical mirror   |horizontal mirror   
abcd --> dcba     |abcd --> mnop 
efgh     hgfe     |efgh     ijkl 
ijkl     lkji     |ijkl     efgh 
mnop     ponm     |mnop     abcd 
```

Task: 
- Write these two functions
- high-order function oper(fct, s) where
- fct is the function of one variable f to apply to the string s (fct will be one of vertMirror, horMirror)

Examples:

```bash
s = "abcd\nefgh\nijkl\nmnop"
oper(vert_mirror, s) => "dcba\nhgfe\nlkji\nponm"
oper(hor_mirror, s) => "mnop\nijkl\nefgh\nabcd"
```

Note: 
The form of the parameter fct in oper changes according to the language. You can see each form according to the language in "Sample Tests".

Bash Note: 
The input strings are separated by , instead of \n. The output strings should be separated by \r instead of \n. See "Sample Tests".

My solution:
```swift
func horMirror(_ s: String) -> String {
    s.components(separatedBy: "\n").reversed().joined(separator:"\n")
}

func vertMirror(_ s: String) -> String {
    s.components(separatedBy: "\n").map{ String($0.reversed()) }.joined(separator: "\n")
}

// replace the dots with function parameter
func oper(_ fn: (_ s:String) -> String, _ s: String) -> String {
    return fn(s)
}
```

---

### [Number's predecessor and sucessor (retired)](https://www.codewars.com/kata/6059f5a0867077001c6287f8/train/swift)

Write an algorithm that returns a number's predecessor and sucessor.

Expected return format: "Predecessor: n. Sucessor: n"

My solution:
```swift
func successorAndPredecessor(of number: Int) -> String {
  return "Predecessor: \(number - 1). Sucessor: \(number + 1)"
}

successorAndPredecessor(of: 4) // "Predecessor: 3. Sucessor: 5"
```

---

### [Over The Road](https://www.codewars.com/kata/5f0ed36164f2bc00283aed07)

Вы только что въехали на совершенно прямую улицу с ровно n одинаковыми домами по обеим сторонам дороги. Естественно, вы хотели бы узнать номер дома людей на другой стороне улицы. Улица выглядит примерно так:

```bash
Street
1|   |6
3|   |4
5|   |2
  you
```

События увеличиваются справа; коэффициенты уменьшаются слева. Номера домов начинаются с 1 и увеличиваются без пробелов. Когда n = 3, 1 противоположно 6, 3 противоположно 4, а 5 противоположно 2

Пример (адрес, n --> output) Учитывая адрес вашего дома и длину улицы n, укажите номер дома на противоположной стороне улицы.

```bash
1, 3 --> 6
3, 3 --> 4
2, 3 --> 5
3, 5 --> 8
```

My solution:
```swift
func overTheRoad(address: Int, street: Int) -> Int {
  return street * 2 + 1 - address
  // or
  // address == 1 ? street * 2 : street * 2 - (address - 1)
}
}
```

---

### [Printer Errors](https://www.codewars.com/kata/56541980fa08ab47a0000040)

На фабрике принтер печатает этикетки для коробок. Для одного вида коробок принтеру приходится использовать цвета, которые для простоты обозначаются буквами от `а` до `м`.

Цвета, используемые принтером, записываются в управляющую строку. Например, "хорошей" управляющей строкой была бы `aaabbbbhaijjjm`, означающая, что принтер использовал три раза цвет a, четыре раза цвет b, один раз цвет h, затем один раз цвет a...

Иногда возникают проблемы: отсутствие цветов, техническая неисправность и выдается "плохая" управляющая строка, например, `aaaxbbbbyyhwawiwjjjwwm` с буквами не от `a` до `m`.

Вы должны написать функцию `printer_error`, которая при заданной строке вернет частоту ошибок принтера в виде строки, представляющей рациональное число, числителем которого является количество ошибок, а знаменателем - длина управляющей строки. Не сводите эту дробь к более простому выражению.

Строка имеет длину, большую или равную единице, и содержит только буквы от `a` до `z`.

```bash
s="aaabbbbhaijjjm"
printer_error(s) => "0/14"

s="aaaxbbbbyyhwawiwjjjwwm"
printer_error(s) => "8/22"
```

My solution:
```swift
func printerError(_ s: String) -> String {
    return "\(s.count - s.filter(("a"..."m").contains).count)/\(s.count)"
}
```

Other solutions:
```swift
func printerError(_ s: String) -> String {
    let errors = s.filter { $0 > "m" }
    return "\(errors.count)/\(s.count)"
}
```

```swift
func printerError(_ s: String) -> String {
    var count = 0
    for c in s {
        count += ("a"..."m").contains(c) ? 0 : 1
    }
    return "\(count)/\(s.count)"
}
```

---

### [Shortest Word](https://www.codewars.com/kata/57cebe1dc6fdc20c57000ac9)

Просто, учитывая строку слов, вернуть длину самого кратчайшего/маленького слова (слов). Строка никогда не будет пустой, и вам не нужно учитывать разные типы данных

My solution:
```swift
func find_short(_ str: String) -> Int {
    return str.split(separator: " ").sorted{ $0.count < $1.count }[0].count
    // or
    // return str.split(separator: " ").min(by: {$0.count < $1.count})!.count
}

find_short("bitcoin take over the world maybe who knows perhaps") // 3
```

---

### [Simple Fun #2: Circle of Numbers](https://www.codewars.com/kata/58841cb52a077503c4000015)

Рассмотрим целые числа от `0` до `n - 1`, записанные вдоль окружности таким образом, чтобы расстояние между любыми двумя соседними числами было равным (обратите внимание, что `0` и `n - 1` тоже являются соседними).

Учитывая `n` и `firstNumber`, найдите число, которое записано в позиции, радиально противоположной `firstNumber`.

Пример: 
Для `n = 10` и `firstNumber` = 2 результат должен быть равен 7

<img alt="image" src="images/Simple Fun 2 Circle of Numbers.jpeg" width = 60% />

[input] integer `n`

A positive even integer.

Constraints: `4 ≤ n ≤ 1000`.

[input] integer `firstNumber`

Constraints: `0 ≤ firstNumber ≤ n - 1`

[output] an integer

My solution:
```swift
func circleOfNumbers(_ n: Int, _ fst: Int) -> Int {
    return (n / 2 + fst) % n
}

circleOfNumbers(10, 2) // 7
circleOfNumbers(10, 7) // 2
circleOfNumbers(4, 1) // 3
circleOfNumbers(6, 3) // 0
circleOfNumbers(20, 0) // 10
```

---

### [Digit*Digit](https://www.codewars.com/kata/546e2562b03326a88e000020/swift)

Необходимо возвести в квадрат каждую цифру числа и соединить их. Функция принимает целое число и возвращает целое число

9119 -> 811181 ( 9^2 is 81 and 1^2 is 1)

My solution:
```swift
func squareDigits(_ num: Int) -> Int {
    let num = String(num)
    var stringResult = ""

    for i in num {
        stringResult += "\( Int( String(i) )! * Int( String(i) )! )"
    }
  return Int(stringResult) ?? 0
}
```

Other solutions:
```swift
func squareDigits(_ num: Int) -> Int {
  return Int(String(num).compactMap { Int(String($0)) }.compactMap { String($0 * $0) }.joined()) ?? 0
}
```

```swift
extension StringProtocol {
    subscript(offset: Int) -> Character {
        self[index(startIndex, offsetBy: offset)]
    }
}

func squareDigits(_ num: Int) -> Int {
    let stringNum = String(num)
    var result = ""
    var stringValue: Character
    for index in 0...(stringNum.count - 1) {
        stringValue = stringNum[index]
        if let intValue = Int(String(stringValue)) {
            result += String(intValue * intValue)
        }
    }
    
    if let intResult = Int(result){
        return intResult
    }
    
    return 0
}
```

---

### [Doubleton number](https://www.codewars.com/kata/604287495a72ae00131685c7/)

Мы будем называть натуральное число "двойным числом", если оно содержит ровно две разные цифры. Например, 23, 35, 100, 121 являются двойными числами, а 123 и 9980 - нет.

Для заданного натурального числа `n` (от 1 до 1 000 000) вам нужно найти следующее двойное число. Если `n` само по себе является двойным, верните следующее большее, чем `n`

My solution:
```swift
func doubleton(_ num: Int) -> Int {
    var current = num + 1
    while !isDoubleton(current) {
        current += 1
    }
    return current
}
func isDoubleton(_ n: Int) -> Bool {
    let digits = Set(String(n))
    return digits.count == 2
}

doubleton(120) // 121
doubleton(1234) // 1311
doubleton(10) // 12
```

---

### [Sum of Minimums!](https://www.codewars.com/kata/5d5ee4c35162d9001af7d699)

Учитывая двумерный (вложенный) список (массив) размера `m * n`, ваша задача состоит в том, чтобы найти сумму минимальных значений в каждой строке

```bash
[ [ 1, 2, 3, 4, 5 ]        #  minimum value of row is 1
, [ 5, 6, 7, 8, 9 ]        #  minimum value of row is 5
, [ 20, 21, 34, 56, 100 ]  #  minimum value of row is 20
]
```

So the function should `return 26` because the sum of the minimums is `1 + 5 + 20 = 26`.

Note: You will always be given a non-empty list containing positive values

My solution:
```swift
func sumOfMinimums(_ numbers: [[Int]]) -> Int {
    var minInRows: [Int] = []
    for row in numbers {
        minInRows.append(row.min() ?? 0)
    }
    
    var result = 0
    for i in minInRows {
        result += i
    }
    
    return result
}

sumOfMinimums([[2,8,5,4,3], [8,3,4,5,6]]) // 5
sumOfMinimums([[1,6,3,11,32], [21,32,45,24,34], [8,12,13,6,3]]) // 25
sumOfMinimums([[7,1,4,3,6],[9,3,13,24,25],[23,35,37,47,56],[12,32,35,58,53],[22,24,35,47,56]]) // 61
```

Other solutions:
```swift
func sumOfMinimums(_ numbers: [[Int]]) -> Int {
    return numbers.compactMap{$0.min()}.reduce(0, +)
}
```

---

### [Is It Negative Zero (-0)?](https://www.codewars.com/kata/5c5086287bc6600001c7589a)

There exist two zeroes: `+0` (or just 0) and `-0`.

Write a function that `return true` if the input number is -0 and `return false` otherwise

My solution:
```swift
func isNegativeZero(_ n: Float) -> Bool {
  return String(n) == "-0.0"
  // or
  // n.description == "-0.0"
}
```

Other solutions:
```swift
func isNegativeZero(_ n: Float) -> Bool {
  return n == 0 && n.sign == .minus
}
```

```swift
func isNegativeZero(_ n: Float) -> Bool {
  return n == 0 && 1 / n == -Float.infinity
}
```

---

### [Alphabetical Addition](https://www.codewars.com/kata/5d50e3914861a500121e1958)

Your task is to add up letters to one letter.

The function will be given an `Array<Character>`, each one being a letter to add, and the function will return a Character.

Notes:

- Letters will always be lowercase.
- Letters can overflow (see second to last example of the description)
- If no letters are given, the function should return 'z'

Examples:
```bash
addLetters(["a", "b", "c"]) = "f"
addLetters(["a", "b"]) = "c"
addLetters(["z"]) = "z"
addLetters(["z", "a"]) = "a"
addLetters(["y", "c", "b"]) = "d" // notice the letters overflowing
addLetters([]) = "z"
```

My solution:
```swift
func addLetters(_ letters: [Character]) -> Character {
    let dictionary: [Character : Int] = ["a" : 1, "b" : 2, "c" : 3, "d" : 4, "e" : 5, "f" : 6, "g" : 7, "h" : 8, "i" : 9, "j" : 10, "k" : 11, "l" : 12, "m" : 13, "n" : 14, "o" : 15, "p" : 16, "q" : 17, "r" : 18, "s" : 19, "t" : 20, "u" : 21, "v" : 22, "w" : 23, "x" : 24, "y" : 25, "z" : 26]
     
     var sum = 0
     
     for letter in letters {
       sum += dictionary[(letter)] ?? 0
     }
     while sum > 26 {
       sum = sum - 26
     }
     
     for (key, value) in dictionary {
       if value == sum {
         return key
       }
     }
     return "z"
}

print(addLetters(["a", "b", "c"])) // Output: f
print(addLetters(["a", "b"])) // Output: c
print(addLetters(["z"])) // Output: z
print(addLetters(["z", "a"])) // Output: a
print(addLetters(["y", "c", "b"])) // Output: d
print(addLetters([])) // Output: z
```

---

### [Minimum Perimeter of a Rectangle](https://www.codewars.com/kata/5826f54cc60c7e5266000baf)

Прямоугольник может быть определен двумя факторами: высотой и шириной.

Его площадь определяется как умножение двух значений: `высота * ширина`.

Его периметр равен сумме его четырех ребер: `высота + высота + ширина + ширина`.

Можно создавать прямоугольники одинаковой площади, но разных периметров. Например, учитывая площадь 45, возможные высоты, ширины и результирующие периметры будут следующими:

```bash
(1, 45) = 92
(9, 5) = 28
(15, 3) = 36
```

Задача написать функцию, которая, учитывая площадь в виде целого положительного числа, возвращает наименьший возможный периметр прямоугольника с целыми длинами сторон.

Диапазон входного сигнала: 
`1 <= площадь <= 5 x 10 ^ 10`

My solution:
```swift
func minimumPerimeter(_ area: Int64) -> Int64 {
    var minPerimeter: Int64 = Int64.max
    for height in 1...Int64(sqrt(Double(area))) {
        if area % height == 0 {
            let width = area / height
            let perimeter = (height + width) * 2
            minPerimeter = min(minPerimeter, perimeter)
        }
    }
    return minPerimeter
}

minimumPerimeter(45) // 28
minimumPerimeter(30) // 22
minimumPerimeter(81) // 36
minimumPerimeter(89) // 180
minimumPerimeter(10000019) // 20000040
minimumPerimeter(982451653) // 1964903308
```

Other solutions:
```swift
func minimumPerimeter(_ area: Int64) -> Int64 {
    var width = Int64(sqrt(Double(area)))
    
    while area % width != 0 {
        width -= 1
    }
    
    return width * 2 + area / width * 2
}
```

---

### [Drone Fly-By](https://www.codewars.com/kata/58356a94f8358058f30004b5)

Вам будут даны две строки: лампы и дрона. Лампы представляют собой ряд ламп, в данный момент выключенных, каждая из которых обозначена символом `x`. Когда эти лампы включены, они должны быть обозначены символом `o`.

Строка дрона представляет положение дрона `T`, а траектория его полета вплоть до этой точки в виде `===`. Всегда летит слева направо и всегда начинается с начала ряда ламп. В любом месте, где пролетел беспилотник, включая его текущее местоположение, лампа в этом положении включится в `o`.

Верните строку `lamps` c включенныеми лампами. 

My solution:
```swift
func flyBy(lamps: String, drone: String) -> String {
    let lampsArray = Array(lamps)
    var result = ""
    for (index, lamp) in lampsArray.enumerated() {
        if index <= drone.count-1 {
            result += "o"
        } else {
            result += "\(lamp)"
        }
    }
    return result
}

flyDrone(lamps: "xxxxxx", drone: "====T") // ooooox
flyDrone(lamps: "xxxxxx", drone: "====T") // "ooooox"
flyDrone(lamps: "xxxxxxxxx", drone: "==T") // "oooxxxxxx"
flyDrone(lamps: "xxxxxxxxxxxxxxx", drone: "=========T") // "ooooooooooxxxxx"
```

Other solutions:
```swift
func flyBy( lamps: String, drone: String) -> String {
    return String(repeating: "o", count: drone.count) + String(repeating: "x", count: (lamps.count - drone.count))
}
```

```swift
func flyBy(lamps: String, drone: String) -> String {
    let lampsNum = lamps.count - 1
    let drone = drone.count
    var newString = ""
    
    for i in 0...lampsNum {
        if i < drone {
            newString += "o"
        } else {
            newString += "x"
        }
    }
  return "\(newString)"
}
```

---

### []()



My solution:
```swift

```

Other solutions:
```swift

```

---

### []()



My solution:
```swift

```

Other solutions:
```swift

```

---

### []()



My solution:
```swift

```

Other solutions:
```swift

```

---

### []()



My solution:
```swift

```

Other solutions:
```swift

```

---

### []()



My solution:
```swift

```

Other solutions:
```swift

```

---

### []()



My solution:
```swift

```

Other solutions:
```swift

```

---

### []()



My solution:
```swift

```

Other solutions:
```swift

```

---

### []()



My solution:
```swift

```

Other solutions:
```swift

```


