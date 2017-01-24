# miniProgram-lite
微信小程序php后端接口轻量版


####初衷：
好用的微信SDK一大堆，已经没有自己写了。  
但是好用的SDK大而全，依赖也大。对于业务很小的应用着实有点浪费。  
当时业务需求，顺势做小程序，但是实际后端的接口用量很小，所以打算用到的接口自己包一下。  
再然后，就打算拆出来分享出来。  

##安装：
```shell
composer require yingouqlj/wechat-mini-program-lite
```


##基本使用:

```php
<?php

use Yingou\MiniProgram\MiniProgram;
$config=[
    'appId' => 'appid',
    'secret' => 'secret'
    ];
$program=new MiniProgram($config);
//创建Qrcode
$program->createQrCode->create('/page?id=1',120);

```


##建议用法:
增加个配置继承Config  
在里面实现 token 的读写覆盖原有方法  

```php
<?php

class ProgramConfig extends \Yingou\MiniProgram\Config{
    public function getAccessToken()
    {
        //覆盖掉原来的方法在这里 读取token
    }
     public function setAccessToken($token, $expires = 0)
     {
          //覆盖写入 如 redis      
     }   
}

use Yingou\MiniProgram\MiniProgram;
$program=new MiniProgram(new ProgramConfig());
$program->createQrCode->create('/page?id=1',120);

```


##接口

+ [获取 access_token](https://github.com/yingouqlj/MiniProgram-lite/wiki/%E8%8E%B7%E5%8F%96-access_token)
+ [js换取登录后的openid](https://github.com/yingouqlj/MiniProgram-lite/wiki/code-%E6%8D%A2%E5%8F%96-session_key)


####进度
先立项，慢慢完善。后面也会考虑引入其他依赖包。第一版是轻巧。
<a href="https://yingou.net">
<img src='https://hit.yingou.net/image/s.jpg' />
</a>
