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
    "invited": false
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
			status: 0,
			houseRequestIds ：
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
|goType|String|push类型|是|
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
		avatars: [
			"http://test-1251500528.file.myqcloud.com/hzp/060d1555d20b62bfbd3b73e38670814945"
		]
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

