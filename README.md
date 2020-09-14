# 学习笔记

## 创建示例工程

```sh
npx create-next-app nextjs-blog --use-npm --example "https://github.com/vercel/next-learn-starter/tree/master/learn-starter"
cd nextjs-blog
npm run dev
```

## 页面导航

### Link 组件

* Client-Side Navigation
  * 相比 a 标签，不会重新加载整个页面，跳转速度更快
  * 通过浏览器开发者工具修改 background 样式，可以验证这一点（跳转时背景色不变）
* Code splitting and prefetching:
  * 每个 page 的代码都是分离的，意味着加载更快
  * 当 Link 出现在可视区域时，会自动预取该页面的代码，这样点击时可以做到几乎实时跳转（生产环境中）
* Note:
  * 如果需要链接到 Next.js 管理之外的链接，请使用 a 标签
  * 如果需要增加属性，例如 className，增加到 a 标签上，例如：  

    ```js
    <Link href="/">
        <a className="foo" target="_blank" rel="noopener noreferrer">
            Hello World
        </a>
    </Link>
    ```

### App 组件

顶级组件，位于 pages/_app.js，该组件可以在页面跳转时保留状态。

另外，全局 CSS 也只能在该文件中使用。

## 资源文件，元数据和样式

Next.js 内建支持 CSS 和 Sass。

public 目录下的文件，可作为根目录下的文件来引用。

通过 Head 组件来修改 title、link 等 head 属性。

[查看如何自定义 html 标签属性](https://nextjs.org/docs/advanced-features/custom-document) 。

内建支持 styled-jsx，示例：

```js
<style jsx>{`
        .container {
          min-height: 100vh;
          padding: 0 0.5rem;
          display: flex;
          flex-direction: column;
          justify-content: center;
          align-items: center;
        }
`}</style>
```

默认组件内生效，不会影响其他组件。
