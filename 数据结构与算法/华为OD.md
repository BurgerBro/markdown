



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

[一年中的第几天]:https://leetcode.cn/problems/day-of-the-year/

```javascript
1154. 一年中的第几天
提示
简单
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

[验证回文串]:https://leetcode.cn/problems/valid-palindrome/

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

