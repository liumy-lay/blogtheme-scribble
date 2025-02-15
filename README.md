# Scribble

A Jekyll theme. [Demo :point_left:](http://scribble.muan.co/posts/scribble-the-jekyll-theme). 

  - Jekyll 是一个静态站点生成器，内置 GitHub Pages 支持，即Github会自动为你的仓库构建网站。Jekyll 是由 Ruby 语言开发而成的网站搭建工具，其可完成由 Markdown 代码仓库生成网站的流程，请确保已经成功安装了Ruby 环境。

![screenshot](https://cloud.githubusercontent.com/assets/1153134/23830104/6d4665e0-06b7-11e7-8805-57e73c346459.png)

## Get started

1. [Fork the repository](https://github.com/liumy-lay/blogtheme-scribble/fork)

2. Clone the repository: `git clone https://github.com/[yourusername]/[blogtheme-scribble]`

3. Run `bundle install`  

   > 如果你已经安装过Jekyll主题，请跳过以下经验
   
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
   - run `jekyll serve -w`报错：```You have already activated public_suffix 6.0.1, but your Gemfile requires public_suffix 5.1.1. Prepending `bundle exec` to your command may solve this. (Gem::LoadError)```版本冲突问题，使用`bundle exec jekyll serve -w`进行本地预览
2. Change `about.md` for blog intro
3. 修改内容后上传到Github仓库
   - `git add .`
   - `git commit -m "修改配置内容"`
   - `git push origin gh-pages`

### Custom domain

For domain settings see [the guide from GitHub](https://help.github.com/articles/setting-up-a-custom-domain-with-pages)

1. 我的域名是在阿里云购买并进行备案的。

2. `github pages` 的 `CNAME` 文件配置：在 GitHub 仓库的根目录下创建或修改 `CNAME` 文件，并在其中输入您的自定义域名`liumyblog.cn`。

3. 阿里云服务器的域名解析设置。

   - **A 记录**：DNS服务器需要知道你的域名指向的 IP 地址，cmd中输入`ping -4 xxx.github.io`，即可找到你的Github Pages的IPv4地址（如果不加-4，得到的是IPv6地址），多ping几次你会发现每次的IP地址都不一样，因为Github官方的IP地址一共有四个，这四个都要添加上：

     ```
     185.199.108.153
     185.199.109.153
     185.199.110.153
     185.199.111.153
     ```

     <img src="./images/image-20241101181222966.png" alt="image-20241101181222966" style="zoom:50%;" />

     ![image-20241101203029532](./images/image-20241101203029532.png)

   - 最后要是实在不确定是否配置成功，去终端`git bash`，进入你的`xxxxx.github.io`文件夹，然后运行命令`nslookup 你的域名`，能看到四个IP地址就是配置成功。

     ![image-20241101203150231](./images/image-20241101203150231.png)

4. 更新`_config.yml`

   在 GitHub 项目的 `_config.yml` 文件中，更新 `url` 字段以匹配您的自定义域名：

   ```
   url: "https://liumyblog.cn"
   baseurl: ""  # 确保 baseurl 为空
   ```

5. 等待 DNS 生效（可能需要几个小时）后，就可以通过 `https://liumyblog.cn` 访问。

6. 注：

   - GitHub 这里会提示检测不到 `www.liumyblog.cn` 的 DNS 记录，导致 `www` 子域无法正确解析到 GitHub Pages。这个提示是因为 GitHub 默认会检查根域（`liumyblog.cn`）和 `www` 子域（`www.liumyblog.cn`）的 DNS 配置。由于不打算使用 `www.liumyblog.cn`，因此没有为 `www` 设置 CNAME 记录，导致 GitHub 检查 `www` 子域时发现配置不正确。<img src="./images/image-20241101203711356.png" alt="image-20241101203711356" style="zoom:50%;" />
   
   - 如果希望消除此提示，可以在阿里云的 DNS 设置中为 `www` 子域添加一个 CNAME 记录指向 `liumy-lay.github.io`，添加新的 DNS 记录，这将让 `www.liumyblog.cn` 也指向 GitHub Pages，同时消除这个警告提示：
     - **主机记录**：`www`
     - **记录类型**：`CNAME`
     - **记录值**：`liumy-lay.github.io`
       ![image-20241101204140152](./images/image-20241101204140152.png)
   
   - 阿里云SSL证书绑定域名，为网站添加HTTPS，教程：https://developer.aliyun.com/article/1595201
   
     ![image-20241101212830073](./images/image-20241101212830073.png)
   
   

## The end

Like it? [Tell me](http://twitter.com/muanchiou).<br/>
Problem? [Use GitHub Issues](https://github.com/muan/scribble).
