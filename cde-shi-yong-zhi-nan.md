---
description: 关于CDE使用的小结
---

# CDE 使用指南

## 起步知识

* 布局
* 组件
* 数据源

![](.gitbook/assets/tu-pian.png)

CDE将布局，组件，数据源进行的划分。

布局负责

## 使用布局

## 两个Dashboard传参

获取：

`// 获取查询语句参数  
Utils.getQueryParameter("paramName");  
// 获取path  
Utils.getPathParameter(url);  
// 获取url参数?paramfoo=bar  
Utils.getURLParameters(sURL);`

设置参数：

`dashboard.fireChange("paramName",value);`

## Echarts联动思路

对图形的点击绑定`click`事件，并进行如下操作  
**1**. 传递参数  
ajax异步加载实现，通过CDA文件获取\(参考[CDA Web API](cda-web-api.md)\)  
**2**. 刷新关联图形  
重新渲染Echarts图形，实现刷新功能

### AJAX请求

通过指定CDA文件进行数据获取，构造函数如下：

```javascript
// url:
// /pentaho/plugin/cda/api/doQuery
// ?path=public/testWind/testChartCDE_winds.cda
// &dataAccessId=departmentEmplNum
function readJSONFile(url){
    let jsonData;
    $.ajax({
        type: 'GET',
        url: url,
        async: false,
        dataType: 'json',
        data: null,
        success: function(response){
            jsonData = response;
        }
    });
    return jsonData;
}
```

### 数据格式化

根据不同图形要求，将获取数据进行翻译，变成所需的格式，如下：

```javascript
// 柱形图简单示例
function BarTranslate(data,instance){
    let title = {
        text: 'bar title',
    },
    xAxis = {
        type: 'category',
        axisLabel: {
            interval: 0
        },
        data: data.map(function(item){return item[0]})
    },
    yAxis = {
        type: 'value',
    },
    series = [{
        data: data.map(function(item){return item[2]}),
        type: 'bar'
    }];

    let option = {
        title,
        xAxis,
        yAxis,
        series
    };

    instance.setOption(option);
    window.addEventListener('resize',function(){
        instance.resize();
    });
    return option;
}
```

### 封装初始化Chart

```javascript
/**
* url: CDA数据来源
* id: 挂载htmlObject
* func: Options生成器
*/
function initCharts(url,id,func){
    let resultJSON = readJSONFile(url).resultset;
    const cartContainer = echarts.init(document.getElementById(id));

    func(resultJSON,cartContainer)
}
```

## 导出文件的按钮组件

Standard 》 Export Button Component  
按钮文本：Label  
导出数据源：Component Name指定组件的数据源  
支持导出格式：xls，csv



