### 尚硅谷

###### 打包

1.  npm run build
2.  npm install -g serve
3.  serve build
4. 访问 http://localhost:5000

###### git仓库  命令

1. git init  创建仓库
2. git add . 推送到暂存区
3. git commit -m "名字随意"  推送到工作区
4. 仓库地址链接
5. git push -u origin master 推送到远程仓库里面 
6. git checkout -b dev  创建 分支 dev分支  名字随意
7. git branch dev  切换分支名
8. git clone   仓库地址                克隆远程仓库
9. **git checkout -b dev origin/dev**本地dev分支和远程仓库产生关联   根据远程dev分支迅速生成本地dev分支        解释:**git checkout -b  dev切换到别的分支origin/dev  直接推送**
10. git branch   查看当前所在那个分支        已经切换到dev分支上了

###### React 目录结构![](https://upload-images.jianshu.io/upload_images/1987062-7f3b4cd84a7d591a.png?imageMogr2/auto-orient/strip|imageView2/2/w/659/format/webp)

1. assets 目录里面放所有的资源文件。虽然在某些页面里面放上一些图片资源引用起来很方便，但是页面一多就会发现有很多图片是一样的。这时候统一存放资源文件就可以复用一些文件。避免不必要的重复文件占空间。
2. components 目录里存放公共的组件。我对于组件的定义是尽量只实现 UI 呈现方面的事情，业务逻辑可以通过事件传递出去，交给 page 和 module 来实现。
3. pages 目录里存放路由级别的页面。
4. 由于项目中使用了 redux，所以每个页面会有一个 container 用来获取 redux 数据和定义 dispatch 事件。
5. index 里面承载了大部分页面逻辑的处理，以及页面结构的呈现。
6. model 用于定义 redux state 以及数据操作方式。
7. components 目录用于存放仅仅在本页面中会用到的组件。
8. service 目录用于配置和定义 API 接口。
9. modules 目录里面存放了非路由级别的功能模块。它的目录结构和 pages 目录完全一致。只不过这个目录下的模块不能被路由直接访问到。
10. utils 用于定义公共工具函数。
11. page 和 module 通过 container 和 model 来连接 redux 数据，通过 index 来处理大多数页面逻辑。
12. 通过 props 和回调函数传递数据尽量不要超过三层。如果一个 prop 属性会存在 A -> B -> C -> D -> E，并且回调函数是从 E 到 A 的，这必然不合理。
13. 为了低耦合，尽量少的使用 props 和 events。定义 events 的参数也是也少越好。
14. page 不存在 props，module 尽量少定义 props，降低耦合性。
15. 一般只在 page 中使用 module，避免 module 中使用其他 module 形成套娃。

##### 项目源代码基本设计

###### 基本设计

#### **src**/文件夹目录

###### api 				ajax相关

###### assets    		共用资源

###### components    非路由组件

###### config                  配置

###### pages                  路由组件

###### utlis                     工具根组件 

​    **App.js              应用根组件**

​    **index.js            入口js**





