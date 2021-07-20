# julia加法模板
## 公式

```
当前位 = (A 的当前位 + B 的当前位 + 进位carry) % 10
```

**注意**：`AB`两数都加完后，最后判断一下进位`carry`, 进位不为`0`的话加在前面。

## 模板

```
while ( A 没完 || B 没完)
    A 的当前位
    B 的当前位

    和 = A 的当前位 + B 的当前位 + 进位carry

    当前位 = 和 % 10;
    进位 = 和 / 10;

判断还有进位吗
```

## 练习

### [两数相加](https://leetcode-cn.com/problems/add-two-numbers/)

### [LC989 数组形式的整数加法](https://leetcode-cn.com/problems/add-to-array-form-of-integer/)

### [LC809 情感丰富的文字](https://leetcode-cn.com/problems/expressive-words/)

* **注**：以上内容转载并改编自[力扣解析](https://leetcode-cn.com/problems/add-to-array-form-of-integer/solution/989-ji-zhu-zhe-ge-jia-fa-mo-ban-miao-sha-8y9r/)