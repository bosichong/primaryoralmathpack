# PrimaryOralMathPack 小学生口算题生成器

## 一、简介
PrimaryOralMathPack是一个功能强大的NPM包，专门用于生成小学生口算题。它可以根据用户指定的各种参数，如运算类型（加法、减法、乘法、除法）的属性、运算步数、题目数量、是否求结果或运算项、是否包含括号以及数值范围和运算符列表等，生成符合要求的口算题数组，为教育工作者或家长创建个性化的口算练习材料提供了便利。

## 二、使用帮助

### 1. 安装
使用npm安装该包：
```bash
npm install PrimaryOralMathPack
```

### 2. 导入
在你的JavaScript项目中，可以通过以下方式导入：
```javascript
const FormulasGenerator = require('PrimaryOralMathPack');
```

### 3. 使用示例
以下是一个使用PrimaryOralMathPack生成口算题的示例：
```javascript
// 创建一个FormulasGenerator实例
const generator = new FormulasGenerator(
    // 加法属性，这里{"carry": 1}表示加法有进位（可根据需要修改）
    {"carry": 1}, 
    // 减法属性，{"abdication": 1}表示减法有退位（可根据需要修改）
    {"abdication": 1}, 
    // 乘法属性（根据具体需求设置）
    null, 
    // 除法属性，{"remainder":2}表示除法是整除（可根据需要修改）
    {"remainder":2}, 
    // 运算步数，这里设置为2步运算
    2, 
    // 生成的口算题数量，这里设置为10道题
    10, 
    // 0表示求运算结果，1表示求运算项（这里以求结果为例）
    0, 
    // 0表示不包含括号，1表示包含括号（这里设置为不包含括号）
    0, 
    // 多步运算的数值范围，这里是示例范围，可按需调整
    [[0, 99], [0, 99], [0, 99], [0, 99], [1, 99]], 
    // 运算符列表，这里示例包含加法和减法，可根据需求修改
    [[1,2],[1],[1]]
);

// 生成口算题
const oralMathProblems = generator.generate();
console.log(oralMathProblems); 
```

在上述示例中：
- `addattrs`、`subattrs`、`multattrs`、`divattrs`分别用于设置加法、减法、乘法、除法的属性。例如，加法属性中的`carry`值可以是1（有进位）、2（无进位）、3（随机进位）。
- `step`指定运算步数，目前仅支持1、2、3步运算，其他值会报错。
- `number`确定要生成的口算题数量。
- `is_result`为0时求运算结果，为1时求运算项。
- `is_bracket`为0时生成的口算题不包含括号，为1时包含括号。
- `multistep`是一个数组，用于定义多步运算中每一步运算数的取值范围。
- `symbols`是一个二维数组，用于指定每一步允许的运算符，例如`[1]`表示加法，`[2]`表示减法，`[3,4]`表示乘法和除法。

通过调整这些参数，可以生成满足不同需求的口算题。