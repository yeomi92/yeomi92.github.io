---
layout: post
title:  "mongoose, 스키마"
subtitle: "mongodb"
date:   2019-01-29 -0400
background: '/img/posts/06.jpg'
category: "mongodb"
---

## 1. MongoDB란
> mongoDB는 noSQL(not only SQL) 중 가장 유명합니다.


## 2. Mongoose란
> Mongoose는 mongoDB ODM으로 가장 많이 사용하는 것 중 하나 입니다.


## 3. 스키마 작성
~~~javascript
const mongoose = require('mongoose')
const Schema = mongoose.Schema

const userSchema = new Schema({
    id: String,
    password: String,
    name: String,
    nickname: String,
    email: String,
    create_date: {
        type: Date,
        default: Date.now
    }
})

module.exports = mongoose.model('user', userSchema)
~~~