# Scribble

A Jekyll theme. [Demo :point_left:](http://scribble.muan.co/posts/scribble-the-jekyll-theme). 

  - Jekyll 是一个静态站点生成器，内置 GitHub Pages 支持。Jekyll 是由 Ruby 语言开发而成的网站搭建工具，其可完成由 Markdown 代码仓库生成网站的流程，请确保已经成功安装了Ruby 环境。

![screenshot](https://cloud.githubusercontent.com/assets/1153134/23830104/6d4665e0-06b7-11e7-8805-57e73c346459.png)

## Get started

1. [Fork the repository](https://github.com/liumy-lay/blogtheme-scribble/fork)

2. Clone the repository: `git clone https://github.com/[yourusername]/[blogtheme-scribble]`

3. Run `bundle install`  

   > [!NOTE]
   >
   > 如果你第一次安装Jekyll主题，请参考以下经验

- 安装[Ruby :point_left:](https://rubyinstaller.org/downloads/).
    - <img src="https://github.com/user-attachments/assets/39a5d638-38fb-48b2-9d4b-feccbf7507c4" alt="image" style="zoom:50%;" />
- 我的安装位置：<img src="https://github.com/user-attachments/assets/2ac7e973-d168-409b-8c31-32d6364e7c1e" alt="image" style="zoom:50%;" />

- 安装后，通过在命令行中输入以下命令来确保一切工作正常：

  ```
    $ ruby -v
    ruby 3.3.5(2024-09-03 revision ef084cc8f4)[x64-mingw-ucrt]
    $ bundler -v
    Bundler version 2.5.16
  ```
  - 返回项目根目录下 Run `bundle install`，安装时间较长，大约半小时
  - 遇到的问题及解决方法：
    - ``Bundler 2.5. 16 is running, but your lockfile was generated with 1.10.6. Installing Bundler 1.10.6 and restarting using that version.``删除现有的 Gemfile.lock 文件``rm Gemfile.lock``重新生成 Gemfile.lock 文件``bundle install``
    - bundle install 长时间无响应：这个问题其实是因为bundle install运行的时候需要配置的包比较多、耗时间，解决方法是后面加上--verbose。
    在cmd中按``Ctrl+C``结束当前执行命令，将默认源修改为清华镜像`https://mirrors.tuna.tsinghua.edu.cn/rubygems/`或者阿里云镜像源`https://mirrors.aliyun.com/rubygems/`再执行：
  ```
      # 添加 TUNA 源并移除默认源
      $ gem sources --add https://mirrors.tuna.tsinghua.edu.cn/rubygems/ --remove https://rubygems.org/
      # 列出已有源,应该只有 TUNA 一个
      $ gem sources -l
      *** CURRENT SOURCES ***
      https://mirrors.tuna.tsinghua.edu.cn/rubygems
      # 替换bundle默认源
      $ bundle config mirror.https://rubygems.org https://mirrors.tuna.tsinghua.edu.cn/rubygems
      # 在后面加上--verbose
      $ bundle install --verbose
  ```

4. Run Jekyll: `bundle exec jekyll serve -w`

- `boundler:command not found:jekyll Install missing gem executables with bundle install`：手动安装jekyll `gem install jekyll`

5. Go to `http://localhost:4000` for your site.

---

## Make it yours

1. Edit `_config.yml`, and then rerun `jekyll serve -w`

2. Change `about.md` for blog intro

3. For domain settings see [the guide from GitHub](https://help.github.com/articles/setting-up-a-custom-domain-with-pages)

## The end

Like it? [Tell me](http://twitter.com/muanchiou).<br/>
Problem? [Use GitHub Issues](https://github.com/muan/scribble).
