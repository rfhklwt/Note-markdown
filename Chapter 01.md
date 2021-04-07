## 模块、包以及数据类型
### 模块和包
#### 1. 创建一个包

* 利用`PkgTemplates`包来快速创建一个包的模板，首先先添加该包，如下：

```shell
(@v1.6) pkg> add PkgTemplates
```

* 接着通过如下方式既可以创建我们的第一个包，比如名字叫`Calculator`：

```shell
julia> using PkgTemplates
julia> template = Template(; license = "MIT", user = "Qling")
┌ Warning: Unrecognized keywords were supplied, see the documentation for help
│   kwargs =
│    Dict{Symbol, String} with 1 entry:
│      :license => "MIT"
└ @
Template:
  authors: ["Qling <rfhklwt@163.com> and contributors"]
  dir: "~/.julia/dev"
  host: "github.com"
  julia: v"1.0.0"
  user: "Qling"
  plugins:
julia> generate(template, "Calculator")
```

* 需要注意的是，默认情况下，`Calculator`包的位置位于`~/.julia/dev`

  

