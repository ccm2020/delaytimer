home assistant 延时开关控制器

用途: 用户通过前端UI 选择要控制的设备和延时时间,组建在倒计时结束后,控制设备的开关


使用说明:

第一步:添加自定义组件 delaytimer

将custom_components目录下的delaytimer目录复制到.homeassistant下的custom_components下

configuration.yaml 中添加如下内容

delaytimer:
  timer1:
    duration: 00:00:00

第二步: 添加delaytimer 的UI

将www目录复制到.homeassistant目录下

登录homeassistant网页管理页面
http://你的IP地址:8123

编辑lovelace,  配置UI->原始编辑器
添加如下内容:

    - type: html
    url: /local/delay-panel.html

views:
- badges: []
cards:
    - entities:
        - light.bedroom_sw
        - switch.wifi_plug
        - switch.route_switch
    name: 延时控制器
    type: 'custom:delay-panel'

说明:entities中添加你要控制的设备entity_id

重启home assistant