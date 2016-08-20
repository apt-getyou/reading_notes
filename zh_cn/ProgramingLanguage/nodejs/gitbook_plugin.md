# gitbook 插件

部分插件在Windows下无法正常使用，且版本问题严重

-------------------------------

1. GitBook Ace Plugin  
  [插件地址](https://github.com/ymcatar/gitbook-plugin-ace)  

  使用方法  
  ```C
  {%ace edit=true, lang='c_cpp'%}  
  // This is a hello world program for C.  
  #include <stdio.h>  

  int main(){  
    printf("Hello World!");  
    return 1;  
  }  
  {%endace%}
  ```
  效果  

  {%ace edit=true, lang='c_cpp'%}  
  // This is a hello world program for C.  
  #include <stdio.h>  

  int main(){  
    printf("Hello World!");  
    return 1;  
  }  
  {%endace%}

1. 添加github图标
  [插件地址](https://plugins.gitbook.com/plugin/github)

  ```JSON
  "plugins": [
      "github"
  ],
  "pluginsConfig": {
      "github": {
          "url": "https://github.com/apt-getyou"
      }
  }
  ```

1. KaTex [项目地址](https://github.com/GitbookIO/plugin-katex)

  为了支持数学公式, 我们可以使用KaTex和MathJax插件, 官网上说Katex速度要快于MathJax
  插件地址
  MathJax使用LaTeX语法编写数学公式教程

  ```JSON
  "plugins": [
      "katex"
  ]
  ```

1. Mermaid

  支持渲染Mermaid图表
  [插件地址](https://plugins.gitbook.com/plugin/mermaid)
  ```JSON
  "plugins": [
      "mermaid"
  ]
  ```

1. Tbfed-pagefooter  
  为页面添加页脚  
  [插件地址](https://plugins.gitbook.com/plugin/tbfed-pagefooter)

  ```JSON
  "plugins": [
     "tbfed-pagefooter"
  ],
  "pluginsConfig": {
      "tbfed-pagefooter": {
          "copyright":"Copyright &copy zhangjikai.com 2015",
          "modify_label": "该文件修订时间：",
          "modify_format": "YYYY-MM-DD HH:mm:ss"
      }
  }
  ```

1. GA  
  [google 统计](https://www.google.com/intl/zh-CN_sg/analytics/)  
  [插件地址](https://plugins.gitbook.com/plugin/ga)

  ```JSON
  "plugins": [
      "ga"
   ],
  "pluginsConfig": {
      "ga": {
          "token": "UA-XXXX-Y"
      }
  }
  ```
1. Donate  

  打赏插件  

  [插件地址](https://plugins.gitbook.com/plugin/donate)
  ```JSON
  "plugins": [
      "donate"
  ],
  "pluginsConfig": {
      "donate": {
          "wechat": "http://zhangjikai.com/resource/weixin.png",
          "alipay": "http://zhangjikai.com/resource/alipay.png",
          "title": "",
          "button": "赏",
          "alipayText": "支付宝打赏",
          "wechatText": "微信打赏"
      }
  }
  ```
