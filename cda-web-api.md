---
description: 记录如果通过网页api调用cda文件获取数据
---

# CDA Web API

{% api-method method="get" host="$BASE\_URL" path="/pentaho/plugin/cda/api/doQuery?" %}
{% api-method-summary %}
doQuery
{% endapi-method-summary %}

{% api-method-description %}
执行对应CDA文件的SQL语句。  
  
doQuery 建立必要的连接并执行由dataAccessId参数指定的SQL语句。  
  
你需要自己指定SQL语句中不同的parameters的值（否则将使用CDA文件中的默认值），Parameters通过URL变量paramParameter的形式传递，其中Parameter为要传递的参数名。  
 `$BASE_URL/pentaho/plugin/cda/api/doQuery?path=public/plugin-samples/cda/cdafiles/compoundJoin.cda&dataAccessId=2&paramstatus=Shipped`
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="param\[name\]" type="string" required=false %}
传递对应name的参数
{% endapi-method-parameter %}

{% api-method-parameter name="dataAccessId" type="string" required=false %}
执行对应Id的查询语句
{% endapi-method-parameter %}

{% api-method-parameter name="path" type="string" required=true %}
cda文件路径path
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
返回结果为JSON对象
{% endapi-method-response-example-description %}

```javascript
{
    "resultset":[
        ["3","","union"],
        ["2","Sql Query on SampleData","sql"]
    ],
    "metadata":[{
        "colIndex": 0,
        "colType": "String",
        "colName": "id"
    },{
        "colIndex": 1,
        "colType": "String",
        "colName": "name"
    },{
        "colIndex": 2,
        "colType": "String",
        "colName": "type"
    }]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="$BASE\_URL" path="/pentaho/plugin/cda/api/listQueries?" %}
{% api-method-summary %}
listQueries
{% endapi-method-summary %}

{% api-method-description %}
列出指定CDA文件的公共查询语句
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="path" type="string" required=false %}
cda文件的路径path
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
返回JSON格式的指定CDA文件的所有公共查询语句
{% endapi-method-response-example-description %}

```javascript

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="$BASE\_URL" path="/pentaho/plugin/cda/api/getCdaList?" %}
{% api-method-summary %}
getCdaList
{% endapi-method-summary %}

{% api-method-description %}
获取所有CDA文件
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
返回所有CDA文件
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="$BASE\_URL" path="/pentaho/plugin/cda/api/listDataAccessTypes?" %}
{% api-method-summary %}
listDataAccessTypes
{% endapi-method-summary %}

{% api-method-description %}
列出所有支持的data access types和其定义的连接
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
返回JSON格式的所有支持的data access types 和其所定义的连接
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="$BASE\_URL" path="/pentaho/plugin/cda/api/listParameters?" %}
{% api-method-summary %}
listParameters
{% endapi-method-summary %}

{% api-method-description %}
列出该data access使用的所有参数。
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="path" type="string" required=true %}
CDA文件路径
{% endapi-method-parameter %}

{% api-method-parameter name="dataAccessId" type="string" required=true %}
指定的data access id
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Previewer And Editor\(CDA文件的显示与编辑\)

Previewer 提供CDA文件的显示，并提供导出.xls文件，提供对应获取数据URL、还有设置相关缓存策略。

```text
$BASE_URL/pentaho/plugin/cda/api/previewQuery?path=xxx/xxx/xxx.cda
```

Editor提供CDA文件的编辑。

```text
$BASE_URL/pentaho/plugin/cda/api/editFile?path=xxxx/xxx/xxxx.cda
```

