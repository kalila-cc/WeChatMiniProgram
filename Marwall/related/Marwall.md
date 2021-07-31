[TOC]

# 更新时间

## 2020-05-24

# 代码结构

## `userInfo`（用户信息）

+ `openid: String`（身份：微信授权后默认直接注册并加入数据库）
+ `avatar: String`（头像：新用户默认为`null`）
+ `nickname: String`（昵称：新用户默认用 "新用户+时间戳" 命名）
+ `realname: String`（姓名：新用户默认为`null`）
+ `gender: String`（性别：新用户默认为`null`，可选项目为`[男, 女]`）
+ `tel: Number`（手机号：新用户默认为`null`，授权手机号后即可发帖留言等（临时性））
+ `wxid: String`（微信号：新用户默认为`null`）
+ `qq: Number`（QQ号：新用户默认为`null`）
+ `campus: String`（学校：新用户默认为`null`，目前设置可选项目为`[河源中学]`）
+ `grade: String`（年级：新用户默认为`null`，目前设置可选项目为`[高一, 高二, 高三]`）
+ `certification: Boolean`（认证：新用户默认为`false`）
+ `like: Array<Object>`（点赞：新用户默认为`[]`）
  + `postid: Number`
  + `index: Array<Number>`
+ `comment: Array<Object>`（评论：新用户默认为`[]`）
  + `postid: Number`
  + `index: Array<Number>`
+ `view: Array<Number>`（浏览：存储`postid`，新用户默认为`[]`）
+ `report: Array<Object>`（举报：新用户默认为`[]`）
  + `postid: Number`
  + `index: Array<Number>`

## `post`（帖子信息）

+ `postid: Number`（编号：由`(new Date().getTime()` 确定，即时间戳)
+ `type: String`（类型：目前设置可选项目为`[confession(表白墙), QA(问答墙), transaction(交易墙), help(雷锋墙), complaint(吐槽墙), community(社团墙), study(致习室), topic(话题街), message(留言巷), activity(活动站), advise(添砖瓦)]`）
+ `postedby: Object`（发布者）
  + `openid: String`（身份：便于追溯）
  + `avatar: String`（头像：便于显示）
  + `nickname: String`（昵称：便于显示）
+ `title: String`（标题）
+ `label: Array<String>`（标签：可以为空，默认为`[]`）
+ `price: Number`（价格：非负整数，可以为空，必须在`[0,9999.99]`，默认为 0）
+ `content: String`（内容：限制 140 字）
+ `image: Array<String>`（配图：可以为空，最多 9 张，默认为`[]`）
+ `posttime: Number`（时间戳）
+ `status: Object`（状态）
  + `anonymous: Boolean`（匿名：布尔值）
  + `hot: Number`（热度：非负整数，初始化为 0，同一个人浏览多次仅算作一次）
  + `like: Number`（点赞：非负整数，初始化为 0，点赞可撤销）
  + `report: Number`（举报：非负整数，初始化为 0，举报可撤销，点击15s后再向数据库发送数据，举报数超过 3 则不显示该评论）
  + `comment: Array<Object>`（评论：初始化为`[]`）
    + `commentedby: Object`（发布者）
      + `openid: String `（身份：便于追溯）
      + `avatar: String`（头像：便于显示）
      + `nickname: String`（昵称：便于显示）
    + `commenttime: Number`（评论时间：时间戳）
    + `content: String`（内容：限制 140 字）
    + `image: Array<String>`（配图：可以为空，最多 9 张，默认为`[]`）
    + `status: Object`（状态）
      + `anonymous: Boolean`（匿名：布尔值）
      + `like: Number`（点赞：非负整数，初始化为 0）
      + `report: Number`（举报：非负整数，初始化为 0，超过 3 则不显示该评论）

## `type`（发帖类型）

### 核心功能

+ `confession`（表白墙）
  + 功能列表（暂定）：包含标签`['高一', '高二', '高三', '班级', '社团', '团队']`（若选则只能选其一）
  + 功能说明：无
+ `QA`（问答墙）
  + 功能列表（暂定）：包含标签`['找组织', '寻资料']`（若选则只能选其一）
  + 功能说明（暂定）：找组织（如分班结果、兴趣爱好等）、寻资料（如段考成绩、参考答案等）
+ `transaction`（交易墙）
  + 功能列表（暂定）：包含标签`['学习类', '生活类', '租赁类', '代劳类']`（若选则只能选其一）
  + 功能说明（暂定）：代劳类（如代买东西等）
+ `help`（雷锋墙）
  + 功能列表（暂定）：包含标签`['寻物启事', '失物招领', '爱心募捐']`（若选则只能选其一）
  + 功能说明（暂定）：无
+ `complaint`（吐槽墙）
  + 功能列表（暂定）：包含标签`[]`
  + 功能说明（暂定）：无
+ `community`（社团墙）
  + 功能列表（暂定）：包含标签`[<所有校内社团>]`（必选且只能选其一）
  + 功能说明（暂定）：无

### 扩展功能

+ `study`（致习室）
  + 功能列表（暂定）：包含标签`[]`
  + 功能说明（暂定）：无
+ `topic`（话题街）
  + 功能列表（暂定）：包含标签`[]`
  + 功能说明（暂定）：无
+ `message`（留言巷）
  + 功能列表（暂定）：包含标签`[]`
  + 功能说明（暂定）：无
+ `activity`（活动站）
  + 功能列表（暂定）：包含标签`[]`
  + 功能说明（暂定）：无
+ `propose`（砖瓦房）
  + 功能列表（暂定）：包含标签`[]`
  + 功能说明（暂定）：无

# 补充说明

## `userInfo`

+ 初始化为`null`并不影响某些属性的数据类型，比如，当`avatar`为`null`时，可以通过短路运算符直接把头像`url`置为`avatar||url`
+ 部分属性可能暂时用不上，但是是为了以后可能的扩展而留后路
+ 点赞评论浏览举报等属性是为了不重复计数

## `post`

+ 并非只有交易帖才可以加上悬赏价格
+ 帖子和评论都能举报，超过 3 人举报即不再显示，举报点击10s后再发送数据到数据库，防止误操作

## `others`

+ 请大家根据对象结构调整核对一下代码
+ 为什么叫雷锋墙呢。。。因为我们学校的失物招领处就叫雷锋岗
+ 为什么叫黑洞呢。。。因为这样就可以名正言顺使劲塞新功能又不破坏核心功能了（作用类似文件夹）
+ 为什么叫砖瓦房呢。。。符合为万能墙添砖加瓦（提建议）的核心理念
+ 其他细节先不补，太多了，遇到了再补充