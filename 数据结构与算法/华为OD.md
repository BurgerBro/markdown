



OD算法练习

以下为leetcode od算法题考点

> **第一阶段:**
>
> 练习字符串、数组、链表的基本操作，熟悉语言和编码手感
>
> 参考题目：
>
> 字符串，简单 1154，125，344，20，392，409，859，14，1694，551
>
> 数组，简单 1，169，53，1502，88，594，643，463，
>
> 链表，简单 234，21，141，83
>
> **第二阶段:**
>
> 练习较为复杂的字符串，数组的处理
>
> 字符串，中等 468，692，151，686，1764
>
> 数组，中等56，229，347
>
> **第三阶段:**
>
> 算法练习
>
> 字符串，中等，回溯93
>
> 数组，中等，回溯 39，90，46，78
>
> 数组，中等，深度优先，广度优先，417，994，385
>
> 数组，中等，滑动窗口，713
>
> 字符串，中等，滑动窗口424
>
> 动态规划，简单70
>
> 动态规划，中等64
>
> 数组，中等，双指针 16
>
> 字符串，中等，双指针15，
>
> 数组，中等，栈150

## 第一阶段

### 字符串

[1154. 一年中的第几天](https://leetcode.cn/problems/day-of-the-year/)

```javascript
1154. 一年中的第几天
提示
简单/**
 * @param {character[]} s
 * @return {void} Do not return anything, modify s in-place instead.
 */
var reverseString = function(s) {
    for (let i = 0,  j = s.length -1; i<j; i++, j--) {
        let temp = s[i]
        s[i] = s[j]
        s[j] = temp
    }
};
113
相关企业
给你一个字符串 date ，按 YYYY-MM-DD 格式表示一个 现行公元纪年法 日期。返回该日期是当年的第几天。

示例 1：

输入：date = "2019-01-09"
输出：9
解释：给定日期是2019年的第九天。
示例 2：

输入：date = "2019-02-10"
输出：41

/**
 * @param {string} date
 * @return {number}
 */
var dayOfYear = function(date) {
    const [year, month, day] = date.split('-')
    const amount = [31, 28, 31, 30, 31, 30 ,31, 31, 30, 31, 30, 31]
    if (year % 400 === 0 || (year % 4 === 0 && year % 100 !== 0)) {
        ++amount[1]
    }
    let ans = 0
    for(let i = 0; i < parseInt(month) - 1; i++) {
        ans += amount[i]
    }
    ans += parseInt(day)
    return ans
};
```

[125. 验证回文串](https://leetcode.cn/problems/valid-palindrome/)

```javascript
如果在将所有大写字符转换为小写字符、并移除所有非字母数字字符之后，短语正着读和反着读都一样。则可以认为该短语是一个 回文串 。

字母和数字都属于字母数字字符。

给你一个字符串 s，如果它是 回文串 ，返回 true ；否则，返回 false 。

示例 1：

输入: s = "A man, a plan, a canal: Panama"
输出：true
解释："amanaplanacanalpanama" 是回文串。
示例 2：

输入：s = "race a car"
输出：false
解释："raceacar" 不是回文串。
示例 3：

输入：s = " "
输出：true
解释：在移除非字母数字字符之后，s 是一个空字符串 "" 。
由于空字符串正着反着读都一样，所以是回文串。

/**
 * @param {string} s
 * @return {boolean}
 */
var isPalindrome = function(s) {
    s = s.replace(/[^a-zA-Z0-9]/g,"").replace(/\s/g,"").toLowerCase()
    for (let i = 0, j = s.length - 1; i < j; i++, j--) {
        if (s[i] !== s[j]) return false
    }
    return true
};

```

[344. 反转字符串](https://leetcode.cn/problems/reverse-string/)

```javascript
344. 反转字符串
提示
简单
785
相关企业
编写一个函数，其作用是将输入的字符串反转过来。输入字符串以字符数组 s 的形式给出。

不要给另外的数组分配额外的空间，你必须原地修改输入数组、使用 O(1) 的额外空间解决这一问题。

 

示例 1：

输入：s = ["h","e","l","l","o"]
输出：["o","l","l","e","h"]
示例 2：

输入：s = ["H","a","n","n","a","h"]
输出：["h","a","n","n","a","H"]

/**
 * @param {character[]} s
 * @return {void} Do not return anything, modify s in-place instead.
 */
var reverseString = function(s) {
    for (let i = 0,  j = s.length -1; i<j; i++, j--) {
        let temp = s[i]
        s[i] = s[j]
        s[j] = temp
    }
};
```

[20. 有效的括号](https://leetcode.cn/problems/valid-parentheses/)

```javascript
20. 有效的括号
提示
简单
4K
相关企业
给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串 s ，判断字符串是否有效。

有效字符串需满足：

左括号必须用相同类型的右括号闭合。
左括号必须以正确的顺序闭合。
每个右括号都有一个对应的相同类型的左括号。
 

示例 1：

输入：s = "()"
输出：true
示例 2：

输入：s = "()[]{}"
输出：true
示例 3：

输入：s = "(]"
输出：false

/**
 * @param {string} s
 * @return {boolean}
 */
var isValid = function(s) {
    const l = s.length
    if (l % 2 === 1) return false
    let stack = []
    const pairs = new Map([
        [')', '('],
        ['}', '{'],
        [']', '[']
    ])
    for (let i = 0; i<s.length ; i++) {
        if (pairs.has(s[i])) {
            if (pairs.get(s[i]) !== stack[stack.length - 1] || !stack.length) {
                return false
            }
            stack.pop()
        }
        else {
            stack.push(s[i])
        }
    }
    return !stack.length
};
```

[392. 判断子序列](https://leetcode.cn/problems/is-subsequence/)

```javascript
392. 判断子序列
简单
900
相关企业
给定字符串 s 和 t ，判断 s 是否为 t 的子序列。

字符串的一个子序列是原始字符串删除一些（也可以不删除）字符而不改变剩余字符相对位置形成的新字符串。（例如，"ace"是"abcde"的一个子序列，而"aec"不是）。

进阶：

如果有大量输入的 S，称作 S1, S2, ... , Sk 其中 k >= 10亿，你需要依次检查它们是否为 T 的子序列。在这种情况下，你会怎样改变代码？

致谢：

特别感谢 @pbrother 添加此问题并且创建所有测试用例。

 

示例 1：

输入：s = "abc", t = "ahbgdc"
输出：true
示例 2：

输入：s = "axc", t = "ahbgdc"
输出：false

/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
var isSubsequence = function(s, t) {
    if (s.length < 1) return true
    let i = 0
    while (i < t.length) {
        if (s[0] === t[i]) {
            const subs = s.substring(1)
            const subt = t.substring(i+1)
            return isSubsequence(subs, subt)
        }
        i++
    }
    return false
}
```

[409. 最长回文串](https://leetcode.cn/problems/longest-palindrome/)

给定一个包含大写字母和小写字母的字符串 `s` ，返回 *通过这些字母构造成的 **最长的回文串*** 。

在构造过程中，请注意 **区分大小写** 。比如 `"Aa"` 不能当做一个回文字符串。

 

**示例 1:**

```
输入:s = "abccccdd"
输出:7
解释:
我们可以构造的最长的回文串是"dccaccd", 它的长度是 7。
```

**示例 2:**

```
输入:s = "a"
输出:1
```

**示例 3：**

```
输入:s = "aaaaaccc"
输出:7
```

```javascript
/**
 * @param {string} s
 * @return {number}
 */
var longestPalindrome = function(s) {
    let ans = 0 
    let hashmap = new Map()
    let flag = 0
    for (let i = 0; i<s.length; i++) {
        hashmap.set(s[i], hashmap.has(s[i])?hashmap.get(s[i])+1 : 1)
    }
    for (let item of hashmap) {
        if (item[1] % 2 === 0) {
            ans += item[1]
        }else {
            ans += item[1]>1? (item[1]-1) : 0
            flag = 1
        }
    }
    return flag? ans + 1 : ans
};
```

[859. 亲密字符串](https://leetcode.cn/problems/buddy-strings/)

给你两个字符串 `s` 和 `goal` ，只要我们可以通过交换 `s` 中的两个字母得到与 `goal` 相等的结果，就返回 `true` ；否则返回 `false` 。

交换字母的定义是：取两个下标 `i` 和 `j` （下标从 `0` 开始）且满足 `i != j` ，接着交换 `s[i]` 和 `s[j]` 处的字符。

- 例如，在 `"abcd"` 中交换下标 `0` 和下标 `2` 的元素可以生成 `"cbad"` 。

 

**示例 1：**

```
输入：s = "ab", goal = "ba"
输出：true
解释：你可以交换 s[0] = 'a' 和 s[1] = 'b' 生成 "ba"，此时 s 和 goal 相等。
```

**示例 2：**

```
输入：s = "ab", goal = "ab"
输出：false
解释：你只能交换 s[0] = 'a' 和 s[1] = 'b' 生成 "ba"，此时 s 和 goal 不相等。
```

**示例 3：**

```
输入：s = "aa", goal = "aa"
输出：true
解释：你可以交换 s[0] = 'a' 和 s[1] = 'a' 生成 "aa"，此时 s 和 goal 相等。
```

 

**提示：**

- `1 <= s.length, goal.length <= 2 * 104`
- `s` 和 `goal` 由小写英文字母组成

```javascript
/**
 * @param {string} s
 * @param {string} goal
 * @return {boolean}
 */
var buddyStrings = function(s, goal) {
    if (s.length<2 || s.length !== goal.length) return false
    let i = 0
    let diffCount = 0
    let charSMap = new Map()
    let charGoalMap = new Map()
    while (i < s.length) {
        charSMap.get(s[i])? charSMap.set(s[i], charSMap.get(s[i])+1) :  charSMap.set(s[i], 1)
        charGoalMap.get(goal[i])? charGoalMap.set(goal[i], charGoalMap.get(goal[i])+1) :  charGoalMap.set(goal[i], 1)
        s[i] !== goal[i]? diffCount++ : 0
        if(diffCount > 2) return false
        i++
    }
    for (const [key, value] of charSMap) {
        if (!charGoalMap.has(key) || charGoalMap.get(key) !== value) {
            return false;
        }
    }
    if (diffCount === 1) return false
    if (s === goal) {
        let flag = 0
        charSMap.forEach((item)=> {
            if (item>1) flag = 1
        })
        if (flag === 0) return false
    }
    return true
};
```

[14. 最长公共前缀](https://leetcode.cn/problems/longest-common-prefix/)

编写一个函数来查找字符串数组中的最长公共前缀。

如果不存在公共前缀，返回空字符串 `""`。

 

**示例 1：**

```
输入：strs = ["flower","flow","flight"]
输出："fl"
```

**示例 2：**

```
输入：strs = ["dog","racecar","car"]
输出：""
解释：输入不存在公共前缀。
```

 

**提示：**

- `1 <= strs.length <= 200`
- `0 <= strs[i].length <= 200`
- `strs[i]` 仅由小写英文字母组成

```javascript
/**
 * @param {string[]} strs
 * @return {string}
 */
var longestCommonPrefix = function(strs) {
    if (strs.length === 0) return ""
    function isCommonPrefix(length) {
        return strs.every(str => str.startsWith(strs[0].substring(0,length)))
    }
    let minLen = strs[0].length
    for (let str of strs) {
        if (str.length< minLen) {
            minLen = str.length
        }
    }
    let low = 0, high = minLen
    while (low <high) {
        mid = Math.floor((low + high + 1)/2)
        if (isCommonPrefix(mid)) {
            low = mid
        } else {
            high = mid - 1
        }
    }
    return strs[0].substring(0,low)
};
```

[1694. 重新格式化电话号码](https://leetcode.cn/problems/reformat-phone-number/)

给你一个字符串形式的电话号码 `number` 。`number` 由数字、空格 `' '`、和破折号 `'-'` 组成。

请你按下述方式重新格式化电话号码。

- 首先，**删除** 所有的空格和破折号。

- 其次，将数组从左到右

   

  每 3 个一组

   

  分块，

  直到 

  剩下 4 个或更少数字。剩下的数字将按下述规定再分块：

  - 2 个数字：单个含 2 个数字的块。
  - 3 个数字：单个含 3 个数字的块。
  - 4 个数字：两个分别含 2 个数字的块。

最后用破折号将这些块连接起来。注意，重新格式化过程中 **不应该** 生成仅含 1 个数字的块，并且 **最多** 生成两个含 2 个数字的块。

返回格式化后的电话号码。

 

**示例 1：**

```
输入：number = "1-23-45 6"
输出："123-456"
解释：数字是 "123456"
步骤 1：共有超过 4 个数字，所以先取 3 个数字分为一组。第 1 个块是 "123" 。
步骤 2：剩下 3 个数字，将它们放入单个含 3 个数字的块。第 2 个块是 "456" 。
连接这些块后得到 "123-456" 。
```

**示例 2：**

```
输入：number = "123 4-567"
输出："123-45-67"
解释：数字是 "1234567".
步骤 1：共有超过 4 个数字，所以先取 3 个数字分为一组。第 1 个块是 "123" 。
步骤 2：剩下 4 个数字，所以将它们分成两个含 2 个数字的块。这 2 块分别是 "45" 和 "67" 。
连接这些块后得到 "123-45-67" 。
```

**示例 3：**

```
输入：number = "123 4-5678"
输出："123-456-78"
解释：数字是 "12345678" 。
步骤 1：第 1 个块 "123" 。
步骤 2：第 2 个块 "456" 。
步骤 3：剩下 2 个数字，将它们放入单个含 2 个数字的块。第 3 个块是 "78" 。
连接这些块后得到 "123-456-78" 。
```

**示例 4：**

```
输入：number = "12"
输出："12"
```

**示例 5：**

```
输入：number = "--17-5 229 35-39475 "
输出："175-229-353-94-75"
```

 

**提示：**

- `2 <= number.length <= 100`
- `number` 由数字和字符 `'-'` 及 `' '` 组成。
- `number` 中至少含 **2** 个数字。

```javascript
/**
 * @param {string} number
 * @return {string}
 */
var reformatNumber = function(number) {
     const regex = /[\s-]/g
     let ans = ''
     number = number.replace(regex, '')
     if (number.length < 4) {
         ans = number
         return ans
     }
     else if (number.slice(0,number.length-4).length%3 === 0 || number.length === 4) {
        if (number.length === 4) return number.slice(0,2) + '-' + number.slice(2,4)
        let str1 = number.slice(number.length-4,number.length-2)
        let str2 = number.slice(number.length-2,number.length)
        let i = 1
        number = number.slice(0,number.length-4)
        let paras = Math.floor(number.length / 3)
        while (i < paras+1) {
            let lastIndex = i * 3, firstIndex = (i-1) * 3
            ans += number.slice(firstIndex, lastIndex)
            ans += '-'
            i++
        }
        return ans + str1 + '-' + str2
     }
     else {
         let paras = Math.floor(number.length / 3)
         let i = 1
         while (i < paras+1) {
             let lastIndex = i * 3, firstIndex = (i-1) * 3
             ans += number.slice(firstIndex, lastIndex)
             ans += '-'
             i++
         }
         return (number.length % 3 === 0) ? ans.slice(0, ans.length-1) : ans.concat(number.slice(paras*3, number.length))
     }
};  
```

[551. 学生出勤记录 I](https://leetcode.cn/problems/student-attendance-record-i/)

给你一个字符串 `s` 表示一个学生的出勤记录，其中的每个字符用来标记当天的出勤情况（缺勤、迟到、到场）。记录中只含下面三种字符：

- `'A'`：Absent，缺勤
- `'L'`：Late，迟到
- `'P'`：Present，到场

如果学生能够 **同时** 满足下面两个条件，则可以获得出勤奖励：

- 按 **总出勤** 计，学生缺勤（`'A'`）**严格** 少于两天。
- 学生 **不会** 存在 **连续** 3 天或 **连续** 3 天以上的迟到（`'L'`）记录。

如果学生可以获得出勤奖励，返回 `true` ；否则，返回 `false` 。

 

**示例 1：**

```
输入：s = "PPALLP"
输出：true
解释：学生缺勤次数少于 2 次，且不存在 3 天或以上的连续迟到记录。
```

**示例 2：**

```
输入：s = "PPALLL"
输出：false
解释：学生最后三天连续迟到，所以不满足出勤奖励的条件。
```

 

**提示：**

- `1 <= s.length <= 1000`
- `s[i]` 为 `'A'`、`'L'` 或 `'P'`

```javascript
/**
 * @param {string} s
 * @return {boolean}
 */
var checkRecord = function(s) {
    let regexAbsent = /.*A.*A.*/g
    let regexLate = /.*L{3}.*/g
    if (!s.match(regexAbsent) && ! s.match(regexLate)) return true
    return false
};
```

