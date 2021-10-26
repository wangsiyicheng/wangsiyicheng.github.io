---
layout: post
title: node导入excel文件,处理再导出excel文件
date: 2021-10-25
categories: blog
tags: [node,excel]
description: 文章金句。
---

const fs = require('fs')
const xlsx = require('node-xlsx').default
 
// 读取Excel
let exceldata = xlsx.parse(`${__dirname}/11.xlsx`)
let exportData = []
for (let rowId in exceldata[0]['data']) {
    let row = exceldata[0]['data'][rowId]
    exportData.push(row[0])
  }
//处理数据 
let excelData = new Array()
for (var i = 0; i < exportData.length; i++) {
    let arr = new Array()
    arr.push(exportData[i])
    excelData.push(arr)
  }
//导出数据
let buffer = xlsx.build([{name:'sheet1',data:excelData}]);
let path = `${__dirname}/22.xlsx`
fs.writeFile(path, buffer, (err) => {
    err ? console.log(err) : null
})













