# WebView Native Bridge

## 选型

- iOS: [marcuswestin/WebViewJavascriptBridge](https://github.com/marcuswestin/WebViewJavascriptBridge)
- Android: [wendux/WebViewJavascriptBridge](https://github.com/wendux/WebViewJavascriptBridge)

## 存储区公共数据

通过原生桥的 `storageSet` 和 `storageGet` 接口读写的存储区。

| Key                   | Description              | Example |
| --------------------- | ------------------------ | ------- |
| `pushDeviceToken`     | 推送消息设备令牌         |         |
| `jpushRegistrationId` | 极光推送 Registration ID |         |

## 接口：H5-Native

### loaded

Web 初始化完成通知

- 参数：无

- 返回：

    | Key     | Type   | Description                      | Example    |
    | ------- | ------ | -------------------------------- | ---------- |
    | `error` | string | 错误信息标识，仅当出错时存在该键 | `"failed"` |

### storageSet

写入 App 存储行

- 参数：

    | Key     | Type   | Description | Example                      |
    | ------- | ------ | ----------- | ---------------------------- |
    | `key`   | string | (必需) 键名 | `"user"`                     |
    | `value` | (any)  | (必需) 键值 | `{ "id": 1, "name": "Bob" }` |

- 返回：

    | Key     | Type   | Description                      | Example    |
    | ------- | ------ | -------------------------------- | ---------- |
    | `error` | string | 错误信息标识，仅当出错时存在该键 | `"failed"` |

### storageGet

读取 App 存储行

- 参数：

    | Key   | Type   | Description | Example  |
    | ----- | ------ | ----------- | -------- |
    | `key` | string | (必需) 键名 | `"user"` |


- 返回：

    | Key     | Type   | Description                      | Example                      |
    | ------- | ------ | -------------------------------- | ---------------------------- |
    | `error` | string | 错误信息标识，仅当出错时存在该键 | `"failed"`                   |
    | `value` | (any)  | 键值                             | `{ "id": 1, "name": "Bob" }` |

### scanCode

扫描二维码或条码

- 参数：无

- 返回：

    | Key | Type | Description | Example |
    | --- | --- | --- | --- |
    | `error` | string | 错误信息标识，仅当出错时存在该键<br />`"cancelled"`: 拒绝授权;<br />`"unauthorized"`: 永久拒绝授权;<br />`"failed"`: 其他错误; | `"failed"` |
    | `data` | string | 扫码结果 | `"https://www.example.com/"` |

### snsShare

显示分享界面

- 参数：

    | Key     | Type   | Description         | Example                               |
    | ------- | ------ | ------------------- | ------------------------------------- |
    | `text`  | string | (必需) 分享文字     | `"The text content goes here"`        |
    | `image` | string | (必需) 分享图片 URL | `"https://www.example.com/image.png"` |
    | `url`   | string | (必需) 分享链接     | `"https://www.example.com/"`          |

- 返回：

    | Key     | Type   | Description                      | Example       |
    | ------- | ------ | -------------------------------- | ------------- |
    | `error` | string | 错误信息标识，仅当出错时存在该键 | `"cancelled"` |

### getContactNumber

获取通讯录电话号码

- 参数：无

- 返回：

    | Key | Type | Description | Example |
    | --- | --- | --- | --- |
    | `error` | string | 错误信息标识，仅当出错时存在该键<br />`"cancelled"`: 拒绝授权;<br />`"unauthorized"`: 永久拒绝授权;<br />`"failed"`: 其他错误; | `"failed"` |
    | `number` | string | 电话号码 | `"+8613800138000"` |

### dialPhone

拨打电话

- 参数：

    | Key      | Type   | Description     | Example            |
    | -------- | ------ | --------------- | ------------------ |
    | `number` | string | (必需) 电话号码 | `"+8613800138000"` |

- 返回：

    | Key     | Type   | Description                      | Example                          |
    | ------- | ------ | -------------------------------- | -------------------------------- |
    | `error` | string | 错误信息标识，仅当出错时存在该键 | `"cancelled"`, `"not_supported"` |

### sendMessage

发送信息

- 参数：

    | Key         | Type   | Description     | Example            |
    | ----------- | ------ | --------------- | ------------------ |
    | `recipient` | string | (必需) 电话号码 | `"+8613800138000"` |
    | `body`      | string | (必需) 信息内容 | `"Hello there."`   |

- 返回：

    | Key     | Type   | Description                      | Example                          |
    | ------- | ------ | -------------------------------- | -------------------------------- |
    | `error` | string | 错误信息标识，仅当出错时存在该键 | `"cancelled"`, `"not_supported"` |

### sendMail

发送邮件

- 参数：

    | Key         | Type   | Description         | Example                    |
    | ----------- | ------ | ------------------- | -------------------------- |
    | `recipient` | string | (必需) 电子邮件地址 | `"postmaster@example.com"` |
    | `subject`   | string | (必需) 电子邮件标题 | `"The subject goes here."` |
    | `body`      | string | (必需) 电子邮件内容 | `"The body goes here."`    |

- 返回：

    | Key     | Type   | Description                      | Example                          |
    | ------- | ------ | -------------------------------- | -------------------------------- |
    | `error` | string | 错误信息标识，仅当出错时存在该键 | `"cancelled"`, `"not_supported"` |

### getGeoLocation

获取地理定位信息

- 参数：无

- 返回：

    | Key | Type | Description | Example |
    | --- | --- | --- | --- |
    | `error` | string | 错误信息标识，仅当出错时存在该键<br />`"cancelled"`: 拒绝授权;<br />`"unauthorized"`: 永久拒绝授权;<br />`"failed"`: 其他错误; | `"failed"` |
    | `latitude` | float  | 纬度 | `31.237743` |
    | `longitude` | float  | 经度 | `121.416600` |

### geoNavigation

显示地理导航界面

- 参数：

    | Key           | Type   | Description     | Example                        |
    | ------------- | ------ | --------------- | ------------------------------ |
    | `title`       | string | (必需) 地点名称 | `"Somewhere to Eat"`           |
    | `description` | string | (必需) 地点描述 | `"Why to eat."`                |
    | `address`     | string | (必需) 地点地址 | `"A detail physical address."` |
    | `latitude`    | float  | (必需) 纬度     | `31.237743`                    |
    | `longitude`   | float  | (必需) 经度     | `121.416600`                   |

- 返回：

    | Key     | Type   | Description                      | Example                                     |
    | ------- | ------ | -------------------------------- | ------------------------------------------- |
    | `error` | string | 错误信息标识，仅当出错时存在该键 | `"cancelled"`, `"unauthorized"`, `"failed"` |

### openWebpage

打开网页

- 参数：

    | Key    | Type    | Description                                                  | Example                     |
    | ------ | ------- | ------------------------------------------------------------ | --------------------------- |
    | `url`  | string  | (必需) 网页链接                                              | `"https://www.google.com/"` |
    | `type` | integer | 打开方式 (缺省: `0`)<br />`0`: App 内打开;<br />`1`: App 外浏览器打开; | `1`                         |

- 返回：

    | Key     | Type   | Description                      | Example    |
    | ------- | ------ | -------------------------------- | ---------- |
    | `error` | string | 错误信息标识，仅当出错时存在该键 | `"failed"` |

### openApp

跳转 App（当 App 未安装时，则跳转应用商店）

- 参数：

    | Key                | Type   | Description             | Example                             |
    | ------------------ | ------ | ----------------------- | ----------------------------------- |
    | `url`              | string | (必需) URL              | `"alipayqr://platformapi/startapp"` |
    | `androidPackageId` | string | (必需) Android App 包名 | `"com.eg.android.AlipayGphone"`     |
    | `iosItunesAppId`   | string | (必需) iOS App 包 ID    | `"333206289"`                       |

- 返回：

    | Key     | Type   | Description                      | Example    |
    | ------- | ------ | -------------------------------- | ---------- |
    | `error` | string | 错误信息标识，仅当出错时存在该键 | `"failed"` |

### getCacheSize

获取 App 缓存大小

- 参数：无

- 返回：

    | Key     | Type    | Description                      | Example    |
    | ------- | ------- | -------------------------------- | ---------- |
    | `error` | string  | 错误信息标识，仅当出错时存在该键 | `"failed"` |
    | `size`  | integer | 缓存大小（单位：字节）           | `1048576`  |

### clearCache

清理 App 缓存

- 参数：无

- 返回：

    | Key     | Type   | Description                      | Example    |
    | ------- | ------ | -------------------------------- | ---------- |
    | `error` | string | 错误信息标识，仅当出错时存在该键 | `"failed"` |

### exit

退出 App

- 参数：无

- 返回：

    | Key     | Type   | Description                      | Example    |
    | ------- | ------ | -------------------------------- | ---------- |
    | `error` | string | 错误信息标识，仅当出错时存在该键 | `"failed"` |

### setBrightness

调整屏幕亮度

- 参数：

    | Key    | Type    | Description                                                  | Example |
    | ------ | ------- | ------------------------------------------------------------ | ------- |
    | `mode` | integer | 模式 (必需)<br />`0`: 自适应模式;<br />`1`: 最亮模式;<br />`-1`: 最暗模式; | `1`     |

- 返回：

    | Key     | Type   | Description                      | Example    |
    | ------- | ------ | -------------------------------- | ---------- |
    | `error` | string | 错误信息标识，仅当出错时存在该键 | `"failed"` |

### setBadgeNumber

设置应用角标数字值

- 参数：

    | Key     | Type    | Description | Example |
    | ------- | ------- | ----------- | ------- |
    | `value` | integer | 数字值      | `2`     |

- 返回：

    | Key     | Type   | Description                      | Example    |
    | ------- | ------ | -------------------------------- | ---------- |
    | `error` | string | 错误信息标识，仅当出错时存在该键 | `"failed"` |

### setStatusBarStyle

调整系统状态栏前景样式

- 参数：

    | Key     | Type   | Description                                            | Example  |
    | ------- | ------ | ------------------------------------------------------ | -------- |
    | `style` | string | 样式 (必需)<br />`"dark"`: 黑色;<br />`"light"`: 白色; | `"dark"` |

- 返回：

    | Key     | Type   | Description                      | Example    |
    | ------- | ------ | -------------------------------- | ---------- |
    | `error` | string | 错误信息标识，仅当出错时存在该键 | `"failed"` |

### i18nGetLocale

获取当前语言

- 参数：无

- 返回：

    | Key      | Type   | Description                      | Example    |
    | -------- | ------ | -------------------------------- | ---------- |
    | `error`  | string | 错误信息标识，仅当出错时存在该键 | `"failed"` |
    | `locale` | string | 语言标识                         | `"en_US"`  |

### i18nSetLocale

设置当前语言

- 参数：

    | Key      | Type   | Description     | Example   |
    | -------- | ------ | --------------- | --------- |
    | `locale` | string | (必需) 语言标识 | `"en_US"` |

- 返回：

    | Key     | Type   | Description                      | Example    |
    | ------- | ------ | -------------------------------- | ---------- |
    | `error` | string | 错误信息标识，仅当出错时存在该键 | `"failed"` |

### setSplashBanner

更新启动页广告信息

- 参数：

    | Key        | Type    | Description             | Example |
    | ---------- | ------- | ----------------------- | ------- |
    | `id`       | integer | (必需) 广告 ID          |         |
    | `name`     | string  | (必需) 广告名称         |         |
    | `image`    | string  | (必需) 广告图片 URL     |         |
    | `startsAt` | integer | (必需) 广告显示起始时间 |         |
    | `endsAt`   | integer | (必需) 广告显示结束时间 |         |

- 返回：

    | Key     | Type   | Description                      | Example    |
    | ------- | ------ | -------------------------------- | ---------- |
    | `error` | string | 错误信息标识，仅当出错时存在该键 | `"failed"` |

### wechatShare

分享到微信

- 参数：

    | Key | Type | Description | Example |
    | --- | --- | --- | --- |
    | `isText` | boolean | (必需) 是否为纯文本消息 | `false` |
    | `text` | string  | 文本消息内容 (`isText` 为 `true` 时必需) | `""` |
    | `title` | string | 消息标题 (`isText` 为 `false` 时必需) | `""` |
    | `description` | string | 消息内容 (`isText` 为 `false` 时必需) | `""` |
    | `thumbUrl` | string | 消息缩略图 URL | `""` |
    | `scene` | string  | (必需) 发送目标场景<br />`"session"`: 对话;<br />`"timeline"`: 朋友圈;<br />`"favorite"`: 收藏; | |
    | `mediaObjectType` | string  | 多媒体消息类型<br />`"image"`: 图片;<br />`"music"`: 音乐;<br />`"video"`: 视频;<br />`"webpage"`: 网页;<br />`"miniProgram"`: 小程序; | |
    | `mediaObject` | dict | 多媒体消息参数 | `{}` |
    | `mediaObject.imageUrl` | string  | (图片类型时必需) 图片 URL | `""` |
    | `mediaObject.musicUrl` | string  | (音乐类型时必需) 音乐网页 URL | `""` |
    | `mediaObject.musicDataUrl` | string  | (音乐类型时必需) 音乐数据 URL | `""` |
    | `mediaObject.videoUrl` | string | (视频类型时必需) 视频数据 URL | `""` |
    | `mediaObject.webpageUrl` | string | (网页类型时必需) 网页 URL | `""` |
    | `mediaObject.webpageUrl` | string | (小程序类型时必需) 兼容网页 URL | `""` |
    | `mediaObject.userName` | string | (小程序类型时必需) 小程序 ID | `""` |
    | `mediaObject.path` | string | (小程序类型时必需) 小程序页面路径 | `""` |
    |`mediaObject.hdImageUrl`  | string | (小程序类型时必需) 预览图片 URL | `""` |
    | `mediaObject.withShareTicket` | boolean | (小程序类型时必需) 是否使用带 `shareTicket` 的分享 | false |
    |`mediaObject.miniProgramType`  | string | (小程序类型时必需) 小程序的类型<br />`"release"`: 正式版;<br />`"test"`: 测试版;<br />`"preview"`: 体验版; |  |

- 返回：

    | Key      | Type   | Description                      | Example    |
    | -------- | ------ | -------------------------------- | ---------- |
    | `error`  | string | 错误信息标识，仅当出错时存在该键 | `"failed"` |
    | `result` | dict   | SDK 回调通知                     | `{}`       |

### alipayPayment

支付宝 SDK 支付请求

- 参数：

    | Key           | Type   | Description           | Example |
    | ------------- | ------ | --------------------- | ------- |
    | `orderString` | string | (必需) 请求参数字符串 |         |

- 返回：

    | Key      | Type   | Description                      | Example    |
    | -------- | ------ | -------------------------------- | ---------- |
    | `error`  | string | 错误信息标识，仅当出错时存在该键 | `"failed"` |
    | `result` | dict   | SDK 回调通知                     | `{}`       |

### wechatpayPayment

微信 SDK 支付请求

- 参数：

    | Key            | Type   | Description              | Example                              |
    | -------------- | ------ | ------------------------ | ------------------------------------ |
    | `appId`        | string | (必需) 应用 ID           | `"wx8888888888888888"`               |
    | `partnerId`    | string | (必需) 商户号            | `"1900000109"`                       |
    | `prepayId`     | string | (必需) 预支付交易会话 ID | `"WX1217752501201407033233368018"`   |
    | `packageValue` | string | (必需) 扩展字段          | `"Sign=WXPay"`                       |
    | `nonceStr`     | string | (必需) 随机字符串        | `"5K8264ILTKCH16CQ2502SI8ZNMTM67VS"` |
    | `timeStamp`    | string | (必需) 时间戳            | `"1412000000"`                       |
    | `sign`         | string | (必需) 签名              | `"C380BEC2BFD727A4B6845133519F3AD6"` |

- 返回：

    | Key      | Type   | Description                      | Example    |
    | -------- | ------ | -------------------------------- | ---------- |
    | `error`  | string | 错误信息标识，仅当出错时存在该键 | `"failed"` |
    | `result` | dict   | SDK 回调通知                     | `{}`       |

### oauthWechat

微信登录授权

- 参数：

    | Key     | Type   | Description     | Example             |
    | ------- | ------ | --------------- | ------------------- |
    | `scope` | string | (必需) 授权域   | `"snsapi_userinfo"` |
    | `state` | string | (必需) 状态标识 | `""`                |

- 返回：

    | Key      | Type   | Description                      | Example    |
    | -------- | ------ | -------------------------------- | ---------- |
    | `error`  | string | 错误信息标识，仅当出错时存在该键 | `"failed"` |
    | `result` | dict   | SDK 回调通知                     | `{}`       |

### oauthFacebook / oauthLine

第三方登录授权

- 参数：无

- 返回：

    | Key     | Type   | Description                      | Example    |
    | ------- | ------ | -------------------------------- | ---------- |
    | `error` | string | 错误信息标识，仅当出错时存在该键 | `"failed"` |
    | `token` | string | 回调 Access Token                |            |

## 接口：Native-H5

### pushMessage

推送消息

- 参数：

    | Key       | Type    | Description                  | Example                           |
    | --------- | ------- | ---------------------------- | --------------------------------- |
    | `subject` | string  | 消息体标题                   | `"The message subject goes here"` |
    | `body`    | string  | 消息体内容                   | `"The message body goes here"`    |
    | `date`    | integer | 推送时间，格式为 Unix 时间戳 | `1442534400`                      |
    | `extras`  | dict    | 附加数据                     | `{ "foo": "bar" }`                |

- 返回：无

### pausing

当 App 正在置于后台

- 参数：无

- 返回：无

### pause

当 App 已置于后台

- 参数：无

- 返回：无

### resuming

当 App 正在置于前台

- 参数：无

- 返回：无

### resume

当 App 已置于前台

- 参数：无

- 返回：无

### backButton

设备返回按钮被点击 (仅 Android)

- 参数：无

- 返回：无

### menuButton

设备菜单按钮被点击 (仅 Android)

- 参数：无

- 返回：无

### searchButton

设备搜索按钮被点击 (仅 Android)

- 参数：无

- 返回：无
