# ASP.NET 期末复习

## ✅ 第一阶段：基础架构与页面构建 (11/22 - 12/03)

**核心目标：掌握基本概念、常用控件属性、导航与登录体系**

### 架构与环境

- [ ] **B/S 与 C/S 结构对比**：B/S 优点（免安装、任意地点），C/S 缺点（局域网限制、操作系统限制）
- [ ] **Web 三层结构**：数据访问层（增删改查）、业务逻辑层（具体逻辑）、页面显示层（显示功能）
- [ ] **.NET Framework 组成**：通用语言开发环境(CLR)、基础类库、开发语言、VS.NET
- [ ] **开发语言对比表**：PHP、JSP、ASP.NET 在运行平台、安全性、开发难度上的区别

### 基础控件

- [ ] **控件类型区别**：HTML控件（客户端运行） vs HTML服务器控件（`runat="server"`） vs Web服务器控件（ASP.NET特有）
- [ ] **TextBox**：`AutoPostBack`（自动回发）、`TextMode`（密码/多行等）
- [ ] **Button**：`Click`事件
- [ ] **RadioButton**：`GroupName`属性（实现互斥关键）
- [ ] **列表控件**：`RadioButtonList`和 `CheckBoxList`的 `RepeatDirection`（排列方式）

### 验证、导航与登录

​	**6大验证控件**：

- [ ]  [ ] `RequiredFieldValidator`（必填）

- [ ]  [ ] `RangeValidator`（范围，如1-100） 

- [ ] [ ] `CompareValidator`（比较两个值） 

- [ ] [ ] `CustomValidator`（自定义函数）

- [ ]  [ ] `RegularExpressionValidator`（正则匹配）

- [ ]  [ ] `ValidationSummary`（汇总错误信息

  **3大导航控件**：

- [ ]  [ ] `Menu`（适合各种网页，动静结合）

- [ ]  [ ] `TreeView`（树形结构，不适合首页）

- [ ]  [ ] `SiteMapPath`（面包屑导航，需配合站点地图）

- [ ] **登录控件**：`Login`（登录）、`LoginView`（区分匿名/登录用户模板）、`PasswordRecovery`（需SMTP配置）

------

## ✅ 第二阶段：核心逻辑与数据交互 (12/04 - 12/17)

**核心目标：攻克 Web 开发最难点——状态管理和数据库连接**

### 状态管理（必考重点）

- [ ] **Session**：服务器内存，默认20分钟，存登录信息，空间小
- [ ] **Cookies**：客户端硬盘，长期有效，存非敏感信息
- [ ] **Application**：全局共享，服务器运行期间有效，需锁定操作
- [ ] **Web.Config**：XML格式，子目录继承父目录配置
- [ ] **Request 与 Response**：Request 接请求，Response 发送信息

### SQL 与 ADO.NET

- [ ] **SQL 四大语句**： [ ] `SELECT ... FROM` [ ] `INSERT INTO ... VALUES` [ ] `UPDATE ... SET ... WHERE` [ ] `DELETE FROM ... WHERE`
- [ ] **SqlConnection 类**：`Open()`打开连接，`Close()`关闭连接
- [ ] **Web.Config 数据库连接串**： [ ] 格式：`<connectionStrings><add name="..." connectionString="..." /></connectionStrings>` [ ] 属性：`AttachDBFilename`（附加数据库）、`User Instance=true`（用户实例）

------

## ✅ 第三阶段：高级数据控件与优化 (12/18 - 12/28)

**核心目标：区分易混淆的数据控件，了解新技术概念**

### 数据绑定控件对比（易混淆）

- [ ] **GridView**：多条显示，自动化高，支持排序/分页/编辑/删除，**不支持插入**
- [ ] **DetailsView**：单条显示，支持插入/编辑/删除，分页只显一条
- [ ] **FormView**：单条显示，模板灵活（需自定义），支持插入/编辑/删除
- [ ] **ListView**：批量显示，支持增删改，模板兼容性较差
- [ ] **GridView 数据源绑定**：`DataSourceID`（推荐，自动功能） vs `DataSource`（需写代码）

### XML、LINQ 与 优化

- [ ] **XML**：用于数据交换
- [ ] **XSLT**：将 XML 转换为 HTML 等其他文档
- [ ] **LINQ 包含内容**：To Objects, To XML, To SQL, To DataSet, To Entities
- [ ] **网站优化 4 方面**：数据库、C#代码、ASP.NET、AJAX
- [ ] **数据库优化 4 点**：存储过程（ADO.NET或LINQ调用）、连接池、查询代码优化

------

## ✅ 第四阶段：考前冲刺 (12/29 - 01/05)

**核心目标：查漏补缺，防止遗忘**

- [ ] **易错点回顾**：Session 和 Cookies 的区别背熟了吗？
- [ ] **代码填空预备**：默写一遍 SQL 的 `INSERT`和 `UPDATE`语句格式
- [ ] **配置检查**：看一眼 Web.config 连接字符串里的 `providerName="System.Data.SqlClient"`

