---
title: Cocos Creator 插件开发指南
date: 2025-02-10 23:45:36
tags:
---

# Cocos Creator 插件开发指南

## 一、新建插件目录结构

必须包含的基础目录结构：
hello-world
├── main.js # 插件主逻辑文件
└── package.json # 插件配置文件

## 二、插件菜单配置

### package.json 核心配置项说明

| 字段          | 类型   | 说明                                           |
| ------------- | ------ | ---------------------------------------------- |
| `name`        | String | **必填**，全局唯一的插件名称                   |
| `version`     | String | **必填**，遵循 semver 规范的版本号 (例: 0.0.1) |
| `description` | String | _可选_，插件的功能描述                         |
| `author`      | String | _可选_，插件作者信息                           |
| `main`        | String | _可选_，入口文件路径 (例: main.js)             |
| `main-menu`   | Object | _可选_，主菜单配置项                           |

### 配置示例

```json
{
  "name": "hello-world",
  "version": "0.0.1",
  "description": "简单的示例插件",
  "author": "Cocos Creator",
  "main": "main.js",
  "main-menu": {
    "Packages/Hello World": {
      "message": "hello-world:say-hello"
    }
  }
}
```

### 菜单配置详解

```json
"main-menu": {
  "<菜单路径>": {
    "message": "<插件名称>:<自定义消息>"
  }
}

注：当用户点击菜单时，会向插件发送对应的消息，插件需在 main.js 中监听处理这些消息

main.js

'use strict';
module.exports = {
  load () {
    // 当 package 被正确加载的时候执行
  },

  unload () {
    // 当 package 被正确卸载的时候执行
  },

  messages: {
    'say-hello' () {
      Editor.log('Hello World!');
    }
  },
};
```
