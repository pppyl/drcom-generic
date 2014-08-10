本页面仅供drcom客户端开发的童鞋有价值，需要有一些相关的知识。

drcom_2011.lua
---------------------
这是一个由 *googlecode* 上 *jdrcom* 项目中的 *wireshark* 插件 <br>
项目地址：(https://code.google.com/p/jdrcom/) <br>
使用(for windows):

将 *drcom_2011.lua* 放到 *Wireshark.exe* 所在的目录下， 打开 *init.lua* ，在 `dofile(DATA_DIR.."console.lua")` 之后添加 `dofile(DATA_DIR.."drcom_2011.lua")`.

之后就可以在过滤器中使用 *drcom* 协议了。


关于 idx=05 错误包的错误信息类型
---------------------

login包服务器返回错误类型 (发送序号为03的包后）<br>
> 05000005XX00...

XX是错误编号，对应下面的a2

* 0x01 有人正在使用这个账号，且是有线的方式
* 0x02 服务器繁忙，请稍候重新登录
* 0x03 帐号或密码错误
* 0x04 本帐号的累计时间或流量已超出限制
* 0x05 本帐号暂停使用
* 0x07 IP地址不匹配，本帐号只能在指定IP地址上使用 
* 0x0b MAC(物理)地址不匹配，本帐号只能在指定的IP和MAC(物理)地址上使用
* 0x14 本帐IP地址太多
* 0x15 客户端版本不正确
* 0x16 本帐号只能在指定的Mac和IP上使用
* 0x17 你的PC设置了静态IP,请改为动态获取方式(DHCP),然后重新登录
* 0x18 - 0x1c 保留错误信息
* 其他都会提示账号密码错误


关于版本号对应的字段
-------------------
位置在 +148 处
对应本文代码的

```python
data += '\x0a\x00' # for u64, \x1a\x00
```

尚且不知道第二个字节是什么东西，所以只考虑第一个字节

* U60: 0x09
* U60R0: 0x0a
* U64: 0x1a

该数值应该随着版本号递增


吉林大学用户
------------------
由于这个sb学校的特殊性，请使用 https://github.com/ly0/jlu-drcom-client 里的客户端
（U62协议中带了dhcp_option，这是其他学校没有的）

其他
-------------------
HITwh的Shindo酱的项目也是非常优秀的请参考 <br>
https://github.com/coverxit/EasyDrcom/
