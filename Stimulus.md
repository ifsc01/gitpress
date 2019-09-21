---
title: Stimulus 小记
date: 2019-09-21
---

- [Stimulus: A modest JavaScript framework for the HTML you already have.](https://stimulusjs.org/)
- [stimulusjs/stimulus: A modest JavaScript framework for the HTML you already have](https://github.com/stimulusjs/stimulus)
- [Stimulus Handbook: Introduction](https://stimulusjs.org/handbook/introduction)
- [Stimulus Discourse](https://discourse.stimulusjs.org/)

生命周期回调

* initialize dcontroller 初始化是调用一次
* connect 只要 controller `connected` 到DOM
* disconnect controller 和 DOM `disconnected`

Action 标识

data-action `click->hello#greet`

* click 表示事件
* hello 表示controller标识符
* greet 表示要调用的action方法