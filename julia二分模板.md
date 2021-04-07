# julia二分模板
## 查找一个数
### 思路
* **首先定义解空间为`[left, right]`，注意是左右都闭合**
* 由于定义的解空间为`[left, right]`，因此当`left <= right`的时候，解空间都不为空，此时我们都需要继续搜索。也就是说终止搜索条件应该为`left <= right`。
* 循环体内，我们不断计算`mid`，并将`ums[mid]`与目标值比对。
    * 如果`nums[mid]`等于目标值， 则提前返回`mid`（只需要找到一个满足条件的即可）
    * 如果`nums[mid]`小于目标值， 说明目标值在`mid`右侧，这个时候解空间可缩小为`[mid + 1, right]`（`mid`以及`mid`左侧的数字被我们排除在外）
    * 如果`nums[mid]`大于目标值， 说明目标值在`mid`左侧，这个时候解空间可缩小为`[left, mid - 1]`（`mid`以及`mid`右侧的数字被我们排除在外）
    * 循环结束都没有找到，则说明找不到，返回 -1 表示未找到。
```julia
function binary_search(nums, target)
    left, right = 1, length(nums)
    while left <= right
        mid = (left + right) >> 1
        nums[mid] == target && return mid
        nums[mid] < target && left = mid + 1
        nums[mid] > target && right = mid - 1
    end

    return -1
end
```

## 寻找最左插入位置
上面我们讲了**寻找满足条件**的值。如果找不到，就返回`-1`。那如果不是返回`-1`，而是返回应该插入的位置，使得插入之后列表仍然有序呢？

比如一个数组`nums: [1,3,4]`，target 是 2。我们应该将其插入（注意不是真的插入）的位置是索引`1`的位置，即`[1,「2」,3,4]`。因此**寻找最左插入位置**应该返回`1`，而**寻找满足条件的位置**应该返回`-1`。

另外如果有多个满足条件的值，我们返回最左侧的。比如一个数组`nums: [1,2,2,2,3,4]`，`target`是`2`，我们应该插入的位置是`1`。

### 思路
* **首先定义解空间为`[left, right]`，注意是左右都闭合**
* 由于定义的解空间为`[left, right]`，因此当`left <= right`的时候，解空间都不为空，此时我们都需要继续搜索。也就是说终止搜索条件应该为`left <= right`。
* 当`x <= A[mid]`，说明找到一个备胎，我们令`r = mid - 1`将`mid`从解空间排除，继续看看有没有更好的备胎。

* 当`x > A[mid]`，说明`mid`根本就不是答案，直接更新`l = mid + 1`，从而将`mid`从解空间排除。

* 最后解空间的`l`就是最好的备胎，备胎转正。

```julia
function bisect_left(nums, x)
    # 内置api
    left = searchsortedfirst(nums, x)
    # 手写
    left, right = 1, length(nums)
    while left <= right
        mid = (left + right) >> 1
        if x <= A[mid]
            right = mid - 1
        else
            left = mid + 1
        end
    end

    return left
end
```

## 寻找最右插入位置

### 思路
* **首先定义解空间为`[left, right]`，注意是左右都闭合**
* 由于定义的解空间为`[left, right]`，因此当`left <= right`的时候，解空间都不为空，此时我们都需要继续搜索。也就是说终止搜索条件应该为`left <= right`。
* 当`x < A[mid]`，说明找到一个备胎，我们令`r = mid - 1`将`mid`从解空间排除，继续看看有没有更好的备胎。

* 当`x >= A[mid]`，说明`mid`根本就不是答案，直接更新`l = mid + 1`，从而将`mid`从解空间排除。

* 最后解空间的`l`就是最好的备胎，备胎转正。

```julia
function bisect_right(nums, x)
    # 内置api
    left = searchsortedlast(nums, x)
    # 手写
    left, right = 1, length(nums)
    while left <= right
        mid = (left + right) >> 1
        if x >= nums[mid]
            left = mid + 1
        else
            right = mid - 1
        end
    end

    return left
end
```


**注**：以上内容转载并改编自[力扣加加](https://lucifer.ren/blog/categories/%E4%BA%8C%E5%88%86/)