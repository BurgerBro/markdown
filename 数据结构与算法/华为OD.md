



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

[169. 多数元素](https://leetcode.cn/problems/majority-element/)

给定一个大小为 `n` 的数组 `nums` ，返回其中的多数元素。多数元素是指在数组中出现次数 **大于** `⌊ n/2 ⌋` 的元素。

你可以假设数组是非空的，并且给定的数组总是存在多数元素。

 

**示例 1：**

```
输入：nums = [3,2,3]
输出：3
```

**示例 2：**

```
输入：nums = [2,2,1,1,1,2,2]
输出：2
```

 

**提示：**

- `n == nums.length`
- `1 <= n <= 5 * 104`
- `-109 <= nums[i] <= 109`

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var majorityElement = function(nums) {
    nums.sort((a,b)=> a-b)
    return nums[Math.floor(nums.length/2)]
};
```

[53. 最大子数组和](https://leetcode.cn/problems/maximum-subarray/)

给你一个整数数组 `nums` ，请你找出一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。

**子数组** 是数组中的一个连续部分。

 

**示例 1：**

```
输入：nums = [-2,1,-3,4,-1,2,1,-5,4]
输出：6
解释：连续子数组 [4,-1,2,1] 的和最大，为 6 。
```

**示例 2：**

```
输入：nums = [1]
输出：1
```

**示例 3：**

```
输入：nums = [5,4,-1,7,8]
输出：23
```

 

**提示：**

- `1 <= nums.length <= 105`
- `-104 <= nums[i] <= 104`

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var maxSubArray = function(nums) {
    let pre = 0, maxAns = nums[0];
    nums.forEach((x) => {
        pre = Math.max(pre + x, x);
        maxAns = Math.max(maxAns, pre);
    });
    return maxAns;
};
```

[1502. 判断能否形成等差数列](https://leetcode.cn/problems/can-make-arithmetic-progression-from-sequence/)

给你一个数字数组 `arr` 。

如果一个数列中，任意相邻两项的差总等于同一个常数，那么这个数列就称为 **等差数列** 。

如果可以重新排列数组形成等差数列，请返回 `true` ；否则，返回 `false` 。

 

**示例 1：**

```
输入：arr = [3,5,1]
输出：true
解释：对数组重新排序得到 [1,3,5] 或者 [5,3,1] ，任意相邻两项的差分别为 2 或 -2 ，可以形成等差数列。
```

**示例 2：**

```
输入：arr = [1,2,4]
输出：false
解释：无法通过重新排序得到等差数列。
```

 

**提示：**

- `2 <= arr.length <= 1000`
- `-10^6 <= arr[i] <= 10^6`

```javascript
/**
 * @param {number[]} arr
 * @return {boolean}
 */
var canMakeArithmeticProgression = function(arr) {
    arr.sort((a,b)=> a-b)
    let l = arr.length
    if (l === 1) return true
    let diffValue = arr[l-1] - arr[l-2]
    while(l>1) {
        if (arr[l-1] - arr[l-2] !== diffValue) return false
        l--
    } 
    return true
};
```

[88. 合并两个有序数组](https://leetcode.cn/problems/merge-sorted-array/)

给你两个按 **非递减顺序** 排列的整数数组 `nums1` 和 `nums2`，另有两个整数 `m` 和 `n` ，分别表示 `nums1` 和 `nums2` 中的元素数目。

请你 **合并** `nums2` 到 `nums1` 中，使合并后的数组同样按 **非递减顺序** 排列。

**注意：**最终，合并后数组不应由函数返回，而是存储在数组 `nums1` 中。为了应对这种情况，`nums1` 的初始长度为 `m + n`，其中前 `m` 个元素表示应合并的元素，后 `n` 个元素为 `0` ，应忽略。`nums2` 的长度为 `n` 。

 

**示例 1：**

```
输入：nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3
输出：[1,2,2,3,5,6]
解释：需要合并 [1,2,3] 和 [2,5,6] 。
合并结果是 [1,2,2,3,5,6] ，其中斜体加粗标注的为 nums1 中的元素。
```

**示例 2：**

```
输入：nums1 = [1], m = 1, nums2 = [], n = 0
输出：[1]
解释：需要合并 [1] 和 [] 。
合并结果是 [1] 。
```

**示例 3：**

```
输入：nums1 = [0], m = 0, nums2 = [1], n = 1
输出：[1]
解释：需要合并的数组是 [] 和 [1] 。
合并结果是 [1] 。
注意，因为 m = 0 ，所以 nums1 中没有元素。nums1 中仅存的 0 仅仅是为了确保合并结果可以顺利存放到 nums1 中。
```

 

**提示：**

- `nums1.length == m + n`
- `nums2.length == n`
- `0 <= m, n <= 200`
- `1 <= m + n <= 200`
- `-109 <= nums1[i], nums2[j] <= 109`

```javascript
/**
 * @param {number[]} nums1
 * @param {number} m
 * @param {number[]} nums2
 * @param {number} n
 * @return {void} Do not return anything, modify nums1 in-place instead.
 */
var merge = function(nums1, m, nums2, n) {
    nums1.splice(m,n, ...nums2)
    nums1.sort((a,b)=> a-b)
};
```



[594. 最长和谐子序列](https://leetcode.cn/problems/longest-harmonious-subsequence/)

和谐数组是指一个数组里元素的最大值和最小值之间的差别 **正好是 `1`** 。

现在，给你一个整数数组 `nums` ，请你在所有可能的子序列中找到最长的和谐子序列的长度。

数组的子序列是一个由数组派生出来的序列，它可以通过删除一些元素或不删除元素、且不改变其余元素的顺序而得到。

 

**示例 1：**

```
输入：nums = [1,3,2,2,5,2,3,7]
输出：5
解释：最长的和谐子序列是 [3,2,2,2,3]
```

**示例 2：**

```
输入：nums = [1,2,3,4]
输出：2
```

**示例 3：**

```
输入：nums = [1,1,1,1]
输出：0
```

 

**提示：**

- `1 <= nums.length <= 2 * 104`
- `-109 <= nums[i] <= 109`

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var findLHS = function(nums) {
    nums = nums.sort((a,b)=> a-b)
    let begin = 0
    let res = 0
    for (let end = 0; end < nums.length; end++) {
        while (nums[end]-nums[begin]>1) {
            begin++
        }
        if (nums[end]-nums[begin] === 1) {
            res = Math.max(res, end-begin+1)
        }
    }
    return res
};
```



[643. 子数组最大平均数 I](https://leetcode.cn/problems/maximum-average-subarray-i/)

给你一个由 `n` 个元素组成的整数数组 `nums` 和一个整数 `k` 。

请你找出平均数最大且 **长度为 `k`** 的连续子数组，并输出该最大平均数。

任何误差小于 `10-5` 的答案都将被视为正确答案。

 

**示例 1：**

```
输入：nums = [1,12,-5,-6,50,3], k = 4
输出：12.75
解释：最大平均数 (12-5-6+50)/4 = 51/4 = 12.75
```

**示例 2：**

```
输入：nums = [5], k = 1
输出：5.00000
```

 

**提示：**

- `n == nums.length`
- `1 <= k <= n <= 105`
- `-104 <= nums[i] <= 104`

```javascript
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number}
 */
var findMaxAverage = function(nums, k) {
    const l = nums.length
    let sum = 0;
    for (let i=0;i<k;i++) {
        sum += nums[i]
    }
    let res = sum
    for (let j = k; j<l; j++) {
        sum = sum - nums[j-k] + nums[j]
        res = Math.max(res, sum)
    }
    return res /k
};
```

