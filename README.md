# datepicker_plugin

日期选择器 支持农历公历转换 提供多个自定义接口

### 小程序插件-日期选择器

@(datepicker)[公历农历转换|显示星期|自定义设置]

> 该插件弥补了原生 datepicker 的不足，提供了农历公历的一键转换、星期的显示控制、自定义是否需要农历或者公历，自定义按钮样式等，同时提供了多个处理事件，并返回完整的回调信息可供用户使用。

### 版本介绍

目前最新版本号： **1.0.2**

小程序 appid： **wxbd2294144155ad2c**

---

### 插件使用方式

1.  在知晓程序插件市场中查看 **日期选择器 datepicker**
2.  点击获取插件
3.  获取插件后完成与小程序绑定即可使用

---

### 在小程序中使用插件

> 在**app.json**中添加声明

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

> 在需要引入该插件的页面的**json 配置**中加入

```
{
  "usingComponents": {
    "date-picker": "plugin://datePicker/datePicker"
  }
}
```

> 在需要引入该插件的页面的**wxml**中使用

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

### 属性接口文档

| 属性名           | 类型    | 默认值   | 描述                                     |
| ---------------- | ------- | -------- | ---------------------------------------- |
| date-picker-mode | Boolean | false    | 组件是否显示                             |
| is-solar         | Boolean | true     | 组件是否以公历显示                       |
| show-weekday     | Boolean | true     | 组件是否显示星期几                       |
| picker-position  | String  | 'middle' | 组件显示位置，只能设置为默认值或'bottom' |
| show-lunar-btn   | Boolean | true     | 是否显示农历转换按钮                     |
| select-icon      | String  |          | 选中农历按钮后的 icon 链接               |

### 事件

> 事件绑定和使用方式

**wxml**

```html
<date-picker bind:dateSelectConfirm="confirm" />
```

**js**

```javascript
Page({
  confirm: function(e) {
    // 返回选择日期的详细信息
    console.log(e.detail);
    
  }
});
```

* #### **dateSelectConfirm** -> 日期选择完成事件

> 当组件的 **is-solar** 属性为 **true** 时，返回数据结构如下

   { 
     year: 2018, month: 5, day: 6 
   }  
   **注意**：月份需+1才是真实月份

> 当组件的 **is-solar** 属性为 **false** 时，返回数据结构如下

   { 
     "lYear":2018,"lMonth":4,"lDay":23,"Animal":"狗","IMonthCn":"四月","IDayCn":"廿三","cYear":2018,"cMonth":6,"cDay":6,"gzYear":"戊戌","gzMonth":"戊午","gzDay":"己巳","isToday":true,"isLeap":false,"nWeek":3,"ncWeek":"星期三","isTerm":true,"Term":"芒种","astro":"双子座"
   }

| 属性名   | 类型     | 描述                 |
| -------- | -------- | -------------------- |
| lYear    | Number   | 农历年份             |
| lMonth   | Number   | 农历月份（不需要+1） |
| lDay     | Number   | 农历日期             |
| Animal   | String   | 年份生肖             |
| IMonthCn | String   | 农历月份中文         |
| IDayCn   | String   | 农历日期中文         |
| cYear    | Number   | 公历年份             |
| cMonth   | Number   | 公历月份（不需要+1） |
| cDay     | Number   | 公历日期             |
| gzYear   | String   | 天干地支年份         |
| gzMonth  | String   | 天干地支月份         |
| gzDay    | String   | 天干地支日期         |
| isToday  | Bololean | 是否今天             |
| isLeap   | Bololean | 是否闰年             |
| nWeek    | Number   | 星期几 数字          |
| ncWeek   | String   | 星期几 中文          |
| isTerm   | Boolean  | 是否节气             |
| Term     | String   | 节气                 |
| astro    | String   | 星座                 |

* #### **dateSelectCancel** -> 日期选择取消事件

> 该事件没有实际返回值，只是提供监听取消事件，可以根据需求来灵活设置取消之后页面的状态

* #### **triggerLunar** -> 在日期选择器中切换公/农历事件

> 该事件返回数据结构如下

{ 
  isSolar: false 
}

| 属性名    | 类型     | 描述                 |
| -------- | -------- | -------------------- |
| isSolar  | Boolean  | 是否公历              |
