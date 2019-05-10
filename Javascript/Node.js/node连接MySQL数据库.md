#### **连接时报错：**`ER_NOT_SUPPORTED_AUTH_MODE: Client does not support authentication protocol`

**原因：**因为MySQL版本(8.0)版本较高，最新的加密方式node还不支持

**解决办法：**（修改加密规则为普通模式，默认是严格加密模式）

1.启动登录MySQL后修改加密规则

```mysql
ALTER USER 'root'@'localhost' IDENTIFIED BY 'password' PASSWORD EXPIRE NEVER; 
```

2.更新用户密码

```mysql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password'; 
```

3.刷新权限（或重启MySQL）

```mysql
FLUSH PRIVILEGES; 
```

------

