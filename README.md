# action-test

github-actions 学习 demo，主要注意几个地方：

- 根目录新建 `.github/workflows` 目录，里面新建 `xxx.yml` 文件，配置参考如下：

```yml
name: GitHub Actions Build and Deploy Demo
on:
  push:
    branches:
      - main
jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout
      uses: actions/checkout@v2
    
    - name: 安装依赖和编译.... 🔧 # This example project is built using npm and outputs the result to the 'build' folder. Replace with the commands required to build your project, or remove this step entirely if your site is pre-built.
      run: |
        npm install
        npm run build
    - name: 部署到github-page...
      uses: JamesIves/github-pages-deploy-action@4.1.1
      with:
        token: ${{ secrets.ACCESS_TOKEN }}
        branch: gh-pages
        folder: dist

```

- 这是一个 vue 项目，需要配置 vue 项目打包后的 根目录路径

```js
// /vue.config.js
module.exports = {
  publicPath: '/github-action-test/'
}
```

- 然后，再项目的 `settings` 里面找到 `github-pages` ，配置部署分支即可


相关资料参考：

- [GitHub Actions 入门教程](http://www.ruanyifeng.com/blog/2019/09/getting-started-with-github-actions.html)
- [github-actions market](https://github.com/marketplace?type=actions)
- [vue.config.js](https://cli.vuejs.org/zh/config/)
