![简单图床示例](https://i1.100024.xyz/public/data/2019/05/5ce6915f50a1a.png
 "简单图床示例")
![简单图床示例](https://i1.100024.xyz/public/data/2019/05/5cecf12575f6e.png
 "简单图床示例")

## EasyImage 简单图床 2.0
> 支持多文件上传,简单无数据库,返回图片url,markdown,bbscode,html的一款图床程序
演示地址： [https://img.545141.com](https://img.545141.com"https://img.545141.com")
之前一直用的图床程序是:[PHP多图长传程序2.4.3](http://www.mycodes.net/48/4925.htm "PHP多图长传程序2.4.3")
由于版本过老并且使用falsh上传，在当前html5流行大势所趋下，遂利用基础知识新写了一个以html5为默认上传并且支持flash,向下兼容至IE9。

<hr />

#### 功能支持：

- [x] 支持仅登录后上传
- [x] 支持设置图片质量
- [x] 支持上传图片转换为指定格式
- [x] 支持文字/图片水印
- [x] 支持设置图片指定宽/高
- [x] 支持限制最低宽度/高度上传
- [x] 支持设置广告
- [x] 支持开启/关闭api上传
- [x] 在线管理图片(增、删、改、查)
- [x] 支持网站统计 请将统计代码放入:public/static/hm.js
- [x] 更多·····

#### 注意：

1. 安装之前先使用浏览器访问check.php检查扩展是否都安装！
2. 使用前请注意先修改config.php中的domain域名。
3. 请将所有文件必须赋予0755权限，或者赋予www权限
4. 上传后必须修改config.php的位置：
   - domain 当前图片域名
   - password 登录管理密码！
5. 如果无法登陆管理界面或上传图片，请先打开check.php检查扩展或者使用phpinfo检查。
6. 可以使用浏览器的 F12调试模式->console查看错误
7. 如果对php不太熟悉的话，不要将图床程序放置于二级目录
8. js不要设置分片上传大小，此会导致部分图片上传失败。
9. 默认我会给你设置成最优方案，api上传默认关闭
10. 下载源码后可以删除一些文件：README.md,check.php,LICENSE
11. 欢迎加群：[623688684](https://shang.qq.com/wpa/qunwpa?idkey=3feb4e8be8f1839f71e53bf2e876de36afc6889b2630c33c877d8df5a5583a6f)

#### API上传示例：
参数：

| 参数名称 | 类型 | 是否必须 | 说明 |
| :------------: | :------------: | :------------: | :------------: |
| image | file | 是 | 需上传的图片 |
| api | text | 是 | token |

html form上传示例:
```html
<form action="../index.php" method="post" enctype="multipart/form-data">
    <input type="file"  name="image" accept="image/*" >
    <input type="text" name = "token" placeholder="在tokenList文件找到token并输入"/>
    <input type="submit" />
</form>
```
api上传成功后返回json：

```json
参数:"sucess"上传成功 "failed" 上传失败 "url" 图片链接  "del" 删除链接
{"result":"success","url":"http:\/\/192.168.1.15\/i\/2021\/05\/03\/u34au6_2.jpg","del":"http:\/\/192.168.1.15\/api\/api-web.php?hash=XH%BB2Z%D1%08%D8%E2%D7%048%DFJ%86n%C0%06%DAD%DCP%3E%CF%C4%1B%60%E5%C4Pli"}
```

#### 安全配置
 - Apache配置文件默认设置上传目录不可运行 

```Apache
RewriteEngine on RewriteCond % !^$
RewriteRule i/(.*).(php)$ – [F]
RewriteRule public/(.*).(php)$ – [F]
RewriteRule config/(.*).(php)$ – [F]
```
 - Nginx请在Nginx配置：

```Nginx
 # 禁止运行php的目录
    location ~* ^/(i|public|config)/.*\.(php|php5)$
    {
     deny all;
    }
```
 - 或者参考：[https://www.545141.com/981.html](https://www.545141.com/981.html)

<details><summary><mark><font color=darkred>点击查看更新日志</font></mark></summary>

* 2021-5-2 v2.1
- 将tinyfilemanager配置文件简单翻译并集成到config.php
- 增加底部自定义信息
- 增加检测PHP环境，给与提示
- 增加删除图片url（不会保存链接）
- 恢复随机浏览20张上传图片 可以设定浏览数量和关闭浏览
- - 随机浏览图片可以在线删除
- 可以使用 https://img.545141.com/libs/list.php?num=100 定义浏览数量
- 修复一些调用
- 更改二维码显示方式
- 开启api 并以token方式上传
- 修复check.php相关文件
- 重构部分代码
- 更改目录结构
- 增加安全性配置
- * Apache配置文件默认设置上传目录不可运行 

```Apache
RewriteEngine on RewriteCond % !^$
RewriteRule i/(.*).(php)$ – [F]
RewriteRule public/(.*).(php)$ – [F]
RewriteRule config/(.*).(php)$ – [F]
```

- * Nginx请在Nginx配置：

```Nginx
 # 禁止运行php的目录
    location ~* ^/(i|public|config)/.*\.(php|php5)$
    {
     deny all;
    }
```
- - 或者参考：https://www.545141.com/981.html
- 一些精简

* 2021-4-14 v2.0.2.1 Dev1
- 更新静态文件版本
- 请所有更新过2.0.2.1版本升级到此版本
- 更改一些描述
- md5提交登录验证
- 登录上传也显示公告

* 2021-03-28 v2.0.2.1
- 更新管理程序，修复部分漏洞
- 修复不能等比例缩小图片 
- 支持php8

* 2019-6-26 v2.0.2.0
- 精简压缩代码，使得不再压缩后反而变大
- 删除异域上传功能，不再支持异域上传
- 修复开启登录后无法粘贴密码
- 后台控制上传数量,上传格式
- 其他一些优化

* 2019-6-14 v2.0.1.9
- 增加复制链接按钮
- 增加暂停上传按钮
- 增加QQ截图，剪切板上传
- 增加文字/图片水印透明度
- 恢复开启/关闭api上传
- 恢复支持水印文字颜色
- 恢复支持远程上传图片
- 修复安装时候的权限
- 修复管理无法多选的问题
- 修复上传透明png背景变为纯黑的问题
- 修复成功上传图片但前端无法获取链接
- 修复在centos64 lnmp1.6 php7.1环境下的图片信息读取问题
- 修改图片压缩方式，速度更快，相比之前提高5倍以上
- 更改管理路径
- 更改上传路径，文件名更短
- 更改上传显示方式为缩略图
- 关闭添加图片后自动上传
- 纪念一下2019年，将版本号改为2.0.1.9

* 2019-5-23 v2.0
- 在继承上个版本（1.6.4）的基础上进行了全新优化
- 修复上传经常失败的问题
- 删除一些不常用但会增加功耗的过程
- 全新的压缩 将文件继续缩小
- 全新的目录系统，精简代码
- 设置仅允许在config.php修改，注释更加明了，即使没有代码基础也可以操作
- 增加新的文件管理系统，感谢 tinyfilemanager
- ~~支持文字/图片水印 可自定义文字颜色~~
- ~~支持文字水印背景颜色~~
- ~~支持文字水印透明度~~
- ~~支持删除远程上传文件~~ -> 不再支持删除远程文件
- ~~(支持开启/关闭api自定义文字水印)~~
- ~~支持删除自定义删除图片(仅管理员)~~
</details>

<details><summary><mark><font color=darkred>与1.6.4版本差别</font></mark></summary>

- 在继承上个版本（[1.6.4](https://github.com/icret/easyImages "1.6.4")）的基础上进行了全新优化
- 修复上传经常失败的问题
- 删除一些不常用但会增加功耗的过程 （删除的在下边会有标记）
- 全新的压缩 将文件继续缩小
- 全新的目录系统，精简代码
- 设置仅允许在config.php修改，注释更加明了，即使没有代码基础也可以操作
- 增加新的文件管理系统

</details>

<br />
[EasyImage 1.6.4版本](https://github.com/icret/easyImages)    不建议再使用
<hr />

#### 兼容性
文件上传视图不支持IE9以下的浏览器,api不限制。建议php7.0及以上版本,需要服务器支持Fileinfo、iconv、zip、mbstring、openssl 扩展,如果缺失会导致无法访问管理面板以及上传/删除图片。

文件上传视图提供文件列表管理和文件批量上传功能，允许拖拽（需要 HTML5 支持）来添加上传文件，支持上传大图片，优先使用 HTML5，旧的浏览器自动使用Flash和Silverlight的方式兼容。
<hr />

 - 感谢: [verot](https://github.com/verot/class.upload.php "verot" )提供非常好用的class.upload.php上传类
 - 感谢: [ZUI](https://github.com/easysoft/zui "ZUI" ) 提供css框架
 - 感谢:[tinyfilemanager](https://github.com/prasathmani/tinyfilemanager "tinyfilemanager" ) 提供的文件管理
 - 本源码遵循 GNU Public License
