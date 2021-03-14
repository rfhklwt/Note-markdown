# Julia实现回溯模板

## **例子一**: [LC 22](https://leetcode-cn.com/problems/generate-parentheses/) 
```julia
function _generate!(p::String, left::Int, right::Int, res::Vector{String})
    # 递归终结条件
    if right == 0
        push!(res, p)
    else
        # 每一层可以添加的数(左括号和右括号)
        if left > 0
            _generate!(string(p, "("), left - 1, right, res)
        end

        if right > left
            _generate!(string(p, ")"), left, right - 1, res)
        end
    end
end

function generate_parenthesis(n::Int)::Vector{String}
    # 申请一个空间存放所有可能性
    res = String[]
    _generate!("", n, n, res)
    return res
end
```

## **例子二**: [LC 131](https://leetcode-cn.com/problems/palindrome-partitioning/)
```julia
function partition(s::AbstractString)::Vector{Vector{String}}
    n = length(s)
    is_parlindrom = fill(true, n, n)

    for i = n:-1:1, j = (i+1):n
        is_parlindrom[i, j] = (s[i] == s[j]) && is_parlindrom[i+1, j-1]
    end

    res = Vector{Vector{String}}()

    function backtrace!(p::Vector{String}, i::Int)
        if i == n + 1
            push!(res, p[:])
            return
        end

        for j = i:n
            if is_parlindrom[i, j]
                backtrace!(push!(p, SubString(s, i, j)), j + 1)
                pop!(p)
            end
        end
    end

    backtrace!(String[], 1)

    return res
end
```
