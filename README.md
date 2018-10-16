## 通用参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|token|字符串|用户登录凭证|否|
|ver|字符串|版本号|是|
|pf|字符串|客户端平台类型,iOS或者android|是|
|cityId|数字|城市id|是|

## 接口域名
```
  测试:hzp.caidingke.net
  正式:hzp.baihejia.com
```

## 错误码
|code|msg|
|---|---|
|10001| "验证码错误。"|
|10002| "请勿重复操作，请稍候。"|
|10003| "您的操作过于频繁，请稍后重试。"|
|10004| "非法的平台标识。"|
|10005| "生日格式不正确。"|
|10006| "腾讯云IM注册失败。"|
|10007| "目前不支持更换手机号功能。"|
|10008| "该手机号码已被绑定。"|
|10009| "芝麻信用查询失败。"|
|10010| "房源不存在。"|
|10011| "该房源已被签约。"|
|10012| "签约信息已存在。"|
|10013| "参数校验失败。"|
|10014| "合同信息不存在。"|
|10015| "用户昵称包含非法字符。"|
|90001| "卧室至少一间"|
|90002| "出租房间不能为空"|
|90003| "图片不能为空"|
|90004| "租金不能为空"|
|90005| "租金不能小于三位数"|
|90006| "付款方式不能为空"|
|90007| "半年内只能发布一次"|
|80001| "请设置商户号mchId"|
|80002| "请设置证书地址cert"|
|80003| "签名校验失败"|
|80004| "调用微信接口失败"|
|80005| "无法获取预支付交易会话标识"|
|80006| "订单不存在"|

## 搜索
### 模糊搜索关键词列表
##### 接口:/Match/search
##### 请求方式:GET
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|type|Integer|搜索类型,1-出租,2-合租|是|
|name|String|搜索关键字|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": [
    {
      "aliasName": "小区",
      "name": "1+1联合大厦",
      "cityId": 1,
      "type": 2,
      "url": "b1143c1196u1084018"
    }
  ]
}
```
## 投诉/建议/反馈
### 反馈
##### 接口:/ProfileController/feedback
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|url|String|图片url|否|
|content|String|反馈内容|是|
|contact|String|联系方式|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}
```

## 交互（社区/评论/动态/通知/点赞/收藏/分享）
### 输入邀请码
##### 接口:/UserController/provideInvitationCode
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|invitationCode|String|邀请码|是|
##### 成功返回值
```
{
	"ret": 200,
	"data": 0.5//金额大于0给用户提示
}
```

### 点击push消息
##### 接口:/UserController/clickPush
##### 请求方式:GET
|参数名|类型|描述|是否必须|
|---|---|---|---|
|uid|String|pushId|是|
##### 成功返回值
```
{
	"ret": 200,
	"data": {}
}
```

### 客户端私信调用
##### 接口:/PrivateMsgController/sendMessage
##### 请求方式:GET
|参数名|类型|描述|是否必须|
|---|---|---|---|
|toUserId|long|被私信的用户id|是|
##### 成功返回值
```
{
	"ret": 200,
	"data": {}
}
```

### 参与活动用户列表
##### 接口:/CommunityController/joinUsers
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|infoId|Long|主题id|是|
|infoType|String|GANG/ACTIVITY|是|
|page|Integer|>=1|是|
|pageSize|Integer|>=1|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": [
    {
      "id": 134,
      "nickname": "坚果🌰🌰",
      "nicknameModified": true,
      "avatar": "http://test-1251500528.file.myqcloud.com/hzp/df520be7fb839e1bd7f998b8207ca18a45",
      "avatarModified": true,
      "gender": 2,
      "genderModified": true,
      "mobileNumber": "13021022715",
      "ageLabel": 4,
      "birthday": "12-01",
      "pushToken": "An-jCefuudEIBgPUwvIFmHwSJqOhp4QSr7UE42xqXEAA",
      "pf": "WEB",
      "career": "销售",
      "favorite": "工作,美食,旅游,电影",
      "personalProfile": "我去拯救地球了...",
      "zmScore": 0,
      "zmAuth": false,
      "constellation": "射手座",
      "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
      "zmAuthPushed": false,
      "infoCompleted": true,
      "flag": false,
      "privacy": 0,
      "forbidden": false,
      "virtual": false,
      "isPublishHouse": true,
      "isPublishHouseRequest": true
    }
  ]
}
```

### 分享动态
##### 接口:/CommunityController/share
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|infoId|Long|动态id|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}
```

### 社区首页
##### 接口:/CommunityController/communityList
##### 请求方式:GET
##### 接口参数
无

##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "gangList": [
      {
        "id": 2,
        "name": "论有一个漂亮的合租室友是一种怎样的体验？",
        "image": "https://test-1251500528.file.myqcloud.com/backend/img/152222182897756c6692de80f1.jpg",
        "content": "说起我的漂亮室友，“浓眉大眼、五官精致”已经不足以用来形容其漂亮之极，那小脸儿叫一个肤若凝脂、细腻光滑呀，一双炯炯有神的大眼睛，长长的睫毛扑闪扑闪，高挺的鼻梁，深深的酒窝，修长的手指……口水流一地……没错！！他就是位男生啊…楼主超级羡慕的好不好…秀出你的漂亮合租室友，超1000人，楼主上图！PS，最热的可能被抽中做我们合租派的封面人物哦，一不小心成网红，你说气人不气人，咯咯。",
        "combatPower": 51,
        "joinCount": 23,
        "isBroker": false
      },
      {
        "id": 3,
        "name": "有没有一部电影让你一个人在深夜中痛哭？",
        "image": "https://test-1251500528.file.myqcloud.com/backend/img/15222219894640adbfea0200c5c7cc785bd3dc1dcb540958445ae.jpg",
        "content": "现在的我们，尽可以在办公室干劲十足地加班，在周末的饭局上谈笑风生，认真地考虑健身、过积极的生活。可是下班回家后，便不再想多说一句话，换一身宽松的衣服，一个人窝着挑一部电影，慢慢看来，有时候不知不觉脸上也挂满泪痕，越来越容易被感动，是因为经历了越来越多。有哪部电影让你一个人在深夜里痛哭过呢，说出来，让我们知道。",
        "combatPower": 9,
        "joinCount": 3,
        "isBroker": false
      }
    ],
    "banners": [
         {
            "pictureUrl" : "null/public/img/banner7.jpg",
            "redirectUrl" : "null/community/page7",
            "shareContent" : "",
            "shareFriendsCircle" : "",
            "shareSina" : "@合租趣，有家，有友，有故事null/community/page7",
            "shareTitle" : ""
         },
         {
            "pictureUrl" : "null/public/img/banner5.jpg",
            "redirectUrl" : "null/community/page5",
            "shareContent" : "Dylan说，租房改造后，找室友一起合租成为了幸福的事儿",
            "shareFriendsCircle" : "Dylan说，租房改造后，找室友一起合租成为了幸福的事儿",
            "shareSina" : "Dylan说，租房改造后，找室友一起合租成为了幸福的事儿@合租趣，有家，有友，有故事null/community/page5",
            "shareTitle" : "Dylan说，租房改造后，找室友一起合租成为了幸福的事儿"
         },
         {
            "pictureUrl" : "null/public/img/banner4.jpg",
            "redirectUrl" : "null/community/page4",
            "shareContent" : "震惊！租房押金保险免费送",
            "shareFriendsCircle" : "震惊！租房押金保险免费送",
            "shareSina" : "震惊！租房押金保险免费送@合租趣，有家，有友，有故事null/community/page4",
            "shareTitle" : "震惊！租房押金保险免费送"
         },
         {
            "pictureUrl" : "null/public/img/banner1.jpg",
            "redirectUrl" : "null/community/page1",
            "shareContent" : "阿翔说：妈妈给我起名字的时候，翔还是一个褒义词",
            "shareFriendsCircle" : "阿翔说：妈妈给我起名字的时候，翔还是一个褒义词",
            "shareSina" : "阿翔说：妈妈给我起名字的时候，翔还是一个褒义词@合租趣，有家，有友，有故事null/community/page1",
            "shareTitle" : "阿翔说：妈妈给我起名字的时候，翔还是一个褒义词"
         },
         {
            "pictureUrl" : "null/public/img/banner2.jpg",
            "redirectUrl" : "null/community/page2",
            "shareContent" : "遇见望京1904，再没什么比这更好的了",
            "shareFriendsCircle" : "遇见望京1904，再没什么比这更好的了",
            "shareSina" : "遇见望京1904，再没什么比这更好的了@合租趣，有家，有友，有故事null/community/page2",
            "shareTitle" : "遇见望京1904，再没什么比这更好的了"
         }
    ]
  }
}
```

### 活动页面
##### 接口:/CommunityController/gangDetail
##### 请求方式:GET
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|id|Long|活动id|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "shareInfo": {
      "title": "电影，遇见另一种人生",
      "content": "一部电影便可以解释全世界",
      "friendsCircle": "电影，遇见另一种人生",
      "sina": "电影发明以后，人类的生命比起以前延长了至少三倍。（一一），通过电影你可以看到梦想的影子。遇到对的电影，是一件非常惬意的事。@合租派，有家，有友，有故事。null/community/gang?gangId=3&share=true",
      "image": "http://test-1251500528.file.myqcloud.com/backend/img/15222219894640adbfea0200c5c7cc785bd3dc1dcb540958445ae.jpg",
      "shareUrl": "null/community/gang?gangId=3&share=true"
    },
    "signature": "0dbd059161b486233c7860ceeb1ca9a72d6bf905",
    "gangView": {
      "id": 3,
      "name": "有没有一部电影让你一个人在深夜中痛哭？",
      "image": "https://test-1251500528.file.myqcloud.com/backend/img/15222219894640adbfea0200c5c7cc785bd3dc1dcb540958445ae.jpg",
      "declaration": "http://test-1251500528.file.myqcloud.com/backend/img/15222220244551350272012760.jpg",
      "userId": 21,
      "nickname": "鹤舞清风",
      "avatar": "https://wx.qlogo.cn/mmopen/vi_32/GdsKZDNqBbgdNAMOgKL4GcrI1PL8fyWOC22EqLUDyMEZ1JxU3aPn3xLDvwsT2fiao8LumLyyuTaemiaupuE7FQDw/0",
      "ageLabel": "95后",
      "constellation": "摩羯座",
      "career": "销售",
      "gender": 2,
      "combatPower": 9,
      "totalCount": 3,
      "joinCount": 3,
      "dynamicList": [
        {
          "id": 14,
          "infoId": 3,
          "content": "bbnbbkigghhhjjjjjkk",
          "image": "http://test-1251500528.file.myqcloud.com/hzpfd044d58-7ee9-44f8-a4d0-0e3d4561a49b.jpg",
          "userId": 92,
          "nickname": "雪花",
          "avatar": "http://test-1251500528.file.myqcloud.com/hzp88f5d4bb-270a-4aa9-b63f-8cd72e8e20b9.jpg",
          "gender": 1,
          "likedCount": 0,
          "messageCount": 0,
          "forwardCount": 0,
          "infoType": "GANG",
          "infoName": "有没有一部电影让你一个人在深夜中痛哭？",
          "liked": false,
          "createTime": "04-28",
          "messageViewList": [],
          "share": "/login",
          "joinCount": 3,
          "isBroker": false
        },
        {
          "id": 4,
          "infoId": 3,
          "content": "我做最在真为我",
          "image": "http://test-1251500528.file.myqcloud.com/hzp59a66a11-1f87-4eb8-8f37-991a030c7a7d.jpg",
          "userId": 88,
          "nickname": "雨滴💦",
          "avatar": "http://test-1251500528.file.myqcloud.com/hzp06f665c6-a936-447b-b3fb-b02d85aa7743.jpg",
          "gender": 2,
          "likedCount": 0,
          "messageCount": 0,
          "forwardCount": 0,
          "infoType": "GANG",
          "infoName": "有没有一部电影让你一个人在深夜中痛哭？",
          "liked": false,
          "createTime": "04-17",
          "messageViewList": [],
          "share": "/login",
          "joinCount": 3,
          "isBroker": false
        },
        {
          "id": 3,
          "infoId": 3,
          "content": "么有",
          "image": "http://test-1251500528.file.myqcloud.com/hzp30122a0e-ba9b-4559-9562-77f8da12e6c0.jpg",
          "userId": 92,
          "nickname": "雪花",
          "avatar": "http://test-1251500528.file.myqcloud.com/hzp88f5d4bb-270a-4aa9-b63f-8cd72e8e20b9.jpg",
          "gender": 1,
          "likedCount": 1,
          "messageCount": 1,
          "forwardCount": 0,
          "infoType": "GANG",
          "infoName": "有没有一部电影让你一个人在深夜中痛哭？",
          "liked": false,
          "createTime": "04-16",
          "messageViewList": [
            {
              "id": 1104,
              "sentTime": "04-27",
              "context": "该评论已删除",
              "fromUserId": 83,
              "fromNickname": "杰瑞",
              "fromAvatar": "http://test-1251500528.file.myqcloud.com/hzp265d0e1e-baeb-40db-a4b9-c2b3176ef318.jpg",
              "fromGender": 1,
              "subMessageList": []
            }
          ],
          "share": "/login",
          "joinCount": 3,
          "isBroker": false
        }
      ],
      "joinUserList": [
        {
          "id": 83,
          "nickname": "杰瑞",
          "nicknameModified": true,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzp265d0e1e-baeb-40db-a4b9-c2b3176ef318.jpg",
          "avatarModified": true,
          "gender": 1,
          "genderModified": true,
          "mobileNumber": "",
          "ageLabel": 5,
          "birthday": "03-13",
          "pushToken": "5aa9242bf4c3f9a0a542d653680a71b2ada7c1446f27cbb693d6e0613d7037a5",
          "pf": "iOS",
          "career": "逗猫的",
          "favorite": "工作,旅游,读书,音乐,摄影",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "双鱼座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": true,
          "infoCompleted": true,
          "flag": false,
          "privacy": 1,
          "forbidden": false,
          "virtual": false
        }
      ],
      "isBroker": false
    },
    "appId": "wxdcffde018ea257ac",
    "jsapi_ticket": "HoagFKDcsGMVCIY2vOjf9rHPIm6CQmURTqD3zYD4uC02vipmlCQZPVNk1yox0vPZT97w6Kf3L2j_h56X2rBmEA",
    "url": "null/CommunityController/gangDetail?share=true&id=3",
    "nonceStr": "5228cf70-501f-45fe-a924-56307ee43429",
    "timestamp": "1525252445"
  }
}
```

### 动态分页
##### 接口:/CommunityController/dynamicList
##### 请求方式:GET
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|infoId|Long|主题id|是|
|infoType|String|GANG/ACTIVITY|是|
|page|Integer|>=1|否，默认1|
|order|String|new/hot|否，默认new|
##### 成功返回值
```
{
  "ret": 200,
  "data": [
    {
      "id": 3,
      "infoId": 3,
      "content": "么有",
      "image": "http://test-1251500528.file.myqcloud.com/hzp30122a0e-ba9b-4559-9562-77f8da12e6c0.jpg",
      "userId": 92,
      "nickname": "雪花",
      "avatar": "http://test-1251500528.file.myqcloud.com/hzp88f5d4bb-270a-4aa9-b63f-8cd72e8e20b9.jpg",
      "gender": 1,
      "likedCount": 1,
      "messageCount": 1,
      "forwardCount": 0,
      "infoType": "GANG",
      "infoName": "有没有一部电影让你一个人在深夜中痛哭？",
      "liked": false,
      "createTime": "04-16",
      "messageViewList": [
        {
          "id": 1104,
          "sentTime": "04-27",
          "context": "该评论已删除",
          "fromUserId": 83,
          "fromNickname": "杰瑞",
          "fromAvatar": "http://test-1251500528.file.myqcloud.com/hzp265d0e1e-baeb-40db-a4b9-c2b3176ef318.jpg",
          "fromGender": 1,
          "subMessageList": []
        }
      ],
      "share": "/login",
      "joinCount": 3,
      "isBroker": false
    }
  ]
}
```

### 动态详情
##### 接口:/CommunityController/dynamicDetail
##### 请求方式:GET
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|id|Long|动态|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "dynamicView": {
      "id": 21,
      "infoId": 2,
      "content": "回龙观医院治疗抑郁症了、\n",
      "userId": 89,
      "nickname": "龙",
      "avatar": "http://test-1251500528.file.myqcloud.com/hzp/4D5B137B-A260-42CD-95EC-D1688866D8E5.jpg",
      "gender": 1,
      "likedCount": 2,
      "messageCount": 9,
      "forwardCount": 1,
      "infoType": "GANG",
      "infoName": "论有一个漂亮的合租室友是一种怎样的体验？",
      "liked": false,
      "createTime": "20小时前",
      "share": "/login",
      "joinCount": 23,
      "isBroker": false,
      "messages": [
        {
          "id": 1286,
          "fromUserId": 89,
          "toUserId": 89,
          "sentTime": 1525406060441,
          "messageInfoType": "NEWS",
          "messageInfoId": 21,
          "context": "这些是你给我们",
          "isReply": false,
          "fromUser": {
            "id": 89,
            "nickname": "龙",
            "nicknameModified": true,
            "avatar": "http://test-1251500528.file.myqcloud.com/hzp/4D5B137B-A260-42CD-95EC-D1688866D8E5.jpg",
            "avatarModified": true,
            "gender": 1,
            "genderModified": true,
            "mobileNumber": "15279055744",
            "ageLabel": 4,
            "birthday": "04-13",
            "pushToken": "b52eca16d1957bd81c6741c9c4c51ef51abab5f7dc64342d320ee644e86e9418",
            "pf": "iOS",
            "career": "搬砖",
            "favorite": "音乐,摄影,撸猫,健身",
            "personalProfile": "我去拯救地球了...",
            "zmScore": 0,
            "zmAuth": false,
            "constellation": "白羊座",
            "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
            "zmAuthPushed": true,
            "infoCompleted": true,
            "flag": false,
            "privacy": 0,
            "forbidden": false,
            "virtual": false
          },
          "toUser": {
            "id": 89,
            "nickname": "龙",
            "nicknameModified": true,
            "avatar": "http://test-1251500528.file.myqcloud.com/hzp/4D5B137B-A260-42CD-95EC-D1688866D8E5.jpg",
            "avatarModified": true,
            "gender": 1,
            "genderModified": true,
            "mobileNumber": "15279055744",
            "ageLabel": 4,
            "birthday": "04-13",
            "pushToken": "b52eca16d1957bd81c6741c9c4c51ef51abab5f7dc64342d320ee644e86e9418",
            "pf": "iOS",
            "career": "搬砖",
            "favorite": "音乐,摄影,撸猫,健身",
            "personalProfile": "我去拯救地球了...",
            "zmScore": 0,
            "zmAuth": false,
            "constellation": "白羊座",
            "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
            "zmAuthPushed": true,
            "infoCompleted": true,
            "flag": false,
            "privacy": 0,
            "forbidden": false,
            "virtual": false
          },
          "reply": [
            {
              "id": 1289,
              "fromUserId": 96,
              "toUserId": 89,
              "sentTime": 1525410037420,
              "messageInfoType": "NEWS",
              "messageInfoId": 21,
              "context": "，1",
              "parentId": 1286,
              "isReply": false,
              "baseId": 1286,
              "fromUser": {
                "id": 96,
                "nickname": "皮卡丘",
                "nicknameModified": true,
                "avatar": "http://test-1251500528.file.myqcloud.com/hzp/11B8C33D-427B-426A-830C-02E555A77745.jpg",
                "avatarModified": true,
                "gender": 1,
                "genderModified": true,
                "mobileNumber": "15611869130",
                "ageLabel": 4,
                "birthday": "04-13",
                "pushToken": "61ce719babed944c0b7d243219cfe68a493268074792dffae84e6ea9a11ee97b",
                "pf": "iOS",
                "career": "猿",
                "personalProfile": "我去拯救地球了...",
                "zmScore": 0,
                "zmAuth": false,
                "constellation": "白羊座",
                "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
                "zmAuthPushed": true,
                "infoCompleted": true,
                "flag": false,
                "privacy": 1,
                "forbidden": false,
                "virtual": false
              },
              "toUser": {
                "id": 89,
                "nickname": "龙",
                "nicknameModified": true,
                "avatar": "http://test-1251500528.file.myqcloud.com/hzp/4D5B137B-A260-42CD-95EC-D1688866D8E5.jpg",
                "avatarModified": true,
                "gender": 1,
                "genderModified": true,
                "mobileNumber": "15279055744",
                "ageLabel": 4,
                "birthday": "04-13",
                "pushToken": "b52eca16d1957bd81c6741c9c4c51ef51abab5f7dc64342d320ee644e86e9418",
                "pf": "iOS",
                "career": "搬砖",
                "favorite": "音乐,摄影,撸猫,健身",
                "personalProfile": "我去拯救地球了...",
                "zmScore": 0,
                "zmAuth": false,
                "constellation": "白羊座",
                "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
                "zmAuthPushed": true,
                "infoCompleted": true,
                "flag": false,
                "privacy": 0,
                "forbidden": false,
                "virtual": false
              }
            }
          ],
          "replyCount": 7
        }
      ]
    }
  }
}
```

### 动态点赞
##### 接口:/CommunityController/liked
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|id|Long|动态|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}
```

### 取消动态点赞
##### 接口:/CommunityController/unliked
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|id|Long|动态|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}
```

### 被收藏列表
##### 接口:/UserController/passiveLikeList
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|page|Long|page|是|
|pageSize|Long|pageSize|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": []
}
```

### 过滤被封禁用户
##### 接口:/UserController/filterForbiddenUser
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|destUserIds|List<Long>|需要被过滤的用户id list|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": []
}
```

### 判断是否被拉黑
##### 接口:/UserController/hasLoggedIn
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|userId|Long|对方userId|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": {"blocked":true}
}
```
### 私信发短信
##### 接口:/PrivateMsgController/sendMessage
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|toUserId|Long|被评论人的的ID|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}
```
### 拉黑
##### 接口:/UserController/blockUser
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|blockUserId|Long|被拉黑人的Id|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}
```

### 取消拉黑
##### 接口:/ProfileController/unBlock
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|blockedUserId|Long|被拉黑人的Id|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}
```

### 删除评论
##### 接口:/ProfileController/removeMessage
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|messageId|Long|消息Id|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}
```

### 查询是否有未读消息
##### 接口:/UserController/hasNewMessages
##### 请求方式:GET
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|lastLikeTime|Long|最新收到的点赞或分享时间，没有传0|是|
|lastSentTime|Long|最新收到的评论时间，没有传0|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": true
}
```

### 喜欢/收藏出租
##### 接口:/HouseController/like
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|id|Long|房源id|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}
```

### 取消喜欢/收藏出租
##### 接口:/HouseController/unlike
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|id|Long|房源id|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}
```

### 喜欢/收藏求租
##### 接口:/HouseRequestController/like
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|id|Long|房源id|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}
```

### 取消喜欢/收藏求租
##### 接口:/HouseRequestController/unlike
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|id|Long|房源id|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}
```

### 喜欢/收藏列表
##### 接口:/UserController/likeList
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|type|String|HOUSE/HOUSE_REQUEST|是|
|page|int|>=1|否|
|pageSize|int|>=1|否|
##### 成功返回
##### 有房列表如下
```
{
  "ret": 200,
  "data": [
    {
      "id": 5,
      "rent": 67667,
      "readyTime": 1,
      "room": 2,
      "parlor": 1,
      "payment": "1,2,3",
      "rentType": "1,2,3",
      "communityId": 1064,
      "buildArea": 123,
      "cityId": 1,
      "areaId": 1139,
      "businessAreaId": 5803,
      "lon": 116.392535,
      "lat": 39.971349,
      "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzpd718c6ee-9db1-4967-833a-0ccbdc41d8fc.jpg",
      "status": 1,
      "createTime": 1513847453273,
      "nearbySubways": "236719,640931,823.0;236719,1102109,1089.0",
      "userId": 7,
      "pictureCount": 2,
      "communityName": "阳光丽景",
      "areaName": "西城",
      "businessAreaName": "马甸",
      "ip": "10.90.5.142",
      "hasWIFI": false,
      "hasFridge": false,
      "hasAirConditioning": true,
      "hasWasher": false,
      "hasToilet": true,
      "hasShower": false,
      "hasHeating": false,
      "hasGas": false,
      "hasWardrobe": true,
      "hasKitchen": false,
      "hasTV": false,
      "hasSofa": false,
      "hasBalcony": false,
      "hasElevator": false,
      "description": "用民工哦婆婆opp",
      "subwayName": "8号线,8号线",
      "user": {
        "id": 7,
        "nickname": "大冒险家1",
        "nicknameModified": true,
        "avatar": "http://test-1251500528.file.myqcloud.com/hzpcc46668d-64c2-4fc8-b466-6f304742465d.jpg",
        "avatarModified": true,
        "gender": 1,
        "genderModified": true,
        "mobileNumber": "18401657466",
        "ageLabel": 1,
        "birthday": "12-21",
        "pf": "android",
        "favorite": "null",
        "aliCredit": false
      },
      "liked": true
    }
  ]
}
```
##### 无房列表如下
```
{
  "ret": 200,
  "data": [
    {
      "id": 51,
      "description": "啦啦啦啦啦",
      "expectedLocation": "5803",
      "expectedLocations": "xxx xxx dddd gggg",
      "expectedTime": 2312312312312312300,
      "startRent": 1000,
      "endRent": 10000,
      "cityId": 1,
      "status": 2,
      "createTime": 1513390206979,
      "userId": 4,
      "user": {
        "id": 4,
        "nickname": "PAI4588523981",
        "nicknameModified": false,
        "avatar": "ooo",
        "avatarModified": true,
        "gender": 2,
        "genderModified": true,
        "mobileNumber": "18514030307",
        "ageLabel": 2,
        "birthday": "03-071",
        "pf": "iOS",
        "career": "xxx2",
        "favorite": "xxx1;xxx2",
        "personalProfile": "xxx1",
        "aliCredit": false
      },
      "liked": true
    }
  ]
}
```
### 评论
##### 接口:/ProfileController/comment
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|toUserId|Long||是|
|messageInfoType|String|评论类型 ACTIVITY,NEWS,HOUSE,HOUSE_REQUEST,GANG|是|
|messageInfoId|Long|评论类型ID|是|
|context|String|评论内容|是|
|parentId|Long|父消息ID只有二级|否|
|isReply|boolean|是否是回复|是|
|baseId|Long|回复谁就是谁的ID|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": ""
}
```

### 通知评论
##### 接口:ProfileController/messageByLoginUserId
##### 请求方式:GET
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|page|int|分页|是|
|pageSize|int|分页|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": [
    {
      "id": 44,
      "fromUserId": 7,
      "toUserId": 1,
      "sentTime": 1514346369419,
      "messageInfoType": "HOUSE",
      "messageInfoId": 7,
      "context": "KKK",
      "parentId": 35,
      "isReply": true,
      "baseId": 38,
      "fromUser": {
        "id": 7,
        "nickname": "Marry",
        "nicknameModified": true,
        "avatar": "http://test-1251500528.file.myqcloud.com/hzp/img/default_avatar.png",
        "avatarModified": true,
        "gender": 3,
        "genderModified": true,
        "mobileNumber": "13552416017",
        "ageLabel": 0,
        "pf": "android",
        "career": "\"科学家\"",
        "favorite": "美食,旅游,电影,摄影",
        "aliCredit": false,
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpeg"
      },
      "toUser": {
        "id": 1,
        "nickname": "奥特曼",
        "nicknameModified": true,
        "avatar": "http://test-1251500528.file.myqcloud.com/hzpa9bb293f-3b66-4363-9a72-e0193264549b.jpg",
        "avatarModified": true,
        "gender": 1,
        "genderModified": true,
        "mobileNumber": "18610211532",
        "ageLabel": 3,
        "birthday": "12-26",
        "pf": "android",
        "career": "\"科学家\"",
        "favorite": "工作,读书,逛街",
        "personalProfile": "我去拯救地球了...",
        "aliCredit": false,
        "constellation": "摩羯座",
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpeg"
      },
      "baseMessage": {
        "id": 38,
        "fromUserId": 1,
        "toUserId": 7,
        "sentTime": 1514344943234,
        "messageInfoType": "HOUSE",
        "messageInfoId": 7,
        "context": "咯默默图看了看可口可乐了看了看兔兔可口可乐了",
        "parentId": 35,
        "isReply": true,
        "baseId": 37,
        "fromUser": {
          "id": 1,
          "nickname": "奥特曼",
          "nicknameModified": true,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzpa9bb293f-3b66-4363-9a72-e0193264549b.jpg",
          "avatarModified": true,
          "gender": 1,
          "genderModified": true,
          "mobileNumber": "18610211532",
          "ageLabel": 3,
          "birthday": "12-26",
          "pf": "android",
          "career": "\"科学家\"",
          "favorite": "工作,读书,逛街",
          "personalProfile": "我去拯救地球了...",
          "aliCredit": false,
          "constellation": "摩羯座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpeg"
        },
        "toUser": {
          "id": 7,
          "nickname": "Marry",
          "nicknameModified": true,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzp/img/default_avatar.png",
          "avatarModified": true,
          "gender": 3,
          "genderModified": true,
          "mobileNumber": "13552416017",
          "ageLabel": 0,
          "pf": "android",
          "career": "\"科学家\"",
          "favorite": "美食,旅游,电影,摄影",
          "aliCredit": false,
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpeg"
        }
      }
    }
  ]
}
```


### 动态点赞
##### 接口:CommunityController/like
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|infoId|Long|分页|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}
```

### 动态分享
##### 接口:CommunityController/share
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|infoId|Long|分页|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}
```

### 通知列表-点赞/分享
##### 接口:UserController/getLikeNotifications
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|page|int|页数，1开始，默认1|否|
|pageSize|int|条数，默认20|否|
##### 成功返回值
```
{
  "ret": 200,
  "data": [
    {
      "id": 68,
      "userId": 5,
      "likedUserId": 1,
      "likeTime": 1514358596531,
      "likeInfoType": "ACTIVITY",
      "likeType": "SHARE",
      "likeInfoId": 1,
      "user": {
        "id": 5,
        "nickname": "PAI5287464902",
        "nicknameModified": false,
        "avatar": "http://test-1251500528.file.myqcloud.com/hzp/img/default_avatar.png",
        "avatarModified": false,
        "gender": 3,
        "genderModified": false,
        "mobileNumber": "18514030307",
        "ageLabel": 0,
        "pf": "iOS",
        "career": "\"科学家\"",
        "personalProfile": "我去拯救地球了...",
        "aliCredit": false,
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpeg"
      },
      "dynamic": {
        "id": 1,
        "infoId": 1,
        "content": "这里是动态1",
        "image": "http://prod-1251500528.file.myqcloud.com/m/img/index.png",
        "userId": 1,
        "likedCount": 0,
        "messageCount": 13,
        "forwardCount": 0,
        "infoType": "ACTIVITY",
        "createTime": 1514260874000
      }
    }
  ]
}
```

### 查看回复
##### 接口:/ProfileController/replyMessageByParent
##### 请求方式:GET
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|parentId|Long|父消息ID只有二级|否|
##### 成功返回值
```
{
  "ret": 200,
  "data": [
    {
      "id": 16,
      "fromUserId": 6,
      "toUserId": 6,
      "sentTime": 1514000469885,
      "messageInfoType": "HOUSE",
      "messageInfoId": 15,
      "context": "PKPM婆婆婆婆实际上jsjsjsjdjd实际上计算机",
      "parentId": 15,
      "isReply": false,
      "fromUser": {
        "id": 6,
        "nickname": "超人啊啊啊啊啊啊iiiuu",
        "nicknameModified": true,
        "avatar": "http://test-1251500528.file.myqcloud.com/hzp/BF42AEC0-0EBF-45F4-B590-AF7CBA0D4CE2.jpg",
        "avatarModified": true,
        "gender": 1,
        "genderModified": true,
        "mobileNumber": "15011350101",
        "ageLabel": 4,
        "birthday": "11-27",
        "pf": "iOS",
        "career": "神级天才",
        "favorite": "美食,电影",
        "personalProfile": "知世故，而不世故。",
        "aliCredit": false
      },
      "toUser": {
        "id": 6,
        "nickname": "超人啊啊啊啊啊啊iiiuu",
        "nicknameModified": true,
        "avatar": "http://test-1251500528.file.myqcloud.com/hzp/BF42AEC0-0EBF-45F4-B590-AF7CBA0D4CE2.jpg",
        "avatarModified": true,
        "gender": 1,
        "genderModified": true,
        "mobileNumber": "15011350101",
        "ageLabel": 4,
        "birthday": "11-27",
        "pf": "iOS",
        "career": "神级天才",
        "favorite": "美食,电影",
        "personalProfile": "知世故，而不世故。",
        "aliCredit": false
      }
    }
  ]
}
```

## 配置/第三方配置/数据

### 基础配置
##### 接口:/Application/config
##### 请求方式:GET
##### 接口参数
无
##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "loginReward": 35,
    "inviteAlertReward": 26,
    "pushCertificateId": 8749,
    "publishRequest": 50,
    "accountType": 25685,
    "invited": 2,
    "scanCodeShareSwitch": true,
    "inviteAlertLimit": 10,
    "inviteAlertUserCount": 3,
    "bannerRedirectUrl": "yajinxian",
    "imSdkAppId": "1400086951",
    "publishHouse": 30,
    "bannerPictureUrl": "http://prod-1251500528.file.myqcloud.com/resource/biyeji-banner.jpg",
    "rewardSwitch": true,
    "authentication": 10
    "summerRedEnvelopes" : true
  }
}
```

### 支付接口
##### 接口:/WeChatController/unifiedOrder
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|orderId|Long|订单ID|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "returnCode": "SUCCESS",
    "returnMsg": "OK",
    "appId": "wxa91cf5dabed99eec",
    "mchId": "1496204652",
    "nonceStr": "UMDThgdJiTCDVGBbAifTfCdRdWfEGeOW",
    "sign": "C86C5D39A46A0180BB23812CCB20EE82",
    "resultCode": "SUCCESS",
    "tradeType": "APP",
    "prepayId": "wx201801101106566e38d1d1850410318755",
    "packageValue:" "Sign=WXPay",
    "timestamp": "1515553624"
  }
}
```

### 查询支付结果接口
##### 接口:/WeChatController/queryOrder
##### 请求方式:GET
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|orderId|Long|订单ID|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "returnCode": "SUCCESS",
    "returnMsg": "OK",
    "appId": "wxa91cf5dabed99eec",
    "mchId": "1496204652",
    "nonceStr": "VFMFqVVyLgjODFUm",
    "sign": "4A8B85F0E5EAE0AF7787854B38BB9043",
    "resultCode": "SUCCESS",
    "openid": "oTHJ80Sgi7TRA_ajjbY7rfmvhoGc",
    "tradeType": "APP",
    "bankType": "ABC_DEBIT",
    "totalFee": 1,
    "cashFee": 1,
    "transactionId": "4200000087201801090958590981",
    "outTradeNo": "97626D12-",
    "attach": "",
    "timeEnd": "20180109125115",
    "tradeState": "SUCCESS"
  }
}
```

### 腾讯云图片上传配置
##### 接口:/Application/qcloudCosConfig
##### 请求方式:GET
##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "bucket": "test",
    "filepath": "hzp",
    "appid": "1251500528",
    "sign": "eqwPb0nyayQF11vkSWl2Cr55aOVhPTEyNTE1MDA1MjgmYj10ZXN0Jms9QUtJRE93dlBONDhQYmxoME0ybHFGc0FaREF3eFBBNlNwOVhVJnI9NzU1MDAzOTgzODgyOTI1MDIwMyZlPTE1MTM2NzM3MjMmdD0xNTEzNjczMTIzJmY9",
    "region": "tj"
  }
}
```

### 阿里api签名
##### 接口:/UserController/aliSignInfo
##### 请求方式:GET
##### 接口参数
##### 成功返回值
```
{
  "ret": 200,
  "data": "apiname=com.alipay.account.auth&app_id=2018010201514439&app_name=mc&auth_type=AUTHACCOUNT&biz_type=openservice&method=zhima.credit.score.get&pid=2088921298689521&product_id=APP_FAST_LOGIN&scope=auth_zhima&sign_type=RSA2&target_id=dded461b-d6cc-45ca-b47d-1b1f6ce71b1a8&sign=GXgrj%2BaSpr4lcAmHhb4w2ijkCQfFLXyVxfixw6YWpM04S0OmOqdIH7fcVJ%2Bjq72rAroMgRbXzKbuFvRFfxqBMYxI1pvsBGSFnT4BzW2qCFFDSz90R%2F4Bbo3%2BCVQJeY1EohrhxwM8%2BSNbMPDbJjcBF50W5pz47rHojjLiH%2FghVSA1u9Vv76GQ71ALttK6NZLCK50olS6xR9tpk%2FGyL4v6THG4dMPuGJWYQbh5vIDlNIs%2BkzqRoQoRJQOcBJlIti2mCEcUHylLDc1jIVlJpIx8mTmoY2a3Y1GgFfqgr0duZKmRQbmAg0xKhAIgT1F4ig8uNIJCmTncbHsGfy39yQA%2FZg%3D%3D"
}
```

### 是否做过芝麻认证
##### 接口:/UserController/getZmScore
##### 请求方式:GET
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|authCode|String|authCode|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": true
}
```

## 地域
### 新版城市列表
##### 接口:/LocationController/cities
##### 请求方式:GET
##### 接口参数
无
##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "hot": [
      {
        "id": 1,
        "name": "北京",
        "listName": "beijing",
        "open": 1,
        "hot": true
      }
    ],
    "cities": {
      "A": [],
      "B": [
        {
          "id": 1,
          "name": "北京",
          "listName": "beijing",
          "open": 1,
          "hot": true
        }
      ]
    }
  }
}
```

### 省份列表
##### 接口:/LocationController/provinces
##### 请求方式:GET
##### 接口参数
无
##### 成功返回值
```
{
  "ret": 200,
  "data": [
    {
      "id": 28,
      "name": "北京",
      "initial": "B",
      "open": true,
      "sortOrder": 1
    }
  ]
}
```

### 城市列表
##### 接口:/LocationController/getCitiesByProvinceId
##### 请求方式:GET
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|provinceId|Long|省份id|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": [
    {
      "id": 3,
      "name": "广州",
      "listName": "guangzhou",
      "open": 1,
      "hot": true,
      "provinceId": 3
    }
  ]
}
```

### 获取城市
##### 接口:/LocationController/openCities
##### 请求方式:GET
##### 成功返回值
```
{
  "ret": 200,
  "data": [
    {
      "id": 1,
      "name": "北京",
      "listName": "bj",
      "open": 1,
      "setOpen": true,
      "setId": true,
      "setName": true,
      "setListName": true
    }
  ]
}
```

### 获取区域
##### 接口:/ProfileController/areas
##### 请求方式:GET

|参数名|类型|描述|是否必须|
|---|---|---|---|
|cityId|Long|城市ID|是|

##### 成功返回值

```
{
  "ret": 200,
  "data": [
    {
      "id": 1138,
      "cityId": 1,
      "name": "东城",
      "sort": 0,
      "setId": true,
      "setCityId": true,
      "setName": true,
      "setSort": true
    }
  ]
}
```

### 获取商圈
##### 接口:/ProfileController/businessAreas
##### 请求方式:GET

|参数名|类型|描述|是否必须|
|---|---|---|---|
|areaId|Long|区域ID|是|

##### 成功返回值

```
{
  "ret": 200,
  "data": [
    {
      "id": 5817,
      "cityId": 1,
      "areaId": 1138,
      "name": "安定门",
      "pinyin": "A"
    }
  ]
}
```

### 获取地铁线
##### 接口:/ProfileController/subways
##### 请求方式:GET
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|

##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}
```

### 获取地铁站
##### 接口:/ProfileController/subwayStations
##### 请求方式:GET
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|subwayId|Long|地铁线ID|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": []
}
```

### 模糊搜索小区
##### 接口:/ProfileController/communities
##### 请求方式:GET
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|cityId|Long|城市ID|是|
|communityName|String|名称|是|
|lat|Double|纬度|否|
|lon|Double|经度|否|
##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "communitys": [
      {
        "id": 2080814,
        "name": "望京金茂府",
        "listName": "wangjingjinmaofu",
        "ganjiId": 219397,
        "ajkId": 511075,
        "cityId": 1,
        "areaId": 1142,
        "businessAreaId": 6012,
        "dsCityId": 1,
        "dsAreaId": 1142,
        "dsBusinessAreaId": 6012,
        "letter": "w",
        "lon": 116.467223,
        "lat": 40.025041,
        "sosoLon": 116.4606050648,
        "sosoLat": 40.0193652602,
        "address": "广顺北大街",
        "sort": 0,
        "type": 0,
        "state": 1,
        "buildingType": "小高层",
        "builtDate": 2014,
        "plotRatio": 2.3,
        "greeningRate": 0.3,
        "developer": "北京方兴融创房地产开发有限公司",
        "avgPrice": 12.9577,
        "pmc": "中化金茂物业管理(北京)有限公司",
        "pmf": 0.7,
        "url": "http://prod-1251500528.image.myqcloud.com/3ddb355ff02238d3a32b490be59d5367.jpg",
        "nearbySubways": "677835,1101621,521.0;677835,1101620,1126.0",
        "areaName": "朝阳",
        "businessAreaName": "来广营",
        "onlineSecondHandHouseCount": 14,
        "onlineRentHouseCount": 1,
        "recentVppv": 0,
        "vppvTime": 0
      }
    ],
    "count": 27,
    "showCount": 27,
  }
}
```

## 用户
### 获取登录人信息
##### 接口:/UserController/me
##### 请求方式:GET
|参数名|类型|描述|是否必须|
|---|---|---|---|
|token|String|token|是|

##### 成功返回值
```
{
  ret: 200,
  data: {
    "id": 4,
    "nickname": "PAI4588523981",
    "nicknameModified": false,
    "avatar": "xxx",
    "avatarModified": false,
    "gender": 0,
    "genderModified": false,
    "mobileNumber": "18514030307",
    "ageLabel": 0,
    "birthday": 0,
    "pushToken": "xxx",
    "pf": "iOS",
    "career": "xxx",
    "favorite": "xxx",
    "personalProfile": "xxx",
    "aliCredit": false,
    "token": "2fAHedgJvxoprJqq63686",
    "IMSignature": "eJxlj01Pg0AURff8CsK2RocpU6WJi6Y0ijIBLFbDhiDzqC9VGIahHxr-uxWbSOL6nHtv7qdhmqaVBMvzvCjqrtKZPkiwzKlpEevsD0qJIst1NlbiH4S9RAVZXmpQPbQZY5SQoYMCKo0lngxngFqxyfr#####36xzDDJ2xdhQwXUP#####eJx7scehvw5yW8vpEhHJb93JrB-aL2QHlxeNE8c-KD50NXWiXjsryM73OhZAmWsRJpGLyoYwQ2NnUWH3t0uXb16aY3dcv7WzK4Hkxrf4XTGHjOXTcjlgG5BtVhXvUDJUaHEJT#####PjS-jGz5qW-E_",
    "isAdministrators": true,
    "apartmentName": "自如公寓",
    apartmentCityId: 1,
    reason: "aaa",
    "status": 1,//(0 普通用户没有提交过入驻申请 1 待审核 2 审核通过 3 审核不通过)
    "invitationCode": "xxx",
    "invited": false,
    "userProvincesId":1,
    "userProvincesName":"河北省",
    "userCityId":1,
    "userCityName":"张家口市",
    "schoolId":1
    "schoolName":"d"
  }
}
```

### 用户删除推荐给他的用户
##### 接口:/ProfileController/excludeCommend
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|userId|Long|删除推荐用户的ID|是|
|type|String|类型|是，HOUSE、HOUSE_REQUEST|

##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}
```

### 小程序登录注册接口
##### 接口:/UserController/register
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|code|String|授权code|是|
|nickname|String|昵称|是|
|sex|Integer|性别|是|
|headimgurl|String|头像|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "id": 4,
    "nickname": "PAI4588523981",
    "nicknameModified": false,
    "avatar": "xxx",
    "avatarModified": false,
    "gender": 0,
    "genderModified": false,
    "mobileNumber": "18514030307",
    "ageLabel": 0,
    "birthday": 0,
    "pushToken": "xxx",
    "pf": "iOS",
    "career": "xxx",
    "favorite": "xxx",
    "personalProfile": "xxx",
    "aliCredit": false,
    "token": "2fAHedgJvxoprJqq63686",
    "sessionKey": "abc",
    "invitationCode": "xxx",
    "invited": false
  }
}
```

### 隐私设置
##### 接口:/UserController/privacySettings
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|privacy|int|1不空开 0 公开|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}
```

### 年龄标签列表
##### 接口:/EnumController/ageLabel
##### 请求方式:GET
##### 成功返回值
```
{
  "ret": 200,
  "data": [
    {
      "value": 1,
      "name": "80前"
    },
    {
      "value": 2,
      "name": "80后"
    },
    {
      "value": 3,
      "name": "85后"
    },
    {
      "value": 4,
      "name": "90后"
    },
    {
      "value": 5,
      "name": "95后"
    }
  ]
}
```

### 更新pushToken
##### 接口:/UserController/updatePushToken
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|pushToken|String|pushToken|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}
```

### 微信注册/登录
##### 接口:/UserController/loginByWeChat
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|code|字符串|第三方登录凭证|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "id": 4,
    "nickname": "PAI4588523981",
    "nicknameModified": false,
    "avatar": "xxx",
    "avatarModified": false,
    "gender": 0,
    "genderModified": false,
    "mobileNumber": "18514030307",
    "ageLabel": 0,
    "birthday": 0,
    "pushToken": "xxx",
    "pf": "iOS",
    "career": "xxx",
    "favorite": "xxx",
    "personalProfile": "xxx",
    "aliCredit": false,
    "token": "2fAHedgJvxoprJqq63686",
    "IMSignature": "eJxlj01Pg0AURff8CsK2RocpU6WJi6Y0ijIBLFbDhiDzqC9VGIahHxr-uxWbSOL6nHtv7qdhmqaVBMvzvCjqrtKZPkiwzKlpEevsD0qJIst1NlbiH4S9RAVZXmpQPbQZY5SQoYMCKo0lngxngFqxyfr#####36xzDDJ2xdhQwXUP#####eJx7scehvw5yW8vpEhHJb93JrB-aL2QHlxeNE8c-KD50NXWiXjsryM73OhZAmWsRJpGLyoYwQ2NnUWH3t0uXb16aY3dcv7WzK4Hkxrf4XTGHjOXTcjlgG5BtVhXvUDJUaHEJT#####PjS-jGz5qW-E_",
    "isAdministrators": true,
    "apartmentName": "自如公寓",
    apartmentCityId: 1,
    reason: "aaa",
    "status": 1,//(0 普通用户没有提交过入驻申请 1 待审核 2 审核通过 3 审核不通过)
    "invitationCode": "xxx",
    "invited": false
  }
}
```

### 获取登录验证码
##### 接口:/UserController/generateCode
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|mobileNumber|字符串|手机号码|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}
```

### 手机号码注册/登录
##### 接口:/UserController/loginByMobile
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|code|字符串|第三方登录凭证|是|
|mobileNumber|字符串|手机号码|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "id": 4,
    "nickname": "PAI4588523981",
    "nicknameModified": false,
    "avatar": "xxx",
    "avatarModified": false,
    "gender": 0,
    "genderModified": false,
    "mobileNumber": "18514030307",
    "ageLabel": 0,
    "birthday": 0,
    "pushToken": "xxx",
    "pf": "iOS",
    "career": "xxx",
    "favorite": "xxx",
    "personalProfile": "xxx",
    "aliCredit": false,
    "token": "2fAHedgJvxoprJqq63686",
    "IMSignature": "eJxlj01Pg0AURff8CsK2RocpU6WJi6Y0ijIBLFbDhiDzqC9VGIahHxr-uxWbSOL6nHtv7qdhmqaVBMvzvCjqrtKZPkiwzKlpEevsD0qJIst1NlbiH4S9RAVZXmpQPbQZY5SQoYMCKo0lngxngFqxyfr#####36xzDDJ2xdhQwXUP#####eJx7scehvw5yW8vpEhHJb93JrB-aL2QHlxeNE8c-KD50NXWiXjsryM73OhZAmWsRJpGLyoYwQ2NnUWH3t0uXb16aY3dcv7WzK4Hkxrf4XTGHjOXTcjlgG5BtVhXvUDJUaHEJT#####PjS-jGz5qW-E_",
    "invitationCode": "xxx",
    "invited": false
  }
}
```

### 注销（退出登录）
##### 接口:/UserController/logout
##### 请求方式:POST
##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}
```

### 举报
##### 接口:UserController/report
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|userId|Long|被举报的用户id|是|
|reason|Integer|1-中介，2-广告、推销，3-不友善行为，4-其他|否|
##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}
```

### 绑定手机号码
##### 接口:/UserController/bindMobile
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|mobileNumber|String|手机号码|是|
|code|String|验证码|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": true
}
```

### 根据用户ID获取用户信息
##### 接口:/UserController/findById
##### 请求方式:GET
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|userId|Long|用户ID|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": {
    用户model
  }
}
```

### 更新个人信息
##### 接口:/UserController/updateProfile
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|avatar|String|头像|否|
|nickname|String|昵称|否|
|gender|Integer|性别|否|
|ageLabel|Integer|年龄标签|否|
|birthDay|String|生日|否|
|personalProfile|String|个人介绍|否|
|career|String|职业|否|
|favorite|String|个人爱好|否|
|background|String|个人爱好|否|
##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}
```

### 我的发布
##### 接口:/UserController/myPublication
##### 请求方式:GET
##### 成功返回值
```
{
  "ret": 200,
  "data": [
    {
      "id": 4,
      "rent": 5000,
      "readyTime": 1,
      "room": 1,
      "parlor": 0,
      "payment": "2,3",
      "rentType": "2",
      "communityId": 2185691,
      "buildArea": 20,
      "cityId": 1,
      "areaId": 1139,
      "businessAreaId": 5801,
      "lon": 116.384696,
      "lat": 39.969346,
      "status": 1,
      "createTime": 1513847269591,
      "userId": 9,
      "pictureCount": 3,
      "communityName": "新风街1号院",
      "areaName": "西城",
      "businessAreaName": "德胜门",
      "updateTime": 0,
      "ip": "10.90.5.195",
      "hasWIFI": false,
      "hasFridge": false,
      "hasAirConditioning": true,
      "hasWasher": false,
      "hasToilet": false,
      "hasShower": false,
      "hasHeating": false,
      "hasGas": false,
      "hasWardrobe": false,
      "hasKitchen": false,
      "hasTV": false,
      "hasSofa": false,
      "hasBalcony": false,
      "hasElevator": false,
      "description": "Eeeeeeeeeeeeeeeeeeeeeeee",
      "subwayName": "",
      "outTime": "",
      "signedTime": "",
      "type": "house",
      promotions: [
        {
          id: 3,
          term: 3,
          bonus: 50,
          description: "超出十五天完成在线签约，奖50元现金！",
          active: true,
          tips: "您已完成签约，根据《趣签约计划》 您可以获取50元",
          obtainBonusTips: "关注公众号“合租趣味”；发送您交易绑定的手机号码，以及交易订单页面截图，2个工作日内完成打款。",
          day: 0
        }
      ]
      "contractStatus" :  4   交易订单状态  1已签订 4已关闭
      "authenticationStatus" : 2   身份验证状态 0未验证 1 验证成功 2 验证失败
      "closeReason" : "身份信息校验失败2次，交易关闭"
      "promotionStatus" : 0     1 发过钱 2 违规 3 点击已经领取
      "bonus" : 50 奖励金额
	  "contractType" :2    1线上 2线下有房 3线下无房
	  "isNew" : true
    },
    {
      "id": 60,
      "description": "上市啦咔咔啦啦啦啦啦啦啦快上课上课上课上课时",
      "expectedLocation": "1185",
      "expectedLocations": "崇文周边",
      "expectedAreas": "1140",
      "expectedAreaNames": "崇文",
      "expectedTime": 1,
      "startRent": 0,
      "endRent": 5000,
      "cityId": 1,
      "status": 2,
      "createTime": 1513926959165,
      "userId": 9,
      "type": "houseRequest"
	  "isNew" : true
    }
  ]
}
```

### 看过我的
##### 接口:ProfileController/seen
##### 请求方式:GET
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|userId|Long|用户Id|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": [
    {
      "id": 9,
      "nickname": "PAI4564064851",
      "nicknameModified": false,
      "avatarModified": false,
      "gender": 0,
      "genderModified": false,
      "mobileNumber": "18645251609",
      "ageLabel": 0,
      "pf": "iOS",
      "favorite": "工作,美食,摄影",
      "aliCredit": false,
      "isPublishHouse": true,
      "isPublishHouseRequest": true
    }
  ]
}
```

### 个人主页
##### 接口:UserController/personalHomePage
##### 请求方式:GET
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|userId|Long|用户Id|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "user": {
      "id": 7,
      "nickname": "大冒险家哈哈哈吃好喝好哈1",
      "nicknameModified": true,
      "avatar": "http://test-1251500528.file.myqcloud.com/hzpcc46668d-64c2-4fc8-b466-6f304742465d.jpg",
      "avatarModified": true,
      "gender": 1,
      "genderModified": true,
      "mobileNumber": "18401657466",
      "ageLabel": 1,
      "birthday": "12-21",
      "pf": "android",
      "career": "\"科鞥4米公学家\"",
      "favorite": "旅游,音乐",
      "aliCredit": false,
      "constellation": "射手座"
    },
    "houses":[
    {
      "id": 5,
      "rent": 67667,
      "readyTime": 1,
      "room": 2,
      "parlor": 1,
      "payment": "1,2,3",
      "rentType": "1,2,3",
      "communityId": 1064,
      "buildArea": 123,
      "cityId": 1,
      "areaId": 1139,
      "businessAreaId": 5803,
      "lon": 116.392535,
      "lat": 39.971349,
      "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzpd718c6ee-9db1-4967-833a-0ccbdc41d8fc.jpg",
      "status": 1,
      "createTime": 1513847453273,
      "nearbySubways": "236719,640931,823.0;236719,1102109,1089.0",
      "userId": 7,
      "pictureCount": 2,
      "communityName": "阳光丽景",
      "areaName": "西城",
      "businessAreaName": "马甸",
      "ip": "10.90.5.142",
      "hasWIFI": false,
      "hasFridge": false,
      "hasAirConditioning": true,
      "hasWasher": false,
      "hasToilet": true,
      "hasShower": false,
      "hasHeating": false,
      "hasGas": false,
      "hasWardrobe": true,
      "hasKitchen": false,
      "hasTV": false,
      "hasSofa": false,
      "hasBalcony": false,
      "hasElevator": false,
      "description": "用民工哦婆婆opp",
      "subwayName": "8号线,8号线"
    }
    ]
    "house": {
      "id": 5,
      "rent": 67667,
      "readyTime": 1,
      "room": 2,
      "parlor": 1,
      "payment": "1,2,3",
      "rentType": "1,2,3",
      "communityId": 1064,
      "buildArea": 123,
      "cityId": 1,
      "areaId": 1139,
      "businessAreaId": 5803,
      "lon": 116.392535,
      "lat": 39.971349,
      "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzpd718c6ee-9db1-4967-833a-0ccbdc41d8fc.jpg",
      "status": 1,
      "createTime": 1513847453273,
      "nearbySubways": "236719,640931,823.0;236719,1102109,1089.0",
      "userId": 7,
      "pictureCount": 2,
      "communityName": "阳光丽景",
      "areaName": "西城",
      "businessAreaName": "马甸",
      "ip": "10.90.5.142",
      "hasWIFI": false,
      "hasFridge": false,
      "hasAirConditioning": true,
      "hasWasher": false,
      "hasToilet": true,
      "hasShower": false,
      "hasHeating": false,
      "hasGas": false,
      "hasWardrobe": true,
      "hasKitchen": false,
      "hasTV": false,
      "hasSofa": false,
      "hasBalcony": false,
      "hasElevator": false,
      "description": "用民工哦婆婆opp",
      "subwayName": "8号线,8号线"
    },
    "houseRequest": {
      "id": 66,
      "description": "他知我者谓我心忧中央音乐学院天助自助者呜呜呜呜呜呜呜呜了我",
      "expectedLocation": "5149",
      "expectedLocations": "菜市口",
      "expectedAreas": "1141",
      "expectedAreaNames": "宣武",
      "expectedTime": 1514044800000,
      "startRent": 800,
      "endRent": 4500,
      "cityId": 1,
      "status": 2,
      "createTime": 1513997509330,
      "userId": 7,
      "updateTime": 1513997509330
    },
    "seen": {
      "gender": "1,1,1,1,",
      "seenCount": "4",
      "avatar": "121212,null,http://test-1251500528.file.myqcloud.com/hzp4934a5e2-0303-4c2f-b813-94c11f208104.jpg,http://test-1251500528.file.myqcloud.com/hzpe667c904-eb6f-4299-ab12-1159d1fa514b.jpg,"
    },
    "dynamicProfiles": [
      {
        "id": 29,
        "createTime": 1514184162756,
        "dynamicType": "PUBLISH_HOUSE",
        "content": "第一次发布房源",
        "userId": 7
      }
    ],
    "conformExpectedLocation": false,
    "matchExpectedLocation": [],
    "matchDegree": 0,
    "conformHouseCount": 0,
    "matchFavorite": [],
    "conformPublishHouse": false,
    "loginUserIsPublishHouse":false,
    "loginUserIsPublishHouseRequest":false

  }
}
```

### 离线时看过我的用户（杀掉进程到重新启动这段时间）
##### 接口:ProfileController/seeMe
##### 请求方式:GET
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|startTime|double|杀掉进程时候的时间|是|
|endTime|double|启动应用的时间|是|
```
{
  "ret": 200,
  "data": 0
}
```

##房源&出租
### 出租列表
##### 接口:/chuzu|/chuzu/axxxbxxxcxxxuxxx?page=...
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|a|+数字|年龄标签(年龄复选的话例如a123)|否|
|b|+数字|区域id|否
|c|+数字|商圈id|否|
|d|+数字|付款方式|否|
|e|+数字|性别|否|
|q|+0/1|租金升序/降序|否|
|r|+0/1|发布时间升序/降序|否|
|u|+数字|小区id|否|
|page|数字|页数，从1开始，默认1|否|
|startRent|double|最小租金|否|
|endRent|double|最大租金|否|
|startPublishTime|long|最小发布时间的时间戳|否|
|endPublishTime|long|最大发布时间的时间戳|否|
|keywords|String|关键字|否|
|f|+数字|地铁线id|否|
|g|+数字|地铁站id|否|
|sortType|数字|1按距离由近及远|否|
|point|坐标|40.041092,116.319671|否|
|i|+数字|附近距离区间(1:1公里内 2:3公里内 3:5公里内)|否|
|j|+数字|出租类型(1:整租 2:合租)|否|
|k|+数字|居室(开间 9)|否|
|isAdministrators|int|房屋来源(1个人 2公寓)|否|
|forMiss|boolean|女性专区传true|是|
成功返回值
```
{
  "ret": 200,
  "data": {
    "count": 2,
    "showCount": 2,
    "houses": [
      {
        "id": 3,
        "rent": 1500,
        "readyTime": 1513409358000,
        "room": 1,
        "parlor": 1,
        "payment": 1,
        "rentType": "1",
        "communityId": 6280,
        "buildArea": 20,
        "cityId": 1,
        "areaId": 1139,
        "businessAreaId": 5803,
        "lon": 116.383373,
        "lat": 39.967424,
        "listImageUrl": "xxx",
        "status": 1,
        "createTime": 1513409978018,
        "userId": 4,
        "pictureCount": 2,
        "communityName": "新风南里",
        "areaName": "西城",
        "businessAreaName": "马甸",
        "updateTime": 1513409358000,
        "ip": "127.0.0.1",
        "hasWIFI": false,
        "hasFridge": false,
        "hasAirConditioning": false,
        "hasWasher": false,
        "hasToilet": false,
        "hasShower": false,
        "hasHeating": false,
        "hasGas": false,
        "hasWardrobe": false,
        "hasKitchen": false,
        "hasTV": false,
        "hasSofa": false,
        "hasBalcony": false,
        "hasElevator": false,
        "description": "xxxxx",
        "user": {
          "id": 4,
          "nickname": "PAI4588523981",
          "nicknameModified": false,
          "avatar": "xxx",
          "avatarModified": false,
          "gender": 0,
          "genderModified": false,
          "mobileNumber": "18514030307",
          "ageLabel": 0,
          "birthday": 0,
          "pf": "iOS",
          "career": "xxx",
          "favorite": "xxx",
          "personalProfile": "xxx",
          "aliCredit": false
        },
        "liked": false
		redSwitch: true
      }
    ],
    "houseRequestUsers": [
      {
        "id": 4,
        "nickname": "PAI4588523981",
        "nicknameModified": false,
        "avatar": "xxx",
        "avatarModified": false,
        "gender": 0,
        "genderModified": false,
        "mobileNumber": "18514030307",
        "ageLabel": 0,
        "birthday": 0,
        "pf": "iOS",
        "career": "xxx",
        "favorite": "xxx",
        "personalProfile": "xxx",
        "aliCredit": false
      }
    ]
  }
}
```

### 求租列表
##### 接口:/qiuzu|/qiuzu/axxxbxxxcxxxuxxx?page=...
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|a|+数字|年龄标签|否|
|b|+数字|区域id|否
|c|+数字|商圈id|否|
|e|数字|性别|否|
|r|+0/1|发布时间升序/降序|否|
|page|数字|页数，从1开始，默认1|否|
|startRent|double|最小租金|否|
|endRent|double|最大租金|否|
|startPublishTime|long|最小发布时间的时间戳|否|
|endPublishTime|long|最大发布时间的时间戳|否|
|keywords|String|关键字|否|
|forMiss|boolean|女性专区传true|是|
成功返回值
```
{
  "ret": 200,
  "data": {
    "count": 51,
    "showCount": 51,
    "houseRequests": [
      {
        "id": 4,
        "description": "啦啦啦啦啦",
        "expectedLocation": "5803",
        "expectedLocations": "xxx xxx dddd gggg",
        "expectedTime": 2312312312312312300,
        "cityId": 1,
        "status": 2,
        "createTime": 1513390173122,
        "userId": 4,
        "user": {
          "id": 4,
          "nickname": "PAI4588523981",
          "nicknameModified": false,
          "avatar": "xxx",
          "avatarModified": false,
          "gender": 0,
          "genderModified": false,
          "mobileNumber": "18514030307",
          "ageLabel": 0,
          "birthday": 0,
          "pf": "iOS",
          "career": "xxx",
          "favorite": "xxx",
          "personalProfile": "xxx",
          "aliCredit": false
        },
        "liked": false
		redSwitch: true
      }
    ],
    "users": [
      {
        "id": 1,
        "nickname": "1111",
        "nicknameModified": false,
        "avatar": "xxx",
        "avatarModified": false,
        "gender": 0,
        "genderModified": false,
        "ageLabel": 85,
        "birthday": 0,
        "pushToken": "xxx",
        "career": "xxx",
        "favorite": "xxx",
        "personalProfile": "xxx",
        "aliCredit": true
      }
    ]
  }
}
```

### 有房发布&更新
##### 接口:/HouseController/publishOrUpdate
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|id|Long|id|否|
|rent|Double|租金|是|
|readyTime|Long|入住时间|是|
|room|Integer|室|是|
|parlor|Integer|厅|是|
|payment|String|支付方式 逗号隔开|是|
|rentType|String|出租类型 逗号隔开|是|
|communityId|Long|小区Id|是|
|buildArea|Double|面积|是|
|cityId|Long|城市ID|是|
|areaId|Long|区域ID|是|
|images|String|图片url逗号分隔|是|
|listImageUrl|String|展示第一张图片|是|
|hasWIFI|boolean|wifi|否|
|hasFridge|boolean|冰箱|否|
|hasAirConditioning|boolean|空调|否|
|hasWasher|boolean|洗衣机|否|
|hasToilet|boolean|独立卫生间|否|
|hasShower|boolean|淋浴|否|
|hasGas|boolean|燃气|否|
|hasWardrobe|boolean|衣柜|否|
|hasKitchen|boolean|厨房|否|
|hasTV|boolean|电视|否|
|hasSofa|boolean|沙发|否|
|hasBalcony|boolean|阳台|否|
|hasElevator|boolean|电梯|否|
|hasHeating|boolean|暖气|否|
|description|boolean|介绍|否|
|phone|String|手机号|是|
|code|String|验证码|是|
|favorite|String|喜好|否|
|identity|int|1 我是房东 2 我要转租 3 我要合租|否|
|toiletCount|int|厕所个数|否|
|contractPlan|boolean|是否参与去签约计划|否|
|forMiss|boolean|true-仅展示给女性，false-不限，当前用户为女性是必传|否|
|requirement|String|出租需求|否|
|userProvincesId|Long|家乡省ID|否|
|userProvincesName|String|家乡省名称|否|
|userCityId|Long|家乡城市Id|否|
|userCityName|Long|家乡城市名称|否|
|schoolId|Long|学校Id|否|
|schoolName|String|学校名称|否|

##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "house": {
      "id": 2,
      "rent": 2345,
      "readyTime": 1513320419764,
      "room": 1,
      "parlor": 1,
      "payment": "1,2,3",
      "rentType": "1,2,3",
      "communityId": 6280,
      "buildArea": 30,
      "cityId": 1,
      "areaId": 1139,
      "businessAreaId": 5803,
      "lon": 116.383373,
      "lat": 39.967424,
      "status": 1,
      "createTime": 1513333817291,
      "userId": 5,
      "pictureCount": 2,
      "communityName": "新风南里",
      "areaName": "西城",
      "businessAreaName": "马甸",
      "updateTime": 1513580209224,
      "ip": "0:0:0:0:0:0:0:1",
      "hasWIFI": true,
      "hasFridge": false,
      "hasAirConditioning": false,
      "hasWasher": false,
      "hasToilet": false,
      "hasShower": false,
      "hasHeating": false,
      "hasGas": false,
      "hasWardrobe": false,
      "hasKitchen": false,
      "hasTV": false,
      "hasSofa": false,
      "hasBalcony": false,
      "hasElevator": false,
      "description": "有花堪折直须折，待到无花空折枝.。。33",
      "isApartment": "true"
    },
    "conformHouseRequestCount": 0,
    "image": "xxx",
    "reward": true
  }
}
```

### 无房发布&更新
##### 接口:/HouseRequestController/publishOrUpdate
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|id|Long|id|否|
|expectedLocation|String|期望位置ID 空格隔开|是|
|expectedTime|Long|期望入住时间|是|
|startRent|Double|租金开始价格|是|
|endRent|Double|租金结束价格|是|
|cityId|Long|城市ID|是|
|description|boolean|介绍|否|
|favorite|String|喜好|否|
|phone|String|电话|是|
|code|String|验证码|是|
|expectedSubwayStationId|String|期望地铁站 空格隔开|否|
|expectedSubwayId|String|对应地铁站的地铁线ID 空格隔开|否|
|forMiss|boolean|true-仅展示给女性，false-不限，当前用户为女性是必传|否|
|requirement|String|出租需求|否|
|userProvincesId|Long|家乡省ID|否|
|userProvincesName|String|家乡省名称|否|
|userCityId|Long|家乡城市Id|否|
|userCityName|Long|家乡城市名称|否|
|schoolId|Long|学校Id|否|
|schoolName|String|学校名称|否|
##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "houseRequest": {
        "id": 55,
        "description": "啦啦啦啦啦",
        "expectedLocation": "1194 1198",
        "expectedLocations": "三元桥 三里屯",
        "expectedAreaNames": "朝阳 朝阳",
        "expectedTime": 2312312312312312312,
        "startRent": 2000,
        "endRent": 20000,
        "cityId": 1,
        "status": 2,
        "createTime": 1513583840900,
    	"userId": 5
    },
    "conformHouseCount": 0,
    "image": "xxx",
    "reward": true
  }
}
```

### 有房详情
##### 接口:/HouseController/findById
##### 请求方式:GET

|参数名|类型|描述|是否必须|
|---|---|---|---|
|id|Long|id|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "image": [
      {
        "id": 17,
        "houseId": 2,
        "url": "images",
        "createTime": 1513580209000
      },
      {
        "id": 18,
        "houseId": 2,
        "url": "5803防守打法是尖峰岭上附近三点了",
        "createTime": 1513580209000
      }
    ],
    "user": {
      "id": 5,
      "nickname": "PAI7854883123",
      "nicknameModified": false,
      "avatarModified": false,
      "gender": 0,
      "genderModified": false,
      "mobileNumber": "15321763132",
      "ageLabel": 0,
      "pf": "iOS",
      "aliCredit": false
    },
    "house": {
      "id": 2,
      "rent": 2345,
      "readyTime": 1513320419764,
      "room": 1,
      "parlor": 1,
      "payment": "1,2,3",
      "rentType": "1,2,3",
      "communityId": 6280,
      "buildArea": 30,
      "cityId": 1,
      "areaId": 1139,
      "businessAreaId": 5803,
      "lon": 116.383373,
      "lat": 39.967424,
      "status": 1,
      "createTime": 1513333817291,
      "userId": 5,
      "pictureCount": 2,
      "communityName": "新风南里",
      "areaName": "西城",
      "businessAreaName": "马甸",
      "updateTime": 1513580209224,
      "ip": "0:0:0:0:0:0:0:1",
      "hasWIFI": true,
      "hasFridge": false,
      "hasAirConditioning": false,
      "hasWasher": false,
      "hasToilet": false,
      "hasShower": false,
      "hasHeating": false,
      "hasGas": false,
      "hasWardrobe": false,
      "hasKitchen": false,
      "hasTV": false,
      "hasSofa": false,
      "hasBalcony": false,
      "hasElevator": false,
      "description": "有花堪折直须折，待到无花空折枝.。。33",
      "subwayName": "1号线,5号线"
    },
    "seen": {
      "seenCount": "2",
      "avatar": "xxx,null,"
    },
    "messages": [
      {
        "id": 1,
        "fromUserId": 2,
        "toUserId": 1,
        "messageInfoType": "HOUSE",
        "messageInfoId": 2,
        "context": "飞飞飞",
        "fromUser": {
          "id": 2,
          "nickname": "2222",
          "nicknameModified": false,
          "avatar": "xxx",
          "avatarModified": false,
          "gender": 0,
          "genderModified": false,
          "ageLabel": 90,
          "pushToken": "xxx",
          "career": "xxx",
          "favorite": "xxx",
          "personalProfile": "xxx",
          "aliCredit": true
        },
        "toUser": {
          "id": 1,
          "nickname": "1111",
          "nicknameModified": false,
          "avatar": "xxx",
          "avatarModified": false,
          "gender": 0,
          "genderModified": false,
          "ageLabel": 85,
          "pushToken": "xxx",
          "career": "xxx",
          "favorite": "xxx",
          "personalProfile": "xxx",
          "aliCredit": true
        },
        "reply": [
          {
            "id": 2,
            "fromUserId": 2,
            "toUserId": 1,
            "messageInfoType": "HOUSE",
            "messageInfoId": 2,
            "context": "NIHAOAHJSDFLASDJFS\n",
            "parentId": 1,
            "fromUser": {
              "id": 2,
              "nickname": "2222",
              "nicknameModified": false,
              "avatar": "xxx",
              "avatarModified": false,
              "gender": 0,
              "genderModified": false,
              "ageLabel": 90,
              "pushToken": "xxx",
              "career": "xxx",
              "favorite": "xxx",
              "personalProfile": "xxx",
              "aliCredit": true
            },
            "toUser": {
              "id": 1,
              "nickname": "1111",
              "nicknameModified": false,
              "avatar": "xxx",
              "avatarModified": false,
              "gender": 0,
              "genderModified": false,
              "ageLabel": 85,
              "pushToken": "xxx",
              "career": "xxx",
              "favorite": "xxx",
              "personalProfile": "xxx",
              "aliCredit": true
            }
          },
          {
            "id": 5,
            "fromUserId": 1,
            "toUserId": 2,
            "messageInfoType": "HOUSE",
            "messageInfoId": 2,
            "context": "浪里个浪",
            "parentId": 1,
            "fromUser": {
              "id": 1,
              "nickname": "1111",
              "nicknameModified": false,
              "avatar": "xxx",
              "avatarModified": false,
              "gender": 0,
              "genderModified": false,
              "ageLabel": 85,
              "pushToken": "xxx",
              "career": "xxx",
              "favorite": "xxx",
              "personalProfile": "xxx",
              "aliCredit": true
            },
            "toUser": {
              "id": 2,
              "nickname": "2222",
              "nicknameModified": false,
              "avatar": "xxx",
              "avatarModified": false,
              "gender": 0,
              "genderModified": false,
              "ageLabel": 90,
              "pushToken": "xxx",
              "career": "xxx",
              "favorite": "xxx",
              "personalProfile": "xxx",
              "aliCredit": true
            }
          }
        ]
      }
    ],
    "recommendHouses": [],
    "liked": false,
    "houseIsContract": false,
    "loginUserIsContract": false,
    "alterBonus": true
  }
}
```

### 无房详情
##### 接口:/HouseRequestController/findById
##### 请求方式:GET

|参数名|类型|描述|是否必须|
|---|---|---|---|
|id|Long|id|是|

##### 成功返回值

```
{
  "ret": 200,
  "data": {
    "user": {
      "id": 4,
      "nickname": "PAI4588523981",
      "nicknameModified": false,
      "avatar": "ooo",
      "avatarModified": true,
      "gender": 2,
      "genderModified": true,
      "mobileNumber": "18514030307",
      "ageLabel": 2,
      "birthday": 3,
      "pf": "iOS",
      "career": "xxx2",
      "favorite": "xxx1;xxx2",
      "personalProfile": "xxx1",
      "aliCredit": false
    },
    "houseRequest": {
      "id": 4,
      "description": "啦啦啦啦啦",
      "expectedLocation": "5803 1111",
      "expectedLocations": "xxx xxx",
      "expectedAreaNames": "朝阳 海淀"
      "expectedTime": 2312312312312312312,
      "startRent": 1000,
      "endRent": 10000,
      "cityId": 1,
      "status": 2,
      "createTime": 1513390173122,
      "userId": 4
    },
    "messages": [],
    "seen": {
      "seenCount": "1",
      "avatar": "null,"
    },
    "nearbyRentFriend": [],
    "liked": false,
    "alterBonus": true
  }
}
```

### 地图根据坐标查询附近房源
##### 接口:/HouseController/findNearbyHouses
##### 请求方式:GET
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|lat|Long|纬度|是|
|lon|Long|经度|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": [
    {
      "id": 2,
      "rent": 799766,
      "readyTime": 1,
      "room": 2,
      "parlor": 3,
      "payment": "押一付一,押一付三,押一付六",
      "rentType": "主卧,次卧",
      "communityId": 1064,
      "buildArea": 979,
      "cityId": 1,
      "areaId": 1139,
      "businessAreaId": 5803,
      "lon": 116.392535,
      "lat": 39.971349,
      "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp051ce290-6548-4c2a-8ded-da864871afa5.jpg",
      "status": 1,
      "createTime": 1513684401673,
      "nearbySubways": "236719,640931,823.0;236719,1102109,1089.0",
      "userId": 7,
      "pictureCount": 7,
      "communityName": "阳光丽景",
      "areaName": "西城",
      "businessAreaName": "马甸",
      "ip": "10.141.159.122",
      "hasWIFI": false,
      "hasFridge": false,
      "hasAirConditioning": false,
      "hasWasher": false,
      "hasToilet": true,
      "hasShower": true,
      "hasHeating": false,
      "hasGas": false,
      "hasWardrobe": true,
      "hasKitchen": true,
      "hasTV": false,
      "hasSofa": true,
      "hasBalcony": true,
      "hasElevator": false,
      "description": "涅破婆婆婆婆鞥农民工民工漫",
      "subwayName": "8号线,8号线",
      "user": {
        "id": 7,
        "nickname": "PAI7983812345",
        "nicknameModified": false,
        "avatarModified": false,
        "gender": 0,
        "genderModified": false,
        "mobileNumber": "18401657466",
        "ageLabel": 0,
        "pf": "android",
        "favorite": "null",
        "aliCredit": false
      }
    }
  ]
}
```

### 获取求租信息（更新）
##### 接口:HouseRequestController/byId
##### 请求方式:GET
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|id|Long|id|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "id": 66,
    "description": "他知我者谓我心忧中央音乐学院天助自助者呜呜呜呜呜呜呜呜了我",
    "expectedLocation": "5149",
    "expectedLocations": "菜市口",
    "expectedAreas": "1141",
    "expectedAreaNames": "宣武",
    "expectedTime": 1514044800000,
    "startRent": 800,
    "endRent": 4500,
    "cityId": 1,
    "status": 2,
    "createTime": 1513997509330,
    "userId": 7,
    "updateTime": 1513997509330
  }
}
```

### 获取房源信息（更新）
##### 接口:HouseController/byId
##### 请求方式:GET
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|id|Long|id|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "images": [
      {
        "id": 92,
        "houseId": 15,
        "url": "http://test-1251500528.file.myqcloud.com/hzpbacfc8e5-4956-4568-aad2-fd7b0ca838dc.jpg",
        "createTime": 1513942122000
      }
    ],
    "house": {
      "id": 15,
      "rent": 3000,
      "readyTime": 1,
      "room": 2,
      "parlor": 1,
      "payment": "2",
      "rentType": "2",
      "communityId": 1064,
      "buildArea": 68,
      "cityId": 1,
      "areaId": 1139,
      "businessAreaId": 5803,
      "lon": 116.392535,
      "lat": 39.971349,
      "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzpbacfc8e5-4956-4568-aad2-fd7b0ca838dc.jpg",
      "status": 1,
      "createTime": 1513942122068,
      "nearbySubways": "236719,640931,823.0;236719,1102109,1089.0",
      "userId": 7,
      "pictureCount": 8,
      "communityName": "阳光丽景",
      "areaName": "西城",
      "businessAreaName": "马甸",
      "updateTime": 1513942122068,
      "ip": "10.141.159.122",
      "hasWIFI": true,
      "hasFridge": true,
      "hasAirConditioning": true,
      "hasWasher": true,
      "hasToilet": true,
      "hasShower": true,
      "hasHeating": true,
      "hasGas": true,
      "hasWardrobe": true,
      "hasKitchen": true,
      "hasTV": true,
      "hasSofa": true,
      "hasBalcony": true,
      "hasElevator": false,
      "description": "repo实际情况实际上看上去看看",
      "subwayName": "8号线"
    }
  }
}
```

### 查看登录用户是否可以发布房源和求租
##### 接口:/ProfileController/canPublish
##### 请求方式:GET
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "canPublishHouseRequest": false,
    "canPublishHouse": false
  }
}
```

### 求租上架
##### 接口:/HouseRequestController/on
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|houseRequestId|Long|求租Id|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}
```

### 求租下架
##### 接口:/HouseRequestController/off
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|houseRequestId|Long|求租Id|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}
```

### 房源上架
##### 接口:/HouseController/on
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|houseId|Long|房子Id|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}
```

### 房源下架
##### 接口:/HouseController/off
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|houseId|Long|房子Id|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}
```

### 发布权限检查
##### 接口:/ProfileController/checkPublish
##### 请求方式:GET
|参数名|类型|描述|是否必须|
|---|---|---|---|
|type|String|发布类型 ： HOUSE  HOUSE_REQUEST|是|

##### 成功返回值
```
{
  ret: 200,
  data: {
    administratorsIsPublishHouse: false (房管员审核成功之后是否发布过房源)
  }
}
```

##IM
### 需要在IM中展示的push信息
##### 接口:/UserController/imMessages
##### 请求方式:GET
##### 成功返回值
```
{
  "ret": 200,
  "data": [
    {
      "userId": 0,
      "title": "合租派",
      "text": "1321",
      "inIm": true,
      "time": 1515561482043,
      "goType": "homePage",
      "all": true
    },
    {
      "userId": 0,
      "title": "合租派",
      "text": "测试消息列表",
      "inIm": true,
      "time": 1515564267091,
      "goType": "homePage",
      "all": true
    },
    {
      "userId": 0,
      "title": "合租派",
      "text": "测试消息列表\n2",
      "inIm": true,
      "time": 1515565633179,
      "goType": "homePage",
      "all": true
    }
  ]
}
```

## 押金险/签约
### 获取购买押金险数量
##### 接口:/DepositController/depositCount
##### 请求方式:GET
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|

##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}
```

### 查询押金险
##### 接口:/ActivityController/queryDeposit
##### 请求方式:GET
##### 接口参数
公共参数
##### 成功返回值
```
{
	"ret": 200,
	"data": {
		"date": "2018年06月29日",  过期时间
		"code": "HYYFGH",
		"status": "1" ,  押金险领取状态 1未使用 2已使用 3已过期
        "money": 5000  页面显示金额
	}
}
```


### 去签约介绍页
##### 接口:Application/contractPlanDetail
##### 请求方式:GET、
##### 成功返回值
```
{
ret: 200,
data: {
promotions: [
{
id: 1,
term: 1,
bonus: 200,
description: "7天内完成在线签约，奖200元现金！",
active: true,
tips: "您在7天内完成签约，根据《趣签约计划》 您可以获取200元",
obtainBonusTips: "关注公众号“合租趣味”；发送您交易绑定的手机号码，以及交易订单页面截图，2个工作日内完成打款。",
day: 7,
currentTime: 1528858220687,
expireTime: 545715781
},
{
id: 2,
term: 2,
bonus: 100,
description: "15天内完成在线签约，奖100元现金！",
active: true,
tips: "您在15天内完成签约，根据《趣签约计划》 您可以获取100元",
obtainBonusTips: "关注公众号“合租趣味”；发送您交易绑定的手机号码，以及交易订单页面截图，2个工作日内完成打款。",
day: 15,
currentTime: 1528858220687,
expireTime: 1236915781
},
{
id: 3,
term: 3,
bonus: 50,
description: "超出十五天完成在线签约，奖50元现金！",
active: true,
tips: "您已完成签约，根据《趣签约计划》 您可以获取50元",
obtainBonusTips: "关注公众号“合租趣味”；发送您交易绑定的手机号码，以及交易订单页面截图，2个工作日内完成打款。",
day: 0
}
],
contractPlan: "true",
showPromotions: [
{
id: 1,
term: 1,
bonus: 200,
description: "7天内完成在线签约，奖200元现金！",
active: true,
tips: "您在7天内完成签约，根据《趣签约计划》 您可以获取200元",
obtainBonusTips: "关注公众号“合租趣味”；发送您交易绑定的手机号码，以及交易订单页面截图，2个工作日内完成打款。",
day: 7
},
{
id: 2,
term: 2,
bonus: 100,
description: "15天内完成在线签约，奖100元现金！",
active: true,
tips: "您在15天内完成签约，根据《趣签约计划》 您可以获取100元",
obtainBonusTips: "关注公众号“合租趣味”；发送您交易绑定的手机号码，以及交易订单页面截图，2个工作日内完成打款。",
day: 15
},
{
id: 3,
term: 3,
bonus: 50,
description: "超出十五天完成在线签约，奖50元现金！",
active: true,
tips: "您已完成签约，根据《趣签约计划》 您可以获取50元",
obtainBonusTips: "关注公众号“合租趣味”；发送您交易绑定的手机号码，以及交易订单页面截图，2个工作日内完成打款。",
day: 0
}
],
house: {
id: 133,
rent: 5333,
readyTime: 1528732800000,
room: 2,
parlor: 1,
payment: "2",
rentType: "1",
communityId: 1102837,
buildArea: 23,
cityId: 1,
areaId: 1142,
businessAreaId: 1203,
lon: 116.490587,
lat: 39.998943,
listImageUrl: "http://test-1251500528.file.myqcloud.com/hzp1b271196-0bec-4c16-ac0e-1503ee1e0379.jpg",
status: 1,
createTime: 1528799136468,
nearbySubways: "677835,1101618,822.0;677835,1101619,1129.0;572986,573111,1326.0;677835,573111,1326.0;677835,1101617,1359.0",
userId: 222,
pictureCount: 1,
violationReason: "",
outTime: 1528799869027,
communityName: "方恒时代中心",
areaName: "朝阳",
businessAreaName: "望京",
updateTime: 1528855756391,
ip: "10.141.159.122",
hasWIFI: true,
hasFridge: false,
hasAirConditioning: false,
hasWasher: false,
hasToilet: false,
hasShower: false,
hasHeating: false,
hasGas: false,
hasWardrobe: false,
hasKitchen: true,
hasTV: false,
hasSofa: false,
hasBalcony: false,
hasElevator: false,
hasBed: true,
description: "房子很好。交通方便设施完善。干净卫生整洁。",
subwayName: "14号线 14号线 15号线 14号线 14号线",
identity: 2,
toiletCount: 1,
subwayStationName: "望京南 阜通 望京 望京 高家园",
contractPlan: true
}
}
}
```
### 去签约开关
##### 接口:/ActivityController/operate
##### 请求方式:GET
|参数名|类型|描述|是否必须|
|---|---|---|---|
##### 成功返回值
```
{
ret: 200,
data: {
promotions: [
{
id: 1,
term: 1,
bonus: 200,
description: "7天内完成在线签约，奖200元现金！",
active: true,
tips: "您在7天内完成签约，根据《趣签约计划》 您可以获取200元",
obtainBonusTips: "关注公众号“合租趣味”；发送您交易绑定的手机号码，以及交易订单页面截图，2个工作日内完成打款。",
day: 7,
currentTime: 1528858930454,
expireTime: 545006014
},
{
id: 2,
term: 2,
bonus: 100,
description: "15天内完成在线签约，奖100元现金！",
active: true,
tips: "您在15天内完成签约，根据《趣签约计划》 您可以获取100元",
obtainBonusTips: "关注公众号“合租趣味”；发送您交易绑定的手机号码，以及交易订单页面截图，2个工作日内完成打款。",
day: 15,
currentTime: 1528858930454,
expireTime: 1236206014
},
{
id: 3,
term: 3,
bonus: 50,
description: "超出十五天完成在线签约，奖50元现金！",
active: true,
tips: "您已完成签约，根据《趣签约计划》 您可以获取50元",
obtainBonusTips: "关注公众号“合租趣味”；发送您交易绑定的手机号码，以及交易订单页面截图，2个工作日内完成打款。",
day: 0
}
],
contractPlan: "true",
cityOnOff: true,
onOff: true
}
}
```

### 去签约返回模型为
```
{
id: 1,
term: 1,
bonus: 200,
description: "7天内完成在线签约，奖200元现金！",
active: true,
tips: "您在7天内完成签约，根据《趣签约计划》 您可以获取200元",
obtainBonusTips: "关注公众号“合租趣味”；发送您交易绑定的手机号码，以及交易订单页面截图，2个工作日内完成打款。",
day: 7,
currentTime: 1528858930454,
expireTime: 545006014
}
```


### 线下签约
##### 接口:/SignController/offOnlineSave
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|houseId|long|签约房源id|是|
|startTime|Date|起租日期|是|
|endTime|Date|终止日期|是|
|rentPrice|double|月租金|是|
|payment|int|支付方式|是|
|certNo|String|出租方身份证号|是|
|name|String|出租方姓名|是|
|lesseeCertNo|String|承租方身份证号|是
|lesseeName|String|承租方姓名|是|
|contractUrl|String|合同照片(url 逗号隔开)|是|

##### 成功返回值
```
{
  ret: 200,
  data: {}
}
```

### 签约之前提示
##### 接口:/SignController/matchPromotion
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|houseId|long|签约房源id|是|

##### 成功返回值
```
{
  ret: 200,
  data: {
  id: 1,
  term: 1,
  bonus: 200,
  description: "7天内完成在线签约，奖200元现金！",
  active: true,
  tips: "您在7天内完成签约，根据《趣签约计划》 您可以获取200元",
  obtainBonusTips: "关注公众号“合租趣味”；发送您交易绑定的手机号码，以及交易订单页面截图，2个工作日内完成打款。",
  day: 7,
  currentTime: 1528858930454,
  expireTime: 545006014
  }
}
```

### 选择线上或者线下
##### 接口:/SignController/paymentMode
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|contractId|long|签约id|是|
|mode|int|1-线上，2-线下|是|
##### 成功返回值
```
{
  ret: 200,
  data: {}
}
```

### 租金历史记录接口
##### 接口:/SignController/contractPaymentList
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|contractId|long|签约id|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "startTime": 1534953600000,//开始时间
    "endTime": 1566403200000,//结束时间
    "list": [
      {
        "rentCount": 6,//月租X
        "shouldPayDate": 1534953600000,X前支付
        "depositCount": 1,//押金X
        "startTime": 1534953600000,期间
        "endTime": 1550764800000,期间
        "status": "未支付",
        "statusValue": "_0",//_2已支付
        "paymentTime": null,
      },
      {
        "rentCount": 6,
        "shouldPayDate": 1550851200000,
        "depositCount": 0,
        "startTime": 1550851200000,
        "endTime": 1566403200000,
        "status": "未支付",
        "statusValue": "_0",//_2已支付
        "paymentTime": null,
      }
    ]
  }
}
```

### 绑定微信接口
##### 接口:/OperationController/bindWechat
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|code|String|code|是|
##### 成功返回值
```
{
  ret: 200,
  data: {}
}
```

### 公寓提现接口
##### 接口:/OperationController/gongyuWithdraw
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|image|String|image|是|
##### 成功返回值
```
{
  ret: 200,
  data: {}
}
```

## 其他
### 生成海报
##### 接口:/ActivityController/getPoster
##### 请求方式:GET
|参数名|类型|描述|是否必须|
|---|---|---|---|
|id|long|房源id|是|
|type|int|房源类型 0出租 1求租|是|
##### 成功返回值
```
{
	"ret": 200,
	"data": "http://test-1251500528.file.myqcloud.com/backend/img/1527842495956a1104c0c4bff4391bd7f822cedff8ff5.jpg"
}
```

## 公寓

### 入驻申请
##### 接口:/UserController/initState
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|apartmentName|String|公寓名称|是|
|apartmentCityId|Long|城市id|是|
|phone|String|手机号|是|
|code|String|验证码|是|
##### 成功返回值
```
{
  ret: 200,
  data: {
    "id": 4,
    "nickname": "PAI4588523981",
    "nicknameModified": false,
    "avatar": "xxx",
    "avatarModified": false,
    "gender": 0,
    "genderModified": false,
    "mobileNumber": "18514030307",
    "ageLabel": 0,
    "birthday": 0,
    "pushToken": "xxx",
    "pf": "iOS",
    "career": "xxx",
    "favorite": "xxx",
    "personalProfile": "xxx",
    "aliCredit": false,
    "token": "2fAHedgJvxoprJqq63686",
    "IMSignature": "eJxlj01Pg0AURff8CsK2RocpU6WJi6Y0ijIBLFbDhiDzqC9VGIahHxr-uxWbSOL6nHtv7qdhmqaVBMvzvCjqrtKZPkiwzKlpEevsD0qJIst1NlbiH4S9RAVZXmpQPbQZY5SQoYMCKo0lngxngFqxyfr#####36xzDDJ2xdhQwXUP#####eJx7scehvw5yW8vpEhHJb93JrB-aL2QHlxeNE8c-KD50NXWiXjsryM73OhZAmWsRJpGLyoYwQ2NnUWH3t0uXb16aY3dcv7WzK4Hkxrf4XTGHjOXTcjlgG5BtVhXvUDJUaHEJT#####PjS-jGz5qW-E_",
    "isAdministrators": true,
    "apartmentName": "自如公寓",
    apartmentCityId: 1,
    reason: "aaa",
    "status": 1(0 普通用户没有提交过入驻申请 1 待审核 2 审核通过 3 审核不通过)
  }
}
```

### 我的交易(公寓房管员)
##### 接口:/SignController/housekeeperContract
##### 请求方式:GET
|参数名|类型|描述|是否必须|
|---|---|---|---|
|type|int|类型 0展示房源 上架 1签订中 2已签约 3已下架|是|
##### 成功返回值
```
{
	"ret": 200,
	"data": {
		"list": [{
			"id": 118,
			"rent": 6900.0,
			"readyTime": 1,
			"room": 2,
			"parlor": 2,
			"payment": "3",
			"rentType": "3",
			"communityId": 1084664,
			"buildArea": 135.0,
			"cityId": 1,
			"areaId": 1142,
			"businessAreaId": 1193,
			"lon": 116.419837,
			"lat": 40.014772,
			"listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/35CAE0BF-2B61-4A3B-B697-B96AA2B3FE98.jpg",
			"status": 2,
			"createTime": 1528280799366,
			"nearbySubways": "236718,573170,570.0;572986,573170,570.0;572986,11",
			"userId": 201,
			"pictureCount": 1,
			"violationReason": "",
			"outTime": 1528455069366,
			"communityName": "荣尊堡国际俱乐部公寓",
			"areaName": "朝阳",
			"businessAreaName": "亚运村",
			"updateTime": 1528455071873,
			"ip": "10.141.159.122",
			"hasWIFI": false,
			"hasFridge": true,
			"hasAirConditioning": true,
			"hasWasher": true,
			"hasToilet": true,
			"hasShower": false,
			"hasHeating": false,
			"hasGas": false,
			"hasWardrobe": true,
			"hasKitchen": false,
			"hasTV": false,
			"hasSofa": false,
			"hasBalcony": true,
			"hasElevator": false,
			"hasBed": true,
			"description": "季节里的咯头盖埃诺偷偷女哦人类爱老婆母母母母竭",
			"subwayName": "5号线 15号线 15号线 15号线 8号线 15号线 8号线",
			"identity": 2,
			"toiletCount": 1,
			"subwayStationName": "大屯路东 大屯路东 安立路 关庄 森林公园南门 森林公园南门 奥林匹克公园",
			"contractPlan": false,
			"isApartment": false
			"contractType" :1 线上  //1线上 2线下
           	"isHasHouse" : 1   是否有房源 //0无房 1有房
            "authenticationStatus": 1   身份信息验证  0未验证 1 验证成功 2 验证失败
            "contractTypeStatus" : 1
            交易状态 数字 0, "签订中"  1, "已签订" 2, "已失效" 3, "已过期"  4, "已关闭"
            "extend" :20 扩展字字段 页面展示20元金额需要
            "isFailToplimit" :0  身份验证失败上限 //0无 1有
            "closeReason" :"身份信息校验失败2次，交易关闭"      交易关闭原因
		}]
	}
}
```

### 管理员发布房源数量
##### 接口:/GoSignH5Controller/administratorsHouseCount
##### 请求方式:GET
|参数名|类型|描述|是否必须|
|---|---|---|---|
|token|String|token|是|
##### 成功返回值
```
{
  ret: 200,
  data: {
    houseCount: 10
  }
}
```

## 钱包
### 查看钱包当前信息
##### 接口:/OperationController/account
##### 请求方式:GET
##### 成功返回值
```
{
  ret: 200,
  data: {
    bonusTotal: 100.12，//账户余额
    moneyInTransit: 40.22，//账户余额
    available: true//为ture表示可提现，false不可提现
  }
}
```

### 获奖信息展示接口
##### 接口:/OperationController/dynamic
##### 请求方式:GET
##### 成功返回值
```
{
  "ret": 200,
  "data": [
    {
      "name": "name1",
      "amount": 99
    }
  ]
}
```

## 扫码激励
### 扫码进入小程序奖励
##### 接口:/OperationController/fromQRCODE
##### 请求方式:GET
|参数名|类型|描述|是否必须|
|---|---|---|---|
|token|String|token|是|
|userId|Long|二维码中嵌套的userId|是|
##### 成功返回值
```
{
  ret: 200,
  data: {
  }
}
```

### 新版线下签约
##### 接口:/SignController/newOffOnlineSave
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|houseId|long|签约房源id|是|
|startTime|Date|起租日期|是|
|endTime|Date|终止日期|是|
|rentPrice|double|月租金|是|
|payment|String|支付方式|是|
|certNo|String|出租方身份证号|是|
|name|String|出租方姓名|是|
|lesseeCertNo|String|承租方身份证号|是
|lesseeName|String|承租方姓名|是|
|contractUrl|String|合同照片(url 逗号隔开)|是|
|id|long|签约合同id 没有传0|是|
|room|Integer|卧室|是|
|parlor|Integer|厅|是|
|toiletCount|Integer|卫生间|是|
|paymentType|int|支付方式 数字 1押一付一 2押一付三 等等|是|
|rentType|int|出租类型 数字 1主卧 2次卧"|是|
|communityId|Long|小区Id|是|
|areaId|Long|区域ID|是|
|images|String|图片url逗号分隔|是|
|listImageUrl|String|展示第一张图片|是|
|hasToilet|boolean|是否独卫|是|
|deposit|double|押金|是|
|address|String|门牌号|是|
|lesseeMobile|String|门牌号|是|


##### 成功返回值
```
{
  "ret": 200,
  "data": [
    {
      "failType": "1", 1房管员身份信息失败 2租客失败
      "msg": "房管员身份验证失败，请返回修改",
      "contract": {
			"id": 6102,
			"communityName": "新一城",
			"address": "123",
			"rentPrice": 2008.0,
			"deposit": 300.0,
			"payment": "押一付三",
			"startTime": 1530144000000,
			"endTime": 1561593600000,
			"houseId": 184,
			"signDate": 1530172388000,
			"status": 1,
			"userId": 219,
			"expireDate": 1530258788000,
			"lessorPromotionStatus": 0,
			"lessorBonus": 50.00,
			"type": 2,
			"lessorCertNo": "372928198812188529",
			"lesseeCertNo": "372928198812188528",
			"lesseeName": "程序",
			"lessorName": "石总",
			"lesseeMobile": "18201370436",
			"authenticationStatus": 1
		}
      (1)字段type 1线上 2线下有房 3线下无房
      (2)字段authenticationStatus  身份验证状态 0未验证 1 验证成功 2 验证失败
      (3)字段status 新增类型 4交易已关闭
    }
  ]
}
```

### 短信通知租户 上线签约
##### 接口:/SignController/notifyLessee
##### 请求方式:GET
|参数名|类型|描述|是否必须|
|---|---|---|---|
|id|Long|交易id|是|
|isCheck|boolean|是否校验 列表是进入是true 其他是false|是|
##### 成功返回值
```
{
  ret: 200,
  data: {
  }
}
```

### 签约奖励
##### 接口:/SignController/offLineSign
##### 请求方式:GET
|参数名|类型|描述|是否必须|
|---|---|---|---|
|contractId|Long|交易id|是|
|type|int|类型 1租客 2房管员|是|
##### 成功返回值
```
{
  ret: 200,
  data: {
  }
}
```

### 查询交易接口
##### 接口:/SignController/queryContract
##### 请求方式:GET
|参数名|类型|描述|是否必须|
|---|---|---|---|
|contractId|Long|交易id|是|
##### 成功返回值
```
{
	"ret": 200,
	"data": {
		"contract": {
			"id": 6102,
			"communityName": "新一城",
			"address": "123",
			"rentPrice": 2008.0,
			"deposit": 300.0,
			"payment": "押一付三",
			"startTime": 1530144000000,
			"endTime": 1561593600000,
			"houseId": 184,
			"signDate": 1530172388000,
			"status": 1,
			"userId": 219,
			"expireDate": 1530258788000,
			"lessorPromotionStatus": 0,
			"lessorBonus": 50.00,
			"type": 2,
			"lessorCertNo": "372928198812188529",
			"lesseeCertNo": "372928198812188528",
			"lesseeName": "程序",
			"lessorName": "石总",
			"lesseeMobile": "18201370436",
			"authenticationStatus": 0
		},
		"house": {
			"id": 184,
			"rent": 2000.0,
			"readyTime": 1529397063205,
			"room": 1,
			"parlor": 1,
			"payment": "5",
			"rentType": "1",
			"communityId": 1102850,
			"buildArea": 63.0,
			"cityId": 1,
			"areaId": 1142,
			"businessAreaId": 1203,
			"lon": 116.47983,
			"lat": 39.998999,
			"listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/4A1DD90B-4AA7-45B3-958F-AA26600CDAB0.jpg",
			"status": 4,
			"createTime": 1529397095050,
			"nearbySubways": "677835,1101619,243.0;572986,573111,630.0;677835,573111,630.0;677835,1101618,676.0;677835,1101617,1804.0;677835,1101620,1986.0",
			"userId": 219,
			"pictureCount": 1,
			"violationReason": "图片不符合规范",
			"outTime": 1529896397432,
			"communityName": "新一城",
			"areaName": "朝阳",
			"businessAreaName": "望京",
			"updateTime": 1530170334642,
			"ip": "10.141.159.122",
			"hasWIFI": false,
			"hasFridge": false,
			"hasAirConditioning": false,
			"hasWasher": false,
			"hasToilet": false,
			"hasShower": false,
			"hasHeating": false,
			"hasGas": false,
			"hasWardrobe": false,
			"hasKitchen": false,
			"hasTV": false,
			"hasSofa": false,
			"hasBalcony": false,
			"hasElevator": false,
			"hasBed": true,
			"description": "兔兔陪不补劳斯莱斯劳斯莱斯他她爬起来去了摸我哦",
			"subwayName": "14号线 15号线 14号线 14号线 14号线 14号线",
			"signedTime": 1530172388187,
			"identity": 5,
			"toiletCount": 1,
			"subwayStationName": "阜通 望京 望京 望京南 高家园 东湖渠",
			"contractPlan": false,
			"isApartment": true
		}
	}
}
```

### 通过房源id查询交易
##### 接口:/SignController/queryContractByHouseId
##### 请求方式:GET
|参数名|类型|描述|是否必须|
|---|---|---|---|
|houseId|Long|房源id|是|
##### 成功返回值
```
{
	"ret": 200,
	"data": {
		{
			id": 6102,
			"communityName": "新一城",
			"address": "123",
			"rentPrice": 2008.0,
			"deposit": 300.0,
			"payment": "押一付三",
			"startTime": 1530144000000,
			"endTime": 1561593600000,
			"houseId": 184,
			"signDate": 1530172388000,
			"status": 1,
			"userId": 219,
			"expireDate": 1530258788000,
			"lessorPromotionStatus": 0,
			"lessorBonus": 50.00,
			"type": 2,
			"lessorCertNo": "372928198812188529",
			"lesseeCertNo": "372928198812188528",
			"lesseeName": "程序",
			"lessorName": "石总",
			"lesseeMobile": "18201370436",
			"authenticationStatus": 0
		} 
	}
}
```

### 去赚钱分享页获取分享数据
##### 接口:/OperationController/shareLink
##### 请求方式:GET
|参数名|类型|描述|是否必须|
|---|---|---|---|
##### 成功返回值
```
{
	ret: 200,
	data: {
		qrcode: "http://www.baidu.com",
		dynamic: [
			{
				name: "空城**",
				amount: 34
			},
			{
				name: "如梦**",
				amount: 32
			},
			{
				name: "旧夏天**",
				amount: 30
			},
			{
				name: "我想要**",
				amount: 27
			}
		],
		message: "合租趣送百万大礼，现金红包抢不停，当天提现！http://u6.gg/dKveP",
		title: "合租趣送百万大礼;"
		subhead: "现金红包请不停,当天提现!",
		link: "http://u6.gg/dKYcE"
	}
}
```
### 去赚钱绑定手机号
##### 接口:/OperationController/bind
##### 请求方式:GET
|参数名|类型|描述|是否必须|
|---|---|---|---|
|userId|Long|邀请人ID|是|
|mobile|String|手机号|是|

##### 成功返回值
```
{
	ret: 200,
	data: {}
}
```

### 身份校验
##### 接口:/UserController/authentication
##### 请求方式:GET
|参数名|类型|描述|是否必须|
|---|---|---|---|
|name|String|姓名|是|
|certNo	|String|身份证号|是|
##### 成功返回值
```
{
	ret: 200,
	data: true
}
```

### 女性专区身份校验
##### 接口:/UserController/missAuth
##### 请求方式:GET
|参数名|类型|描述|是否必须|
|---|---|---|---|
|name|String|姓名|是|
|certNo	|String|身份证号|是|
##### 成功返回值
```
{
	ret: 200,
	data: true
}
```

### 每日签到
##### 接口:/ActivityController/everydaySignIn
##### 请求方式:GET
|参数名|类型|描述|是否必须|
|---|---|---|---|
|isDouble|boolean|是否加倍|是|
##### 成功返回值
```
{
	ret: 200,
	data: {
		money: 25,
		signInDays: 1
	}
}
```

### 签到信息
##### 接口:/ActivityController/signInConfig
##### 请求方式:GET
|参数名|类型|描述|是否必须|
|---|---|---|---|
##### 成功返回值
```
{
	ret: 200,
	data: {
		rewardList: [
			"0.25",
			"0.1",
			"0.1",
			"0.5",
			"0.1",
			"0.25",
			"0.5"
		],
	isSignIn: true,  当日是否签到
	isDouble: true,  当日是否加倍
	signInDays: 1   
}
}
```

## 趣赚钱
### 活动主页接口
##### 接口:/GoSignH5Controller/makeMoneyInfo
##### 请求方式:GET
##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "wallet": {
      "id": 1426,
      "userId": 13261,
      "bonusTotal": 2.05,
      "moneyInTransit": 0,
      "moneyReceived": 0,
      "available": false
    },
    "authenticate": true,//是否可做实名认证任务
    "publishHouse": false,//发房源
    "viewHouseRequest": true,//访问求租
    "publishRequest": true,//发求租
    "forward": true,//转发房源
    "inviteCode": true,//输入邀请码
    "sign": true,//签约
    "invite": true,//邀请好友
    "viewHouse": true,//访问房源
    "rewardCities": [1,2],//签约奖励开放的城市
    "user": {
      "id": 13261,
      "nickname": "阿迪",
      "nicknameModified": true,
      "avatar": "http://test-1251500528.file.myqcloud.com/hzp/F4F82D6A-61EB-40FF-B43C-BC5C8A91F846.jpg",
      "avatarModified": true,
      "gender": 1,
      "genderModified": true,
      "mobileNumber": "18201370436",
      "ageLabel": 2,//年龄标签，具体规则参考客户端吧。。
      "birthday": "06-29",
      "pushToken": "AoacZWXhZ3cycbV6XjwOIoJAuTXC0YO3PD5Jzj7p7NrS",
      "pf": "android",
      "career": "电子通讯",
      "personalProfile": "我去拯救地球了...",
      "zmScore": 0,
      "zmAuth": false,
      "constellation": "巨蟹座",
      "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
      "zmAuthPushed": false,
      "infoCompleted": true,
      "flag": false,
      "privacy": 0,
      "forbidden": false,
      "virtual": false,
      "subscribe": false,
      "isForeign": false,
      "isAdministrators": true,
      "apartmentName": "链家",
      "apartmentCityId": 1,
      "administratorStatus": 2,
      "verifyTime": 1530272291434,
      "realName": "石景梅",
      "certNo": "372928198812188529",
      "isScanCode": false,
      "subscribeFwh": false,
      "invitationCode": "HEZUQU1748771BCD",
      "invited": false,
      "authenticationStatus": 0
    },
    "dynamic": [
      {
        "name": "空城**",
        "amount": 34
      },
      {
        "name": "如梦**",
        "amount": 32
      }
    ]
  }
}
```

### 普通用户线下签约
##### 接口:/SignController/commonOffOnlineSave
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|houseId|long|签约房源id|是|
|startTime|Date|起租日期|是|
|endTime|Date|终止日期|是|
|rentPrice|double|月租金|是|
|payment|String|支付方式|是|
|certNo|String|出租方身份证号|是|
|name|String|出租方姓名|是|
|lesseeCertNo|String|承租方身份证号|是
|lesseeName|String|承租方姓名|是|
|contractUrl|String|合同照片(url 逗号隔开)|是|
|id|long|签约合同id 没有传0|是|
|room|Integer|卧室|是|
|parlor|Integer|厅|是|
|toiletCount|Integer|卫生间|是|
|paymentType|int|支付方式 数字 1押一付一 2押一付三 等等|是|
|rentType|int|出租类型 数字 1主卧 2次卧"|是|
|communityId|Long|小区Id|是|
|areaId|Long|区域ID|是|
|images|String|图片url逗号分隔|是|
|listImageUrl|String|展示第一张图片|是|
|hasToilet|boolean|是否独卫|是|
|deposit|double|押金|是|
|address|String|门牌号|是|
|lesseeMobile|String|求租电话|是|
|dealPlatform|int|线下交易成交平台  1线下门店 258同城 3豆瓣小组 4其他线下平台|是|


##### 成功返回值
```
{
  "ret": 200,
  "data": [
    {
      "failType": "1", 1承租方身份信息失败 2租客失败
      "msg": "身份验证失败，请返回修改",
      "contract": {
			"id": 6102,
			"communityName": "新一城",
			"address": "123",
			"rentPrice": 2008.0,
			"deposit": 300.0,
			"payment": "押一付三",
			"startTime": 1530144000000,
			"endTime": 1561593600000,
			"houseId": 184,
			"signDate": 1530172388000,
			"status": 1,
			"userId": 219,
			"expireDate": 1530258788000,
			"lessorPromotionStatus": 0,
			"lessorBonus": 50.00,
			"type": 2,
			"lessorCertNo": "372928198812188529",
			"lesseeCertNo": "372928198812188528",
			"lesseeName": "程序",
			"lessorName": "石总",
			"lesseeMobile": "18201370436",
			"authenticationStatus": 1
		}
      (1)字段type 1线上 2线下有房 3线下无房
      (2)字段authenticationStatus  身份验证状态 0未验证 1 验证成功 2 验证失败
      (3)字段status 新增类型 4交易已关闭
    }
  ]
}
```

### 是否能线下交易
##### 接口:/SignController/IsCommonOffOnlineSave
##### 请求方式:GET

##### 成功返回值
```
{
	ret: 200,
	data: true
}
```
### 红包字段介绍(必传的参数要传 同盾的 版本 平台（android 调用 传android iOS 调用传iOS）等 等.)
```
红包 summerRedEnvelopes": {
      "id": 1,
      "userId": 13434,
      "createTime": 1533617570975,
      "count": 5, 红包个数
      "bonus": 5, 红包总金额
      "withDrawBonus": 0.43, 被领取的金额
      "withDrawCount": 4, 被领取红包的个数
      "type": "_1"
    }

```
### 领取奖励
##### 接口:/OperationController/withDrawRedEnvelopes
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|summerRedEnvelopesId|Long|红包Id|是|
|mobile|String|手机号|是|
|unionId|String|unionid|是|
|nickname|String|nickname|是|
|headimgurl|String|headimgurl|是|
|sex|Integer|sex|是|
|openId|String|openId|是|
|smsCode|String|验证码|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "bonus": 0.43,
    "redEnvelopes": {
      "id": 1,
      "userId": 13434,
      "createTime": 1533617570975,
      "count": 5,
      "bonus": 5,
      "withDrawBonus": 0,
      "withDrawCount": 3,
      "type": "_1"
    },
    "item": [
      {
        "id": 2518,
        "userId": 15634,
        "bonus": 0.43,
        "createTime": 1533624560584,
        "type": "_11",
        "summerRedEnvelopesId": 1,
        "user": {
          "id": 15634,
          "nickname": "包Sir大魔王",
          "nicknameModified": false,
          "avatar": "http://thirdwx.qlogo.cn/mmopen/vi_32/Q0j4TwGTfTIuADne7YZ7I9kymQzJ4mLSh52CuXgO5sPsz39b5x3kOVsZVzTYic6Qh1GNCPD1TUMnAC6f0GJicQnw/132",
          "avatarModified": false,
          "gender": 1,
          "genderModified": false,
          "mobileNumber": "15321763132",
          "ageLabel": 0,
          "openId": "ob2_D02-Djr_6spN4PusrrcbCCYQ",
          "unionId": "o6EOJ1Yx2RpHwrDEZfykc-6xvimg",
          "career": "卖艺的",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": false,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU1748772512",
          "invited": false,
          "authenticationStatus": 0
        },
        "showDate": "刚刚"
      }
    ]
  }
}
```
### 查看可以创建那中类型的红包
##### 接口:/OperationController/checkSummerRedEnvelopes
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|token|String|token|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "_1": true,(5元)
    "_2": true,（10元）
    "_3": true （20元）
  }
}

```

### 分享红包
##### 接口:/OperationController/shareRedEnvelopes
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|type|String|红包类型|是|
|token|String|token|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "link": "http://hzp.caidingke.net/H5/xx/summerRedEnvelopesId=2",
    "subhead": "你想要冰激凌or大西瓜？",
    "title": "合租趣消暑红包，快来领取！"
  }
}

```

### 红包领取详情
##### 接口:/OperationController/summerRedEnvelopesDetail
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|type|String|红包类型|是|
|token|String|token|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "summerRedEnvelopesItem": [
      {
        "id": 2518,
        "userId": 15634,
        "bonus": 0.43,
        "createTime": 1533624560584,
        "type": "_11",
        "summerRedEnvelopesId": 1,
        "user": {
          "id": 15634,
          "nickname": "包Sir大魔王",
          "nicknameModified": false,
          "avatar": "http://thirdwx.qlogo.cn/mmopen/vi_32/Q0j4TwGTfTIuADne7YZ7I9kymQzJ4mLSh52CuXgO5sPsz39b5x3kOVsZVzTYic6Qh1GNCPD1TUMnAC6f0GJicQnw/132",
          "avatarModified": false,
          "gender": 1,
          "genderModified": false,
          "mobileNumber": "15321763132",
          "ageLabel": 0,
          "openId": "ob2_D02-Djr_6spN4PusrrcbCCYQ",
          "unionId": "o6EOJ1Yx2RpHwrDEZfykc-6xvimg",
          "career": "卖艺的",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": false,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU1748772512",
          "invited": false,
          "authenticationStatus": 0
        },
        "showDate": "48分钟前"
      }
    ],
    "summerRedEnvelopes": {
      "id": 1,
      "userId": 13434,
      "createTime": 1533617570975,
      "count": 5,
      "bonus": 5,
      "withDrawBonus": 0.43,
      "withDrawCount": 4,
      "type": "_1"
    }
  }
}

```

### 根据红包ID查看红包领取详情
##### 接口:/OperationController/findSummerRedEnvelopesItemBySummerRedEnvelopesId
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|summerRedEnvelopesId|Long|红包ID|是|


##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "summerRedEnvelopesItem": [
      {
        "id": 2518,
        "userId": 15634,
        "bonus": 0.43,
        "createTime": 1533624560584,
        "type": "_11",
        "summerRedEnvelopesId": 1,
        "user": {
          "id": 15634,
          "nickname": "包Sir大魔",
          "nicknameModified": true,
          "avatar": "http://thirdwx.qlogo.cn/mmopen/vi_32/Q0j4TwGTfTIuADne7YZ7I9kymQzJ4mLSh52CuXgO5sPsz39b5x3kOVsZVzTYic6Qh1GNCPD1TUMnAC6f0GJicQnw/132",
          "avatarModified": false,
          "gender": 1,
          "genderModified": false,
          "mobileNumber": "15321763132",
          "ageLabel": 1,
          "birthday": "08-07",
          "openId": "ob2_D02-Djr_6spN4PusrrcbCCYQ",
          "unionId": "o6EOJ1Yx2RpHwrDEZfykc-6xvimg",
          "pf": "android",
          "career": "经营管理",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "狮子座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": true,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU1748772512",
          "invited": false,
          "authenticationStatus": 0
        },
        "showDate": "08-07"
      }
    ],
    "summerRedEnvelopes": {
      "id": 1,
      "userId": 13434,
      "createTime": 1533617570975,
      "count": 5,
      "bonus": 5,
      "withDrawBonus": 0.43,
      "withDrawCount": 4,
      "type": "_1"
    }
  }
}

```

### 红包二次分享
##### 接口:/OperationController/secondTimeShare
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|summerRedEnvelopesId|Long|红包ID|是|


##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "wechatConfig": {
      "signature": "0a106f07919e324bf20a4e35b835b34e3a758d40",
      "appId": "wx5f8525c2230c4872",
      "jsapi_ticket": "HoagFKDcsGMVCIY2vOjf9jZqMWLKIwyTPafcjrcPlrY4p46FxSTbTiTPE3ZFaIv27bTh3tXex1QfP2mTq7cCYg",
      "url": "https://open.weixin.qq.com/connect/oauth2/authorize?appid=wx5f8525c2230c4872&redirect_uri=https%3A%2F%2Fhzpwechat-test.baihejia.com%2FGoSignH5Controller%2FsummerGetTel%3FsummerRedEnvelopesId%3D1&response_type=code&scope=snsapi_userinfo&state=STATE#wechat_redirect",
      "nonceStr": "4e354e2d-8171-4526-822f-6abcd6bd972f",
      "timestamp": "1533715998"
    },
    "subhead": "你想要冰激凌or大西瓜？",
    "title": "合租趣消暑红包，快来领取！"
  }
}

```

### 获取公寓接口
##### 接口:/ApartmentController/getApartment
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|name|String|公寓名称|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "items": [
      {
        "id": 11004,
        "name": "测试",
        "brand": "测试",
        "createTime": 1533548865321,
        "status": 1,
        "bankId": 2,
        "bankName": "农业银行",
        "accountName": "王国栋",
        "accountNo": "12123454343",
        "total": 0
      }
    ],
    "count": 1,
    "showCount": 1,
    "extraItems": []
  }
}

```

### 入驻接口
##### 接口:/UserController/administratorProfileAndAuthentication
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|token|String|token|是|
|apartmentName|String|公寓名称|是|
| cityId |Long|城市id|是|
| apartmentId |Long|公寓ID|是|
| brand |String|公寓品牌|是|
| realName |String|姓名|是|
| certNo |String|身份证号|是|
|avatar|String|头像|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "id": 555574,
    "nickname": "果果",
    "nicknameModified": false,
    "avatarModified": false,
    "gender": 3,
    "genderModified": false,
    "mobileNumber": "15278099621",
    "ageLabel": 0,
    "openId": "o_lBJ1BnpXu_97tXkm6ZLlkKVybc",
    "unionId": "o6EOJ1cKdnLKRM33cqJpuXUA0dY0",
    "pf": "android",
    "career": "吉祥物",
    "personalProfile": "我去拯救地球了...",
    "zmScore": 0,
    "zmAuth": false,
    "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
    "zmAuthPushed": false,
    "infoCompleted": false,
    "flag": false,
    "privacy": 0,
    "forbidden": false,
    "virtual": false,
    "subscribe": false,
    "isForeign": false,
    "isAdministrators": false,
    "apartmentName": "自如公寓",
    "apartmentCityId": 1,
    "administratorStatus": 1,
    "isScanCode": false,
    "subscribeFwh": false,
    "invitationCode": "HEZUQU17487F6236",
    "invited": false,
    "apartmentId": 1,
    "brand": "自如",
    "isFacePerception": false,
    "authenticationStatus": 0
  }
}

```

### 人脸认证成功接口
##### 接口:/UserController/facePerception
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|token|String|token|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "id": 555574,
    "nickname": "果果",
    "nicknameModified": false,
    "avatarModified": false,
    "gender": 3,
    "genderModified": false,
    "mobileNumber": "15278099621",
    "ageLabel": 0,
    "openId": "o_lBJ1BnpXu_97tXkm6ZLlkKVybc",
    "unionId": "o6EOJ1cKdnLKRM33cqJpuXUA0dY0",
    "pf": "android",
    "career": "吉祥物",
    "personalProfile": "我去拯救地球了...",
    "zmScore": 0,
    "zmAuth": false,
    "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
    "zmAuthPushed": false,
    "infoCompleted": false,
    "flag": false,
    "privacy": 0,
    "forbidden": false,
    "virtual": false,
    "subscribe": false,
    "isForeign": false,
    "isAdministrators": false,
    "apartmentName": "自如公寓",
    "apartmentCityId": 1,
    "administratorStatus": 1,
    "isScanCode": false,
    "subscribeFwh": false,
    "invitationCode": "HEZUQU17487F6236",
    "invited": false,
    "apartmentId": 1,
    "brand": "自如",
    "isFacePerception": true,
    "authenticationStatus": 0
  }
}

```

### 房源和电话点击量统计
##### 接口:/ApartmentController/clickStatistics
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|token|String|token|是|
|start|Long|开始时间|否|
|end|Long|结束时间|否|
|type|String|类型 PHONE HOUSE|是|


##### 成功返回值
```
不传时间：
{
  "ret": 200,
  "data": {
    "yesterdayClick": 0,
    "todayClickAvg": 0,
    "todayClick": 0,
    "yesterdayClickAvg": 0
  }
}

传时间：
{
  "ret": 200,
  "data": {
    "clickAvg": 0,
    "click": 0
  }
}

```

### 房源量统计
##### 接口:/ApartmentController/houseStatistics
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|token|String|token|是|
|start|Long|开始时间|否|
|end|Long|结束时间|否|


##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "showHouse": 0,
    "business": 0,
    "publish": 0
  }
}

```
### 交易量统计
##### 接口:/ApartmentController/businessStatistics
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|token|String|token|是|
|start|Long|开始时间|否|
|end|Long|结束时间|否|


##### 成功返回值
```
不传时间：
{
  "ret": 200,
  "data": {
    "todaySigning": 0,
    "yesterdayOffline": 0,
    "yesterdayOnline": 0,
    "todayOnline": 0,
    "todayOffline": 0,
    "yesterdaySigning": 0
  }
}

传时间：
{
  "ret": 200,
  "data": {
    "offline": 0,
    "online": 0,
    "signing": 0
  }
}

```

### 点击电话
##### 接口:/ApartmentController/clickPhone
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|userId|Long|被点击电话的userId|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}

```

### 公司账号
##### 接口:/ApartmentController/companyAccount
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|token|String|token|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}

```

### 公司申请
##### 接口:/ApartmentController/apartmentApply
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|token|String|token|是|
|name|String|公司名称|是|
|brand|String|公司品牌|是|
|url|String|营业执照|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}

```

### 绑定提现账号（更新）
##### 接口:/UserController/accountBank
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|token|String|token|是|
|bankId|Long|银行ID|是|
|bankName|String|银行名称|是|
|cardNo|String|卡号|是|
|mobile|String|手机号|是|
|code|String|验证码|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "id": 555574,
    "nickname": "果果",
    "nicknameModified": false,
    "avatarModified": false,
    "gender": 3,
    "genderModified": false,
    "mobileNumber": "15278099621",
    "ageLabel": 0,
    "openId": "o_lBJ1BnpXu_97tXkm6ZLlkKVybc",
    "unionId": "o6EOJ1cKdnLKRM33cqJpuXUA0dY0",
    "pf": "android",
    "career": "吉祥物",
    "personalProfile": "我去拯救地球了...",
    "zmScore": 0,
    "zmAuth": false,
    "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
    "zmAuthPushed": false,
    "infoCompleted": false,
    "flag": false,
    "privacy": 0,
    "forbidden": false,
    "virtual": false,
    "subscribe": false,
    "isForeign": false,
    "isAdministrators": false,
    "apartmentName": "自如公寓",
    "apartmentCityId": 1,
    "administratorStatus": 1,
    "isScanCode": false,
    "subscribeFwh": false,
    "invitationCode": "HEZUQU17487F6236",
    "invited": false,
    "apartmentId": 1,
    "brand": "自如",
    "isFacePerception": true,
    "authenticationStatus": 0,
    "bankId": 1,
    "bankName" : "招商银行",
    "bankCardNo" : "123456",
    "source": 2
  }
}
```

### 获取银行列表
##### 接口:/ProfileController/bank
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|token|String|token|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": [
    {
      "id": 1,
      "name": "招商银行"
    },
    {
      "id": 2,
      "name": "农业银行"
    }
  ]
}

```
### 获取银行列表
##### 接口:/ApartmentController/findApartmentByUserId
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|token|String|token|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "id": 2,
    "name": "自如管家公司",
    "brand": "自如管家",
    "url": "http://test-1251500528.file.myqcloud.com/hzp4db10eb7-dda9-453b-9e83-221d56445c0a.jpg",
    "createTime": 1534233073804,
    "status": 0,
    "requestUserId": 555648
  }
}

```

### 房源列表 (B端)
##### 接口:/SignController/houseList
##### 请求方式:GET
|参数名|类型|描述|是否必须|
|---|---|---|---|
|type|int|0展示房源 上架  1已签约 2已下架|是|
##### 成功返回值
```
type为 0和2的返回值
{
	ret: 200,
	data: {
		list: [{
				id: 31097,
				rent: 3688,
				readyTime: 1534176000000,
				room: 1,
				parlor: 1,
				payment: "2",
				rentType: "1",
				communityId: 1085892,
				buildArea: 56,
				cityId: 1,
				areaId: 1141,
				businessAreaId: 5842,
				lon: 116.340519,
				lat: 39.893557,
				listImageUrl: "http://test-1251500528.file.myqcloud.com/hzp0682d912-3926-4160-a3ab-bf31a4f6850a.jpg",
				status: 1,
				createTime: 1534228804429,
				nearbySubways: "1101595,1101597,253.0;1101595,1101596,540.0;1101595,634627,1341.0;634618,634627,1341.0;634618,634626,1705.0",
				userId: 555583,
				pictureCount: 3,
				communityName: "马连道北街小区",
				areaName: "宣武",
				businessAreaName: "马连道",
				updateTime: 1534228804429,
				ip: "106.39.84.154",
				hasWIFI: false,
				hasFridge: false,
				hasAirConditioning: false,
				hasWasher: true,
				hasToilet: false,
				hasShower: true,
				hasHeating: false,
				hasGas: false,
				hasWardrobe: false,
				hasKitchen: false,
				hasTV: false,
				hasSofa: false,
				hasBalcony: true,
				hasElevator: false,
				hasBed: true,
				description: "明明你哦你狗狗狗狗狗狗狗ing明明哦明明哦轰轰轰",
				subwayName: "7号线 7号线 7号线 9号线 9号线",
				identity: 5,
				toiletCount: 1,
				subwayStationName: "达官营 湾子 北京西站 北京西站 六里桥东",
				contractPlan: false,
				isApartment: true,
				lessorBonus: 100,
				extend: 20
			}
		]
	}
}
type为1 的返回值

{
	ret: 200,
	data: {
		list: [{
			id: 6329,
			communityName: "白纸坊桥",
			address: "门萨排比唉",
			rentPrice: 2589,
			deposit: 2685,
			payment: "押一付一",
			startTime: 1534262400000,
			endTime: 1565712000000,
			lessor: {
				id: 6415,
				userId: 555583,
				name: "张振东",
				certNo: "410782199206254736",
				mobile: "18401657466",
				type: "LESSOR",
				contractId: 6329,
				gender: 3
			},
			lessee: {
				id: 6414,
				userId: 13365,
				name: "付森",
				certNo: "131182199203043416",
				mobile: "13021021262",
				type: "LESSEE",
				contractId: 6329,
				avatar: "http://test-1251500528.file.myqcloud.com/hzpd94b0855-4bf8-49c6-ba2a-2666b6edaa32.jpg",
				gender: 2,
				nickname: "包子"
			},
			status: "已签订",
			isDeposit: false,
			url: "http://hzp.caidingke.net/sign/detail?id=6329&pf=WEB&cityId=1&ver=null",
			effectDate: 1534651200166,
			expiredDate: 1566100800166,
			amount: 2685,
			premium: 0.01,
			premiumOri: 299,
			supplement: "",
			overdue: 1534389918000,
			house: {
				id: 31036,
				rent: 699,
				readyTime: 1534176000000,
				room: 1,
				parlor: 1,
				payment: "2",
				rentType: "1",
				communityId: 1085882,
				buildArea: 500,
				cityId: 1,
				areaId: 1141,
				businessAreaId: 5835,
				lon: 116.355769,
				lat: 39.883297,
				listImageUrl: "http://test-1251500528.file.myqcloud.com/hzpcb005ae6-3675-4c93-9266-2184191722d1.jpg",
				status: 4,
				createTime: 1534216719236,
				nearbySubways: "1101595,1101598,1555.0;1101595,1101597,1895.0",
				userId: 555583,
				pictureCount: 3,
				communityName: "白纸坊桥",
				areaName: "宣武",
				businessAreaName: "白纸坊",
				updateTime: 1534216719236,
				ip: "106.39.84.154",
				hasWIFI: false,
				hasFridge: false,
				hasAirConditioning: false,
				hasWasher: true,
				hasToilet: false,
				hasShower: false,
				hasHeating: false,
				hasGas: false,
				hasWardrobe: true,
				hasKitchen: false,
				hasTV: false,
				hasSofa: false,
				hasBalcony: true,
				hasElevator: false,
				hasBed: true,
				description: "446464644466464646468756464664",
				subwayName: "7号线 7号线",
				signedTime: 1534303683219,
				identity: 5,
				toiletCount: 1,
				subwayStationName: "广安门内 达官营",
				contractPlan: false,
				isApartment: false
			},
			lessorUser: {
				id: 555583,
				nickname: "P53392",
				nicknameModified: false,
				avatar: "http://test-1251500528.file.myqcloud.com/hzp17276f12-6413-449f-8897-d9b3396f1187.jpg",
				avatarModified: false,
				gender: 3,
				genderModified: false,
				mobileNumber: "18401657466",
				ageLabel: 0,
				pushToken: "AneAA6239h7SuXbOQW_iouV7plSYiDMaApfggmy7l5mb",
				pf: "android",
				career: "小宝贝",
				personalProfile: "我去拯救地球了...",
				zmScore: 0,
				zmAuth: false,
				background: "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
				zmAuthPushed: false,
				infoCompleted: false,
				flag: false,
				privacy: 0,
				forbidden: false,
				virtual: false,
				subscribe: false,
				isForeign: false,
				isAdministrators: true,
				apartmentName: "租趣科技有限公司",
				apartmentCityId: 1,
				administratorStatus: 2,
				realName: "张振东",
				certNo: "410782199206254736",
				isScanCode: false,
				subscribeFwh: false,
				invitationCode: "HEZUQU17487F623F",
				invited: false,
				apartmentId: 1,
				brand: "租趣公寓",
				isFacePerception: true,
				authenticationStatus: 1,
				source: 2
			},
			lesseeUser: {
				id: 13365,
				nickname: "包子",
				nicknameModified: true,
				avatar: "http://test-1251500528.file.myqcloud.com/hzpd94b0855-4bf8-49c6-ba2a-2666b6edaa32.jpg",
				avatarModified: true,
				gender: 2,
				genderModified: true,
				mobileNumber: "13021021262",
				ageLabel: 5,
				birthday: "07-31",
				pushToken: "Aoi23MV2l6kBT27z4CoBmiCz4xnMkDtrCibYhVFJsOQY",
				pf: "android",
				career: "法律",
				personalProfile: "我去拯救地球了...",
				zmScore: 0,
				zmAuth: false,
				constellation: "狮子座",
				background: "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
				zmAuthPushed: false,
				infoCompleted: true,
				flag: false,
				privacy: 0,
				forbidden: false,
				virtual: false,
				subscribe: false,
				isForeign: false,
				isAdministrators: false,
				administratorStatus: 0,
				realName: "石景梅",
				certNo: "372928198812188529",
				isScanCode: false,
				subscribeFwh: false,
				invitationCode: "HEZUQU1748771C35",
				invited: false,
				isFacePerception: false,
				authenticationStatus: 1
			},
			lessorPromotionStatus: 0,
			lessorBonus: 100,
			contractType: 1,
			isHasHouse: 1,
			authenticationStatus: 0,
			contractTypeStatus: 1,
			extend: "20",
			isFailToplimit: 0,
			showContractType: 1,
			rent: 2589,
			total: 5178,
			signMonth: 1,
			payStatus: 0,
			payWay: 0,
			isNotice: false
		}]
	}
}

```

### 交易列表 (B端)
##### 接口:/SignController/contractList
##### 请求方式:GET
|参数名|类型|描述|是否必须|
|---|---|---|---|
|type|int|0线上签约 1线下签约  2签订中|是|
##### 成功返回值
```
{
	ret: 200,
	data: {
		list: [{
			id: 6329,
			communityName: "白纸坊桥",
			address: "门萨排比唉",
			rentPrice: 2589,
			deposit: 2685,
			payment: "押一付一",
			startTime: 1534262400000,
			endTime: 1565712000000,
			lessor: {
				id: 6415,
				userId: 555583,
				name: "张振东",
				certNo: "410782199206254736",
				mobile: "18401657466",
				type: "LESSOR",
				contractId: 6329,
				gender: 3
			},
			lessee: {
				id: 6414,
				userId: 13365,
				name: "付森",
				certNo: "131182199203043416",
				mobile: "13021021262",
				type: "LESSEE",
				contractId: 6329,
				avatar: "http://test-1251500528.file.myqcloud.com/hzpd94b0855-4bf8-49c6-ba2a-2666b6edaa32.jpg",
				gender: 2,
				nickname: "包子"
			},
			status: "已签订",
			isDeposit: false,
			url: "http://hzp.caidingke.net/sign/detail?id=6329&pf=WEB&cityId=1&ver=null",
			effectDate: 1534651200166,
			expiredDate: 1566100800166,
			amount: 2685,
			premium: 0.01,
			premiumOri: 299,
			supplement: "",
			overdue: 1534389918000,
			house: {
				id: 31036,
				rent: 699,
				readyTime: 1534176000000,
				room: 1,
				parlor: 1,
				payment: "2",
				rentType: "1",
				communityId: 1085882,
				buildArea: 500,
				cityId: 1,
				areaId: 1141,
				businessAreaId: 5835,
				lon: 116.355769,
				lat: 39.883297,
				listImageUrl: "http://test-1251500528.file.myqcloud.com/hzpcb005ae6-3675-4c93-9266-2184191722d1.jpg",
				status: 4,
				createTime: 1534216719236,
				nearbySubways: "1101595,1101598,1555.0;1101595,1101597,1895.0",
				userId: 555583,
				pictureCount: 3,
				communityName: "白纸坊桥",
				areaName: "宣武",
				businessAreaName: "白纸坊",
				updateTime: 1534216719236,
				ip: "106.39.84.154",
				hasWIFI: false,
				hasFridge: false,
				hasAirConditioning: false,
				hasWasher: true,
				hasToilet: false,
				hasShower: false,
				hasHeating: false,
				hasGas: false,
				hasWardrobe: true,
				hasKitchen: false,
				hasTV: false,
				hasSofa: false,
				hasBalcony: true,
				hasElevator: false,
				hasBed: true,
				description: "446464644466464646468756464664",
				subwayName: "7号线 7号线",
				signedTime: 1534303683219,
				identity: 5,
				toiletCount: 1,
				subwayStationName: "广安门内 达官营",
				contractPlan: false,
				isApartment: false
			},
			lessorUser: {
				id: 555583,
				nickname: "P53392",
				nicknameModified: false,
				avatar: "http://test-1251500528.file.myqcloud.com/hzp17276f12-6413-449f-8897-d9b3396f1187.jpg",
				avatarModified: false,
				gender: 3,
				genderModified: false,
				mobileNumber: "18401657466",
				ageLabel: 0,
				pushToken: "AneAA6239h7SuXbOQW_iouV7plSYiDMaApfggmy7l5mb",
				pf: "android",
				career: "小宝贝",
				personalProfile: "我去拯救地球了...",
				zmScore: 0,
				zmAuth: false,
				background: "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
				zmAuthPushed: false,
				infoCompleted: false,
				flag: false,
				privacy: 0,
				forbidden: false,
				virtual: false,
				subscribe: false,
				isForeign: false,
				isAdministrators: true,
				apartmentName: "租趣科技有限公司",
				apartmentCityId: 1,
				administratorStatus: 2,
				realName: "张振东",
				certNo: "410782199206254736",
				isScanCode: false,
				subscribeFwh: false,
				invitationCode: "HEZUQU17487F623F",
				invited: false,
				apartmentId: 1,
				brand: "租趣公寓",
				isFacePerception: true,
				authenticationStatus: 1,
				source: 2
			},
			lesseeUser: {
				id: 13365,
				nickname: "包子",
				nicknameModified: true,
				avatar: "http://test-1251500528.file.myqcloud.com/hzpd94b0855-4bf8-49c6-ba2a-2666b6edaa32.jpg",
				avatarModified: true,
				gender: 2,
				genderModified: true,
				mobileNumber: "13021021262",
				ageLabel: 5,
				birthday: "07-31",
				pushToken: "Aoi23MV2l6kBT27z4CoBmiCz4xnMkDtrCibYhVFJsOQY",
				pf: "android",
				career: "法律",
				personalProfile: "我去拯救地球了...",
				zmScore: 0,
				zmAuth: false,
				constellation: "狮子座",
				background: "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
				zmAuthPushed: false,
				infoCompleted: true,
				flag: false,
				privacy: 0,
				forbidden: false,
				virtual: false,
				subscribe: false,
				isForeign: false,
				isAdministrators: false,
				administratorStatus: 0,
				realName: "石景梅",
				certNo: "372928198812188529",
				isScanCode: false,
				subscribeFwh: false,
				invitationCode: "HEZUQU1748771C35",
				invited: false,
				isFacePerception: false,
				authenticationStatus: 1
			},
			lessorPromotionStatus: 0,
			lessorBonus: 100,
			contractType: 1,
			isHasHouse: 1,
			authenticationStatus: 0,
			contractTypeStatus: 1,
			extend: "20",
			isFailToplimit: 0,
			showContractType: 1,
			rent: 2589,
			total: 5178,
			signMonth: 1,
			payStatus: 0,
			payWay: 0,
			isNotice: false
		}]
	}
}

```

### 租金打折
##### 接口:/SignController/rentDiscount
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|id|long|交易id|是|
|rent|double|打折之后租金|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}

```

### 交易拒绝接口
##### 接口:/SignController/refuseSign
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|id|long|交易id|是|
|reason|String|拒绝原因|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}

```

### 获取用户未读push消息 
##### 接口:/UserController/getUnreadPush
##### 请求方式:POST

##### 成功返回值
```
{
	ret: 200,
	data: {
		matchUnicast: { 匹配通知未读信息最新
			id: 54,
			userId: 555583,
			title: "合租派",
			text: "(T＿T)您发布的求租信息因图片不符合规范，未通过审核，现在前往修改可立即发布喔！",
			pushTime: 1522229524625,
			goType: "matching",
			status: 0,
			houseRequestIds ：12,34
			unReadCount  ：1  未读信息数量
		}，
		accountUnicast: { 到账通知未读信息最新
			id: 53,
			userId: 555583,
			title: "合租派",
			text: "(T＿T)您发布的求租信息因图片不符合规范，未通过审核，现在前往修改可立即发布喔！",
			pushTime: 1522229524625,
			goType: "rent",
            type : 1 1租金 2奖励
			status: 0,
			unReadCount  ：1  未读信息数量
		}
	}
}

```

### banner
##### 接口:/Application/administratorsBanners
##### 请求方式:GET

##### 成功返回值
```
{
  "ret": 200,
  "data": [
    {
      "bannerPictureUrl": "http://prod-1251500528.file.myqcloud.com/resource/biyeji-banner.jpg",
      "bannerRedirectUrl": "yajinxian"
    }
  ]
}
```
### push消息已读接口
##### 接口:/UserController/readPush
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|goType|String|push类型|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}

```

### 是否可以发送求合租 
##### 接口:/UserController/checkRecommend
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|ids|String|用户ids 逗号隔开|是|
|houseId|long|房源id|是|	
##### 成功返回值
```
{
	ret: 200,
	data: {
		msg: "只可以推荐2次哦",
		ids: [
			1,
			2
		],
		house: {
			id: 71,
			rent: 6900,
			readyTime: 1,
			room: 3,
			parlor: 1,
			payment: "2",
			rentType: "1",
			communityId: 270,
			buildArea: 138,
			cityId: 1,
			areaId: 1142,
			businessAreaId: 11367,
			lon: 116.569578,
			lat: 39.911007,
			listImageUrl: "http://test-1251500528.file.myqcloud.com/hzp/47727F61-22B3-4D64-ACEF-FCC5FA343373.jpg",
			status: 2,
			createTime: 1525942570645,
			nearbySubways: "236715,236833,841.0;236715,236834,1294.0",
			userId: 155,
			pictureCount: 1,
			violationReason: "",
			outTime: 1525942592683,
			communityName: "艺水芳园",
			areaName: "朝阳",
			businessAreaName: "双桥",
			updateTime: 1525942595244,
			ip: "10.141.159.122",
			hasWIFI: false,
			hasFridge: false,
			hasAirConditioning: false,
			hasWasher: false,
			hasToilet: false,
			hasShower: false,
			hasHeating: false,
			hasGas: false,
			hasWardrobe: false,
			hasKitchen: false,
			hasTV: false,
			hasSofa: false,
			hasBalcony: false,
			hasElevator: false,
			hasBed: true,
			description: "哈哈哈萨拉了垮了肉木木木木木木不了肉木木木木木木木木哦阿塔帕肉木木木木木木阿塔帕哈哈 set 多头父母呃拉萨怕热透福福福福福福福",
			subwayName: "八通线 八通线",
			identity: 1,
			toiletCount: 1,
			subwayStationName: "传媒大学 双桥",
			contractPlan: false,
			isApartment: false
		}
	}
}
```

### 发送求合租 成功
##### 接口:/UserController/recommendSuccess
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|ids|String|用户ids 逗号隔开|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}

```

### 获取push列表
##### 接口:/UserController/getPushList
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|goType|String|push类型 matching 租户匹配 account 到账通知|是|
|page|int|当前页数|是|	
|pageSize|int|每页数据|是|	
##### 成功返回值
```
{
	ret: 200,
	data: [{
		id: 54,
		userId: 555741,
		title: "合租派",
		text: "(T＿T)您发布的求租信息因图片不符合规范，未通过审核，现在前往修改可立即发布喔！",
		pushTime: 1522229524625,
		goType: "matching",
		status: 0,
		houseRequestIds: "51",
		houseId: 0,
		orderId: 0,
		contractId: 0,
		senderId: 0,
		money: 0,
        type:0,
		avatars: [
			"http://test-1251500528.file.myqcloud.com/hzp/060d1555d20b62bfbd3b73e38670814945"
		],
        gender: [
			1
		],
        communityName : 小西,
        picUrl : http://prod-1251500528.file.myqcloud.com/resource/money_source_1.png,
        url : http://hzp.caidingke.net/ApartmentH5Controller/apartmentBillInfor?orderId=52;
		tips : 租金1255元
        send  : 付款方：xiaxoa
        receive : 收款账户:个人账户
	}]
}

```

### 根据ids获取求租列表
##### 接口:/HouseRequestController/getHouseRequestByIds
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|ids|String|用户ids 逗号隔开|是|

##### 成功返回值
```
{
	ret: 200,
	data: [{
		id: 51,
		description: "哈哈哈应该是没有问题了，违规后再次发房源哦哦哦哦哦哦看了看自己",
		expectedLocation: "1206 5994 16082 6828",
		expectedLocations: "酒仙桥 奥林匹克公园 学院路北 亚运村小营",
		expectedAreas: "1142 1142 1143 1142",
		expectedAreaNames: "朝阳 朝阳 海淀 朝阳",
		expectedTime: 1,
		startRent: 100,
		endRent: 5100,
		cityId: 1,
		status: 2,
		createTime: 1525935304993,
		userId: 147,
		violationReason: "",
		outTime: 1528790850744,
		updateTime: 1528797727487,
		pictureCount: 1,
		listImageUrl: "http://test-1251500528.file.myqcloud.com/hzp/8ae947190f64a41cd69a1732f79f985145",
		expectedSubwayStationId: "",
		expectedSubwayId: "",
		user: {
			id: 147,
			nickname: "西瓜的人都就",
			nicknameModified: true,
			avatar: "http://test-1251500528.file.myqcloud.com/hzp/060d1555d20b62bfbd3b73e38670814945",
			avatarModified: true,
			gender: 1,
			genderModified: true,
			mobileNumber: "17611265966",
			ageLabel: 5,
			birthday: "12-01",
			openId: "ob2_D06cjM68I9ofCUP1Afo5-syI",
			unionId: "",
			pf: "WEB",
			career: "房地产",
			favorite: "美食,旅游",
			personalProfile: "没有签名才个性。咯路",
			zmScore: 0,
			zmAuth: false,
			constellation: "射手座",
			background: "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
			zmAuthPushed: true,
			infoCompleted: true,
			flag: false,
			privacy: 1,
			forbidden: false,
			virtual: false,
			mpOpenId: "oOKCt4piIMT0cRzKWk-IbpS-ucSQ",
			subscribe: true,
			isForeign: false,
			isAdministrators: false,
			administratorStatus: 0,
			isScanCode: true,
			subscribeFwh: false,
			invitationCode: "HEZUQU174876E893",
			invited: true,
			isFacePerception: false,
			authenticationStatus: 0
		}
	}]
}

```
### 短信通知租户 线上支付
##### 接口:/SignController/notifyPay
##### 请求方式:POST
|参数名|类型|描述|是否必须|
|---|---|---|---|
|id|long|合同id|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": {}
}

```

### B端升级
##### 接口:/ProfileController/bVersion
##### 请求方式:GET
|参数名|类型|描述|是否必须|
|---|---|---|---|
|type|String|IOS,ANDROID|是|

##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "id": 3,
    "type": "IOS",
    "forceUpgrade": false,
    "downloadPath","",
    "forceUpgrade","",
    "tips","",
    "version",""
  }
}

```

## 女性专区
### 创建陪同看房并返回支付签名
##### 接口:/Miss/escort
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|type|String|COME-来看房，GO-去看房|是|
|communityId|Long|小区id|是|
|address|String|地址|是|
|planTime|Long|看房时间|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "returnCode": "SUCCESS",
    "returnMsg": "OK",
    "appId": "wxa91cf5dabed99eec",
    "mchId": "1496204652",
    "nonceStr": "PfUXChQHCFESciJaTIXhgJgfZgSiYGNI",
    "sign": "BCA6F4CB54C8D5FD75A201558F0BABB6",
    "resultCode": "SUCCESS",
    "serviceId": 4,//陪同看房id
    "tradeType": "APP",
    "prepayId": "wx11125806279955d259cb0da80199546316",
    "packageValue": "Sign=WXPay",
    "timestamp": "1536641886"
  }
}
```

### 陪同看房详情
##### 接口:/Miss/escortDetail
##### 请求方式:GET
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|id|Long|/Miss/escort返回的serviceId|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "id": 3,
    "type": "COME",//COME-来看房，GO-去看房
    "createTime": 1536637048905,//创建时间
    "communityId": 13,
    "communityName": "远洋山水北区",
    "address": "address",
    "planTime": 0,//看房时间
    "contact": "18514030307",//联系方式
    "orderId": 411,
    "userId": 555993,
    "status": "ONGOING",//ONGOING为等待看房，FINISHED为看房结束
    "depositStatus": "RETURNED",//status=FINISHED时有值，RETURNED-归还押金，NOT_RETURNED-不归还
    "reason": "xxxx",//不退押金的时候有值
    "escortAmount": 0.01,//押金金额
    "orderStatus": "_2"//_0-未支付，_1-已提交第三方，_2-支付成功
  }
}
```

### 陪同看房列表
##### 接口:/Miss/escortList
##### 请求方式:GET
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|page|Integer|page,从1开始|是|
|pageSize|Integer|pageSize，默认20|否|
##### 成功返回值
```
{
  "ret": 200,
  "data": [
    {
      "id": 3,
      "type": "COME",//COME-来看房，GO-去看房
      "createTime": 1536637048905,
      "communityId": 13,
      "communityName": "远洋山水北区",
      "address": "address",
      "planTime": 0,//看房时间
      "contact": "18514030307",//联系方式
      "orderId": 411,
      "status": "ONGOING",//ONGOING为等待看房，FINISHED未看房结束
    "depositStatus": "RETURNED",//status=FINISHED时有值，RETURNED-归还押金，NOT_RETURNED-不归还
      "userId": 555993
    },
    {
      "id": 2,
      "type": "COME",
      "createTime": 1536636980126,
      "communityId": 13,
      "communityName": "远洋山水北区",
      "address": "address",
      "planTime": 0,
      "contact": "18514030307",
      "orderId": 410,
      "status": "ONGOING",//ONGOING为等待看房，FINISHED未看房结束
      "depositStatus": "RETURNED",//status=FINISHED时有值，RETURNED-归还押金，NOT_RETURNED-不归还
      "userId": 555993
    }
  ]
}
```

### 认证状态
##### 接口:/UserController/missAuthStatus
##### 请求方式:GET
##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "authenticated": true,//true已认证，false未认证
    "canAuth": false//true可以认证，false不可以认证
  }
}
```

### 所有省份
##### 接口:/LocationController/provincesAll
##### 请求方式:GET
##### 成功返回值
```
{
  "ret": 200,
  "data": [
    {
      "isNew": false,
      "id": 28,
      "name": "北京",
      "initial": "B",
      "open": true,
      "sortOrder": 1,
      "new": false
    },
    {
      "isNew": false,
      "id": 29,
      "name": "上海",
      "initial": "S",
      "open": true,
      "sortOrder": 2,
      "new": false
    },
    {
      "isNew": false,
      "id": 30,
      "name": "天津",
      "initial": "T",
      "open": true,
      "sortOrder": 3,
      "new": false
    },
    {
      "isNew": false,
      "id": 31,
      "name": "重庆",
      "initial": "C",
      "open": true,
      "sortOrder": 4,
      "new": false
    },
    {
      "isNew": false,
      "id": 1,
      "name": "安徽",
      "initial": "A",
      "open": true,
      "sortOrder": 99999,
      "new": false
    },
    {
      "isNew": false,
      "id": 2,
      "name": "福建",
      "initial": "F",
      "open": true,
      "sortOrder": 99999,
      "new": false
    },
    {
      "isNew": false,
      "id": 3,
      "name": "广东",
      "initial": "G",
      "open": true,
      "sortOrder": 99999,
      "new": false
    },
    {
      "isNew": false,
      "id": 5,
      "name": "贵州",
      "initial": "G",
      "open": true,
      "sortOrder": 99999,
      "new": false
    },
    {
      "isNew": false,
      "id": 8,
      "name": "河南",
      "initial": "H",
      "open": true,
      "sortOrder": 99999,
      "new": false
    },
    {
      "isNew": false,
      "id": 10,
      "name": "湖北",
      "initial": "H",
      "open": true,
      "sortOrder": 99999,
      "new": false
    },
    {
      "isNew": false,
      "id": 11,
      "name": "湖南",
      "initial": "H",
      "open": true,
      "sortOrder": 99999,
      "new": false
    },
    {
      "isNew": false,
      "id": 12,
      "name": "河北",
      "initial": "H",
      "open": true,
      "sortOrder": 99999,
      "new": false
    },
    {
      "isNew": false,
      "id": 13,
      "name": "江苏",
      "initial": "J",
      "open": true,
      "sortOrder": 99999,
      "new": false
    },
    {
      "isNew": false,
      "id": 20,
      "name": "山东",
      "initial": "S",
      "open": true,
      "sortOrder": 99999,
      "new": false
    },
    {
      "isNew": false,
      "id": 22,
      "name": "陕西",
      "initial": "S",
      "open": true,
      "sortOrder": 99999,
      "new": false
    },
    {
      "isNew": false,
      "id": 23,
      "name": "四川",
      "initial": "S",
      "open": true,
      "sortOrder": 99999,
      "new": false
    },
    {
      "isNew": false,
      "id": 26,
      "name": "云南",
      "initial": "Y",
      "open": true,
      "sortOrder": 99999,
      "new": false
    },
    {
      "isNew": false,
      "id": 27,
      "name": "浙江",
      "initial": "Z",
      "open": true,
      "sortOrder": 99999,
      "new": false
    },
    {
      "isNew": false,
      "id": 33,
      "name": "澳门",
      "initial": "A",
      "open": false,
      "sortOrder": 99999,
      "new": false
    },
    {
      "isNew": false,
      "id": 4,
      "name": "广西",
      "initial": "G",
      "open": false,
      "sortOrder": 99999,
      "new": false
    },
    {
      "isNew": false,
      "id": 6,
      "name": "甘肃",
      "initial": "G",
      "open": false,
      "sortOrder": 99999,
      "new": false
    },
    {
      "isNew": false,
      "id": 7,
      "name": "海南",
      "initial": "H",
      "open": false,
      "sortOrder": 99999,
      "new": false
    },
    {
      "isNew": false,
      "id": 9,
      "name": "黑龙江",
      "initial": "H",
      "open": false,
      "sortOrder": 99999,
      "new": false
    },
    {
      "isNew": false,
      "id": 14,
      "name": "江西",
      "initial": "J",
      "open": false,
      "sortOrder": 99999,
      "new": false
    },
    {
      "isNew": false,
      "id": 15,
      "name": "吉林",
      "initial": "J",
      "open": false,
      "sortOrder": 99999,
      "new": false
    },
    {
      "isNew": false,
      "id": 16,
      "name": "辽宁",
      "initial": "L",
      "open": false,
      "sortOrder": 99999,
      "new": false
    },
    {
      "isNew": false,
      "id": 17,
      "name": "宁夏",
      "initial": "N",
      "open": false,
      "sortOrder": 99999,
      "new": false
    },
    {
      "isNew": false,
      "id": 18,
      "name": "内蒙古",
      "initial": "N",
      "open": false,
      "sortOrder": 99999,
      "new": false
    },
    {
      "isNew": false,
      "id": 19,
      "name": "青海",
      "initial": "Q",
      "open": false,
      "sortOrder": 99999,
      "new": false
    },
    {
      "isNew": false,
      "id": 21,
      "name": "山西",
      "initial": "S",
      "open": false,
      "sortOrder": 99999,
      "new": false
    },
    {
      "isNew": false,
      "id": 34,
      "name": "台湾",
      "initial": "T",
      "open": false,
      "sortOrder": 99999,
      "new": false
    },
    {
      "isNew": false,
      "id": 24,
      "name": "新疆",
      "initial": "X",
      "open": false,
      "sortOrder": 99999,
      "new": false
    },
    {
      "isNew": false,
      "id": 25,
      "name": "西藏",
      "initial": "X",
      "open": false,
      "sortOrder": 99999,
      "new": false
    },
    {
      "isNew": false,
      "id": 32,
      "name": "香港",
      "initial": "X",
      "open": false,
      "sortOrder": 99999,
      "new": false
    }
  ]
}

```

### 根据身份ID查找城市
##### 接口:/LocationController/getCitiesAllByProvinceId
##### 请求方式:GET
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|provinceId|Long|省份ID|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": [
    {
      "isNew": false,
      "id": 740,
      "name": "太原",
      "listName": "taiyuan",
      "open": 0,
      "hot": false,
      "provinceId": 21,
      "new": false
    },
    {
      "isNew": false,
      "id": 3222,
      "name": "吕梁",
      "listName": "lvliang",
      "open": 0,
      "hot": false,
      "provinceId": 21,
      "new": false
    },
    {
      "isNew": false,
      "id": 3350,
      "name": "晋城",
      "listName": "jincheng",
      "open": 0,
      "hot": false,
      "provinceId": 21,
      "new": false
    },
    {
      "isNew": false,
      "id": 3453,
      "name": "忻州",
      "listName": "xinzhou",
      "open": 0,
      "hot": false,
      "provinceId": 21,
      "new": false
    },
    {
      "isNew": false,
      "id": 5653,
      "name": "运城",
      "listName": "yuncheng",
      "open": 0,
      "hot": false,
      "provinceId": 21,
      "new": false
    },
    {
      "isNew": false,
      "id": 5669,
      "name": "临汾",
      "listName": "linfen",
      "open": 0,
      "hot": false,
      "provinceId": 21,
      "new": false
    },
    {
      "isNew": false,
      "id": 6921,
      "name": "长治",
      "listName": "zhangzhi",
      "open": 0,
      "hot": false,
      "provinceId": 21,
      "new": false
    },
    {
      "isNew": false,
      "id": 6964,
      "name": "大同",
      "listName": "datong",
      "open": 0,
      "hot": false,
      "provinceId": 21,
      "new": false
    },
    {
      "isNew": false,
      "id": 8760,
      "name": "阳泉",
      "listName": "yangquan",
      "open": 0,
      "hot": false,
      "provinceId": 21,
      "new": false
    },
    {
      "isNew": false,
      "id": 8854,
      "name": "晋中",
      "listName": "jinzhong",
      "open": 0,
      "hot": false,
      "provinceId": 21,
      "new": false
    },
    {
      "isNew": false,
      "id": 9193,
      "name": "临猗",
      "listName": "linyi",
      "open": 0,
      "hot": false,
      "provinceId": 21,
      "new": false
    },
    {
      "isNew": false,
      "id": 9871,
      "name": "朔州",
      "listName": "shuozhou",
      "open": 0,
      "hot": false,
      "provinceId": 21,
      "new": false
    },
    {
      "isNew": false,
      "id": 10908,
      "name": "清徐",
      "listName": "qingxu",
      "open": 0,
      "hot": false,
      "provinceId": 21,
      "new": false
    }
  ]
}

```
### 根据name模糊匹配学校
##### 接口:/LocationController/schoolByName
##### 请求方式:GET
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|name|String|name|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": [
    {
      "isNew": false,
      "id": 5398,
      "name": "电子科技大学",
      "provinceId": 23,
      "new": false
    },
    {
      "isNew": false,
      "id": 5411,
      "name": "西安电子科技大学",
      "provinceId": 22,
      "new": false
    },
    {
      "isNew": false,
      "id": 5468,
      "name": "杭州电子科技大学",
      "provinceId": 27,
      "new": false
    },
    {
      "isNew": false,
      "id": 5551,
      "name": "桂林电子科技大学",
      "provinceId": 4,
      "new": false
    },
    {
      "isNew": false,
      "id": 6060,
      "name": "北京电子科技学院",
      "provinceId": 28,
      "new": false
    },
    {
      "isNew": false,
      "id": 6152,
      "name": "贵州电子科技职业学院",
      "provinceId": 5,
      "new": false
    },
    {
      "isNew": false,
      "id": 6225,
      "name": "北京电子科技职业学院",
      "provinceId": 28,
      "new": false
    },
    {
      "isNew": false,
      "id": 6232,
      "name": "杭州电子科技大学信息工程学院",
      "provinceId": 27,
      "new": false
    },
    {
      "isNew": false,
      "id": 6333,
      "name": "电子科技大学沙河校区",
      "provinceId": 23,
      "new": false
    },
    {
      "isNew": false,
      "id": 6989,
      "name": "电子科技大学中山学院",
      "provinceId": 3,
      "new": false
    }
  ]
}
```

### 根据离开时间推荐在此时间段内发布的符合（您）的房源或者求租
##### 接口:/ProfileController/commend
##### 请求方式:POST
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|startTime|long|开始时间|是|
|endTime|long|结束时间|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "houses": [
      {
        "id": 31440,
        "rent": 2586,
        "readyTime": 1537844022730,
        "room": 1,
        "parlor": 1,
        "payment": "2",
        "rentType": "1",
        "communityId": 329,
        "buildArea": 25,
        "cityId": 1,
        "areaId": 1142,
        "businessAreaId": 1203,
        "lon": 116.489079,
        "lat": 40.005896,
        "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/A8742B32-BB04-4FB8-9B3D-D5A941A5BBFA.jpg",
        "status": 1,
        "createTime": 1537844066373,
        "nearbySubways": "572986,573111,1088.0;677835,573111,1088.0;677835,1101619,1339.0;677835,1101618,1428.0;677835,1101620,1744.0",
        "userId": 556041,
        "pictureCount": 1,
        "communityName": "宝星国际",
        "areaName": "朝阳",
        "businessAreaName": "望京",
        "updateTime": 1537844066373,
        "ip": "210.12.116.196",
        "hasWIFI": false,
        "hasFridge": true,
        "hasAirConditioning": false,
        "hasWasher": false,
        "hasToilet": false,
        "hasShower": false,
        "hasHeating": true,
        "hasGas": false,
        "hasWardrobe": false,
        "hasKitchen": false,
        "hasTV": true,
        "hasSofa": false,
        "hasBalcony": false,
        "hasElevator": false,
        "hasBed": true,
        "description": "啦啦啦啦啦啦啦德玛西亚啦啦啦啦啦啦啦啦啦啦啦啦啦啦啦啦啦啦啦啦啦啦啦啦啦啦啦",
        "subwayName": "15号线 14号线 14号线 14号线 14号线",
        "identity": 1,
        "toiletCount": 1,
        "subwayStationName": "望京 望京 阜通 望京南 东湖渠",
        "contractPlan": false,
        "isApartment": false,
        "isOffline": false,
        "operateTime": 1537844066373,
        "user": {
          "id": 556041,
          "nickname": "9145",
          "nicknameModified": true,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzp/178D787C-F742-4BC2-B2DD-C6980BBB7951.jpg",
          "avatarModified": true,
          "gender": 2,
          "genderModified": true,
          "mobileNumber": "15611869145",
          "ageLabel": 3,
          "birthday": "09-18",
          "pushToken": "84ee058beb1b24efb4616b1c482cd67d448dc778116be4f6cac6bf2fc9873c9c",
          "pf": "iOS",
          "career": "公关市场",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "处女座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": true,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU17487F6409",
          "invited": false,
          "authenticationStatus": 0,
          "migrate": 0,
          "isLogin": true
        }
      },
      {
        "id": 66,
        "rent": 3500,
        "readyTime": 1,
        "room": 1,
        "parlor": 1,
        "payment": "5",
        "rentType": "1",
        "communityId": 8182,
        "buildArea": 25,
        "cityId": 1,
        "areaId": 1142,
        "businessAreaId": 1203,
        "lon": 116.476415,
        "lat": 39.992226,
        "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/d8d3c986d53cec76d4da4dcf44516bf6.jpg",
        "status": 1,
        "createTime": 1525923890862,
        "nearbySubways": "677835,1101619,629.0;677835,1101618,648.0;572986,573111,1318.0;677835,573111,1318.0;677835,1101617,1615.0",
        "userId": 147,
        "pictureCount": 1,
        "violationReason": "",
        "outTime": 1532516967713,
        "communityName": "望京大厦",
        "areaName": "朝阳",
        "businessAreaName": "望京",
        "updateTime": 1532516973570,
        "ip": "10.141.159.122",
        "hasWIFI": false,
        "hasFridge": false,
        "hasAirConditioning": false,
        "hasWasher": true,
        "hasToilet": false,
        "hasShower": false,
        "hasHeating": true,
        "hasGas": true,
        "hasWardrobe": true,
        "hasKitchen": true,
        "hasTV": false,
        "hasSofa": false,
        "hasBalcony": true,
        "hasElevator": false,
        "hasBed": true,
        "description": "防横波，很好很大很宽敞，明亮整洁干净利落？？？？？？？？。。。嗯哼哈哈家里",
        "subwayName": "14号线 14号线 15号线 14号线 14号线",
        "identity": 1,
        "toiletCount": 1,
        "subwayStationName": "阜通 望京南 望京 望京 高家园",
        "contractPlan": false,
        "isApartment": false,
        "isOffline": false,
        "operateTime": 0,
        "user": {
          "id": 147,
          "nickname": "西瓜的人都就",
          "nicknameModified": true,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzp/060d1555d20b62bfbd3b73e38670814945",
          "avatarModified": true,
          "gender": 1,
          "genderModified": true,
          "mobileNumber": "17611265966",
          "ageLabel": 5,
          "birthday": "12-01",
          "openId": "ob2_D06cjM68I9ofCUP1Afo5-syI",
          "unionId": "",
          "pf": "WEB",
          "career": "房地产",
          "favorite": "美食,旅游",
          "personalProfile": "没有签名才个性。咯路",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "射手座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": true,
          "infoCompleted": true,
          "flag": false,
          "privacy": 1,
          "forbidden": false,
          "virtual": false,
          "mpOpenId": "oOKCt4piIMT0cRzKWk-IbpS-ucSQ",
          "subscribe": true,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": true,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU174876E893",
          "invited": true,
          "isFacePerception": false,
          "authenticationStatus": 0,
          "migrate": 0,
          "isLogin": false
        }
      },
      {
        "id": 31203,
        "rent": 6000,
        "readyTime": 1534327478582,
        "room": 1,
        "parlor": 1,
        "payment": "2",
        "rentType": "1",
        "communityId": 379643,
        "buildArea": 50,
        "cityId": 1,
        "areaId": 1142,
        "businessAreaId": 1203,
        "lon": 116.487544,
        "lat": 40.005106,
        "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/6A8EC1AA-A5CD-4FF3-BD6B-F6BE2747A28A.jpg",
        "status": 1,
        "createTime": 1534327548238,
        "nearbySubways": "572986,573111,945.0;677835,573111,945.0;677835,1101619,1183.0;677835,1101618,1307.0;677835,1101620,1710.0",
        "userId": 555744,
        "pictureCount": 1,
        "outTime": 1534328306307,
        "communityName": "宝星华庭",
        "areaName": "朝阳",
        "businessAreaName": "望京",
        "updateTime": 1534500571990,
        "ip": "210.12.116.196",
        "hasWIFI": false,
        "hasFridge": true,
        "hasAirConditioning": false,
        "hasWasher": false,
        "hasToilet": false,
        "hasShower": false,
        "hasHeating": true,
        "hasGas": false,
        "hasWardrobe": false,
        "hasKitchen": false,
        "hasTV": true,
        "hasSofa": false,
        "hasBalcony": false,
        "hasElevator": false,
        "hasBed": true,
        "description": "记录记录了，给外婆哦去Pro哦搜狗像我这种",
        "subwayName": "15号线 14号线 14号线 14号线 14号线",
        "identity": 5,
        "toiletCount": 1,
        "subwayStationName": "望京 望京 阜通 望京南 东湖渠",
        "contractPlan": false,
        "isApartment": true,
        "isOffline": false,
        "operateTime": 0,
        "user": {
          "id": 555744,
          "nickname": "P82430",
          "nicknameModified": false,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzp214b2312-ed5b-4dc9-83de-53c4e56dde7d.jpg",
          "avatarModified": true,
          "gender": 3,
          "genderModified": false,
          "mobileNumber": "15611118958",
          "ageLabel": 0,
          "pushToken": "53297dfa73c7a059aaf27f44327be14325a08e1d76ef3c89553c0cfae843559c",
          "pf": "iOS",
          "career": "卖萌的",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": true,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": true,
          "apartmentName": "自如皇家公司",
          "apartmentCityId": 1,
          "administratorStatus": 2,
          "verifyTime": 1534327092291,
          "realName": "",
          "certNo": "",
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU17487F62E0",
          "invited": false,
          "apartmentId": 11005,
          "brand": "自如管家",
          "isFacePerception": true,
          "authenticationStatus": 0,
          "source": 2,
          "migrate": 0,
          "isLogin": false
        }
      },
      {
        "id": 50,
        "rent": 5000,
        "readyTime": 1,
        "room": 1,
        "parlor": 1,
        "payment": "1",
        "rentType": "1",
        "communityId": 8182,
        "buildArea": 100,
        "cityId": 1,
        "areaId": 1142,
        "businessAreaId": 1203,
        "lon": 116.476415,
        "lat": 39.992226,
        "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/489986aee99a303e893a251bf0aa2dfb.png",
        "status": 2,
        "createTime": 1524554993362,
        "userId": 122,
        "pictureCount": 1,
        "violationReason": "",
        "outTime": 1525418564270,
        "communityName": "望京大厦",
        "areaName": "朝阳",
        "businessAreaName": "望京",
        "updateTime": 1525426112162,
        "ip": "10.141.159.122",
        "hasWIFI": false,
        "hasFridge": false,
        "hasAirConditioning": false,
        "hasWasher": false,
        "hasToilet": true,
        "hasShower": false,
        "hasHeating": true,
        "hasGas": false,
        "hasWardrobe": false,
        "hasKitchen": false,
        "hasTV": true,
        "hasSofa": false,
        "hasBalcony": false,
        "hasElevator": false,
        "hasBed": true,
        "description": "交通特别好啊啊啊啊啊啊啊啊哈哈哈哈哈哈哈",
        "subwayName": "14号线 14号线 15号线 14号线 14号线",
        "toiletCount": 1,
        "subwayStationName": "阜通 望京南 望京 望京 高家园",
        "contractPlan": false,
        "isApartment": false,
        "isOffline": false,
        "operateTime": 0,
        "user": {
          "id": 122,
          "nickname": "婷",
          "nicknameModified": true,
          "avatar": "https://wx.qlogo.cn/mmopen/vi_32/Q0j4TwGTfTKoVicJa9T7Ct7CkrC2cDnd0tUfJnbxhA6AJysLll1WHvxtOl4iceic4HO5YHKv142Krg8PoMzqAahEw/0",
          "avatarModified": true,
          "gender": 2,
          "genderModified": true,
          "mobileNumber": "15834102126",
          "ageLabel": 3,
          "birthday": "02-01",
          "pf": "WEB",
          "career": "码农",
          "favorite": "美食,旅游,电影",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "水瓶座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": true,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU174876E87A",
          "invited": false,
          "isFacePerception": false,
          "authenticationStatus": 0,
          "migrate": 0,
          "isLogin": false
        }
      },
      {
        "id": 16241,
        "rent": 1500,
        "readyTime": 1529942400000,
        "room": 1,
        "parlor": 1,
        "payment": "2",
        "rentType": "1",
        "communityId": 379949,
        "buildArea": 15,
        "cityId": 1,
        "areaId": 1142,
        "businessAreaId": 1203,
        "lon": 116.484439,
        "lat": 40.002867,
        "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp2f8f212e-0c53-447e-a2a8-239c53b96788.jpg",
        "status": 1,
        "createTime": 1530004001623,
        "nearbySubways": "572986,573111,686.0;677835,573111,686.0;677835,1101619,820.0;677835,1101618,1019.0;677835,1101620,1745.0;677835,1101617,1946.0",
        "userId": 13260,
        "pictureCount": 3,
        "communityName": "合生麒麟社",
        "areaName": "朝阳",
        "businessAreaName": "望京",
        "updateTime": 1530004001623,
        "ip": "10.141.159.122",
        "hasWIFI": false,
        "hasFridge": false,
        "hasAirConditioning": false,
        "hasWasher": false,
        "hasToilet": false,
        "hasShower": true,
        "hasHeating": false,
        "hasGas": true,
        "hasWardrobe": true,
        "hasKitchen": false,
        "hasTV": false,
        "hasSofa": false,
        "hasBalcony": false,
        "hasElevator": false,
        "hasBed": true,
        "description": "哈哈哈哈哈啊哈哈哈哈哈哈哈哈哈哈唉唉唉拆拆拆啊哈哈哈",
        "subwayName": "15号线 14号线 14号线 14号线 14号线 14号线",
        "identity": 5,
        "toiletCount": 1,
        "subwayStationName": "望京 望京 阜通 望京南 东湖渠 高家园",
        "contractPlan": false,
        "isApartment": true,
        "isOffline": false,
        "operateTime": 0,
        "user": {
          "id": 13260,
          "nickname": "P64449",
          "nicknameModified": false,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzp5b47f028-e5da-48d3-b3bf-16772e8b18c5.jpg",
          "avatarModified": true,
          "gender": 2,
          "genderModified": true,
          "mobileNumber": "13269822572",
          "ageLabel": 0,
          "pf": "android",
          "career": "\"科学家\"",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": true,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": true,
          "apartmentName": "自如",
          "apartmentCityId": 1,
          "administratorStatus": 2,
          "verifyTime": 1530003882021,
          "realName": "哈哈",
          "certNo": "220282199309164444",
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU1748771BCC",
          "invited": false,
          "apartmentId": 11021,
          "brand": "自如",
          "isFacePerception": false,
          "authenticationStatus": 0,
          "source": 2,
          "migrate": 0,
          "isLogin": false
        }
      },
      {
        "id": 216,
        "rent": 567,
        "readyTime": 1532016000000,
        "room": 1,
        "parlor": 0,
        "payment": "1",
        "rentType": "1",
        "communityId": 1102837,
        "buildArea": 545,
        "cityId": 1,
        "areaId": 1142,
        "businessAreaId": 1203,
        "lon": 116.490587,
        "lat": 39.998943,
        "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/2FE789AD-CB66-4B27-A5F9-1E0B01EB41B2.jpg",
        "status": 1,
        "createTime": 1529495394425,
        "nearbySubways": "677835,1101618,822.0;677835,1101619,1129.0;572986,573111,1326.0;677835,573111,1326.0;677835,1101617,1359.0",
        "userId": 224,
        "pictureCount": 1,
        "communityName": "方恒时代中心",
        "areaName": "朝阳",
        "businessAreaName": "望京",
        "updateTime": 1529495394425,
        "ip": "10.141.159.122",
        "hasWIFI": true,
        "hasFridge": true,
        "hasAirConditioning": true,
        "hasWasher": true,
        "hasToilet": false,
        "hasShower": true,
        "hasHeating": true,
        "hasGas": true,
        "hasWardrobe": true,
        "hasKitchen": true,
        "hasTV": true,
        "hasSofa": true,
        "hasBalcony": true,
        "hasElevator": true,
        "hasBed": true,
        "description": "粗福福尺寸好福福福福福福福福吃一次一次又尺寸出差一次",
        "subwayName": "14号线 14号线 15号线 14号线 14号线",
        "identity": 5,
        "toiletCount": 1,
        "subwayStationName": "望京南 阜通 望京 望京 高家园",
        "contractPlan": false,
        "isApartment": true,
        "isOffline": false,
        "operateTime": 0,
        "user": {
          "id": 224,
          "nickname": "轩轩",
          "nicknameModified": true,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzp4c91e9fc-4bd4-4711-8bd7-df348e50139d.jpg",
          "avatarModified": true,
          "gender": 1,
          "genderModified": true,
          "mobileNumber": "1300115395778",
          "ageLabel": 3,
          "birthday": "06-13",
          "pushToken": "553b7093f99a5957c838a0ec36d4bec21701d18ac858da550001e753635ab7ad",
          "pf": "iOS",
          "career": "房地产",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "双子座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": true,
          "flag": false,
          "privacy": 1,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": true,
          "apartmentName": "回龙观新村",
          "apartmentCityId": 1,
          "administratorStatus": 2,
          "verifyTime": 13001153957,
          "realName": "石景梅",
          "certNo": "372928198812188888",
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU174876E8E0",
          "invited": true,
          "apartmentId": 11018,
          "brand": "回龙观新村",
          "isFacePerception": false,
          "authenticationStatus": 0,
          "source": 2,
          "migrate": 0,
          "isLogin": false
        }
      },
      {
        "id": 31264,
        "rent": 67767,
        "readyTime": 1535731200000,
        "room": 1,
        "parlor": 1,
        "payment": "2",
        "rentType": "1",
        "communityId": 379643,
        "buildArea": 676,
        "cityId": 1,
        "areaId": 1142,
        "businessAreaId": 1203,
        "lon": 116.487544,
        "lat": 40.005106,
        "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp1a8b20af-815a-4052-8981-bbcc149d58b8.jpg",
        "status": 1,
        "createTime": 1534746185005,
        "nearbySubways": "572986,573111,945.0;677835,573111,945.0;677835,1101619,1183.0;677835,1101618,1307.0;677835,1101620,1710.0",
        "userId": 555799,
        "pictureCount": 2,
        "communityName": "宝星华庭",
        "areaName": "朝阳",
        "businessAreaName": "望京",
        "updateTime": 1534746185005,
        "ip": "210.12.116.196",
        "hasWIFI": false,
        "hasFridge": false,
        "hasAirConditioning": false,
        "hasWasher": true,
        "hasToilet": false,
        "hasShower": false,
        "hasHeating": false,
        "hasGas": false,
        "hasWardrobe": true,
        "hasKitchen": false,
        "hasTV": false,
        "hasSofa": false,
        "hasBalcony": true,
        "hasElevator": false,
        "hasBed": true,
        "description": "我是知你嘻嘻嘻嘻嘻婆婆你公公明明你你明年",
        "subwayName": "15号线 14号线 14号线 14号线 14号线",
        "identity": 1,
        "toiletCount": 1,
        "subwayStationName": "望京 望京 阜通 望京南 东湖渠",
        "contractPlan": true,
        "isApartment": false,
        "isOffline": false,
        "operateTime": 0,
        "user": {
          "id": 555799,
          "nickname": "振东最帅",
          "nicknameModified": true,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzpf02cd602-6452-47b5-a39c-8f66e5db11e3.jpg",
          "avatarModified": true,
          "gender": 1,
          "genderModified": true,
          "mobileNumber": "12165438756",
          "ageLabel": 1,
          "birthday": "08-18",
          "pf": "android",
          "career": "房地产",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "狮子座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": true,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU17487F6317",
          "invited": false,
          "authenticationStatus": 0,
          "migrate": 0,
          "isLogin": false
        }
      },
      {
        "id": 31404,
        "rent": 6000,
        "readyTime": 1536214096066,
        "room": 1,
        "parlor": 1,
        "payment": "2",
        "rentType": "1",
        "communityId": 379643,
        "buildArea": 60,
        "cityId": 1,
        "areaId": 1142,
        "businessAreaId": 1203,
        "lon": 116.487544,
        "lat": 40.005106,
        "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/094764CA-5C10-40CD-A689-D41322C9B434.jpg",
        "status": 1,
        "createTime": 1536214125537,
        "nearbySubways": "572986,573111,945.0;677835,573111,945.0;677835,1101619,1183.0;677835,1101618,1307.0;677835,1101620,1710.0",
        "userId": 555981,
        "pictureCount": 1,
        "communityName": "宝星华庭",
        "areaName": "朝阳",
        "businessAreaName": "望京",
        "updateTime": 1536214125537,
        "ip": "210.12.116.196",
        "hasWIFI": true,
        "hasFridge": false,
        "hasAirConditioning": false,
        "hasWasher": false,
        "hasToilet": false,
        "hasShower": false,
        "hasHeating": false,
        "hasGas": false,
        "hasWardrobe": false,
        "hasKitchen": false,
        "hasTV": false,
        "hasSofa": false,
        "hasBalcony": false,
        "hasElevator": false,
        "hasBed": true,
        "description": "第一个有提高明白出来后才可还行辛苦好辛苦好辛苦好想高考题做题的",
        "subwayName": "15号线 14号线 14号线 14号线 14号线",
        "identity": 5,
        "toiletCount": 1,
        "subwayStationName": "望京 望京 阜通 望京南 东湖渠",
        "contractPlan": false,
        "isApartment": true,
        "isOffline": false,
        "operateTime": 0,
        "user": {
          "id": 555981,
          "nickname": "马丽",
          "nicknameModified": false,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzp/0287A5E2-74CD-42B5-8291-9A9D5062946D.jpg",
          "avatarModified": false,
          "gender": 3,
          "genderModified": false,
          "mobileNumber": "13552416017",
          "ageLabel": 0,
          "pf": "iOS",
          "career": "",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": false,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": true,
          "apartmentName": "别使用我的公司",
          "apartmentCityId": 1,
          "administratorStatus": 2,
          "verifyTime": 1536203609343,
          "realName": "马丽",
          "certNo": "220282199309164167",
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU17487F63CD",
          "invited": false,
          "apartmentId": 11011,
          "brand": "别点击公寓",
          "isFacePerception": true,
          "authenticationStatus": 1,
          "source": 2,
          "migrate": 0,
          "isLogin": true
        }
      },
      {
        "id": 31429,
        "rent": 2000,
        "readyTime": 1536912548005,
        "room": 1,
        "parlor": 1,
        "payment": "5",
        "rentType": "1",
        "communityId": 411,
        "buildArea": 20,
        "cityId": 1,
        "areaId": 1142,
        "businessAreaId": 1203,
        "lon": 116.492461,
        "lat": 40.000407,
        "listImageUrl": "",
        "status": 2,
        "createTime": 1536912571752,
        "nearbySubways": "677835,1101618,1050.0;677835,1101619,1314.0;572986,573111,1417.0;677835,573111,1417.0;677835,1101617,1495.0",
        "userId": 555870,
        "pictureCount": 1,
        "violationReason": "",
        "communityName": "国风北京",
        "areaName": "朝阳",
        "businessAreaName": "望京",
        "updateTime": 1537512710425,
        "ip": "210.12.116.196",
        "hasWIFI": false,
        "hasFridge": false,
        "hasAirConditioning": true,
        "hasWasher": false,
        "hasToilet": false,
        "hasShower": false,
        "hasHeating": false,
        "hasGas": true,
        "hasWardrobe": false,
        "hasKitchen": false,
        "hasTV": false,
        "hasSofa": true,
        "hasBalcony": false,
        "hasElevator": false,
        "hasBed": true,
        "description": "百里killKKK卡巴啊啊啊吧唧啊啊啊吧",
        "subwayName": "14号线 14号线 15号线 14号线 14号线",
        "identity": 2,
        "toiletCount": 1,
        "subwayStationName": "望京南 阜通 望京 望京 高家园",
        "contractPlan": false,
        "isApartment": false,
        "isOffline": false,
        "operateTime": 1537522302874,
        "user": {
          "id": 555870,
          "nickname": "测试9144",
          "nicknameModified": true,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzp/BD26B58B-FCAB-45B9-B8C4-DCE360AA8477.jpg",
          "avatarModified": true,
          "gender": 2,
          "genderModified": true,
          "mobileNumber": "15611869144",
          "ageLabel": 5,
          "birthday": "08-24",
          "pf": "iOS",
          "career": "贸易销售",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "处女座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": true,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU17487F635E",
          "invited": false,
          "authenticationStatus": 0,
          "migrate": 0,
          "isLogin": true
        }
      },
      {
        "id": 28250,
        "rent": 663,
        "readyTime": 1544284800000,
        "room": 9,
        "parlor": 9,
        "payment": "5",
        "rentType": "1",
        "communityId": 10818,
        "buildArea": 336,
        "cityId": 1,
        "areaId": 1142,
        "businessAreaId": 1203,
        "lon": 116.482004,
        "lat": 40.004341,
        "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/91C8287E-6F73-44E4-B145-F2257B6FF311.jpg",
        "status": 2,
        "createTime": 1530273930000,
        "nearbySubways": "572986,573111,466.0;677835,573111,466.0;677835,1101619,823.0;677835,1101618,1191.0;677835,1101620,1499.0",
        "userId": 13261,
        "pictureCount": 12,
        "violationReason": "",
        "outTime": 1531119675579,
        "communityName": "绿荫芳邻",
        "areaName": "朝阳",
        "businessAreaName": "望京",
        "updateTime": 1531119695899,
        "ip": "10.141.159.122",
        "hasWIFI": true,
        "hasFridge": true,
        "hasAirConditioning": false,
        "hasWasher": false,
        "hasToilet": false,
        "hasShower": true,
        "hasHeating": true,
        "hasGas": false,
        "hasWardrobe": false,
        "hasKitchen": true,
        "hasTV": true,
        "hasSofa": true,
        "hasBalcony": false,
        "hasElevator": false,
        "hasBed": true,
        "description": "卡布阿库塔卡哭哭哭哭哭哭哭哭哭来咯了来接我们哦哦谢谢我一直以为自己",
        "subwayName": "15号线 14号线 14号线 14号线 14号线",
        "identity": 5,
        "toiletCount": 9,
        "subwayStationName": "望京 望京 阜通 望京南 东湖渠",
        "contractPlan": false,
        "isApartment": true,
        "isOffline": false,
        "operateTime": 0,
        "user": {
          "id": 13261,
          "nickname": "阿迪",
          "nicknameModified": true,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzp/F4F82D6A-61EB-40FF-B43C-BC5C8A91F846.jpg",
          "avatarModified": true,
          "gender": 1,
          "genderModified": true,
          "mobileNumber": "18201370426",
          "ageLabel": 2,
          "birthday": "06-29",
          "pf": "iOS",
          "career": "电子通讯",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "巨蟹座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": true,
          "flag": false,
          "privacy": 1,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": true,
          "apartmentName": "链家",
          "apartmentCityId": 1,
          "administratorStatus": 2,
          "verifyTime": 1530272291434,
          "realName": "石景梅",
          "certNo": "372928198812188888",
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU1748771BCD",
          "invited": true,
          "apartmentId": 11022,
          "brand": "链家",
          "isFacePerception": false,
          "authenticationStatus": 0,
          "source": 2,
          "migrate": 0,
          "isLogin": false
        }
      },
      {
        "id": 44,
        "rent": 6800,
        "readyTime": 1,
        "room": 2,
        "parlor": 1,
        "payment": "5",
        "rentType": "3",
        "communityId": 1389,
        "buildArea": 135,
        "cityId": 1,
        "areaId": 1142,
        "businessAreaId": 1203,
        "lon": 116.486791,
        "lat": 40.007068,
        "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/B664EA37-CAB6-4B35-96AD-02585FAA5E75.jpg",
        "status": 2,
        "createTime": 1524213992857,
        "userId": 117,
        "pictureCount": 3,
        "violationReason": "",
        "communityName": "宝星园",
        "areaName": "朝阳",
        "businessAreaName": "望京",
        "updateTime": 1524570467954,
        "ip": "10.141.159.122",
        "hasWIFI": true,
        "hasFridge": true,
        "hasAirConditioning": true,
        "hasWasher": true,
        "hasToilet": true,
        "hasShower": true,
        "hasHeating": true,
        "hasGas": true,
        "hasWardrobe": true,
        "hasKitchen": true,
        "hasTV": true,
        "hasSofa": true,
        "hasBalcony": true,
        "hasElevator": true,
        "hasBed": true,
        "description": "浮浮沉沉浮浮参加规规矩矩聚聚进步达官显贵此次鞠躬尽瘁菊花茶香港徐福吃吃吃吃吃吃成绩感到昏昏沉沉结果就聚聚",
        "subwayName": "15号线 14号线 14号线 14号线 14号线",
        "toiletCount": 1,
        "subwayStationName": "望京 望京 阜通 望京南 东湖渠",
        "contractPlan": false,
        "isApartment": false,
        "isOffline": false,
        "operateTime": 0,
        "user": {
          "id": 117,
          "nickname": "测试",
          "nicknameModified": true,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzp/63F185B4-A31B-41CE-B5AF-9DB36A41C904.jpg",
          "avatarModified": true,
          "gender": 1,
          "genderModified": true,
          "mobileNumber": "13020056947",
          "ageLabel": 3,
          "birthday": "04-18",
          "pushToken": "An-jCefuudEIBgPUwvIFmHwSJqOhp4QSr7UE42xqXEAA",
          "pf": "android",
          "career": "哈哈",
          "favorite": "工作",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "白羊座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": true,
          "infoCompleted": true,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU174876E875",
          "invited": false,
          "isFacePerception": false,
          "authenticationStatus": 0,
          "migrate": 0,
          "isLogin": false
        }
      },
      {
        "id": 122,
        "rent": 2660,
        "readyTime": 1528358369000,
        "room": 1,
        "parlor": 1,
        "payment": "2",
        "rentType": "1",
        "communityId": 379949,
        "buildArea": 25,
        "cityId": 1,
        "areaId": 1142,
        "businessAreaId": 1203,
        "lon": 116.484439,
        "lat": 40.002867,
        "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/55EF00A4-9628-4074-933E-79EBE035DF46.jpg",
        "status": 2,
        "createTime": 1528358442940,
        "nearbySubways": "572986,573111,686.0;677835,573111,686.0;677835,1101619,820.0;677835,1101618,1019.0;677835,1101620,1745.0;677835,1101617,1946.0",
        "userId": 214,
        "pictureCount": 1,
        "violationReason": "",
        "communityName": "合生麒麟社",
        "areaName": "朝阳",
        "businessAreaName": "望京",
        "updateTime": 1528358442940,
        "ip": "10.141.159.122",
        "hasWIFI": false,
        "hasFridge": false,
        "hasAirConditioning": true,
        "hasWasher": false,
        "hasToilet": false,
        "hasShower": false,
        "hasHeating": false,
        "hasGas": true,
        "hasWardrobe": false,
        "hasKitchen": false,
        "hasTV": false,
        "hasSofa": true,
        "hasBalcony": false,
        "hasElevator": false,
        "hasBed": true,
        "description": "还没有没有，我拔出来啊啊吧你还账的事都可以可以可以",
        "subwayName": "15号线 14号线 14号线 14号线 14号线 14号线",
        "identity": 1,
        "toiletCount": 1,
        "subwayStationName": "望京 望京 阜通 望京南 东湖渠 高家园",
        "contractPlan": true,
        "isApartment": false,
        "isOffline": false,
        "operateTime": 0,
        "user": {
          "id": 214,
          "nickname": "嗨呀喂",
          "nicknameModified": true,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzp/773DF6BD-327B-449F-8D21-42CCC64C4FC1.jpg",
          "avatarModified": true,
          "gender": 1,
          "genderModified": true,
          "mobileNumber": "15611869222",
          "ageLabel": 4,
          "birthday": "04-07",
          "pf": "iOS",
          "career": "IT互联网",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "白羊座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": true,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU174876E8D6",
          "invited": false,
          "isFacePerception": false,
          "authenticationStatus": 0,
          "migrate": 0,
          "isLogin": false
        }
      },
      {
        "id": 31220,
        "rent": 6000,
        "readyTime": 1534435200000,
        "room": 1,
        "parlor": 1,
        "payment": "2",
        "rentType": "1",
        "communityId": 992,
        "buildArea": 60,
        "cityId": 1,
        "areaId": 1142,
        "businessAreaId": 1203,
        "lon": 116.477805,
        "lat": 40.012972,
        "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzpaa63eeea-0ac6-4fa1-ab05-42325f045cb0.jpg",
        "status": 1,
        "createTime": 1534476567781,
        "nearbySubways": "677835,1101620,503.0;572986,573111,996.0;677835,573111,996.0;677835,1101621,1512.0;677835,1101619,1686.0",
        "userId": 555708,
        "pictureCount": 3,
        "outTime": 1534572010519,
        "communityName": "望京花园",
        "areaName": "朝阳",
        "businessAreaName": "望京",
        "updateTime": 1534572013288,
        "ip": "106.39.84.154",
        "hasWIFI": false,
        "hasFridge": false,
        "hasAirConditioning": false,
        "hasWasher": false,
        "hasToilet": false,
        "hasShower": false,
        "hasHeating": false,
        "hasGas": false,
        "hasWardrobe": false,
        "hasKitchen": false,
        "hasTV": false,
        "hasSofa": false,
        "hasBalcony": false,
        "hasElevator": false,
        "hasBed": true,
        "description": "块儿阿拉pls不不夸他怕pls路来PK7k7kpls",
        "subwayName": "14号线 15号线 14号线 14号线 14号线",
        "identity": 5,
        "toiletCount": 1,
        "subwayStationName": "东湖渠 望京 望京 来广营站 阜通",
        "contractPlan": false,
        "isApartment": true,
        "isOffline": false,
        "operateTime": 0,
        "user": {
          "id": 555708,
          "nickname": "P54720",
          "nicknameModified": false,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzpbee2fa49-9980-405f-9d4c-84f5ad197d14.jpg",
          "avatarModified": false,
          "gender": 3,
          "genderModified": false,
          "ageLabel": 0,
          "pf": "android",
          "career": "卖萌的",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": false,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": true,
          "apartmentName": "租趣科技有限公司",
          "apartmentCityId": 1,
          "administratorStatus": 2,
          "verifyTime": 1534300704000,
          "realName": "包瑞",
          "certNo": "232131198812260821",
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU17487F62BC",
          "invited": false,
          "apartmentId": 11007,
          "brand": "租趣公寓",
          "isFacePerception": true,
          "authenticationStatus": 1,
          "source": 2,
          "migrate": 0,
          "isLogin": false
        }
      },
      {
        "id": 31427,
        "rent": 5800,
        "readyTime": 1536821728380,
        "room": 1,
        "parlor": 1,
        "payment": "5",
        "rentType": "1",
        "communityId": 379949,
        "buildArea": 25,
        "cityId": 1,
        "areaId": 1142,
        "businessAreaId": 1203,
        "lon": 116.484439,
        "lat": 40.002867,
        "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/F7CE3A5D-2ECF-41EB-B3E7-77E57D4B58BF.jpg",
        "status": 1,
        "createTime": 1536821746904,
        "nearbySubways": "572986,573111,686.0;677835,573111,686.0;677835,1101619,820.0;677835,1101618,1019.0;677835,1101620,1745.0;677835,1101617,1946.0",
        "userId": 556021,
        "pictureCount": 1,
        "communityName": "合生麒麟社",
        "areaName": "朝阳",
        "businessAreaName": "望京",
        "updateTime": 1536904934601,
        "ip": "210.12.116.196",
        "hasWIFI": true,
        "hasFridge": true,
        "hasAirConditioning": true,
        "hasWasher": true,
        "hasToilet": false,
        "hasShower": true,
        "hasHeating": true,
        "hasGas": true,
        "hasWardrobe": true,
        "hasKitchen": true,
        "hasTV": true,
        "hasSofa": true,
        "hasBalcony": true,
        "hasElevator": true,
        "hasBed": true,
        "description": "特特屠夫偷摸头目哦涂抹偷偷哦哦投投投要小心翼翼",
        "subwayName": "15号线 14号线 14号线 14号线 14号线 14号线",
        "identity": 3,
        "toiletCount": 1,
        "subwayStationName": "望京 望京 阜通 望京南 东湖渠 高家园",
        "contractPlan": true,
        "isApartment": false,
        "isOffline": false,
        "operateTime": 0,
        "user": {
          "id": 556021,
          "nickname": "红包",
          "nicknameModified": true,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzpbce65356-9173-44f5-bcad-d778a8e82a17.jpg",
          "avatarModified": true,
          "gender": 1,
          "genderModified": true,
          "mobileNumber": "13212341234",
          "ageLabel": 5,
          "birthday": "09-12",
          "pf": "android",
          "career": "法律",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "处女座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": true,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU17487F63F5",
          "invited": false,
          "authenticationStatus": 0,
          "migrate": 0,
          "isLogin": true
        }
      },
      {
        "id": 31439,
        "rent": 6000,
        "readyTime": 1,
        "room": 1,
        "parlor": 1,
        "payment": "5",
        "rentType": "1",
        "communityId": 379949,
        "buildArea": 28,
        "cityId": 1,
        "areaId": 1142,
        "businessAreaId": 1203,
        "lon": 116.484439,
        "lat": 40.002867,
        "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/46B20104-2E5E-406D-9256-5B5DB35292DC.jpg",
        "status": 1,
        "createTime": 1537520859780,
        "nearbySubways": "572986,573111,686.0;677835,573111,686.0;677835,1101619,820.0;677835,1101618,1019.0;677835,1101620,1745.0;677835,1101617,1946.0",
        "userId": 556018,
        "pictureCount": 1,
        "outTime": 1537521142404,
        "communityName": "合生麒麟社",
        "areaName": "朝阳",
        "businessAreaName": "望京",
        "updateTime": 1537521160541,
        "ip": "106.39.84.154",
        "hasWIFI": true,
        "hasFridge": false,
        "hasAirConditioning": true,
        "hasWasher": true,
        "hasToilet": false,
        "hasShower": true,
        "hasHeating": false,
        "hasGas": true,
        "hasWardrobe": false,
        "hasKitchen": true,
        "hasTV": false,
        "hasSofa": true,
        "hasBalcony": true,
        "hasElevator": false,
        "hasBed": true,
        "description": "炖猫汤，就是要先把猫打一顿，然后把它放入锅中",
        "subwayName": "15号线 14号线 14号线 14号线 14号线 14号线",
        "identity": 1,
        "toiletCount": 1,
        "subwayStationName": "望京 望京 阜通 望京南 东湖渠 高家园",
        "contractPlan": true,
        "isApartment": false,
        "isOffline": false,
        "operateTime": 1537521160541,
        "user": {
          "id": 556018,
          "nickname": "我们去大草原",
          "nicknameModified": true,
          "avatar": "https://wx.qlogo.cn/mmopen/vi_32/ZLhicyPutHBNRkQIZAUzHEFA2a25hp7la6f2GxVltZSbzc0AzGnO3pWQ0QBibAvLbm4UU3GqLHJC980srYNqAeuA/132",
          "avatarModified": true,
          "gender": 2,
          "genderModified": true,
          "mobileNumber": "17110001016",
          "ageLabel": 1,
          "birthday": "01-01",
          "pushToken": "2321f2cbd8f0f1f8a7f110763e0030468d83cc39dc200855884a7ac9dc64e93b",
          "pf": "iOS",
          "career": "经营管理",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "摩羯座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": true,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU17487F63F2",
          "invited": false,
          "authenticationStatus": 2,
          "migrate": 0,
          "isLogin": true
        }
      }
    ],
    "startTime": 0,
    "houseRequests": [
      {
        "id": 9118,
        "description": "啦咯啦咯啦咯啦咯啦咯啦咯啦咯啦咯啦咯啦咯啦",
        "expectedLocation": "1203",
        "expectedLocations": "望京",
        "expectedAreas": "1142",
        "expectedAreaNames": "朝阳",
        "expectedTime": 1535339393000,
        "startRent": 0,
        "endRent": 5000,
        "cityId": 1,
        "status": 1,
        "createTime": 1535339415129,
        "userId": 555870,
        "updateTime": 1537513838233,
        "pictureCount": 0,
        "expectedSubwayStationId": "236765",
        "expectedSubwayStationName": "西直门",
        "expectedSubwayId": "236717",
        "expectedSubwayName": "2号线",
        "operateTime": 1537522302874,
        "user": {
          "id": 555870,
          "nickname": "测试9144",
          "nicknameModified": true,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzp/BD26B58B-FCAB-45B9-B8C4-DCE360AA8477.jpg",
          "avatarModified": true,
          "gender": 2,
          "genderModified": true,
          "mobileNumber": "15611869144",
          "ageLabel": 5,
          "birthday": "08-24",
          "pf": "iOS",
          "career": "贸易销售",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "处女座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": true,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU17487F635E",
          "invited": false,
          "authenticationStatus": 0,
          "migrate": 0,
          "isLogin": true
        }
      },
      {
        "id": 9124,
        "description": "大大大大大大大大大哥别杀我，我我我我我我我我我把枪都给你",
        "expectedLocation": "1203",
        "expectedLocations": "望京",
        "expectedAreas": "1142",
        "expectedAreaNames": "朝阳",
        "expectedTime": 1537171954000,
        "startRent": 0,
        "endRent": 6900,
        "cityId": 1,
        "status": 1,
        "createTime": 1537172055088,
        "userId": 556018,
        "outTime": 1537260242830,
        "updateTime": 1537261546136,
        "pictureCount": 0,
        "expectedSubwayStationId": "",
        "expectedSubwayId": "",
        "operateTime": 1537520995792,
        "user": {
          "id": 556018,
          "nickname": "我们去大草原",
          "nicknameModified": true,
          "avatar": "https://wx.qlogo.cn/mmopen/vi_32/ZLhicyPutHBNRkQIZAUzHEFA2a25hp7la6f2GxVltZSbzc0AzGnO3pWQ0QBibAvLbm4UU3GqLHJC980srYNqAeuA/132",
          "avatarModified": true,
          "gender": 2,
          "genderModified": true,
          "mobileNumber": "17110001016",
          "ageLabel": 1,
          "birthday": "01-01",
          "pushToken": "2321f2cbd8f0f1f8a7f110763e0030468d83cc39dc200855884a7ac9dc64e93b",
          "pf": "iOS",
          "career": "经营管理",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "摩羯座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": true,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU17487F63F2",
          "invited": false,
          "authenticationStatus": 2,
          "migrate": 0,
          "isLogin": true
        }
      },
      {
        "id": 9128,
        "description": "后管理机构过敏吗管理机构建立后去去去想去上学q y",
        "expectedLocation": "1203",
        "expectedLocations": "望京",
        "expectedAreas": "1142",
        "expectedAreaNames": "朝阳",
        "expectedTime": 1537516730000,
        "startRent": 0,
        "endRent": 5000,
        "cityId": 1,
        "status": 1,
        "createTime": 1537516757279,
        "userId": 556037,
        "updateTime": 1537516757279,
        "pictureCount": 0,
        "expectedSubwayStationId": "",
        "expectedSubwayId": "",
        "operateTime": 1537516757279,
        "user": {
          "id": 556037,
          "nickname": "5411",
          "nicknameModified": true,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzp/EC5A73E2-7984-472C-A0E7-A1FFAD105685.jpg",
          "avatarModified": true,
          "gender": 2,
          "genderModified": true,
          "mobileNumber": "15279055411",
          "ageLabel": 4,
          "birthday": "09-17",
          "pushToken": "62e5fa26040d6211f7bee07d4995305065983f655838a8bf840aea1914bb2872",
          "pf": "iOS",
          "career": "公关市场",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "处女座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": true,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU17487F6405",
          "invited": false,
          "authenticationStatus": 0,
          "migrate": 0,
          "isLogin": true
        }
      },
      {
        "id": 76,
        "description": "术语求组队形成什么的吗嗯我的，/::< 兔肉麻辣烫里有，",
        "expectedLocation": "1203 5994",
        "expectedLocations": "望京 奥林匹克公园",
        "expectedAreas": "1142 1142",
        "expectedAreaNames": "朝阳 朝阳",
        "expectedTime": 1528416000000,
        "startRent": 0,
        "endRent": 5300,
        "cityId": 1,
        "status": 2,
        "createTime": 1528423843341,
        "userId": 216,
        "violationReason": "",
        "outTime": 1528683223927,
        "updateTime": 1528697775336,
        "pictureCount": 2,
        "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/03fea031418de4827c7761ebe8aafe9961",
        "expectedSubwayStationId": "1101618",
        "expectedSubwayStationName": "望京南",
        "expectedSubwayId": "677835",
        "expectedSubwayName": "14号线",
        "operateTime": 0,
        "user": {
          "id": 216,
          "nickname": "萌了",
          "nicknameModified": true,
          "avatar": "https://wx.qlogo.cn/mmopen/vi_32/ZLhicyPutHBNRkQIZAUzHEFA2a25hp7la6f2GxVltZSbzc0AzGnO3pWQ0QBibAvLbmVOEKZiakfjMGcEok1qpYYdg/132",
          "avatarModified": true,
          "gender": 2,
          "genderModified": true,
          "mobileNumber": "17190171888",
          "ageLabel": 5,
          "birthday": "04-01",
          "pushToken": "AnR-ShYHR7_kzUJ9NJd4cvpxnV2OB7Hsyas40tiAI0Kh",
          "pf": "android",
          "career": "法律",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "白羊座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": true,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU174876E8D8",
          "invited": false,
          "isFacePerception": false,
          "authenticationStatus": 0,
          "migrate": 0,
          "isLogin": false
        }
      },
      {
        "id": 29,
        "description": "室友必须得好哈哈哈哈哈或hh哈哈哈哈哈哈",
        "expectedLocation": "1203",
        "expectedLocations": "望京",
        "expectedAreas": "1142",
        "expectedAreaNames": "朝阳",
        "expectedTime": 1,
        "startRent": 0,
        "endRent": 6000,
        "cityId": 1,
        "status": 2,
        "createTime": 1524555392218,
        "userId": 122,
        "violationReason": "",
        "outTime": 1525420007436,
        "updateTime": 1525420056641,
        "pictureCount": 1,
        "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/bbeaac1d4aa5dd3508391d86dd1b6dac103",
        "expectedSubwayStationId": "236742 236743",
        "expectedSubwayStationName": "苹果园 古城路",
        "expectedSubwayId": "236713 236713",
        "expectedSubwayName": "1号线 1号线",
        "operateTime": 0,
        "user": {
          "id": 122,
          "nickname": "婷",
          "nicknameModified": true,
          "avatar": "https://wx.qlogo.cn/mmopen/vi_32/Q0j4TwGTfTKoVicJa9T7Ct7CkrC2cDnd0tUfJnbxhA6AJysLll1WHvxtOl4iceic4HO5YHKv142Krg8PoMzqAahEw/0",
          "avatarModified": true,
          "gender": 2,
          "genderModified": true,
          "mobileNumber": "15834102126",
          "ageLabel": 3,
          "birthday": "02-01",
          "pf": "WEB",
          "career": "码农",
          "favorite": "美食,旅游,电影",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "水瓶座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": true,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU174876E87A",
          "invited": false,
          "isFacePerception": false,
          "authenticationStatus": 0,
          "migrate": 0,
          "isLogin": false
        }
      },
      {
        "id": 9122,
        "description": "木楼摩托头诺路路通考虑噜噜噜踏踏图考虑吕布踏踏噜噜噜噜啊哦哦哦",
        "expectedLocation": "1203",
        "expectedLocations": "望京",
        "expectedAreas": "1142",
        "expectedAreaNames": "朝阳",
        "expectedTime": 1,
        "startRent": 0,
        "endRent": 5000,
        "cityId": 1,
        "status": 1,
        "createTime": 1536649668572,
        "userId": 556014,
        "updateTime": 1536654457400,
        "pictureCount": 0,
        "listImageUrl": "",
        "expectedSubwayStationId": "",
        "expectedSubwayId": "",
        "operateTime": 0,
        "user": {
          "id": 556014,
          "nickname": "客运站",
          "nicknameModified": true,
          "avatar": "https://wx.qlogo.cn/mmopen/vi_32/K1qzYQaht3W71hyicBichtxRoiaKkzGlrxoXU8hngYxibLuzrm3k2TNOticIIqN3Y2ibwaJl3victib42udrY47Z5Qajcg/132",
          "avatarModified": true,
          "gender": 1,
          "genderModified": true,
          "mobileNumber": "15105827777",
          "ageLabel": 1,
          "birthday": "01-01",
          "pushToken": "AoacZWXhZ3cycbV6XjwOIoKotIZR8cyGnckVbW0aN4g-",
          "pf": "android",
          "career": "经营管理",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "摩羯座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": true,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "realName": "石景梅",
          "certNo": "372928198812188529",
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU17487F63EE",
          "invited": false,
          "authenticationStatus": 1,
          "migrate": 0,
          "isLogin": true
        }
      },
      {
        "id": 48,
        "description": "123123312313123123123123",
        "expectedLocation": "1203",
        "expectedLocations": "望京",
        "expectedAreas": "1142",
        "expectedAreaNames": "朝阳",
        "expectedTime": 1,
        "startRent": 0,
        "endRent": 8000,
        "cityId": 1,
        "status": 2,
        "createTime": 1525882355154,
        "userId": 149,
        "violationReason": "",
        "outTime": 1525882657231,
        "updateTime": 1527150102581,
        "pictureCount": 1,
        "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/951ccbbb8c73de6e829e644c15508ccf103",
        "expectedSubwayStationId": "236742",
        "expectedSubwayStationName": "苹果园",
        "expectedSubwayId": "236713",
        "expectedSubwayName": "1号线",
        "operateTime": 0,
        "user": {
          "id": 149,
          "nickname": "bboy小松",
          "nicknameModified": false,
          "avatar": "https://wx.qlogo.cn/mmopen/vi_32/Q0j4TwGTfTKy3EjibgVhPianAf86zcMcSYHbTQNWEzyHc9MPXVmou1g1uwKY6Hv6TDjicmBQNVu7SMmCO6V41Vm0w/132",
          "avatarModified": false,
          "gender": 1,
          "genderModified": false,
          "mobileNumber": "15901066043",
          "ageLabel": 1,
          "birthday": "01-01",
          "openId": "ob2_D070HhLor0_Q4xuzDx7Eqeqo",
          "unionId": "",
          "pf": "iOS",
          "career": "IT互联网",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "摩羯座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": true,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "mpOpenId": "oOKCt4haOJbNMYHvThAQkccwWQ3s",
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": true,
          "apartmentName": "自如公寓",
          "apartmentCityId": 1,
          "administratorStatus": 2,
          "verifyTime": 0,
          "realName": "高晓琳",
          "certNo": "37092319950321152X",
          "isScanCode": true,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU174876E895",
          "invited": true,
          "apartmentId": 11014,
          "brand": "自如公寓",
          "isFacePerception": false,
          "authenticationStatus": 1,
          "source": 2,
          "migrate": 0,
          "isLogin": false
        }
      },
      {
        "id": 2,
        "description": "想找个离地铁近的，方便出行周边设施完善的地方",
        "expectedLocation": "6819 1203 1163",
        "expectedLocations": "牡丹园 望京 陶然亭",
        "expectedAreas": "1143 1142 1141",
        "expectedAreaNames": "海淀 朝阳 宣武",
        "expectedTime": 1,
        "startRent": 1000,
        "endRent": 3500,
        "cityId": 1,
        "status": 2,
        "createTime": 1522120884567,
        "userId": 1,
        "violationReason": "",
        "outTime": 1522756831110,
        "updateTime": 1522835410828,
        "pictureCount": 2,
        "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/245c471b890986c46053f85aca0d926545",
        "operateTime": 0,
        "user": {
          "id": 1,
          "nickname": "��",
          "nicknameModified": true,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzp/6ed68153b9beb2dbcd4c1451c7c093f045",
          "avatarModified": true,
          "gender": 1,
          "genderModified": true,
          "mobileNumber": "",
          "ageLabel": 4,
          "birthday": "04-16",
          "openId": "",
          "unionId": "",
          "pf": "WEB",
          "career": "开飞机的",
          "favorite": "电影,读书,音乐,摄影,宅家,烘焙",
          "personalProfile": "等你发现时间是贼了，它早已偷光你的选择。",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "白羊座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": true,
          "infoCompleted": true,
          "flag": false,
          "privacy": 1,
          "forbidden": true,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU174876E801",
          "invited": false,
          "isFacePerception": false,
          "authenticationStatus": 0,
          "migrate": 0,
          "isLogin": false
        }
      },
      {
        "id": 61,
        "description": "吧还不哦头母哦咯头 克莱斯勒怕热头母母茶卡卡卡特痛",
        "expectedLocation": "1203 2640 1193",
        "expectedLocations": "望京 回龙观 亚运村",
        "expectedAreas": "1142 1150 1142",
        "expectedAreaNames": "朝阳 昌平 朝阳",
        "expectedTime": 1,
        "startRent": 0,
        "endRent": 5000,
        "cityId": 1,
        "status": 2,
        "createTime": 1526980633113,
        "userId": 171,
        "violationReason": "",
        "updateTime": 1526980633113,
        "pictureCount": 1,
        "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/A9C67DAC-014A-45FA-BF2B-5A2100B616CF.jpg",
        "expectedSubwayStationId": "",
        "expectedSubwayId": "",
        "operateTime": 0,
        "user": {
          "id": 171,
          "nickname": "123",
          "nicknameModified": false,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzp/img/default_avatar.png",
          "avatarModified": false,
          "gender": 0,
          "genderModified": false,
          "ageLabel": 0,
          "career": "小吃货",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": false,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invited": false,
          "isFacePerception": false,
          "authenticationStatus": 0,
          "migrate": 0,
          "isLogin": false
        }
      },
      {
        "id": 16,
        "description": "5757242424275868686868685727275757575757575858586858572242425686858606068575757575758585",
        "expectedLocation": "5833 1238 1203",
        "expectedLocations": "北七家 上地 望京",
        "expectedAreas": "1150 1143 1142",
        "expectedAreaNames": "昌平 海淀 朝阳",
        "expectedTime": 1,
        "startRent": 600,
        "endRent": 3900,
        "cityId": 1,
        "status": 2,
        "createTime": 1522657550706,
        "userId": 10,
        "violationReason": "",
        "outTime": 1522744380394,
        "updateTime": 1522751902445,
        "pictureCount": 3,
        "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/1345A352-971D-4845-A3A5-7F58222B9E3D.jpg",
        "operateTime": 0,
        "user": {
          "id": 10,
          "nickname": "123",
          "nicknameModified": false,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzp/img/default_avatar.png",
          "avatarModified": false,
          "gender": 0,
          "genderModified": false,
          "ageLabel": 0,
          "career": "小可爱",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": false,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invited": false,
          "isFacePerception": false,
          "authenticationStatus": 0,
          "migrate": 0,
          "isLogin": false
        }
      },
      {
        "id": 6,
        "description": "房子周边交通方便，室友一定要友善，爱干净！",
        "expectedLocation": "1203 5817",
        "expectedLocations": "望京 安定门",
        "expectedAreas": "1142 1138",
        "expectedAreaNames": "朝阳 东城",
        "expectedTime": 1,
        "startRent": 0,
        "endRent": 6000,
        "cityId": 1,
        "status": 2,
        "createTime": 1522139637209,
        "userId": 11,
        "violationReason": "",
        "outTime": 1522315817925,
        "updateTime": 1522406321788,
        "pictureCount": 1,
        "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/64d378f7cc30106c77126b29a793558591",
        "operateTime": 0,
        "user": {
          "id": 11,
          "nicknameModified": false,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzp/img/default_avatar.png",
          "avatarModified": false,
          "gender": 0,
          "genderModified": false,
          "ageLabel": 0,
          "career": "",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": false,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invited": false,
          "authenticationStatus": 0,
          "migrate": 0,
          "isLogin": false
        }
      },
      {
        "id": 9,
        "description": "sfdfsfsdflkjsflksjdflksdjlfks",
        "expectedLocation": "5817 1203",
        "expectedLocations": "安定门 望京",
        "expectedAreas": "1138 1142",
        "expectedAreaNames": "东城 朝阳",
        "expectedTime": 1,
        "startRent": 0,
        "endRent": 6000,
        "cityId": 1,
        "status": 2,
        "createTime": 1522308033606,
        "userId": 18,
        "violationReason": "",
        "updateTime": 1522308131136,
        "pictureCount": 1,
        "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/0e4302c9ed44f92d1973d4b48d461c56103",
        "operateTime": 0,
        "user": {
          "id": 18,
          "nickname": "123",
          "nicknameModified": false,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzp/img/default_avatar.png",
          "avatarModified": false,
          "gender": 0,
          "genderModified": false,
          "ageLabel": 0,
          "career": "小吃货",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": false,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invited": false,
          "isFacePerception": false,
          "authenticationStatus": 0,
          "migrate": 0,
          "isLogin": false
        }
      },
      {
        "id": 3,
        "description": "哦哦哦哦柳健健康康快快乐乐旅途快乐太累了",
        "expectedLocation": "1203",
        "expectedLocations": "望京",
        "expectedAreas": "1142",
        "expectedAreaNames": "朝阳",
        "expectedTime": 1,
        "startRent": 0,
        "endRent": 5000,
        "cityId": 1,
        "status": 2,
        "createTime": 1522123604036,
        "userId": 2,
        "violationReason": "",
        "updateTime": 1522143975460,
        "pictureCount": 1,
        "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/378721D9-001C-4BC5-8DF6-13C382DE55D7.jpg",
        "operateTime": 0,
        "user": {
          "id": 2,
          "nickname": "123",
          "nicknameModified": false,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzp/img/default_avatar.png",
          "avatarModified": false,
          "gender": 0,
          "genderModified": false,
          "mobileNumber": "15101039080",
          "ageLabel": 0,
          "career": "卖艺的",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": false,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invited": false,
          "isFacePerception": false,
          "authenticationStatus": 0,
          "migrate": 0,
          "isLogin": false
        }
      }
    ],
    "houseRequestMessage": "7052，在你离开的1年内，新增13位伙伴，符合你发布的房源地点，其中最新发布的是测试9144哦～",
    "houseMessage": "7052，在你离开的1年内，新增15位伙伴，符合你的求租地点，其中最新发布的是9145哦～",
    "endTime": 1537846020000,
    "house": {
      "id": 31436,
      "rent": 5000,
      "readyTime": 1537459200000,
      "room": 1,
      "parlor": 1,
      "payment": "2",
      "rentType": "1",
      "communityId": 379949,
      "buildArea": 50,
      "cityId": 1,
      "areaId": 1142,
      "businessAreaId": 1203,
      "lon": 116.484439,
      "lat": 40.002867,
      "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzpfb1897ba-0010-4efa-b2d3-f36c02e2490f.jpg",
      "status": 1,
      "createTime": 1537510258120,
      "nearbySubways": "572986,573111,686.0;677835,573111,686.0;677835,1101619,820.0;677835,1101618,1019.0;677835,1101620,1745.0;677835,1101617,1946.0",
      "userId": 555908,
      "pictureCount": 2,
      "outTime": 1537519026573,
      "communityName": "合生麒麟社",
      "areaName": "朝阳",
      "businessAreaName": "望京",
      "updateTime": 1537519049075,
      "ip": "106.39.84.154",
      "hasWIFI": false,
      "hasFridge": false,
      "hasAirConditioning": false,
      "hasWasher": false,
      "hasToilet": false,
      "hasShower": false,
      "hasHeating": false,
      "hasGas": false,
      "hasWardrobe": false,
      "hasKitchen": false,
      "hasTV": false,
      "hasSofa": false,
      "hasBalcony": false,
      "hasElevator": false,
      "hasBed": true,
      "description": "人转切转切让外婆搜嘎给你追就去QQ里李敏呼呼呼估计胡明明体会己饥己溺HK",
      "subwayName": "15号线 14号线 14号线 14号线 14号线 14号线",
      "identity": 1,
      "toiletCount": 1,
      "subwayStationName": "望京 望京 阜通 望京南 东湖渠 高家园",
      "contractPlan": true,
      "isApartment": false,
      "isOffline": false,
      "operateTime": 1537843986414
    },
    "houseRequest": {
      "id": 9127,
      "description": "胡悔之晚矣提醒去去去去一下去去去去去睡去去去去去去",
      "expectedLocation": "1203",
      "expectedLocations": "望京",
      "expectedAreas": "1142",
      "expectedAreaNames": "朝阳",
      "expectedTime": 1537459200000,
      "startRent": 0,
      "endRent": 1000000,
      "cityId": 1,
      "status": 1,
      "createTime": 1537510767695,
      "userId": 555908,
      "outTime": 1537519028271,
      "updateTime": 1537519050482,
      "pictureCount": 0,
      "listImageUrl": "",
      "expectedSubwayStationId": "",
      "expectedSubwayId": "",
      "operateTime": 1537843986414
    }
  }
}

```
### 推荐house列表
##### 接口:/HouseController/commendHouse
##### 请求方式:GET
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|id|Long|发布的求租ID|是|
|startTime|long|开始时间|是|
|endTime|long|结束时间|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": [
    {
      "id": 28427,
      "rent": 666,
      "readyTime": 1,
      "room": 1,
      "parlor": 1,
      "payment": "2",
      "rentType": "1",
      "communityId": 807,
      "buildArea": 555,
      "cityId": 1,
      "areaId": 1142,
      "businessAreaId": 1203,
      "lon": 116.481732,
      "lat": 40.00093,
      "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/F019CEB1-3C16-4FF4-A112-20A758E166CB.jpg",
      "status": 5,
      "createTime": 1531894497510,
      "nearbySubways": "677835,1101619,504.0;572986,573111,564.0;677835,573111,564.0;677835,1101618,820.0;677835,1101620,1834.0;677835,1101617,1872.0",
      "userId": 13290,
      "pictureCount": 2,
      "violationReason": "",
      "outTime": 1531896714791,
      "communityName": "华鼎世家",
      "areaName": "朝阳",
      "businessAreaName": "望京",
      "updateTime": 1531894497510,
      "ip": "10.141.159.122",
      "hasWIFI": true,
      "hasFridge": false,
      "hasAirConditioning": false,
      "hasWasher": false,
      "hasToilet": false,
      "hasShower": true,
      "hasHeating": false,
      "hasGas": false,
      "hasWardrobe": false,
      "hasKitchen": false,
      "hasTV": false,
      "hasSofa": false,
      "hasBalcony": false,
      "hasElevator": false,
      "hasBed": true,
      "description": "房租为这个特别房子位置特别合适，退还是退还是。",
      "subwayName": "14号线 15号线 14号线 14号线 14号线 14号线",
      "identity": 2,
      "toiletCount": 1,
      "subwayStationName": "阜通 望京 望京 望京南 东湖渠 高家园",
      "contractPlan": true,
      "isApartment": false,
      "isOffline": false,
      "operateTime": 0,
      "user": {
        "id": 13290,
        "nickname": "背锅侠",
        "nicknameModified": true,
        "avatar": "http://test-1251500528.file.myqcloud.com/hzp/6F044C9F-DD33-49EC-A90A-B0C246D83673.jpg",
        "avatarModified": true,
        "gender": 1,
        "genderModified": true,
        "mobileNumber": "15910677888",
        "ageLabel": 5,
        "birthday": "05-01",
        "pf": "WEB",
        "career": "文职",
        "personalProfile": "我去拯救地球了...",
        "zmScore": 0,
        "zmAuth": false,
        "constellation": "金牛座",
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
        "zmAuthPushed": false,
        "infoCompleted": true,
        "flag": false,
        "privacy": 0,
        "forbidden": false,
        "virtual": false,
        "subscribe": false,
        "isForeign": false,
        "isAdministrators": false,
        "administratorStatus": 0,
        "isScanCode": false,
        "subscribeFwh": false,
        "invitationCode": "HEZUQU1748771BEA",
        "invited": true,
        "isFacePerception": false,
        "authenticationStatus": 2,
        "migrate": 0,
        "isLogin": false
      }
    },
    {
      "id": 31216,
      "rent": 500,
      "readyTime": 1534476102188,
      "room": 1,
      "parlor": 1,
      "payment": "2",
      "rentType": "1",
      "communityId": 379949,
      "buildArea": 80,
      "cityId": 1,
      "areaId": 1142,
      "businessAreaId": 1203,
      "lon": 116.484439,
      "lat": 40.002867,
      "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/ABD7E4A0-737B-4110-95C9-58126A501B79.jpg",
      "status": 4,
      "createTime": 1534476122238,
      "nearbySubways": "572986,573111,686.0;677835,573111,686.0;677835,1101619,820.0;677835,1101618,1019.0;677835,1101620,1745.0;677835,1101617,1946.0",
      "userId": 555759,
      "pictureCount": 2,
      "outTime": 1534904653658,
      "communityName": "合生麒麟社",
      "areaName": "朝阳",
      "businessAreaName": "望京",
      "updateTime": 1534904944485,
      "ip": "210.12.116.196",
      "hasWIFI": false,
      "hasFridge": true,
      "hasAirConditioning": true,
      "hasWasher": true,
      "hasToilet": false,
      "hasShower": false,
      "hasHeating": false,
      "hasGas": false,
      "hasWardrobe": true,
      "hasKitchen": false,
      "hasTV": false,
      "hasSofa": false,
      "hasBalcony": true,
      "hasElevator": false,
      "hasBed": true,
      "description": "在线客服时间截止日期到明天开始好好学习的话就是好给力哈！你说什么我不会告诉你为什么会",
      "subwayName": "15号线 14号线 14号线 14号线 14号线 14号线",
      "signedTime": 1534922144791,
      "identity": 5,
      "toiletCount": 1,
      "subwayStationName": "望京 望京 阜通 望京南 东湖渠 高家园",
      "contractPlan": false,
      "isApartment": true,
      "isOffline": false,
      "operateTime": 0,
      "user": {
        "id": 555759,
        "nickname": "P24213",
        "nicknameModified": false,
        "avatar": "http://test-1251500528.file.myqcloud.com/hzp/36C9FBF2-71E9-4E89-B0ED-D4406851EE3D.jpg",
        "avatarModified": false,
        "gender": 3,
        "genderModified": false,
        "mobileNumber": "15279055744",
        "ageLabel": 0,
        "pushToken": "d62fcfaefdde452fdde4d17d3bd6039fde4aec7d3f11f0bac96683169a9f5694",
        "pf": "iOS",
        "career": "小可爱",
        "personalProfile": "我去拯救地球了...",
        "zmScore": 0,
        "zmAuth": false,
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
        "zmAuthPushed": false,
        "infoCompleted": false,
        "flag": false,
        "privacy": 0,
        "forbidden": false,
        "virtual": false,
        "subscribe": false,
        "isForeign": false,
        "isAdministrators": true,
        "apartmentName": "自如皇家公司",
        "apartmentCityId": 1,
        "administratorStatus": 2,
        "verifyTime": 1534475633791,
        "realName": "邓金龙",
        "certNo": "360122199212303318",
        "isScanCode": false,
        "subscribeFwh": false,
        "invitationCode": "HEZUQU17487F62EF",
        "invited": false,
        "apartmentId": 11005,
        "brand": "自如管家",
        "isFacePerception": true,
        "authenticationStatus": 1,
        "source": 2,
        "migrate": 0,
        "isLogin": true
      }
    },
    {
      "id": 160,
      "rent": 2000,
      "readyTime": 1529039146541,
      "room": 1,
      "parlor": 1,
      "payment": "2",
      "rentType": "1",
      "communityId": 379643,
      "buildArea": 20,
      "cityId": 1,
      "areaId": 1142,
      "businessAreaId": 1203,
      "lon": 116.487544,
      "lat": 40.005106,
      "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/6359948B-E480-4913-9CF6-E1DA3D62BA01.jpg",
      "status": 1,
      "createTime": 1529039188048,
      "nearbySubways": "572986,573111,945.0;677835,573111,945.0;677835,1101619,1183.0;677835,1101618,1307.0;677835,1101620,1710.0",
      "userId": 234,
      "pictureCount": 1,
      "communityName": "宝星华庭",
      "areaName": "朝阳",
      "businessAreaName": "望京",
      "updateTime": 1529039188048,
      "ip": "10.141.159.122",
      "hasWIFI": false,
      "hasFridge": false,
      "hasAirConditioning": true,
      "hasWasher": false,
      "hasToilet": false,
      "hasShower": false,
      "hasHeating": false,
      "hasGas": true,
      "hasWardrobe": false,
      "hasKitchen": false,
      "hasTV": false,
      "hasSofa": true,
      "hasBalcony": false,
      "hasElevator": false,
      "hasBed": true,
      "description": "把刺激了己饥己溺还没到什么时候回来了吗我就",
      "subwayName": "15号线 14号线 14号线 14号线 14号线",
      "identity": 2,
      "toiletCount": 1,
      "subwayStationName": "望京 望京 阜通 望京南 东湖渠",
      "contractPlan": true,
      "isApartment": false,
      "isOffline": false,
      "operateTime": 0,
      "user": {
        "id": 234,
        "nickname": "哈哈哈",
        "nicknameModified": true,
        "avatar": "http://test-1251500528.file.myqcloud.com/hzp/509D7F06-DB7F-49D4-83BE-99FBDF818777.jpg",
        "avatarModified": true,
        "gender": 1,
        "genderModified": true,
        "mobileNumber": "15611869199",
        "ageLabel": 4,
        "birthday": "06-14",
        "pf": "iOS",
        "career": "财务",
        "personalProfile": "我去拯救地球了...",
        "zmScore": 0,
        "zmAuth": false,
        "constellation": "双子座",
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
        "zmAuthPushed": false,
        "infoCompleted": true,
        "flag": false,
        "privacy": 0,
        "forbidden": false,
        "virtual": false,
        "subscribe": false,
        "isForeign": false,
        "isAdministrators": false,
        "administratorStatus": 0,
        "realName": "杨天3",
        "certNo": "210703199307273013",
        "isScanCode": false,
        "subscribeFwh": false,
        "invitationCode": "HEZUQU174876E8EA",
        "invited": false,
        "isFacePerception": false,
        "authenticationStatus": 0,
        "migrate": 0,
        "isLogin": false
      }
    },
    {
      "id": 31340,
      "rent": 5000,
      "readyTime": 1,
      "room": 1,
      "parlor": 1,
      "payment": "4",
      "rentType": "1",
      "communityId": 1035,
      "buildArea": 50,
      "cityId": 1,
      "areaId": 1142,
      "businessAreaId": 1203,
      "lon": 116.475618,
      "lat": 40.009805,
      "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/A893D381-2E32-410A-BCDA-3D2B3368E1C7.jpg",
      "status": 4,
      "createTime": 1535446876381,
      "nearbySubways": "572986,573111,642.0;677835,573111,642.0;677835,1101620,731.0;677835,1101619,1342.0;677835,1101621,1824.0;677835,1101618,1920.0",
      "userId": 555912,
      "pictureCount": 3,
      "communityName": "望京明苑",
      "areaName": "朝阳",
      "businessAreaName": "望京",
      "updateTime": 1535446876381,
      "ip": "210.12.116.196",
      "hasWIFI": false,
      "hasFridge": false,
      "hasAirConditioning": false,
      "hasWasher": false,
      "hasToilet": false,
      "hasShower": false,
      "hasHeating": false,
      "hasGas": false,
      "hasWardrobe": false,
      "hasKitchen": false,
      "hasTV": false,
      "hasSofa": false,
      "hasBalcony": false,
      "hasElevator": false,
      "hasBed": true,
      "description": "涂抹木头娜家数据库铁路局家数据库铁路局路开始哭哭哭",
      "subwayName": "15号线 14号线 14号线 14号线 14号线 14号线",
      "signedTime": 1535453942299,
      "identity": 5,
      "toiletCount": 1,
      "subwayStationName": "望京 望京 东湖渠 阜通 来广营站 望京南",
      "contractPlan": false,
      "isApartment": true,
      "isOffline": false,
      "operateTime": 0,
      "user": {
        "id": 555912,
        "nickname": "范晓禹",
        "nicknameModified": false,
        "avatar": "http://test-1251500528.file.myqcloud.com/hzp/2AD66637-5C4A-4FE9-8237-AA82FDA3DDBB.jpg",
        "avatarModified": false,
        "gender": 3,
        "genderModified": false,
        "mobileNumber": "18601949783",
        "ageLabel": 0,
        "pf": "iOS",
        "career": "",
        "personalProfile": "我去拯救地球了...",
        "zmScore": 0,
        "zmAuth": false,
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
        "zmAuthPushed": false,
        "infoCompleted": false,
        "flag": false,
        "privacy": 0,
        "forbidden": false,
        "virtual": false,
        "subscribe": false,
        "isForeign": false,
        "isAdministrators": true,
        "apartmentName": "北京好孩子公寓有限责任公司",
        "apartmentCityId": 1,
        "administratorStatus": 2,
        "verifyTime": 1535446109706,
        "realName": "范晓禹",
        "certNo": "220211198708223910",
        "isScanCode": false,
        "subscribeFwh": false,
        "invitationCode": "HEZUQU17487F6388",
        "invited": false,
        "apartmentId": 11010,
        "brand": "好孩子公寓",
        "isFacePerception": true,
        "authenticationStatus": 1,
        "source": 2,
        "migrate": 0,
        "isLogin": true
      }
    },
    {
      "id": 28260,
      "rent": 6695,
      "room": 1,
      "parlor": 1,
      "payment": "1",
      "rentType": "1",
      "communityId": 379949,
      "cityId": 1,
      "areaId": 1142,
      "businessAreaId": 1203,
      "lon": 116.484439,
      "lat": 40.002867,
      "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzpba41ca79-14fa-40ff-ba0c-2f8a57e190a1.jpg",
      "status": 4,
      "createTime": 1530856084007,
      "nearbySubways": "572986,573111,686.0;677835,573111,686.0;677835,1101619,820.0;677835,1101618,1019.0;677835,1101620,1745.0;677835,1101617,1946.0",
      "userId": 215,
      "pictureCount": 3,
      "communityName": "合生麒麟社",
      "areaName": "朝阳",
      "businessAreaName": "望京",
      "updateTime": 1530856084007,
      "hasWIFI": false,
      "hasFridge": false,
      "hasAirConditioning": false,
      "hasWasher": false,
      "hasToilet": false,
      "hasShower": false,
      "hasHeating": false,
      "hasGas": false,
      "hasWardrobe": false,
      "hasKitchen": false,
      "hasTV": false,
      "hasSofa": false,
      "hasBalcony": false,
      "hasElevator": false,
      "hasBed": false,
      "subwayName": "15号线 14号线 14号线 14号线 14号线 14号线",
      "toiletCount": 1,
      "subwayStationName": "望京 望京 阜通 望京南 东湖渠 高家园",
      "contractPlan": false,
      "isApartment": false,
      "isOffline": true,
      "operateTime": 0,
      "user": {
        "id": 215,
        "nickname": "123",
        "nicknameModified": false,
        "avatar": "http://test-1251500528.file.myqcloud.com/hzp/img/default_avatar.png",
        "avatarModified": false,
        "gender": 0,
        "genderModified": false,
        "ageLabel": 0,
        "career": "卖艺的",
        "personalProfile": "我去拯救地球了...",
        "zmScore": 0,
        "zmAuth": false,
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
        "zmAuthPushed": false,
        "infoCompleted": false,
        "flag": false,
        "privacy": 0,
        "forbidden": false,
        "virtual": false,
        "subscribe": false,
        "isForeign": false,
        "isAdministrators": false,
        "administratorStatus": 0,
        "isScanCode": false,
        "subscribeFwh": false,
        "invited": false,
        "isFacePerception": false,
        "authenticationStatus": 0,
        "migrate": 0,
        "isLogin": false
      }
    },
    {
      "id": 28457,
      "rent": 2555,
      "readyTime": 1532563200000,
      "room": 1,
      "parlor": 1,
      "payment": "1",
      "rentType": "1",
      "communityId": 2300468,
      "buildArea": 13,
      "cityId": 1,
      "areaId": 1142,
      "businessAreaId": 1203,
      "lon": 116.49203,
      "lat": 40.002902,
      "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/712a8a6db4f48babfd04f5eb1997069c.jpg",
      "status": 2,
      "createTime": 1532584685228,
      "nearbySubways": "677835,1101618,1241.0;572986,573111,1327.0;677835,573111,1327.0;677835,1101619,1367.0;677835,1101617,1775.0",
      "userId": 13334,
      "pictureCount": 1,
      "violationReason": "",
      "communityName": "融科橄榄城",
      "areaName": "朝阳",
      "businessAreaName": "望京",
      "updateTime": 1532584685228,
      "ip": "10.141.159.122",
      "hasWIFI": false,
      "hasFridge": false,
      "hasAirConditioning": false,
      "hasWasher": false,
      "hasToilet": false,
      "hasShower": false,
      "hasHeating": false,
      "hasGas": false,
      "hasWardrobe": false,
      "hasKitchen": false,
      "hasTV": false,
      "hasSofa": false,
      "hasBalcony": false,
      "hasElevator": false,
      "hasBed": true,
      "description": "房子魏子涵好位置共享好我在干什么东北啊？",
      "subwayName": "14号线 15号线 14号线 14号线 14号线",
      "identity": 1,
      "toiletCount": 1,
      "subwayStationName": "望京南 望京 望京 阜通 高家园",
      "contractPlan": true,
      "isApartment": false,
      "isOffline": false,
      "operateTime": 0,
      "user": {
        "id": 13334,
        "nickname": "2667",
        "nicknameModified": true,
        "avatar": "http://test-1251500528.file.myqcloud.com/hzp/077c4f3a6cb0744e793fcd72bf83634d45",
        "avatarModified": true,
        "gender": 1,
        "genderModified": true,
        "mobileNumber": "13315192667",
        "ageLabel": 2,
        "birthday": "01-01",
        "pf": "android",
        "career": "设计",
        "personalProfile": "我去拯救地球了...",
        "zmScore": 0,
        "zmAuth": false,
        "constellation": "摩羯座",
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
        "zmAuthPushed": false,
        "infoCompleted": true,
        "flag": false,
        "privacy": 0,
        "forbidden": false,
        "virtual": false,
        "subscribe": false,
        "isForeign": false,
        "isAdministrators": false,
        "administratorStatus": 0,
        "isScanCode": false,
        "subscribeFwh": false,
        "invitationCode": "HEZUQU1748771C16",
        "invited": false,
        "isFacePerception": false,
        "authenticationStatus": 0,
        "migrate": 0,
        "isLogin": true
      }
    },
    {
      "id": 125,
      "rent": 5363,
      "readyTime": 1,
      "room": 1,
      "parlor": 1,
      "payment": "2",
      "rentType": "1",
      "communityId": 2300468,
      "buildArea": 35,
      "cityId": 1,
      "areaId": 1142,
      "businessAreaId": 1203,
      "lon": 116.49203,
      "lat": 40.002902,
      "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/1ede7dc296312cf8bc5350a747aee45e.jpg",
      "status": 2,
      "createTime": 1528426657343,
      "nearbySubways": "677835,1101618,1241.0;572986,573111,1327.0;677835,573111,1327.0;677835,1101619,1367.0;677835,1101617,1775.0",
      "userId": 216,
      "pictureCount": 1,
      "violationReason": "",
      "outTime": 1528697678521,
      "communityName": "融科橄榄城",
      "areaName": "朝阳",
      "businessAreaName": "望京",
      "updateTime": 1528705608909,
      "ip": "10.141.159.122",
      "hasWIFI": true,
      "hasFridge": false,
      "hasAirConditioning": false,
      "hasWasher": false,
      "hasToilet": false,
      "hasShower": true,
      "hasHeating": true,
      "hasGas": true,
      "hasWardrobe": false,
      "hasKitchen": true,
      "hasTV": false,
      "hasSofa": false,
      "hasBalcony": false,
      "hasElevator": false,
      "hasBed": true,
      "description": "来了吗我像那种人吗好的了直接回家吃饭吧额",
      "subwayName": "14号线 15号线 14号线 14号线 14号线",
      "identity": 1,
      "toiletCount": 1,
      "subwayStationName": "望京南 望京 望京 阜通 高家园",
      "contractPlan": false,
      "isApartment": false,
      "isOffline": false,
      "operateTime": 0,
      "user": {
        "id": 216,
        "nickname": "萌了",
        "nicknameModified": true,
        "avatar": "https://wx.qlogo.cn/mmopen/vi_32/ZLhicyPutHBNRkQIZAUzHEFA2a25hp7la6f2GxVltZSbzc0AzGnO3pWQ0QBibAvLbmVOEKZiakfjMGcEok1qpYYdg/132",
        "avatarModified": true,
        "gender": 2,
        "genderModified": true,
        "mobileNumber": "17190171888",
        "ageLabel": 5,
        "birthday": "04-01",
        "pushToken": "AnR-ShYHR7_kzUJ9NJd4cvpxnV2OB7Hsyas40tiAI0Kh",
        "pf": "android",
        "career": "法律",
        "personalProfile": "我去拯救地球了...",
        "zmScore": 0,
        "zmAuth": false,
        "constellation": "白羊座",
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
        "zmAuthPushed": false,
        "infoCompleted": true,
        "flag": false,
        "privacy": 0,
        "forbidden": false,
        "virtual": false,
        "subscribe": false,
        "isForeign": false,
        "isAdministrators": false,
        "administratorStatus": 0,
        "isScanCode": false,
        "subscribeFwh": false,
        "invitationCode": "HEZUQU174876E8D8",
        "invited": false,
        "isFacePerception": false,
        "authenticationStatus": 0,
        "migrate": 0,
        "isLogin": false
      }
    },
    {
      "id": 31422,
      "rent": 5555,
      "readyTime": 1536624000000,
      "room": 1,
      "parlor": 1,
      "payment": "2",
      "rentType": "1",
      "communityId": 9183,
      "buildArea": 470,
      "cityId": 1,
      "areaId": 1142,
      "businessAreaId": 1203,
      "lon": 116.481001,
      "lat": 40.01027,
      "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/c154e04143eafa0ffd554ab536b3ac17.jpg",
      "status": 4,
      "createTime": 1536650055079,
      "nearbySubways": "572986,573111,787.0;677835,573111,787.0;677835,1101620,909.0;677835,1101619,1418.0;677835,1101618,1857.0;677835,1101621,1883.0",
      "userId": 555983,
      "pictureCount": 1,
      "communityName": "望京新居",
      "areaName": "朝阳",
      "businessAreaName": "望京",
      "updateTime": 1536650055079,
      "ip": "10.141.159.122",
      "hasWIFI": false,
      "hasFridge": false,
      "hasAirConditioning": false,
      "hasWasher": false,
      "hasToilet": false,
      "hasShower": true,
      "hasHeating": false,
      "hasGas": false,
      "hasWardrobe": false,
      "hasKitchen": true,
      "hasTV": false,
      "hasSofa": false,
      "hasBalcony": false,
      "hasElevator": false,
      "hasBed": true,
      "description": "哈喽喽KKKKKK哦myX5盼头女扣扣图",
      "subwayName": "15号线 14号线 14号线 14号线 14号线 14号线",
      "signedTime": 1536718474016,
      "identity": 1,
      "toiletCount": 1,
      "subwayStationName": "望京 望京 东湖渠 阜通 望京南 来广营站",
      "contractPlan": true,
      "isApartment": false,
      "isOffline": false,
      "operateTime": 0,
      "user": {
        "id": 555983,
        "nickname": "1008",
        "nicknameModified": true,
        "avatar": "http://test-1251500528.file.myqcloud.com/hzpe550e695-55e2-4985-a728-b993c30b53ac.jpg",
        "avatarModified": true,
        "gender": 1,
        "genderModified": true,
        "mobileNumber": "17110001008",
        "ageLabel": 3,
        "birthday": "09-06",
        "pf": "WEB",
        "career": "建筑规划",
        "personalProfile": "我去拯救地球了...",
        "zmScore": 0,
        "zmAuth": false,
        "constellation": "处女座",
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
        "zmAuthPushed": false,
        "infoCompleted": true,
        "flag": false,
        "privacy": 0,
        "forbidden": false,
        "virtual": false,
        "subscribe": false,
        "isForeign": false,
        "isAdministrators": false,
        "administratorStatus": 0,
        "realName": "孙长军",
        "certNo": "222426198801283536",
        "isScanCode": false,
        "subscribeFwh": false,
        "invitationCode": "HEZUQU17487F63CF",
        "invited": false,
        "authenticationStatus": 1,
        "migrate": 0,
        "isLogin": true
      }
    },
    {
      "id": 31214,
      "rent": 275879,
      "readyTime": 1534348800000,
      "room": 1,
      "parlor": 1,
      "payment": "4",
      "rentType": "1",
      "communityId": 8182,
      "buildArea": 257,
      "cityId": 1,
      "areaId": 1142,
      "businessAreaId": 1203,
      "lon": 116.476415,
      "lat": 39.992226,
      "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp6e800862-dd5f-4971-800f-46e855d3dc9b.jpg",
      "status": 1,
      "createTime": 1534403753665,
      "nearbySubways": "677835,1101619,629.0;677835,1101618,648.0;572986,573111,1318.0;677835,573111,1318.0;677835,1101617,1615.0",
      "userId": 13306,
      "pictureCount": 2,
      "communityName": "望京大厦",
      "areaName": "朝阳",
      "businessAreaName": "望京",
      "updateTime": 1534405653836,
      "ip": "192.168.62.125",
      "hasWIFI": false,
      "hasFridge": false,
      "hasAirConditioning": false,
      "hasWasher": false,
      "hasToilet": false,
      "hasShower": false,
      "hasHeating": false,
      "hasGas": false,
      "hasWardrobe": false,
      "hasKitchen": false,
      "hasTV": false,
      "hasSofa": false,
      "hasBalcony": false,
      "hasElevator": false,
      "hasBed": true,
      "description": "11经济技术8极速弹力素提供姑姑肃肃兔罝",
      "subwayName": "14号线 14号线 15号线 14号线 14号线",
      "identity": 5,
      "toiletCount": 1,
      "subwayStationName": "阜通 望京南 望京 望京 高家园",
      "contractPlan": false,
      "isApartment": true,
      "isOffline": false,
      "operateTime": 0,
      "user": {
        "id": 13306,
        "nickname": "帅哥",
        "nicknameModified": true,
        "avatar": "http://test-1251500528.file.myqcloud.com/hzp50d0ebc9-7c6e-4c5a-b38f-1ecfc07c6a24.jpg",
        "avatarModified": true,
        "gender": 1,
        "genderModified": true,
        "mobileNumber": "13021021302",
        "ageLabel": 5,
        "birthday": "07-30",
        "pushToken": "AgU0j5xn62VA-MgeTV1Zx1nOdpSPuvHHxHxfNJypYdxt",
        "pf": "android",
        "career": "金融经济",
        "personalProfile": "我去拯救地球了...",
        "zmScore": 0,
        "zmAuth": false,
        "constellation": "狮子座",
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
        "zmAuthPushed": false,
        "infoCompleted": true,
        "flag": false,
        "privacy": 0,
        "forbidden": false,
        "virtual": false,
        "subscribe": false,
        "isForeign": false,
        "isAdministrators": true,
        "apartmentName": "嘉年华",
        "apartmentCityId": 1,
        "administratorStatus": 2,
        "verifyTime": 1532081883024,
        "realName": "",
        "certNo": "",
        "isScanCode": false,
        "subscribeFwh": false,
        "invitationCode": "HEZUQU1748771BFA",
        "invited": true,
        "apartmentId": 11028,
        "brand": "嘉年华",
        "isFacePerception": false,
        "authenticationStatus": 0,
        "source": 2,
        "migrate": 0,
        "isLogin": false
      }
    },
    {
      "id": 28365,
      "rent": 5555,
      "room": 1,
      "parlor": 1,
      "payment": "1",
      "rentType": "1",
      "communityId": 3401,
      "cityId": 1,
      "areaId": 1142,
      "businessAreaId": 1203,
      "lon": 116.490587,
      "lat": 39.998639,
      "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/069C427A-76CA-4055-8F1C-296D06296F34.jpg",
      "status": 4,
      "createTime": 1531131972228,
      "nearbySubways": "677835,1101618,798.0;677835,1101619,1126.0;677835,1101617,1326.0;572986,573111,1341.0;677835,573111,1341.0",
      "userId": 242,
      "pictureCount": 3,
      "communityName": "方恒国际中心",
      "areaName": "朝阳",
      "businessAreaName": "望京",
      "updateTime": 1531131972228,
      "hasWIFI": false,
      "hasFridge": false,
      "hasAirConditioning": false,
      "hasWasher": false,
      "hasToilet": false,
      "hasShower": false,
      "hasHeating": false,
      "hasGas": false,
      "hasWardrobe": false,
      "hasKitchen": false,
      "hasTV": false,
      "hasSofa": false,
      "hasBalcony": false,
      "hasElevator": false,
      "hasBed": false,
      "subwayName": "14号线 14号线 14号线 15号线 14号线",
      "toiletCount": 1,
      "subwayStationName": "望京南 阜通 高家园 望京 望京",
      "contractPlan": false,
      "isApartment": false,
      "isOffline": true,
      "operateTime": 0,
      "user": {
        "id": 242,
        "nickname": "吼吼吼",
        "nicknameModified": true,
        "avatar": "http://test-1251500528.file.myqcloud.com/hzp/463255D1-9667-4AC9-BE45-EE261FD39BA8.jpg",
        "avatarModified": true,
        "gender": 1,
        "genderModified": true,
        "mobileNumber": "15611869130",
        "ageLabel": 4,
        "birthday": "06-19",
        "pushToken": "bf4c03dba2d829a39fdb531e133c020496e9b62ba33c819524621ca74d6d2533",
        "pf": "iOS",
        "career": "经营管理",
        "personalProfile": "我去拯救地球了...",
        "zmScore": 0,
        "zmAuth": false,
        "constellation": "双子座",
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
        "zmAuthPushed": false,
        "infoCompleted": true,
        "flag": false,
        "privacy": 0,
        "forbidden": false,
        "virtual": false,
        "subscribe": false,
        "isForeign": false,
        "isAdministrators": false,
        "administratorStatus": 0,
        "realName": "",
        "certNo": "",
        "isScanCode": false,
        "subscribeFwh": false,
        "invitationCode": "HEZUQU174876E8F2",
        "invited": false,
        "isFacePerception": false,
        "authenticationStatus": 0,
        "source": 2,
        "migrate": 0,
        "isLogin": false
      }
    },
    {
      "id": 28436,
      "rent": 3000,
      "room": 1,
      "parlor": 1,
      "payment": "1",
      "rentType": "1",
      "communityId": 2300468,
      "cityId": 1,
      "areaId": 1142,
      "businessAreaId": 1203,
      "lon": 116.49203,
      "lat": 40.002902,
      "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp75c1aec6-0b7a-448a-9c93-9ff62c285213.jpg",
      "status": 4,
      "createTime": 1532348779233,
      "nearbySubways": "677835,1101618,1241.0;572986,573111,1327.0;677835,573111,1327.0;677835,1101619,1367.0;677835,1101617,1775.0",
      "userId": 13310,
      "pictureCount": 3,
      "communityName": "融科橄榄城",
      "areaName": "朝阳",
      "businessAreaName": "望京",
      "updateTime": 1532348779233,
      "hasWIFI": false,
      "hasFridge": false,
      "hasAirConditioning": false,
      "hasWasher": false,
      "hasToilet": false,
      "hasShower": false,
      "hasHeating": false,
      "hasGas": false,
      "hasWardrobe": false,
      "hasKitchen": false,
      "hasTV": false,
      "hasSofa": false,
      "hasBalcony": false,
      "hasElevator": false,
      "hasBed": false,
      "subwayName": "14号线 15号线 14号线 14号线 14号线",
      "signedTime": 1532348779233,
      "toiletCount": 1,
      "subwayStationName": "望京南 望京 望京 阜通 高家园",
      "contractPlan": false,
      "isApartment": false,
      "isOffline": true,
      "operateTime": 0,
      "user": {
        "id": 13310,
        "nickname": "明世隐",
        "nicknameModified": true,
        "avatar": "http://test-1251500528.file.myqcloud.com/hzpa39e4ac0-42cd-4a1a-8d8b-e8ea20f7595e.jpg",
        "avatarModified": true,
        "gender": 1,
        "genderModified": true,
        "mobileNumber": "13521873762",
        "ageLabel": 1,
        "birthday": "07-23",
        "pf": "android",
        "career": "经营管理",
        "personalProfile": "我去拯救地球了...",
        "zmScore": 0,
        "zmAuth": false,
        "constellation": "狮子座",
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
        "zmAuthPushed": false,
        "infoCompleted": true,
        "flag": false,
        "privacy": 0,
        "forbidden": false,
        "virtual": false,
        "subscribe": false,
        "isForeign": false,
        "isAdministrators": false,
        "administratorStatus": 0,
        "realName": "张振东",
        "certNo": "111111111111111111",
        "isScanCode": false,
        "subscribeFwh": false,
        "invitationCode": "HEZUQU1748771BFE",
        "invited": true,
        "isFacePerception": false,
        "authenticationStatus": 2,
        "migrate": 0,
        "isLogin": false
      }
    },
    {
      "id": 28312,
      "rent": 2000,
      "room": 1,
      "parlor": 1,
      "payment": "1",
      "rentType": "1",
      "communityId": 379643,
      "cityId": 1,
      "areaId": 1142,
      "businessAreaId": 1203,
      "lon": 116.487544,
      "lat": 40.005106,
      "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/A7206E91-3401-41F5-8DB2-FBDAEC679E6C.jpg",
      "status": 4,
      "createTime": 1530862141203,
      "nearbySubways": "572986,573111,945.0;677835,573111,945.0;677835,1101619,1183.0;677835,1101618,1307.0;677835,1101620,1710.0",
      "userId": 242,
      "pictureCount": 3,
      "communityName": "宝星华庭",
      "areaName": "朝阳",
      "businessAreaName": "望京",
      "updateTime": 1530862141203,
      "hasWIFI": false,
      "hasFridge": false,
      "hasAirConditioning": false,
      "hasWasher": false,
      "hasToilet": false,
      "hasShower": false,
      "hasHeating": false,
      "hasGas": false,
      "hasWardrobe": false,
      "hasKitchen": false,
      "hasTV": false,
      "hasSofa": false,
      "hasBalcony": false,
      "hasElevator": false,
      "hasBed": false,
      "subwayName": "15号线 14号线 14号线 14号线 14号线",
      "toiletCount": 1,
      "subwayStationName": "望京 望京 阜通 望京南 东湖渠",
      "contractPlan": false,
      "isApartment": false,
      "isOffline": true,
      "operateTime": 0,
      "user": {
        "id": 242,
        "nickname": "吼吼吼",
        "nicknameModified": true,
        "avatar": "http://test-1251500528.file.myqcloud.com/hzp/463255D1-9667-4AC9-BE45-EE261FD39BA8.jpg",
        "avatarModified": true,
        "gender": 1,
        "genderModified": true,
        "mobileNumber": "15611869130",
        "ageLabel": 4,
        "birthday": "06-19",
        "pushToken": "bf4c03dba2d829a39fdb531e133c020496e9b62ba33c819524621ca74d6d2533",
        "pf": "iOS",
        "career": "经营管理",
        "personalProfile": "我去拯救地球了...",
        "zmScore": 0,
        "zmAuth": false,
        "constellation": "双子座",
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
        "zmAuthPushed": false,
        "infoCompleted": true,
        "flag": false,
        "privacy": 0,
        "forbidden": false,
        "virtual": false,
        "subscribe": false,
        "isForeign": false,
        "isAdministrators": false,
        "administratorStatus": 0,
        "realName": "",
        "certNo": "",
        "isScanCode": false,
        "subscribeFwh": false,
        "invitationCode": "HEZUQU174876E8F2",
        "invited": false,
        "isFacePerception": false,
        "authenticationStatus": 0,
        "source": 2,
        "migrate": 0,
        "isLogin": false
      }
    },
    {
      "id": 31341,
      "rent": 232,
      "readyTime": 1538092800000,
      "room": 1,
      "parlor": 1,
      "payment": "2",
      "rentType": "1",
      "communityId": 8182,
      "buildArea": 23,
      "cityId": 1,
      "areaId": 1142,
      "businessAreaId": 1203,
      "lon": 116.476415,
      "lat": 39.992226,
      "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/1f263bf772caab5cd2ff97f8f98b7646.jpg",
      "status": 2,
      "createTime": 1535448915219,
      "nearbySubways": "677835,1101619,629.0;677835,1101618,648.0;572986,573111,1318.0;677835,573111,1318.0;677835,1101617,1615.0",
      "userId": 555915,
      "pictureCount": 3,
      "violationReason": "",
      "communityName": "望京大厦",
      "areaName": "朝阳",
      "businessAreaName": "望京",
      "updateTime": 1535449065941,
      "ip": "10.141.159.122",
      "hasWIFI": false,
      "hasFridge": false,
      "hasAirConditioning": false,
      "hasWasher": false,
      "hasToilet": false,
      "hasShower": false,
      "hasHeating": false,
      "hasGas": false,
      "hasWardrobe": false,
      "hasKitchen": false,
      "hasTV": false,
      "hasSofa": false,
      "hasBalcony": false,
      "hasElevator": false,
      "hasBed": true,
      "description": "333333333333333333333333",
      "subwayName": "14号线 14号线 15号线 14号线 14号线",
      "identity": 1,
      "toiletCount": 1,
      "subwayStationName": "阜通 望京南 望京 望京 高家园",
      "contractPlan": true,
      "isApartment": false,
      "isOffline": false,
      "operateTime": 0,
      "user": {
        "id": 555915,
        "nickname": "白富美",
        "nicknameModified": true,
        "avatar": "http://test-1251500528.file.myqcloud.com/hzp/45eb790dcb54fe6b0f6f2f6d2d4f703f103",
        "avatarModified": true,
        "gender": 2,
        "genderModified": true,
        "mobileNumber": "15901066088",
        "ageLabel": 4,
        "birthday": "01-02",
        "pf": "android",
        "career": "金融经济",
        "personalProfile": "我去拯救地球了...",
        "zmScore": 0,
        "zmAuth": false,
        "constellation": "摩羯座",
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
        "zmAuthPushed": false,
        "infoCompleted": true,
        "flag": false,
        "privacy": 0,
        "forbidden": false,
        "virtual": false,
        "subscribe": false,
        "isForeign": false,
        "isAdministrators": false,
        "administratorStatus": 0,
        "realName": "韩雪松",
        "certNo": "272323199210070910",
        "isScanCode": false,
        "subscribeFwh": false,
        "invitationCode": "HEZUQU17487F638B",
        "invited": false,
        "authenticationStatus": 0,
        "migrate": 0,
        "isLogin": true
      }
    },
    {
      "id": 145,
      "rent": 500,
      "readyTime": 1528905600000,
      "room": 1,
      "parlor": 1,
      "payment": "2",
      "rentType": "1",
      "communityId": 10818,
      "buildArea": 600,
      "cityId": 1,
      "areaId": 1142,
      "businessAreaId": 1203,
      "lon": 116.482004,
      "lat": 40.004341,
      "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzpc796e73b-32ba-498a-a77e-bff48f228713.jpg",
      "status": 4,
      "createTime": 1528961986348,
      "nearbySubways": "572986,573111,466.0;677835,573111,466.0;677835,1101619,823.0;677835,1101618,1191.0;677835,1101620,1499.0",
      "userId": 228,
      "pictureCount": 3,
      "outTime": 1529387206258,
      "communityName": "绿荫芳邻",
      "areaName": "朝阳",
      "businessAreaName": "望京",
      "updateTime": 1529464295732,
      "ip": "10.141.159.122",
      "hasWIFI": false,
      "hasFridge": false,
      "hasAirConditioning": false,
      "hasWasher": true,
      "hasToilet": false,
      "hasShower": false,
      "hasHeating": false,
      "hasGas": false,
      "hasWardrobe": true,
      "hasKitchen": false,
      "hasTV": false,
      "hasSofa": false,
      "hasBalcony": true,
      "hasElevator": false,
      "hasBed": true,
      "description": "哦婆婆松坡婆婆说松坡婆婆婆婆哦哦破哦婆婆婆婆送",
      "subwayName": "15号线 14号线 14号线 14号线 14号线",
      "signedTime": 1529555883673,
      "identity": 5,
      "toiletCount": 1,
      "subwayStationName": "望京 望京 阜通 望京南 东湖渠",
      "contractPlan": false,
      "isApartment": true,
      "isOffline": false,
      "operateTime": 0,
      "user": {
        "id": 228,
        "nickname": "房管元",
        "nicknameModified": true,
        "avatar": "http://test-1251500528.file.myqcloud.com/hzp35258a32-69a5-4b23-8107-1dd504eb7720.jpg",
        "avatarModified": true,
        "gender": 1,
        "genderModified": true,
        "ageLabel": 1,
        "birthday": "06-14",
        "pushToken": "AneAA6239h7SuXbOQW_iouV7plSYiDMaApfggmy7l5mb",
        "pf": "android",
        "career": "房地产",
        "personalProfile": "我去拯救地球了...",
        "zmScore": 0,
        "zmAuth": false,
        "constellation": "双子座",
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
        "zmAuthPushed": false,
        "infoCompleted": true,
        "flag": false,
        "privacy": 0,
        "forbidden": false,
        "virtual": false,
        "subscribe": false,
        "isForeign": false,
        "isAdministrators": true,
        "apartmentName": "我爱我家",
        "apartmentCityId": 1,
        "administratorStatus": 1,
        "verifyTime": 0,
        "realName": "张振东",
        "certNo": "410782199206254736",
        "isScanCode": false,
        "subscribeFwh": false,
        "invitationCode": "HEZUQU174876E8E4",
        "invited": true,
        "apartmentId": 11019,
        "brand": "我爱我家",
        "isFacePerception": false,
        "authenticationStatus": 0,
        "source": 2,
        "migrate": 0,
        "isLogin": false
      }
    },
    {
      "id": 31217,
      "rent": 500,
      "room": 1,
      "parlor": 1,
      "payment": "2",
      "rentType": "1",
      "communityId": 379949,
      "cityId": 1,
      "areaId": 1142,
      "businessAreaId": 1203,
      "lon": 116.484439,
      "lat": 40.002867,
      "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/AB841A77-2956-46B2-8433-9FAAB561C8A2.jpg",
      "status": 4,
      "createTime": 1534476243705,
      "nearbySubways": "572986,573111,686.0;677835,573111,686.0;677835,1101619,820.0;677835,1101618,1019.0;677835,1101620,1745.0;677835,1101617,1946.0",
      "userId": 555759,
      "pictureCount": 3,
      "communityName": "合生麒麟社",
      "areaName": "朝阳",
      "businessAreaName": "望京",
      "updateTime": 1534476243705,
      "hasWIFI": false,
      "hasFridge": false,
      "hasAirConditioning": false,
      "hasWasher": false,
      "hasToilet": false,
      "hasShower": false,
      "hasHeating": false,
      "hasGas": false,
      "hasWardrobe": false,
      "hasKitchen": false,
      "hasTV": false,
      "hasSofa": false,
      "hasBalcony": false,
      "hasElevator": false,
      "hasBed": false,
      "subwayName": "15号线 14号线 14号线 14号线 14号线 14号线",
      "signedTime": 1534476243705,
      "toiletCount": 1,
      "subwayStationName": "望京 望京 阜通 望京南 东湖渠 高家园",
      "contractPlan": false,
      "isApartment": false,
      "isOffline": true,
      "operateTime": 0,
      "user": {
        "id": 555759,
        "nickname": "P24213",
        "nicknameModified": false,
        "avatar": "http://test-1251500528.file.myqcloud.com/hzp/36C9FBF2-71E9-4E89-B0ED-D4406851EE3D.jpg",
        "avatarModified": false,
        "gender": 3,
        "genderModified": false,
        "mobileNumber": "15279055744",
        "ageLabel": 0,
        "pushToken": "d62fcfaefdde452fdde4d17d3bd6039fde4aec7d3f11f0bac96683169a9f5694",
        "pf": "iOS",
        "career": "小可爱",
        "personalProfile": "我去拯救地球了...",
        "zmScore": 0,
        "zmAuth": false,
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
        "zmAuthPushed": false,
        "infoCompleted": false,
        "flag": false,
        "privacy": 0,
        "forbidden": false,
        "virtual": false,
        "subscribe": false,
        "isForeign": false,
        "isAdministrators": true,
        "apartmentName": "自如皇家公司",
        "apartmentCityId": 1,
        "administratorStatus": 2,
        "verifyTime": 1534475633791,
        "realName": "邓金龙",
        "certNo": "360122199212303318",
        "isScanCode": false,
        "subscribeFwh": false,
        "invitationCode": "HEZUQU17487F62EF",
        "invited": false,
        "apartmentId": 11005,
        "brand": "自如管家",
        "isFacePerception": true,
        "authenticationStatus": 1,
        "source": 2,
        "migrate": 0,
        "isLogin": true
      }
    }
  ]
}
```

### 推荐houserequest列表
##### 接口:/HouseRequestController/commendHouseRequest
##### 请求方式:GET
##### 接口参数
|参数名|类型|描述|是否必须|
|---|---|---|---|
|id|Long|发布的房源ID|是|
|startTime|long|开始时间|是|
|endTime|long|结束时间|是|
##### 成功返回值
```
{
  "ret": 200,
  "data": [
    {
      "id": 9118,
      "description": "啦咯啦咯啦咯啦咯啦咯啦咯啦咯啦咯啦咯啦咯啦",
      "expectedLocation": "1203",
      "expectedLocations": "望京",
      "expectedAreas": "1142",
      "expectedAreaNames": "朝阳",
      "expectedTime": 1535339393000,
      "startRent": 0,
      "endRent": 5000,
      "cityId": 1,
      "status": 1,
      "createTime": 1535339415129,
      "userId": 555870,
      "updateTime": 1537513838233,
      "pictureCount": 0,
      "expectedSubwayStationId": "236765",
      "expectedSubwayStationName": "西直门",
      "expectedSubwayId": "236717",
      "expectedSubwayName": "2号线",
      "operateTime": 1537522302874,
      "user": {
        "id": 555870,
        "nickname": "测试9144",
        "nicknameModified": true,
        "avatar": "http://test-1251500528.file.myqcloud.com/hzp/BD26B58B-FCAB-45B9-B8C4-DCE360AA8477.jpg",
        "avatarModified": true,
        "gender": 2,
        "genderModified": true,
        "mobileNumber": "15611869144",
        "ageLabel": 5,
        "birthday": "08-24",
        "pf": "iOS",
        "career": "贸易销售",
        "personalProfile": "我去拯救地球了...",
        "zmScore": 0,
        "zmAuth": false,
        "constellation": "处女座",
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
        "zmAuthPushed": false,
        "infoCompleted": true,
        "flag": false,
        "privacy": 0,
        "forbidden": false,
        "virtual": false,
        "subscribe": false,
        "isForeign": false,
        "isAdministrators": false,
        "administratorStatus": 0,
        "isScanCode": false,
        "subscribeFwh": false,
        "invitationCode": "HEZUQU17487F635E",
        "invited": false,
        "authenticationStatus": 0,
        "migrate": 0,
        "isLogin": true
      }
    },
    {
      "id": 9124,
      "description": "大大大大大大大大大哥别杀我，我我我我我我我我我把枪都给你",
      "expectedLocation": "1203",
      "expectedLocations": "望京",
      "expectedAreas": "1142",
      "expectedAreaNames": "朝阳",
      "expectedTime": 1537171954000,
      "startRent": 0,
      "endRent": 6900,
      "cityId": 1,
      "status": 1,
      "createTime": 1537172055088,
      "userId": 556018,
      "outTime": 1537260242830,
      "updateTime": 1537261546136,
      "pictureCount": 0,
      "expectedSubwayStationId": "",
      "expectedSubwayId": "",
      "operateTime": 1537520995792,
      "user": {
        "id": 556018,
        "nickname": "我们去大草原",
        "nicknameModified": true,
        "avatar": "https://wx.qlogo.cn/mmopen/vi_32/ZLhicyPutHBNRkQIZAUzHEFA2a25hp7la6f2GxVltZSbzc0AzGnO3pWQ0QBibAvLbm4UU3GqLHJC980srYNqAeuA/132",
        "avatarModified": true,
        "gender": 2,
        "genderModified": true,
        "mobileNumber": "17110001016",
        "ageLabel": 1,
        "birthday": "01-01",
        "pushToken": "2321f2cbd8f0f1f8a7f110763e0030468d83cc39dc200855884a7ac9dc64e93b",
        "pf": "iOS",
        "career": "经营管理",
        "personalProfile": "我去拯救地球了...",
        "zmScore": 0,
        "zmAuth": false,
        "constellation": "摩羯座",
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
        "zmAuthPushed": false,
        "infoCompleted": true,
        "flag": false,
        "privacy": 0,
        "forbidden": false,
        "virtual": false,
        "subscribe": false,
        "isForeign": false,
        "isAdministrators": false,
        "administratorStatus": 0,
        "isScanCode": false,
        "subscribeFwh": false,
        "invitationCode": "HEZUQU17487F63F2",
        "invited": false,
        "authenticationStatus": 2,
        "migrate": 0,
        "isLogin": true
      }
    },
    {
      "id": 9128,
      "description": "后管理机构过敏吗管理机构建立后去去去想去上学q y",
      "expectedLocation": "1203",
      "expectedLocations": "望京",
      "expectedAreas": "1142",
      "expectedAreaNames": "朝阳",
      "expectedTime": 1537516730000,
      "startRent": 0,
      "endRent": 5000,
      "cityId": 1,
      "status": 1,
      "createTime": 1537516757279,
      "userId": 556037,
      "updateTime": 1537516757279,
      "pictureCount": 0,
      "expectedSubwayStationId": "",
      "expectedSubwayId": "",
      "operateTime": 1537516757279,
      "user": {
        "id": 556037,
        "nickname": "5411",
        "nicknameModified": true,
        "avatar": "http://test-1251500528.file.myqcloud.com/hzp/EC5A73E2-7984-472C-A0E7-A1FFAD105685.jpg",
        "avatarModified": true,
        "gender": 2,
        "genderModified": true,
        "mobileNumber": "15279055411",
        "ageLabel": 4,
        "birthday": "09-17",
        "pushToken": "62e5fa26040d6211f7bee07d4995305065983f655838a8bf840aea1914bb2872",
        "pf": "iOS",
        "career": "公关市场",
        "personalProfile": "我去拯救地球了...",
        "zmScore": 0,
        "zmAuth": false,
        "constellation": "处女座",
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
        "zmAuthPushed": false,
        "infoCompleted": true,
        "flag": false,
        "privacy": 0,
        "forbidden": false,
        "virtual": false,
        "subscribe": false,
        "isForeign": false,
        "isAdministrators": false,
        "administratorStatus": 0,
        "isScanCode": false,
        "subscribeFwh": false,
        "invitationCode": "HEZUQU17487F6405",
        "invited": false,
        "authenticationStatus": 0,
        "migrate": 0,
        "isLogin": true
      }
    },
    {
      "id": 76,
      "description": "术语求组队形成什么的吗嗯我的，/::< 兔肉麻辣烫里有，",
      "expectedLocation": "1203 5994",
      "expectedLocations": "望京 奥林匹克公园",
      "expectedAreas": "1142 1142",
      "expectedAreaNames": "朝阳 朝阳",
      "expectedTime": 1528416000000,
      "startRent": 0,
      "endRent": 5300,
      "cityId": 1,
      "status": 2,
      "createTime": 1528423843341,
      "userId": 216,
      "violationReason": "",
      "outTime": 1528683223927,
      "updateTime": 1528697775336,
      "pictureCount": 2,
      "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/03fea031418de4827c7761ebe8aafe9961",
      "expectedSubwayStationId": "1101618",
      "expectedSubwayStationName": "望京南",
      "expectedSubwayId": "677835",
      "expectedSubwayName": "14号线",
      "operateTime": 0,
      "user": {
        "id": 216,
        "nickname": "萌了",
        "nicknameModified": true,
        "avatar": "https://wx.qlogo.cn/mmopen/vi_32/ZLhicyPutHBNRkQIZAUzHEFA2a25hp7la6f2GxVltZSbzc0AzGnO3pWQ0QBibAvLbmVOEKZiakfjMGcEok1qpYYdg/132",
        "avatarModified": true,
        "gender": 2,
        "genderModified": true,
        "mobileNumber": "17190171888",
        "ageLabel": 5,
        "birthday": "04-01",
        "pushToken": "AnR-ShYHR7_kzUJ9NJd4cvpxnV2OB7Hsyas40tiAI0Kh",
        "pf": "android",
        "career": "法律",
        "personalProfile": "我去拯救地球了...",
        "zmScore": 0,
        "zmAuth": false,
        "constellation": "白羊座",
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
        "zmAuthPushed": false,
        "infoCompleted": true,
        "flag": false,
        "privacy": 0,
        "forbidden": false,
        "virtual": false,
        "subscribe": false,
        "isForeign": false,
        "isAdministrators": false,
        "administratorStatus": 0,
        "isScanCode": false,
        "subscribeFwh": false,
        "invitationCode": "HEZUQU174876E8D8",
        "invited": false,
        "isFacePerception": false,
        "authenticationStatus": 0,
        "migrate": 0,
        "isLogin": false
      }
    },
    {
      "id": 64,
      "description": "头额咳咳咳咳咳咳可口木木杜甫墓福特偷渡诺特特特特头木木木多头屠夫恶徒嘟嘟屠夫图图腾木木木欧诺",
      "expectedLocation": "1203",
      "expectedLocations": "望京",
      "expectedAreas": "1142",
      "expectedAreaNames": "朝阳",
      "expectedTime": 1610121600000,
      "startRent": 1200,
      "endRent": 1000000,
      "cityId": 1,
      "status": 4,
      "createTime": 1527493045956,
      "userId": 202,
      "updateTime": 1527493045956,
      "pictureCount": 1,
      "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp35ffaaa2-f855-4c8d-968d-ad61d78a9d85.jpg",
      "signedTime": 1527495915011,
      "expectedSubwayStationId": "573111",
      "expectedSubwayStationName": "望京",
      "expectedSubwayId": "572986",
      "expectedSubwayName": "15号线",
      "operateTime": 0,
      "user": {
        "id": 202,
        "nickname": "叶子",
        "nicknameModified": true,
        "avatar": "http://test-1251500528.file.myqcloud.com/hzp60d1af43-09ae-4951-a025-80e6a1dd72b2.jpg",
        "avatarModified": true,
        "gender": 2,
        "genderModified": true,
        "mobileNumber": "18201370499",
        "ageLabel": 1,
        "birthday": "05-28",
        "pf": "android",
        "career": "其他",
        "personalProfile": "以前总觉得时间可以任意挥霍，如今竟然对它斤斤计较起来。",
        "zmScore": 0,
        "zmAuth": false,
        "constellation": "双子座",
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
        "zmAuthPushed": false,
        "infoCompleted": true,
        "flag": false,
        "privacy": 0,
        "forbidden": false,
        "virtual": false,
        "subscribe": false,
        "isForeign": false,
        "isAdministrators": false,
        "administratorStatus": 0,
        "isScanCode": false,
        "subscribeFwh": false,
        "invitationCode": "HEZUQU174876E8CA",
        "invited": false,
        "isFacePerception": false,
        "authenticationStatus": 0,
        "migrate": 0,
        "isLogin": false
      }
    },
    {
      "id": 29,
      "description": "室友必须得好哈哈哈哈哈或hh哈哈哈哈哈哈",
      "expectedLocation": "1203",
      "expectedLocations": "望京",
      "expectedAreas": "1142",
      "expectedAreaNames": "朝阳",
      "expectedTime": 1,
      "startRent": 0,
      "endRent": 6000,
      "cityId": 1,
      "status": 2,
      "createTime": 1524555392218,
      "userId": 122,
      "violationReason": "",
      "outTime": 1525420007436,
      "updateTime": 1525420056641,
      "pictureCount": 1,
      "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/bbeaac1d4aa5dd3508391d86dd1b6dac103",
      "expectedSubwayStationId": "236742 236743",
      "expectedSubwayStationName": "苹果园 古城路",
      "expectedSubwayId": "236713 236713",
      "expectedSubwayName": "1号线 1号线",
      "operateTime": 0,
      "user": {
        "id": 122,
        "nickname": "婷",
        "nicknameModified": true,
        "avatar": "https://wx.qlogo.cn/mmopen/vi_32/Q0j4TwGTfTKoVicJa9T7Ct7CkrC2cDnd0tUfJnbxhA6AJysLll1WHvxtOl4iceic4HO5YHKv142Krg8PoMzqAahEw/0",
        "avatarModified": true,
        "gender": 2,
        "genderModified": true,
        "mobileNumber": "15834102126",
        "ageLabel": 3,
        "birthday": "02-01",
        "pf": "WEB",
        "career": "码农",
        "favorite": "美食,旅游,电影",
        "personalProfile": "我去拯救地球了...",
        "zmScore": 0,
        "zmAuth": false,
        "constellation": "水瓶座",
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
        "zmAuthPushed": false,
        "infoCompleted": true,
        "flag": false,
        "privacy": 0,
        "forbidden": false,
        "virtual": false,
        "subscribe": false,
        "isForeign": false,
        "isAdministrators": false,
        "administratorStatus": 0,
        "isScanCode": false,
        "subscribeFwh": false,
        "invitationCode": "HEZUQU174876E87A",
        "invited": false,
        "isFacePerception": false,
        "authenticationStatus": 0,
        "migrate": 0,
        "isLogin": false
      }
    },
    {
      "id": 20,
      "description": "性格非常好啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊",
      "expectedLocation": "1203 1193",
      "expectedLocations": "望京 亚运村",
      "expectedAreas": "1142 1142",
      "expectedAreaNames": "朝阳 朝阳",
      "expectedTime": 1,
      "startRent": 0,
      "endRent": 6000,
      "cityId": 1,
      "status": 4,
      "createTime": 1523587533713,
      "userId": 85,
      "updateTime": 1523587533713,
      "pictureCount": 1,
      "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/3311e7fc391a4729d8d52b36c4afd846103",
      "signedTime": 1523964402269,
      "operateTime": 0,
      "user": {
        "id": 85,
        "nickname": "L  T",
        "nicknameModified": false,
        "avatar": "https://wx.qlogo.cn/mmopen/vi_32/Q0j4TwGTfTKufwOp2wDiaWiaguliboEc3fFtn5F9RsvqU1TvgTSw0v5OeIL1gGt2knZoKlicDALJiaHrhgKyTtStztg/132",
        "avatarModified": true,
        "gender": 2,
        "genderModified": false,
        "mobileNumber": "13011298825",
        "ageLabel": 3,
        "birthday": "01-04",
        "openId": "oTHJ80Zi81hjTDStOjL1l-_uX8g4",
        "unionId": "o_M7e0wWLLTWf_4TPorm_-GR2K5w",
        "pf": "WEB",
        "career": "保密",
        "favorite": "美食,旅游,电影,摄影",
        "personalProfile": "我去拯救地球了...",
        "zmScore": 740,
        "zmAuth": true,
        "constellation": "摩羯座",
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
        "zmAuthPushed": true,
        "infoCompleted": true,
        "flag": false,
        "privacy": 0,
        "forbidden": false,
        "virtual": false,
        "mpOpenId": "o-x4r5GGn4n2xVFVbeHeKNNshU1s",
        "subscribe": false,
        "isForeign": false,
        "isAdministrators": false,
        "administratorStatus": 0,
        "isScanCode": false,
        "subscribeFwh": false,
        "invitationCode": "HEZUQU174876E855",
        "invited": false,
        "isFacePerception": false,
        "authenticationStatus": 0,
        "migrate": 0,
        "isLogin": false
      }
    },
    {
      "id": 9122,
      "description": "木楼摩托头诺路路通考虑噜噜噜踏踏图考虑吕布踏踏噜噜噜噜啊哦哦哦",
      "expectedLocation": "1203",
      "expectedLocations": "望京",
      "expectedAreas": "1142",
      "expectedAreaNames": "朝阳",
      "expectedTime": 1,
      "startRent": 0,
      "endRent": 5000,
      "cityId": 1,
      "status": 1,
      "createTime": 1536649668572,
      "userId": 556014,
      "updateTime": 1536654457400,
      "pictureCount": 0,
      "listImageUrl": "",
      "expectedSubwayStationId": "",
      "expectedSubwayId": "",
      "operateTime": 0,
      "user": {
        "id": 556014,
        "nickname": "客运站",
        "nicknameModified": true,
        "avatar": "https://wx.qlogo.cn/mmopen/vi_32/K1qzYQaht3W71hyicBichtxRoiaKkzGlrxoXU8hngYxibLuzrm3k2TNOticIIqN3Y2ibwaJl3victib42udrY47Z5Qajcg/132",
        "avatarModified": true,
        "gender": 1,
        "genderModified": true,
        "mobileNumber": "15105827777",
        "ageLabel": 1,
        "birthday": "01-01",
        "pushToken": "AoacZWXhZ3cycbV6XjwOIoKotIZR8cyGnckVbW0aN4g-",
        "pf": "android",
        "career": "经营管理",
        "personalProfile": "我去拯救地球了...",
        "zmScore": 0,
        "zmAuth": false,
        "constellation": "摩羯座",
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
        "zmAuthPushed": false,
        "infoCompleted": true,
        "flag": false,
        "privacy": 0,
        "forbidden": false,
        "virtual": false,
        "subscribe": false,
        "isForeign": false,
        "isAdministrators": false,
        "administratorStatus": 0,
        "realName": "石景梅",
        "certNo": "372928198812188529",
        "isScanCode": false,
        "subscribeFwh": false,
        "invitationCode": "HEZUQU17487F63EE",
        "invited": false,
        "authenticationStatus": 1,
        "migrate": 0,
        "isLogin": true
      }
    },
    {
      "id": 9123,
      "description": "里边有链接露明桶子咯家阿咖发了个拉黑🐰",
      "expectedLocation": "1203",
      "expectedLocations": "望京",
      "expectedAreas": "1142",
      "expectedAreaNames": "朝阳",
      "expectedTime": 1,
      "startRent": 0,
      "endRent": 5000,
      "cityId": 1,
      "status": 4,
      "createTime": 1536653646885,
      "userId": 556009,
      "outTime": 1536659952065,
      "updateTime": 1536659992730,
      "pictureCount": 0,
      "listImageUrl": "",
      "signedTime": 1536718474016,
      "expectedSubwayStationId": "",
      "expectedSubwayId": "",
      "operateTime": 0,
      "user": {
        "id": 556009,
        "nickname": "陌生1013",
        "nicknameModified": true,
        "avatar": "http://test-1251500528.file.myqcloud.com/hzp/d95b826f2b6589ff19612e1d205bce4b61",
        "avatarModified": true,
        "gender": 1,
        "genderModified": true,
        "mobileNumber": "17110001013",
        "ageLabel": 1,
        "birthday": "01-01",
        "pf": "WEB",
        "career": "经营管理",
        "personalProfile": "我去拯救地球了...",
        "zmScore": 0,
        "zmAuth": false,
        "constellation": "摩羯座",
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
        "zmAuthPushed": false,
        "infoCompleted": true,
        "flag": false,
        "privacy": 0,
        "forbidden": false,
        "virtual": false,
        "subscribe": false,
        "isForeign": false,
        "isAdministrators": false,
        "administratorStatus": 0,
        "realName": "康晨",
        "certNo": "11010419931017301X",
        "isScanCode": false,
        "subscribeFwh": false,
        "invitationCode": "HEZUQU17487F63E9",
        "invited": false,
        "authenticationStatus": 1,
        "migrate": 0,
        "isLogin": true
      }
    },
    {
      "id": 74,
      "description": "佳木斯大学毕业的事啊啊啊他说话啊哦哦里面的人都没办法了",
      "expectedLocation": "5994 1203",
      "expectedLocations": "奥林匹克公园 望京",
      "expectedAreas": "1142 1142",
      "expectedAreaNames": "朝阳 朝阳",
      "expectedTime": 1528329600000,
      "startRent": 0,
      "endRent": 6100,
      "cityId": 1,
      "status": 4,
      "createTime": 1528342100123,
      "userId": 139,
      "outTime": 1528356585342,
      "updateTime": 1528356603332,
      "pictureCount": 1,
      "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/0263d4febbd6dc1a80f6ab5654c2464361",
      "signedTime": 1528363164992,
      "expectedSubwayStationId": "573111",
      "expectedSubwayStationName": "望京",
      "expectedSubwayId": "572986",
      "expectedSubwayName": "15号线",
      "operateTime": 0,
      "user": {
        "id": 139,
        "nickname": "姐两",
        "nicknameModified": true,
        "avatar": "http://test-1251500528.file.myqcloud.com/hzp/66374D85-EC4C-4AE7-81EF-E28E9FAB89B7.jpg",
        "avatarModified": true,
        "gender": 1,
        "genderModified": true,
        "mobileNumber": "15910677555",
        "ageLabel": 4,
        "birthday": "09-04",
        "pf": "WEB",
        "career": "财务",
        "personalProfile": "我去拯救地球了...",
        "zmScore": 0,
        "zmAuth": false,
        "constellation": "处女座",
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
        "zmAuthPushed": true,
        "infoCompleted": true,
        "flag": false,
        "privacy": 0,
        "forbidden": false,
        "virtual": false,
        "mpOpenId": "o-x4r5DenWcq40s9vhGGddFbILhE",
        "subscribe": false,
        "isForeign": false,
        "isAdministrators": false,
        "administratorStatus": 0,
        "isScanCode": false,
        "subscribeFwh": false,
        "invitationCode": "HEZUQU174876E88B",
        "invited": false,
        "isFacePerception": false,
        "authenticationStatus": 0,
        "migrate": 0,
        "isLogin": false
      }
    },
    {
      "id": 48,
      "description": "123123312313123123123123",
      "expectedLocation": "1203",
      "expectedLocations": "望京",
      "expectedAreas": "1142",
      "expectedAreaNames": "朝阳",
      "expectedTime": 1,
      "startRent": 0,
      "endRent": 8000,
      "cityId": 1,
      "status": 2,
      "createTime": 1525882355154,
      "userId": 149,
      "violationReason": "",
      "outTime": 1525882657231,
      "updateTime": 1527150102581,
      "pictureCount": 1,
      "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/951ccbbb8c73de6e829e644c15508ccf103",
      "expectedSubwayStationId": "236742",
      "expectedSubwayStationName": "苹果园",
      "expectedSubwayId": "236713",
      "expectedSubwayName": "1号线",
      "operateTime": 0,
      "user": {
        "id": 149,
        "nickname": "bboy小松",
        "nicknameModified": false,
        "avatar": "https://wx.qlogo.cn/mmopen/vi_32/Q0j4TwGTfTKy3EjibgVhPianAf86zcMcSYHbTQNWEzyHc9MPXVmou1g1uwKY6Hv6TDjicmBQNVu7SMmCO6V41Vm0w/132",
        "avatarModified": false,
        "gender": 1,
        "genderModified": false,
        "mobileNumber": "15901066043",
        "ageLabel": 1,
        "birthday": "01-01",
        "openId": "ob2_D070HhLor0_Q4xuzDx7Eqeqo",
        "unionId": "",
        "pf": "iOS",
        "career": "IT互联网",
        "personalProfile": "我去拯救地球了...",
        "zmScore": 0,
        "zmAuth": false,
        "constellation": "摩羯座",
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
        "zmAuthPushed": false,
        "infoCompleted": true,
        "flag": false,
        "privacy": 0,
        "forbidden": false,
        "virtual": false,
        "mpOpenId": "oOKCt4haOJbNMYHvThAQkccwWQ3s",
        "subscribe": false,
        "isForeign": false,
        "isAdministrators": true,
        "apartmentName": "自如公寓",
        "apartmentCityId": 1,
        "administratorStatus": 2,
        "verifyTime": 0,
        "realName": "高晓琳",
        "certNo": "37092319950321152X",
        "isScanCode": true,
        "subscribeFwh": false,
        "invitationCode": "HEZUQU174876E895",
        "invited": true,
        "apartmentId": 11014,
        "brand": "自如公寓",
        "isFacePerception": false,
        "authenticationStatus": 1,
        "source": 2,
        "migrate": 0,
        "isLogin": false
      }
    },
    {
      "id": 57,
      "description": "给您咯楼get多扣欧诺热头欧诺搜搜set虐lol哦咯",
      "expectedLocation": "1203 1237",
      "expectedLocations": "望京 清华大学",
      "expectedAreas": "1142 1143",
      "expectedAreaNames": "朝阳 海淀",
      "expectedTime": 1,
      "startRent": 1300,
      "endRent": 7300,
      "cityId": 1,
      "status": 4,
      "createTime": 1504195200001,
      "userId": 161,
      "violationReason": "",
      "outTime": 1526366471201,
      "updateTime": 1526366315116,
      "pictureCount": 3,
      "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp2465f68a-e791-46df-997e-d312eecd3093.jpg",
      "signedTime": 1528773540024,
      "expectedSubwayStationId": "572985 1101618",
      "expectedSubwayStationName": "望京西 望京南",
      "expectedSubwayId": "572986 677835",
      "expectedSubwayName": "15号线 14号线",
      "operateTime": 0,
      "user": {
        "id": 161,
        "nickname": "黄蓉",
        "nicknameModified": true,
        "avatar": "http://test-1251500528.file.myqcloud.com/hzp1817db46-f278-4db4-bc1b-7f9c12f3df30.jpg",
        "avatarModified": true,
        "gender": 1,
        "genderModified": true,
        "mobileNumber": "15711367995",
        "ageLabel": 5,
        "birthday": "06-23",
        "pf": "android",
        "career": "客户服务",
        "favorite": "健身",
        "personalProfile": "因为害怕自己并非明珠而不敢刻苦琢磨，又因为有几分相信自己是明珠而不能与瓦砾碌碌为伍，遂逐渐远离时间，疏避人群，结果在内心不断地用愤懑和羞怒饲育着自己懦弱的自尊心，世上每个人都是驯兽师，而那匹猛兽，就是每个人各自的性情。",
        "zmScore": 0,
        "zmAuth": false,
        "constellation": "巨蟹座",
        "background": "http://test-1251500528.file.myqcloud.com/hzp3539be59-9907-4e6a-95ec-3a9de1be178f.jpg",
        "zmAuthPushed": true,
        "infoCompleted": true,
        "flag": false,
        "privacy": 0,
        "forbidden": false,
        "virtual": false,
        "subscribe": false,
        "isForeign": false,
        "isAdministrators": false,
        "administratorStatus": 0,
        "realName": "石园园",
        "certNo": "",
        "isScanCode": false,
        "subscribeFwh": false,
        "invitationCode": "HEZUQU174876E8A1",
        "invited": false,
        "isFacePerception": false,
        "authenticationStatus": 2,
        "migrate": 0,
        "isLogin": false
      }
    },
    {
      "id": 38,
      "description": "我们在这方面做出突出贡献中青年骨干企业初步形成的人在外面吃饭时不要用力地捶了我要吃好睡一点就更完美啦",
      "expectedLocation": "1203",
      "expectedLocations": "望京",
      "expectedAreas": "1142",
      "expectedAreaNames": "朝阳",
      "expectedTime": 1,
      "startRent": 0,
      "endRent": 5000,
      "cityId": 1,
      "status": 5,
      "createTime": 1524903197282,
      "userId": 138,
      "outTime": 1526721452915,
      "updateTime": 1526005086647,
      "pictureCount": 2,
      "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/0F7E8FD1-5821-437F-BF22-C062D995A2A4.jpg",
      "expectedSubwayStationId": "",
      "expectedSubwayId": "",
      "operateTime": 0,
      "user": {
        "id": 138,
        "nickname": "泰坦",
        "nicknameModified": true,
        "avatar": "http://test-1251500528.file.myqcloud.com/hzp/40C26F63-91E0-48C4-B19A-D87EE154C64A.jpg",
        "avatarModified": true,
        "gender": 1,
        "genderModified": true,
        "mobileNumber": "17190171058",
        "ageLabel": 4,
        "birthday": "04-28",
        "pf": "WEB",
        "career": "无业",
        "favorite": "摄影,健身,烘焙",
        "personalProfile": "我去拯救地球了...",
        "zmScore": 0,
        "zmAuth": false,
        "constellation": "金牛座",
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
        "zmAuthPushed": true,
        "infoCompleted": true,
        "flag": false,
        "privacy": 1,
        "forbidden": false,
        "virtual": false,
        "mpOpenId": "o-x4r5DenWcq40s9vhGGddFbILhE",
        "subscribe": false,
        "isForeign": false,
        "isAdministrators": false,
        "administratorStatus": 0,
        "isScanCode": false,
        "subscribeFwh": false,
        "invitationCode": "HEZUQU174876E88A",
        "invited": false,
        "isFacePerception": false,
        "authenticationStatus": 0,
        "migrate": 0,
        "isLogin": false
      }
    },
    {
      "id": 44,
      "description": "求租求租位置合适的，啊啊啊啊啊啊啊啊啊啊啊啊嗯哼哈哈哈哈哈哈DO YOU",
      "expectedLocation": "1203 6012",
      "expectedLocations": "望京 来广营",
      "expectedAreas": "1142 1142",
      "expectedAreaNames": "朝阳 朝阳",
      "expectedTime": 1,
      "startRent": 100,
      "endRent": 8000,
      "cityId": 1,
      "status": 3,
      "createTime": 1504195200001,
      "userId": 147,
      "violationReason": "图片不符合规范",
      "outTime": 1525935014805,
      "updateTime": 1525935084021,
      "pictureCount": 2,
      "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/9e9da43794f1b09ad19f111213e5a05245",
      "expectedSubwayStationId": "573111 1101619 573241 573171",
      "expectedSubwayStationName": "望京 阜通 立水桥南 惠新西街北口",
      "expectedSubwayId": "572986 677835 236718 236718",
      "expectedSubwayName": "15号线 14号线 5号线 5号线",
      "operateTime": 0,
      "user": {
        "id": 147,
        "nickname": "西瓜的人都就",
        "nicknameModified": true,
        "avatar": "http://test-1251500528.file.myqcloud.com/hzp/060d1555d20b62bfbd3b73e38670814945",
        "avatarModified": true,
        "gender": 1,
        "genderModified": true,
        "mobileNumber": "17611265966",
        "ageLabel": 5,
        "birthday": "12-01",
        "openId": "ob2_D06cjM68I9ofCUP1Afo5-syI",
        "unionId": "",
        "pf": "WEB",
        "career": "房地产",
        "favorite": "美食,旅游",
        "personalProfile": "没有签名才个性。咯路",
        "zmScore": 0,
        "zmAuth": false,
        "constellation": "射手座",
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
        "zmAuthPushed": true,
        "infoCompleted": true,
        "flag": false,
        "privacy": 1,
        "forbidden": false,
        "virtual": false,
        "mpOpenId": "oOKCt4piIMT0cRzKWk-IbpS-ucSQ",
        "subscribe": true,
        "isForeign": false,
        "isAdministrators": false,
        "administratorStatus": 0,
        "isScanCode": true,
        "subscribeFwh": false,
        "invitationCode": "HEZUQU174876E893",
        "invited": true,
        "isFacePerception": false,
        "authenticationStatus": 0,
        "migrate": 0,
        "isLogin": false
      }
    },
    {
      "id": 2,
      "description": "想找个离地铁近的，方便出行周边设施完善的地方",
      "expectedLocation": "6819 1203 1163",
      "expectedLocations": "牡丹园 望京 陶然亭",
      "expectedAreas": "1143 1142 1141",
      "expectedAreaNames": "海淀 朝阳 宣武",
      "expectedTime": 1,
      "startRent": 1000,
      "endRent": 3500,
      "cityId": 1,
      "status": 2,
      "createTime": 1522120884567,
      "userId": 1,
      "violationReason": "",
      "outTime": 1522756831110,
      "updateTime": 1522835410828,
      "pictureCount": 2,
      "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/245c471b890986c46053f85aca0d926545",
      "operateTime": 0,
      "user": {
        "id": 1,
        "nickname": "��",
        "nicknameModified": true,
        "avatar": "http://test-1251500528.file.myqcloud.com/hzp/6ed68153b9beb2dbcd4c1451c7c093f045",
        "avatarModified": true,
        "gender": 1,
        "genderModified": true,
        "mobileNumber": "",
        "ageLabel": 4,
        "birthday": "04-16",
        "openId": "",
        "unionId": "",
        "pf": "WEB",
        "career": "开飞机的",
        "favorite": "电影,读书,音乐,摄影,宅家,烘焙",
        "personalProfile": "等你发现时间是贼了，它早已偷光你的选择。",
        "zmScore": 0,
        "zmAuth": false,
        "constellation": "白羊座",
        "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
        "zmAuthPushed": true,
        "infoCompleted": true,
        "flag": false,
        "privacy": 1,
        "forbidden": true,
        "virtual": false,
        "subscribe": false,
        "isForeign": false,
        "isAdministrators": false,
        "administratorStatus": 0,
        "isScanCode": false,
        "subscribeFwh": false,
        "invitationCode": "HEZUQU174876E801",
        "invited": false,
        "isFacePerception": false,
        "authenticationStatus": 0,
        "migrate": 0,
        "isLogin": false
      }
    }
  ]
}
```

### 首页
##### 接口:/
##### 请求方式:GET
##### 成功返回值
```
{
  "ret": 200,
  "data": {
    "houses": [
      {
        "id": 31440,
        "rent": 2586,
        "readyTime": 1537844022730,
        "room": 1,
        "parlor": 1,
        "payment": "5",
        "rentType": "1",
        "communityId": 329,
        "buildArea": 25,
        "cityId": 1,
        "areaId": 1142,
        "businessAreaId": 1203,
        "lon": 116.489079,
        "lat": 40.005896,
        "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/A8742B32-BB04-4FB8-9B3D-D5A941A5BBFA.jpg",
        "status": 1,
        "createTime": 1537844066373,
        "nearbySubways": "572986,573111,1088.0;677835,573111,1088.0;677835,1101619,1339.0;677835,1101618,1428.0;677835,1101620,1744.0",
        "userId": 556041,
        "pictureCount": 1,
        "communityName": "宝星国际",
        "areaName": "朝阳",
        "businessAreaName": "望京",
        "updateTime": 1537951273080,
        "ip": "210.12.116.196",
        "hasWIFI": false,
        "hasFridge": true,
        "hasAirConditioning": false,
        "hasWasher": false,
        "hasToilet": false,
        "hasShower": false,
        "hasHeating": true,
        "hasGas": false,
        "hasWardrobe": false,
        "hasKitchen": false,
        "hasTV": true,
        "hasSofa": false,
        "hasBalcony": false,
        "hasElevator": false,
        "hasBed": true,
        "description": "啦啦啦啦啦啦啦德玛西亚啦啦啦啦啦啦啦啦啦啦啦啦啦啦啦啦啦啦啦啦啦啦啦啦啦啦啦",
        "subwayName": "15号线 14号线 14号线 14号线 14号线",
        "identity": 1,
        "toiletCount": 1,
        "subwayStationName": "望京 望京 阜通 望京南 东湖渠",
        "contractPlan": false,
        "isApartment": false,
        "isOffline": false,
        "operateTime": 1539592447147,
        "requirement": "爱护房子,不带异性过夜,不租情侣,作息正常,一家人",
        "forMiss": false,
        "user": {
          "id": 556041,
          "nickname": "9145",
          "nicknameModified": true,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzp/178D787C-F742-4BC2-B2DD-C6980BBB7951.jpg",
          "avatarModified": true,
          "gender": 2,
          "genderModified": true,
          "mobileNumber": "15611869145",
          "ageLabel": 3,
          "birthday": "09-18",
          "pushToken": "3f34993424d21dc14edffb50bc4ed8759ff025ab196f44ca74b9e83f55651e33",
          "pf": "iOS",
          "career": "公关市场",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "处女座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": true,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU17487F6409",
          "invited": false,
          "authenticationStatus": 0,
          "migrate": 0,
          "isLogin": true,
          "userProvincesId": 20,
          "userProvincesName": "山东",
          "userCityId": 944,
          "userCityName": "滨州",
          "schoolId": 5815,
          "schoolName": "山东理工大学"
        },
        "seenCount": "13",
        "redSwitch": true,
        "showOperateTime": "47秒前"
      },
      {
        "id": 31357,
        "rent": 1650,
        "readyTime": 1535512445383,
        "room": 2,
        "parlor": 1,
        "payment": "1",
        "rentType": "2",
        "communityId": 600352,
        "buildArea": 12,
        "cityId": 1,
        "areaId": 1142,
        "businessAreaId": 5782,
        "lon": 116.438569,
        "lat": 40.055578,
        "listImageUrl": "https://test-1251500528.file.myqcloud.com/hzp/bb1940c0722465889653c2e667694f1f.jpg",
        "status": 2,
        "createTime": 1535462974000,
        "nearbySubways": "236714,236790,782.0;236718,573241,1712.0;236718,236789,1758.0;236714,236789,1758.0",
        "userId": 555928,
        "pictureCount": 5,
        "violationReason": "",
        "communityName": "华贸城",
        "areaName": "朝阳",
        "businessAreaName": "北苑",
        "updateTime": 1535462974000,
        "hasWIFI": false,
        "hasFridge": true,
        "hasAirConditioning": true,
        "hasWasher": true,
        "hasToilet": true,
        "hasShower": true,
        "hasHeating": false,
        "hasGas": false,
        "hasWardrobe": true,
        "hasKitchen": true,
        "hasTV": true,
        "hasSofa": true,
        "hasBalcony": true,
        "hasElevator": true,
        "hasBed": true,
        "description": "13号地铁站附近\n【招女室友】房东直租，时间:九月一个月，如果你想在租一段时间可以自己和房东协商\n原因:合租的室友八月底就走了，但是我租到了九月，所以想找个室友跟我一起分摊房租\n地点：朝阳区清河营南街华贸城（距地铁13线10分钟左右，附近还有公交站，出门走几分钟就有超市，餐馆，麦当劳，还有电影院）\n小区情况:门口有保安，很安全，小区内环境也挺好的\n房屋情况：南北通透，二楼，次卧，家具家电齐全，房东一家人很好说话，冰箱，空调，微波炉，洗衣机都有，都可以用，拎包入住。\n价格：主卧1650元/月，另外水费，电费，网费统一50块一个月\n舍友要求：生活规律，爱护家中设施，晚上尽量早归，不酗酒，不留外人留宿\n联系方式：粲，微信:wang100qian100wen，电话:18389186710，欢迎骚扰。可以私聊看房子照片",
        "subwayName": "13号线 5号线 5号线 13号线",
        "toiletCount": 1,
        "subwayStationName": "北苑 立水桥南 立水桥 立水桥",
        "contractPlan": false,
        "isApartment": false,
        "crawlTime": 1535512446121,
        "isOffline": false,
        "operateTime": 1539590596441,
        "forMiss": false,
        "user": {
          "id": 555928,
          "nickname": "雨",
          "nicknameModified": true,
          "avatar": "https://test-1251500528.file.myqcloud.com/hzp/72c5c75d4c9415fd26118ba9b3ae709a.jpg",
          "avatarModified": false,
          "gender": 2,
          "genderModified": true,
          "mobileNumber": "18201370436",
          "ageLabel": 5,
          "birthday": "10-20",
          "pf": "android",
          "career": "金融经济",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "天秤座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": true,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": true,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU17487F6398",
          "invited": false,
          "authenticationStatus": 0,
          "activateTime": 1539055976334,
          "migrate": 0,
          "isLogin": true
        },
        "seenCount": "6",
        "redSwitch": true,
        "showOperateTime": "31分钟前"
      },
      {
        "id": 31303,
        "rent": 6666,
        "readyTime": 1,
        "room": 1,
        "parlor": 1,
        "payment": "2",
        "rentType": "1",
        "communityId": 1087596,
        "buildArea": 666,
        "cityId": 1,
        "areaId": 1150,
        "businessAreaId": 2640,
        "lon": 116.353351,
        "lat": 40.087459,
        "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/68dfce548bcdc4354bf78cd5cae0688a.png",
        "status": 1,
        "createTime": 1535367319410,
        "nearbySubways": "236719,677830,985.0;236719,634617,1400.0;236714,236787,1546.0;236714,236788,1582.0;236719,236788,1582.0;236719,677831,1796.0",
        "userId": 555871,
        "pictureCount": 3,
        "violationReason": "审核中",
        "outTime": 1536804732006,
        "communityName": "回龙观东别墅",
        "areaName": "昌平",
        "businessAreaName": "回龙观",
        "updateTime": 1539141138721,
        "ip": "210.12.116.196",
        "hasWIFI": false,
        "hasFridge": false,
        "hasAirConditioning": false,
        "hasWasher": false,
        "hasToilet": false,
        "hasShower": false,
        "hasHeating": false,
        "hasGas": false,
        "hasWardrobe": false,
        "hasKitchen": false,
        "hasTV": false,
        "hasSofa": false,
        "hasBalcony": false,
        "hasElevator": false,
        "hasBed": true,
        "description": "66666666666666666666666666",
        "subwayName": "8号线 8号线 13号线 13号线 8号线 8号线",
        "identity": 1,
        "toiletCount": 1,
        "subwayStationName": "平西府 回龙观东大街 回龙观 霍营 霍营 育知路",
        "contractPlan": true,
        "isApartment": false,
        "isOffline": false,
        "operateTime": 1539582968273,
        "forMiss": false,
        "user": {
          "id": 555871,
          "nickname": "漫舞",
          "nicknameModified": true,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzp/a746ed1287c44d92e3c5544068a690bf45",
          "avatarModified": true,
          "gender": 2,
          "genderModified": true,
          "mobileNumber": "15865206722",
          "ageLabel": 5,
          "birthday": "01-01",
          "pushToken": "fd95f035ad911b3da0b37451b8766bd7de658e4e2b8be728bef70b8ddb56eb50",
          "pf": "iOS",
          "career": "经营管理",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "摩羯座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": true,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU17487F635F",
          "invited": false,
          "authenticationStatus": 0,
          "migrate": 0,
          "isLogin": true
        },
        "seenCount": "1",
        "redSwitch": true,
        "showOperateTime": "2小时前"
      },
      {
        "id": 31463,
        "rent": 6000,
        "readyTime": 1,
        "room": 1,
        "parlor": 1,
        "payment": "2",
        "rentType": "1",
        "communityId": 379643,
        "buildArea": 23,
        "cityId": 1,
        "areaId": 1142,
        "businessAreaId": 1203,
        "lon": 116.487544,
        "lat": 40.005106,
        "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzpc3f16fb9-987e-4106-9f86-74207bd54ead.jpg",
        "status": 1,
        "createTime": 1539173996508,
        "nearbySubways": "572986,573111,945.0;677835,573111,945.0;677835,1101619,1183.0;677835,1101618,1307.0;677835,1101620,1710.0",
        "userId": 556088,
        "pictureCount": 1,
        "communityName": "宝星华庭",
        "areaName": "朝阳",
        "businessAreaName": "望京",
        "updateTime": 1539173996508,
        "ip": "106.39.84.154",
        "hasWIFI": true,
        "hasFridge": true,
        "hasAirConditioning": false,
        "hasWasher": false,
        "hasToilet": false,
        "hasShower": true,
        "hasHeating": true,
        "hasGas": true,
        "hasWardrobe": false,
        "hasKitchen": false,
        "hasTV": true,
        "hasSofa": true,
        "hasBalcony": false,
        "hasElevator": true,
        "hasBed": false,
        "description": "图了。😖😣😣😣😪😪😪😪😪😪😪😪😪😪😣😪😪😪",
        "subwayName": "15号线 14号线 14号线 14号线 14号线",
        "identity": 1,
        "toiletCount": 1,
        "subwayStationName": "望京 望京 阜通 望京南 东湖渠",
        "contractPlan": true,
        "isApartment": false,
        "isOffline": false,
        "operateTime": 1539312186675,
        "requirement": "",
        "forMiss": false,
        "user": {
          "id": 556088,
          "nickname": "1026",
          "nicknameModified": true,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzp850d5b33-fd7f-40b2-bd1e-db577b54f966.jpg",
          "avatarModified": true,
          "gender": 2,
          "genderModified": true,
          "mobileNumber": "17110001026",
          "ageLabel": 1,
          "birthday": "10-08",
          "pushToken": "AnR-ShYHR7_kzUJ9NJd4cvpxnV2OB7Hsyas40tiAI0Kh",
          "pf": "android",
          "career": "经营管理",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "天秤座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": true,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU17487F6438",
          "invited": false,
          "authenticationStatus": 0,
          "migrate": 0,
          "isLogin": true
        },
        "seenCount": "3",
        "redSwitch": true,
        "showOperateTime": "3天前"
      },
      {
        "id": 31455,
        "rent": 3737,
        "readyTime": 1537947980214,
        "room": 1,
        "parlor": 1,
        "payment": "5",
        "rentType": "1",
        "communityId": 601453,
        "buildArea": 464,
        "cityId": 1,
        "areaId": 1142,
        "businessAreaId": 1208,
        "lon": 116.491962,
        "lat": 40.002366,
        "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/66961B44-D7B4-4E5E-9D05-C6D9A4A3133E.jpg",
        "status": 1,
        "createTime": 1537948058558,
        "nearbySubways": "677835,1101618,1189.0;572986,573111,1328.0;677835,573111,1328.0;677835,1101619,1338.0;677835,1101617,1717.0",
        "userId": 556032,
        "pictureCount": 4,
        "communityName": "融科橄榄城三期",
        "areaName": "朝阳",
        "businessAreaName": "朝阳周边",
        "updateTime": 1537955611327,
        "ip": "210.12.116.196",
        "hasWIFI": false,
        "hasFridge": false,
        "hasAirConditioning": false,
        "hasWasher": true,
        "hasToilet": false,
        "hasShower": false,
        "hasHeating": false,
        "hasGas": false,
        "hasWardrobe": false,
        "hasKitchen": true,
        "hasTV": false,
        "hasSofa": false,
        "hasBalcony": false,
        "hasElevator": false,
        "hasBed": true,
        "description": "啊啊啊啊啊啊啊啊啊啊啊啊啊啊明明哦我也不知道为什么啊啊啊啊啊啊",
        "subwayName": "14号线 15号线 14号线 14号线 14号线",
        "identity": 1,
        "toiletCount": 3,
        "subwayStationName": "望京南 望京 望京 阜通 高家园",
        "contractPlan": true,
        "isApartment": false,
        "isOffline": false,
        "operateTime": 1539246625767,
        "requirement": "",
        "forMiss": false,
        "user": {
          "id": 556032,
          "nickname": "0110",
          "nicknameModified": true,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzp/484FF31D-2AE4-4C52-A17E-FA09FB493C29.jpg",
          "avatarModified": true,
          "gender": 2,
          "genderModified": true,
          "mobileNumber": "15011350110",
          "ageLabel": 5,
          "birthday": "09-14",
          "pushToken": "ceed5b89cd436868d073184d9fd2de5753ca1ac3fe7b25d8fd842f3a2280b933",
          "pf": "iOS",
          "career": "财务",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "处女座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": true,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU17487F6400",
          "invited": false,
          "authenticationStatus": 0,
          "migrate": 0,
          "isLogin": true,
          "userProvincesId": 16,
          "userProvincesName": "辽宁",
          "userCityId": 2354,
          "userCityName": "锦州",
          "schoolId": 5367,
          "schoolName": "复旦大学"
        },
        "seenCount": "20",
        "redSwitch": true,
        "showOperateTime": "4天前"
      },
      {
        "id": 31469,
        "rent": 2000,
        "readyTime": 1,
        "room": 1,
        "parlor": 1,
        "payment": "2",
        "rentType": "1",
        "communityId": 8182,
        "buildArea": 20,
        "cityId": 1,
        "areaId": 1142,
        "businessAreaId": 1203,
        "lon": 116.476415,
        "lat": 39.992226,
        "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/098c1af9ca5bd8899e86691a2867e328.jpg",
        "status": 1,
        "createTime": 1539245907816,
        "nearbySubways": "677835,1101619,629.0;677835,1101618,648.0;572986,573111,1318.0;677835,573111,1318.0;677835,1101617,1615.0",
        "userId": 556068,
        "pictureCount": 1,
        "communityName": "望京大厦",
        "areaName": "朝阳",
        "businessAreaName": "望京",
        "updateTime": 1539245907816,
        "ip": "210.12.116.196",
        "hasWIFI": false,
        "hasFridge": false,
        "hasAirConditioning": false,
        "hasWasher": false,
        "hasToilet": false,
        "hasShower": false,
        "hasHeating": false,
        "hasGas": false,
        "hasWardrobe": false,
        "hasKitchen": false,
        "hasTV": false,
        "hasSofa": false,
        "hasBalcony": false,
        "hasElevator": false,
        "hasBed": true,
        "description": "啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊111111",
        "subwayName": "14号线 14号线 15号线 14号线 14号线",
        "identity": 1,
        "toiletCount": 1,
        "subwayStationName": "阜通 望京南 望京 望京 高家园",
        "contractPlan": false,
        "isApartment": false,
        "isOffline": false,
        "operateTime": 1539245907816,
        "forMiss": false,
        "user": {
          "id": 556068,
          "nickname": "wxLT",
          "nicknameModified": true,
          "avatar": "https://wx.qlogo.cn/mmopen/vi_32/Q0j4TwGTfTKEIX41WPdfX2AZQuZiax78ls2RkISLThScBw1MfY9DGOyzeuK3Fq9LbxqmAONRp6LXNlqLAUoaWEA/132",
          "avatarModified": false,
          "gender": 2,
          "genderModified": false,
          "mobileNumber": "18404977721",
          "ageLabel": 4,
          "birthday": "09-29",
          "openId": "ob2_D0y1ds0sgcu_tAAkUeU0xDfk",
          "unionId": "o6EOJ1WkPwK-7GQcF1RA9gAdbTQw",
          "pf": "WEB",
          "career": "经营管理",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "天秤座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": true,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "mpOpenId": "oChIZ4845VMfC8miWP_h4SvQd5HA",
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU17487F6424",
          "invited": false,
          "authenticationStatus": 0,
          "migrate": 0,
          "isLogin": true
        },
        "seenCount": null,
        "redSwitch": true,
        "showOperateTime": "4天前"
      }
    ],
    "houseRequests": [
      {
        "id": 9132,
        "description": "啦啦啦啦啦啦啦啦啦啦啦啦啦啦啦到家咯你怎么样的",
        "expectedLocation": "5779",
        "expectedLocations": "双井",
        "expectedAreas": "1142",
        "expectedAreaNames": "朝阳",
        "expectedTime": 1537950882000,
        "startRent": 0,
        "endRent": 5000,
        "cityId": 1,
        "status": 1,
        "createTime": 1537950973554,
        "userId": 556041,
        "updateTime": 1537955058373,
        "pictureCount": 1,
        "listImageUrl": "http://test-1251500528.file.myqcloud.com/hzp/6F989591-C2D6-4B23-B9D4-9121B33DB222.jpg",
        "expectedSubwayStationId": "",
        "expectedSubwayId": "",
        "operateTime": 1539592447147,
        "requirement": "",
        "forMiss": false,
        "user": {
          "id": 556041,
          "nickname": "9145",
          "nicknameModified": true,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzp/178D787C-F742-4BC2-B2DD-C6980BBB7951.jpg",
          "avatarModified": true,
          "gender": 2,
          "genderModified": true,
          "mobileNumber": "15611869145",
          "ageLabel": 3,
          "birthday": "09-18",
          "pushToken": "3f34993424d21dc14edffb50bc4ed8759ff025ab196f44ca74b9e83f55651e33",
          "pf": "iOS",
          "career": "公关市场",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "处女座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": true,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU17487F6409",
          "invited": false,
          "authenticationStatus": 0,
          "migrate": 0,
          "isLogin": true,
          "userProvincesId": 20,
          "userProvincesName": "山东",
          "userCityId": 944,
          "userCityName": "滨州",
          "schoolId": 5815,
          "schoolName": "山东理工大学"
        },
        "seenCount": "13",
        "redSwitch": true,
        "showOperateTime": ""
      },
      {
        "id": 9147,
        "description": "123456877889988555544",
        "expectedLocation": "1203",
        "expectedLocations": "望京",
        "expectedAreas": "1142",
        "expectedAreaNames": "朝阳",
        "expectedTime": 1,
        "startRent": 0,
        "endRent": 5400,
        "cityId": 1,
        "status": 1,
        "createTime": 1539312070972,
        "userId": 556068,
        "updateTime": 1539312175766,
        "pictureCount": 0,
        "listImageUrl": "",
        "expectedSubwayStationId": "",
        "expectedSubwayId": "",
        "operateTime": 1539312175766,
        "forMiss": false,
        "user": {
          "id": 556068,
          "nickname": "wxLT",
          "nicknameModified": true,
          "avatar": "https://wx.qlogo.cn/mmopen/vi_32/Q0j4TwGTfTKEIX41WPdfX2AZQuZiax78ls2RkISLThScBw1MfY9DGOyzeuK3Fq9LbxqmAONRp6LXNlqLAUoaWEA/132",
          "avatarModified": false,
          "gender": 2,
          "genderModified": false,
          "mobileNumber": "18404977721",
          "ageLabel": 4,
          "birthday": "09-29",
          "openId": "ob2_D0y1ds0sgcu_tAAkUeU0xDfk",
          "unionId": "o6EOJ1WkPwK-7GQcF1RA9gAdbTQw",
          "pf": "WEB",
          "career": "经营管理",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "天秤座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": true,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "mpOpenId": "oChIZ4845VMfC8miWP_h4SvQd5HA",
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU17487F6424",
          "invited": false,
          "authenticationStatus": 0,
          "migrate": 0,
          "isLogin": true
        },
        "seenCount": null,
        "redSwitch": true,
        "showOperateTime": ""
      },
      {
        "id": 9142,
        "description": "啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊",
        "expectedLocation": "1203",
        "expectedLocations": "望京",
        "expectedAreas": "1142",
        "expectedAreaNames": "朝阳",
        "expectedTime": 1538215337000,
        "startRent": 0,
        "endRent": 5000,
        "cityId": 1,
        "status": 1,
        "createTime": 1538215372124,
        "userId": 556032,
        "updateTime": 1538215372124,
        "pictureCount": 0,
        "expectedSubwayStationId": "",
        "expectedSubwayId": "",
        "operateTime": 1539246625767,
        "forMiss": false,
        "user": {
          "id": 556032,
          "nickname": "0110",
          "nicknameModified": true,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzp/484FF31D-2AE4-4C52-A17E-FA09FB493C29.jpg",
          "avatarModified": true,
          "gender": 2,
          "genderModified": true,
          "mobileNumber": "15011350110",
          "ageLabel": 5,
          "birthday": "09-14",
          "pushToken": "ceed5b89cd436868d073184d9fd2de5753ca1ac3fe7b25d8fd842f3a2280b933",
          "pf": "iOS",
          "career": "财务",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "处女座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": true,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU17487F6400",
          "invited": false,
          "authenticationStatus": 0,
          "migrate": 0,
          "isLogin": true,
          "userProvincesId": 16,
          "userProvincesName": "辽宁",
          "userCityId": 2354,
          "userCityName": "锦州",
          "schoolId": 5367,
          "schoolName": "复旦大学"
        },
        "seenCount": "20",
        "redSwitch": true,
        "showOperateTime": ""
      },
      {
        "id": 9146,
        "description": "11111111111111111111111111",
        "expectedLocation": "1203",
        "expectedLocations": "望京",
        "expectedAreas": "1142",
        "expectedAreaNames": "朝阳",
        "expectedTime": 1,
        "startRent": 700,
        "endRent": 5800,
        "cityId": 1,
        "status": 1,
        "createTime": 1539246073937,
        "userId": 556094,
        "updateTime": 1539246073937,
        "pictureCount": 0,
        "listImageUrl": "",
        "expectedSubwayStationId": "1101619",
        "expectedSubwayStationName": "阜通",
        "expectedSubwayId": "677835",
        "expectedSubwayName": "14号线",
        "operateTime": 1539246073937,
        "forMiss": false,
        "user": {
          "id": 556094,
          "nickname": "1111",
          "nicknameModified": true,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzp/95fac39037e87a243ce21c6719517734103",
          "avatarModified": true,
          "gender": 2,
          "genderModified": true,
          "mobileNumber": "13011291111",
          "ageLabel": 2,
          "birthday": "01-01",
          "pf": "WEB",
          "career": "经营管理",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "摩羯座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": true,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU17487F643E",
          "invited": false,
          "authenticationStatus": 0,
          "migrate": 0,
          "isLogin": true
        },
        "seenCount": "3",
        "redSwitch": true,
        "showOperateTime": ""
      },
      {
        "id": 9130,
        "description": "流量监控哦摸摸摸摸摸摸浓浓的环球时尚家居可口可乐了看看",
        "expectedLocation": "6856",
        "expectedLocations": "椿树街道",
        "expectedAreas": "1141",
        "expectedAreaNames": "宣武",
        "expectedTime": 1538323200000,
        "startRent": 0,
        "endRent": 1000000,
        "cityId": 1,
        "status": 1,
        "createTime": 1537867697427,
        "userId": 555965,
        "updateTime": 1537867697427,
        "pictureCount": 0,
        "listImageUrl": "",
        "expectedSubwayStationId": "",
        "expectedSubwayId": "",
        "operateTime": 1539223299108,
        "requirement": "爱干净,爱护房子,不带异性过夜,不吸烟,不租情侣,作息正常,工作稳定,不养宠物",
        "forMiss": false,
        "user": {
          "id": 555965,
          "nickname": "匿名",
          "nicknameModified": true,
          "avatar": "http://test-1251500528.file.myqcloud.com/hzpe2b2fa6e-bfdb-49df-b22d-46d525187063.jpg",
          "avatarModified": true,
          "gender": 2,
          "genderModified": true,
          "mobileNumber": "15665438756",
          "ageLabel": 1,
          "birthday": "09-04",
          "pushToken": "AneAA6239h7SuXbOQW_iouWEM8UKllPDm4msOZoRbo53",
          "pf": "android",
          "career": "机械",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "处女座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": true,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "realName": "陈从凯",
          "certNo": "370623197312194215",
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU17487F63BD",
          "invited": false,
          "authenticationStatus": 1,
          "migrate": 0,
          "isLogin": true,
          "userProvincesId": 18,
          "userProvincesName": "内蒙古",
          "userCityId": 2043,
          "userCityName": "海拉尔",
          "schoolId": 5388,
          "schoolName": "北京航空航天大学"
        },
        "seenCount": "4",
        "redSwitch": true,
        "showOperateTime": ""
      },
      {
        "id": 9124,
        "description": "大大大大大大大大大哥别杀我，我我我我我我我我我把枪都给你",
        "expectedLocation": "1203",
        "expectedLocations": "望京",
        "expectedAreas": "1142",
        "expectedAreaNames": "朝阳",
        "expectedTime": 1537171954000,
        "startRent": 0,
        "endRent": 6900,
        "cityId": 1,
        "status": 1,
        "createTime": 1537172055088,
        "userId": 556018,
        "outTime": 1537260242830,
        "updateTime": 1538204289356,
        "pictureCount": 0,
        "expectedSubwayStationId": "",
        "expectedSubwayId": "",
        "operateTime": 1539174014501,
        "forMiss": false,
        "user": {
          "id": 556018,
          "nickname": "我们去大草原",
          "nicknameModified": true,
          "avatar": "https://wx.qlogo.cn/mmopen/vi_32/ZLhicyPutHBNRkQIZAUzHEFA2a25hp7la6f2GxVltZSbzc0AzGnO3pWQ0QBibAvLbm4UU3GqLHJC980srYNqAeuA/132",
          "avatarModified": true,
          "gender": 2,
          "genderModified": true,
          "mobileNumber": "17110001016",
          "ageLabel": 1,
          "birthday": "01-01",
          "pushToken": "c2703915d174e1a441fec2d635c615923aac3e4e2f377ff59311ab1fc85896e4",
          "pf": "iOS",
          "career": "经营管理",
          "personalProfile": "我去拯救地球了...",
          "zmScore": 0,
          "zmAuth": false,
          "constellation": "摩羯座",
          "background": "http://test-1251500528.file.myqcloud.com/hzp/img/default_background.jpg",
          "zmAuthPushed": false,
          "infoCompleted": true,
          "flag": false,
          "privacy": 0,
          "forbidden": false,
          "virtual": false,
          "subscribe": false,
          "isForeign": false,
          "isAdministrators": false,
          "administratorStatus": 0,
          "realName": "张振东",
          "certNo": "410782199206254736",
          "isScanCode": false,
          "subscribeFwh": false,
          "invitationCode": "HEZUQU17487F63F2",
          "invited": false,
          "authenticationStatus": 1,
          "migrate": 0,
          "isLogin": true
        },
        "seenCount": "11",
        "redSwitch": true,
        "showOperateTime": ""
      }
    ],
    "banners": [
      {
        "bannerPictureUrl": "http://prod-1251500528.file.myqcloud.com/resource/quzhuanqian.jpg",
        "bannerRedirectUrl": "makeMoney"
      },
      {
        "bannerPictureUrl": "http://prod-1251500528.file.myqcloud.com/resource/scancode.jpg",
        "bannerRedirectUrl": "forwardActivity"
      },
      {
        "bannerPictureUrl": "http://prod-1251500528.file.myqcloud.com/resource/sign-activity.jpg",
        "bannerRedirectUrl": "signActivity"
      },
      {
        "bannerPictureUrl": "http://prod-1251500528.file.myqcloud.com/resource/biyeji-banner.jpg",
        "bannerRedirectUrl": "yajinxian"
      }
    ],
    subheads: [
        "22套精选整租房源",
        "已有29人满意入住",
        "312人已领取"
	]
  }
}
```

