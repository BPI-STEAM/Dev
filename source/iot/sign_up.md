## 用户注册

开始设想是使用微博账号单点登录，省去管理账号的麻烦，不过考虑到对接天猫精灵的时候就是
OAuth2 授权，在授权的时候再调用一次 OAuth2 授权有点太复杂了，暂时先 pass

也可以使用手机号加验证码的方式登录，但是短信验证码服务是要收费的。。。。。

所以暂时决定还是使用传统的注册账号加手工验证的方式开通账号

### 用户表设计

- 使用邮箱账号作为用户名，注册时检查格式
- 昵称默认使用邮箱前缀，用户可以自行修改
- 密码使用 md5 加密，除了使用字典应该是不能破解的，网上有破解 md5 的网站，看介绍也是用搜集来的 md5 码做对比假装破解了
- 手机号前期不用录入，可以作为第二用户名，或者等短信验证码免费了可以用验证码直接登录
- 每个用户分配一个 uuid，作为对接天猫精灵时的身份认定
- 用户组，确定用户权限
- 启用状态，由管理员以手工方式启用，代表注册成功
- 登录ip，应该没啥用
- 注册日期，也没啥用

### 字段设计

<table>
<thead>
<tr class="header">
<th style="text-align: center;">name</th>
<th style="text-align: center;">type</th>
<th style="text-align: center;">length</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: center;">email</td>
<td style="text-align: center;">varchar</td>
<td style="text-align: center;">20</td>
</tr>
<tr class="even">
<td style="text-align: center;">nickname</td>
<td style="text-align: center;">varchar</td>
<td style="text-align: center;">20</td>
</tr>
<tr class="odd">
<td style="text-align: center;">passwd</td>
<td style="text-align: center;">varchar</td>
<td style="text-align: center;">32</td>
</tr>
<tr class="even">
<td style="text-align: center;">mobile</td>
<td style="text-align: center;">varchar</td>
<td style="text-align: center;">11</td>
</tr>
<tr class="odd">
<td style="text-align: center;">uuid</td>
<td style="text-align: center;">varchar</td>
<td style="text-align: center;">36</td>
</tr>
<tr class="even">
<td style="text-align: center;">group</td>
<td style="text-align: center;">int</td>
<td style="text-align: center;"></td>
</tr>
<tr class="odd">
<td style="text-align: center;">enabled</td>
<td style="text-align: center;">int</td>
<td style="text-align: center;"></td>
</tr>
<tr class="even">
<td style="text-align: center;">ip</td>
<td style="text-align: center;">varchar</td>
<td style="text-align: center;">15</td>
</tr>
<tr class="odd">
<td style="text-align: center;">date</td>
<td style="text-align: center;">datetime</td>
<td style="text-align: center;"></td>
</tr>
</tbody>
</table>


