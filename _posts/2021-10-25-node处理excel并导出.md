<!-- ---
layout: post
title: node导入excel文件,处理再导出excel文件
date: 2021-10-25
categories: blog
tags: [node,excel]
description: 文章金句。
--- -->

const fs = require('fs')
const xlsx = require('node-xlsx').default
<!--   -->
// 读取Excel
<!--  -->
let exceldata = xlsx.parse(`${__dirname}/11.xlsx`)<br/>
let exportData = []<br/>
for (let rowId in exceldata[0]['data']) {<br/>
    &nbsp;&nbsp;&nbsp;let row = exceldata[0]['data'][rowId]<br/>
    &nbsp;&nbsp; exportData.push(row[0])<br/>
  }<br/>
<!--    -->
//处理数据 
<!--  -->
let excelData = new Array()<br/>
for (var i = 0; i < exportData.length; i++) {<br/>
    &nbsp;&nbsp;let arr = new Array()<br/>
    &nbsp;&nbsp;arr.push(exportData[i])<br/>
    &nbsp;&nbsp;excelData.push(arr)<br/>
  }<br/>
<!--    -->
//导出数据
<!--  -->
let buffer = xlsx.build([{name:'sheet1',data:excelData}]);
<br/>
let path = `${__dirname}/22.xlsx`<br/>
fs.writeFile(path, buffer, (err) => {<br/>
    &nbsp;&nbsp;err ? console.log(err) : null<br/>
})













