# vue-kindeditor使用帮助



## 1. 创建项目
    
   使用vue官方提供的vue-cli进行创建项目。

   使用npm安装vue-cli
   
    npm install vue-cli -g
   
   等待安装成功
    如果npm安装速度慢，按键盘 Ctrl+c 退出安装。切换下npm镜像为 https://npm.taobao.org/ ,切换方法如下：
    

    npm config set registry https://registry.npm.taobao.org 
    npm config get registry 
（如果上面配置正确，会显示https://registry.npm.taobao.org )
   
    
   完成了上述步骤，接着使用 vue-cli 创建项目。
    
    vue init webpack demo    ( demo为项目名称 )
    cd demo    ( 切换目录到刚刚创建的项目目录 )
    npm install    ( 安装依赖包 )
    npm run dev    ( 运行项目，就可以在浏览器中看到了 )
      

## 2. 添加vue-kindedtior

   在终端项目目录下执行
    
    npm install vue-kindeditor --save-dev
    
   安装成功后，运行 npm run dev 启动项目，就可以在项目中使用了。

## 3.使用vue-kindedtior  

   第一步，编辑 demo/src/main.js 文件

    import Vue from 'vue'
    import App from './App'
    // 引入 vue-kikindeditor 需要的文件
    import VueKindEditor from 'vue-kindeditor'
    import 'kindeditor/kindeditor-all-min.js'
    import 'kindeditor/themes/default/default.css'

    Vue.config.productionTip = false

    // 注册 vue-kikindeditor plugin
    Vue.use(VueKindEditor)

    /* eslint-disable no-new */
    new Vue({
      el: '#app',
      template: '<App/>',
      components: { App }
    })

编辑完配置文件后，就可以在组件中使用了。  

 第二步，编辑 demo/src/components/Hello.vue 文件

   在 template 中添加如下代码

    <template>
      <div class="hello">
         <editor id="editor_id" height="500px" width="700px" :content="editorText"
            pluginsPath="/static/kindeditor/plugins/"
            :loadStyleMode="false"
            @on-content-change="onContentChange"></editor>
      </div>
    </template>

    <script>
    export default {
      name: 'hello',
      data () {
        return {
           editorText: ''
        }
      }, 
      methods: {
        onContentChange (val) {
          this.editorText = val
        }
      }
    }
    </script>

   返回浏览器就可以看到编辑器了。


    使用 editor 标签使用kindeditor。<editor  ...></editor>
    参数：   

        id: 设置编辑器的id，kindeditor创建使用需要用到，所以必填。例子：editor_id  

        content: 用来获取编辑器内容，使用双向绑定获取编辑器内容数据。例子：editorText  

        loadStyleMode: 是否自动加载kindeditor需要的css文件，默认是从 / 查找，所以设置为false，搭配pluginsPath使用  

        pluginsPath: 设置编辑器的plugins目录。例子中为了方便把kindeditor全部目录复制到了demo/static中了，实际使用中地址自行设置。


 更多的设置参数参考kindeditor官方的编辑器初始化参数文档
[http://kindeditor.net/docs/option.html][1]
    

  [1]: http://kindeditor.net/docs/option.html
