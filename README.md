# Python-BaiduEditor-Tornado
Python3.6和tornado使用百度富文本编辑器示例，可以拖拽上传、读取粘贴板、多图上传、涂鸦、代码编辑、格式、表格等非常丰富的功能，是一款很好的在线编辑工具
使用方法：
1.将static下的ueditor文件夹拷贝到网站的static目录下，upload目录不用管这是自动生成的存放编辑器中图片、多媒体资源的文件夹
2.将templates中的index.HTML中的js文件和富文本框所在的块元素嵌入页面相应位置，使用Ajax获取富文本框内的内容如：
        var article_data = {};
        article_data['content'] = ue["body"]["innerHTML"]
2.将main中的IndexHandler、Upload拷贝到程序中并做相应调整以嵌入原站点、同时增加
            (r"/", IndexHandler),
            (r"/upload", UploadHandler)这两条路由，第一个是用来返回编辑器页面的，第二个是用来给编辑器调用的接口，用来传递编辑器中获取到的多媒体资源
3.修改static/ueditor/ueditor.config.js文件中的
        serverUrl: "/upload" // 服务器统一请求接口路径，更改为主程序中的编辑器调用的接口路由请求地址
4.如果编辑器被遮挡则修改static/ueditor/ueditor.config.js文件中的zIndex : 900     //编辑器层级的基数,默认是900
5.注意：富文本编辑接口没有设置安全项，容易被攻击，可以设置cookie或者token需要的查询手册
