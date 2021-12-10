# vue-music

## 下载依赖

```
npm install
```

### 启动项目

```
npm run serve
```

### 打包项目

```
npm run build
```

### 后台 GitHub 地址

https://github.com/Binaryify/NeteaseCloudMusicApi
版本：4.0.23

### 预览地址

[仿网易云音乐预览地址 ](http://47.102.159.133/)

### 目前完成功能

- 歌曲播放器：播放、拖动进度、音量调整、下载、播放列表，歌曲页歌词滚动、评论
- 发现页：推荐、歌单、歌手、排行榜、最新音乐（新歌速递、新碟上架（本周新碟））
- 登录：手机号密码登录，二维码登录，验证码登录，退出登录
- 各详情页
  - 歌单详情页：歌曲列表、歌单页搜索、加载完整歌单、收藏、评论
  - 专辑详情页：歌曲列表、搜索、收藏、评论、专辑详情
  - 歌手详情页：专辑列表、歌手描述、MV、相似歌手
  - 视频详情页：视频播放（使用原生 video 及控件播放）、相似视频推荐、 MV 播放、MV 推荐，点赞、收藏、评论、关注创作者
  - 用户详情页：基本信息（地区需要引入中国省市信息。暂未加入，后续与修改个人信息一起加入）、创建的歌单、收藏的歌单
- 搜索：歌曲、歌手、歌单、用户、MV、专辑搜索、热搜榜、搜索建议、搜索结果快捷入口
- 评论（需要登录）：点赞、回复、评论、评论分页、及页码跳转和回复跳转输入框的动画
- 视频（需要登录）：视频列表、MV 列表、全部 MV 页、MV 排行页
- 我的收藏（需要登录）：收藏的专辑、MV、歌手及筛选功能
- 最近播放（本地存储，不是云端的播放记录）
- 全部页面移动端适配
- 路由懒加载及代码分块，添加未登录情况下导航守卫，路由props解耦合
- 使用 Vuex 管理登录状态、当前歌曲列表及歌曲状态、其余多组件状态

### BUG or UPDATE

- 添加对歌单加载完整歌曲的限制（使用过程中遇到了个 6000 单曲的歌单，使用 trackIds 请求对应歌曲会造成 431 错误）
- 添加对最近播放歌曲数量的限制 11/19
- 解决添加导航守卫后，刷新丢失登录状态，在重新获取完登录状态就错误导航的 bug 11/20
- 添加视频播放时停止歌曲播放
- 解决歌手详情页相似歌手 tab 下切换歌手无法更新数据的状况
- 添加歌词滚动的 js 动画
- 添加路由视图切换的动画
- 添加歌手详情页 Tab 切换加载数据的动画以及为空时的提示
- 添加@根目录,并将 API 按功能模块化，便于管理
- 遇到了作用域具名插槽后备内容打包后不生效的问题，其在开发环境表现正常，暂未解决，只能用到都使用，而不是利用后备内容
- 遇到了超出 JS 最大安全数字的问题，暂未解决（在获取搜索建议时得到的歌曲信息中的图片是 NULL，但是图片 ID 有，只不过超出安全数不准确），可以自己定义 axios 处理数据的方式（axios 默认直接 JSON.parse）,有相关的插件
- 解决歌曲页面评论区点击用户跳转用户路由，但是播放界面不关闭的 bug，以及用户页面不随 id 变化的 bug,删除播放组件重复逻辑
- 移动端 outline 没有圆角，更换为 border
- 将专辑列表、歌单列表、歌手列表整合为一个组件
- 将仅渲染的数据冻结，优化性能
- 将视频详情和 MV 详情页整合为一个组件
- 大部分子页面均使用同一个滚动条，监听路由地址，重置滚动条，以及更换歌曲时重置歌曲播放页滚动条
