# datepicker_plugin
日期选择器 支持农历公历转换 提供多个自定义接口

### 小程序插件-日期选择器
@(datepicker)[公历农历转换|显示星期|自定义设置]

> 该插件弥补了原生datepicker的不足，提供了农历公历的一键转换、星期的显示控制、自定义是否需要农历或者公历，自定义按钮样式等，同时提供了多个处理事件，并返回完整的回调信息可供用户使用。


### 版本介绍
目前最新版本号： **1.0.2** 

小程序appid：  **wxbd2294144155ad2c**

----------

### 插件使用方式
1. 在知晓程序插件市场中查看 **日期选择器datepicker**
2. 点击获取插件
3. 获取插件后完成与小程序绑定即可使用

----------

### 在小程序中使用插件
>在**app.json**中添加声明
```
{
  "plugins": {
    "datePicker": {
      "version": "1.0.2",
      "provider": "wxbd2294144155ad2c"
    }
  }
}
```
>在需要引入该插件的页面的**json配置**中加入
```
{
  "usingComponents": {
    "date-picker": "plugin://datePicker/datePicker"
  }
}
```
>在需要引入该插件的页面的**wxml**中使用
```
<date-picker
      date-picker-mode="{{ datePickerMode }}"
      is-solar="{{ isSolar }}"
      show-weekday="{{ showWeekday }}"
      picker-position="{{ pickerPosition }}"
      show-lunar-btn="{{ showLunarBtn }}"
      select-icon="https://www.51wnl.com/wxapp_resource/wnl/pop-radio-ok-icon.png"
      
      bind:dateSelectConfirm="confirm"
      bind:dateSelectCancel="cancel"
      bind:triggerLunar="changeSolar"
      
      confirm_btn='confirm_style'
      cancel_btn='cancel_style'   />
 
```

###属性接口文档
属性名                   | 类型         |  默认值     |  描述                                  
 ---------------------  | ------------ | ---------- | ------------------- 
date-picker-mode        | Boolean      |   false    |  组件是否显示 
is-solar        		    | Boolean      |   true     |  组件是否以公历显示  
show-weekday        	  | Boolean      |   true     |  组件是否显示星期几  
picker-position         | String       |  'middle'  |  组件显示位置，只能设置为默认值或'bottom' 
show-lunar-btn          | Boolean      |   false    |  是否显示农历转换按钮
select-icon             | String       |            |  选中农历按钮后的icon链接

第一表头 | 第二表头
------------ | -------------
第一单元格内容 | 第二单元格内容
第一列内容 | 第二列内容
