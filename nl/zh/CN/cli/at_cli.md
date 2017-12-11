---

copyright:

  years: 2016, 2017

lastupdated: "2017-09-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# IBM Cloud Activity Tracker CLI
{: #at_cli}

{{site.data.keyword.cloudaccesstraillong}} CLI 是一种 CF 插件，可用于管理 {{site.data.keyword.cloudaccesstrailshort}} 事件。
{: shortdesc}

**先决条件**
* 运行命令之前，请使用 `cf login` 命令登录到 {{site.data.keyword.Bluemix}}，以生成 {{site.data.keyword.Bluemix_short}} 访问令牌并对会话进行认证。

要了解有关如何使用 {{site.data.keyword.cloudaccesstrailshort}} CLI 的信息，请参阅[通过 CLI 管理 {{site.data.keyword.cloudaccesstrailshort}} 事件](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#managing_events)。 

{{site.data.keyword.cloudaccesstraillong}} CLI 插件支持 Linux、Mac 和 Windows 平台。

<table>
  <caption>用于管理 {{site.data.keyword.cloudaccesstrailshort}} 的命令</caption>
  <tr>
    <th>命令</th>
    <th>用途</th>
  </tr>
  <tr>
    <td>[cf at](#base)</td>
    <td>使用此命令可获取有关 CLI 的信息，例如版本或命令列表。</td>
  </tr>
  <tr>
    <td>[cf at delete](#delete)</td>
    <td>使用此命令可删除 {{site.data.keyword.cloudaccesstrailshort}} 事件。</td>
  </tr>
  <tr>
    <td>[cf at download](#download)</td>
    <td>使用此命令可将 {{site.data.keyword.cloudaccesstrailshort}} 日志下载到本地文件。</td>
  </tr>
  <tr>
    <td>[cf at help](#help)</td>
    <td>使用此命令可获取有关如何使用 CLI 的帮助以及所有命令的列表。</td>
  </tr>
  <tr>
    <td>[cf at option](#option)</td>
    <td>使用此命令可查看或更改 {{site.data.keyword.Bluemix_notm}} 空间或帐户中提供的 {{site.data.keyword.cloudaccesstrailshort}} 事件选项（例如，保留时间）。</td>
  </tr>
  <tr>
    <td>[cf at session create](#session_create)</td>
    <td>使用此命令可创建新会话。</td>
  </tr>
  <tr>
    <td>[cf at session delete](#session_delete)</td>
    <td>使用此命令可删除会话。</td>
  </tr>  
  <tr>
    <td>[cf at session list](#session_list)</td>
    <td>使用此命令可列出活动会话及其标识。</td>
  </tr>  
  <tr>
    <td>[cf at session show](#session_show)</td>
    <td>使用此命令可显示单个会话的状态。</td>
  </tr>   
  <tr>
    <td>[cf at status](#status)</td>
    <td>使用此命令可查看有关 {{site.data.keyword.cloudaccesstrailshort}} 中所存储事件的状态的信息。</td>
  </tr>
  <tr>
    <td>[cf at trail](#trail)</td>
    <td>使用此命令可将事件发送到 {{site.data.keyword.cloudaccesstrailshort}}。</td>
  </tr>
  </table>


## cf at
{: #base}

提供有关 CLI 版本以及如何使用 CLI 的信息。

```
cf at [parameters]
```
{: codeblock}

**参数**

<dl>
<dt>--help, -h</dt>
<dd>设置此参数可显示命令列表，或获取一个命令的帮助。
</dd>

<dt>--version, -v</dt>
<dd>设置此参数可显示 CLI 的版本。</dd>
</dl>

**示例**

要获取命令列表，请运行以下命令：

```
cf at --help
```
{: codeblock}

要获取 CLI 的版本，请运行以下命令：

```
cf at --version
```
{: codeblock}


## cf at delete
{: #delete}

删除 {{site.data.keyword.cloudaccesstrailshort}} 事件。

```
cf at delete [parameters] [arguments..]
```
{: codeblock}

**参数**

<dl>
  <dt>--start value, -s value</dt>
  <dd>（可选）设置开始日期，格式为全球标准时间 (UTC)：*YYYY-MM-DD*，例如 `2017-01-02`。<br>缺省值设置为 2 周前。</dd>
  
  <dt>--end value, -e value</dt>
  <dd>（可选）设置结束日期，格式为全球标准时间 (UTC)：*YYYY-MM-DD*。<br>日期的 UTC 格式为 **YYYY-MM-DD**，例如`2017-01-02`。<br>缺省值设置为当天。</dd>
  
</dl>

**示例**

要删除 2017 年 6 月 22 日的事件，请运行以下命令：
```
cf at delete -s 2017-06-22 -e 2017-06-22
```
{: codeblock}

您会收到类似于以下输出的信息：

`Deleted successfully`
`"6 logs were deleted, freeing 13737 bytes."`


## cf at download
{: #download}

将 {{site.data.keyword.cloudaccesstrailshort}} 事件下载到本地文件，或者将这些事件流式传出到 Windows 和 Mac OS X 中的终端窗口，或者传出到 Linux 终端中的 stdout。 

**注：**要下载文件，必须先创建会话。会话基于日期范围来定义要下载的事件。您将在会话的上下文中下载事件。有关更多信息，请参阅 [cf at session create](/docs/services/CloudActivityTracker/reference/at_cli.html#session_create)。

```
cf at download [parameters] [arguments...]
```
{: codeblock}

**参数**

<dl>
<dt>--output value, -o value</dt>
<dd>（可选）设置将事件下载到的本地输出文件的路径和文件名。<br>缺省值为连字符 (-)。<br>将此参数设置为缺省值可将日志输出到标准输出。</dd>
</dl>

**自变量**

<dl>
<dt>会话标识</dt>
<dd>设置在运行 `cf at session create` 命令时获取的会话标识值。此值指示在下载事件时要使用的会话。<br>**注：**`cf at session create` 命令提供用于控制下载哪些事件的参数。</dd>
</dl>

**注：**下载完成后，要再次下载相同数据，必须使用不同的文件或不同的会话。

**示例**

要将事件下载到名为 `events.log` 的文件中，请运行以下命令：

```
cf at download -o events.log 1db6ce16-824d-4d50-bd40-37f1d8fea9b7
```
{: screen}

您会收到类似于以下输出的信息： 

```
6.70 KiB / 3.06 KiB [========] 219.03% 8.60 MiB/s 0s
Download completed successfully
```
{: screen}


## cf at help
{: #help}

提供有关如何使用命令的信息。

```
cf at help [parameters]
```
{: codeblock}

**参数**

<dl>
<dt>命令</dt>
<dd>设置要获取其帮助的命令的名称。
</dd>
</dl>


**示例**

要获取有关如何运行命令来查看 {{site.data.keyword.cloudaccesstrailshort}} 状态的帮助，请运行以下命令：

```
cf at help status
```
{: codeblock}


## cf at option
{: #option}

显示或更改 {{site.data.keyword.Bluemix_notm}} 空间中可用事件的保留期。设置保留时间策略时，事件在达到保留天数时会自动删除。

* 该时间段以天数为单位进行设置。
* 缺省值为 **-1**，表示事件会存储起来，而不会删除。

**注：**缺省情况下，将存储所有事件。如果未设置保留期，那么必须使用 `cf at delete` 命令手动删除事件。 

```
cf at option [parameters] [arguments...]
```
{: codeblock}

**参数**

<dl>
<dt>--retention value, -r value</dt>
<dd>（可选）设置保留天数。<br> 缺省值为 *-1* 天。</dd>

</dl>

**示例**

要查看您登录到的空间的当前保留期，请运行以下命令：

```
cf at option
```
{: codeblock}

输出类似于以下输出：

```
+--------------------------------------+-----------+
|               SPACEID                | RETENTION |
+--------------------------------------+-----------+
| 2af890ce-fb4f-4e41-a975-901a56ed1f11 |        30 |
+--------------------------------------+-----------+
```
{: screen}


要将您已登录到的空间的保留期更改为 25 天，请运行以下命令：

```
cf at option -r 25
```
{: codeblock}

输出类似于以下输出：

```
+--------------------------------------+-----------+
|               SPACEID                | RETENTION |
+--------------------------------------+-----------+
| 2af890ce-fb4f-4e41-a975-901a56ed1f11 |        25 |
+--------------------------------------+-----------+
```
{: screen}



## cf at session create
{: #session_create}

创建新会话。

**注：**一个空间中最多可以有 30 个并发会话。会话是针对用户创建的。一个空间的用户之间不能共享会话。

```
cf at session create [parameters] [arguments...]
```
{: codeblock}

**参数**

<dl>
  <dt>--start value, -s value</dt>
  <dd>（可选）设置开始日期，格式为全球标准时间 (UTC)：*YYYY-MM-DD*，例如 `2017-01-02`。<br>缺省值设置为 2 周前。</dd>
  
  <dt>--end value, -e value</dt>
  <dd>（可选）设置结束日期，格式为全球标准时间 (UTC)：*YYYY-MM-DD*，例如 `2017-01-02`。<br>缺省值设置为当天。</dd>
 </dl>

**返回的值**

<dl>
<dt>Access-Time</dt>
<dd>指示上次使用会话的时间的时间戳记。</dd>

<dt>Create-Time</dt>
<dd>与创建会话的日期和时间相对应的时间戳记。</dd>

<dt>Date-Range</dt>
<dd>指示用于过滤事件的日期范围。此日期范围内确定的事件可以通过会话进行管理。</dd>

<dt>ID</dt>
<dd>会话标识。</dd>

<dt>Space</dt>
<dd>会话在其中处于活动状态的空间的标识。</dd>

<dt>Type-Account</dt>
<dd>此值设置为 **ActivityTracker**。</dd>

<dt>Username</dt>
<dd>创建会话的用户的 {{site.data.keyword.IBM_notm}} 标识。</dd>
</dl>


**示例**

要创建 2017 年 7 月 10 日的会话，请运行以下命令：

```
cf at session create -s 2017-07-10 -e 2017-07-10
```
{: screen}

输出类似于以下输出：

```
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| id           | 9b8c4db8-5841-4993-a449-305815a53a8e      |
| space        | xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx      |
| username     | xxx@yyy.com                               |
| create-time  | 2017-07-25T11:54:00.20042645Z             |
| access-time  | 2017-07-25T11:54:00.20042645Z             |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
+--------------+-------------------------------------------+
```
{: screen}



## cf at session delete
{: #session_delete}

删除由会话标识指定的会话。

```
cf at session delete [arguments...]
```
{: codeblock}


**自变量**

<dl>
<dt>会话标识</dt>
<dd>要删除的会话的标识。<br>可以使用 `cf at session list` 命令来获取所有活动会话标识。</dd>
</dl>

**示例**

要删除会话标识为 *9b8c4db8-5841-4993-a449-305815a53a8e* 的会话，请运行以下命令：

```
cf at session delete 9b8c4db8-5841-4993-a449-305815a53a8e
```
{: screen}

输出类似于以下输出：

```
+---------------+--------------------------+
|    NAME       |     VALUE                |
+---------------+--------------------------+
|  message      | Delete session success   |
+---------------+--------------------------+
```
{: screen}


## cf at session list
{: #session_list}

列出活动会话及其标识。

```
cf at session list 
```
{: codeblock}

**返回的值**

<dl>
<dt>ID</dt>
<dd>会话标识。</dd>

<dt>SPACE</dt>
<dd>会话在其中处于活动状态的空间的标识。</dd>

<dt>USERNAME</dt>
<dd>创建会话的用户的 {{site.data.keyword.IBM_notm}} 标识。</dd>

<dt>CREATE-TIME</dt>
<dd>与创建会话的日期和时间相对应的时间戳记。</dd>

<dt>ACCESS-TIME</dt>
<dd>指示上次使用会话的时间的时间戳记。</dd>
</dl>
 
**示例**

要列出会话，请运行以下命令：

```
cf at session list
```
{: screen}

输出类似于以下输出：

```
+--------------------------------------+--------------------------------------+-----------------------------------+--------------------------------+--------------------------------+
| ID                                   | SPACE                                | USERNAME                          | CREATE-TIME                    | ACCESS-TIME                    |
+--------------------------------------+--------------------------------------+-----------------------------------+--------------------------------+--------------------------------+
| fa3f1970-21f3-4e32-b480-1ffb41badc16 | 12345678-fb4f-acdf-a975-11335678r3fg | xxx@yyy.com                       | 2017-07-10T09:04:07.916788069Z | 2017-07-10T09:04:07.916788069Z |
| 9b8c4db8-5841-4993-a449-305815a53a8e | 12345678-fb4f-acdf-a975-11335678r3fg | xxx@yyy.com                       | 2017-07-11T09:19:14.666532796Z | 2017-07-12T09:19:14.666532796Z |
+--------------------------------------+--------------------------------------+-----------------------------------+--------------------------------+--------------------------------+
```
{: screen}


## cf at session show
{: #session_show}

显示单个会话的状态。

```
cf at session show [arguments...]
```
{: codeblock}

**自变量**

<dl>
<dt>会话标识</dt>
<dd>要获取其信息的活动会话的标识。</dd>
</dl>

**返回的值**

<dl>
<dt>Access-Time</dt>
<dd>指示上次使用会话的时间的时间戳记。</dd>

<dt>Create-Time</dt>
<dd>与创建会话的日期和时间相对应的时间戳记。</dd>

<dt>Date-Range</dt>
<dd>指示用于过滤事件的日期范围。此日期范围内确定的事件可以通过会话进行管理。</dd>

<dt>id</dt>
<dd>会话标识。</dd>

<dt>Space</dt>
<dd>会话在其中处于活动状态的空间的标识。</dd>

<dt>Type-Account</dt>
<dd>此值设置为 **ActivityTracker**。</dd>

<dt>Username</dt>
<dd>创建会话的用户的 {{site.data.keyword.IBM_notm}} 标识。</dd>
</dl>

**示例**

要显示会话标识为 *9b8c4db8-5841-4993-a449-305815a53a8e* 的会话的详细信息，请运行以下命令：

```
cf at session show 9b8c4db8-5841-4993-a449-305815a53a8e
```
{: screen}

输出类似于以下输出：

```
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| create-time  | 2017-07-25T11:54:00.20042645Z             |
| access-time  | 2017-07-25T11:54:00.20042645Z             |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
| id           | 9b8c4db8-5841-4993-a449-305815a53a8e      |
| space        | xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx      |
| username     | xxx@yyy.com                               |
+--------------+-------------------------------------------+
```
{: screen}


## cf at status
{: #status}

返回有关 {{site.data.keyword.cloudaccesstrailshort}} 事件的状态的信息。

```
cf at status [parameters] [arguments...]
```
{: codeblock}

**参数**

<dl>
  <dt>--start value, -s value</dt>
  <dd>（可选）设置开始日期，格式为全球标准时间 (UTC)：*YYYY-MM-DD*，例如 `2017-01-02`。<br>缺省值设置为 2 周前。</dd>
  
  <dt>--end value, -e value</dt>
  <dd>（可选）设置结束日期，格式为全球标准时间 (UTC)：*YYYY-MM-DD*，例如 `2017-01-02`。<br>缺省值设置为当天。</dd>
  
  <dt>--at-account-level, -a</dt>
  <dd>（可选）将作用域设置为帐户级别。<br> **注：**设置此值可获取帐户信息。<br>如果未指定此参数，那么缺省值设置为仅当前空间，即使用命令 `cf login` 登录到的空间。</dd>
  
</dl>


**注：**未指定开始日期和结束日期时，`cf at status` 命令仅报告 {{site.data.keyword.cloudaccesstrailshort}} 中存储的最近两周的事件。 

**返回的值**   

<dl>
  <dt>DATE</dt>
  <dd>日期，格式为全球标准时间 (UTC)：*YYYY-MM-DD*，例如 `2017-01-02`。</dd>
  
  <dt>COUNT</dt>
  <dd>事件总数。</dd>
  
  <dt>SIZE</dt>
  <dd>事件的总大小（以兆字节为单位）。</dd>

  <dt>TYPES</dt>
  <dd>此值设置为 **ActivityTracker**。</dd>
  
  <dt>SEARCHABLE</dt>
  <dd>此字段指示事件是否可供在 Kibana 中进行搜索。<br>如果字段 **SEARCHABLE** 的值设置为 *None*，那么事件可供下载，但不能在 Kibana 中分析这些事件。</dd>
  
</dl>

**示例**

要显示 2017 年 7 月 20 日的事件的详细信息，请运行以下命令：

```
cf at status -s 2017-07-20 -e 2017-07-20
```
{: codeblock}


您会收到类似于以下输出的信息：

```
+------------+-----------+-------+------------------+--------------+
|   Date     |  Count    | Size  | Types            |  Searchable  | 
+------------+-----------+-------+------------------+--------------+
| 2017-07-20 |    1      | 2531  | ActivityTracker  | All          | 
+------------+-----------+-------+------------------+--------------+
```
{: screen}



## cf at trail
{: #trail}

将序列化事件发送到 {{site.data.keyword.cloudaccesstrailshort}}。

```
cf at trail [parameters] [arguments...]
```
{: codeblock}

**参数**

<dl>
  <dt>--file FILE, -f FILE</dt>
  <dd>（可选）使用以下格式指定事件文件：`PATH/filename`</dd>
  
  <dt>--type FORMAT, -t FORMAT</dt>
  <dd>（可选）指定该文件中包含的事件的格式。有效值为：*cadf* 和 *kong*。<br> 使用 *CADF* 可发送符合 CADF 格式的事件。使用 *KONG* 可发送符合 Kong 格式的事件。<br> **注：**在一个文件中只能发送同一类型的事件。</dd>
 </dl>
 
**示例**

要将序列化的 CADF 事件发送到 {{site.data.keyword.cloudaccesstrailshort}}，请运行以下命令：

```
cf at trail -t cadf -f events.log
```
{: codeblock}

其中，*events.log* 是包含要发送到 {{site.data.keyword.cloudaccesstrailshort}} 的事件的文件。此文件包含符合 CADF 格式的事件。

您会收到类似于以下输出的信息：

```
+--------------------------------------+---------------------------+
|            ID                        |          Value            |
+--------------------------------------+---------------------------+
| bbb170dc-2b0a-42d4-b560-b416f3308869 | B0UtwP1FhemsZIr4rTJVKA==  |
+--------------------------------------+---------------------------+
| 688f1194-2305-4367-8ece-f468e67c19fb | KLCG9f++usNolgvutRCR1Q==  |
+--------------------------------------+---------------------------+
```
{: screen}
