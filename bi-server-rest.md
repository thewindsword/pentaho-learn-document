---
description: pentaho 服务器
---

# BI Server REST

## AJAX 认证

postman: 复制登陆后对应的cookie到postman Cookies中

## 文件浏览

`/repo/files/{pathId}/children?filter=FILES_FOLDERS&showHidden=true`

用于浏览pathId下的所有文件/文件夹，pathId分割为%3A

## 文件下载

```text
/repo/files/{pathId}/download
```

用于下载pathId对应的文件，pathId分割为:

## 文件删除



## 文件上传/新增





{pathId}中/需要转义为%3A

```javascript
// 直接获取对应文件内容
$BASE_URL/pentaho/api/repos/{pathId}/content
// 根据默认打开方式打开对应文件
$BASE_URL/pentaho/api/repos/{pathId}/default

// prpt文件，带设置栏
$BASE_URL/pentaho/api/repos/{pathId}/viewer
// prpt文件，不带设置栏
$BASE_URL/pentaho/api/repos/{pathId}/report
```



