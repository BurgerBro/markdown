OD算法练习

以下为leetcode od算法题考点

> 字符串：**3**，**49**，30
> 线性表：**86**，**16**，**27**，732
> 队列：641，**406**，899
> 栈：**946**，116，117，895
> 哈希表：**61**，**729**，25，554
> dfs：105，112，98，494，547，1254
> bfs：1091，1129，102，101，752
>
> **第一阶段:**
>
> 练习字符串、数组、链表的基本操作，熟悉语言和编码手感
>
> 参考题目：
>
> 字符串，简单 **1154，125，344，20，392，409，859，14，1694，551** 
>
> 数组，简单 **1，169，53，1502，88，594，643，463**，
>
> 链表，简单 **234，21，141，83**
>
> **第二阶段:**
>
> 练习较为复杂的字符串，数组的处理
>
> 字符串，中等 **468，692，151，686**，1764
>
> 数组，中等56，**229**，**347**
>
> 链表，中等**24**
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

> - 双指针
> - 快慢指针
> - KMP
> - 滑动窗口

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

[463. 岛屿的周长](https://leetcode.cn/problems/island-perimeter/)

给定一个 `row x col` 的二维网格地图 `grid` ，其中：`grid[i][j] = 1` 表示陆地， `grid[i][j] = 0` 表示水域。

网格中的格子 **水平和垂直** 方向相连（对角线方向不相连）。整个网格被水完全包围，但其中恰好有一个岛屿（或者说，一个或多个表示陆地的格子相连组成的岛屿）。

岛屿中没有“湖”（“湖” 指水域在岛屿内部且不和岛屿周围的水相连）。格子是边长为 1 的正方形。网格为长方形，且宽度和高度均不超过 100 。计算这个岛屿的周长。

 

**示例 1：**

![img](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/12/island.png)

```
输入：grid = [[0,1,0,0],[1,1,1,0],[0,1,0,0],[1,1,0,0]]
输出：16
解释：它的周长是上面图片中的 16 个黄色的边
```

**示例 2：**

```
输入：grid = [[1]]
输出：4
```

**示例 3：**

```
输入：grid = [[1,0]]
输出：4
```

 

**提示：**

- `row == grid.length`
- `col == grid[i].length`
- `1 <= row, col <= 100`
- `grid[i][j]` 为 `0` 或 `1`

```javascript
/**
 * @param {number[][]} grid
 * @return {number}
 */
var islandPerimeter = function(grid) {
    const dfs = (i, j) => {
        if (i<0 || j< 0 || i >= grid.length || j >= grid[0].length) {
            return 1
        }
        else if (grid[i][j] === 0) {
            return 1
        }
        else if (grid[i][j] === 2) {
            return 0
        }
        grid[i][j] = 2
        return dfs(i-1,j) + dfs(i+1,j) + dfs(i,j-1) + dfs(i,j+1)
    }
    for (let i = 0; i < grid.length; i++) {
        for (let j = 0; j < grid[0].length; j++) {
            if (grid[i][j] == 1) {
            return dfs(i, j);   // dfs的入口
            }
        }
    }
  return 0
};
```

[234. 回文链表](https://leetcode.cn/problems/palindrome-linked-list/)

给你一个单链表的头节点 `head` ，请你判断该链表是否为回文链表。如果是，返回 `true` ；否则，返回 `false` 。

 

**示例 1：**

![img](https://assets.leetcode.com/uploads/2021/03/03/pal1linked-list.jpg)

```
输入：head = [1,2,2,1]
输出：true
```

**示例 2：**

![img](https://assets.leetcode.com/uploads/2021/03/03/pal2linked-list.jpg)

```
输入：head = [1,2]
输出：false
```

 

**提示：**

- 链表中节点数目在范围`[1, 105]` 内
- `0 <= Node.val <= 9`

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} head
 * @return {boolean}
 */
var isPalindrome = function(head) {
    if (head === null || head.next === null) {
        return true
    }
    let fast = head
    let slow = head
    let prev
    while(fast && fast.next) {
        prev = slow
        slow = slow.next
        fast = fast.next.next
    }
    prev.next = null
    // 反转链表
    let head2 = null
    while (slow) {
        const tmp = slow.next
        slow.next = head2
        head2 = slow
        slow = tmp
    }
    while (head && head2) {
        if (head.val !== head2.val) {
            return false
        }
        head = head.next
        head2 = head2.next
    }
    return true
};

```

[21. 合并两个有序链表](https://leetcode.cn/problems/merge-two-sorted-lists/)

将两个升序链表合并为一个新的 **升序** 链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。 

 

**示例 1：**

![img](https://assets.leetcode.com/uploads/2020/10/03/merge_ex1.jpg)

```
输入：l1 = [1,2,4], l2 = [1,3,4]
输出：[1,1,2,3,4,4]
```

**示例 2：**

```
输入：l1 = [], l2 = []
输出：[]
```

**示例 3：**

```
输入：l1 = [], l2 = [0]
输出：[0]
```

 

**提示：**

- 两个链表的节点数目范围是 `[0, 50]`
- `-100 <= Node.val <= 100`
- `l1` 和 `l2` 均按 **非递减顺序** 排列

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} list1
 * @param {ListNode} list2
 * @return {ListNode}
 */
var mergeTwoLists = function(list1, list2) {
    let res = new ListNode()
    let cur = res
    while(list1 && list2) {
        // 比较大小
        if (list1.val < list2.val) {
            cur.next = list1
            list1 = list1.next
        }
        else {
            cur.next = list2
            list2 = list2.next
        }
        cur = cur.next
    }
    if (list1) {
        cur.next = list1
    }
    if (list2) {
        cur.next = list2
    }
    return res.next
};
```

[141. 环形链表](https://leetcode.cn/problems/linked-list-cycle/)

给你一个链表的头节点 `head` ，判断链表中是否有环。

如果链表中有某个节点，可以通过连续跟踪 `next` 指针再次到达，则链表中存在环。 为了表示给定链表中的环，评测系统内部使用整数 `pos` 来表示链表尾连接到链表中的位置（索引从 0 开始）。**注意：`pos` 不作为参数进行传递** 。仅仅是为了标识链表的实际情况。

*如果链表中存在环* ，则返回 `true` 。 否则，返回 `false` 。

 

**示例 1：**

![img](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/07/circularlinkedlist.png)

```
输入：head = [3,2,0,-4], pos = 1
输出：true
解释：链表中有一个环，其尾部连接到第二个节点。
```

**示例 2：**

![img](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/07/circularlinkedlist_test2.png)

```
输入：head = [1,2], pos = 0
输出：true
解释：链表中有一个环，其尾部连接到第一个节点。
```

**示例 3：**

![img](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/07/circularlinkedlist_test3.png)

```
输入：head = [1], pos = -1
输出：false
解释：链表中没有环。
```

 

**提示：**

- 链表中节点的数目范围是 `[0, 104]`
- `-105 <= Node.val <= 105`
- `pos` 为 `-1` 或者链表中的一个 **有效索引** 。

 

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */

/**
 * @param {ListNode} head
 * @return {boolean}
 */
var hasCycle = function(head) {
    let slow = head, fast = head
    while (fast && fast.next) {
        slow = slow.next
        fast = fast.next.next
        if (slow == fast) return true
    }
    return false
};
```

[83. 删除排序链表中的重复元素](https://leetcode.cn/problems/remove-duplicates-from-sorted-list/)

给定一个已排序的链表的头 `head` ， *删除所有重复的元素，使每个元素只出现一次* 。返回 *已排序的链表* 。

 

**示例 1：**

![img](https://assets.leetcode.com/uploads/2021/01/04/list1.jpg)

```
输入：head = [1,1,2]
输出：[1,2]
```

**示例 2：**

![img](https://assets.leetcode.com/uploads/2021/01/04/list2.jpg)

```
输入：head = [1,1,2,3,3]
输出：[1,2,3]
```

 

**提示：**

- 链表中节点数目在范围 `[0, 300]` 内
- `-100 <= Node.val <= 100`
- 题目数据保证链表已经按升序 **排列**

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} head
 * @return {ListNode}
 */
var deleteDuplicates = function(head) {
    if (!head) {
        return head
    }
    let cur = head
    while(cur.next) {
        if (cur.val === cur.next.val) {
            cur.next = cur.next.next
        }
        else {
            cur = cur.next
        }
    }
    return head
};
```



[24. 两两交换链表中的节点](https://leetcode.cn/problems/swap-nodes-in-pairs/)

给你一个链表，两两交换其中相邻的节点，并返回交换后链表的头节点。你必须在不修改节点内部的值的情况下完成本题（即，只能进行节点交换）。

 

**示例 1：**

![img](https://assets.leetcode.com/uploads/2020/10/03/swap_ex1.jpg)

```
输入：head = [1,2,3,4]
输出：[2,1,4,3]
```

**示例 2：**

```
输入：head = []
输出：[]
```

**示例 3：**

```
输入：head = [1]
输出：[1]
```

 

**提示：**

- 链表中节点的数目在范围 `[0, 100]` 内
- `0 <= Node.val <= 100`

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} head
 * @return {ListNode}
 */
var swapPairs = function(head) {
    if (!head || !head.next) {
        return head
    }
    const newHead = head.next 
    head.next = swapPairs(newHead.next)
    newHead.next = head
    return newHead
};
```

[692. 前K个高频单词](https://leetcode.cn/problems/top-k-frequent-words/)

给定一个单词列表 `words` 和一个整数 `k` ，返回前 `k` 个出现次数最多的单词。

返回的答案应该按单词出现频率由高到低排序。如果不同的单词有相同出现频率， **按字典顺序** 排序。

 

**示例 1：**

```
输入: words = ["i", "love", "leetcode", "i", "love", "coding"], k = 2
输出: ["i", "love"]
解析: "i" 和 "love" 为出现次数最多的两个单词，均为2次。
    注意，按字母顺序 "i" 在 "love" 之前。
```

**示例 2：**

```
输入: ["the", "day", "is", "sunny", "the", "the", "the", "sunny", "is", "is"], k = 4
输出: ["the", "is", "sunny", "day"]
解析: "the", "is", "sunny" 和 "day" 是出现次数最多的四个单词，
    出现次数依次为 4, 3, 2 和 1 次。
```

 

**注意：**

- `1 <= words.length <= 500`
- `1 <= words[i] <= 10`
- `words[i]` 由小写英文字母组成。
- `k` 的取值范围是 `[1, **不同** words[i] 的数量]`

```javascript
/**
 * @param {string[]} words
 * @param {number} k
 * @return {string[]}
 */
var topKFrequent = function(words, k) {
    const map = new Map()
    for (let word of words) {
        if (map.get(word)) {
            map.set(word,map.get(word)+ 1)
        } else {
            map.set(word, 1)
        } 
    }
    const arr = []
    for (const key of map.keys()) {
        arr.push(key)
    }
    arr.sort((word1, word2)=> {
        return map.get(word1) === map.get(word2) ? word1.localeCompare(word2) : map.get(word2) - map.get(word1)
    })
    return arr.slice(0,k)
};
```

[686. 重复叠加字符串匹配](https://leetcode.cn/problems/repeated-string-match/)

给定两个字符串 `a` 和 `b`，寻找重复叠加字符串 `a` 的最小次数，使得字符串 `b` 成为叠加后的字符串 `a` 的子串，如果不存在则返回 `-1`。

**注意：**字符串 `"abc"` 重复叠加 0 次是 `""`，重复叠加 1 次是 `"abc"`，重复叠加 2 次是 `"abcabc"`。

 

**示例 1：**

```
输入：a = "abcd", b = "cdabcdab"
输出：3
解释：a 重复叠加三遍后为 "abcdabcdabcd", 此时 b 是其子串。
```

**示例 2：**

```
输入：a = "a", b = "aa"
输出：2
```

**示例 3：**

```
输入：a = "a", b = "a"
输出：1
```

**示例 4：**

```
输入：a = "abc", b = "wxyz"
输出：-1
```

 

**提示：**

- `1 <= a.length <= 104`
- `1 <= b.length <= 104`
- `a` 和 `b` 由小写英文字母组成

```javascript
/**
 * @param {string} a
 * @param {string} b
 * @return {number}
 */
var repeatedStringMatch = function(a, b) {
    if (a.indexOf(b) !== -1) { //如果a直接包含b
        return 1
    }
    let num = 1
    let str = a
    while (str.length <= (b.length + a.length * 2)) { //判断的最大边界是b.length + a.length * 2
        str += a;
        num += 1
        if (str.indexOf(b) !== -1) { //如果b存在于新的strz中返回重复的次数
            return num
        }
    }
    return -1
};
```

[70. 爬楼梯](https://leetcode.cn/problems/climbing-stairs/)

假设你正在爬楼梯。需要 `n` 阶你才能到达楼顶。

每次你可以爬 `1` 或 `2` 个台阶。你有多少种不同的方法可以爬到楼顶呢？

 

**示例 1：**

```
输入：n = 2
输出：2
解释：有两种方法可以爬到楼顶。
1. 1 阶 + 1 阶
2. 2 阶
```

**示例 2：**

```
输入：n = 3
输出：3
解释：有三种方法可以爬到楼顶。
1. 1 阶 + 1 阶 + 1 阶
2. 1 阶 + 2 阶
3. 2 阶 + 1 阶
```

 

**提示：**

- `1 <= n <= 45`

```javascript
/**
 * @param {number} n
 * @return {number}
 */
var climbStairs = function(n) {
    let p = 0, q = 0, r = 1
    for (let i = 0;i<n; i++) {
        p = q
        q = r
        r = p + q
    }
    return r
};
```

[229. 多数元素 II](https://leetcode.cn/problems/majority-element-ii/)

给定一个大小为 *n* 的整数数组，找出其中所有出现超过 `⌊ n/3 ⌋` 次的元素。

 

**示例 1：**

```
输入：nums = [3,2,3]
输出：[3]
```

**示例 2：**

```
输入：nums = [1]
输出：[1]
```

**示例 3：**

```
输入：nums = [1,2]
输出：[1,2]
```

 

**提示：**

- `1 <= nums.length <= 5 * 104`
- `-109 <= nums[i] <= 109`

```javascript
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var majorityElement = function(nums) {
    const map = new Map()
    for (let num of nums) {
        map.set(num, map.has(num)?map.get(num)+1:1)
    }
    const res = []
    map.forEach((value, key)=>{
        if (value>(nums.length/3)) res.push(key)
    })
    return res
};
```

[438. 找到字符串中所有字母异位词](https://leetcode.cn/problems/find-all-anagrams-in-a-string/)

定两个字符串 `s` 和 `p`，找到 `s` 中所有 `p` 的 **异位词** 的子串，返回这些子串的起始索引。不考虑答案输出的顺序。

**异位词** 指由相同字母重排列形成的字符串（包括相同的字符串）。

 

**示例 1:**

```
输入: s = "cbaebabacd", p = "abc"
输出: [0,6]
解释:
起始索引等于 0 的子串是 "cba", 它是 "abc" 的异位词。
起始索引等于 6 的子串是 "bac", 它是 "abc" 的异位词。
```

 **示例 2:**

```
输入: s = "abab", p = "ab"
输出: [0,1,2]
解释:
起始索引等于 0 的子串是 "ab", 它是 "ab" 的异位词。
起始索引等于 1 的子串是 "ba", 它是 "ab" 的异位词。
起始索引等于 2 的子串是 "ab", 它是 "ab" 的异位词。
```

 

**提示:**

- `1 <= s.length, p.length <= 3 * 104`
- `s` 和 `p` 仅包含小写字母

```javascript
/**
 * @param {string} s
 * @param {string} p
 * @return {number[]}
 */
var findAnagrams = function(s, p) {
    const l = p.length
    if (s.length<l) return []
    const pMap = new Map()
    const sMap = new Map()
    for (let j=0; j<l; j++) {
        pMap.set(p[j], pMap.has(p[j])?pMap.get(p[j])+1: 1)
        sMap.set(s[j], sMap.has(s[j])?sMap.get(s[j])+1: 1)
    }
    function cmpMap(mapA, mapB) {
        for (const [key, value] of mapA) {
            if (!mapB.has(key) || mapB.get(key) !== value) {
                return false
            }
        }
        return true
    }
    const ans = []
    if (cmpMap(pMap, sMap)) ans.push(0)
    for(let i=0; i<s.length-l; i++) {
        if (sMap.get(s[i]==1)) sMap.delete(s[i])
        else sMap.set(s[i],sMap.get(s[i])-1)
        sMap.set(s[i+l], sMap.has(s[i+l])?sMap.get(s[i+l])+1:1)
        if (cmpMap(pMap, sMap)) ans.push(i+1)        
    }
    return ans
};
```

[347. 前 K 个高频元素](https://leetcode.cn/problems/top-k-frequent-elements/)

给你一个整数数组 `nums` 和一个整数 `k` ，请你返回其中出现频率前 `k` 高的元素。你可以按 **任意顺序** 返回答案。

 

**示例 1:**

```
输入: nums = [1,1,1,2,2,3], k = 2
输出: [1,2]
```

**示例 2:**

```
输入: nums = [1], k = 1
输出: [1]
```

 

**提示：**

- `1 <= nums.length <= 105`
- `k` 的取值范围是 `[1, 数组中不相同的元素的个数]`
- 题目数据保证答案唯一，换句话说，数组中前 `k` 个高频元素的集合是唯一的

```javascript
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number[]}
 */
var topKFrequent = function(nums, k) {
    let map = new Map()
    let res = []
    for (let i = 0; i < nums.length; i++) {
        map.set(nums[i],map.has(nums[i])?map.get(nums[i])+1:1)
    }
    // map转二维数组进行排序
    let sortArray = Array.from(map).sort((a,b)=> b[1]-a[1])
    for (let i =0; i< k; i++ ){
        res.push(sortArray[i][0])
    }
    return res
};
```

[3. 无重复字符的最长子串](https://leetcode.cn/problems/longest-substring-without-repeating-characters/)

给定一个字符串 `s` ，请你找出其中不含有重复字符的 **最长子串** 的长度。

 

**示例 1:**

```
输入: s = "abcabcbb"
输出: 3 
解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。
```

**示例 2:**

```
输入: s = "bbbbb"
输出: 1
解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。
```

**示例 3:**

```
输入: s = "pwwkew"
输出: 3
解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
     请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。
```

 

**提示：**

- `0 <= s.length <= 5 * 104`
- `s` 由英文字母、数字、符号和空格组成

```javascript
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function(s) {
    if (s.length<=1) return s.length
    let left = 0 
    let right = 1
    let ans = 0
    let temp
    while(right<s.length) {
        temp = s.slice(left,right)
        if (temp.indexOf(s[right])>-1) {
            left++
            continue
        }
        else {
            right++
        }
        ans = Math.max(ans, right-left)
    }
    return ans
};
```

[49. 字母异位词分组](https://leetcode.cn/problems/group-anagrams/)

给你一个字符串数组，请你将 **字母异位词** 组合在一起。可以按任意顺序返回结果列表。

**字母异位词** 是由重新排列源单词的所有字母得到的一个新单词。

 

**示例 1:**

```
输入: strs = ["eat", "tea", "tan", "ate", "nat", "bat"]
输出: [["bat"],["nat","tan"],["ate","eat","tea"]]
```

**示例 2:**

```
输入: strs = [""]
输出: [[""]]
```

**示例 3:**

```
输入: strs = ["a"]
输出: [["a"]]
```

 

**提示：**

- `1 <= strs.length <= 104`
- `0 <= strs[i].length <= 100`
- `strs[i]` 仅包含小写字母

```javascript
/**
 * @param {string[]} strs
 * @return {string[][]}
 */
var groupAnagrams = function(strs) {
    let map = new Map()
    let ans = []
    strs.forEach((str)=> {
        let temp = str.split('').sort().join('')
        map.has(temp)?map.get(temp).push(str): map.set(temp,[str])
    })
    map.forEach(value=>{
        ans.push(value)
    })
    return ans
};
```

[86. 分隔链表](https://leetcode.cn/problems/partition-list/)

给你一个链表的头节点 `head` 和一个特定值 `x` ，请你对链表进行分隔，使得所有 **小于** `x` 的节点都出现在 **大于或等于** `x` 的节点之前。

你应当 **保留** 两个分区中每个节点的初始相对位置。

 

**示例 1：**

![img](https://assets.leetcode.com/uploads/2021/01/04/partition.jpg)

```
输入：head = [1,4,3,2,5,2], x = 3
输出：[1,2,2,4,3,5]
```

**示例 2：**

```
输入：head = [2,1], x = 2
输出：[1,2]
```

 

**提示：**

- 链表中节点的数目在范围 `[0, 200]` 内
- `-100 <= Node.val <= 100`
- `-200 <= x <= 200`

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} head
 * @param {number} x
 * @return {ListNode}
 */
var partition = function(head, x) {
    let small = new ListNode(0)
    let smallHead = small
    let large = new ListNode(0)
    let largeHead = large
    while(head) {
        if (head.val<x) {
            small.next = head
            small = small.next
         }
        else{
            large.next = head
            large = large.next
        }
        head = head.next
    }
    large.next = null
    small.next = largeHead.next
    return smallHead.next
};
```

[15. 三数之和](https://leetcode.cn/problems/3sum/)

给你一个整数数组 `nums` ，判断是否存在三元组 `[nums[i], nums[j], nums[k]]` 满足 `i != j`、`i != k` 且 `j != k` ，同时还满足 `nums[i] + nums[j] + nums[k] == 0` 。请

你返回所有和为 `0` 且不重复的三元组。

**注意：**答案中不可以包含重复的三元组。

 

 

**示例 1：**

```
输入：nums = [-1,0,1,2,-1,-4]
输出：[[-1,-1,2],[-1,0,1]]
解释：
nums[0] + nums[1] + nums[2] = (-1) + 0 + 1 = 0 。
nums[1] + nums[2] + nums[4] = 0 + 1 + (-1) = 0 。
nums[0] + nums[3] + nums[4] = (-1) + 2 + (-1) = 0 。
不同的三元组是 [-1,0,1] 和 [-1,-1,2] 。
注意，输出的顺序和三元组的顺序并不重要。
```

**示例 2：**

```
输入：nums = [0,1,1]
输出：[]
解释：唯一可能的三元组和不为 0 。
```

**示例 3：**

```
输入：nums = [0,0,0]
输出：[[0,0,0]]
解释：唯一可能的三元组和为 0 。
```

 

**提示：**

- `3 <= nums.length <= 3000`
- `-105 <= nums[i] <= 105`

```javascript
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var threeSum = function(nums) {
    let ans = []
    const len = nums.length
    if (len<3) return ans
    nums.sort((a,b) => a-b)
    for (let i = 0 ; i<len ; i ++) {
        if (nums[i]>0) return ans
        if (i>0&&nums[i] === nums[i-1]) continue
        let l = i+1
        let r = len-1
        while(l<r) {
            let sum = nums[i] + nums[l] + nums[r]
            if (sum === 0) {
                ans.push([nums[i],nums[l],nums[r]])
                while(r>l&&nums[l] === nums[l+1]) l++
                while(r>l&&nums[r] === nums[r-1]) r--
                l++
                r--
            }
            else if (sum<0) {
                l++
            }
            else if (sum>0) {
                r--
            }
        }
    }
    return ans
};
```

[16. 最接近的三数之和](https://leetcode.cn/problems/3sum-closest/)

给你一个长度为 `n` 的整数数组 `nums` 和 一个目标值 `target`。请你从 `nums` 中选出三个整数，使它们的和与 `target` 最接近。

返回这三个数的和。

假定每组输入只存在恰好一个解。

 

**示例 1：**

```
输入：nums = [-1,2,1,-4], target = 1
输出：2
解释：与 target 最接近的和是 2 (-1 + 2 + 1 = 2) 。
```

**示例 2：**

```
输入：nums = [0,0,0], target = 1
输出：0
```

 

**提示：**

- `3 <= nums.length <= 1000`
- `-1000 <= nums[i] <= 1000`
- `-104 <= target <= 104`

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var threeSumClosest = function(nums, target) {
    let N = nums.length
    let res = Number.MAX_SAFE_INTEGER
    nums.sort((a, b) => a - b)
    for (let i = 0; i < N; i++) {
        let left = i + 1
        let right = N - 1
        while (left < right) {
            let sum = nums[i] + nums[left] + nums[right]
            if (Math.abs(sum - target) < Math.abs(res - target)) {
                res = sum
            }
            if (sum < target) {
                left++
            } else if (sum > target) {
                right--
            } else {
                return sum
            }
        }
    }
    return res
};

```

[27. 移除元素](https://leetcode.cn/problems/remove-element/)

给你一个数组 `nums` 和一个值 `val`，你需要 **[原地](https://baike.baidu.com/item/原地算法)** 移除所有数值等于 `val` 的元素，并返回移除后数组的新长度。

不要使用额外的数组空间，你必须仅使用 `O(1)` 额外空间并 **[原地 ](https://baike.baidu.com/item/原地算法)修改输入数组**。

元素的顺序可以改变。你不需要考虑数组中超出新长度后面的元素。

 

**说明:**

为什么返回数值是整数，但输出的答案是数组呢?

请注意，输入数组是以**「引用」**方式传递的，这意味着在函数里修改输入数组对于调用者是可见的。

你可以想象内部操作如下:

```
// nums 是以“引用”方式传递的。也就是说，不对实参作任何拷贝
int len = removeElement(nums, val);

// 在函数里修改输入数组对于调用者是可见的。
// 根据你的函数返回的长度, 它会打印出数组中 该长度范围内 的所有元素。
for (int i = 0; i < len; i++) {
    print(nums[i]);
}
```

 

**示例 1：**

```
输入：nums = [3,2,2,3], val = 3
输出：2, nums = [2,2]
解释：函数应该返回新的长度 2, 并且 nums 中的前两个元素均为 2。你不需要考虑数组中超出新长度后面的元素。例如，函数返回的新长度为 2 ，而 nums = [2,2,3,3] 或 nums = [2,2,0,0]，也会被视作正确答案。
```

**示例 2：**

```
输入：nums = [0,1,2,2,3,0,4,2], val = 2
输出：5, nums = [0,1,4,0,3]
解释：函数应该返回新的长度 5, 并且 nums 中的前五个元素为 0, 1, 3, 0, 4。注意这五个元素可为任意顺序。你不需要考虑数组中超出新长度后面的元素。
```

 

**提示：**

- `0 <= nums.length <= 100`
- `0 <= nums[i] <= 50`
- `0 <= val <= 100`

```javascript
/**
 * @param {number[]} nums
 * @param {number} val
 * @return {number}
 */
var removeElement = function(nums, val) {
    let l = nums.length
    for (let i= 0;i<l;i++)  {
        if (nums[i] === val) {
            nums.splice(i,1)
            i--
            l--
        }
    }
};
```

[406. 根据身高重建队列](https://leetcode.cn/problems/queue-reconstruction-by-height/)

假设有打乱顺序的一群人站成一个队列，数组 `people` 表示队列中一些人的属性（不一定按顺序）。每个 `people[i] = [hi, ki]` 表示第 `i` 个人的身高为 `hi` ，前面 **正好** 有 `ki` 个身高大于或等于 `hi` 的人。

请你重新构造并返回输入数组 `people` 所表示的队列。返回的队列应该格式化为数组 `queue` ，其中 `queue[j] = [hj, kj]` 是队列中第 `j` 个人的属性（`queue[0]` 是排在队列前面的人）。

 



**示例 1：**

```
输入：people = [[7,0],[4,4],[7,1],[5,0],[6,1],[5,2]]
输出：[[5,0],[7,0],[5,2],[6,1],[4,4],[7,1]]
解释：
编号为 0 的人身高为 5 ，没有身高更高或者相同的人排在他前面。
编号为 1 的人身高为 7 ，没有身高更高或者相同的人排在他前面。
编号为 2 的人身高为 5 ，有 2 个身高更高或者相同的人排在他前面，即编号为 0 和 1 的人。
编号为 3 的人身高为 6 ，有 1 个身高更高或者相同的人排在他前面，即编号为 1 的人。
编号为 4 的人身高为 4 ，有 4 个身高更高或者相同的人排在他前面，即编号为 0、1、2、3 的人。
编号为 5 的人身高为 7 ，有 1 个身高更高或者相同的人排在他前面，即编号为 1 的人。
因此 [[5,0],[7,0],[5,2],[6,1],[4,4],[7,1]] 是重新构造后的队列。
```

**示例 2：**

```
输入：people = [[6,0],[5,0],[4,0],[3,2],[2,2],[1,4]]
输出：[[4,0],[5,0],[2,2],[3,2],[1,4],[6,0]]
```

 

**提示：**

- `1 <= people.length <= 2000`
- `0 <= hi <= 106`
- `0 <= ki < people.length`
- 题目数据确保队列可以被重建

```javascript
/**
 * @param {number[][]} people
 * @return {number[][]}
 */

var reconstructQueue = function(people) {
    if (!people || !people.length) return [];
    people.sort((a, b) => a[0] === b[0] ? a[1] - b[1] : b[0] - a[0]);
    const res = [];
    people.forEach(item => {
        res.splice(item[1], 0, item); // 插入到k对应的位置
    })
    return res;
};

```

[61. 旋转链表](https://leetcode.cn/problems/rotate-list/)

给你一个链表的头节点 `head` ，旋转链表，将链表每个节点向右移动 `k` 个位置。

 

**示例 1：**

![img](https://assets.leetcode.com/uploads/2020/11/13/rotate1.jpg)

```
输入：head = [1,2,3,4,5], k = 2
输出：[4,5,1,2,3]
```

**示例 2：**

![img](https://assets.leetcode.com/uploads/2020/11/13/roate2.jpg)

```
输入：head = [0,1,2], k = 4
输出：[2,0,1]
```

 

**提示：**

- 链表中节点的数目在范围 `[0, 500]` 内
- `-100 <= Node.val <= 100`
- `0 <= k <= 2 * 109`

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} head
 * @param {number} k
 * @return {ListNode}
 */
var rotateRight = function(head, k) {
    if (k === 0 || !head || !head.next) return head
    let originHead = head
    let length = 1
    while(head.next) {
        head = head.next
        length++
    }
    // 此时head指向末尾节点，连接成环
    head.next = originHead
    // 计算移动单位
    k = length- k % length 
    while (k--) {
        head = head.next
    }
    originHead = head.next
    head.next = null
    return originHead
};
```

[729. 我的日程安排表 I](https://leetcode.cn/problems/my-calendar-i/)

实现一个 `MyCalendar` 类来存放你的日程安排。如果要添加的日程安排不会造成 **重复预订** ，则可以存储这个新的日程安排。

当两个日程安排有一些时间上的交叉时（例如两个日程安排都在同一时间内），就会产生 **重复预订** 。

日程可以用一对整数 `start` 和 `end` 表示，这里的时间是半开区间，即 `[start, end)`, 实数 `x` 的范围为，  `start <= x < end` 。

实现 `MyCalendar` 类：

- `MyCalendar()` 初始化日历对象。
- `boolean book(int start, int end)` 如果可以将日程安排成功添加到日历中而不会导致重复预订，返回 `true` 。否则，返回 `false` 并且不要将该日程安排添加到日历中。

 

**示例：**

```
输入：
["MyCalendar", "book", "book", "book"]
[[], [10, 20], [15, 25], [20, 30]]
输出：
[null, true, false, true]

解释：
MyCalendar myCalendar = new MyCalendar();
myCalendar.book(10, 20); // return True
myCalendar.book(15, 25); // return False ，这个日程安排不能添加到日历中，因为时间 15 已经被另一个日程安排预订了。
myCalendar.book(20, 30); // return True ，这个日程安排可以添加到日历中，因为第一个日程安排预订的每个时间都小于 20 ，且不包含时间 20 。
```

 

**提示：**

- `0 <= start < end <= 109`
- 每个测试用例，调用 `book` 方法的次数最多不超过 `1000` 次。

```javascript
var MyCalendar = function() {
    this.bookArr = []
};

/** 
 * @param {number} start 
 * @param {number} end
 * @return {boolean}
 */
MyCalendar.prototype.book = function(start, end) {
    for (let item of this.bookArr) {
        let l = item[0], r = item[1]
        if (l<end && r>start) {
            return false
        }
    }
    this.bookArr.push([start, end])
    return true
};

/**
 * Your MyCalendar object will be instantiated and called as such:
 * var obj = new MyCalendar()
 * var param_1 = obj.book(start,end)
 */
```

[946. 验证栈序列](https://leetcode.cn/problems/validate-stack-sequences/)

给定 `pushed` 和 `popped` 两个序列，每个序列中的 **值都不重复**，只有当它们可能是在最初空栈上进行的推入 push 和弹出 pop 操作序列的结果时，返回 `true`；否则，返回 `false` 。

 

**示例 1：**

```
输入：pushed = [1,2,3,4,5], popped = [4,5,3,2,1]
输出：true
解释：我们可以按以下顺序执行：
push(1), push(2), push(3), push(4), pop() -> 4,
push(5), pop() -> 5, pop() -> 3, pop() -> 2, pop() -> 1
```

**示例 2：**

```
输入：pushed = [1,2,3,4,5], popped = [4,3,5,1,2]
输出：false
解释：1 不能在 2 之前弹出。
```

 

**提示：**

- `1 <= pushed.length <= 1000`
- `0 <= pushed[i] <= 1000`
- `pushed` 的所有元素 **互不相同**
- `popped.length == pushed.length`
- `popped` 是 `pushed` 的一个排列

```javascript
/**
 * @param {number[]} pushed
 * @param {number[]} popped
 * @return {boolean}
 */
var validateStackSequences = function(pushed, popped) {
     const stack = []
     const n = pushed.length
     for (let i=0, j=0; i<n; i++) {
          stack.push(pushed[i])
          while(stack.length && stack[stack.length-1] == popped[j]) {
              stack.pop()
              j++
          }
     }
     return stack.length===0
};
```

### JS中树定义

```javascript
function treeNode(val, left, right) {
	this.val = (val===undefined? 0 : val)
	this.left = (left===undefined? null: left)
    this.right = (right===undefined? null: right)
}
```

