
## 青龙拉取链接(sendNotify需要放到/ql/deps目录下)
``` 
ql repo https://github.com/58565856/KKK.git "jd_|jx_|jddj_|gua_|getJDCookie|wskey" "activity|backUp|encrypted" "^jd[^_]|USER|utils|ZooFaker_Necklace|JDJRValidator_|sign_graphics_validate|jddj_cookie|function|ql|magic|JDJR|JD|sendNotify" "main"
```

## 带ccwav大佬通知版(不需要放/ql/deps目录下)
``` 
ql repo https://github.com/58565856/KKK.git "jd_|jx_|jddj_|gua_|getJDCookie|wskey|sendNotify" "activity|backUp|encrypted" "^jd[^_]|USER|utils|ZooFaker_Necklace|JDJRValidator_|sign_graphics_validate|jddj_cookie|function|ql|magic|JDJR|JD" "main"
```
```
推荐定时 0 */4 * * *
```


[退会：JDMemberCloseAccount](https://github.com/yqchilde/JDMemberCloseAccount)

修改deps内的sendNotify.js
可以设置青龙config内EnableExtraShell="true"
然后填写[task_after.sh](https://raw.githubusercontent.com/gys619/Absinthe/main/task_after.sh) (仓库内的仅供参考)

免责声明: 本仓库项目中所涉及的任何解锁和解密分析脚本，仅用于测试和学习研究，不保证其合法性，准确性，完整性和有效性，请根据情况自行判断。请勿将本项目的任何内容用于商业或非法途径，否则后果由使用者自负。如果您认为该项目的内容可能涉嫌侵犯其权利，请与我联系，我会尽快删除文件。如果您使用或复制了本仓库项目中的任何内容，则视为您已接受此免责声明。

拉不到库，需要删了重新拉一下，运行一下下面命令就好了，库不稳，见谅！

docker exec -it 容器名 bash

cd repo

rm -rf gys619_Absinthe_main

<details>
<summary>使用技巧与问题解答</summary>
<pre><code>

1、涉及兑换或需要抢的可以配置任务并发，就是全部一起跑。

并发配置方法：

在任务后面加conc JD_COOKIE

如 task XXXXX.js conc JD_COOKIE

任务分组运行方法：

在任务后面加desi JD_COOKIE 需要运行的ck序号

如 task XXXX.js desi JD_COOKIE 1-10  前10个一组运行，2 8 9就是第2/8/9序号的ck执行，以此类推。

2、极速版签到建议并发，号多跑很久的，一个号要30多分钟。。

task 6dylan6_jdpro_jd_speed_sign.js conc JD_COOKIE （具体任务路径不同版本不一样，按自己的写）

3、保价建议并发，否则可能前几个号正常跑，后面会报频繁！

task 6dylan6_jdpro_jd_price.js conc JD_COOKIE

4、通知支持一对一推送和显示备注，详细用法参考[notify.md](./notify.md)

备注显示变量如下

export NOTIFY_SHOWNAMETYPE="1"    不做任何变动

export NOTIFY_SHOWNAMETYPE="2"    效果是 :  账号名称：别名(备注)	

export NOTIFY_SHOWNAMETYPE="3"    效果是 :  账号名称：pin(备注)

export NOTIFY_SHOWNAMETYPE="4"    效果是 :  账号名称：备注

5、因为青龙有随机延时（可以在配置文件设置为0，默认300秒），所以涉及准点运行的任务，最后加now，如果是desi或conc不用加也会准时跑。

6、青龙系统通知（新增删除任务、登录等通知），需把通知变量写到config.sh文件，在环境变量里只发脚本运行通知哈。

7、本库开卡任务默认不执行，如需运行请设置变量export DY_OPENALL="true"，所有开卡任务通用。

8、如果通知文件发现和库里的不一致，那是青龙自带的覆盖了，正常库里会自动覆盖掉青龙的通知文件，如果没有自动那就手动拷贝一份到deps目录下吧，或者直接删掉deps目录下的sendnotify.js

9、建议调整任务运行超时时间，青龙默认1小时有些脚本跑不完就被强制kill，config.sh里配置。CommandTimeoutTime="3h"  即改为3小时，根据自己的号数量调整。
</code></pre>
</details>

## 加密脚本清单

<details>
<summary>加密脚本清单，不放心可禁用</summary>
<pre><code>
jd_zjd.js (赚京豆，全加密）
jd_fans.js （粉丝互动，全加密）
jd_half_redrain.js (半点京豆雨，全加密）
jd_jxmc.js （京喜牧场，算法加密）
jd_cfd.js （京喜财富岛，算法加密）
jd_cfd_loop.js (京喜财富岛捡贝壳，算法加密）
jd_speed_sign.js （极速版签到，算法加密）
jd_speed_signred.js  （极速版红包，算法加密）
开卡系列全部都有算法加密 
</code></pre>
</details>


## 控制脚本功能环境变量


|             Name             |             归属             |  属性  | 说明                                                         |
| :--------------------------: | :--------------------------: | :----: | ------------------------------------------------------------ |
|     `PET_NOTIFY_CONTROL`     |     东东萌宠<br>推送开关     | 非必须 | 控制京东萌宠是否静默运行,<br>`false`为否(发送推送通知消息),`true`为是(即：不发送推送通知消息) |
|    `FRUIT_NOTIFY_CONTROL`    |     东东农场<br>推送开关     | 非必须 | 控制京东农场是否静默运行,<br>`false`为否(发送推送通知消息),`true`为是(即：不发送推送通知消息) |
|    `NOTIFY_AUTOCHECKCK`    |       自动禁用失效CK开关  | 非必须 | 有CK失效自动禁用并通知，true为自动禁用，false不自动禁用，默认false |
|       `JOY_FEED_COUNT`       |        宠汪汪喂食数量        | 非必须 | 控制`jd_joy_feedPets.js`脚本喂食数量,可以填的数字10,20,40,80,其他数字不可. |
|       `NOTIFY_SKIP_LIST`       |        控制关闭某些标题的通知  | 非必须 | 通知标题在此变量里面存在(&隔开),则屏蔽不发送通知.例 : export NOTIFY_SKIP_LIST="临期京豆换喜豆&京东资产统计" |
|      `FRUIT_BEAN_CARD`       |    农场<br>使用水滴换豆卡    | 非必须 | 农场使用水滴换豆卡(如果出现限时活动时100g水换20豆,此时比浇水划算,推荐换豆),<br>`true`表示换豆(不浇水),`false`表示不换豆(继续浇水),脚本默认是浇水 |
|       `JD_UNSUB`             |      批量取消商品与店铺关注开关      | 非必须 | 控制jd_unsubscribe.js运行，默认为true取关，false不取关 |
|       `JD_CART_REMOVE`       |      清空购物车      | 非必须 | 控制jd_clean_car.js运行 ，默认false不清空，true清空 |
|   `MONEY_TREE_SELL_FRUIT`    |    摇钱树<br>是否卖出金果    | 非必须 | 控制摇钱树脚本是否自动卖出金果兑换成金币，`true`卖出，`false`不卖出，默认卖出 |
|   `QCARD`    |    店铺退会链接<br>是否运行    | 非必须 | 按需运行，`true`运行，默认`false`不运行 |
|   `Ev_Start`    |    自动评价<br>是否运行    | 非必须 | 选择运行，`true`运行，默认`false`不运行 |
|   `exjxbeans`                |     临期京豆换喜豆     | 非必须 | 默认为false不换，设置true换7天内过期京豆换喜豆 |
|   `WSKEY_DISCHECK`           |     wskey转换     | 非必须 | 默认为false检查，设置true为不检查直接转换 |
|   ` HelpType`           |     互助模式    | 非必须 | 默认顺序助力，0是全部一样顺序助力，1是均等机会助力，2是随机顺序助力，例： export HelpType=1 |
|   `PandaToken`           |     领现金使用     | 非必须 | Token去[TG](https://t.me/pang_da_bot) 获取，获取一次7天有效期1000次调用，export PandaToken='你获取的token' |
|   `DY_OPENALL`           |     开卡系列     | 非必须 |开卡系列任务默认不执行，设置变量DY_OPENALL='true'执行 |




### 脚本说明
<details>
<summary>查看</summary>

加了一件安装依赖脚本

* 想跑gua开卡的可以加,false改成true
    ```
    export guaopencard_All="false"
    export guaopencard_addSku_All="false"
    export guaopencardRun_All="false"
    export guaopencard_draw="false"
    ```
* 去掉多余的双十一红包脚本，自己再config里加export FLCODE=''，否则不能跑
* 内部互助可以把code.sh和task_before.sh放config目录下，并添加一个code的定时任务，命令:task /ql/config/code.sh
* 加KingRan大佬仓库
* 最新面板2.9.7或者新版拉不到可以进入容器
    ```
    docker exec -it 容器名 bash
    cd repo
    rm -rf gys619_jdd
    ```

* 加了[Oreomeow大佬](https://raw.githubusercontent.com/Oreomeow/VIP/main/Conf/Qinglong/config.sample.sh)的config模板,名字是jd_config.sample.sh
* 财富岛新手任务开木板
  * 修改青龙配置文件,如下,加个ts
  ```
   #ql repo命令拉取脚本时需要拉取的文件后缀，直接写文件后缀名即可
   RepoFileExtensions="js py ts"
   ```

 
 
</details>

### 安装青龙需要一些的依赖
<details>
<summary>查看依赖列表</summary>


* 最新青龙支持安装依赖需要啥依赖，去依赖管理添加即可，简单方便
* 遇到Cannot find module 'xxxxxx'报错就进入青龙容器
* docker exec -it QL(自己容器名) bash
* pnpm install xxxxx(报错中引号里的复制过来)

 

 安装青龙的一些依赖，按需求安装
* docker exec -it qinglong(自己容器名) bash -c "npm install -g typescript"

* docker exec -it qinglong bash -c "npm install axios date-fns"

* docker exec -it qinglong bash -c "npm install crypto -g"

* docker exec -it qinglong bash -c "npm install png-js"

* docker exec -it qinglong bash -c "npm install -g npm"

* docker exec -it qinglong bash -c "pnpm i png-js"

* docker exec -it qinglong bash -c "pip3 install requests"

* docker exec -it qinglong bash -c "apk add --no-cache build-base g++ cairo-dev pango-dev giflib-dev && cd scripts && npm install canvas --build-from-source"

* docker exec -it qinglong bash -c "apk add python3 zlib-dev gcc jpeg-dev python3-dev musl-dev freetype-dev"

* docker exec -it qinglong bash -c "cd /ql/scripts/ && apk add --no-cache build-base g++ cairo-dev pango-dev giflib-dev && npm i && npm i -S ts-node typescript @types/node date-fns axios png-js canvas --build-from-source"

或者

* npm install -g png-js
* npm install -g date-fns
* npm install -g axios
* npm install -g crypto-js
* npm install -g ts-md5
* npm install -g tslib
* npm install -g @types/node
* npm install -g requests

</details>



### 青龙拉取常用京东脚本库([Oreomeow大佬](https://github.com/Oreomeow/VIP/blob/main/Tasks/qlrepo/Readme.md)整理的一些仓库)
<details>
<summary>京东脚本库</summary>
 

#### 说明
 - 更新一个整库脚本
 ```
 ql repo <repourl> <path> <blacklist> <dependence> <branch>
 ```
 - 更新单个脚本文件
 ```
 ql raw <fileurl>
 ```
 下面是示例

#### 整库
- `Unknown 备份托管等`
  
  1. `JDHelloWorld`
  ```
  ql repo https://github.com/JDHelloWorld/jd_scripts.git "jd_|jx_|getJDCookie" "activity|backUp|Coupon|enen|update|test" "^jd[^_]|USER|^TS|utils|notify|env|package|ken.js"
  ```
  2. `he1pu`（自动提交助力码-京喜工厂、种豆得豆、东东工厂、东东农场、健康社区、京喜财富岛、东东萌宠、闪购盲盒，随机从数据库中选取助力码互助）
  ```
  ql repo https://github.com/he1pu/JDHelp.git "jd_|jx_|getJDCookie" "Coupon|update" "^jd[^_]|USER|^sign|^ZooFaker|utils"
  ```
  3. `shufflewzc`
  ```
  ql repo https://github.com/shufflewzc/faker2.git "jd_|jx_|gua_|jddj_|getJDCookie" "activity|backUp" "^jd[^_]|USER|utils|^JS|^TS|^JDJRValidator_Pure|^ZooFaker|^sign"
  ```
  4. `Aaron-lv`
  ```
  ql repo https://github.com/Aaron-lv/sync.git "jd_|jx_|getJDCookie" "activity|backUp|Coupon" "^jd[^_]|USER|utils" "jd_scripts"
  ```
  5. `panghu999`（无维护）
  ```
  ql repo https://github.com/panghu999/jd_scripts.git "jd_|jx_|getJDCookie" "activity|backUp|Coupon|jd_try|format_" "^jd[^_]|USER"
  ```
  6. `chinnkarahoi`（无维护）
  ```
  ql repo https://github.com/chinnkarahoi/jd_scripts.git "jd_|jx_|getJDCookie" "activity|backUp|Coupon" "^jd[^_]|USER"
  ```

- `passerby-b`
```
ql repo https://github.com/passerby-b/JDDJ.git "jddj_" "scf_test_event|jddj_fruit_code.js|jddj_getck.js|jd_|jddj_cookie"
```
- `curtinlv`
```
ql repo https://github.com/curtinlv/JD-Script.git "jd_"
```
- `smiek2221`
```
ql repo https://github.com/smiek2221/scripts.git "jd_|gua_" "" "^MovementFaker|^JDJRValidator|^ZooFaker|^sign" 
```
- `cdle`
```
ql repo https://github.com/cdle/xdd.git "jd_" "disposable|expired|jdc"
```
- `ZCY01`
```
ql repo https://github.com/ZCY01/daily_scripts.git "jd_"
```
- `whyour/hundun`
```
ql repo https://github.com/whyour/hundun.git "quanx" "tokens|caiyun|didi|donate|fold|Env"
```
- `moposmall`
```
ql repo https://github.com/moposmall/Script.git "Me"
```
- `Ariszy (Zhiyi-N)`
```
ql repo https://github.com/Ariszy/Private-Script.git "JD"
```
- `photonmang`（宠汪汪及兑换、点点券修复）
```
ql repo https://github.com/photonmang/quantumultX.git "JDscripts"
```
- `jiulan`
```
ql repo https://github.com/jiulan/platypus.git "jd_|jx_" "" "overdue" "main"
```
- `star261`
```
ql repo https://github.com/star261/jd.git "jd_|star" "" "code" "main"
```
- `Wenmoux`
```
ql repo https://github.com/Wenmoux/scripts.git "other|jd" "" "" "wen"
```
- `Tsukasa007`
```
ql repo https://github.com/Tsukasa007/my_script.git "jd_|jx_" "jdCookie|USER_AGENTS|sendNotify|backup" "" "master"
```

#### 单脚本
#### 名称之后标注`﹢`的单脚本，若上面已拉取仓库的可以不拉，否则会重复拉取。这里适用于只拉取部分脚本使用
> `curtinlv`﹢

>> 入会
```
ql raw https://raw.githubusercontent.com/curtinlv/JD-Script/main/OpenCard/jd_OpenCard.py
```
>> 关注
```
ql raw https://raw.githubusercontent.com/curtinlv/JD-Script/main/getFollowGifts/jd_getFollowGift.py
```

> `chiupam`

>> 京喜工厂瓜分电力开团 ID 
```
ql raw https://raw.githubusercontent.com/chiupam/JD_Diy/master/pys/activeId.py
```

> `Aaron-lv`+

>> 财富岛
```
ql raw https://raw.githubusercontent.com/Aaron-lv/sync/jd_scripts/jd_cfd.js
```
or
```
ql repo https://github.com/Aaron-lv/sync.git "jd_cfd" "" "" "jd_scripts"
```

> `Wenmoux`+

>> 口袋书店
```
ql raw https://raw.githubusercontent.com/Wenmoux/scripts/wen/jd/chinnkarahoi_jd_bookshop.js
```
or
```
ql repo https://github.com/Wenmoux/scripts.git "chinnkarahoi_jd_bookshop" "" "" "wen"
```

> `NobyDa`

>> 京东多合一签到脚本

```
ql raw https://raw.githubusercontent.com/NobyDa/Script/master/JD-DailyBonus/JD_DailyBonus.js
```
or
```
ql repo https://github.com/NobyDa/Script.git "JD-DailyBonus" "" "JD_DailyBonus" "master"
```

#### 已删库存档
- `monk-coder`
```
ql repo https://github.com/monk-dust/dust.git "i-chenzhe|normal|member|car" "backup"
```
- `hyzaw`
```
ql repo https://github.com/hyzaw/scripts.git "ddo_"
```
- `zooPanda`
```
ql repo https://github.com/zooPanda/zoo.git "zoo"
```
- `longzhuzhu`
```
ql repo https://github.com/longzhuzhu/nianyu.git "qx"
```
- `panghu999/panghu`
```
ql repo https://github.com/panghu999/panghu.git "jd_"
```
</details>
 
 

 
 
 

### 致谢
* [@kangwenhang](https://github.com/kangwenhang)
* [@smiek2221](https://github.com/smiek2221/scripts.git)
* [@yuannian1112](https://github.com/yuannian1112/jd_scripts.git)
*  [@okyyds](https://github.com/okyyds/yyds/tree/master)
*  [@shufflewzc](https://github.com/shufflewzc/faker2/tree/main)
*  [@passerby-b](https://github.com/passerby-b/JDDJ.git)
*  [@he1pu](https://github.com/he1pu/JDHelp.git)
*  [@ccwav](https://github.com/ccwav/QLScript2.git)
*  [@Zy143L](https://github.com/Zy143L/wskey.git)
*  [@X1a0He](https://github.com/X1a0He/jd_scripts_fixed)
*  [@KingRan](https://github.com/KingRan/KR)
*  [@Aaron-lv](https://github.com/Aaron-lv/sync)
*  [@zero205](https://github.com/zero205/JD_tencent_scf)
*  [@okyyds_duck](https://github.com/okyyds/duck.git)
