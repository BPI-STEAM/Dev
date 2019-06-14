## 创建设备

用户登录平台以后第一件事当然是新建一个虚拟设备，硬件设备使用虚拟设备提供的 `key` 和 `secret` 与平台进行对接绑定，

### 虚拟设备表设计

- key 和 secret 还没想好用什么方法生成
- device_name，手动指定设备名称
- 想好了再补充。。。。。
- 生成日期

以下是对接天猫精灵平台需要的参数，如果不对接可以不用填

- device_id，自动生成
- device_type，天猫平台支持的设备类型，从下拉列表选择
- device_zone，设备摆放位置，从 [这里](https://open.bot.tmall.com/oauth/api/placelist?spm=0.7629140.0.0.29751780d0p90U) 获取最新的，并从下拉列表选择（也可以不填，可以事后从 `天猫精灵 app` 中选择）
- device_brand，设备品牌（可以不填，使用系统默认）
- device_modal，设备型号（不知道用途，也可以不填）
- device_icon，设备图片 url（可以不填，使用系统默认）

例如按以下设置：

```
"deviceId" => "1234567890",
"deviceName" => "智能开关",
"deviceType" => "switch",
"zone" => "办公室",
"brand" => "Walkline Hardware",
"modal" => "wkhw_one_switch",
"icon" => "https://walkline.wang/logo.png",
```

则显示内容如图：

![](images/device_list.png)

> 此例中的两个 `开关` 字样是对应 `deviceType` 的 `switch`，是不能自己指定的

### 字段设计

暂时是这些

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
<td style="text-align: center;">key</td>
<td style="text-align: center;">varchar</td>
<td style="text-align: center;">36</td>
</tr>
<tr class="even">
<td style="text-align: center;">secret</td>
<td style="text-align: center;">varchar</td>
<td style="text-align: center;">36</td>
</tr>
<tr class="odd">
<td style="text-align: center;">device_id</td>
<td style="text-align: center;"></td>
<td style="text-align: center;">varchar</td>
</tr>
<tr class="even">
<td style="text-align: center;">device_name</td>
<td style="text-align: center;">varchar</td>
<td style="text-align: center;">20</td>
</tr>
<tr class="odd">
<td style="text-align: center;">device_type</td>
<td style="text-align: center;">varchar</td>
<td style="text-align: center;">20</td>
</tr>
<tr class="even">
<td style="text-align: center;">device_zone</td>
<td style="text-align: center;">varchar</td>
<td style="text-align: center;">20</td>
</tr>
<tr class="odd">
<td style="text-align: center;">device_brand</td>
<td style="text-align: center;">varchar</td>
<td style="text-align: center;">30</td>
</tr>
<tr class="even">
<td style="text-align: center;">device_modal</td>
<td style="text-align: center;">varchar</td>
<td style="text-align: center;">30</td>
</tr>
<tr class="odd">
<td style="text-align: center;">device_icon</td>
<td style="text-align: center;">varchar</td>
<td style="text-align: center;">100</td>
</tr>
<tr class="even">
<td style="text-align: center;">date</td>
<td style="text-align: center;">datetime</td>
<td style="text-align: center;"></td>
</tr>
</tbody>
</table>