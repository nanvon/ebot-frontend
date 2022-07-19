# ebot-frontend

## Project preview
![prewview1](./public/preview1.png)
![prewview1](./public/preview2.png)

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```


### Push to gh-pages Branch & Auto Build on GitHub Pages

After coding, commit on master branch and push it at first.

```sh
git subtree push --prefix dist origin gh-pages
```

---
若执行`git subtree push --prefix dist origin gh-pages`命令时，出现443等网络错误时，采用如下方法：
在`main`分支下执行`npm run build`命令，执行完将dist文件夹内所有文件拷贝到电脑其他位置，切换至`gh-pages`分支，将刚才拷贝的所有文件粘贴到项目根目录，在GitHub Desktop中提交并推送`gh-pages`分支。
