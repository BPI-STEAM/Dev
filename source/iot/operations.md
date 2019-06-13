## 用户操作记录

这里用来记录用户所有的操作，包括：登入登出、添加修改虚拟设备、修改个人信息等

<strike>但是不包括虚拟设备与硬件设备交互操作的记录</strike>
还是应该包括与硬件设备交互的操作记录的~

### 操作记录表设计

需要记录的操作应该包括

- 用户登入、登出等
- 虚拟设备添加、删除等
- 平台发送的控制命令等
- 平台接收的数据等
- 来自其它平台，比如天猫精灵的控制命令等

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
<td style="text-align: center;">uuid</td>
<td style="text-align: center;">varchar</td>
<td style="text-align: center;">36</td>
</tr>
<tr class="even">
<td style="text-align: center;">op_type</td>
<td style="text-align: center;">int</td>
<td style="text-align: center;"></td>
</tr>
<tr class="odd">
<td style="text-align: center;">operation</td>
<td style="text-align: center;">varchar</td>
<td style="text-align: center;">200</td>
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

### op_type 数据记录

<table>
<thead>
<tr class="header">
<th style="text-align: center;">name</th>
<th style="text-align: center;">memo</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: center;">Login</td>
<td style="text-align: center;">用户登入、登出等操作</td>
</tr>
<tr class="even">
<td style="text-align: center;">Device</td>
<td style="text-align: center;">添加、删除设备等操作</td>
</tr>
<tr class="odd">
<td style="text-align: center;">Control</td>
<td style="text-align: center;">发送控制命令等操作</td>
</tr>
<tr class="even">
<td style="text-align: center;">Data</td>
<td style="text-align: center;">接收设备数据等操作</td>
</tr>
<tr class="odd">
<td style="text-align: center;">Remote</td>
<td style="text-align: center;">接收来自远端命令等操作，如来自天猫精灵</td>
</tr>
</tbody>
</table>