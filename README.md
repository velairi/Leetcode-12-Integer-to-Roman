# Integer to Roman

https://leetcode.com/problems/integer-to-roman/

Leetcode #12 Integer to Roman

```
Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.

Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
For example, two is written as II in Roman numeral, just two one's added together. Twelve is written as, XII, which is simply X + II. The number twenty seven is written as XXVII, which is XX + V + II.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not IIII. Instead, the number four is written as IV. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as IX. There are six instances where subtraction is used:

I can be placed before V (5) and X (10) to make 4 and 9. 
X can be placed before L (50) and C (100) to make 40 and 90. 
C can be placed before D (500) and M (1000) to make 400 and 900.
Given an integer, convert it to a roman numeral. Input is guaranteed to be within the range from 1 to 3999.

Example 1:

Input: 3
Output: "III"
Example 2:

Input: 4
Output: "IV"
Example 3:

Input: 9
Output: "IX"
Example 4:

Input: 58
Output: "LVIII"
Explanation: L = 50, V = 5, III = 3.
Example 5:

Input: 1994
Output: "MCMXCIV"
Explanation: M = 1000, CM = 900, XC = 90 and IV = 4.
```

<p> Solution </p>
1. Create a mapping of number to roman numerals
2. Create the arr of keys
3. Find the number in the array to get the largest roman numeral
4. Add the roman numeral to output string
5. Subtract the value of the roman numeral from our current number
6. repeat until we hit zero

```
    let numToRomanMap = [1: "I", 
    4: "IV", 5: "V", 9: "IX", 
    10: "X", 40: "XL", 50: "L", 
    90: "XC", 100: "C", 400: "CD", 
    500: "D", 900: "CM", 1000: "M"]
    let numToRomanArr = [1, 4, 5, 9, 10, 40, 50, 90, 100, 400, 500, 900, 1000]
                                                                           
    
    func intToRoman(_ num: Int) -> String {
      var numCopy = num
      var output = ""
      while numCopy > 0 {
        let romanNumber = findRomanNumForNumCopy(numCopy)
        if let romanNum = numToRomanMap[romanNumber] {
          output += romanNum
        }
        numCopy -= romanNumber
      }
      return output
    }

    func findRomanNumForNumCopy(_ num: Int) -> Int {
      for i in 0..<numToRomanArr.count {
        if num < numToRomanArr[i] {
          return numToRomanArr[i-1]
        } else if num == numToRomanArr[i] {
          return numToRomanArr[i] 
        } else if num > numToRomanArr[numToRomanArr.count - 1] {
          return 1000
        }
      }
      return 0
    }
    
 ```
 Time: O(n^2)
 Space: O(n)
