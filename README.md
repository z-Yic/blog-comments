# blog-comments
用作[博客站点](https://z-yic.github.io/)评论系统的仓库。

博客网站所用工具：

- 网站构建工具：[hugo](https://gohugo.io/)
- 主题：[stack主题](https://github.com/CaiJimmy/hugo-theme-stack)
- 评论功能：[utterances](https://utteranc.es/)
## 给stack主题站点添加utterances评论功能
1. 配置`hugo.toml`启用评论功能，并指定`utterances`作为评论系统；

   ```toml
   [params.comments]
   enabled = true
   provider = 'utterances'
   ```

   - `enabled`：默认值为false，设置为true以启用评论功能；
   - `provides`：所用的评论系统，这里使用`utterances`;

2. 配置utterances：

   1. 创建并登录GitHub账号，新建用于评论的仓库(要求为public)；

   2. 给该仓库安装[utterances app](https://github.com/apps/utterances)；

   3. 在`hugo.toml`中添加关于utterances的配置项；

      ```toml
      [params.comments.utterances]
      repo = "[author/github-repository]"
      issue-term = "url"
      label = "comment"
      ```

      - `repo`：指向那个安装了utterance app的public仓库，值为`用户名/仓库名`；
      - `issue-term`：issue标题，可选值有`pathname`(基于页面路径)，`url`(基于完整 URL)，`title`(基于页面标题)；
      - `label`：标签；
     
  3. 补充说明：
      - 通过[utterance指引](https://utteranc.es/)填写对应信息后会给出对应的js配置，可将需要的片段修改格式后添加到`hugo.toml`中;
      - 当前stack主题只支持以上三个配置项，其它配置不支持，需另外实现；
      - 关于匿名评论，因为utterances是基于github issue，需要登录GitHub账号后评论；

