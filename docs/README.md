## winforce17的个人笔记
记录了本人计算机学习过程，包含计算机，安全，CTF，运维等各种内容，很多内容还未整理，排版有问题，欢迎PR。
## Material color palette 颜色主题

### Primary colors 主色

> 默认 `white`

点击色块可更换主题的主色

<button data-md-color-primary="red">Red</button>
<button data-md-color-primary="pink">Pink</button>
<button data-md-color-primary="purple">Purple</button>
<button data-md-color-primary="deep-purple">Deep Purple</button>
<button data-md-color-primary="indigo">Indigo</button>
<button data-md-color-primary="blue">Blue</button>
<button data-md-color-primary="light-blue">Light Blue</button>
<button data-md-color-primary="cyan">Cyan</button>
<button data-md-color-primary="teal">Teal</button>
<button data-md-color-primary="green">Green</button>
<button data-md-color-primary="light-green">Light Green</button>
<button data-md-color-primary="lime">Lime</button>
<button data-md-color-primary="yellow">Yellow</button>
<button data-md-color-primary="amber">Amber</button>
<button data-md-color-primary="orange">Orange</button>
<button data-md-color-primary="deep-orange">Deep Orange</button>
<button data-md-color-primary="brown">Brown</button>
<button data-md-color-primary="grey">Grey</button>
<button data-md-color-primary="blue-grey">Blue Grey</button>
<button data-md-color-primary="white">White</button>

<script>
  var buttons = document.querySelectorAll("button[data-md-color-primary]");
  Array.prototype.forEach.call(buttons, function(button) {
    button.addEventListener("click", function() {
      document.body.dataset.mdColorPrimary = this.dataset.mdColorPrimary;
      localStorage.setItem("data-md-color-primary",this.dataset.mdColorPrimary);
    })
  })
</script>

### Accent colors 辅助色

> 默认 `red`

点击色块更换主题的辅助色

<button data-md-color-accent="red">Red</button>
<button data-md-color-accent="pink">Pink</button>
<button data-md-color-accent="purple">Purple</button>
<button data-md-color-accent="deep-purple">Deep Purple</button>
<button data-md-color-accent="indigo">Indigo</button>
<button data-md-color-accent="blue">Blue</button>
<button data-md-color-accent="light-blue">Light Blue</button>
<button data-md-color-accent="cyan">Cyan</button>
<button data-md-color-accent="teal">Teal</button>
<button data-md-color-accent="green">Green</button>
<button data-md-color-accent="light-green">Light Green</button>
<button data-md-color-accent="lime">Lime</button>
<button data-md-color-accent="yellow">Yellow</button>
<button data-md-color-accent="amber">Amber</button>
<button data-md-color-accent="orange">Orange</button>
<button data-md-color-accent="deep-orange">Deep Orange</button>

<script>
  var buttons = document.querySelectorAll("button[data-md-color-accent]");
  Array.prototype.forEach.call(buttons, function(button) {
    button.addEventListener("click", function() {
      document.body.dataset.mdColorAccent = this.dataset.mdColorAccent;
      localStorage.setItem("data-md-color-accent",this.dataset.mdColorAccent);
    })
  })
</script>

## Todo List
- [x64dbg ida同步插件](https://github.com/bootleg/ret-sync)
- [IDA符号执行插件使用](https://github.com/illera88/Ponce)
- 为什么int 3 可以反调试
- extractvalue()函数报错注入
- 短url，系统设计
- https://www.leavesongs.com/
  
## coding...

* crc32原理 
* https://github.com/zanyarjamal/xerxes
* 开3389 c++
* 跨平台抓包，支持https
* 各种后门隐藏与发现,制作 asp php python c
* 分布式肉鸡控制器
* [高性能开发](https://xie.infoq.cn/article/a0d418bf29915ecad5d5eeab0)
* https://hackme.inndy.tw/


## 要搭建的服务
* CTFoj
* owasp
* ZvulDrill
* msf vuln
* wooyun drop
* file server
* 社工库

## mysql 协议加密算法
```
hash1 = SHA1(password) //password是用户输入的密码
result = hash1 ^ sha1(scramble+sha1(hash1)) //scamble 是mysql server端发送的，当密码为空，固定为0x00
```
