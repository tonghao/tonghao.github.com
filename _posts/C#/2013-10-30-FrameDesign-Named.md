---
layout: default
title: .net命名规范
---

## {{ page.title }}

##.net命名规范
--------
###**大小写**

两种：

> - PascalCasing:于由多个单词构成的名字空间、类型、成员名字
> - camelCasing:用于参数的名字

###**通用命名约定**

>- **单词选择**：易阅读；不要用下划线、连字符；不要用匈牙利命名法；避免关键字

>- **不要用缩写**：常用可以，IO、Html、Xml

>- **复合词/术语**：复合词作为一个单词；
 
>- **新版本API命名**：与旧API相似，使用后缀表示版本

### **程序集和DLL命名**
### **名字空间命名**

> - 公司名称作为前缀，产品名称（要求稳定、与版本无关）为第二层，采用PascalCasing，可考虑复数形式
 - 避免名字空间与类型空间的冲突
 - 四种名字空间：
    1. **应用程序模型名字空间：**属于单个应用程序模型的名字空间经常在一起使用，但是它们几乎从不和属于其他应用程序模型的名字空间一起使用。
         - System.Windows
         - System.Web.UI
    2. **基础设施名字空间**：开发常用的应用程序很少会导入的名字空间
        - System.Windows.Form.Design
        - *.Design
        - *.Permissions
    3. **核心名字空间:**：包括所有的System名字空间，但应用程序模型名字空间和基础设施名字空间除外，包括如：System、System.IO、System.Xml、System.Net等
    4. **技术名字空间**：
包括所有以相同两个前缀（<Company>.<Technology>*）开始的名字空间

### **类、结构、接口命名**

> - 类、结构：名词或名词短语命名
- 接口：形容诩短语，少数用名词/短语；以I开头
- 派生类的末尾考虑用基类名字
- 接口标准实现类/接口只相差***I***字符

- **泛型**

> - 用单字符描述参数/用描述性命字命名参数：`<T>,<TSeession>,<TInput>`

- **常用类型的命名**

   基类                    | 派生/实现类型的规范
   ----------------------- | ----------------------------------
   System.Attribute        | 要给自定义的修饰属性类添加“Attribute”后缀
   System.Delegate         | 给用于事件处理的委托添加“EventHandle”后缀
   System.Delegate         | 给用于事件处理之外的委托添加“Callback”后缀
   System.Delegate         | 不要添加“Delegates”后缀
   System.Enum             | 不要派生自该类，用enum关键字
   System.Exception        | 要添加“Exception”后缀
   ----------------------- |-----------------------------
   IEnumerable         | 要添加“Collection”后缀
   ICollection         | 要添加“Collection”后缀
   IList               | 要添加“Collection”后缀
   IEnumerable<T>         | 要添加“Collection”后缀
   ICollection<T>         | 要添加“Collection”后缀
   IList<T>         | 要添加“Collection”后缀
   ---|---
   System.IO.Stream        | 要添加“Stream”后缀
   CodeAccessPermission    | 要添加“Permission”后缀
   Ipermission             | 要添加“Permission”后缀
 
   
- **枚举类型命名**

> - 单数名词命名枚举类型
- 复数名词命名位域
- 不要加类型名上加后缀：如：ColorFlag
- 不要在类型的值上加前缀(与C++相反)：如：  
```C#
    public enum ImageMode {
        Bitmap  == 0,
        GrayScale = 1,
        Index = 2,
        Rgb = 3,
    }
```

### **类型成员命名**   

> - **方法**:用动词或短语
- **属性**：
    - 名词、名词短语或形容词
    - 集合用其中项目的复数形式，不要用短语单数加"List/Collection"
    - 用肯定式短语命名布尔属性，可加“Is”、“Can”、“Has”前缀
- **事件**：
    - 表动作，正在发生或已经发生，用动词或动词短语命名事件如：`Clicked`，`Painting`,`DrioppedDown`
    - 用现在时和过去时赋予事件名以前和之后的概念，不要用Before/After
    - 事件处理程序加上`EventHandler`后缀
    - 避免创建自定义的事件处理程序，用`EventHandler<TEventArgs>`委托
    - 用`sender`和`e`作为两个参数的名字
    - 命名事件的参数类时，加上`EventArgs`后缀
- **字段**：
    - 指静态公用字段和静态保护字段
    - 用PascalCasing风格
    - 用名诩、名词短语或形容词来命名
    - 不要给字段添加前缀
    
### **参数的命名**

> - 用camelCasing风格
- 用具有描述性的参数名
```C#
    public class String {
        public bool Contain (String value);
        public String Remove(int startIndex, int count);
    }
```
    
> - 考虑参数的意思而不是参数的类型

- **重载操作符的参数的命名** 

> - 参数无具体含义，用left和right来命名重载二元操作符的参数
- 要用value来命名一元操作符参数
- 如可名字表达意义，可用有意义名字重载操作符参数
- 命名重载操作符参数时，不用缩写或数字编号

### **资源命名**
> - 命名资源键（resource key）时使用PascalCasing风格
- 名字具有描述性
- 不要用关键字
- 仅使用字母、数字、下划线
- 异常消息资源应当是异常的类型名加上简短的异常标识符
