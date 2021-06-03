# 桥接联通路由器

## 桥接修改
一、路由器型号：TEWA-800

二、步骤

1. 浏览器（最好是Chrome）输入192.168.1.1
2. F12打开控制台，切换到console选项卡
3. 粘贴下面的代码回车：

```
document.getElementById('loginfrm').setAttribute('method','get')
document.getElementById('username').value = 'CUAdmin'
document.getElementById('password').value = '这里填你自己改的管理密码，如果没改过，那就是默认的CUAdmin'
function submitFrm()
{
with(document.forms[0])
{
if ( password.value.length == 0 ) {
alert('密码不得为空!');
return;
}
if ( password.value.length > 32 ) {
alert('密码长度不得大于32!');
return;
}
}
document.getElementById('loginfrm').submit();
}
submitFrm()

```

顺利登陆联通后台

4. 备份当前配置文件，以防万一。
   http://192.168.1.1/backupsettings.conf
5. 在控制台下，搜索“new wanConn(”，会有下面的信息，其中第二条，99000xxx是PPPoE账号，后面的值是密码，【务必记下来】
![image](https://user-images.githubusercontent.com/54582748/120621521-86c00d00-c490-11eb-8c74-721d6d4be26e.png)
6. 配置光猫为桥接模式
```
  1）基础配置 > 上行线路配置
  2）选择2_Internet_B_VID_3691
  3）修改为“上网”+“桥接”+“DHCP关闭“+”lan1勾选“
  4）保存配置
```
7. 重启光猫（断电即可），用网线将光猫的lan1口，连接到路由器的wan口
8. 打开路由器管理界面，输入第5步获得的账号密码，就可以正常上网了







