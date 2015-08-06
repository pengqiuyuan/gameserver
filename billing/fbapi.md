# fb项目api

####  1、说明
```
json文件，拖到 http://10.0.29.250/v1/#/ 或者 http://playground.apistudio.io/346bf9ed-3939-4c88-bcfb-a24a7339abb2/#/，如图

```
![image](https://cloud.githubusercontent.com/assets/4953205/9106704/c36596a0-3c54-11e5-8117-a3f3e4d4a3fa.png)

####  1、fb项目gm api

```
swagger: "2.0"
info:
  version: "0.0.1"
  title: Swagger API
host: playground.apistudio.io
basePath: /try/346bf9ed-3939-4c88-bcfb-a24a7339abb2
schemes:
  - http
  - https
consumes:
  - application/json
produces:
  - application/json
paths:
  /fbserver/server/getAllServer:
    get:
      summary: Server Types
      description: |
        获取服务器状态
      parameters:
        - name: serverZoneId
          in: query
          required: false
          type: string
        - name: gameId
          in: query
          required: false
          type: string
        - name: serverId
          in: query
          required: false
          type: string
        - name: pageNumber
          in: query
          required: false
          type: number
        - name: pageSize
          in: query
          required: false
          type: number
      tags:
        - Server
      responses:
        200:
          description: An array of Server
          schema:
            type: array
            items:
              $ref: '#/definitions/Server'
        default:
          description: Unexpected error
          schema:
            $ref: '#/definitions/Error'
  /fbserver/getTotalByServerZoneIdAndGameId:
    get:
      description: |
        total
      parameters:
        - name: serverZoneId
          in: query
          required: false
          type: string
        - name: gameId
          in: query
          required: false
          type: string
        - name: category
          description: 分类（server account placard gag seal ）
          in: query
          required: false
          type: string
      tags:
        - GetTotal
      responses:
        200:
          description: total
          schema:
            $ref: '#/definitions/Totals'
        default:
          description: Unexpected error
          schema:
            $ref: '#/definitions/Error'
  /fbserver/server/getByServerId:
    get:
      summary: Server Types
      description: |
        根据id获取服务器状态
      parameters:
        - name: serverId
          in: query
          required: true
          type: string
      tags:
        - Server
      responses:
        200:
          description: server
          schema:
            $ref: '#/definitions/Server'
        default:
          description: Unexpected error
          schema:
            $ref: '#/definitions/Error'
  /fbserver/server/updateServers:
    post:
      tags:
        - Server
      summary: Server Types
      description: 修改服务器状态
      produces:
        - application/json
        - application/xml
      parameters:
        - in: body
          name: body
          description: server post
          required: true
          schema:
            $ref: "#/definitions/ServerStatusList"
      responses:
        200:
          description: successful operation
          schema:
            $ref: '#/definitions/Success'
  /fbserver/server/getAllGrayAccount:
    get:
      description: |
        查询所有灰度账号
      parameters:
        - name: serverZoneId
          in: query
          required: false
          type: string
        - name: gameId
          in: query
          required: false
          type: string
        - name: pageNumber
          in: query
          required: false
          type: number
        - name: pageSize
          in: query
          required: false
          type: number
      tags:
        - Server
      responses:
        200:
          description: An array of grayaccount
          schema:
            type: array
            items:
              $ref: '#/definitions/GrayAccount'
        default:
          description: Unexpected error
          schema:
            $ref: '#/definitions/Error'
  /fbserver/server/addGrayAccount:
    post:
      tags:
        - Server
      description: 灰度账号添加
      produces:
        - application/json
        - application/xml
      parameters:
        - in: body
          name: body
          description: server post
          required: true
          schema:
            $ref: "#/definitions/GrayAccount"
      responses:
        200:
          description: successful operation
          schema:
            $ref: '#/definitions/Success'
        default:
          description: Unexpected error
          schema:
            $ref: '#/definitions/Error'
  /fbserver/server/getGrayAccountByAccountId:
    get:
      description: |
        根据id查询灰度账号
      parameters:
        - name: id
          in: query
          required: true
          type: string
      tags:
        - Server
      responses:
        200:
          description: grayaccount
          schema:
              $ref: '#/definitions/GrayAccount'
        default:
          description: Unexpected error
          schema:
            $ref: '#/definitions/Error'
  /fbserver/server/updateGrayAccount:
    post:
      tags:
        - Server
      description: 灰度账号修改
      produces:
        - application/json
        - application/xml
      parameters:
        - in: body
          name: body
          description: server post
          required: true
          schema:
            $ref: "#/definitions/GrayAccount"
      responses:
        200:
          description: successful operation
          schema:
            $ref: '#/definitions/Success'
        default:
          description: Unexpected error
          schema:
            $ref: '#/definitions/Error'
  /fbserver/server/delGrayAccountById:
    get:
      tags:
        - Server
      description: 灰度账号删除
      produces:
        - application/json
        - application/xml
      parameters:
        - name: id
          in: query
          required: true
          type: string
      responses:
        200:
          description: success
          schema:
              $ref: '#/definitions/Success'
        default:
          description: Unexpected error
          schema:
            $ref: '#/definitions/Error'
  /fbserver/placard/addPlacards:
    post:
      tags:
        - Placard
      description: 添加公告
      produces:
        - application/json
        - application/xml
      parameters:
        - in: body
          name: body
          description: placard post
          required: true
          schema:
            $ref: "#/definitions/PlacardList"
      responses:
        200:
          description: successful operation
          schema:
            $ref: '#/definitions/ResponseList'
        400:
          description: fail operation
          schema:
            $ref: '#/definitions/Error'
  /fbserver/placard/getAllPlacards:
    get:
      summary: 获取所有公告
      description: |
        placard get
      parameters:
        - name: serverZoneId
          in: query
          required: false
          type: string
        - name: gameId
          in: query
          required: false
          type: string
        - name: serverId
          in: query
          required: false
          type: string
        - name: pageNumber
          in: query
          required: false
          type: number
        - name: pageSize
          in: query
          required: false
          type: number
      tags:
        - Placard
      responses:
        200:
          description: An array of Placard
          schema:
            type: array
            items:
              $ref: '#/definitions/Placard'
        400:
          description: Unexpected error
          schema:
            $ref: '#/definitions/Error'
  /fbserver/placard/updatePlacards:
    post:
      tags:
        - Placard
      description: 修改公告
      produces:
        - application/json
        - application/xml
      parameters:
        - in: body
          name: body
          description: placard post
          required: true
          schema:
            $ref: "#/definitions/PlacardList"
      responses:
        200:
          description: successful operation
          schema:
            $ref: '#/definitions/ResponseList'
        400:
          description: fail operation
          schema:
            $ref: '#/definitions/Error'
  /fbserver/placard/delPlacardById:
    get:
      tags:
        - Placard
      description: 移除公告
      produces:
        - application/json
        - application/xml
      parameters:
        - name: id
          in: query
          required: true
          type: string
      responses:
        200:
          description: success
          schema:
              $ref: '#/definitions/Success'
        400:
          description: fail operation
          schema:
            $ref: '#/definitions/Error'
  /fbserver/seal/getAllSealAccount:
    get:
      summary: seal Types
      description: |
        获取所有被封账号
      parameters:
        - name: serverZoneId
          in: query
          required: false
          type: string
        - name: gameId
          in: query
          required: false
          type: string
        - name: serverId
          in: query
          required: false
          type: string
        - name: pageNumber
          in: query
          required: false
          type: number
        - name: pageSize
          in: query
          required: false
          type: number
      tags:
        - Seal
      responses:
        200:
          description: An array of Seals
          schema:
            type: array
            items:
              $ref: '#/definitions/SealAccount'
        400:
          description: Unexpected error
          schema:
            $ref: '#/definitions/Error'
  /fbserver/seal/updateSealAccount:
    post:
      tags:
        - Seal
      description: 被封账号修改
      produces:
        - application/json
        - application/xml
      parameters:
        - in: body
          name: body
          description: sealaccount update
          required: true
          schema:
            $ref: "#/definitions/SealAccount"
      responses:
        200:
          description: successful operation
          schema:
            $ref: '#/definitions/Success'
        default:
          description: Unexpected error
          schema:
            $ref: '#/definitions/Error'
  /fbserver/seal/delSealAccount:
    delete:
      tags:
        - Seal
      description: 取消（移除）被封账号
      produces:
        - application/json
        - application/xml
      parameters:
        - in: body
          name: body
          description: sealaccount update
          required: true
          schema:
            $ref: "#/definitions/SealAccount"
      responses:
        200:
          description: success
          schema:
              $ref: '#/definitions/Success'
        400:
          description: Unexpected error
          schema:
            $ref: '#/definitions/Error'
  /fbserver/seal/addSealAccount:
    post:
      tags:
        - Seal
      description: 增加被封账号
      produces:
        - application/json
        - application/xml
      parameters:
        - in: body
          name: body
          description: sealaccount add
          required: true
          schema:
            $ref: "#/definitions/SealAccount"
      responses:
        200:
          description: successful operation
          schema:
            $ref: '#/definitions/Success'
        400:
          description: Unexpected error
          schema:
            $ref: '#/definitions/Error'
  /fbserver/gag/getAllGagAccount:
    get:
      summary: gag Types
      description: |
        获取所有禁言账号
      parameters:
        - name: serverZoneId
          in: query
          required: false
          type: string
        - name: gameId
          in: query
          required: false
          type: string
        - name: serverId
          in: query
          required: false
          type: string
        - name: pageNumber
          in: query
          required: false
          type: number
        - name: pageSize
          in: query
          required: false
          type: number
      tags:
        - Gag
      responses:
        200:
          description: An array of gags
          schema:
            type: array
            items:
              $ref: '#/definitions/GagAccount'
        400:
          description: Unexpected error
          schema:
            $ref: '#/definitions/Error'
  /fbserver/gag/updateGagAccount:
    post:
      tags:
        - Gag
      description: 修改禁言账号
      produces:
        - application/json
        - application/xml
      parameters:
        - in: body
          name: body
          description: gagaccount update
          required: true
          schema:
            $ref: "#/definitions/GagAccount"
      responses:
        200:
          description: successful operation
          schema:
            $ref: '#/definitions/Success'
        default:
          description: Unexpected error
          schema:
            $ref: '#/definitions/Error'
  /fbserver/gag/delGagAccountById:
    get:
      tags:
        - Gag
      description: 取消（移除）禁言账号
      produces:
        - application/json
        - application/xml
      parameters:
        - name: id
          in: query
          required: true
          type: string
      responses:
        200:
          description: success
          schema:
              $ref: '#/definitions/Success'
        400:
          description: Unexpected error
          schema:
            $ref: '#/definitions/Error'
  /fbserver/gag/addGagAccount:
    post:
      tags:
        - Gag
      description: 增加禁言账号
      produces:
        - application/json
        - application/xml
      parameters:
        - in: body
          name: body
          description: gagaccount add
          required: true
          schema:
            $ref: "#/definitions/GagAccount"
      responses:
        200:
          description: successful operation
          schema:
            $ref: '#/definitions/Success'
        400:
          description: Unexpected error
          schema:
            $ref: '#/definitions/Error'
  /fbserver/product/getAllProducts:
    get:
      summary: product Types
      description: |
        获取所有商品
      parameters:
        - name: serverZoneId
          in: query
          required: false
          type: string
        - name: gameId
          in: query
          required: false
          type: string
        - name: serverId
          in: query
          required: false
          type: string
        - name: itemId
          in: query
          required: false
          type: string
        - name: pageNumber
          in: query
          required: false
          type: number
        - name: pageSize
          in: query
          required: false
          type: number
      tags:
        - Product
      responses:
        200:
          description: An array of product
          schema:
            type: array
            items:
              $ref: '#/definitions/Product'
        400:
          description: Unexpected error
          schema:
            $ref: '#/definitions/Error'
  /fbserver/product/getProduct:
    get:
      summary: product Types
      description: |
        根据参数查询商品
      parameters:
        - name: serverZoneId
          in: query
          required: false
          type: string
        - name: gameId
          in: query
          required: false
          type: string
        - name: serverId
          in: query
          required: false
          type: string
        - name: itemId
          in: query
          required: false
          type: string
      tags:
        - Product
      responses:
        200:
          description: product get
          schema:
              $ref: '#/definitions/Product'
        400:
          description: Unexpected error
          schema:
            $ref: '#/definitions/Error'
  /fbserver/product/updateProduct:
    post:
      tags:
        - Product
      description: 修改商品
      produces:
        - application/json
        - application/xml
      parameters:
        - in: body
          name: body
          description: product update
          required: true
          schema:
            $ref: "#/definitions/Product"
      responses:
        200:
          description: successful operation
          schema:
            $ref: '#/definitions/Success'
        default:
          description: Unexpected error
          schema:
            $ref: '#/definitions/Error'
  /fbserver/product/addProduct:
    post:
      tags:
        - Product
      description: 增加商品
      produces:
        - application/json
        - application/xml
      parameters:
        - in: body
          name: body
          description: product add
          required: true
          schema:
            $ref: "#/definitions/Product"
      responses:
        200:
          description: successful operation
          schema:
            $ref: '#/definitions/Success'
        default:
          description: Unexpected error
          schema:
            $ref: '#/definitions/Error'
  /fbserver/product/delProductById:
    get:
      tags:
        - Product
      description: 移除商品
      produces:
        - application/json
        - application/xml
      parameters:
        - name: id
          in: query
          required: true
          type: string
      responses:
        200:
          description: success
          schema:
              $ref: '#/definitions/Success'
        400:
          description: fail operation
          schema:
            $ref: '#/definitions/Error'
  /fbserver/email/addEmail:
    post:
      tags:
        - Email
      description: 添加邮件
      produces:
        - application/json
        - application/xml
      parameters:
        - in: body
          name: body
          description: email post
          required: true
          schema:
            $ref: "#/definitions/Email"
      responses:
        200:
          description: successful operation
          schema:
            $ref: '#/definitions/ResponseList'
        400:
          description: fail operation
          schema:
            $ref: '#/definitions/Error'
  /fbserver/email/getAllEmails:
    get:
      summary: 获取所有邮件
      description: |
        email get
      parameters:
        - name: serverZoneId
          in: query
          required: false
          type: string
        - name: gameId
          in: query
          required: false
          type: string
        - name: serverId
          in: query
          required: false
          type: string
        - name: pageNumber
          in: query
          required: false
          type: number
        - name: pageSize
          in: query
          required: false
          type: number
      tags:
        - Email
      responses:
        200:
          description: An array of email
          schema:
            type: array
            items:
              $ref: '#/definitions/Email'
        400:
          description: Unexpected error
          schema:
            $ref: '#/definitions/Error'
  /fbserver/email/updateEmail:
    post:
      tags:
        - Email
      description: 修改邮件
      produces:
        - application/json
        - application/xml
      parameters:
        - in: body
          name: body
          description: email post
          required: true
          schema:
            $ref: "#/definitions/Email"
      responses:
        200:
          description: successful operation
          schema:
            $ref: '#/definitions/ResponseList'
        400:
          description: fail operation
          schema:
            $ref: '#/definitions/Error'
  /fbserver/email/delEmailById:
    get:
      tags:
        - Email
      description: 移除邮件
      produces:
        - application/json
        - application/xml
      parameters:
        - name: id
          in: query
          required: true
          type: string
      responses:
        200:
          description: success
          schema:
              $ref: '#/definitions/Success'
        400:
          description: fail operation
          schema:
            $ref: '#/definitions/Error'
  /fbserver/email/getEmailById:
    get:
      tags:
        - Email
      description: 获取邮件
      produces:
        - application/json
        - application/xml
      parameters:
        - name: id
          in: query
          required: true
          type: string
      responses:
        200:
          description: success
          schema:
              $ref: '#/definitions/Email'
        400:
          description: fail operation
          schema:
            $ref: '#/definitions/Error'
definitions:
  Success:
    properties:
      message:
        type: string
  Error:
    properties:
      message:
        type: string
  Server:
    properties:
      id:
        type: number
      serverZoneId:
        type: string
      gameId:
        type: string
      serverId:
        type: string
      serverName:
        type: string
      status:
        type: string
  ServerList:
    properties:
      serverZoneId:
        type: string
      gameId:
        type: string
      serverId:
        type: array
        items:
          type: string
      serverName:
        type: string
      status:
        type: string
  ResponseList:
    properties:
      choose:
        type: number
      success:
        type: number
      objFail:
        type: array
        items:
          type: string
      fail:
        type: number
  GrayAccount:
    properties:
      id:
        type: number
      serverZoneId:
        type: string
      gameId:
        type: string
      serverId:
        type: string
      platFormId:
        type: string
      account:
        type: string
  PlacardList:
    properties:
      serverZoneId:
        type: string
      gameId:
        type: string
      serverIds:
        type: array
        items:
          type: string
      version:
        type: string
      content:
        type: string
  Placard:
    properties:
      id:
        type: number
      serverZoneId:
        type: string
      gameId:
        type: string
      serverId:
        type: string
      version:
        type: string
      contents:
        type: string
  SealAccount:
    properties:
      id:
        type: number
      serverZoneId:
        type: string
      gameId:
        type: string
      serverId:
        type: string
      guid:
        type: string
      name:
        type: string
      account:
        type: string
      platForm:
        type: string
      sealTime:
        type: string
      sealStart:
        type: string
      sealEnd:
        type: string
  GagAccount:
    properties:
      id:
        type: number
      serverZoneId:
        type: string
      gameId:
        type: string
      serverId:
        type: string
      guid:
        type: string
      name:
        type: string
      account:
        type: string
      platForm:
        type: string
      gagTime:
        description: 禁言时间（单位为秒，永久禁言为-1）,如（禁言半小时，gagTime为1800）
        type: string
      gagStart:
        type: string
      gagEnd:
        type: string
  Product:
    properties:
      id:
        type: number
      serverZoneId:
        type: string
      gameId:
        type: string
      serverId:
        type: string
      itemId:
        type: string
        description: 道具ID
      num:
        type: string
        description: 个数
      prodcutStoreId:
        type: string
        description: 商店ID
      storeLocation:
        type: string
        description: 商品出现位置
      isRandom:
        type: string
        description: 出现是否随机
      randomProbability:
        type: string
        description: 随机概率
      comsumeType:
        type: string
        description: 消费类型
      comsumeNum:
        type: string
        description: 消费数量
      discount:
        type: string
        description: 折扣率
      levelLimit:
        type: string
        description: 玩家获取该商品的等级下限
      levelCap:
        type: string
        description: 玩家获取该商品的等级上限
      discountStartDate:
        type: string
        description: 折扣生效时间
      discountContinueDate:
        type: string
        description: 折扣持续时间
      discountCycleDate:
        type: string
        description: 折扣循环时间
      productPostDate:
        type: string
        description: 商品上架时间
      productDownDate:
        type: string
        description: 商品下架时间
      showLevel:
        type: string
        description: 显示优先级
  Item:
    type: object
    properties:
      itemId:
        type: string
      itemNum:
        type: number
  Totals:
    properties:
      num:
        type: number
  Email:
    properties:
      id:
        type: number
      serverZoneId:
        type: string
      gameId:
        type: string
      serverId:
        type: string
      sender:
        type: string
        description: 发送人
      title:
        type: string
        description: 标题
      contents:
        type: string
        description: 内容，3000字以内
      annex:
        type: array
        items:
          $ref: '#/definitions/Item'
        description: 附件（道具）
  ServerStatusList:
    properties:
      status:
        type: string
      id:
        type: array
        items:
          type: string

```
