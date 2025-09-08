<style scoped>
/*********************** 主应用样式 start ***********************/
/* canvas 图层样式 */
#container {
    position: relative;
    height: 100vh;
}

canvas {
    position: absolute;
    left: 0;
    top: 0;
    display: none;
}

#game-scene-graph {
    z-index: -1;
}

#game-scene-emoji {
    z-index: -1;
}

#game-scene-lines-bg {
    z-index: -1;
}

#game-scene {
    background: rgba(255, 255, 255, 0);
    /*图层透明，给画的图形填充颜色*/
    z-index: -1;
}

#game-scene-lines {
    z-index: 0;
}

#game-scene-coordinate {
    z-index: 0;
}

#game-main {
    z-index: 1;
}

#game-main-ball {
    z-index: 2;
    pointer-events: none;
    /* 可以点击穿透 */
}

#game-path {
    z-index: 1;
    pointer-events: none;
    /* 可以点击穿透 */
}

#game-path-ball {
    z-index: 1;
    pointer-events: none;
    /* 可以点击穿透 */
}

#game-click-play {
    z-index: 10;
    /* 在角色和运动层之上 */
}

#game-mask {
    z-index: -2;
}

/* 遮罩图层样式 */
#dialog-mask {
    position: absolute;
    left: 0;
    top: 0;
    z-index: 1000;
    background-color: rgba(0, 0, 0, 0.5);
    width: 100vw;
    height: 100vh;
    display: none;
}

/* 应用全局公用样式 */
.collide-try-btn {
    width: 40px;
    text-align: center;
    vertical-align: middle;
    line-height: 1;
    border-radius: 3px;
    cursor: pointer;
}

.collide-try-in-one-line {
    display: flex;
    flex-wrap: nowrap;
    flex-direction: row;
    align-content: center;
    justify-content: center;
    align-items: stretch;
}

.collide-try-each-item-border-bottom {
    width: 100%;
    display: inline-block;
    border-bottom: 1px solid #ddd;
    text-align: left;
}

.collide-try-each-item-margin {
    display: inline-block;
    margin: 3px 0 3px 0;
}

/* 带一个关闭按钮的居中偏上弹窗 */
.collide-try-close-btn-dialog {
    position: absolute;
    left: 0;
    top: -20vh;
    right: 0;
    bottom: 0;
    margin: auto;
    z-index: 10010;
    width: 80%;
    height: max-content;
    border-radius: 10px;
    text-align: center;
    display: none;
}

.collide-try-close-btn-dialog-title {
    border-radius: 10px 10px 0 0;
    background: #edeff6;
    display: flex;
    flex-direction: row;
    align-items: baseline;
    flex-wrap: nowrap;
    justify-content: flex-start;
}

.collide-try-close-btn-dialog-title-close {
    position: absolute;
    width: 100%;
    font-size: 18px;
    top: 6px;
    left: -6px;
    text-align: right;
}

.collide-try-close-btn-dialog-title-close span {
    font-size: 16px;
    cursor: pointer;
}

.collide-try-close-btn-dialog-title b {
    font-size: 18px;
    text-align: left;
    line-height: 2.4;
    padding-left: 10px;
    vertical-align: middle;
}

.collide-try-close-btn-dialog-content {
    background-color: #f7f7fc;
    max-height: 40.0vh;
    /* 内容超出区域，需要设置高度，才能滚动 */
    /* 隐藏 IE、Edge 和 Firefox 的滚动条 */
    -ms-overflow-style: none;
    /* IE and Edge */
    scrollbar-width: none;
    /* Firefox */
    overflow-x: hidden;
    overflow-y: scroll;
    font-size: 14px;
    margin-top: -2px;
    /* 解决标题边框透明问题 */
    padding: 10px 10px 25px 10px;
    border-radius: 0 0 10px 10px;
}

.collide-try-close-btn-dialog-content pre {
    width: 100%;
    text-align: left;
    font-size: 14px;
    line-height: 1.6;
    white-space: pre-line;
}

.collide-try-close-btn-dialog-content pre a {
    font-size: 10px;
}

.collide-try-close-btn-dialog-ok {
    text-align: right;
    margin-top: -11px;
    margin-right: 20px;
}

.collide-try-close-btn-dialog-ok span {
    text-align: center;
    vertical-align: middle;
    width: max-content;
    padding: 6px;
    font-size: 14px;
    background: chartreuse;
    border-radius: 5px;
    border: 1px black;
    box-shadow: rgba(0, 0, 0, 0.16) 0px 10px 36px 0px, rgba(0, 0, 0, 0.06) 0px 0px 0px 1px;
    cursor: pointer;
}

/* 小提示弹窗样式，重写样式需要放在这个样式后面 */
.collide-try-tiny-dialog {
    position: absolute;
    top: 5px;
    right: 40px;
    margin: auto;
    z-index: 0;
    text-align: center;
    font-size: 16px;
    display: none;
}

.collide-try-left-tiny-dialog {
    left: 40px;
    right: unset;
}

.collide-try-tiny-dialog-msg {
    text-align: right;
    vertical-align: middle;
    padding: 0 5px 5px 5px;
    font-size: 16px;
    background: #fff;
    border-radius: 5px;
    border: 1px dashed black;
    box-shadow: rgba(0, 0, 0, 0.16) 0px 10px 36px 0px, rgba(0, 0, 0, 0.06) 0px 0px 0px 1px;
}

.collide-try-tiny-dialog-msg span {
    font-size: 20px;
}

.collide-try-tiny-dialog-ok {
    text-align: right;
    vertical-align: middle;
    width: 100%;
    margin: 5px 0;
    font-size: 14px;
}

.collide-try-left-tiny-dialog-ok {
    text-align: left;
}

.collide-try-tiny-dialog-ok span {
    text-align: center;
    vertical-align: middle;
    width: max-content;
    margin-top: 5px;
    padding: 5px;
    font-size: 14px;
    background: chartreuse;
    border-radius: 5px;
    border: 1px black;
    box-shadow: rgba(0, 0, 0, 0.16) 0px 10px 36px 0px, rgba(0, 0, 0, 0.06) 0px 0px 0px 1px;
    cursor: pointer;
}


/* 左上角重选角色提示弹窗样式 */
#re-choose-role-icon {
    position: absolute;
    left: 10px;
    top: 10px;
    z-index: 0;
}

#re-choose-role-icon>span {
    padding: 2px;
    font-size: 16px;
    text-align: center;
    vertical-align: middle;
    cursor: pointer;
}

/* 右上角设置提示弹窗样式 */
#game-setting-icon {
    position: absolute;
    right: 10px;
    top: 10px;
    z-index: 0;
}

#game-setting-icon>span {
    padding: 2px;
    font-size: 16px;
    text-align: center;
    vertical-align: middle;
    cursor: pointer;
}

/* 设置主角时提示弹窗样式 */
/* 父元素设置 position 为 relative，自身设置为 absolute，即可跟随定位 */
.user-setting-item-input-area {
    position: relative;
}

#game-setting-main-role-dialog {
    top: 25px;
    bottom: 0;
    left: 0;
    right: 0;
    z-index: 1003;
}

#game-setting-main-role-dialog-msg {
    text-align: left;
    padding: 5px;
    font-size: 14px;
}

#game-setting-main-role-dialog-msg span {
    font-size: 16px;
}

#game-setting-main-role-dialog-ok {}

#game-setting-main-role-dialog-ok span {}

/* TODO 后续再封装一个全局弹窗，多处调用同一个，减少重复代码 */
/* 选择角色弹窗样式 */
#choose-role-dialog {
    position: absolute;
    left: 0;
    top: 0;
    right: 0;
    bottom: 0;
    margin: auto;
    z-index: 1001;
    width: 80%;
    height: max-content;
    border-radius: 10px;
    background-color: #f7f7fc;
    text-align: center;
    display: none;
    overflow: hidden;
}

#role-list-area {
    max-height: 80.0vh;
    -ms-overflow-style: none;
    scrollbar-width: none;
    overflow-x: hidden;
    overflow-y: scroll;
}

#role-list-head {
    border-radius: 10px 10px 0 0;
    background: #edeff6;
    text-align: center;
    vertical-align: middle;
}

#role-list-head-msg {
    padding: 12px 0;
    font-size: 24px;
    line-height: 24px;
}

#role-list-head-desc {
    padding: 0 0 5px 0;
    font-size: 10px;
}

#role-list-head-setting-icon {
    position: absolute;
    width: 100%;
    font-size: 24px;
    line-height: 24px;
    top: 7px;
    right: 7px;
    text-align: right;
    display: inline-flex;
    flex-direction: row;
    align-content: center;
    justify-content: flex-end;
    align-items: center;
}

#role-list-head-setting-icon span {
    font-size: 18px;
    cursor: pointer;
}

.role-list {
    padding: 10px 0 10px 0;
    font-size: 20px;
    cursor: pointer;
}

.role-list:not(:last-child) {
    border-bottom: 1px solid #ddd;
}

.role-list:last-child {
    border-radius: 0 0 10px 10px;
}

.role-list:hover {
    background-color: #FAFAFA;
}

/* 选择角色列表icon、name表格样式 */
.role-list-icon-name {
    display: inline-grid;
    grid-template-columns: 50px 180px;
    grid-template-rows: 100%;
    align-content: center;
    justify-content: center;
    align-items: baseline;
    justify-items: stretch;
    /*padding-left: 10px;*/
}

.role-list-icon-name span {
    font-size: 20px;
}

.role-list-icon {
    text-align: right;
    vertical-align: middle;
}

.role-list-name {
    text-align: left;
    margin-left: 10px;
}

/* 选择角色双子图标重画 */
#role-shuangzi span {
    font-size: 20px;
}

#role-shuangzi-new-draw {
    display: inline-grid;
}

.role-shuangzi-single {
    grid-area: 1 / 2;
}

#role-shuangzi-1 {
    margin-right: 4px;
    z-index: 1002;
}

#role-shuangzi-2 {
    margin-right: -4px;
    margin-top: -2px;
    z-index: 1001;
}

/* 用户设置弹窗样式 */
#user-setting-dialog {
    overflow: hidden;
    position: absolute;
    left: 0;
    top: 0;
    right: 0;
    bottom: 0;
    margin: auto;
    z-index: 1002;
    width: 80%;
    height: max-content;
    border-radius: 10px;
    background-color: #f7f7fc;
    text-align: center;
    display: none;
}

#user-setting-area {
    max-height: 80.0vh;
    /* 内容超出区域，需要设置高度，才能滚动 */
    /* 隐藏 IE、Edge 和 Firefox 的滚动条 */
    -ms-overflow-style: none;
    /* IE and Edge */
    scrollbar-width: none;
    /* Firefox */
    overflow-x: hidden;
    overflow-y: scroll;
}

/* 隐藏 Chrome、Safari 和 Opera 的滚动条 */
#user-setting-area::-webkit-scrollbar {
    display: none;
}

#user-setting-head {
    border-radius: 10px 10px 0 0;
    background: #edeff6;
    text-align: center;
    vertical-align: middle;
}

#user-setting-head-msg {
    padding: 12px 0;
    font-size: 24px;
    line-height: 24px;
}

#user-setting-head-desc {
    padding: 0 0 5px 0;
    font-size: 10px;
}

#user-setting-close-icon {
    position: absolute;
    width: 100%;
    font-size: 24px;
    line-height: 24px;
    top: 7px;
    right: 7px;
    text-align: right;
    display: inline-flex;
    flex-direction: row;
    align-content: center;
    justify-content: flex-end;
    align-items: center;
}

#user-setting-close-icon span {
    font-size: 18px;
    cursor: pointer;
}

.user-setting-item {
    padding: 9px 10px;
    font-size: 18px;
    line-height: 18px;
    text-align: left;
}

.li-space-between-center {
    display: flex;
    flex-direction: row;
    align-content: center;
    justify-content: space-between;
    align-items: center;
}

#page-color-image {
    padding: 8.2px 10px;
}

.user-setting-item-msg-left {
    font-size: 16px;
}

.user-setting-item-switch-right button {
    font-size: 12px;
}

.custom-theme-conf-inout {
    line-height: 18px;
    width: 30px;
    margin-left: 7px;
}

.user-setting-item:not(:last-child) {
    border-bottom: 1px solid #ddd;
}

.user-setting-item:last-child {
    border-radius: 0 0 10px 10px;
}

.user-setting-item:hover {
    background-color: #FAFAFA;
}

.user-setting-item-msg-left {
    position: relative;
    text-align: left;
}

.user-setting-item-switch-right {
    position: relative;
    float: right;
    /*top: 4px;*/
    vertical-align: middle;
    display: flex;
}

.user-setting-item-input-area {
    margin: 4px 0px;
}

.user-setting-item-input-area input {
    width: 100%;
    vertical-align: middle;
    border: none;
    padding: 2px 2px;
    font-size: 12px;
    color: #2196F3;
    background-color: transparent;
    outline: none;
    -webkit-appearance: none;
}

.user-setting-item-right-input-area {
    margin: 0;
}

.user-setting-item-right-input-area input {
    width: 100px;
    text-align: right;
    padding: 0;
}

.user-setting-item-right-input-area label {
    font-size: 16px;
    margin-left: 2px;
    cursor: pointer;
}

.user-setting-item-right-input-area svg {
    width: 18px;
    height: 18px;
    vertical-align: sub;
    transform: rotate(90deg);
    fill: #2196F3;
}

.user-setting-item-right-input-color-code {
    width: 80px !important;
}

.user-setting-item-right-input-number-m {
    width: 50px !important;
}

.div-input-game-roles {
    display: inline-block;
    min-width: 25px;
    max-width: 100px;
    vertical-align: middle;
    border: 1px solid transparent;
    border-color: #2196F3;
    border-radius: 4px;
    padding: 2px 4px;
    margin-right: 3px;
    font-size: 12px;
    color: #2196F3;
    background-color: transparent;
    outline: none;
    -webkit-appearance: none;
}

.div-input-game-roles.red {
    color: red;
    border-color: red;
}

.div-input-game-roles.default {}

.reset-btn {
    /*
        vertical-align: middle;
        margin-left: 4px;
        */
    font-size: 15px;
    cursor: pointer;
}

/* 导入/导出角色和坐标 */
#shareRoleAndPos {}

.bg-lv1 {
    background-color: #16C60C;
    color: #fff;
}

.bg-lv2 {
    background-color: #2196F3;
    color: #fff;
}

/* 用户设置-二级列表 */
.user-setting-item-expand {
    background-color: #EDF2FA;
    display: none;
}

.user-setting-item-expand .user-setting-item-msg-left {
    font-size: 14px;
}

.user-setting-item-disabled {
    color: #999 !important;
}


/* 关于应用弹窗样式 */
#user-setting-about-app-dialog {
    position: absolute;
    left: 0;
    top: 0;
    right: 0;
    bottom: 0;
    margin: auto;
    z-index: 1003;
    width: 80%;
    height: max-content;
    border-radius: 10px;
    background-color: #f7f7fc;
    text-align: center;
    display: none;
}

#user-setting-about-app-close-icon {
    position: absolute;
    width: 100%;
    border-radius: 10px 10px 0 0;
    font-size: 18px;
    top: 6px;
    left: -6px;
    text-align: right;
}

#user-setting-about-app-close-icon span {
    font-size: 18px;
    cursor: pointer;
}

#user-setting-about-app-content {
    max-height: 80.0vh;
    /* 内容超出区域，需要设置高度，才能滚动 */
    /* 隐藏 IE、Edge 和 Firefox 的滚动条 */
    -ms-overflow-style: none;
    /* IE and Edge */
    scrollbar-width: none;
    /* Firefox */
    overflow-x: hidden;
    overflow-y: scroll;
    font-size: 14px;
    padding: 10px;
}

#user-setting-about-app-content pre {
    width: 100%;
    text-align: left;
    font-size: 12px;
    line-height: 1.5;
    white-space: pre-line;
}

#user-setting-about-app-content pre b {
    /*line-height: 2;*/
}

#user-setting-about-app-content pre a {
    font-size: 10px;
}

#user-setting-about-app-title {}

#about-app-title {
    font-size: 18px;
    text-align: left;
    line-height: 2.4;
    padding-left: 10px;
    vertical-align: middle;
}

#about-app-title svg {
    width: 25px;
    height: 20px;
    vertical-align: sub;
    padding-right: 5px;
}

.collide-try-goodbye {
    display: none;
}

#collide-try-bye {
    margin-top: 886px;
}

#collide-try-bye span {
    line-height: 1.5;
}

#see-you-next-time {
    font-size: 16px;
    font-weight: bold;
    /*color: mediumblue;*/
}

.collide-try-update-title {
    display: inline-block;
    vertical-align: bottom;
    width: 100%;
    margin-bottom: 2px;
}

.collide-try-update-title b {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    align-content: flex-end;
    justify-content: space-between;
    align-items: flex-end;
}

.collide-try-update-date {
    font-weight: normal;
    font-size: 9px;
    color: #999;
}

.collide-try-author-declare {}

.collide-try-author-declare-title {
    font-size: 14px;
}

.collide-try-author-declare-content {
    display: grid;
    background: #edeff6;
    border: 1px solid black;
    margin-top: 6px;
    padding-bottom: 6px;
}

.collide-try-author-declare-content li {
    display: inline-block;
    margin: 6px 0 0 0;
    padding: 0 5px 0 5px;
}

/* 角色坐标悬浮条样式 */
#collide-try-role-pos-line {
    position: absolute;
    left: 0;
    top: 0;
    margin: auto;
    z-index: 1;
    background-color: #fff;
    border-radius: 5px;
    width: max-content;
    height: max-content;
    text-align: center;
    vertical-align: middle;
    padding: 2px 0px 2px 4px;
    box-shadow: rgba(0, 0, 0, 0.16) 0px 10px 36px 0px, rgba(0, 0, 0, 0.06) 0px 0px 0px 1px;
    display: none;
}

.div-input-role-pos {
    display: inline-block;
    text-align: left;
    line-height: 1;
    padding: 2px 4px;
    background-color: transparent;
    outline: none;
    -webkit-appearance: none;
}

/* 颜色样式 */
.red {
    color: red !important;
}

/* SVG 图形区域 */
.svg-image-area .bi {
    display: none;
}

/************************ 主应用样式 end ************************/


/********************** 第三方组件样式 start *********************/
/* CSS 开关样式 */
/* https://c.runoob.com/codedemo/3146/ */
.switch {
    position: relative;
    display: inline-block;
    width: 40px;
    height: 18px;
}

.switch input {
    display: none;
}

.slider {
    position: absolute;
    cursor: pointer;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: #ccc;
    -webkit-transition: .1s;
    transition: .1s;
}

.slider:before {
    position: absolute;
    content: "";
    height: 14px;
    width: 14px;
    left: 3px;
    bottom: 2px;
    background-color: white;
    -webkit-transition: .1s;
    transition: .1s;
}

input:checked+.slider {
    background-color: #2196F3;
}

input:focus+.slider {
    box-shadow: 0 0 1px #2196F3;
}

input:checked+.slider:before {
    -webkit-transform: translateX(20px);
    -ms-transform: translateX(20px);
    transform: translateX(20px);
}

/* Rounded sliders */
.slider.round {
    border-radius: 34px;
}

.slider.round:before {
    border-radius: 50%;
}


/* CSS 下拉菜单 */
/* https://c.runoob.com/codedemo/161/ */
.dropbtn {
    color: #2196F3;
    border: none;
    cursor: pointer;
    background: unset;
}

.dropdown {
    position: relative;
    display: inline-block;
}

.dropdown-content {
    display: none;
    position: absolute;
    background-color: #f9f9f9;
    width: max-content;
    box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
    z-index: 2;
}

.dropdown-content a {
    color: black;
    padding: 5px 5px 5px 5px;
    text-decoration: none;
    display: block;
}

.dropdown-content a:hover {
    background-color: #f1f1f1
}

.dropdown:hover .dropdown-content {
    display: block;
}

.dropdown:hover .dropbtn {
    background-color: #3e8e41;
}

.show {
    display: block;
}


/* console.log 日志区域 */
/* https://blog.csdn.net/ChenX_Web/article/details/99721636 */
#info {
    position: fixed;
    left: 0;
    top: 0;
    width: 100vw;
    height: 60vh;
    background: #fff;
    overflow: scroll;
    font-size: 10px;
    z-index: 999999999;
    -webkit-tap-highlight-color: transparent;
    /* 隐藏 IE、Edge 和 Firefox 的滚动条 */
    -ms-overflow-style: none;
    /* IE and Edge */
    scrollbar-width: none;
    /* Firefox */
}

#info h1 {
    color: #000;
    word-wrap: break-word;
    word-break: normal;
    border-bottom: 1px solid #D3E3FD;
    padding: 2px;
    font-size: 8px;
}

#info h1:nth-child(odd) {
    background-color: #fff;
}

/********************** 第三方组件样式 end ***********************/
</style>

<template>
    <main id="app-main">
        <!-- canvas 图层容器 -->
        <div id="container" ref="container">
            <!--
    多图层未指定 z-index，后定义的图层会覆盖前面定义的
    图层顺序，会在游戏过程调整
    -->
            <!-- scene-graph 场景图形层 -->
            <canvas id="game-scene-graph" ref="gameSceneGraph" width="420" height="660"
                style="width: 420px; height: 660px; display: unset;"><!-- 静态场景曲线图形层，全屏画布，只渲染一次 -->
                如果看到这个提示，说明你的浏览器不支持Canvas，请升级浏览器版本，或者更换其他浏览器
            </canvas>
            <!-- scene-emoji 场景emoji图标层 -->
            <canvas id="game-scene-emoji" ref="gameSceneEmoji" width="420" height="660"
                style="width: 420px; height: 660px; display: unset;"><!-- 静态场景景物图形层，全屏画布，只渲染一次 -->
                Canvas not supported
            </canvas>
            <!-- scene-lines 场景边框背景层，把游戏场景层夹在中间 -->
            <canvas id="game-scene-lines-bg" width="420" height="660"
                style="width: 420px; height: 660px; display: unset;"><!-- 静态场景边框背景层，全屏画布，只渲染一次 -->
                Canvas not supported
            </canvas>
            <!-- scene 游戏场景层 -->
            <canvas id="game-scene" ref="gameScene" width="420" height="660"
                style="width: 420px; height: 660px;"><!-- 静态场景背景层，只渲染一次，优化CPU性能 -->
                Canvas not supported
            </canvas>
            <!-- scene-lines 场景边框层 -->
            <canvas id="game-scene-lines" ref="gameSceneLines" width="420" height="660"
                style="width: 420px; height: 660px; display: unset;"><!-- 静态场景场地边框层，全屏画布，只渲染一次 -->
                Canvas not supported
            </canvas>
            <!-- scene-coordinate 场景坐标层 -->
            <canvas id="game-scene-coordinate" ref="gameSceneCoordinate" width="420" height="660"
                style="width: 420px; height: 660px; display: unset;"><!-- 静态场景砖格坐标层，全屏画布，只渲染一次 -->
                Canvas not supported
            </canvas>
            <!-- main 角色运动层 -->
            <canvas id="game-main" ref="gameMain" width="420" height="660"
                style="width: 420px; height: 660px;"><!-- 主运动层，每次渲染会清空画布 -->
                Canvas not supported
            </canvas>
            <!-- main-ball 主角运动层 -->
            <canvas id="game-main-ball" ref="gameMainBall" width="420" height="660"
                style="width: 420px; height: 660px;"><!-- 主球（主角）运动层，每次渲染会清空画布 -->
                Canvas not supported
            </canvas>
            <!-- path 角色路径层 -->
            <canvas id="game-path" ref="gamePath" width="420" height="660"
                style="width: 420px; height: 660px;"><!-- 角色中线路径层，手动清空画布 -->
                Canvas not supported
            </canvas>
            <!-- path-ball 主角全路径层 -->
            <canvas id="game-path-ball" ref="gamePathBall" width="420" height="660"
                style="width: 420px; height: 660px;"><!-- 角色全路径层，手动清空画布 -->
                Canvas not supported
            </canvas>
            <!-- click-play 点按发射按钮层 -->
            <canvas id="game-click-play" width="600" height="600"
                style="width: 600px; height: 600px;"><!-- 点按发射按钮层，只画一次 -->
                Canvas not supported
            </canvas>
            <!-- mask 运动遮罩层 -->
            <canvas id="game-mask" ref="gameMask" width="420" height="660"
                style="width: 420px; height: 660px;"><!-- 遮罩层，避免运动时操作小球，手动调整图层顺序 -->
                Canvas not supported
            </canvas>
        </div>
        <!-- 弹窗遮罩 -->
        <div id="dialog-mask" ref="dialogMask" class="collide-try-dialog"></div>
        <!-- 左上角选择角色提示 -->
        <div id="re-choose-role-icon"><span @click="switchChooseRoleDialog(true);">&nbsp;&nbsp;&nbsp;&nbsp;</span>
        </div>
        <div id="re-choose-role-entry-dialog"
            class="collide-try-dialog collide-try-tiny-dialog collide-try-left-tiny-dialog" style="display: none;">
            <div id="re-choose-role-entry-dialog-msg" class="collide-try-tiny-dialog-msg"><span>👈</span>点击左上角可以重新选择角色哦~
            </div>
            <div id="re-choose-role-entry-dialog-ok" class="collide-try-tiny-dialog-ok collide-try-left-tiny-dialog-ok"
                @click="closeReChooseRoleEntryDialog();"><span class="collide-try-dialog-ok">可以的</span></div>
        </div>
        <!-- 右上角设置提示 -->
        <div id="game-setting-icon"><span @click="switchUserSettingDialog(true);">&nbsp;&nbsp;&nbsp;&nbsp;</span></div>
        <div id="game-setting-entry-dialog" ref="gameSettingEntryDialog"
            class="collide-try-dialog collide-try-tiny-dialog" style="display: none;">
            <div id="game-setting-entry-dialog-msg" class="collide-try-tiny-dialog-msg">
                右上角有一个隐藏的设置<span>⚙</span>入口哦~<span>👉</span></div>
            <div id="game-setting-entry-dialog-ok" class="collide-try-tiny-dialog-ok"
                @click="closeGameSettingEntryDialog();"><span class="collide-try-dialog-ok">知道啦</span></div>
        </div>
        <!-- 选择角色弹窗 -->
        <div id="choose-role-dialog" ref="chooseRoleDialog" class="collide-try-dialog">
            <div id="role-list-head">
                <div id="role-list-head-msg">👇请选择角色</div>
                <div id="role-list-head-setting-icon"><span id="choose-role-to-setting-entry"
                        @click="switchUserSettingDialog(true);" style="display: none;">⚙️</span><span
                        id="choose-role-close-btn" @click="switchChooseRoleDialog(false);"
                        style="display: none;">❎</span></div>
                <!--<div id="role-list-head-desc">（重新打开页面/刷新即可再次选角色）</div>-->
            </div>
            <ul id="role-list-area">
                <li id="role-heiwa" class="role-list" @click="chooseRole($event.target, Role.HEIWA.id);">
                    <div class="role-list-icon-name"><span class="role-list-icon">👶🏽</span><span
                            class="role-list-name">圣婴大王（黑娃）</span></div>
                </li>
                <li id="role-jiangjiang" class="role-list" @click="chooseRole($event.target, Role.JIANGJIANG.id);">
                    <div class="role-list-icon-name"><span class="role-list-icon">🧟‍♂</span><span
                            class="role-list-name">波比僵僵（僵尸）</span></div>
                </li>
                <li id="role-duoduo" class="role-list" @click="chooseRole($event.target, Role.DUODUO.id);">
                    <div class="role-list-icon-name"><span class="role-list-icon">🥚</span><span
                            class="role-list-name">风铃朵朵（朵朵）</span></div>
                </li>
                <li id="role-kuilei" class="role-list" @click="chooseRole($event.target, Role.KUILEI.id);">
                    <div class="role-list-icon-name"><span class="role-list-icon">🦊</span><span
                            class="role-list-name">傀儡娃娃（狐狸）</span></div>
                </li>
                <li id="role-shuangzi" class="role-list" @click="chooseRole($event.target, Role.SHUANGZI.id);">
                    <div class="role-list-icon-name">
                        <span class="role-list-icon">
                            <div id="role-shuangzi-new-draw"><span id="role-shuangzi-1"
                                    class="role-shuangzi-single">🧍‍♂️</span><span id="role-shuangzi-2"
                                    class="role-shuangzi-single">🧍</span></div>
                        </span>
                        <span class="role-list-name">怪盗双子（双子）</span>
                    </div>
                </li>
                <li id="role-lele" class="role-list" @click="chooseRole($event.target, Role.DIANYIN.id);">
                    <div class="role-list-icon-name"><span class="role-list-icon">🎵</span><span
                            class="role-list-name">电音少女（电音）</span></div>
                </li>
                <li id="role-lele" class="role-list" @click="chooseRole($event.target, Role.LELE.id);">
                    <div class="role-list-icon-name"><span class="role-list-icon">🥙</span><span
                            class="role-list-name">太平乐（乐乐）</span></div>
                </li>
                <li id="role-lele" class="role-list" @click="chooseRole($event.target, Role.WUKONG.id);">
                    <div class="role-list-icon-name"><span class="role-list-icon">🐒</span><span
                            class="role-list-name">黑神话（悟空）</span></div>
                </li>
                <li id="role-huaqianji" class="role-list" @click="chooseRole($event.target, Role.HUAQIANJI.id);">
                    <div class="role-list-icon-name"><span class="role-list-icon">🚀</span><span
                            class="role-list-name">花千机（炮弹）</span></div>
                </li>
                <li id="role-youxia" class="role-list" @click="chooseRole($event.target, Role.YOUXIA.id);">
                    <div class="role-list-icon-name"><span class="role-list-icon">🏹</span><span
                            class="role-list-name">暗夜游侠（游侠）</span></div>
                </li>
                <li id="role-flash" class="role-list" @click="chooseRole($event.target, -2);">
                    <div class="role-list-icon-name"><span class="role-list-icon">⚡</span><span
                            class="role-list-name">极速开始（来吧）</span></div>
                </li>
                <li id="role-random" class="role-list" @click="chooseRole($event.target, -1);">
                    <div class="role-list-icon-name"><span class="role-list-icon">🔀</span><span
                            class="role-list-name">随便玩玩（好的）</span></div>
                </li>
            </ul>
        </div>
        <!-- 参数设置弹窗 -->
        <div id="user-setting-dialog" ref="userSettingDialog" class="collide-try-dialog">
            <div id="user-setting-head">
                <div id="user-setting-head-msg">参数设置</div>
                <div id="user-setting-close-icon"><span @click="switchUserSettingDialog(false);">❎</span></div>
                <!--<div id="user-setting-head-desc"></div>-->
            </div>
            <ul id="user-setting-area">
                <!-- 指定角色放到最上方，免得每次都要上滑页面很久【输入法会把输入框顶上去导致看不到输入框】 -->
                <li class="user-setting-item li-space-between-center">
                    <span class="user-setting-item-msg-left">自定义主题</span>
                    <span id="toggleCustomThemeSvgArrow"
                        class="user-setting-item-switch-right user-setting-item-input-area user-setting-item-right-input-area"
                        @click="toggleCustomTheme($event.target);">
                        <svg t="1723345403203" class="icon" viewBox="0 0 1024 1024" version="1.1"
                            xmlns="http://www.w3.org/2000/svg" p-id="4920" xmlns:xlink="http://www.w3.org/1999/xlink"
                            width="1000" height="1000">
                            <path
                                d="M346.52382345477406 104.43830532674417c-12.257495055447652-12.257495055447652-30.6437359627898-12.257495055447652-42.90123101823747 0s-12.257495055447652 30.6437359627898 0 42.90123101823747L668.2830560915551 512 303.6225924365366 876.6604636550185c-12.257495055447652 12.257495055447652-12.257495055447652 30.6437359627898 0 42.90123101823747 6.128747527723826 6.128747527723826 15.3218679813949 9.193120453671073 21.450615509118734 9.193120453671073s15.3218679813949-3.064372925947246 21.450615509118734-9.193120453671073l386.1110791641372-386.1110791641372c12.257495055447652-12.257495055447652 12.257495055447652-30.6437359627898 0-42.90123101823747L346.52382345477406 104.43830532674417z"
                                fill="" p-id="4921"></path>
                        </svg>
                    </span>
                </li>
                <li class="user-setting-item user-setting-item-expand li-space-between-center">
                    <span class="user-setting-item-msg-left custom-theme-item user-setting-item-disabled">启用自定义<span
                            id="resetThemeDefault" class="reset-btn" @click="resetThemeDefault($event.target);"
                            title="重置主题" style="display: none;"> 🔄 </span></span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isUseCustomTheme');">
                            <input type="checkbox" id="isUseCustomTheme">
                            <div class="slider round"></div>
                        </label>
                        <input id="customThemeInitStatus" type="hidden" value="0">
                    </span>
                </li>
                <li class="user-setting-item user-setting-item-expand li-space-between-center">
                    <span class="user-setting-item-msg-left custom-theme-item user-setting-item-disabled">导入/导出主题</span>
                    <span id="customThemeInOut" class="user-setting-item-switch-right" style="display: none;">
                        <button class="collide-try-btn bg-lv2 custom-theme-conf-inout" id="customThemeInput">导入</button>
                        <button class="collide-try-btn bg-lv1 custom-theme-conf-inout"
                            id="customThemeOutput">导出</button>
                        <input id="customThemeInputFile" type="file" style="display: none;"
                            accept="text/plain,application/json">
                    </span>
                </li>
                <li class="user-setting-item user-setting-item-expand li-space-between-center">
                    <span class="user-setting-item-msg-left custom-theme-item user-setting-item-disabled">主题名称</span>
                    <span
                        class="user-setting-item-switch-right user-setting-item-input-area user-setting-item-right-input-area">
                        <input type="text" class="custom-theme-item custom-theme-item-input user-setting-item-disabled"
                            id="name" value="自定义主题01" maxlength="7" disabled="disabled">
                    </span>
                </li>
                <li class="user-setting-item user-setting-item-expand li-space-between-center">
                    <span class="user-setting-item-msg-left custom-theme-item user-setting-item-disabled">页面背景颜色</span>
                    <span
                        class="user-setting-item-switch-right user-setting-item-input-area user-setting-item-right-input-area">
                        <input type="text"
                            class="user-setting-item-right-input-color-code custom-theme-item custom-theme-item-input user-setting-item-disabled theme-color-item"
                            id="bgColor" value="#ffffffff" maxlength="9" disabled="disabled">
                    </span>
                </li>
                <li id="page-color-image" class="user-setting-item user-setting-item-expand li-space-between-center">
                    <span class="user-setting-item-msg-left custom-theme-item user-setting-item-disabled">页面背景图片</span>
                    <span
                        class="user-setting-item-switch-right user-setting-item-input-area user-setting-item-right-input-area">
                        <input type="text" id="bgImage"
                            class="custom-theme-item custom-theme-item-input user-setting-item-disabled" value=""
                            placeholder="选择图片" maxlength="9" disabled="disabled">
                        <form class="user-setting-item-form" action="" method="post">
                            <label id="pageBgImageIcon" style="display: none;"><i class=""></i>📁</label>
                            <input id="pageBgImageFile" type="file" style="display: none;"
                                accept="image/jpg,image/jpeg,image/png,image/gif">
                        </form>
                    </span>
                </li>
                <li class="user-setting-item user-setting-item-expand li-space-between-center">
                    <span class="user-setting-item-msg-left custom-theme-item user-setting-item-disabled">台面填充颜色</span>
                    <span
                        class="user-setting-item-switch-right user-setting-item-input-area user-setting-item-right-input-area">
                        <input type="text"
                            class="user-setting-item-right-input-color-code custom-theme-item custom-theme-item-input user-setting-item-disabled theme-color-item"
                            id="tbColor" value="#ffffff00" maxlength="9" disabled="disabled">
                    </span>
                </li>
                <li class="user-setting-item user-setting-item-expand li-space-between-center">
                    <span class="user-setting-item-msg-left custom-theme-item user-setting-item-disabled">台面边框颜色</span>
                    <span
                        class="user-setting-item-switch-right user-setting-item-input-area user-setting-item-right-input-area">
                        <input type="text"
                            class="user-setting-item-right-input-color-code custom-theme-item custom-theme-item-input user-setting-item-disabled theme-color-item"
                            id="tblColor" value="#ffffff00" maxlength="9" disabled="disabled">
                    </span>
                </li>
                <li class="user-setting-item user-setting-item-expand li-space-between-center">
                    <span class="user-setting-item-msg-left custom-theme-item user-setting-item-disabled">砖格线颜色</span>
                    <span
                        class="user-setting-item-switch-right user-setting-item-input-area user-setting-item-right-input-area">
                        <input type="text"
                            class="user-setting-item-right-input-color-code custom-theme-item custom-theme-item-input user-setting-item-disabled theme-color-item"
                            id="glColor" value="#ffffff00" maxlength="9" disabled="disabled">
                    </span>
                </li>
                <li class="user-setting-item user-setting-item-expand li-space-between-center">
                    <span class="user-setting-item-msg-left custom-theme-item user-setting-item-disabled">砖格中线颜色</span>
                    <span
                        class="user-setting-item-switch-right user-setting-item-input-area user-setting-item-right-input-area">
                        <input type="text"
                            class="user-setting-item-right-input-color-code custom-theme-item custom-theme-item-input user-setting-item-disabled theme-color-item"
                            id="glmColor" value="#ffffff00" maxlength="9" disabled="disabled">
                    </span>
                </li>
                <li class="user-setting-item user-setting-item-expand li-space-between-center">
                    <span class="user-setting-item-msg-left custom-theme-item user-setting-item-disabled">砖格坐标颜色</span>
                    <span
                        class="user-setting-item-switch-right user-setting-item-input-area user-setting-item-right-input-area">
                        <input type="text"
                            class="user-setting-item-right-input-color-code custom-theme-item custom-theme-item-input user-setting-item-disabled theme-color-item"
                            id="gnColor" value="#ffffff00" maxlength="9" disabled="disabled">
                    </span>
                </li>
                <li class="user-setting-item user-setting-item-expand li-space-between-center">
                    <span
                        class="user-setting-item-msg-left custom-theme-item user-setting-item-disabled">砖格坐标黑夜颜色</span>
                    <span
                        class="user-setting-item-switch-right user-setting-item-input-area user-setting-item-right-input-area">
                        <input type="text"
                            class="user-setting-item-right-input-color-code custom-theme-item custom-theme-item-input user-setting-item-disabled theme-color-item"
                            id="gndColor" value="#ffffff00" maxlength="9" disabled="disabled">
                    </span>
                </li>
                <li class="user-setting-item user-setting-item-expand li-space-between-center">
                    <span
                        class="user-setting-item-msg-left custom-theme-item user-setting-item-disabled">角色运动路径颜色</span>
                    <span
                        class="user-setting-item-switch-right user-setting-item-input-area user-setting-item-right-input-area">
                        <input type="text"
                            class="user-setting-item-right-input-color-code custom-theme-item custom-theme-item-input user-setting-item-disabled theme-color-item"
                            id="plColor" value="#ffffff00" maxlength="9" disabled="disabled">
                    </span>
                </li>
                <li class="user-setting-item user-setting-item-expand li-space-between-center">
                    <span
                        class="user-setting-item-msg-left custom-theme-item user-setting-item-disabled">角色本体路径颜色</span>
                    <span
                        class="user-setting-item-switch-right user-setting-item-input-area user-setting-item-right-input-area">
                        <input type="text"
                            class="user-setting-item-right-input-color-code custom-theme-item custom-theme-item-input user-setting-item-disabled theme-color-item"
                            id="rlColor" value="#ffffff00" maxlength="9" disabled="disabled">
                    </span>
                </li>
                <!--
      <li class="user-setting-item user-setting-item-expand li-space-between-center">
        <span class="user-setting-item-msg-left custom-theme-item user-setting-item-disabled">傀儡运动路径颜色</span>
        <span class="user-setting-item-switch-right user-setting-item-input-area user-setting-item-right-input-area">
          <input type="text" class="user-setting-item-right-input-color-code custom-theme-item custom-theme-item-input user-setting-item-disabled theme-color-item" id="klplColor" value="#ffffff00" maxlength="9" disabled="disabled">
        </span>
      </li>
      -->
                <li class="user-setting-item user-setting-item-expand li-space-between-center">
                    <span
                        class="user-setting-item-msg-left custom-theme-item user-setting-item-disabled">分身运动路径颜色</span>
                    <span
                        class="user-setting-item-switch-right user-setting-item-input-area user-setting-item-right-input-area">
                        <input type="text"
                            class="user-setting-item-right-input-color-code custom-theme-item custom-theme-item-input user-setting-item-disabled theme-color-item"
                            id="szbplColor" value="#ffffff00" maxlength="9" disabled="disabled">
                    </span>
                </li>
                <!--
      <li class="user-setting-item user-setting-item-expand li-space-between-center">
        <span class="user-setting-item-msg-left custom-theme-item user-setting-item-disabled">分身本体路径颜色</span>
        <span class="user-setting-item-switch-right user-setting-item-input-area user-setting-item-right-input-area">
          <input type="text" class="user-setting-item-right-input-color-code custom-theme-item custom-theme-item-input user-setting-item-disabled theme-color-item" id="szbrlColor" value="#ffffff00" maxlength="9" disabled="disabled">
        </span>
      </li>
      -->
                <li class="user-setting-item user-setting-item-expand li-space-between-center">
                    <span class="user-setting-item-msg-left custom-theme-item user-setting-item-disabled">碰撞指示圈颜色</span>
                    <span
                        class="user-setting-item-switch-right user-setting-item-input-area user-setting-item-right-input-area">
                        <input type="text"
                            class="user-setting-item-right-input-color-code custom-theme-item custom-theme-item-input user-setting-item-disabled theme-color-item"
                            id="ccColor" value="#ffffff00" maxlength="9" disabled="disabled">
                    </span>
                </li>
                <li class="user-setting-item user-setting-item-expand li-space-between-center">
                    <span
                        class="user-setting-item-msg-left custom-theme-item user-setting-item-disabled">分身碰撞指示圈颜色</span>
                    <span
                        class="user-setting-item-switch-right user-setting-item-input-area user-setting-item-right-input-area">
                        <input type="text"
                            class="user-setting-item-right-input-color-code custom-theme-item custom-theme-item-input user-setting-item-disabled theme-color-item"
                            id="szccColor" value="#ffffff00" maxlength="9" disabled="disabled">
                    </span>
                </li>
                <li class="user-setting-item user-setting-item-expand li-space-between-center">
                    <span
                        class="user-setting-item-msg-left custom-theme-item user-setting-item-disabled">猴子分身提示路径颜色</span>
                    <span
                        class="user-setting-item-switch-right user-setting-item-input-area user-setting-item-right-input-area">
                        <input type="text"
                            class="user-setting-item-right-input-color-code custom-theme-item custom-theme-item-input user-setting-item-disabled theme-color-item"
                            id="wkShowColor" value="#ffffff00" maxlength="9" disabled="disabled">
                    </span>
                </li>
                <li class="user-setting-item user-setting-item-expand li-space-between-center">
                    <span class="user-setting-item-msg-left custom-theme-item user-setting-item-disabled">台面边框线宽</span>
                    <span
                        class="user-setting-item-switch-right user-setting-item-input-area user-setting-item-right-input-area">
                        <input type="text"
                            class="user-setting-item-right-input-number-m custom-theme-item custom-theme-item-input user-setting-item-disabled"
                            id="tblWidth" value="0" maxlength="5" disabled="disabled">
                    </span>
                </li>
                <li class="user-setting-item user-setting-item-expand li-space-between-center">
                    <span class="user-setting-item-msg-left custom-theme-item user-setting-item-disabled">台面砖格线宽</span>
                    <span
                        class="user-setting-item-switch-right user-setting-item-input-area user-setting-item-right-input-area">
                        <input type="text"
                            class="user-setting-item-right-input-number-m custom-theme-item custom-theme-item-input user-setting-item-disabled"
                            id="glWidth" value="0" maxlength="5" disabled="disabled">
                    </span>
                </li>
                <li class="user-setting-item user-setting-item-expand li-space-between-center">
                    <span
                        class="user-setting-item-msg-left custom-theme-item user-setting-item-disabled">砖格坐标字体大小</span>
                    <span
                        class="user-setting-item-switch-right user-setting-item-input-area user-setting-item-right-input-area">
                        <input type="text"
                            class="user-setting-item-right-input-number-m custom-theme-item custom-theme-item-input user-setting-item-disabled"
                            id="gnSize" value="0" maxlength="5" disabled="disabled">
                    </span>
                </li>
                <li class="user-setting-item user-setting-item-expand li-space-between-center">
                    <span
                        class="user-setting-item-msg-left custom-theme-item user-setting-item-disabled">角色运动路径线宽</span>
                    <span
                        class="user-setting-item-switch-right user-setting-item-input-area user-setting-item-right-input-area">
                        <input type="text"
                            class="user-setting-item-right-input-number-m custom-theme-item custom-theme-item-input user-setting-item-disabled"
                            id="plWidth" value="0" maxlength="5" disabled="disabled">
                    </span>
                </li>
                <!--
      <li class="user-setting-item user-setting-item-expand li-space-between-center">
        <span class="user-setting-item-msg-left custom-theme-item user-setting-item-disabled">傀儡运动路径线宽</span>
        <span class="user-setting-item-switch-right user-setting-item-input-area user-setting-item-right-input-area">
          <input type="text" class="user-setting-item-right-input-number-m custom-theme-item custom-theme-item-input user-setting-item-disabled" id="klplWidth" value="0" maxlength="5" disabled="disabled">
        </span>
      </li>
      -->
                <li class="user-setting-item user-setting-item-expand li-space-between-center">
                    <span class="user-setting-item-msg-left custom-theme-item user-setting-item-disabled">碰撞指示圈线宽</span>
                    <span
                        class="user-setting-item-switch-right user-setting-item-input-area user-setting-item-right-input-area">
                        <input type="text"
                            class="user-setting-item-right-input-number-m custom-theme-item custom-theme-item-input user-setting-item-disabled"
                            id="ccWidth" value="0" maxlength="5" disabled="disabled">
                    </span>
                </li>
                <li class="user-setting-item li-space-between-center" id="user-setting-item-1st">
                    <span class="user-setting-item-msg-left">游戏场景主题</span>
                    <span class="user-setting-item-switch-right">
                        <button class="dropbtn" @click="toggleDropdown()" id="sceneThemeMode">默认主题</button>
                        <div class="dropdown-content" id="themeDropdown">
                            <!-- a 标签的 href 会触发 popstate 事件 -->
                            <a @click="setSceneThemeVal($event.target, 0);">默认主题</a>
                            <!-- <a @click="setSceneThemeVal($event.target, 2);">新年主题</a> -->
                            <a @click="setSceneThemeVal($event.target, 3);">田园主题</a>
                            <a @click="setSceneThemeVal($event.target, 5);">夏日主题</a>
                            <a @click="setSceneThemeVal($event.target, 4);">星际主题</a>
                            <a @click="setSceneThemeVal($event.target, 1);">冰雪主题</a>
                        </div>
                    </span>
                </li>
                <li class="user-setting-item li-space-between-center">
                    <span class="user-setting-item-msg-left">当前操作方式</span>
                    <span class="user-setting-item-switch-right">
                        <button class="dropbtn" @click="toggleCurrPlayOpt()" id="currPlayOpt">拖拽</button>
                    </span>
                </li>
                <li class="user-setting-item li-space-between-center">
                    <span class="user-setting-item-msg-left">主角所在队颜色</span>
                    <span class="user-setting-item-switch-right">
                        <button class="dropbtn red" @click="toggleTeamColor()" id="mainTeamColor">红色</button>
                    </span>
                </li>
                <li class="user-setting-item li-space-between-center">
                    <span class="user-setting-item-msg-left">只用一个角色测试</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isTestOnlyOne');">
                            <input type="checkbox" id="isTestOnlyOne">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item li-space-between-center">
                    <span class="user-setting-item-msg-left">显示角色运动路径</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isShowBallMovePath');">
                            <input type="checkbox" id="isShowBallMovePath">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item li-space-between-center">
                    <span class="user-setting-item-msg-left">显示角色本体路径</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isShowBallPath');">
                            <input type="checkbox" id="isShowBallPath">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item li-space-between-center">
                    <span class="user-setting-item-msg-left">只瞄准不打</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isJustTrying');">
                            <input type="checkbox" id="isJustTrying">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item li-space-between-center">
                    <span class="user-setting-item-msg-left">只碰一次角色</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isRoleCollidedOnce');">
                            <input type="checkbox" id="isRoleCollidedOnce">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item li-space-between-center">
                    <span class="user-setting-item-msg-left">碰到角色即停止</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isStopAfterCollided');">
                            <input type="checkbox" id="isStopAfterCollided">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item li-space-between-center">
                    <span class="user-setting-item-msg-left">碰墙两次即停止</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isStopAfter2WallCollided');">
                            <input type="checkbox" id="isStopAfter2WallCollided">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item li-space-between-center">
                    <span class="user-setting-item-msg-left">只显示撞击台面</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isJustShowTable');">
                            <input type="checkbox" id="isJustShowTable">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item li-space-between-center">
                    <span class="user-setting-item-msg-left">显示场景图形</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isShowSceneGraph');">
                            <input type="checkbox" id="isShowSceneGraph">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item li-space-between-center">
                    <span class="user-setting-item-msg-left">显示台面边框</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch"
                            @click="switchCheckbox($event, 'isShowTableBorder', { canvasEle: gameSceneLinesCanvas });">
                            <input type="checkbox" id="isShowTableBorder">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item li-space-between-center">
                    <span class="user-setting-item-msg-left">显示砖格坐标</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch"
                            @click="switchCheckbox($event, 'isShowGridCoordinate', { canvasEle: gameSceneCoordinateCanvas });">
                            <input type="checkbox" id="isShowGridCoordinate">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item li-space-between-center">
                    <span class="user-setting-item-msg-left">显示角色血量条</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isShowRoleBloodLine');">
                            <input type="checkbox" id="isShowRoleBloodLine">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item li-space-between-center">
                    <span class="user-setting-item-msg-left">显示角色编号</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isShowRoleBloodNo');">
                            <input type="checkbox" id="isShowRoleBloodNo">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item li-space-between-center">
                    <span class="user-setting-item-msg-left">傀儡拉回</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isKuileiPullBack');">
                            <input type="checkbox" id="isKuileiPullBack">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <!--
                <li class="user-setting-item li-space-between-center">
                    <span class="user-setting-item-msg-left">瞄准穿透</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isPiercesTry');">
                            <input type="checkbox" id="isPiercesTry">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                -->
                <li class="user-setting-item li-space-between-center">
                    <span class="user-setting-item-msg-left">瞄准显示路径</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isShowTryFullPath');">
                            <input type="checkbox" id="isShowTryFullPath">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item li-space-between-center">
                    <span class="user-setting-item-msg-left">显示猴子分身提示</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isShowWkPath');">
                            <input type="checkbox" id="isShowWkPath">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item li-space-between-center">
                    <span class="user-setting-item-msg-left">双击屏幕回退</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isDbclickBack');">
                            <input type="checkbox" id="isDbclickBack">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item li-space-between-center">
                    <span class="user-setting-item-msg-left">长按重置角色位置</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isLongPressRandom');">
                            <input type="checkbox" id="isLongPressRandom">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item li-space-between-center">
                    <span class="user-setting-item-msg-left">显示角色坐标(单位：格)</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isShowRoleMovePos');">
                            <input type="checkbox" id="isShowRoleMovePos">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item li-space-between-center">
                    <span class="user-setting-item-msg-left">角色加速或减速(-20~200)</span>
                    <span
                        class="user-setting-item-switch-right user-setting-item-input-area user-setting-item-right-input-area">
                        <input type="text" class="user-setting-item-right-input-number-m" id="roleSpeedAddVal" value="0"
                            maxlength="3">
                    </span>
                </li>
                <li class="user-setting-item">
                    <span class="user-setting-item-msg-left">指定游戏角色(输入角色名)</span><span class="reset-btn"
                        @click="resetGameRoleIds(this);" title="重置角色"> 🔄 </span>
                    <div class="user-setting-item-input-area">
                        <div class="div-input-game-roles default" contenteditable="true" id="gameRoleId1"
                            placeholder="输入主角" value="">输入主角</div>
                        <div class="div-input-game-roles default" contenteditable="true" id="gameRoleId2"
                            placeholder="输入队友" value="">输入队友</div>
                        <div class="div-input-game-roles default red" contenteditable="true" id="gameRoleId3"
                            placeholder="输入对手1" value="">输入对手1</div>
                        <div class="div-input-game-roles default red" contenteditable="true" id="gameRoleId4"
                            placeholder="输入对手2" value="">输入对手2</div>
                        <div id="game-setting-main-role-dialog" class="collide-try-dialog collide-try-tiny-dialog"
                            style="display: none;">
                            <div id="game-setting-main-role-dialog-msg" class="collide-try-tiny-dialog-msg">
                                👆主角设置只在<span>【极速开始】</span>选项生效哦~</div>
                            <div id="game-setting-main-role-dialog-ok" class="collide-try-tiny-dialog-ok"
                                @click="closeGameSettingMainRoleDialog();"><span
                                    class="collide-try-dialog-ok">好的吧</span></div>
                        </div>
                    </div>
                </li>
                <li class="user-setting-item">
                    <span class="user-setting-item-msg-left">分享/导入角色及坐标</span><span class="reset-btn"
                        @click="resetShareContent(this);" title="重置分享"> 🔄 </span>
                    <div class="user-setting-item-input-area collide-try-in-one-line">
                        <input type="text" id="shareRoleAndPos" value="" maxlength="1000" placeholder="粘贴内容后点击导入">
                        <button class="collide-try-btn bg-lv1" id="rpShareCopy" @click="copyShareContent();">复制</button>
                        <button class="collide-try-btn bg-lv2" id="rpShareImport" @click="importShareContent();"
                            style="display: none;">导入</button>
                    </div>
                </li>
                <li class="user-setting-item" style="display: none;">
                    <span class="user-setting-item-msg-left">卡顿自动恢复等待时间(单位：秒)</span>
                    <div class="user-setting-item-input-area">
                        <input type="text" id="animateAutoRestTime" value="20" maxlength="100">
                    </div>
                </li>
                <li class="user-setting-item">
                    <span class="user-setting-item-msg-left">斜边倾斜偏差(单位：格)</span>
                    <div class="user-setting-item-input-area">
                        <input type="text" id="wan8CocosTableMoveVals" value="0" maxlength="100">
                    </div>
                </li>
                <li class="user-setting-item" id="collide-try-save-html" @click="saveRemoteHtml(this);">
                    <span class="user-setting-item-msg-left">下载离线版</span>
                </li>
                <li class="user-setting-item" @click="resetUserSettings()">
                    <span class="user-setting-item-msg-left">恢复默认设置</span>
                </li>
                <li class="user-setting-item" @click="switchDialogShow(aboutAppDialog, true, { display: 'unset' });">
                    <span class="user-setting-item-msg-left">关于应用</span>
                </li>
                <li class="user-setting-item">&nbsp;&nbsp;</li>
            </ul>
        </div>

        <!-- 更新提示弹窗 -->
        <div id="collide-try-update-content-dialog" ref="collideTryUpdateContentDialog"
            class="collide-try-dialog collide-try-close-btn-dialog">
            <div id="collide-try-update-content-close-icon" class="collide-try-close-btn-dialog-title-close">
                <span @click="showUpdateContent(false);">❎</span>
            </div>
            <div id="collide-try-update-content-title"
                class="collide-try-each-item-border-bottom collide-try-close-btn-dialog-title">
                <b id="update-content-title">🆕 应用更新</b>
            </div>
            <div id="collide-try-update-content" class="collide-try-close-btn-dialog-content">

            </div>
        </div>

        <!-- 操作指南弹窗 -->
        <div id="collide-try-how-to-play-dialog" class="collide-try-dialog collide-try-close-btn-dialog">
            <div class="collide-try-close-btn-dialog-title-close" style="display: none;">
                <span @click="showHowToPlay(false);">❎</span>
            </div>
            <div id="collide-try-how-to-play-title"
                class="collide-try-each-item-border-bottom collide-try-close-btn-dialog-title">
                <b>👇 操作指南</b><span>（先这样再那样🤪）</span>
            </div>
            <div id="collide-try-how-to-play-content" class="collide-try-close-btn-dialog-content">
                <pre>
                ① 拖动角色摆好位置，再拖动主角瞄准，松手开打
                ② 打完双击台面可重打；长按台面可随机重置角色位置
                ③ 设置里面可以指定任意角色哦~
                </pre>
            </div>
            <div class="collide-try-close-btn-dialog-ok" @click="showHowToPlay(false);">
                <span class="collide-try-dialog-ok">朕知道了</span>
            </div>
        </div>

        <!-- 角色坐标悬浮条 -->
        <div id="collide-try-role-pos-line" ref="collideTryRolePosLine"
            class="collide-try-dialog collide-try-role-pos-line-font">
            <b class="collide-try-role-pos-line-font">X</b> :<div
                class="div-input-role-pos collide-try-role-pos-line-font" contenteditable="false" id="rolePosX"
                placeholder="0.00" value="">
                0.00
            </div>
            <b class="collide-try-role-pos-line-font">Y</b> :<div
                class="div-input-role-pos collide-try-role-pos-line-font" contenteditable="false" id="rolePosY"
                placeholder="0.00" value="">
                0.00
            </div>
        </div>

        <!-- 关于应用弹窗 -->
        <div id="user-setting-about-app-dialog" ref="userSettingAboutAppDialog" class="collide-try-dialog">
            <div id="user-setting-about-app-close-icon" style="display: none;"><span
                    @click="switchDialogShow(aboutAppDialog, false);">❎</span></div>
            <div id="user-setting-about-app-title" class="collide-try-each-item-border-bottom">
                <b id="about-app-title">
                    <span @click="switchDialogShow(aboutAppDialog, false);"><svg t="1709376528064" class="icon"
                            viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="8794"
                            width="20" height="20">
                            <path d="M512 959.68L640 896 320 576h640v-128H320L640 128l-128-63.68L64.32 512z"
                                fill="#2c2c2c" p-id="8795"></path>
                        </svg></span>
                    关于应用
                </b>
            </div>
            <div id="user-setting-about-app-content">
                <pre>
<b class="collide-try-app-full-name collide-try-each-item-margin">玩吧-撞击王者-模拟练习工具</b>
<b class="collide-try-each-item-margin">👨‍💻 Author: THeLiGht_ Group</b>
<b class="collide-try-each-item-margin">📧 Contact: m1yellow@163.com</b>
<div class="collide-try-author-declare">
<b class="collide-try-author-declare-title">开发者声明：</b>
<ul class="collide-try-author-declare-content">
<li>1. 本工具<b>不收取任何费用</b>，也不与官方游戏产生任何关联，仅用于日常练习和交流，<b>如果有侵害到玩吧官方的利益，请玩吧工作人员直接联系上方的邮箱处理！</b></li>
<li>2. 本工具<b>保证不包含任何恶意代码，不收集任何个人隐私信息！</b></li>
<!-- <li>3. 个人站点可能会被利益相关者或不友好的人<b>【恶意匿名举报】</b>，每次申诉会在三个工作日内答复（首次申诉很快处理），但可能过不了多久又会被举报屏蔽！</li> -->
<li>3. 这个练习工具已经花费了将近两年的时间和精力开发和维护了，纯属<b>为爱发电！</b></li>
<li>4. 如果有个别浏览器屏蔽了网站导致打不开页面，可以尝试更换其他浏览器。【<a target="_blank" href="https://viayoo.com/zh-cn/">Via浏览器</a>】或【<a target="_blank" href="https://www.xbext.com/">X浏览器</a>】，极简无广告（App大小不到2M），哪个能用好用选哪个就行（没有任何推广），感谢各位玩友的信任！</li>
</ul>
</div>
<div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">📖 功能说明：<span class="collide-try-update-date"></span></b></div>
<span class="collide-try-each-item-margin">1️⃣ 支持一个主打角色、三个辅助角色，主要适用于黑娃、僵僵、朵朵、傀儡、双子、电音、太平乐、悟空等角色『角度』和『走位』练习</span>
<span class="collide-try-each-item-margin">2️⃣ 血量条仅用来区分队伍，因为血量伤害体系很复杂，目前不考虑去实现</span>
<span class="collide-try-each-item-margin">3️⃣ 角色运动速度和距离可能和实战有一定差距，做到一模一样很难</span>
<span class="collide-try-each-item-margin">4️⃣ 可能存在个别角度（碰墙角）反弹有点问题，请以实战数据为准</span>
<span class="collide-try-each-item-margin">5️⃣ 兼容手机、平板、电脑浏览器</span>
<!-- 
<div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">👨‍🏫 温馨提示：<span class="collide-try-update-date"></span></b></div>
<span class="collide-try-each-item-margin">浏览器会对打开过的网页做缓存，多次刷新只会去查询网页是否有变动，没变动是不会重新请求网页资源的，所以，<b>【刷新重选角色】要不了多少流量哦~</b></span>
<span class="collide-try-each-item-margin">输入正确访问密钥后，<b>可以到设置里面下载离线版（没有网络也可以玩）</b>，点击下载的html文件会用默认浏览器打开，也可以长按文件，选择其他方式打开。</span>
<span class="collide-try-each-item-margin">手机系统版本过低，可能会有兼容问题。如果看到一些图形显示为方块，需要升级手机系统或用新的智能手机打开；如果网页打开白屏，则是程序不兼容，可以把网址后面的“collide-try”改为“collide-try-vue”，Vue版本的程序兼容性更好哦~</span>
-->

<div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">🆕 V4.8.0 更新：<span class="collide-try-update-date">2025-09-07</span></b></div>
<pre id="collide-try-about-app-update-newest">
1. 新增【只碰一次角色】开关，方便练习碰撞反弹角度
2. 修复了角色碰撞反弹角度可能不正确的问题
3. 优化了一些已知问题
</pre>
                <div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">V4.7.1 更新：<span
                            class="collide-try-update-date">2025-08-30</span></b></div>
                1. 优化了贴边碰撞可能碰不到的问题
                2. 调整了应用名称

                <div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">V4.7.0 更新：<span
                            class="collide-try-update-date">2025-08-23</span></b></div>
                1. 新增血量条显示角色编号
                2. 优化了一些已知问题

                <div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">V4.6.3 更新：<span
                            class="collide-try-update-date">2025-08-18</span></b></div>
                1. 修复高屏幕刷新率（90/120Hz）兼容性问题
                2. 补全角色录入（70个）

                <div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">V4.6.2 更新：<span
                            class="collide-try-update-date">2025-03-11</span></b></div>
                1. 不公平的游戏，全是⭕️💰️和算计！
                2. 游戏的意义应该是和有趣的人轻松愉快地享受游戏过程，而不是每日每夜千篇一律地打来打去、比来比去！

                <div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">V4.6.1 更新：<span
                            class="collide-try-update-date">2025-02-23</span></b></div>
                1. 新增【点按发射】操作方式
                2. 补全角色录入（67个）

                <div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">V4.6.0 更新：<span
                            class="collide-try-update-date">2025-01-29</span></b></div>
                1. 优化角色碰撞反弹角度问题
                2. 调整台面斜边角度更接近实战
                3. 补全角色录入（66个）

                <div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">V4.5.5 更新：<span
                            class="collide-try-update-date">2024-11-24</span></b></div>
                1. 双子、悟空分身速度调整
                2. 补全角色录入（65个）

                <div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">V4.5.4 更新：<span
                            class="collide-try-update-date">2024-09-03</span></b></div>
                1. 优化傀儡、僵僵、幽灵等可穿透角色碰蛋问题
                2. 补全角色录入（63个）

                <div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">V4.5.3 更新：<span
                            class="collide-try-update-date">2024-08-28</span></b></div>
                1. 重新调整角色速度和摩擦力，让运动碰撞更接近实战

                <div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">V4.5.2 更新：<span
                            class="collide-try-update-date">2024-08-25</span></b></div>
                1. 选择角色列表新增【悟空】选项
                2. 修复自定义主题已知的问题

                <div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">V4.5.1 更新：<span
                            class="collide-try-update-date">2024-08-21</span></b></div>
                1. 新增双击砖格坐标补全数字功能
                2. 加入自定义主题【取色器】，改颜色更便捷
                3. 完善自定义主题重置功能

                <div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">V4.5.0 更新：<span
                            class="collide-try-update-date">2024-08-15</span></b></div>
                1. 刷新页面重选角色改为点击左上角重选角色，不用频繁刷新页面，节省性能
                2. 选择角色列表新增【电音少女】选项
                3. 修复自定义主题已知的问题

                <div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">V4.4.0 更新：<span
                            class="collide-try-update-date">2024-08-12</span></b></div>
                1. 自定义主题尝鲜版（支持设置背景图片，只会在应用内存储，不会上传哦~）

                <div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">V4.3.0 更新：<span
                            class="collide-try-update-date">2024-08-08</span></b></div>
                1. 优化傀儡、僵僵等角色瞄准时不灵敏的问题
                2. 优化长按台面随机重置角色位置不灵敏的问题
                3. 修复碰蛋时位置坐标会出现偏差的问题

                <div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">V4.2.4 更新：<span
                            class="collide-try-update-date">2024-08-06</span></b></div>
                1. 重新加入访问密钥（玩友私聊获取即可哦）
                2. 【关于应用】添加网站被QQ浏览器屏蔽声明

                <div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">V4.2.3 更新：<span
                            class="collide-try-update-date">2024-08-05</span></b></div>
                1. 游戏场景图形重叠问题优化
                2. 【关于应用】添加了版本更新日期

                <div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">V4.2.2 更新：<span
                            class="collide-try-update-date">2024-08-02</span></b></div>
                1. 新增【操作指南】说明，首次进入游戏时提示
                2. 调整双子图标（有显示问题可以反馈一下）
                3. 更新【关于应用】内容

                <div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">V4.2.1 更新：<span
                            class="collide-try-update-date">2024-07-31</span></b></div>
                1. 新增【瞄准穿透】开关，弥补傀儡、僵僵等可穿透角色瞄准时的流畅灵敏度
                2. 补全角色录入（62个）

                <div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">V4.2.0 更新：<span
                            class="collide-try-update-date">2024-07-21</span></b></div>
                1. 新增【夏日主题】
                2. 主题模式随季节自动切换
                3. 补全角色录入（61个）

                <div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">V4.1.5 更新：<span
                            class="collide-try-update-date">2024-07-18</span></b></div>
                1. 新增【显示角色运动路径】开关功能
                2. 修复移动端多点触碰可能出现卡死的问题
                3. 加入超时自动结束（默认20秒），避免程序一直卡死消耗性能
                4. 【保存离线版】（不用联网）改为【下载离线版】（要联网，更可靠）

                <div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">V4.1.4 更新：<span
                            class="collide-try-update-date">2024-05-24</span></b></div>
                1. 兼容适配平板浏览器
                2. 角色图标、场景主题图形大小调整
                3. 加入『告别』信息，退游一段时间

                <div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">V4.1.3 更新：<span
                            class="collide-try-update-date">2024-04-10</span></b></div>
                1. 新增【显示角色坐标】功能
                2. 新增【分享/导入角色及坐标】功能

                <div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">V4.1.2 更新：<span
                            class="collide-try-update-date">2024-03-27</span></b></div>
                1. 离线版调整为不需要输入访问密钥
                2. 新增切换【主角所在队颜色】功能
                3. 优化【只显示撞击台面】、【显示场景图形】开关，免刷新页面

                <div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">V4.1.1 更新：<span
                            class="collide-try-update-date">2024-03-18</span></b></div>
                1. 新增【显示砖格坐标】功能
                2. 新增【长按重置角色位置】功能
                3. 优化【显示台面边框】、【显示砖格坐标】开关，免刷新页面

                <div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">V4.1.0 更新：<span
                            class="collide-try-update-date">2024-03-13</span></b></div>
                1. 新增【瞄准显示路径】功能
                2. 修复【只瞄准不打】时的拖动问题
                3. 加入更新提示
                4. 优化拖动、瞄准时的动画渲染，减少性能消耗

                <div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">V4.0.3 更新：<span
                            class="collide-try-update-date">2024-03-11</span></b></div>
                1. 实现傀儡拉回功能
                2. 新增太平乐练习选项

                <div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">V4.0.2 更新：<span
                            class="collide-try-update-date">2024-03-09</span></b></div>
                1. 修复僵僵、傀儡瞄准时穿透问题
                2. 实现电音突破加速效果
                3. 加入访问密钥（玩友私聊获取即可哦）

                <div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">V4.0.1 更新：<span
                            class="collide-try-update-date">2024-03-07</span></b></div>
                1. 新增【保存离线版】功能
                2. 设置主角时，提示使用【极速开始】才生效

                <div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">V4.0.0 更新：<span
                            class="collide-try-update-date">2024-03-02</span></b></div>
                1. 可以在设置里面指定任意角色
                2. 新增【双击屏幕回退】重打功能
                3. 游戏界面右上角加入隐形设置按钮，多项设置不用刷新页面
                4. 新增【关于应用】信息
                5. 角色动画分层优化，减少性能消耗


                <b class="collide-try-each-item-border-bottom">🔗 参考文章：</b>
                <a target="_blank"
                    href="https://www.kai666666.com/2020/07/28/Canvas%E7%B3%BB%E5%88%97%EF%BC%8814%EF%BC%89%EF%BC%9A%E5%AE%9E%E6%88%98-%E5%B0%8F%E7%90%83%E7%A2%B0%E6%92%9E/">Canvas系列（14）：实战-小球碰撞</a><a
                    target="_blank" href="https://cloud.tencent.com/developer/article/1722313"> ② </a>
                <a target="_blank"
                    href="https://www.kai666666.com/2020/08/04/Canvas%E7%B3%BB%E5%88%97%EF%BC%8816%EF%BC%89%EF%BC%9A%E5%AE%9E%E6%88%98-%E5%B0%8F%E7%90%83%E4%B8%8E%E6%96%9C%E9%9D%A2%E7%A2%B0%E6%92%9E/">Canvas系列（16）：实战-小球与斜面碰撞</a><a
                    target="_blank" href="https://cloud.tencent.com/developer/article/1720496"> ② </a>
                <a target="_blank" href="https://www.w3cschool.cn/xjmuw/xjmuw-ymch25y5.html">canvas动画包教不包会：坐标旋转和斜面反弹</a>
                <a target="_blank" href="https://juejin.cn/post/7016972355956113439">使用canvas制作一个小球碰撞模型</a>

                </pre>

                <br><br>
                <div id="collide-try-bye-reason" class="collide-try-goodbye">
                    <pre>
<div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">几个游戏公平建议：<span class="collide-try-update-date"></span></b></div>
<span class="collide-try-each-item-margin">① 开局在选择角色框下方加入“石头剪刀布”选项，谁赢谁先手！系统不要帮选，不选则后手，选完在游戏界面公示！平局再按现有的蓝红顺序轮流先手方式</span>
<span class="collide-try-each-item-margin">② 1号位先打，2号位后打，交给玩家自己决定，玩家就想1号位先打就这么难？（已实现）</span>
<span class="collide-try-each-item-margin">③ 开局角色位置、🌿、💣、🍄、🔪 等陷阱位置，请完全随机！哪有那么巧就刚好给直线？</span>
<span class="collide-try-each-item-margin">④ 加入『允许发言交流』勾选框，只要有一个玩家不勾选，就不能发言和发表情！</span>
<span class="collide-try-each-item-margin">⑤ 加入《撞王等级资格证》机制，根据上一个赛季和当前赛季最高段位自动区分，大奖赛【大师】以下段位加入撞王等级匹配规则，避免 20、30 多级的玩家频繁对阵满级大佬被气走！留住新用户才有得 ⭕ 啊！[狗头]</span>
<span class="collide-try-each-item-margin">⑥ 中奖概率有偏爱就不提了！回馈衣食父母也没错 👌</span>

你在教我做事？
游戏公平！玩的人更多！格局打开！


<div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">不公平！BUG太多！太浪费时间精力！<span class="collide-try-update-date"></span></b></div>
<span class="collide-try-each-item-margin">• 牺牲公平换利益，实在是玩不过！每天都会被不公平和各种BUG气炸！（越是在乎，看得越清，就会越气）</span>
<span class="collide-try-each-item-margin">• 工作、生活已经够累了，还要比来比去！游戏娱乐放松了个啥？游戏社交真的能交到好朋友或奔现对象？</span>
<span class="collide-try-each-item-margin">• 40级以下，技巧不够、没角色或者只有标配组合，很难打赢高配组合，大概率白送；40级以上，几乎都是高配，先手和开局位置至关重要，两局甚至三局不给先手，大概率连跪！先手和开局好位置给谁，懂的都懂！</span>
<span class="collide-try-each-item-margin">• 耗费一两年好不容易换齐了高配组合，又陆续搞出新的“一刀666”的⭕️💰️角色，永远都是花钱的爽，不花钱的陪玩！</span>
<span class="collide-try-each-item-margin">• 一直匹配满级满角色的对手，还一直给对手先手和开局位置优势，谁有这个时间精力被这样算计戏弄？每天拿一两个小时宝贵的业余时间来玩游戏，换来的却是算计和气愤！</span>


<div class="collide-try-update-title"><b class="collide-try-each-item-border-bottom">所以呢？还玩吗？<span class="collide-try-update-date"></span></b></div>
<span class="collide-try-each-item-margin">• <b>清楚自己为什么玩这个游戏！</b>不公平的事情多了去了！怕浪费时间精力就减少做任务/冲分的局数，或者跟好友过一下日常任务、切磋几局练习角色技巧，再或者每天登录签到就行了！</span>
<span class="collide-try-each-item-margin">• <b>目标段位期望太高会玩得很累！</b>角色搭配没凑齐高配，撞击技巧（角度、连击、落点）熟练度不够（角色 > 技巧 = 运气[氪金]），遇到满级大佬或者突破&高配组合确实很难赢（毕竟他们已经玩了几年了）！很多 20、30 多级的玩家大奖赛频繁对阵满级大佬，输到怀疑人生，没挺过这段艰难的瓶颈期就气到【注销】了！</span>
<span class="collide-try-each-item-margin">• <b>大奖赛“日三”，最多二十局完不成就放下吧！</b>平均一大局（3小局）7 分钟，10 局就一个多小时，20 局两小时以上，每天几个小时玩游戏是挺奢侈的了！用一半的游戏时间经营打理现实生活，会不会更有意义？</span>
<span class="collide-try-each-item-margin">•【角色拼不过】+【系统先后手和开局位置算计】+【一个劲儿不认输】，新手角色跟高配角色比拼，就像“鸡蛋碰石头”和高等数学，打不过就是打不过！不会就是不会！<b>这个【拼角色】的游戏别太较劲硬肝！40级之前，角色兑换路线和技巧练习才是关键！</b></span>


                    </pre>
                </div>
                <div id="collide-try-bye" class="collide-try-goodbye">
                    <span>就只想单纯地玩一下游戏，<br>可曾想被游戏玩得一塌糊涂！</span><br>
                    <span id="see-you-next-time">有缘再见~</span>
                </div>
            </div>
        </div>

        <!-- SVG 图形区域，CSS 设置不显示，宽高过大会导致原有样式错位 -->
        <div class="svg-image-area">
            <!-- https://icons.bootcss.com/icons/snow2/ -->
            <!-- https://yqnn.github.io/svg-path-editor/ -->
            <!-- 默认主题-中心图形 -->
            <svg xmlns="http://www.w3.org/2000/svg" width="800" height="800" fill="#6274C490" id="svg-default-center"
                class="bi bi-default-center" viewBox="0 0 800 800">
                <path
                    d="M39,361l30.165-17.437,30.526,15.268L71.346,378.462Zm662.489-17.437,30.526-15.269L762,345l-29.985,18.194ZM252.321,295.575s-4-11.846,6.541-15.269c0,0,7.614-2.782,17.444,8.725,0,0,4.3,11.666-6.541,15.269C269.765,304.3,259.013,307.626,252.321,295.575Zm82.856-102.519s-1.426-13.026,10.9-10.906c0,0,8.137-.392,10.9,10.906,0,0,2.2,11.184-10.9,10.907C346.08,203.963,338.523,204.884,335.177,193.056Zm2.181,370.813s1.134-10.64,10.9-8.725c0,0,7.362-.237,10.9,8.725,0,0,1.475,12.706-10.9,10.906C348.26,574.775,339.665,575.264,337.358,563.869Zm104.66,2.181s1.121-11.772,13.083-10.906c0,0,9.711,2.567,8.722,10.906,0,0,.728,8.846-10.9,10.906C452.92,576.956,444,578.611,442.018,566.05ZM402.771,361.012s0.222-12.616,13.082-15.268c0,0,9.647-2.729,13.083,15.268,0,0-1.931,11.839-13.083,13.088C415.853,374.1,404.6,372.223,402.771,361.012ZM531,337c4.43,5.388,5.75,43.344,3,40l75.911-24.713Zm-19.208-47.969s-11.152-21.5-30.526-28.356l87.217-74.162Zm-74.135-32.719C428.364,235.6,394.038,50.255,398.41,60l-10.9,161.412S354.487,232.022,333,251.95l-82.856-54.531,58.871,82.887s-17.634,25.994-17.443,56.713L189,358l102.569,16.1s26.934,89.76,111.2,87.25c0,0,98.875,1.955,93.758-100.338,0,0-7.184-64.79-69.774-65.437,0,0-40.215-1.321-54.51,39.263,0,0-7.811,27.219,13.082,47.987,0,0-20.41-45.658,23.673-64.825,0,0,35.347-7.477,48.281,32.106,0,0,16.709,63.783-49.281,77.894,0,0-76.807,4.3-83.725-73.531C324.275,354.469,312.226,252.288,437.657,256.312ZM278.486,428.631L93.15,657.662,274.125,487.525s29.3,23.868,37.068,28.356L283,605l56.538-76.031s20.24,12.3,45.789,13.087L400.59,758s15.5-195.811,17.279-218.224C417.977,538.415,418,540,418,540s33.951-3.5,48-17l71,71-42.651-86.844s17.212-10.4,34.886-32.719L725.474,624.944,518.333,428.631s-42.507,62.707-113.382,67.619C404.951,496.25,343.848,502.446,278.486,428.631Z" />
            </svg>
            <!-- 冰雪主题-中心雪花 -->
            <svg xmlns="http://www.w3.org/2000/svg" width="1600" height="1600" fill="#EEF0F220" id="svg-snow"
                class="bi bi-snow2" viewBox="0 0 1600 1600">
                <path
                    d="M 800 1600 a 50 50 90 0 1 -50 -50 v -129.3 l -64.6 64.7 a 50 50 90 0 1 -70.7 -70.8 L 750 1279.3 v -108.6 l -64.6 64.7 a 50 50 90 0 1 -70.7 -70.8 L 750 1029.3 V 886.6 l -123.6 71.3 l -49.5 185 a 50 50 90 1 1 -96.6 -26 l 23.7 -88.2 l -94 54.2 l -49.6 185 a 50 50 90 1 1 -96.6 -26 l 23.7 -88.2 l -112 64.6 a 50 50 90 0 1 -50 -86.6 l 112 -64.6 l -88.4 -23.7 a 50 50 90 1 1 26 -96.6 l 184.8 49.5 l 94 -54.2 l -88.2 -23.7 a 50 50 90 1 1 25.8 -96.6 l 185 49.5 L 700 800 l -123.6 -71.3 l -184.9 49.5 a 50 50 90 1 1 -25.8 -96.6 l 88.3 -23.7 l -94 -54.2 l -185 49.5 a 50 50 90 0 1 -25.8 -96.6 l 88.3 -23.7 l -112 -64.6 a 50 50 90 1 1 50 -86.6 l 112 64.6 l -23.7 -88.3 a 50 50 90 0 1 96.6 -25.8 l 49.5 184.9 l 94 54.2 l -23.6 -88.3 a 50 50 90 0 1 96.6 -25.8 l 49.5 184.9 l 123.6 71.3 V 570.7 L 614.7 435.4 a 50 50 90 1 1 70.7 -70.8 l 64.6 64.7 V 320.7 L 614.7 185.4 a 50 50 90 1 1 70.7 -70.8 l 64.6 64.7 V 50 a 50 50 90 0 1 100 0 v 129.3 l 64.7 -64.7 a 50 50 90 1 1 70.7 70.8 L 850 320.7 v 108.6 l 64.7 -64.7 a 50 50 90 1 1 70.7 70.8 L 850 570.7 v 142.7 l 123.6 -71.3 l 49.5 -185 a 50 50 90 1 1 96.6 26 l -23.6 88.2 l 94 -54.2 l 49.5 -185 a 50 50 90 1 1 96.6 26 l -23.6 88.2 l 112 -64.6 a 50 50 90 0 1 50 86.6 l -112 64.6 l 88.3 23.7 a 50 50 90 1 1 -26 96.6 l -184.8 -49.5 l -94 54.2 l 88.3 23.7 a 50 50 90 1 1 -26 96.6 l -184.8 -49.5 L 900 800 l 123.6 71.3 l 184.9 -49.5 a 50 50 90 0 1 25.9 96.6 l -88.3 23.7 l 94 54.2 l 184.9 -49.5 a 50 50 90 0 1 25.9 96.6 l -88.3 23.7 l 112 64.6 a 50 50 90 0 1 -50 86.6 l -112 -64.6 l 23.6 88.3 a 50 50 90 1 1 -96.6 25.8 l -49.5 -184.9 l -94 -54.2 l 23.6 88.3 a 50 50 90 0 1 -96.6 25.8 L 973.6 958 L 850 886.6 v 142.7 l 135.4 135.3 a 50 50 90 0 1 -70.7 70.8 l -64.7 -64.7 v 108.6 l 135.4 135.3 a 50 50 90 0 1 -70.7 70.8 l -64.7 -64.7 V 1550 a 50 50 90 0 1 -50 50 z" />
            </svg>
            <!-- 默认主题-骨头 -->
            <svg xmlns="http://www.w3.org/2000/svg" width="1156" height="517" fill="#FAF8F9A0" id="svg-bone"
                class="bi bi-bone" viewBox="0 0 1156 517">
                <path
                    d="M792.742,214l57.981,11c3.363-29.552-.866-54.089-7-78-2.4-9.366-.024-22.848-2-32-2.756-12.77-5.116-37.265,5-41,4.986-3.95,15.353-.123,20.994,2,17.974,6.764,38.175,12.06,55.981,20,7.922,3.532,15.683,10.442,23.993,14,11.179,4.787,21.369,6.927,30.989,13,9.948,6.279,18.756,14.747,28.989,21,10.71,6.539,22.34,9.5,32.99,16,29.58,18.072,58.62,36.04,84.97,57,13.08,10.4,24.71,32.444,26,54,0.61,10.3,1.26,27.307-5,31-6.46,4.477-16.89,2.009-25.99,4-23.16,5.063-56.47.19-80.98,0-9.79-.076-18.55-2.665-25.99,0,0.63,1.754.19,0.971,1,2,2.47,7.744,9.69,9.051,15.99,13,10.61,6.641,22.03,13.213,34.99,18,7.46,2.755,22.38,4.63,27.99,9h-1c-11.71,11.493-31.73,15.109-47.98,22-41.91,17.771-86.1,28-143.953,28-18.818,0-34.74,2-54.982,2H823.732c-5.875-1.889-8.167-7.075-12-11-0.354-17.627,7.822-25.443,13-37,10.049-22.45,19.493-45.007,19.993-77l-3-1c-7.616-5.636-41.911-9.444-53.982-12-4.534,52.915-31.062,101.589-51.984,140-6.922,12.709-17.711,39.253-34.988,40a18.324,18.324,0,0,1-1-6c3.474-3.869,3.686-8.7,6-14,5.09-11.667,10.537-23.4,16-36,14.961-34.548,40.4-82.758,41.986-128l-96.968-16c1.058,44.646-16.339,103.107-33.989,130-3.4,5.179-9.339,9.173-13,14-6.087,8.037-14.232,21.163-25.991,23-1.588-2.95-2.075-5.721-2-11,7.807-10.562,8.419-33.928,13-48,10.814-33.244,20.663-67.317,20.993-110h-2c-4.541-2.84-13.811.31-19.994-1-8.691-1.842-46.887-4.9-52.982-3,4.532,13.093,2,33.92,2,50,0,59.086-15.28,98.1-43.986,128l-4-2c-2.163-18.366,1.188-44.319,5-62q0.5-57.995,1-116c-22.312-.853-50.247,3.117-69.978,9-8.128,2.424-17.691.73-23.992,5-0.96,1.418-.976,3.273-1,6,5.5,8.265,1.426,25.461,3,37,4.01,29.431-17.2,68-28.991,87-4.908,7.908-8.173,23.353-19.993,24v-2c-3.549-5.645,0-30.838,0-40,0-34.26,4.652-65.063,5-101h-1c-2.467,1.738-4.363.709-8,2-12.15,4.316-26.066,10.022-37.988,15-7.112,2.97-16.413,2.355-16.994,12,3.65,5.559,3.123,27.578,3,37-0.324,24.556-14.154,38.656-25.992,52-4.013,4.524-6.914,10.639-14,12-1.124.144-1.787-.067-4-1-3.809-30.813,6.634-57.745,7-89h-2c-6.774,5.9-31.421,12.544-40.987,17-2.567,23.606-22.621,48.571-30.99,68-3.571,8.291-3.524,16.462-7,25-8.157,20.047-17.051,45.871-26.991,65-6.367,12.253-20.929,42.732-36.988,43a24.966,24.966,0,0,0-4-5c0.2-20.015,1.553-52.337-3-69-2.362-8.649-8.5-11.167-9-22,3.069-3.5,3.484-8.853,6-13,6.228-10.274,14.561-22.634,17.994-35a23.635,23.635,0,0,1-8-1,16.936,16.936,0,0,1-2-6c2.161-2.688,3.173-7.056,4-11h-1c-3.27,3.075-38.246,15.949-42.986,13-2.222-1.382-1.89-4.365-2-8,8.746-8.589,19.334-20.834,24.992-32h-2c-1.8,1.488-28.293,10.916-30.99,10-3.031-1.029-3.655-3.981-4-8,7.331-4.806,12.683-11.772,20.993-16v-1h-2c-6.953,4.614-44.236,12.022-54.982,10-1.113-2.476-1.687-3.233-2-7,3.921-3.582,16.349-13.578,17.994-18-13.905-1.408-28.469-9.161-39.987-14-4.759-2-12.629-.525-15-5-0.877-1.3-.894-2.467-1-5a18.058,18.058,0,0,0,4-3c78.125,0.41,150.189,14.25,216.929,26,11.007,1.938,35.66-13.768,43.986-18,3.636-1.848,12.182-3.6,14-7V256c-5.011-7.79-4.018-22.785-9-31-12.138-20.028-28.283-36.567-44.985-52-0.093-10.478,3.9-10.265,9-15,48.81,0.306,58.334,66.3,72.976,103,14.669-6.819,28.894-16.5,43.986-23,6.26-2.7,19.386-4.919,21.993-11-2.408-3.732-1.451-9.225-3-14-3.124-9.629-6.752-20.225-11-30-10.143-23.359-27.548-42.49-37.987-65-4.851-10.459-15.093-29.765,5-29,6.659,6.867,17.167,10.312,24.992,16,5.709,4.15,9.708,11.31,13.995,17l11,10c16.367,22.489,22.482,55.04,32.989,83,17.461-6.611,34.972-9.887,53.982-16,13-4.18,28.214-9.018,43.986-10,0.105-8.829-2.206-16.135-4-23-4.822-18.464-5.314-34.9-12-51-3.043-7.334-8.352-14.31-12-21-6.378-11.711-10.614-24.409-19.993-33a50.141,50.141,0,0,1,1-11c26.713-15.492,39.515.656,49.984,20,16.506,30.5,30.855,76.456,35.988,117,27.335-.087,52.049,1.905,77.975,2,0.445-28.115-8.134-49.972-15-71-5.828-17.862-8.185-32.654-15-49-4.326-10.382-22.8-39.378-17-53,2.189-5.133,7.417-7.271,11-11,27.522-1.686,35.066,13.431,45.985,31,16.622,26.746,22.822,59.785,30.99,96,4.425,19.621.079,41.827,4,62h6c7.736,4.675,24.731,2.585,34.989,5l56.981,10v-2c-2.106-3.544.138-10.073-1-15-3.084-13.361-.965-28.537-5-41-9.288-28.7-15.7-57.04-26.991-83-4.342-9.981-12.346-18.946-16.994-28-3.851-7.5-8.294-28.548-1-34,2.841-2.245,8.155-2.879,13-3,6.25,5.347,15.159,8.379,19.993,15C759.2,32.3,761.34,48.786,767.75,68c4.578,13.723,10.611,29.339,15,44q1.5,12,3,24C791.106,158.74,792.56,187,792.742,214Zm172.944-56c-3.7,2.2-10,1.3-14,3-10.252,4.349-21.064,15.4-24.992,26-11.145,30.082,19.654,64.22,51.983,56C1028.9,230.232,1018.28,160.747,965.686,158Zm140.954,63c-0.96,1.766-1.26,1.68-2,4,6,2.193,5.51,6.5,14,7a10.727,10.727,0,0,1,2-3c-0.64-1.754-.2-0.971-1-2-1.19-3.511-2.84-3.73-5-6h-8Z" />
            </svg>
            <!-- 默认主题-石头 -->
            <svg xmlns="http://www.w3.org/2000/svg" width="800" height="800" id="svg-stone" class="bi bi-stone"
                viewBox="0 0 1024 1024">
                <path
                    d="M614.737067 655.978667c2.4192 0.605867 43.178667-9.796267 46.199466-12.458667 6.4128-5.802667 84.535467-101.956267 97.719467-116.347733-0.610133-4.352 0.1152-2.901333-4.842667-6.165334l-49.9456-30.4768c3.264-3.869867-0.362667-1.3312 4.232534-2.299733l95.057066-38.8224c4.232533-1.6896 10.5216-3.0208 13.7856-6.894933l-39.424-49.5872c-5.568-7.8592-14.276267-17.416533-19.716266-24.5504-9.915733-12.9408-32.533333-39.061333-38.8224-50.1888-1.813333-3.268267-6.045867-9.796267-8.4608-13.064534-1.937067-2.538667-3.268267-4.1088-4.842667-6.7712l-21.768533-32.776533-23.825067-23.825067c-27.456-0.605867-24.3072-3.0208-37.009067-15.9616-17.2928-17.898667-58.2912-43.054933-76.189866-58.052266l-150.442667 17.9072-98.568533 3.0208-101.469867 185.642666c-8.465067 9.553067-18.261333 20.1984-26.1248 30.357334 3.264 4.714667 0.482133-1.450667 1.088 2.781866 0 0.2432-0.362667 1.450667-0.4864 1.937067 11.733333 2.781867 23.825067 6.7712 35.554133 10.039467l66.274134 24.187733c20.680533 7.739733 19.9552 11.1232 34.709333 28.177067l81.271467 96.0256c6.165333 7.377067 11.1232 14.148267 17.655466 21.2864 5.201067 5.6832 121.301333 41.723733 136.661334 46.314666 12.821333 3.7504 62.523733 21.892267 71.4752 20.322134l0.256 0.2432z"
                    fill="#13227a" p-id="3204"></path>
                <path
                    d="M458.120533 847.6672c10.402133 2.180267 31.5648-0.2432 42.449067-0.3584 40.029867-0.482133 90.461867-3.392 128.9216-3.268267 10.525867 0 10.525867 1.813333 18.0224-4.957866 21.6448-19.349333 29.755733-22.980267 54.664533-37.858134 10.282667-6.0416 31.2064-20.189867 40.64-23.940266l15.232-6.1696c0.366933-0.119467 1.693867-0.605867 2.180267-0.725334l49.344-158.6688a2027.989333 2027.989333 0 0 1 24.5504-79.825066c4.232533-12.817067 8.226133-26.363733 12.091733-38.698667 2.542933-8.226133 4.232533-11.490133 8.708267-16.448 2.658133-3.0208 7.8592-7.377067 9.314133-12.578133l-0.482133 5.9264c4.957867-4.475733-0.362667-12.578133-2.7776-17.053867-5.205333-9.796267-20.1984-44.987733-24.797867-52.608-3.0208-4.8384-47.044267-49.224533-54.545066-56.6016L682.709333 246.839467c-5.568-4.232533-15.36-3.5072-22.493866-5.077334l23.825066 23.825067 21.7728 32.776533c1.570133 2.6624 2.901333 4.232533 4.834134 6.7712 2.4192 3.268267 6.656 9.796267 8.465066 13.064534 6.293333 11.246933 28.906667 37.248 38.826667 50.1888 5.44 7.133867 14.148267 16.6912 19.707733 24.5504l39.428267 49.5872c-3.144533 3.7504-9.553067 5.201067-13.7856 6.894933l-122.3936 39.6672c3.025067 3.144533 90.824533-2.4192 95.185067-2.4192 11.972267 0.119467 22.370133-1.207467 35.191466-1.3312 10.5216-0.119467 24.5504-1.937067 36.040534-1.211733-3.7504 4.475733-24.311467 12.334933-32.290134 16.6912l-44.872533 20.322133c-4.5952 2.414933-6.894933 3.8656-11.485867 6.0416-13.184 14.391467-91.306667 110.5408-97.719466 116.347733-3.0208 2.781867-43.780267 13.184-46.199467 12.458667-4.8384 6.045867-8.221867 30.839467-10.039467 39.185067-26.850133-3.989333-79.0912-7.620267-110.178133-10.402134l-72.443733-5.563733c-25.518933-1.6896-23.7056-4.8384-32.0512 4.352-5.802667 6.293333-14.997333 18.2656-21.649067 22.856533-7.8592 5.3248-17.053867 11.127467-23.825067 17.053867l18.8672 12.9408c5.077333 3.746133 34.833067 40.3968 41.723734 47.650133l53.090133 63.735467-0.119467-0.128z"
                    fill="#13227a" p-id="3205"></path>
                <path
                    d="M186.248533 702.664533c3.144533-1.937067-1.813333-1.211733 5.077334-1.088l14.8736 2.295467c39.547733 7.253333 98.688 11.127467 138.116266 19.4688 6.7712-6.045867 15.965867-11.733333 23.825067-17.0496 6.7712-4.599467 15.965867-16.571733 21.649067-22.856533 8.3456-9.070933 6.532267-5.9264 32.0512-4.356267l72.443733 5.563733c31.202133 2.781867 83.451733 6.532267 110.178133 10.402134 1.8176-8.341333 5.320533-33.1392 10.039467-39.185067-8.951467 1.6896-58.653867-16.448-71.4752-20.317867-15.364267-4.599467-131.464533-40.635733-136.661333-46.318933-6.651733-7.2576-11.6096-14.0288-17.655467-21.2864l-81.271467-96.0256c-14.634667-17.053867-13.909333-20.4416-34.709333-28.177067l-66.286933-24.192c-11.733333-3.268267-23.825067-7.2576-35.554134-10.039466 0.119467-0.362667 0.4864-1.6896 0.4864-1.9328-0.605867-4.356267 2.176 1.9328-1.088-2.781867-17.898667 25.275733-11.733333 46.318933-8.465066 76.194133 2.781867 25.156267 5.077333 48.8576 7.620266 74.1376 1.6896 16.324267 13.179733 142.340267 16.6912 147.5456h0.1152z"
                    fill="#13227a" p-id="3206"></path>
                <path
                    d="M281.186133 817.070933c0.968533-4.475733-2.901333-1.207467 9.6768 1.3312l123.477334 22.737067c7.739733 1.454933 41.122133 9.796267 43.780266 6.528l-53.090133-63.735467c-6.7712-7.2576-36.6464-43.784533-41.723733-47.650133l-18.8672-12.9408c-39.547733-8.341333-98.688-12.334933-138.116267-19.4688l-14.8736-2.295467c-6.894933-0.123733-1.937067-0.849067-5.077333 1.088 16.448 18.8672 31.684267 37.853867 47.168 56.840534 3.869867 4.714667 44.266667 55.2704 47.7696 57.6896l-0.123734-0.123734z"
                    fill="#13227a" p-id="3207"></path>
                <path
                    d="M863.633067 470.216533l0.482133-5.9264c-1.450667 5.201067-6.651733 9.4336-9.314133 12.578134-4.475733 4.957867-6.1696 8.221867-8.708267 16.448-3.869867 12.334933-7.863467 25.8816-12.096 38.702933a2042.112 2042.112 0 0 0-24.5504 79.816533l-49.339733 158.673067c-0.482133 0.119467-1.8176 0.605867-2.176 0.725333l-15.240534 6.165334c-9.4336 3.7504-30.353067 17.783467-40.631466 23.9488-24.917333 14.754133-33.015467 18.385067-54.6688 37.8496-7.5008 6.775467-7.5008 4.957867-18.018134 4.957866-38.464-0.2432-88.891733 2.781867-128.925866 3.268267-11.008 0.123733-32.0512 2.542933-42.449067 0.366933-2.6624 3.264-36.040533-5.0816-43.780267-6.532266l-123.477333-22.7328c-12.578133-2.542933-8.708267-5.806933-9.6768-1.335467 4.957867 5.802667 104.3712 37.4912 111.022933 38.216533l100.501334 0.725334c65.668267 0.849067 132.1856-2.176 196.8896-5.802667 6.1696-0.362667 6.289067-0.2432 10.039466-3.144533a174.0928 174.0928 0 0 0 8.827734-7.253334c5.320533-4.714667 11.729067-9.553067 16.810666-13.909333l67.844267-56.1152c3.0208-4.714667 10.641067-52.002133 12.4544-61.435733 7.5008-39.185067 13.422933-85.504 24.917333-122.632534 4.8384-15.726933 32.896-107.153067 33.258667-115.7376v0.1152z"
                    fill="#13227a" p-id="3208"></path>
                <path
                    d="M743.300267 534.673067c5.316267-2.542933 8.098133-4.1088 13.422933-7.0144l52.612267-23.825067c9.309867-5.077333 33.501867-14.272 37.8496-19.592533-13.422933-0.8448-29.870933 1.3312-42.325334 1.450666-15.121067 0.119467-27.217067 1.6896-41.365333 1.570134-5.073067 0-76.066133 5.444267-79.697067 1.813333-5.444267 1.088-1.088-1.813333-4.962133 2.6624l58.658133 35.8016c5.806933 3.8656 4.957867 2.176 5.6832 7.253333l0.123734-0.119466z"
                    fill="#13227a" p-id="3209"></path>
            </svg>
            <!-- 夏日主题-小黄鸭 -->
            <svg xmlns="http://www.w3.org/2000/svg" width="800" height="800" id="svg-yl-duck" class="bi bi-yl-duck"
                viewBox="0 0 1024 1024">
                <path
                    d="M212.5 465c-13.8 4.1-25.5 13.1-33.1 25.3-36.4 58.5-126.6 237.8 38.5 367.8 199.9 157.4 655 68.1 699.7-197.8C953.7 445.5 890 364.7 802.8 320c0 0-51-23.4-106.3 0l-484 145z"
                    fill="#FFDC48" p-id="4556"></path>
                <path
                    d="M526.2 543.3s191.5-7.9 194.7 78.2c1.6 42.1-122.8 357.8-467.3 260 0 0 281.2 161.6 574.6-59.6 216.9-280.7 21.3-572.1-123.4-508.3S526.2 543.3 526.2 543.3z"
                    fill="#FFBE3C" p-id="4557"></path>
                <path
                    d="M206 482.7c21.9 37.2 57.5 64.4 99 76.2 36 10.2 79.1 16.2 125.4 16.2 49.8 0 95.9-6.9 133.5-18.6 39.9-12.4 73.8-39.5 94.6-75.7 0.1-0.2 0.2-0.4 0.3-0.5 21.8-38 34.3-82 34.4-128.9 0.5-144.5-117.1-262.5-261.6-262.5C287.1 88.9 170 206 170 350.5c0.1 48.2 13.2 93.4 36 132.2z"
                    fill="#FFDC48" p-id="4558"></path>
                <path
                    d="M431.7 88.8c-16.7 0-33 1.6-48.8 4.6 95.3 28.8 165 117.7 164.6 222.2-0.1 41.5-11.2 80.3-30.4 113.9-0.1 0.2-0.2 0.3-0.3 0.5-18.4 32-48.4 56-83.6 66.9-33.2 10.4-74 16.5-118 16.5-34.3 0-66.6-3.7-94.9-10.2 21.7 26.7 51.3 46.2 84.8 55.7 36 10.2 79.1 16.2 125.4 16.2 49.8 0 95.9-6.9 133.5-18.6 39.9-12.4 73.8-39.5 94.6-75.7 0.1-0.2 0.2-0.4 0.3-0.5 21.8-38 34.3-82 34.4-128.9 0.5-144.5-117.1-262.6-261.6-262.6z"
                    fill="#FFBE3C" p-id="4559"></path>
                <path
                    d="M162 409.9l18.1-9.6c36.3-12.7 76.6-4.4 104.8 21.7 31.8 34 52.7 59.2 85.1 78.4 4.5 2.7 7.3 7.5 7.3 12.7v12.2c0 11.9-8.5 22.2-20.2 24.5-55.5 10.7-209.4 30.8-260-61.8-15.4-37.2 64.9-78.1 64.9-78.1z"
                    fill="#FF4160" p-id="4560"></path>
                <path
                    d="M324.6 464.1L304 447.6s-164.2 68.3-193.9 59.2c0.2 0.3 0.5 0.6 0.7 0.8 13.8 8.5 85.8 48.9 178.4 34.6 103.1-16 81-41.8 81-41.8-17.4-10.3-31.4-22.2-45.6-36.3z"
                    fill="#F43459" p-id="4561"></path>
                <path
                    d="M361.8 513.2c-51.5 12.7-179.2 36.7-257.2-13.4 56.8 79.1 199.6 60.3 252.6 50 11.7-2.3 20.2-12.5 20.2-24.5v-12.2c0-2.8-0.8-5.4-2.2-7.7-3.6 3.7-8.2 6.5-13.4 7.8z"
                    fill="#DB214E" p-id="4562"></path>
                <path
                    d="M776.9 784.8s-125.5 61.7-153.1-51c-25.5-146.7 140.4-117 163.8-153.1 25.8-39.9 42.5-112.7 70.2-70.2s32.9 210.5-80.9 274.3z"
                    fill="#FFDC48" p-id="4563"></path>
                <path
                    d="M667 793.5c46.6 22.4 109.9-8.8 109.9-8.8C890.7 721 885.4 553 857.7 510.4s-44.3 30.3-70.2 70.2c26.3 95.2-16.2 172.2-120.5 212.9z"
                    fill="#FFBE3C" p-id="4564"></path>
                <path d="M405.2 357.4m-40.7 0a40.7 40.7 0 1 0 81.4 0 40.7 40.7 0 1 0-81.4 0Z" fill="#FFBE3C"
                    p-id="4565"></path>
                <path d="M397.4 351.7m-40.7 0a40.7 40.7 0 1 0 81.4 0 40.7 40.7 0 1 0-81.4 0Z" fill="#5E4153"
                    p-id="4566"></path>
                <path
                    d="M918.4 421.2c-20.9-49.4-55.8-85.2-109.7-112.9-0.2-0.1-0.3-0.2-0.5-0.2-2.2-1-50.4-22.5-105.8-4.3-10.4-60.4-40.9-115.8-87-157.3-50.6-45.6-115.8-70.7-183.7-70.7-151.4 0-274.6 123.2-274.6 274.6 0 15.2 1.3 30.4 3.7 45.3l-4.8 2.5c-9.7 5-90.3 47.9-70.9 94.7 0.2 0.4 0.4 0.9 0.6 1.3 12.4 22.6 30 39.1 50.7 50.9-33.2 79.6-61.1 217.3 73.4 323.1 57.7 45.4 136.9 72.8 229.2 79.2 13.4 0.9 26.9 1.4 40.5 1.4 74.5 0 150.8-13.8 218.5-40 60.7-23.5 113.5-56.6 152.5-95.8 43.6-43.8 70.5-94.5 79.9-150.6 17.3-102.5 13.3-181.4-12-241.2zM431.7 101.9c126.8 0 233 95 247 221 1 9.3 1.6 18.9 1.5 28.4-0.1 43-11.4 85.3-32.7 122.4-0.1 0.2-0.3 0.5-0.3 0.6-19.3 33.5-50.2 58.3-87.2 69.8-37.8 11.8-82.6 18-129.6 18-20.3 0-40.4-1.2-59.6-3.5 11.8-6.5 19.6-19.1 19.6-33.2v-12.2c0-9.8-5.2-19-13.7-24-26.2-15.5-44.3-35.1-69.4-62.3-4.1-4.4-8.4-9-12.8-13.8-0.2-0.2-0.4-0.5-0.7-0.7-29.3-27.2-70-37.2-108.3-27.4-1.6-11.4-2.4-23-2.4-34.6 0-3.1 0.1-6.1 0.2-9.2C194.5 334 202 321.4 202 307c0-9.7-3.4-18.6-9.1-25.6 30-103.5 125.7-179.5 238.8-179.5zM109 482.5c-6.3-17.8 31.2-46.8 59-61 0.1 0 0.1-0.1 0.2-0.1l17.2-9.1c31.4-10.7 65.9-3.4 90.4 19 4.3 4.6 8.4 9.1 12.4 13.3 25.6 27.7 45.8 49.5 75.3 67 0.5 0.3 0.9 0.9 0.9 1.5v12.2c0 5.7-4 10.6-9.6 11.7-45.8 8.8-198.2 30.8-245.8-54.5z m795.7 175.6c-16.3 97.1-95.1 179.6-216.1 226.4-161.7 62.5-356.3 47-462.6-36.7-115.4-90.8-101.4-206.4-66-291.4 31.6 12.1 67.4 16.2 101.1 16.2 13.2 0 26.1-0.6 38.3-1.6 0.7 0.2 1.3 0.4 2 0.6 38.4 10.9 83 16.7 128.9 16.7 49.6 0 97.1-6.6 137.4-19.2 43.2-13.5 79.5-42.5 102.1-81.8l0.2-0.3c0-0.1 0.1-0.1 0.1-0.2 23.5-41 36-87.8 36.2-135.4 0-7-0.2-14-0.8-21 45.9-17.4 88.4 0.1 91.5 1.4 74.1 38 144.6 106.6 107.7 326.3z"
                    fill="#5E4153" p-id="4567"></path>
                <path
                    d="M841.5 482.8c-19.6 1.3-31.1 25.4-44.5 53.4-6 12.5-12.1 25.4-18.7 35.6-4.4 6.8-25.8 11.8-44.8 16.2-27.9 6.5-62.5 14.6-87.9 35-30.4 24.5-41.5 61.9-32.9 111.3 0.1 0.3 0.1 0.6 0.2 0.9 8.3 33.7 25.5 56.9 51.1 68.9 14.1 6.6 29.2 9 43.8 9 39.1 0 74.6-17.2 76.7-18.2l0.6-0.3c60.1-33.7 85.2-91.6 95.7-134.2 16-64.8 7.3-131.6-10.4-158.7-8.6-13.3-18.3-19.6-28.9-18.9z m7 33c12.5 19.2 21.8 77.8 6.9 138.2-9.2 37.5-31.1 88.3-82.8 117.4-4.4 2.1-59 27-97.7 8.8-18-8.4-30.3-25.6-36.6-50.9-15.2-88.8 46.6-103.2 101.1-115.9 28.3-6.6 50.7-11.8 60.8-27.4 7.5-11.6 14.1-25.3 20.4-38.5 6.2-13 16.4-34.4 22.3-38.3 1 0.7 2.9 2.5 5.6 6.6z"
                    fill="#5E4153" p-id="4568"></path>
                <path d="M384.7 339.1m-12.7 0a12.7 12.7 0 1 0 25.4 0 12.7 12.7 0 1 0-25.4 0Z" fill="#FFFFFF"
                    p-id="4569"></path>
                <path
                    d="M225.5 485.3c-5.1-0.5-9.6-4-11.2-9.1-2.1-6.9 1.7-14.2 8.6-16.3 15.5-4.8 33.8-13 34-13.1 6.6-3 14.3 0 17.3 6.5 3 6.6 0 14.3-6.5 17.3-0.8 0.4-19.9 8.9-37 14.2-1.8 0.5-3.5 0.7-5.2 0.5z"
                    fill="#FFD7DF" p-id="4570"></path>
            </svg>

            <!-- 角色icon图标 -->

        </div>

        <!-- 显示console.log日志 -->
        <div id="info" ref="info" @click="show();" type="0"></div>
    </main>
</template>

<script setup>
import { onBeforeMount, onMounted, onBeforeUnmount, onUnmounted } from "vue";

const packageVersion = __APP_VERSION__;

// https://github.com/MaksymSemenykhin/javascript-aes
"use strict"; var Aes = {}; if (Aes.cipher = function (e, r) { for (var o = 4, n = r.length / o - 1, t = [[], [], [], []], s = 0; 4 * o > s; s++)t[s % 4][Math.floor(s / 4)] = e[s]; t = Aes.addRoundKey(t, r, 0, o); for (var f = 1; n > f; f++)t = Aes.subBytes(t, o), t = Aes.shiftRows(t, o), t = Aes.mixColumns(t, o), t = Aes.addRoundKey(t, r, f, o); t = Aes.subBytes(t, o), t = Aes.shiftRows(t, o), t = Aes.addRoundKey(t, r, n, o); for (var a = new Array(4 * o), s = 0; 4 * o > s; s++)a[s] = t[s % 4][Math.floor(s / 4)]; return a }, Aes.keyExpansion = function (e) { for (var r = 4, o = e.length / 4, n = o + 6, t = new Array(r * (n + 1)), s = new Array(4), f = 0; o > f; f++) { var a = [e[4 * f], e[4 * f + 1], e[4 * f + 2], e[4 * f + 3]]; t[f] = a } for (var f = o; r * (n + 1) > f; f++) { t[f] = new Array(4); for (var i = 0; 4 > i; i++)s[i] = t[f - 1][i]; if (f % o == 0) { s = Aes.subWord(Aes.rotWord(s)); for (var i = 0; 4 > i; i++)s[i] ^= Aes.rCon[f / o][i] } else o > 6 && f % o == 4 && (s = Aes.subWord(s)); for (var i = 0; 4 > i; i++)t[f][i] = t[f - o][i] ^ s[i] } return t }, Aes.subBytes = function (e, r) { for (var o = 0; 4 > o; o++)for (var n = 0; r > n; n++)e[o][n] = Aes.sBox[e[o][n]]; return e }, Aes.shiftRows = function (e, r) { for (var o = new Array(4), n = 1; 4 > n; n++) { for (var t = 0; 4 > t; t++)o[t] = e[n][(t + n) % r]; for (var t = 0; 4 > t; t++)e[n][t] = o[t] } return e }, Aes.mixColumns = function (e, r) { for (var o = 0; 4 > o; o++) { for (var n = new Array(4), t = new Array(4), s = 0; 4 > s; s++)n[s] = e[s][o], t[s] = 128 & e[s][o] ? e[s][o] << 1 ^ 283 : e[s][o] << 1; e[0][o] = t[0] ^ n[1] ^ t[1] ^ n[2] ^ n[3], e[1][o] = n[0] ^ t[1] ^ n[2] ^ t[2] ^ n[3], e[2][o] = n[0] ^ n[1] ^ t[2] ^ n[3] ^ t[3], e[3][o] = n[0] ^ t[0] ^ n[1] ^ n[2] ^ t[3] } return e }, Aes.addRoundKey = function (e, r, o, n) { for (var t = 0; 4 > t; t++)for (var s = 0; n > s; s++)e[t][s] ^= r[4 * o + s][t]; return e }, Aes.subWord = function (e) { for (var r = 0; 4 > r; r++)e[r] = Aes.sBox[e[r]]; return e }, Aes.rotWord = function (e) { for (var r = e[0], o = 0; 3 > o; o++)e[o] = e[o + 1]; return e[3] = r, e }, Aes.sBox = [99, 124, 119, 123, 242, 107, 111, 197, 48, 1, 103, 43, 254, 215, 171, 118, 202, 130, 201, 125, 250, 89, 71, 240, 173, 212, 162, 175, 156, 164, 114, 192, 183, 253, 147, 38, 54, 63, 247, 204, 52, 165, 229, 241, 113, 216, 49, 21, 4, 199, 35, 195, 24, 150, 5, 154, 7, 18, 128, 226, 235, 39, 178, 117, 9, 131, 44, 26, 27, 110, 90, 160, 82, 59, 214, 179, 41, 227, 47, 132, 83, 209, 0, 237, 32, 252, 177, 91, 106, 203, 190, 57, 74, 76, 88, 207, 208, 239, 170, 251, 67, 77, 51, 133, 69, 249, 2, 127, 80, 60, 159, 168, 81, 163, 64, 143, 146, 157, 56, 245, 188, 182, 218, 33, 16, 255, 243, 210, 205, 12, 19, 236, 95, 151, 68, 23, 196, 167, 126, 61, 100, 93, 25, 115, 96, 129, 79, 220, 34, 42, 144, 136, 70, 238, 184, 20, 222, 94, 11, 219, 224, 50, 58, 10, 73, 6, 36, 92, 194, 211, 172, 98, 145, 149, 228, 121, 231, 200, 55, 109, 141, 213, 78, 169, 108, 86, 244, 234, 101, 122, 174, 8, 186, 120, 37, 46, 28, 166, 180, 198, 232, 221, 116, 31, 75, 189, 139, 138, 112, 62, 181, 102, 72, 3, 246, 14, 97, 53, 87, 185, 134, 193, 29, 158, 225, 248, 152, 17, 105, 217, 142, 148, 155, 30, 135, 233, 206, 85, 40, 223, 140, 161, 137, 13, 191, 230, 66, 104, 65, 153, 45, 15, 176, 84, 187, 22], Aes.rCon = [[0, 0, 0, 0], [1, 0, 0, 0], [2, 0, 0, 0], [4, 0, 0, 0], [8, 0, 0, 0], [16, 0, 0, 0], [32, 0, 0, 0], [64, 0, 0, 0], [128, 0, 0, 0], [27, 0, 0, 0], [54, 0, 0, 0]], "undefined" != typeof module && module.exports && (module.exports = Aes), "undefined" != typeof module && module.exports) var Aes = require("./aes.js"); Aes.Ctr = {}, Aes.Ctr.encrypt = function (e, r, o) { var n = 16; if (128 != o && 192 != o && 256 != o) throw new Error("Key size is not 128 / 192 / 256"); e = String(e).utf8Encode(), r = String(r).utf8Encode(); for (var t = o / 8, s = new Array(t), f = 0; t > f; f++)s[f] = f < r.length ? r.charCodeAt(f) : 0; var a = Aes.cipher(s, Aes.keyExpansion(s)); a = a.concat(a.slice(0, t - 16)); for (var i = new Array(n), d = (new Date).getTime(), u = d % 1e3, c = Math.floor(d / 1e3), p = Math.floor(65535 * Math.random()), f = 0; 2 > f; f++)i[f] = u >>> 8 * f & 255; for (var f = 0; 2 > f; f++)i[f + 2] = p >>> 8 * f & 255; for (var f = 0; 4 > f; f++)i[f + 4] = c >>> 8 * f & 255; for (var A = "", f = 0; 8 > f; f++)A += String.fromCharCode(i[f]); for (var y = Aes.keyExpansion(a), h = Math.ceil(e.length / n), l = "", v = 0; h > v; v++) { for (var g = 0; 4 > g; g++)i[15 - g] = v >>> 8 * g & 255; for (var g = 0; 4 > g; g++)i[15 - g - 4] = v / 4294967296 >>> 8 * g; for (var w = Aes.cipher(i, y), b = h - 1 > v ? n : (e.length - 1) % n + 1, C = new Array(b), f = 0; b > f; f++)C[f] = w[f] ^ e.charCodeAt(v * n + f), C[f] = String.fromCharCode(C[f]); l += C.join(""), "undefined" != typeof WorkerGlobalScope && self instanceof WorkerGlobalScope && v % 1e3 == 0 && self.postMessage({ progress: v / h }) } return l = (A + l).base64Encode() }, Aes.Ctr.decrypt = function (e, r, o) { var n = 16; if (128 != o && 192 != o && 256 != o) throw new Error("Key size is not 128 / 192 / 256"); e = String(e).base64Decode(), r = String(r).utf8Encode(); for (var t = o / 8, s = new Array(t), f = 0; t > f; f++)s[f] = f < r.length ? r.charCodeAt(f) : 0; var a = Aes.cipher(s, Aes.keyExpansion(s)); a = a.concat(a.slice(0, t - 16)); for (var i = new Array(8), d = e.slice(0, 8), f = 0; 8 > f; f++)i[f] = d.charCodeAt(f); for (var u = Aes.keyExpansion(a), c = Math.ceil((e.length - 8) / n), p = new Array(c), A = 0; c > A; A++)p[A] = e.slice(8 + A * n, 8 + A * n + n); e = p; for (var y = "", A = 0; c > A; A++) { for (var h = 0; 4 > h; h++)i[15 - h] = A >>> 8 * h & 255; for (var h = 0; 4 > h; h++)i[15 - h - 4] = (A + 1) / 4294967296 - 1 >>> 8 * h & 255; for (var l = Aes.cipher(i, u), v = new Array(e[A].length), f = 0; f < e[A].length; f++)v[f] = l[f] ^ e[A].charCodeAt(f), v[f] = String.fromCharCode(v[f]); y += v.join(""), "undefined" != typeof WorkerGlobalScope && self instanceof WorkerGlobalScope && A % 1e3 == 0 && self.postMessage({ progress: A / c }) } return y = y.utf8Decode() }, "undefined" == typeof String.prototype.utf8Encode && (String.prototype.utf8Encode = function () { return unescape(encodeURIComponent(this)) }), "undefined" == typeof String.prototype.utf8Decode && (String.prototype.utf8Decode = function () { try { return decodeURIComponent(escape(this)) } catch (e) { return this } }), "undefined" == typeof String.prototype.base64Encode && (String.prototype.base64Encode = function () { if ("undefined" != typeof btoa) return btoa(this); if ("undefined" != typeof Buffer) return new Buffer(this, "binary").toString("base64"); throw new Error("No Base64 Encode") }), "undefined" == typeof String.prototype.base64Decode && (String.prototype.base64Decode = function () { if ("undefined" != typeof atob) return atob(this); if ("undefined" != typeof Buffer) return new Buffer(this, "base64").toString("binary"); throw new Error("No Base64 Decode") }), "undefined" != typeof module && module.exports && (module.exports = Aes.Ctr);


// https://github.com/zhouatie/plugin/tree/master/colorpicker
(function () {

    var util = {
        css: function (elem, obj) {
            for (var i in obj) {
                elem.style[i] = obj[i];
            }
        },
        hasClass: function (elem, classN) {
            var className = elem.getAttribute("class");
            return className.indexOf(classN) != -1;
        },
        // 判断是否为颜色码
        isColorCode: function (str) {
            if (!str || typeof str !== "string" || str.replaceAll(" ", "") === "") return false;
            if (!str.startsWith("#") || !(/^[A-Fa-f0-9]{3,8}$/.test(str.substring(1)))) return false;
            let len = str.substring(1).length; // 去掉#，3、4、6、8 正常可用
            if (len === 5 || len === 7) return false;
            return true;
        },
        // 颜色短码补全（8位形式）
        getFullColorCode: function (code) {
            if (!code || !this.isColorCode(code)) return code;
            // 不算#，3、4 位短码，每一位重复一次
            // 算上#，往后顺移一位
            code = code.slice(1);
            if (code.length == 3) return '#' + code[0] + code[0] + code[1] + code[1] + code[2] + code[2] + "ff";
            if (code.length == 4) return '#' + code[0] + code[0] + code[1] + code[1] + code[2] + code[2] + code[3] + code[3];
            if (code.length == 6) return '#' + code + "ff";
            return '#' + code;
        },
        // 获取不带透明度的颜色码+开头#
        getColorCodeNormal: function (code) {
            if (!code || !this.isColorCode(code)) return code;
            // 不算#，3-每一位重复一次；4-前三位每一位重复一次；6-直接返回；8-截取前6位
            code = code.slice(1);
            if (code.length === 4) code = code.substring(0, 3);
            if (code.length === 3) return '#' + code[0] + code[0] + code[1] + code[1] + code[2] + code[2];
            if (code.length === 6) return '#' + code;
            if (code.length > 6) return '#' + code.substring(0, 6);
            return '#' + code;
        }
    };

    function Colorpicker(elem) {

        this.bindElem = elem; // 绑定的元素
        this.elem_wrap = null; // 最外层容器
        this.fixedBg = null; // 拾色器后面固定定位的透明div 用于点击隐藏拾色器
        this.elem_colorPickerPancel = null; // 整个取色器面板
        this.elem_colorPancel = null; // 色彩面板
        this.elem_picker = null; // 拾色器色块按钮
        this.elem_barPicker1 = null; // 颜色条
        this.elem_barPicker2 = null; // 透明条
        this.elem_hexInput = null; // 显示hex的表单
        this.elem_showColor = null; // 显示当前颜色
        this.elem_opacityPancel = null; // 透明度背景元素
        this.elem_showModeBtn = null; // 切换输入框模式按钮
        this.elem_inputWrap = null; // 输入框外层容器

        this.pancelLeft = 0;
        this.pancelTop = 0;

        this.downX = 0;
        this.downY = 0;
        this.moveX = 0;
        this.moveY = 0;

        this.pointLeft = 0;
        this.pointTop = 0;

        this.current_mode = 'hex'; // input框当前的模式

        this.rgba = {
            r: 0,
            g: 0,
            b: 0,
            a: 1
        };

        this.hsb = {
            h: 0,
            s: 100,
            b: 100
        };

        try {
            this.init();
        } catch (e) {
            console.log(e.message);
        }
    };
    /*
    var default = {
        elem:obj,
        cards:['#000','#fff'],
        afterCreat : fn
    }
    */
    Colorpicker.Opt = {
        singleton: false, // TODO 后续考虑修改，单例并不一定就好，需要更新不同绑定元素及事件
        bindClass: '',
        initColor: "rgb(255,0,0)",
        allMode: ['hex', 'rgb']
    }

    Colorpicker.create = function (opt) {
        for (var prop in opt) {
            Colorpicker.Opt[prop] = opt[prop];
        };

        var elemArr = document.getElementsByClassName(Colorpicker.Opt.bindClass);

        for (var i = 0; i < elemArr.length; i++) {
            elemArr[i].colorpicker = new Colorpicker(elemArr[i]);
        }

    }

    Colorpicker.prototype = {
        render: function () {
            var tpl = '<div style="position: fixed; top: 0px; right: 0px; bottom: 0px; left: 0px;"></div>' +
                '<div style="position: inherit; z-index: 100;">' +
                '<div class="colorpicker-pancel" style="background: rgb(255, 255, 255); border-radius: 2px; box-shadow: rgba(0, 0, 0, 0.3) 0px 0px 2px, rgba(0, 0, 0, 0.3) 0px 4px 8px; box-sizing: initial; width: 225px; font-family: Menlo;"><div style="width: 100%; padding-bottom: 55%; position: relative; border-radius: 2px 2px 0px 0px; overflow: hidden;">' +
                '<div class="color-pancel" style="position: absolute; top: 0px; right: 0px; bottom: 0px; left: 0px; background: rgb(' + this.rgba.r + ',' + this.rgba.g + ',' + this.rgba.b + ')">' +
                '<style>' +
                '.saturation-white {background: -webkit-linear-gradient(to right, #fff, rgba(255,255,255,0));background: linear-gradient(to right, #fff, rgba(255,255,255,0));}' +
                '.saturation-black {background: -webkit-linear-gradient(to top, #000, rgba(0,0,0,0));background: linear-gradient(to top, #000, rgba(0,0,0,0));}' +
                '</style>' +
                '<div class="saturation-white" style="position: absolute; top: 0px; right: 0px; bottom: 0px; left: 0px;">' +
                '<div class="saturation-black" style="position: absolute; top: 0px; right: 0px; bottom: 0px; left: 0px;"></div>' +
                '<div class="pickerBtn" style="position: absolute; top: 0%; left: 100%; cursor: default;">' +
                '<div style="width: 14px; height: 14px; border-radius: 50%; box-shadow: rgb(255, 255, 255) 0px 0px 0px 1px inset; transform: translate(-6px, -6px);"></div>' +
                '</div>' +
                '</div>' +
                '</div>' +
                '</div>' +
                '<div style="padding: 16px 16px 12px;">' +
                '<div class="flexbox-fix" style="display: flex;">' +
                '<div style="width: 32px; display: inline-flex; flex-direction: row; justify-content: flex-start; align-items: center;">' +
                '<div style="width: 20px; height: 20px; border-radius: 50%; position: relative; overflow: hidden;">' +
                '<div class="colorpicker-showColor" style="position: absolute; top: 0px; right: 0px; bottom: 0px; left: 0px; border-radius: 50%; box-shadow: rgba(0, 0, 0, 0.1) 0px 0px 0px 1px inset; background:rgb(' + this.rgba.r + ',' + this.rgba.g + ',' + this.rgba.b + '); z-index: 2;"></div>' +
                '<div class="" style="position: absolute; top: 0px; right: 0px; bottom: 0px; left: 0px; background: url(&quot;data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAAMUlEQVQ4T2NkYGAQYcAP3uCTZhw1gGGYhAGBZIA/nYDCgBDAm9BGDWAAJyRCgLaBCAAgXwixzAS0pgAAAABJRU5ErkJggg==&quot;) left center;"></div></div></div><div style="-webkit-box-flex: 1; flex: 1 1 0%;"><div style="height: 12px; position: relative; margin-bottom: 12px;"><div style="position: absolute; top: 0px;' + 'right: 0px; bottom: 0px; left: 0px;"><div class="hue-horizontal" style="padding: 0px 2px; position: relative; height: 100%;">' +
                '<style>' +
                '.hue-horizontal {background: linear-gradient(to right, #f00 0%, #ff0 17%, #0f0 33%, #0ff 50%, #00f 67%, #f0f 83%, #f00 100%);background: -webkit-linear-gradient(to right, #f00 0%, #ff0 17%, #0f0 33%, #0ff 50%, #00f 67%, #f0f 83%, #f00 100%);}' +
                '.hue-vertical {background: linear-gradient(to top, #f00 0%, #ff0 17%, #0f0 33%,#0ff 50%, #00f 67%, #f0f 83%, #f00 100%);background: -webkit-linear-gradient(to top, #f00 0%, #ff0 17%,#0f0 33%, #0ff 50%, #00f 67%, #f0f 83%, #f00 100%);}' +
                '</style>' +
                '<div  class="colorBar-color-picker" style="position: absolute; left: 0%;">' +
                '<div style="width: 14px; height: 14px; border-radius: 50%; transform: translate(-6px, -1px); background-color: rgb(248, 248, 248); box-shadow: rgba(0, 0, 0, 0.37) 0px 1px 4px 0px;">' +
                '</div>' +
                '</div>' +
                '</div>' +
                '</div>' +
                '</div>' +
                '<div style="height: 12px; position: relative;">' +
                '<div style="position: absolute; top: 0px; right: 0px; bottom: 0px; left: 0px;">' +
                '<div style="position: absolute; top: 0px; right: 0px; bottom: 0px; left: 0px; overflow: hidden;">' +
                '<div style="position: absolute; top: 0px; right: 0px; bottom: 0px; left: 0px; background: url(&quot;data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAAMUlEQVQ4T2NkYGAQYcAP3uCTZhw1gGGYhAGBZIA/nYDCgBDAm9BGDWAAJyRCgLaBCAAgXwixzAS0pgAAAABJRU5ErkJggg==&quot;) left center;"></div>' +
                '</div>' +
                '<div style="position: absolute; top: 0px; right: 0px; bottom: 0px; left: 0px; background: linear-gradient(to right, rgba(' + this.rgba.r + ',' + this.rgba.g + ',' + this.rgba.b + ',0) 0%, rgb(' + this.rgba.r + ',' + this.rgba.g + ',' + this.rgba.b + ') 100%);"></div>' +
                '<div style="position: relative; height: 100%;">' +
                '<div class="colorBar-opacity-picker" style="position: absolute; left: 100%;">' +
                '<div style="width: 14px; height: 14px; border-radius: 50%; transform: translate(-6px, -1px); background-color: rgb(248, 248, 248); box-shadow: rgba(0, 0, 0, 0.37) 0px 1px 4px 0px;"></div>' +
                '</div>' +
                '</div>' +
                '</div>' +
                '</div>' +
                '</div>' +
                '</div>' +
                '<div class="flexbox-fix" style="padding-top: 10px; display: flex;">' +
                '<div class="flexbox-fix colorpicker-inputWrap" style="-webkit-box-flex: 1; flex: 1 1 0%; display: flex; margin-left: -6px;">';

            tpl += this.getInputTpl();
            tpl += '</div>' +
                '<div class="colorpicker-showModeBtn" style="width: 32px; text-align: right; position: relative; display: none;">' +
                '<div style="margin-right: -4px;  cursor: pointer; position: relative;">' +
                '<svg viewBox="0 0 24 24" style="width: 24px; height: 24px; border: 1px solid transparent; border-radius: 5px;"><path fill="#333" d="M12,5.83L15.17,9L16.58,7.59L12,3L7.41,7.59L8.83,9L12,5.83Z"></path><path fill="#333" d="M12,18.17L8.83,15L7.42,16.41L12,21L16.59,16.41L15.17,15Z"></path></svg>' +
                '</div>' +
                '</div>' +
                '</div>' +
                '</div>' +
                '</div>' +
                '</div>';

            return tpl;
        },
        getInputTpl: function (hex) {
            var current_mode_html = "";
            switch (this.current_mode) {
                case 'hex':
                    //var hex = "#"+this.rgbToHex(this.HSBToRGB(this.hsb));
                    current_mode_html += '<div style="padding-left: 6px; width: 100%;">' +
                        '<div style="position: relative;">' +
                        '<input class="colorpicker-hexInput" value="' + hex + '" maxlength="9" spellcheck="false" style="font-size: 11px; color: rgb(51, 51, 51); width: 100%; border-radius: 2px; border: none; box-shadow: rgb(218, 218, 218) 0px 0px 0px 1px inset; height: 21px; text-align: center;">' +
                        '<span style="text-transform: uppercase; font-size: 11px; line-height: 11px; color: rgb(150, 150, 150); text-align: center; display: block; margin-top: 12px; display: none;">hex</span>' +
                        '</div>' +
                        '</div>';
                    break;
                case 'rgb':
                    for (var i = 0; i < 3; i++) {
                        current_mode_html += '<div style="padding-left: 6px; width: 100%;">' +
                            '<div style="position: relative;">' +
                            '<input class="colorpicker-hexInput" value="' + this.rgba['rgb'[i]] + '" maxlength="3" spellcheck="false" style="font-size: 11px; color: rgb(51, 51, 51); width: 100%; border-radius: 2px; border: none; box-shadow: rgb(218, 218, 218) 0px 0px 0px 1px inset; height: 21px; text-align: center;">' +
                            '<span style="text-transform: uppercase; font-size: 11px; line-height: 11px; color: rgb(150, 150, 150); text-align: center; display: block; margin-top: 12px;">' + ('rgb'[i]) + '</span>' +
                            '</div>' +
                            '</div>';
                    }
                default:

            }
            return current_mode_html;
        },
        init: function () {
            // 颜色码统一转小写
            if (this.bindElem && this.bindElem.value) this.bindElem.value = this.bindElem.value.toLocaleLowerCase();

            var _this = this,
                initColor = (this.bindElem && this.bindElem.value && util.isColorCode(this.bindElem.value)) ? this.rgbToStr(this.hexToRgb(this.bindElem.value)) : Colorpicker.Opt.initColor,
                rgb = initColor.slice(4, -1).split(",");

            this.rgba.r = parseInt(rgb[0]);
            this.rgba.g = parseInt(rgb[1]);
            this.rgba.b = parseInt(rgb[2]);
            this.rgba.a = Number(rgb[3]);

            var body = document.getElementsByTagName("body")[0],
                div = document.createElement("div");

            div.innerHTML = this.render();
            div.classList.add("colorpicker-pancel-wrap");
            body.appendChild(div);

            this.elem_wrap = div;
            this.fixedBg = div.children[0];
            this.elem_colorPickerPancel = div.getElementsByClassName("colorpicker-pancel")[0];
            this.total_pancel_width = this.elem_colorPickerPancel.offsetWidth;
            this.total_pancel_height = this.elem_colorPickerPancel.offsetHeight;
            this.elem_colorPancel = div.getElementsByClassName("color-pancel")[0];
            this.pancel_width = this.elem_colorPancel.offsetWidth;
            this.pancel_height = this.elem_colorPancel.offsetHeight;
            this.elem_picker = div.getElementsByClassName("pickerBtn")[0];
            this.elem_showColor = div.getElementsByClassName("colorpicker-showColor")[0];
            this.elem_barPicker1 = div.getElementsByClassName("colorBar-color-picker")[0];
            this.elem_barPicker2 = div.getElementsByClassName("colorBar-opacity-picker")[0];
            this.elem_hexInput = div.getElementsByClassName("colorpicker-hexInput")[0];
            this.elem_showModeBtn = div.getElementsByClassName("colorpicker-showModeBtn")[0];
            this.elem_inputWrap = div.getElementsByClassName("colorpicker-inputWrap")[0];
            this.elem_opacityPancel = this.elem_barPicker2.parentNode.parentNode.children[1];

            // var rect = this.bindElem.getBoundingClientRect();
            var elem = this.bindElem;
            var top = elem.offsetTop;
            var left = elem.offsetLeft;
            /*
            while(elem.offsetParent) {
                top += elem.offsetParent.offsetTop;
                left += elem.offsetParent.offsetLeft;
                elem = elem.offsetParent;
            }
            */

            // 居中
            top = Math.round(document.body.clientHeight / 6);
            left = Math.round(document.body.clientWidth - this.pancel_width);
            // 右下角（输入法会挡住输入框）
            //top = Math.round(document.body.clientHeight - this.total_pancel_height - 50);
            //left = Math.round(document.body.clientWidth - this.total_pancel_width - 20);
            // 下方
            //top = Math.round(document.body.clientHeight - this.total_pancel_height - 50);
            //left = Math.round((document.body.clientWidth - this.pancel_width) / 2);
            //this.bindElem.offsetHeight = 0; // 只读

            this.pancelLeft = left;
            //this.pancelTop = top + this.bindElem.offsetHeight;
            this.pancelTop = top;

            util.css(div, {
                "position": "absolute",
                "z-index": 999999999,
                "display": 'none',
                "left": left + "px",
                //"top": top + this.bindElem.offsetHeight + "px"
                "top": top + "px"
            });

            this.bindMove(this.elem_colorPancel, this.setPosition, true);
            this.bindMove(this.elem_barPicker1.parentNode, this.setBar, false);
            this.bindMove(this.elem_barPicker2.parentNode, this.setBar, false);

            this.bindElem.addEventListener("click", function () {
                _this.show();
            }, false);

            this.fixedBg.addEventListener("click", function (e) {
                _this.hide();
            }, false)

            this.elem_showModeBtn.addEventListener("click", function () {
                _this.switch_current_mode();
            }, false)

            this.elem_wrap.addEventListener("input", function (e) {
                var target = e.target,
                    value = target.value;

                _this.setColorByInput(value);
            }, false)
        },
        setPosition: function (x, y) {
            var LEFT = parseInt(x - this.pancelLeft),
                TOP = parseInt(y - this.pancelTop);

            this.pointLeft = Math.max(0, Math.min(LEFT, this.pancel_width));
            this.pointTop = Math.max(0, Math.min(TOP, this.pancel_height));

            util.css(this.elem_picker, {
                left: this.pointLeft + "px",
                top: this.pointTop + "px"
            })
            this.hsb.s = parseInt(100 * this.pointLeft / this.pancel_width);
            this.hsb.b = parseInt(100 * (this.pancel_height - this.pointTop) / this.pancel_height);

            this.setShowColor();
            this.setValue(this.rgba);

        },
        setBar: function (elem, x) {
            var elem_bar = elem.getElementsByTagName("div")[0],
                rect = elem.getBoundingClientRect(),
                elem_width = elem.offsetWidth,
                X = Math.max(0, Math.min(x - rect.x, elem_width));

            if (elem_bar === this.elem_barPicker1) {
                util.css(elem_bar, {
                    left: X + "px"
                });
                this.hsb.h = parseInt(360 * X / elem_width);
            } else {
                util.css(elem_bar, {
                    left: X + "px"
                });
                this.rgba.a = X / elem_width;
            }

            this.setPancelColor(this.hsb.h);
            this.setShowColor();
            this.setValue(this.rgba);

        },
        setPancelColor: function (h) {
            var rgb = this.HSBToRGB({ h: h, s: 100, b: 100 });

            util.css(this.elem_colorPancel, {
                background: 'rgba(' + rgb.r + ',' + rgb.g + ',' + rgb.b + ',' + this.rgba.a + ')'
            });
        },
        setShowColor: function () {
            var rgb = this.HSBToRGB(this.hsb);

            this.rgba.r = rgb.r;
            this.rgba.g = rgb.g;
            this.rgba.b = rgb.b;

            util.css(this.elem_showColor, {
                background: 'rgba(' + rgb.r + ',' + rgb.g + ',' + rgb.b + ',' + this.rgba.a + ')'
            });

            util.css(this.elem_opacityPancel, {
                background: 'linear-gradient(to right, rgba(' + rgb.r + ',' + rgb.g + ',' + rgb.b + ',0) 0%, rgba(' + rgb.r + ',' + rgb.g + ',' + rgb.b + ',1))'
            });
        },
        setValue: function (value) {
            var hex = value;
            if (typeof hex !== "string" || !hex.startsWith("#")) hex = "#" + this.rgbToHex(value); // 转换会导致误差
            this.elem_inputWrap.innerHTML = this.getInputTpl(hex);
            // this.bindElem.setAttribute("colorpickerOfColor",'#'+hex);
            // util.css(this.bindElem,{
            //     background:"#"+hex
            // })
            Colorpicker.Opt.change(this.bindElem, hex);

        },
        setColorByInput: function (value) {
            if (!util.isColorCode(value)) return;
            var _this = this;
            switch (this.current_mode) {
                case "hex":
                    this.hsb = this.hexToHsb(value);
                    break;
                case 'rgb':
                    var inputs = this.elem_wrap.getElementsByTagName("input"),
                        rgb = {
                            r: inputs[0].value ? parseInt(inputs[0].value) : 0,
                            g: inputs[1].value ? parseInt(inputs[1].value) : 0,
                            b: inputs[2].value ? parseInt(inputs[2].value) : 0
                        };

                    this.hsb = this.rgbToHsb(rgb);
            }

            this.changeViewByHsb(value);
        },
        changeViewByHsb: function (value) {
            this.pointLeft = parseInt(this.hsb.s * this.pancel_width / 100);
            this.pointTop = parseInt((100 - this.hsb.b) * this.pancel_height / 100);
            util.css(this.elem_picker, {
                left: this.pointLeft + "px",
                top: this.pointTop + "px"
            });

            this.setPancelColor(this.hsb.h);
            this.setShowColor();
            util.css(this.elem_barPicker1, {
                left: this.hsb.h / 360 * (this.elem_barPicker1.parentNode.offsetWidth) + "px"
            });

            //var hex = '#'+this.rgbToHex(this.HSBToRGB(this.hsb)); // 转换会导致误差
            var hex = value;
            if (!util.isColorCode(hex)) return;
            Colorpicker.Opt.change(this.bindElem, hex);
            // this.bindElem.setAttribute("colorpickerOfColor",hex);
            // util.css(this.bindElem,{
            //     background:hex
            // })
        },
        switch_current_mode: function () {
            this.current_mode = this.current_mode == 'hex' ? 'rgb' : 'hex';
            this.elem_inputWrap.innerHTML = this.getInputTpl();
        },
        bindMove: function (elem, fn, bool) {
            var _this = this;

            function mousemove(e) {
                if (e.pageX && typeof e.pageX === "number") {
                    _this.moveX = e.pageX;
                    _this.moveY = e.pageY;
                } else if (e.touches && e.touches[0]) {
                    _this.moveX = e.touches[0].pageX;
                    _this.moveY = e.touches[0].pageY;
                } else if (e.changedTouches && e.changedTouches[0]) { // touchend
                    _this.moveX = e.changedTouches[0].pageX;
                    _this.moveY = e.changedTouches[0].pageY;
                }
                bool ? fn.call(_this, _this.moveX, _this.moveY) : fn.call(_this, elem, _this.moveX, _this.moveY);
                e.preventDefault();
            }

            function mouseup(e) {
                document.removeEventListener("mousemove", mousemove, false)
                document.removeEventListener("mouseup", mouseup, false)
            }

            if (os.isPc) elem.addEventListener("mousedown", (e) => {
                _this.downX = e.pageX;
                _this.downY = e.pageY;
                bool ? fn.call(_this, _this.downX, _this.downY) : fn.call(_this, elem, _this.downX, _this.downY);

                document.addEventListener("mousemove", mousemove, false);
                document.addEventListener("mouseup", mouseup, false);
            }, false);

            // 移动端开始触摸事件
            var currTouchPointNum = 0;
            if (!os.isPc) elem.addEventListener('touchstart', (e) => {
                //console.log(e);
                e.preventDefault();
                currTouchPointNum = e.touches.length;
                // 目前只支持单点触碰
                if (currTouchPointNum !== 1) return;

            }, false);

            var lastTouchEnd = 0;
            if (!os.isPc) elem.addEventListener('touchend', (e) => {
                //console.log(e);
                //alert(e.touches.length);
                e.preventDefault();
                //if (e.type !== "touchend" && e.touches.length !== 0) return;
                if (currTouchPointNum !== 1) return;

                let now = (new Date()).getTime();
                if (now - lastTouchEnd <= 300) { // 200~300
                    //alert(">>>> 双击了");
                    //doDbClick(e);
                } else {
                    //alert(">>>> 单击了");
                    //doClick(e);
                    mousemove(e);
                }
                lastTouchEnd = now;
            }, false);

            // 移动端滑动事件
            if (!os.isPc) elem.addEventListener('touchmove', (e) => {
                if (currTouchPointNum !== 1) return;
                mousemove(e);
            }, false);
        },
        show: function () {
            util.css(this.elem_wrap, {
                "display": "block"
            });

            if (util.isColorCode(this.bindElem.value)) {
                let value = util.getFullColorCode(this.bindElem.value);
                this.rgba = this.hexToRgb(value);
                //this.hsb = this.hexToHsb(value); // setColorByInput 方法中有
                // 透明进度条定位
                let p2Left = this.elem_opacityPancel.getBoundingClientRect().left;
                //console.log(p2Left);
                let p2Width = this.elem_opacityPancel.offsetWidth;
                let a = 1, aStr = value.substring(7);
                if (aStr && aStr.length == 2) a = Math.floor(parseInt(aStr, 16) / 255 * 100) / 100;
                let x = p2Left + p2Width * a;
                this.setBar(this.elem_barPicker2.parentNode, x); // setBar 方法内部也会 setValue
                // 设置默认颜色
                this.setColorByInput(value);
                this.setValue(value);
            }

            var hex = "#" + this.rgbToHex(this.rgba);
            Colorpicker.Opt.show(this.bindElem, hex);
        },
        hide: function () {
            util.css(this.elem_wrap, {
                "display": "none"
            });
            var hex = "#" + this.rgbToHex(this.rgba);
            Colorpicker.Opt.hide(this.bindElem, hex);
        },
        HSBToRGB: function (hsb) {
            var rgb = {};
            var h = Math.round(hsb.h);
            var s = Math.round(hsb.s * 255 / 100);
            var v = Math.round(hsb.b * 255 / 100);

            if (s == 0) {
                rgb.r = rgb.g = rgb.b = v;
            } else {
                var t1 = v;
                var t2 = (255 - s) * v / 255;
                var t3 = (t1 - t2) * (h % 60) / 60;

                if (h == 360) h = 0;

                if (h < 60) { rgb.r = t1; rgb.b = t2; rgb.g = t2 + t3 }
                else if (h < 120) { rgb.g = t1; rgb.b = t2; rgb.r = t1 - t3 }
                else if (h < 180) { rgb.g = t1; rgb.r = t2; rgb.b = t2 + t3 }
                else if (h < 240) { rgb.b = t1; rgb.r = t2; rgb.g = t1 - t3 }
                else if (h < 300) { rgb.b = t1; rgb.g = t2; rgb.r = t2 + t3 }
                else if (h < 360) { rgb.r = t1; rgb.g = t2; rgb.b = t1 - t3 }
                else { rgb.r = 0; rgb.g = 0; rgb.b = 0 }
            }

            return { r: Math.round(rgb.r), g: Math.round(rgb.g), b: Math.round(rgb.b) };
        },
        rgbToHex: function (rgb) {
            //debugger;
            var hex = [
                rgb.r.toString(16),
                rgb.g.toString(16),
                rgb.b.toString(16),
                Math.round(255 * (rgb.a !== undefined && rgb.a >= 0 && rgb.a <= 1 ? rgb.a : (this.rgba.a !== undefined && this.rgba.a >= 0 && this.rgba.a <= 1 ? this.rgba.a : 1))).toString(16)
            ];
            hex.map(function (str, i) {
                if (str.length == 1) {
                    hex[i] = '0' + str;
                }
            });

            return hex.join('');
        },
        hexToRgb: function (hex) {
            var a = parseInt(((hex.indexOf('#') > -1 && hex.length == 9) ? hex.substring(7, 9) : "FF"), 16) * (1 / 255);
            var hex = parseInt(((hex.indexOf('#') > -1) ? hex.substring(1, 7) : hex), 16);
            return { r: hex >> 16, g: (hex & 0x00FF00) >> 8, b: (hex & 0x0000FF), a: Number(a.toFixed(2)) };
        },
        hexToHsb: function (hex) {
            return this.rgbToHsb(this.hexToRgb(hex));
        },
        rgbToHsb: function (rgb) {
            var hsb = { h: 0, s: 0, b: 0 };
            var min = Math.min(rgb.r, rgb.g, rgb.b);
            var max = Math.max(rgb.r, rgb.g, rgb.b);
            var delta = max - min;
            hsb.b = max;
            hsb.s = max != 0 ? 255 * delta / max : 0;
            if (hsb.s != 0) {
                if (rgb.r == max) hsb.h = (rgb.g - rgb.b) / delta;
                else if (rgb.g == max) hsb.h = 2 + (rgb.b - rgb.r) / delta;
                else hsb.h = 4 + (rgb.r - rgb.g) / delta;
            } else hsb.h = -1;
            hsb.h *= 60;
            if (hsb.h < 0) hsb.h += 360;
            hsb.s *= 100 / 255;
            hsb.b *= 100 / 255;
            return hsb;
        },
        rgbToStr: function (rgb) {
            let a = (rgb.a !== undefined && rgb.a >= 0 && rgb.a <= 1) ? rgb.a : 1;
            return `rgb(${rgb.r}, ${rgb.g}, ${rgb.b}, ${a})`;
        }
    }

    window.Colorpicker = Colorpicker;
})()


//////////////////////////////////////////////////////////////////////
// 【框架全局】 变量、方法区域
//////////////////////////////////////////////////////////////////////

// TODO 当前应用环境，发布时记得修改。prod-正式环境，不打日志；dev-开发环境；debug-调试环境
//const currActive = window.location.host.includes("m1yellow.cn") ? "prod" : "dev";
const currActive = "dev"; // TODO 下载的离线版不是线上域名，但也是生产环境，不需要打日志

function isProd() {
    if (currActive && currActive.toLowerCase() === "prod" || import.meta.env.PROD) return true;
    return false;
}

// 全局异常捕获
// https://juejin.cn/post/7031876097390149645
var isGlobalErrorCatchAllow = true;
if (isGlobalErrorCatchAllow) {
    /*
    // error 事件监听可以替代这个方法
    window.onerror = function (message, source, lineno, colno, error) {
        console.log("catch error:", {message, source, line, col, error});
        // message: 错误的信息
        // source:  错误发生的文件
        // lineno:  错误发生的行数
        // colno:   错误发生的列数
        // error:   错误对象
    };
    */

    window.addEventListener('error', (e) => {
        //console.log(">>>> error: " + JSON.stringify(e));
        // 阻止事件冒泡和默认行为
        doEventDefault(e);
        doGlobalError(e, (sysConfig && sysConfig.alertErrorCount) ? sysConfig.alertErrorCount : 3);
        return false; // 这样也可以阻止事件冒泡和默认行为
    }, true);

    window.addEventListener('unhandledrejection', (e) => {
        doEventDefault(e);
        doGlobalError(e, (sysConfig && sysConfig.alertErrorCount) ? sysConfig.alertErrorCount : 3);
        return false;
    }, true);

}


// 异常信息处理
function doGlobalErrorMsg(e, isAlert) {
    // 控制台打印
    console.error(e);
    // 打印调用堆栈
    printStack();
    // 错误信息拼接
    let eMsg;
    if (e.stack) eMsg = e.stack;
    if (!eMsg && (e instanceof ErrorEvent)) eMsg = e.message + ", " + e.lineno + ", " + e.colno;
    if (!eMsg) eMsg = e.message;
    if (eMsg && eMsg.includes("手动结束程序")) isAlert = false;
    // 移动端窗口显示
    console.log("⚠️ 程序出现错误: \n" + eMsg);
    // 弹窗提示
    if (isAlert) alert("⚠️ 程序出现错误: \n" + eMsg);
}


// 关闭整个项目console.log的方法
// https://blog.csdn.net/halo1416/article/details/122595285
// console.log 重写
const isDebug = !isProd(); // 控制是否屏蔽全局 console.log 日志；isDebug 设为 false 即可屏蔽
if (isProd()) console.log = (function (oldLogFunc) {
    return function () {
        if (isDebug) {
            oldLogFunc.apply(this, arguments);
        }
    }
})(console.log);


// 移动端显示console.log日志【会导致严重卡顿，仅在排查问题时使用】
// https://blog.csdn.net/ChenX_Web/article/details/99721636
onMounted(() => {
    let isShowInfoConsole = false;
    let infoConsole = document.getElementById('info');
    if (!isShowInfoConsole && infoConsole) infoConsole.style.display = "none";
    if (isShowInfoConsole && infoConsole) {
        if (console) {
            let _console = {
                log: console.log
            }
            console.log = function (attr) {
                _console.log(attr);
                //let str = JSON.stringify(attr, null, 4);
                let str = attr.toString();
                let node = document.createElement("H1");
                let textnode = document.createTextNode(str);

                node.appendChild(textnode);
                infoConsole.appendChild(node);
                // 滚动到底部，显示最新日志
                infoConsole.scrollTop = infoConsole.scrollHeight;
            }
        }

        function show() {
            // 滚动到底部，显示最新日志
            infoConsole.scrollTop = infoConsole.scrollHeight;
            let type = infoConsole.getAttribute("type");
            if (type === "0") { // 收起
                infoConsole.style.cssText = "width:20px;height:20px;";
                infoConsole.setAttribute("type", "1");
                // 清空日志
                if (confirm("是否清空日志记录？")) {
                    console.clear();
                    infoConsole.innerHTML = "";
                } else { }
            } else { // 展开
                infoConsole.removeAttribute('style');
                infoConsole.setAttribute("type", "0");
            }
        }
    }
})


// 打印调用堆栈
function printStack() {
    let stack = (new Error()).stack;
    console.log(stack);
}


// 判断客户端
const os = function () {
    let ua = navigator.userAgent,
        isChrome = /(?:Chrome|CriOS)/.test(ua),
        isFireFox = /(?:Firefox)/.test(ua),
        isWindowsPhone = /(?:Windows Phone)/.test(ua),
        isSymbian = /(?:SymbianOS)/.test(ua) || isWindowsPhone,
        isAndroid = /(?:Android)/.test(ua),
        isIPhone = /(?:iPhone)/.test(ua),
        isTablet = /(?:iPad|PlayBook)/.test(ua) || (isAndroid && !/(?:Mobile)/.test(ua)) || (isFireFox && /(?:Tablet)/.test(ua)),
        isIPadPro = !isIPhone && !isAndroid && !isSymbian && isIpadPro(),
        isPc = !isIPhone && !isAndroid && !isSymbian && !isTablet && !isIPadPro;
    return {
        isTablet: isTablet || isIPadPro,
        isIPhone: isIPhone,
        isAndroid: isAndroid,
        isPc: isPc
    };
}();


// iPad pro UA 有改动，需要特殊判断
// https://blog.csdn.net/Min_Fox/article/details/135225990
function isIpadPro() {
    var ua = window.navigator.userAgent;
    var IsIPad = false;
    if (/ipad/i.test(ua)) {
        IsIPad = true;
    }
    // iPad from IOS13
    var macApp = ua.match(/Macintosh/i) != null;
    if (macApp) {
        // need to distinguish between Macbook and iPad
        var canvas = document.createElement('canvas');
        if (canvas != null) {
            var context = canvas.getContext('webgl') || canvas.getContext('experimental-webgl');
            if (context) {
                var info = context.getExtension('WEBGL_debug_renderer_info');
                if (info) {
                    var renderer = context.getParameter(info.UNMASKED_RENDERER_WEBGL);
                    //console.log(renderer);
                    // TODO 这个判断需要真实设备、或Mac xcode模拟设备验证
                    if (renderer.indexOf('Apple') != -1) IsIPad = true;
                }
            }
        }
    }

    // 多触点判断、屏幕分辨率宽高判断
    IsIPad = isProd() ? (navigator.maxTouchPoints > 1 && window.screen.height > window.screen.width) : (window.screen.height > window.screen.width);

    return IsIPad;
}


// 判断是否为VUE
function isVue() {
    return window.__VUE__ === true || window.app;
}


// 获取设备屏幕像素比，用于解决图形模糊、锯齿问题
// TODO 所有单独设置线宽的地方都要 * dpr，注意，与半径相关参数不用，因为半径已经计算过了
let dpr = window.devicePixelRatio;
dpr = roundNumber(dpr, 4);
console.log(">>>> dpr=" + dpr); // 2/2.7/3


// 设备帧率检测
let fpsCheckLast = Date.now();
let fpsTicks = 0;
let fpsCheckValues = new Array();
let fpsCheckCount = 0;
let fpsCtrlFlag = false; // fps 帧率是否需要控制帧率
let fpsCheckRst = 60; // fps 检测值，默认60
function fpsCheckLoop() {
    fpsTicks += 1;
    // 每30帧统计一次帧率
    if (fpsTicks >= 30) {
        const now = Date.now();
        const diff = now - fpsCheckLast;
        const fps = Math.round(1000 / (diff / fpsTicks));
        fpsCheckLast = now;
        fpsTicks = 0;
        fpsCheckValues[fpsCheckCount] = fps;
        fpsCheckCount += 1;
        //console.log(">>>> fps" + fpsCheckCount + ":" + fps);
        if (fpsCheckCount >= 3) {
            fpsCheckCount = 0;
            let minVal = 50;
            let maxVal = 70;
            if (fpsCheckValues[0] < minVal && fpsCheckValues[1] < minVal && fpsCheckValues[2] < minVal) alert("⚠️ 当前手机帧率低于60帧，游戏不能正常运作！");
            // TODO 不用限制帧率的方式，改用调整摩檫力比例的方式
            if (fpsCheckValues[0] > maxVal || fpsCheckValues[1] > maxVal || fpsCheckValues[2] > maxVal) fpsCtrlFlag = true;
            fpsCheckRst = fpsCheckValues[2];
            console.log(">>>> fps=" + fpsCheckRst);
            // 重新计算一遍速度和摩檫力
            //setSpeed();
            //setFriction();
            //alert(">>>> fps=" + fpsCheckRst);
            //alert(">>>> friction=" + sysConfig.friction);
            return;
        }
    }
    requestAnimationFrame(fpsCheckLoop);
}
fpsCheckLoop();


// 获取鼠标移动点坐标
let mouse = null; // 放在设置画布位置后再初始化赋值
let screenPos = { x: 0, y: 0 }; // 屏幕可见坐标，不算dpr
function captureMouse(element) {
    mouse = { // 
        x: 0,
        y: 0,
        event: null
    };
    let body_scrollLeft = document.body.scrollLeft;
    let element_scrollLeft = document.documentElement.scrollLeft;
    let body_scrollTop = document.body.scrollTop;
    let element_scrollTop = document.documentElement.scrollTop;
    let offsetLeft = element.offsetLeft;
    let offsetTop = element.offsetTop;
    console.log(">>>> captureMouse offsetLeft:" + offsetLeft + ", offsetTop:" + offsetTop);

    if (os.isPc) { // PC端
        //element.addEventListener('mousedown', (e) => {
        element.addEventListener('mousemove', (e) => {
            let x, y;
            if (e.pageX || e.pageY) { // 页面左上角为原点
                x = e.pageX;
                y = e.pageY;
            } else { // 可视窗口的左上角
                x = e.clientX + body_scrollLeft + element_scrollLeft;
                y = e.clientY + body_scrollTop + element_scrollTop;
            }

            screenPos.x = x;
            screenPos.y = y;

            x -= offsetLeft;
            y -= offsetTop;

            mouse.x = x * dpr;
            mouse.y = y * dpr;
            //console.log(">>>> mouse.x=" + mouse.x + ", mouse.y=" + mouse.y);
            mouse.event = e;
        }, false);

    } else { // 移动端
        //element.addEventListener('touchstart', (e) => {
        element.addEventListener('touchmove', (e) => {
            let x, y;

            x = e.touches[0].pageX;
            y = e.touches[0].pageY;

            screenPos.x = x;
            screenPos.y = y;

            x -= offsetLeft;
            y -= offsetTop;

            mouse.x = x * dpr;
            mouse.y = y * dpr;
            mouse.event = e;
        }, false);
    }

    mouse.x = roundNumber(mouse.x, 4);
    mouse.y = roundNumber(mouse.y, 4);
    return mouse;
};


// 获取鼠标点击坐标
let clickPos = null;
function getClickPos(e) {
    // 只显示台面，不处理点击事件
    if (userConfig.isJustShowTable) return;
    if (!e) return;
    //if (!e || e.type === "touchend") return;
    //console.log(e);
    //console.log(e.target);
    let element = e.target;
    let offsetLeft = element.offsetLeft;
    let offsetTop = element.offsetTop;
    //console.log(">>>> getClickPos offsetLeft:" + offsetLeft + ", offsetTop:" + offsetTop);
    clickPos = { x: 0, y: 0 };
    let x = 0, y = 0;
    if (e.pageX && typeof e.pageX === "number") {
        x = e.pageX;
        y = e.pageY;
    } else if (e.touches && e.touches[0]) {
        x = e.touches[0].pageX;
        y = e.touches[0].pageY;
    } else if (e.changedTouches && e.changedTouches[0]) { // touchend
        x = e.changedTouches[0].pageX;
        y = e.changedTouches[0].pageY;
    }
    x -= offsetLeft;
    y -= offsetTop;
    clickPos.x = x * dpr;
    clickPos.y = y * dpr;
    clickPos.x = roundNumber(clickPos.x, 4);
    clickPos.y = roundNumber(clickPos.y, 4);
    mouse.x = clickPos.x;
    mouse.y = clickPos.y;
    console.log(">>>> getClickPos clickPos.x=" + clickPos.x + ", clickPos.y=" + clickPos.y);
    return clickPos;
}


// 旋转坐标系
function rotate(x, y, sin, cos, reverse) {
    return {
        x: (reverse) ? (x * cos + y * sin) : (x * cos - y * sin),
        y: (reverse) ? (y * cos - x * sin) : (y * cos + x * sin)
    };
}


// 监听页面大小变化，重新调整画布及小球大小
function resetCanvasSize() {
    // dpr 没变不刷新
    if (roundNumber(window.devicePixelRatio, 4) === dpr) return;
    // 直接刷新一次页面就好
    location.reload();
    /*会存在很多历史变量影响，balls、lines、linesMiddlePoints 等数组变量要清空
    // 重新初始化
    init();
    // 渲染完成标识false
    isAnimated = false;
    // 清空一次画布
    context.clearRect(0, 0, canvas.width, canvas.height); // 清理不干净
    context.beginPath(); // 开启新path，避免清理不干净
    // 重新渲染
    if (!isPlaying) animate();
    */
}
window.addEventListener('resize', resetCanvasSize); // 对同一个元素的同一个事件重复添加监听函数，只会生效一次


// 检测是否可以使用，浏览器支持，以及浏览器隐私设置允许
function checkWebStorage() {
    let result = false;

    if (window.localStorage) {
        try {
            localStorage.setItem('collide-try-role-chose-test', 1);
            let testVal = localStorage.getItem('collide-try-role-chose-test');
            localStorage.removeItem('collide-try-role-chose-test');
            if (!testVal) throw new Error(">>>> 当前浏览器支持 localStorage，但使用异常，请检查是否开启了【无痕模式】");
            result = true;
        } catch (e) {
            alert(e.message);
        }
    } else {
        alert(">>>> 当前浏览器不支持 localStorage，请检查是否开启了【无痕模式】，或升级浏览器版本，或更换其他浏览器");
    }

    if (result) return result;

    /*
    if (window.sessionStorage) {
        try {
            sessionStorage.setItem('collide-try-role-chose-test', 1);
            let testVal = sessionStorage.getItem('collide-try-role-chose-test');
            sessionStorage.removeItem('collide-try-role-chose-test');
            if (!testVal) throw new Error(">>>> 当前浏览器支持 sessionStorage，但使用异常，请检查隐私设置是否过于严格");
            result = true;
        } catch (e) {
            alert(e.message);
        }
    } else {
        alert(">>>> 当前浏览器不支持 sessionStorage，请升级浏览器版本，或者更换其他浏览器");
    }
    */

    return result;
}


// 使用 IndexedDB 数据库 存储图片
// https://www.cnblogs.com/zhang-zi-yi/p/12703656.html
var indexedDB = window.indexedDB || window.webkitIndexedDB || window.mozIndexedDB || window.OIndexedDB || window.msIndexedDB,
    IDBTransaction = window.IDBTransaction || window.webkitIDBTransaction || window.OIDBTransaction || window.msIDBTransaction,
    dbVersion = 3, // 版本 The requested version (2) is less than the existing version (3).
    //idbOpenReq, // 打开数据请求
    IDB, // IndexedDB 连接对象
    dbName = "collide-try", // 要使用的数据库
    tbName = "images"; // 要使用的数据库表

if (!indexedDB) {
    console.log(">>>> 浏览器不支持 IndexedDB V" + dbVersion);
} else {
    openIndexedDB();
}

// 打开数据库
function openIndexedDB() {
    // 打开数据库，不存在会自动先创建
    let idbOpenReq = indexedDB.open(dbName, dbVersion);
    // 数据库打开成功
    idbOpenReq.onsuccess = function (event) {
        IDB = idbOpenReq.result;
        doIndexedDBOpenSuccess();
        IDB.onerror = function (e) {
            console.log(">>>> IndexedDB 连接错误：" + e.currentTarget.error.message);
        }
    }

    // 数据库打开失败
    idbOpenReq.onerror = function (e) {
        console.log(">>>> IndexedDB 打开错误：" + e.currentTarget.error.message);
    }

    // 在数据库创建或者版本更新时，会触发onupgradeneeded事件
    idbOpenReq.onupgradeneeded = function (e) {
        IDB = e.target.result;
        if (!IDB.objectStoreNames.contains(tbName)) {
            // 如果表格不存在，创建一个新的表格
            // （keyPath，主键 ； autoIncrement,是否自增），会返回一个对象（objectStore）
            let objectStore = IDB.createObjectStore(tbName); // , { keyPath: 'id', autoIncrement: true }
            // 指定可以被索引的字段，unique字段是否唯一
            // objectStore.createIndex('fileName', 'name', { unique: false });
        }
    }
}

// 处理 IndexedDB 打开成功事项
function doIndexedDBOpenSuccess() {
    // 从IndexedDB读取图片，并设置body图片背景
    if (sysConfig.isRoleChooseFinished)
        doPageBgImage(currTheme.bgImage, true);
}

// 处理 IndexedDB 打开失败事项
function doIndexedDBOpenError() {
    // TODO 
}

// indexedDB 对象 IDB 是否初始化加载完成
function checkIDBReady() {
    if (!IDB) return false;
    if (!IDB.name || !IDB.name.toLocaleLowerCase().startsWith(dbName)) return false;
    return true;
}

// 将 blob 对象存储到数据库中
function putImageInDb(blob, key) {
    let transaction = getNewTransaction();
    if (!transaction) return;
    let put = transaction.objectStore(tbName).put(blob, key);
}

// 获取图片文件
function getImageRequest(key) {
    let transaction = getNewTransaction();
    if (!transaction) return;
    transaction.objectStore(tbName).get(key).onsuccess = (event) => {
        // 异步回调
        let blob = event.target.result;
        if (blob) {
            let url = window.URL.createObjectURL(blob);
            //$('.img').attr('src', url);
        }
    }
}

// 获取一个新的数据库操作事务
function getNewTransaction() {
    if (!checkIDBReady()) {
        console.log(">>>> IndexedDB 数据库连接对象暂未初始化完成");
        return null;
    }
    return IDB.transaction([tbName], 'readwrite');
}

// 清空 indexedDB 表数据存储
function clearTable(tbName) {
    const transaction = IDB.transaction(tbName, 'readwrite');
    const objectStore = transaction.objectStore(tbName);
    const clearRequest = objectStore.clear();
    clearRequest.onsuccess = () => {
        console.log(">>>> " + tbName + " 表数据清空完成");
    }
    clearRequest.onerror = (event) => {
        console.log(">>>> " + tbName + " 表数据清空出错：" + event.target.error);
    }
}


// JS 检测当前环境是否处于深色模式
// https://juejin.cn/post/7080567228029992996
var isLightMode = true;
var isDarkMode = false;
try {
    isLightMode = window.matchMedia('(prefers-color-scheme: light)').matches;
    isDarkMode = window.matchMedia('(prefers-color-scheme: dark)').matches;
} catch (e) {
    doGlobalErrorMsg(e, false);
}
console.log(">>>> isLightMode=" + isLightMode);
console.log(">>>> isDarkMode=" + isDarkMode);


// 监听返回
// popstate 方案，必须手动点一下页面任何地方，才会触发！
// chrome 为了防止流氓网站禁止用户执行回退操作，把用户困在当前网站，专门做的这个设计！
onMounted(() => {
    pushHistory();
    window.addEventListener("popstate", function (e) { // 后退、前进都会触发
        //console.log(e);
        e.preventDefault();
        //alert("我监听到了浏览器的返回按钮事件啦"); // 根据自己的需求实现自己的功能
        pushHistory();
        // 处理返回事项
        doBack();
    }, false);
});

function pushHistory() {
    //let ts = new Date().getTime().toString();
    /*
    var state = {
        title: "title",
        url: "#"
    };
    window.history.pushState(state, "title", "#");
    */
    //window.history.pushState(null, null, "#");
    history.pushState(null, null, document.URL);
}
var backClickCount = 0;
var backClickTimer = 0;
function doBack(isMaskIn) {
    // 弹窗遮罩
    let isDialogMaskShowing = isDialogShowing(dialogMask);
    // 选择角色弹窗
    let isChooseRoleDialogShowing = isDialogShowing(chooseRoleDialog);
    // 游戏设置弹窗
    let isUserSettingDialogShowing = isDialogShowing(userSettingDialog);
    // 关于应用弹窗
    let isAboutAppDialogShowing = isDialogShowing(aboutAppDialog);
    // 更新提示弹窗
    let isUpdateContentDialogShowing = isDialogShowing(updateContentDialog);
    // 操作指南弹窗
    let isHowToPlayDialogShowing = isDialogShowing(howToPlayDialog);

    // 关闭更新提示弹窗
    if (!isMaskIn && isUpdateContentDialogShowing) {
        showUpdateContent(false);
        return;
    }

    // 关闭操作指南弹窗
    if (!isMaskIn && isHowToPlayDialogShowing) {
        showHowToPlay(false);
        return;
    }

    // 关闭关于应用弹窗
    if (isAboutAppDialogShowing) {
        switchDialogShow(aboutAppDialog, false);
        return;
    }

    // 关闭游戏设置弹窗
    if (isUserSettingDialogShowing) {
        switchUserSettingDialog(false);
        return;
    }

    // 关闭选择角色弹窗
    if (isChooseRoleDialogShowing) {
        switchChooseRoleDialog(false);
        return;
    }

    if (isMaskIn) return;

    // 游戏正在进行
    if (checkIsMoving()) {
        //alert("👉 游戏正在进行，不建议返回哦~");
        return;
    } else {
        if (!backClickTimer) backClickTimer = setTimeout(() => {
            backClickCount = 0;
            backClickTimer && clearTimeout(backClickTimer);
            backClickTimer = 0;
        }, 3000);
        backClickCount += 1;
        if (backClickCount > 2) {
            alert("👉 点击左上角重选角色，关掉页面退出游戏");
            backClickCount = 0;
        }
    }

    /*
    // 退出游戏
    if (!isChooseRoleDialogShowing) { // 游戏界面
        window.history.go(0); // 回到起始界面
        return;
    } else { // 选择角色界面
        //window.history.go(0); // 回到起始界面
        window.history.forward(1); // 点后退又前进，相当于没动，达到屏蔽后退按钮的效果
        return;
        if (confirm("💡 确定要离开游戏了吗？")) { // 确认
            window.opener = null;
            window.open('', '_self');
            // Scripts may close only the windows that were opened by them.
            // window.close()方法只能关闭由window.open()或者浏览器直接输入url打开的页面，其余情况安全考虑是被限制的
            window.close(); // js关不了，需要按钮点击调用
        } else { // 取消
            // ignore
        }
        return;
    }
    */
}


// window 全局点击空白事项处理
window.onclick = function (e) {
    doEventDefault(e); // 处理事件默认行为，防止出现点一次，执行两次
    // 点击了主题设置下拉框以外的区域
    if (!e.target.matches('.dropbtn')) {
        let themeDropdown = document.getElementById("themeDropdown");
        if (themeDropdown.classList.contains('show')) {
            themeDropdown.classList.remove('show');
        }
    }
}


// 浏览器窗口关闭或者刷新时【一定要在关闭页面前移除所有监听事件？页面关闭自动处理了啊】
// 会导致重新加载一直提示 “系统可能不会保存您所做的更改”
/*
window.addEventListener("beforeunload", (event) => {
    // Cancel the event as stated by the standard.
    event.preventDefault();
    // Chrome requires returnValue to be set.
    event.returnValue = "";
});
*/


/*
// 监听浏览器切换页面。判断用户浏览的是否为当前页，根据当前页面激活状态，进行业务处理
// Document：hidden 属性
var hiddenProperty = 'hidden' in document ? 'hidden' :
'webkitHidden' in document ? 'webkitHidden' :
'mozHidden' in document ? 'mozHidden' :
null;
var visibilityChangeEvent = hiddenProperty.replace(/hidden/i, 'visibilitychange');
var onVisibilityChange = function() {
    if (document[hiddenProperty]) { // hidden===true 非激活
        console.log('页面非激活');
    } else {
        console.log('页面激活')
    }
}
document.addEventListener(visibilityChangeEvent, onVisibilityChange);
*/


// 获取正常展示 Emoji 时的宽度
// https://cloud.tencent.com/developer/article/2211194
const getTextWidth = (text) => {
    const element = document.createElement('span');
    element.setAttribute('aria-hidden', 'true');
    element.setAttribute('style', 'font-size:16px!important;position:absolute;top:0;opacity:0;font-family:Consolas,"Liberation Mono","Courier New",monospace');
    element.textContent = text;
    document.body.appendChild(element);
    const width = element.clientWidth;
    document.body.removeChild(element);
    return width;
}

// icon 兼容旧机型
//const iconWidth = getTextWidth(Role.getRoleIconById(Role.SHUANGZI.id));
const iconWidth = getTextWidth("🧍‍♂️");
//const iconWidth = getTextWidth("🏃‍♂️‍➡️");
console.log(">>>> iconWidth=" + iconWidth);

// 检验 Emoji 能否被正常展示
const isEmojiValid = (emoji) => {
    return getTextWidth(emoji) === iconWidth && iconWidth >= 14;
}

// 双子分身图标是否能正常显示
//const isTwinSingleIconShow = isEmojiValid("🧍") && isEmojiValid("🧍‍♂️"); // TODO let const 定义的变量，在定义之前不能访问
var isTwinSingleIconShow = isEmojiValid("🧍") && isEmojiValid("🧍‍♂️"); // var 可以全局访问到为初始化的变量（只有默认值），不受定义位置限制
var isTwinLeftIconShow = isEmojiValid("🏃");
var isTwinRightIconShow = isEmojiValid("🏃‍♂️‍➡️");
console.log(">>>> isTwinSingleIconShow=" + isTwinSingleIconShow);
//console.log(">>>> twinSingleIconWidth=" + getTextWidth("🧍"));
//console.log(">>>> twinSingleIconWidth=" + getTextWidth("🧍‍♂️"));
//console.log(">>>> twinSingleIconWidth=" + getTextWidth("🏃‍♂️‍➡️"));

// 田园主题-木头图标是否能正常显示
var isWoodIconShow = getTextWidth("🪵") >= 14;
console.log(">>>> isWoodIconShow=" + isWoodIconShow);

// 默认主题-石头图标是否能正常显示
var isRockIconShow = getTextWidth("🪨") >= 14;
console.log(">>>> isRockIconShow=" + isRockIconShow);

// 星际主题-土星图标是否能正常显示
var isRingedIconShow = getTextWidth("🪐") >= 14;
console.log(">>>> isRingedIconShow=" + isRingedIconShow);


//////////////////////////////////////////////////////////////////////


//////////////////////////////////////////////////////////////////////
// 【加密解密】 变量、方法区域
//////////////////////////////////////////////////////////////////////

// 核心方法解密，动态添加
function addCoreScript(eles, eleId, eleClass, content, targetId) {
    if (eles && eles instanceof HTMLCollection) {
        for (let i = 0, len = eles.length; i < len; i++) {
            //document.head.appendChild(eles[i]);
            document.body.appendChild(eles[i]);
        }
        if (!content) return true;
    }
    if (!content) return false;
    let enScript = document.getElementById(eleId);
    if (!enScript) enScript = document.createElement('script');
    enScript.type = 'text/javascript';
    if (eleId) enScript.setAttribute('id', eleId);
    if (eleClass) enScript.setAttribute('class', eleClass);
    enScript.textContent = content;
    let targetEle = document.getElementById(targetId);
    if (targetEle) targetEle.appendChild(enScript);
    //document.head.appendChild(enScript);
    else document.body.appendChild(enScript);
    return true;
}

onMounted(() => {
    //addCoreScript(null, "test-balls", null, "alert(balls.length)", "app-main");
})

// 移除核心方法[狗头]
// 移除 script 标签，不会影响已经加载进内存的 script
function removeCoreScript(eles, eleIdOrClass) {
    if (eles && eles instanceof HTMLCollection) {
        for (let i = 0, len = eles.length; i < len; i++) {
            eles[i].remove(); // 都会把元素从 eles 中移除
            //document.body.removeChild(eles[i]);
        }
        if (!eleIdOrClass) return true;
    }
    if (!eleIdOrClass) return false;
    let ele = document.getElementById(eleIdOrClass);
    if (!ele) ele = document.getElementsByClassName(eleIdOrClass);
    if (!ele) return false;
    //console.log(ele);
    if (ele instanceof HTMLCollection) {
        for (let i = 0, len = ele.length; i < len; i++) {
            ele[i].remove();
            //document.body.removeChild(ele[i]);
        }
        return true;
    } else {
        ele.remove();
        return true;
    }
    return false;
}


let accessKey = "";
let superKey = "";
let easyKey = "";
let accessMsg = "";
let codeStr = "";
let encodeStr = "iwCkbEe4umgXW8Z8XMxbCkBZYXCUpgJlRaxhZtRQ4cG09pa5tlsKs0jzY+7WLIkaR2JN8tAKX2TpSsDN1YudYqqVasY6kZYG7ywzls7LJEabMBIwPz/O2FlyH1VxamwMxyZHXYGLS/EF2wtiwyUv+npl63pZi4mUNBAwFMy7T5rwiJtiM5guQ/SaK7/3W37A+F46Q0cIKkPfd8ZKs9D7WjfXdfEtiPNCB80QqzvwfOgTSQ0uveMamdpx4lEYcUiEgiWHy0n54lnakg/jj8JLcYqesjAC8GM972q5ZUeV5NZnJ7Q/xRtdOSaFrcDJlXdjyVI11Zrf/nELZDMGTIiC8oGclsYVe7nchj+8lX6NKXrYPlZu1XHze7bW1O6FwZRdNrwL4NbahskjroQlC4Q9FD3e1CPO4v0v7J5zxPkjXxU6cWQ+dB5gLIv3732UyDZj25NBlhmvKzuU82yfB+GInhntvGAjtWdXy2ZsswQvVrhr09sAF5PPycRtQlp1L0oY4TK0BAY7HnYvORPVEcWg1FhPRN1TckMFN7rqTjgUQmps5oZjdoBUCW7V3kpq85FZT8cJFTXPo7EBQu3Oow+CExuGuGJ510QcGVNJshihxUJXFW5zruGYOU8ahqo0+HqpuHTx2j0Emx0=";
let superKeyEnStr = "PQJ2F4bEvWjpdc6Yw2U3jioK4lk/IaWec5Jyy89UeoCGHtii0ljX6A==";
let easyKeyEnStr = "jgCXJUe4umhO7FyajvDhdPi+6mrNKa1/GIUz6wtrBxS3YjtaHGlzEw==";
if (accessKey && codeStr) {
    encodeStr = Aes.Ctr.encrypt(codeStr, accessKey, 256);
    console.log('>>>> encodeStr=', encodeStr);
}
if (accessKey && superKey) {
    superKeyEnStr = Aes.Ctr.encrypt(accessKey, superKey, 256);
    console.log('>>>> superKeyEnStr=', superKeyEnStr);
}
if (accessKey && easyKey) {
    easyKeyEnStr = Aes.Ctr.encrypt(accessKey, easyKey, 256);
    console.log('>>>> easyKeyEnStr=', easyKeyEnStr);
}
// TODO 更新访问密钥之后，还需要更改 nginx 下载链接中的密钥

// 检测核心代码和密钥
function checkCoreCode(method, isDialog) {

    // 本地版本不检测
    if (isLocalVersion()) return true;

    // 调用方法名称校验
    if (!method || typeof method !== 'string' || method.length > 50) return false;

    // 参数默认值
    accessMsg = "🔑 请输入访问密钥";

    for (let i = 0, len = 100; i < len; i++) {
        // 先从 localStorage 获取 accessKey
        accessKey = localStorage.getItem('collide-try-access-key');
        // 退游了，公开访问
        //accessKey = "Pg24fzRl02a45odGEvKsFqL0MHmykigF";

        if (isDialog) {
            // 没找到，再弹窗提示输入【访问密钥】
            // 单击取消按钮，prompt() 方法将返回 null，单击确认按钮，prompt() 将返回输入的文本，弹窗时会暂停 JavaScript 执行
            if (!accessKey) accessKey = prompt(accessMsg, "询问作者或关注作者玩吧动态");
            //console.log(">>>> accessKey=" + accessKey);
            if (accessKey === null) { // 点了取消
                alert("💡 温馨提示：\n没有访问密钥，核心功能会受到影响！请联系开发者获取访问密钥");
                return false;
            }
            if (!accessKey || accessKey.replaceAll(" ", "") === "") {
                accessMsg = "❌ 访问密钥不能为空";
                continue;
            }
            if (accessKey.length < 8 || accessKey.length > 128) {
                accessMsg = "❌ 访问密钥长度错误";
                continue;
            }
        }

        if (!accessKey) {
            console.log(">>>> checkCoreCode accessKey empty");
            return false;
        }

        try {
            //encodeStr = Aes.Ctr.encrypt(codeStr, accessKey, 256);
            //console.log(encodeStr);
            if (accessKey.toLowerCase().includes("thelight")) accessKey = Aes.Ctr.decrypt(superKeyEnStr, accessKey, 256); // superKey
            else if (accessKey.length < 32) accessKey = Aes.Ctr.decrypt(easyKeyEnStr, accessKey, 256); // easyKey
            //console.log(">>>> accessKey=" + accessKey);
            codeStr = Aes.Ctr.decrypt(encodeStr, accessKey, 256);
            //console.log(codeStr); // 密钥不对，返回是乱码 QªÑg=[JLäój´qÀ76

            // 动态添加 do2BallsCollidedMV2 方法
            if (codeStr && codeStr.includes(method)) addCoreScript(null, method, 'collide-try-core-code', codeStr);
            else throw new Error(">>>> Decrypt failed. Please check your accessKey!");
            // 尝试调用验证
            //do2BallsCollidedMV2();
            Function('return ' + method + '()')(); // TODO Function 函数作用域访问不到 vue 内部模板，但是能访问到全局 script
            // 调用不报错，把 accessKey 存入 localStorage
            localStorage.setItem('collide-try-access-key', accessKey);
            codeStr = null; // 释放字符串内存
            encodeStr = null;
            superKeyEnStr = null;
            //break;
            return true;
        } catch (e) {
            accessMsg = "❌ 访问密钥错误";
            //doGlobalError(e, (sysConfig && sysConfig.alertErrorCount)?sysConfig.alertErrorCount:3);
            doGlobalErrorMsg(e, false);
            //localStorage.removeItem('collide-try-access-key');
            // 处理密钥校验不通过
            doKeyCheckFail();
        }
    }
    return false;
}

// 页面元素、脚本、文件加载完成之后再执行，避免获取不到元素
window.onload = function () {
    let keyCkeckResult = checkCoreCode("do2BallsCollidedMV2", false);
    if (!keyCkeckResult) {
        // 处理密钥校验不通过
        doKeyCheckFail();
    }
}


// 密钥校验不通过处理事项
function doKeyCheckFail() {
    // 密钥校验不通过，清除用户已选的角色记录，重新弹出选择角色弹窗
    localStorage.removeItem('collide-try-access-key');
    localStorage.removeItem('collide-try-role-chose');
    //userConfig.currRole = -1;
    setCurrRoleV2();
}


// 检测输入的访问密钥是否正确
function checkAccessKey() {

    // 本地版本不检测
    if (isLocalVersion()) return true;

    let result = false;
    // 校验是否输入了密钥
    accessKey = localStorage.getItem('collide-try-access-key');
    if (!accessKey || accessKey.replaceAll(' ', '') === '') return false;

    // 校验密钥是否正确，解密方法是否能正常访问
    // checkCoreCode 已经解密了一次，这里不再重复解密
    try {
        // 尝试调用验证
        do2BallsCollidedMV2();
        result = true;
    } catch (e) {
        //doGlobalErrorMsg(e, false);
    }

    return result;

    // 这个检测方法直接改为返回true，就破解绕过了
    //return true;
}


// 是否为离线版本
function isLocalVersion() {
    let result = false;
    // 获取核心脚本元素
    let coreJsEles = document.getElementsByClassName("collide-try-core-code");
    if (!coreJsEles || coreJsEles.length < 1) return false;
    //console.log(coreJsEles);
    // 尝试访问核心方法
    try {
        do2BallsCollidedMV2();
        result = true;
    } catch (e) {
        //doGlobalErrorMsg(e, false);
    }

    return result;
}


//////////////////////////////////////////////////////////////////////


//////////////////////////////////////////////////////////////////////
// 【主程序】 变量、方法区域
//////////////////////////////////////////////////////////////////////

// 获取画布
let gameSceneGraphCanvas = document.getElementById('game-scene-graph'); // 静态场景大面积区域景物图形层画布
let gameSceneEmojiCanvas = document.getElementById('game-scene-emoji'); // 静态场景景物图形层画布
let gameSceneCanvas = document.getElementById('game-scene'); // 静态场景层画布
let gameSceneLinesCanvas = document.getElementById('game-scene-lines'); // 静态场景边框层画布
let gameSceneLinesBgCanvas = document.getElementById('game-scene-lines-bg'); // 静态场景边框背景层画布
let gameSceneCoordinateCanvas = document.getElementById('game-scene-coordinate'); // 静态场景砖格坐标布
let canvas = document.getElementById('game-main'); // 主运动层画布
let gameMainBallCanvas = document.getElementById('game-main-ball'); // 主球运动层画布，主球和其他球分开
let gamePathCanvas = document.getElementById('game-path'); // 角色中线路径层画布（一条细线）
let gamePathBallCanvas = document.getElementById('game-path-ball'); // 角色全路径层画布（路径线宽为角色直径）
let gameClickPlayCanvas = document.getElementById('game-click-play'); // 点按发射按钮层
let gameMaskCanvas = document.getElementById('game-mask'); // 遮罩层画布
// 获取上下文
let gameSceneGraphContext = gameSceneGraphCanvas ? gameSceneGraphCanvas.getContext('2d') : null;
let gameSceneEmojiContext = gameSceneEmojiCanvas ? gameSceneEmojiCanvas.getContext('2d') : null;
let gameSceneContext = gameSceneCanvas ? gameSceneCanvas.getContext('2d') : null;
let gameSceneLinesContext = gameSceneLinesCanvas ? gameSceneLinesCanvas.getContext('2d') : null;
let gameSceneLinesBgContext = gameSceneLinesBgCanvas ? gameSceneLinesBgCanvas.getContext('2d') : null;
let gameSceneCoordinateContext = gameSceneCoordinateCanvas ? gameSceneCoordinateCanvas.getContext('2d') : null;
let context = canvas ? canvas.getContext('2d') : null;
let gameMainBallContext = gameMainBallCanvas ? gameMainBallCanvas.getContext('2d') : null;
let gamePathContext = gamePathCanvas ? gamePathCanvas.getContext('2d') : null;
let gamePathBallContext = gamePathBallCanvas ? gamePathBallCanvas.getContext('2d') : null;
let gameClickPlayContext = gameClickPlayCanvas ? gameClickPlayCanvas.getContext('2d') : null;
let gameMaskContext = gameMaskCanvas ? gameMaskCanvas.getContext('2d') : null;
// 弹窗元素
let dialogMask = document.getElementById('dialog-mask'); // 选择角色弹窗遮罩
let chooseRoleDialog = document.getElementById('choose-role-dialog'); // 选择角色弹窗
let userSettingDialog = document.getElementById('user-setting-dialog'); // 参数设置弹窗
let reChooseRoleEntryDialog = document.getElementById('re-choose-role-entry-dialog'); // 重新选择角色入口提示
let gameSettingEntryDialog = document.getElementById('game-setting-entry-dialog'); // 游戏设置提示
let gameSettingMainRoleDialog = document.getElementById('game-setting-main-role-dialog'); // 游戏设置-主角设置提示
let aboutAppDialog = document.getElementById('user-setting-about-app-dialog'); // 参数设置-关于应用
let updateContentDialog = document.getElementById('collide-try-update-content-dialog'); // 更新内容提示
let howToPlayDialog = document.getElementById('collide-try-how-to-play-dialog'); // 操作指南提示
let rolePosLine = document.getElementById('collide-try-role-pos-line'); // 角色坐标悬浮条

onMounted(() => {
    gameSceneGraphCanvas = document.getElementById('game-scene-graph'); // 静态场景大面积区域景物图形层画布
    gameSceneEmojiCanvas = document.getElementById('game-scene-emoji'); // 静态场景景物图形层画布
    gameSceneCanvas = document.getElementById('game-scene'); // 静态场景层画布
    gameSceneLinesCanvas = document.getElementById('game-scene-lines'); // 静态场景边框层画布
    gameSceneLinesBgCanvas = document.getElementById('game-scene-lines-bg'); // 静态场景边框背景层画布
    gameSceneCoordinateCanvas = document.getElementById('game-scene-coordinate'); // 静态场景砖格坐标布
    canvas = document.getElementById('game-main'); // 主运动层画布
    gameMainBallCanvas = document.getElementById('game-main-ball'); // 主球运动层画布，主球和其他球分开
    gamePathCanvas = document.getElementById('game-path'); // 角色中线路径层画布（一条细线）
    gamePathBallCanvas = document.getElementById('game-path-ball'); // 角色全路径层画布（路径线宽为角色直径）
    gameClickPlayCanvas = document.getElementById('game-click-play'); // 点按发射按钮层
    gameMaskCanvas = document.getElementById('game-mask'); // 遮罩层画布

    gameSceneGraphContext = gameSceneGraphCanvas.getContext('2d');
    gameSceneEmojiContext = gameSceneEmojiCanvas.getContext('2d');
    gameSceneContext = gameSceneCanvas.getContext('2d');
    gameSceneLinesContext = gameSceneLinesCanvas.getContext('2d');
    gameSceneLinesBgContext = gameSceneLinesBgCanvas.getContext('2d');
    gameSceneCoordinateContext = gameSceneCoordinateCanvas.getContext('2d');
    context = canvas.getContext('2d');
    gameMainBallContext = gameMainBallCanvas.getContext('2d');
    gamePathContext = gamePathCanvas.getContext('2d');
    gamePathBallContext = gamePathBallCanvas.getContext('2d');
    gameClickPlayContext = gameClickPlayCanvas.getContext('2d');
    gameMaskContext = gameMaskCanvas.getContext('2d');

    dialogMask = document.getElementById('dialog-mask'); // 选择角色弹窗遮罩
    chooseRoleDialog = document.getElementById('choose-role-dialog'); // 选择角色弹窗
    userSettingDialog = document.getElementById('user-setting-dialog'); // 参数设置弹窗
    reChooseRoleEntryDialog = document.getElementById('re-choose-role-entry-dialog'); // 重新选择角色入口提示
    gameSettingEntryDialog = document.getElementById('game-setting-entry-dialog'); // 游戏设置提示
    gameSettingMainRoleDialog = document.getElementById('game-setting-main-role-dialog'); // 游戏设置-主角设置提示
    aboutAppDialog = document.getElementById('user-setting-about-app-dialog'); // 参数设置-关于应用
    updateContentDialog = document.getElementById('collide-try-update-content-dialog'); // 更新内容提示
    howToPlayDialog = document.getElementById('collide-try-how-to-play-dialog'); // 操作指南提示
    rolePosLine = document.getElementById('collide-try-role-pos-line'); // 角色坐标悬浮条
})

////////////////////////////////////////////////
// 系统参数配置
////////////////////////////////////////////////
var sysConfig = {
    // 应用名称
    appName: "玩吧-撞击王者-模拟练习工具",
    // 程序版本号 TODO 记得查看并更新版本过期的时间
    version: Number(packageVersion.replaceAll(".", "") + "250907"),
    versionName: "V" + packageVersion + "-Beta",
    // 设备屏幕像素比，init方法初始化时更新
    dpr: 3,
    // 像素缩放比例，用于平板像素放大
    pxRatio: 1,
    // 游戏是否开始，从第一次拖动后，就设置为true
    isGameBeginning: false,
    // 游戏角色是否选择完成，用于控制性能优化
    isRoleChooseFinished: false,
    // 修改参数设置后，是否需要刷新页面
    isNeedReload: false,
    // 程序出错几次弹窗提示
    alertErrorCount: 3,
    // 设置游戏台面占屏幕宽度的比例
    sceneWidthRatio: 0.78,
    // 设置游戏台面边框线宽，取 0.3 * girdSizeCss
    sceneLineWidth: 6,
    // 设置画布显示大小（css样式中的大小）【大图缩小不会模糊】，初始化的时候会计算修改
    cssWidth: 0,
    cssHeight: 0,
    // 设置Canvas画布偏移位置
    cLeft: 0,
    cTop: 0,
    // 网格大小
    girdSize: 0, // canvas 实际的 girdSize
    girdSizeCss: 0, // css 缩小后的 girdSize
    // 是否为玩吧撞击台面，切角不是标准的 180-45=135 而是 180-44=136
    isWan8CocosTable: true,
    // 斜边角度倾斜偏差（单位：像素），初始化的时候会根据 girdSize 重新计算，程序取这里的数值。第一个值对应点(0, 3)，其他点往顺时针方向递增
    wan8CocosTableMoveVals: [0, 0, 0, 0, 0, 0, 0, 0],
    // 在检测两圆球碰撞时，增加一个微小的容差值（epsilon），确保即使小球非常接近也能检测到碰撞
    epsilon: 0.20,
    // 碰撞损耗，玩吧角色碰墙或者碰其他角色，看着似乎没有损耗。checkBounce方法，作用在合速度上
    bounce: 0,
    // 蛋有弹性，碰撞可增加一定百分比的速度
    eggBounce: 0.35, // v * eggBounce 50 * 0.2 = 10
    // 摩擦力 f=μ×Fn（Fn：正压力，不一定等于施力物体的重力(mg) μ：动摩擦因数，是数值，无单位）
    // 简单模拟 0.05 0.24 一个接近0.9的系数能很好的模拟出摩擦力的效果
    friction: 0.575,
    // 角色重量极重，对应数值，默认 100，其他角色相对这个值的比率取值
    maxWeightVal: 100,
    // emoji/svg 图形图形重叠重试次数
    emojiCrossRetryCount: 3,
    // 是否为展示demo
    isDemo: false,
    // 网页背景图片key
    bgImageKey: "COLLIDE-TRY-BG-IMAGE-THEME-",
    // 是否说再见，用于控制显示告别信息
    isSayGoodbye: true,

}
console.log(">>>> sysConfig=" + JSON.stringify(sysConfig));

////////////////////////////////////////////////
// 用户参数配置
////////////////////////////////////////////////
var userConfig = {
    // 主角色配置
    currRole: -1, // 默认没选任何角色，具体设置哪个角色会弹窗提示用户选择。角色对应序号在 Role 枚举类
    // 场景主题，0-默认主题；1-冬季冰雪主题；2-新年主题；3-田园主题；4-星际主题
    sceneThemeMode: -1, // -1 没选择任何主题，根据时间季节自动设置
    // 当前操作方式，0-拖拽（默认）；1-点按
    currPlayOpt: 0,
    // 主角所在队颜色
    mainTeamColor: 'b',
    // 是否随机角色，完全随机
    isRandomRole: false,
    // 是否极速开始，挑选常用组合
    isFlashRole: false,
    // 是否只用一个角色测试
    isTestOnlyOne: false,
    // 是否显示小球运动路径
    isShowBallMovePath: true,
    // 是否显示小球本体路径
    isShowBallPath: true,
    // 碰到另一个小球是否停止运动
    isStopAfterCollided: false,
    // 只瞄准不打，用于截图分享
    isJustTrying: false,
    // 只碰一次角色，用于练习碰撞反弹
    isRoleCollidedOnce: false,
    // 碰两次后停止，用于测试观察角度
    isStopAfter2WallCollided: false,
    // 只显示台面
    isJustShowTable: false,
    // 是否显示台面边框
    isShowTableBorder: true,
    // 是否显示砖格坐标
    isShowGridCoordinate: true,
    // 是否显示砖格全坐标（显示切角砖格）
    isShowGridCoordinateFull: false,
    // 是否显示场景图形
    isShowSceneGraph: true,
    // 是否显示角色血量条
    isShowRoleBloodLine: true,
    // 是否显示角色编号
    isShowRoleBloodNo: true,
    // 是否双击屏幕回退
    isDbclickBack: true,
    // 傀儡拉回
    isKuileiPullBack: true,
    // 瞄准穿透(提升流畅)，只对僵尸、傀儡等可穿透角色有效
    isPiercesTry: false,
    // 瞄准显示路径，只对僵尸、傀儡等可穿透角色有效
    isShowTryFullPath: true,
    // 显示猴子分身提示
    isShowWkPath: true,
    // 瞄准显示路径，指定碰撞几次的路径
    tryFullPathPointNum: 6,
    // 长按重置角色位置
    isLongPressRandom: true,
    // 移动角色显示坐标（单位：格）
    isShowRoleMovePos: true,
    // 分享/导入角色及坐标
    shareRoleAndPos: "",
    // 指定游戏角色，数量不够会随机补满。输入一个字即可自动识别补充角色全名
    gameRoleIds: [-1, -1, -1, -1],
    // 角色加速或减速（负数为减速）
    roleSpeedAddVal: 0,
    // 卡顿自动恢复等待时间（单位：秒）
    animateAutoRestTime: 20,
    // 是否使用自定义主题
    isUseCustomTheme: false,
    // 斜边角度倾斜偏差（单位：格），用户设置看到的是这里的数值。第一个值对应点(0, 3)，其他点往顺时针方向递增
    //wan8CocosTableMoveVals: [0,0.05,-0.05,-0.05,0.12,-0.025,0.025,0.08], // 注意 undefined 找不到值，或者数值不对，需要清除 localStorage 缓存
    wan8CocosTableMoveVals: [0, 0.05, -0.05, -0.05, 0.12, -0.025, 0.025, 0.05],

}
// 用户原始配置备份
var userConfigBack = JSON.parse(JSON.stringify(userConfig));

// 全局参数设置
class GlobalParams {
    constructor(options = {}) {
        /*
        图形叠加模式 https://blog.csdn.net/qq_33933205/article/details/107337882
        copy：只显示新的图层
        xor：显示新的图层和旧的图层，不显示重叠的图层
        source-over：默认值，新的图层覆盖老的图层
        destination-over：新的图层在老的图层下面
        */
        this.composite = options.composite || "";
        // 所有绘制不受限制
        this.isAll = options.isAll || false;
        // 只画小球
        this.isBallOnly = options.isBallOnly || false;
        // 绘制图形，文字、icon、img、svg 等
        this.graph = options.graph || null;
        // 阴影颜色
        this.shadowColor = options.shadowColor || "#999";
        // 虚化范围
        this.shadowBlur = options.shadowBlur || "5";
    }

    static getInstance(options) {
        if (!this.instance) {
            this.instance = new GlobalParams(options);
            //console.log(">>>> GlobalParams new GlobalParams(options)");
        }
        return this.instance;
    }

    reset() {
        this.composite = "";
        this.isAll = false;
        this.isBallOnly = false;
        this.graph = null;
        this.shadowColor = "#999";
        this.shadowBlur = "5";
    }

    static getCleanParams() {
        this.getInstance();
        this.instance.reset();
        return this.instance;
    }
}
const globalParams = GlobalParams.getCleanParams();

//globalParams.graph = "test";
//console.log(globalParams);
//globalParams.reset();
//console.log(globalParams);


// 判断canvas画布是否有绘制内容
// https://segmentfault.com/q/1010000005820251
function isCanvasBlank(canvas) {
    let blank = document.createElement('canvas'); // 创建一个空canvas对象
    blank.width = canvas.width;
    blank.height = canvas.height;
    return canvas.toDataURL() == blank.toDataURL(); // 比较值相等则为空
}

//////////////////////////////////////////////////////////////////////  


//////////////////////////////////////////////////////////////////////
// 【Ball球相关】 变量、方法区域
//////////////////////////////////////////////////////////////////////

// 球/撞击角色对象
class Ball {
    constructor(context, options = {}) {
        this.context = context;
        this.x = options.x || 0; // 位置
        this.y = options.y || 0;
        this.radius = options.radius || 27; // 半径
        this.color = options.color || ''; // 颜色
        this.vx = options.vx || 0; // 速度
        this.vy = options.vy || 0;
        this.ax = options.ax || 0; // 加速度
        this.ay = options.ay || 0;
        ////////////////////////////////////////////////
        // 【新增】小球碰撞检测相关变量
        ////////////////////////////////////////////////
        this.no = options.no || 0; // 角色编号，从1开始
        this.teamColor = options.teamColor || 'r'; // r-red;b-blue
        this.roleId = options.roleId || Role.HEIWA.id; // 小球对应角色id，从枚举 Role 中取id。注意：options.roleId 为 0 时，是 false，导致取值为 -1
        this.isMainBall = options.isMainBall || false; // 是否为主球，目前只有主球可以发射
        this.sizeRatio = options.sizeRatio || 2.0; // 小球相对网格大小的比例，默认 2 个网格大小
        this.pathRadius = options.pathRadius || roundNumber(5.20 / 2 * dpr, 4); // 路径半径
        this.tryRadius = options.tryRadius || this.radius; // 瞄准圈半径
        this.radiusTmp = options.radiusTmp || this.radius; // 半径备份，用于控制半径变化
        this.pathColor = options.pathColor || "#cfe0d380"; // 路径颜色
        this.tryColor = options.tryColor || "#cfe0d330"; // 瞄准连线颜色
        this.collidedCount = options.collidedCount || 0; // （总）碰撞次数
        this.wallCollidedCount = options.wallCollidedCount || 0; // 墙壁碰撞次数
        this.roleCollidedCount = options.roleCollidedCount || 0; // 角色碰撞次数
        this.vRatio = options.vRatio || 1; // 初始速度比率：极快-快-中等-慢-极慢 逐级递减 0.1 黑娃：极快-1
        this.v = options.v || 0; // 初始速度
        this.mRatio = options.mRatio || 1; // 初始重量比率：极重-重-中等-轻-极轻 逐级递减 0.1 黑娃：极轻-0.6
        this.m = options.m || 0; // 初始重量
        this.x0 = options.x0 || 0; // 起点位置
        this.y0 = options.y0 || 0;
        this.addCount = options.addCount || 0; // 叠加技能计数
        // 检测顺序，从大到小，四面墙-四个切角-蛋
        this.isWallCollided = false; // 墙面是否碰撞
        this.isLineCollided = false; // 切角线是否碰撞
        this.isBallCollided = false; // 球是否碰撞
        this.isEggCollided = false; // 蛋是否碰撞
        this.isCollided = false; // 总碰撞标识，墙面、切面、球、蛋，只要有一个就碰撞了就算
        this.isCheckFinished = false; // 碰撞检测是否完成
        this.collidingNos = []; // 正在与哪几个角色碰撞，设置角色时初始化
        // 备份上一个撞击点
        this.preCollided = null;
        // 备份上一个运动点
        this.prePoint = null;
        // 原始撞击点
        this.collidedP0 = { x: 0, y: 0 };
        // 原始撞击点速度
        this.collidedV0 = { x: 0, y: 0 };
        // 渲染控制相关
        this.isMoving = false; // 在移动
        this.isChgPosFinished = false; // 拖动位置完成状态
        // 突破和效果
        this.upgradeEffect = 0;
        // 图标大小
        this.iconSize = 0;
        ////////////////////////////////////////////////
    }

    // 体型常量，极小-1.80；偏小-1.90；小-2.00；中等-2.10；中大-2.20；大-2.30；极大-2.40
    static SIZERATIO = { XS: 1.80, SS: 1.90, S: 2.00, M: 2.10, ML: 2.20, L: 2.30, XL: 2.40 }
    // 速度常量，极慢-0.70；慢-0.75；中等-0.80；快-0.90；极快-1.00
    static SPEEDRATIO = { XS: 0.70, S: 0.75, M: 0.80, L: 0.90, XL: 1.00 }
    // 质量常量，极轻-0.20；轻-0.40；中等-0.60；重-0.80；极重-1.00
    //static WEIGHTRATIO = { XS: 0.20, S: 0.40, M: 0.60, L: 0.80, XL: 1.00 }
    static WEIGHTRATIO = { XS: 0.30, S: 0.45, M: 0.60, L: 0.80, XL: 1.00 }
    // 分身初始位置
    static BODY2POS = { x: -1000, y: -1000 }
    // 特殊角色id
    static SPECIALROLEID = { eggId: -1 }


    // 碰撞后立马更新，避免多次碰撞后才更新
    update() {
        this.ax = roundNumber(this.ax, 4);
        this.ay = roundNumber(this.ay, 4);
        this.vx = roundNumber(this.vx, 4);
        this.vy = roundNumber(this.vy, 4);
        this.vx += this.ax;
        this.vy += this.ay;
        this.x += this.vx;
        this.y += this.vy;
        this.vx = roundNumber(this.vx, 4);
        this.vy = roundNumber(this.vy, 4);
        this.x = roundNumber(this.x, 4);
        this.y = roundNumber(this.y, 4);
        this.x0 = roundNumber(this.x0, 4);
        this.y0 = roundNumber(this.y0, 4);
        console.log(">>>> Ball update " + this.getBallDesc() + " x=" + this.x + ", y=" + this.y);
        console.log(">>>> Ball update " + this.getBallDesc() + " x0=" + this.x0 + ", y0=" + this.y0);
        console.log(">>>> Ball update " + this.getBallDesc() + " vx=" + this.vx + ", vy=" + this.vy);
        console.log(">>>> Ball update " + this.getBallDesc() + " collidedCount=" + this.collidedCount);
        console.log(">>>> Ball update " + this.getBallDesc() + " wallCollidedCount=" + this.wallCollidedCount);
        console.log(">>>> Ball update " + this.getBallDesc() + " roleCollidedCount=" + this.roleCollidedCount);
        console.log(">>>> Ball update " + this.getBallDesc() + " collidingNos=" + this.collidingNos);
        if (this.roleId === Role.KUKU.id) console.log(">>>> Ball update " + this.getBallDesc() + " addCount=" + this.addCount);

        if (this.isMainBall && this.roleId === Role.KUILEI.id && this.wallCollidedCount >= 3) { // 傀儡碰三次后，绳子速度停止
            if (userConfig.isKuileiPullBack && this.roleCollidedCount > 0 && !isKuileiPulling) { // 傀儡绳子有抓到人，且开启了拉回开关
                doKuileiPullBack(this); // 处理傀儡拉回
            } else if (!isKuileiPulling) {
                this.vx = 0;
                this.vy = 0;
            }
        }
        if (this.vx === 0 && this.vy === 0) { // 运动停止了
            this.isMoving = false;
        } else {
            this.isMoving = true;
        }
    }

    // 获取显示字符串
    getBallDesc() {
        return this.no + "-" + Role.getShortNameById(this.roleId) + "-" + this.roleId + "-" + this.teamColor;
    }

    // 获取角色血量条显示序号
    getShowNo() {
        if (userConfig.isTestOnlyOne) return this.no;
        if (this.no > 4) return this.no;
        // 玩吧目前硬性规则，蓝队编号为1、2，红队为3、4
        if (this.teamColor === 'b') {
            if (this.no % 2 === 0) return 2;
            else return 1;
        } else {
            if (this.no % 2 === 0) return 4;
            else return 3;
        }
    }

    // 是否改变了位置
    isPosChanged() {
        return this.x !== this.x0 || this.y !== this.y0;
    }

    // 判断是否为分身 判断分身 角色分身
    isRoleBuddy() {
        if (userConfig.isTestOnlyOne && !this.isMainBall) return true;
        if (!userConfig.isTestOnlyOne && !this.isMainBall && this.no > 4) return true;

        return false;
    }

    // TODO globalParams 目前只是单例，避免draw方法不停地创建对象。js 单线程执行没问题，多线程不行
    draw(params) {
        //if (this.x === this.prePoint.x && this.y === this.prePoint.y) return; // 位置没动不画。不行，画布被清空了，还是得画
        if (!params) params = GlobalParams.getCleanParams();
        //if (selectedBall && selectedBall.isMainBall && this === selectedBall) console.log(selectedBall.context);
        // 单独绘制起点位置
        if (sysConfig.isGameBeginning && this.x === this.x0 && this.y === this.y0) { // 这个坐标判断会出现重复绘制的问题，小球移动后，经过原始位置，又会再画
            this.drawBeginPoint();
        }
        //if (this.isMainBall && this.roleId === Role.KUILEI.id && this.isMoving) return; // 不画绳子上的娃娃，可以直接返回

        // 突破碰撞效果
        if (this.upgradeEffect > 0) this.drawUpgradeCircle();

        // 画角色图标
        if (!params.isBallOnly) this.drawIcon();

        // TODO canvas中使用的save()数量和restore()的数量需要保持一致，save多会导致内存泄漏，及运行一段时间后变卡顿
        // 尽量少改变 Canvas 状态变量，公共设置放到循环外层，可以节省一点性能
        this.context.save();
        this.context.beginPath();
        this.context.globalCompositeOperation = "destination-over"; // 新的图层在老的图层下面，为了实现路径显示在角色上方
        if (params.composite) this.context.globalCompositeOperation = params.composite;
        if (this.isMainBall && this.roleId === Role.KUILEI.id && this.isMoving && !isKuileiPulling) { // 画绑在绳子上的娃娃【真是个细节狂魔啊】
            // 已经用图标代替了
            //this.context.arc(this.x, this.y, this.tryRadius, 0, roundNumber(Math.PI / 180 * 360, 4));
            //this.context.fillStyle = "#415D9C";
        } else {
            this.context.arc(this.x, this.y, this.radiusTmp, 0, roundNumber(Math.PI / 180 * 360, 4));
            this.context.fillStyle = this.color;
        }
        this.context.fill(); // fill 实心；stroke 空心
        // 有露露，为僵僵加上玻璃球
        if (isLuluExist && this.roleId === Role.JIANGJIANG.id && this.id < 0) { // this.id < 0 先不画玻璃球了
            //this.context.globalCompositeOperation = "source-over";
            this.context.arc(this.x, roundNumber(this.y - this.radius / 4, 4), roundNumber(this.radius + 8 * dpr, 4), 0, roundNumber(Math.PI / 180 * 360, 4));
            this.context.fillStyle = "#C0E0F450";
            //this.context.shadowBlur = 10 * dpr; // 频繁绘制阴影会影响性能
            this.context.fill();
        }
        //this.context.closePath(); // 闭合路径
        //this.context.fill();
        this.context.restore();

        // 画主角指示圈
        if (!checkIsMoving() && !params.isBallOnly) this.drawCurrentCircle();
        // 画角色血量条
        if (!params.isBallOnly) this.drawRoleBloodLine();

    }

    // 绘制角色图标
    drawIcon(params) {
        if (!params) params = GlobalParams.getCleanParams();
        this.context.save();
        this.context.beginPath();
        this.context.globalCompositeOperation = "source-over";
        if (params.composite) this.context.globalCompositeOperation = params.composite;
        this.context.fillStyle = "#EEF0F2";
        // 水平对齐方式 (center left right start end)
        this.context.textAlign = "center";
        // 垂直对齐的方式 (top bottom middle)
        this.context.textBaseline = 'middle';

        let content = Role.getRoleIconById(this.roleId);
        let iconType = 0; // 0-兼容图标；1-新图标
        // 双子运动时，两个人分开
        if (isTwinSingleIconShow && userConfig.currRole === Role.SHUANGZI.id && this.roleId === Role.SHUANGZI.id && this.isMainBall && !selectedBall && (checkIsMoving() || isTwinBallShowStill())) {
            // 本体
            if (os.isPc || !isTwinLeftIconShow || !isTwinRightIconShow || !iconType) {
                content = '🧍‍♂️';
            } else {
                content = '🏃';
            }
        }
        if (params.graph) content = params.graph;
        if (isTwinSingleIconShow && userConfig.currRole === Role.SHUANGZI.id && this.roleId === Role.SHUANGZI.id && !this.isMainBall && this.teamColor === balls[0].teamColor) {
            // 分身
            if (os.isPc || !isTwinLeftIconShow || !isTwinRightIconShow || !iconType) {
                content = '🧍';
            } else {
                content = '🏃‍♂️‍➡️';
            }
        }

        // 猴子分身
        if (userConfig.currRole === Role.WUKONG.id && this.roleId === Role.WUKONG.id && !this.isMainBall && this.teamColor === balls[0].teamColor) {
            content = '🐵';
        }

        if (this.iconSize < 10) {
            let metrics, width, ratio;
            ratio = 1.4;
            if (this.roleId === Role.BAKE.id || this.roleId === Role.GOLDKING.id
                || this.roleId === Role.X.id || this.roleId === Role.DUODUO.id
                || this.roleId === Role.HUAQIANJI.id) ratio = 1.2; // 图标偏大，手动调小一点

            if (this.roleId === Role.ZHANAN.id) // 重画多次的图标
                ratio = 1.0;

            let fontSize = roundNumber(sysConfig.girdSize * ratio, 4);
            //console.log(">>>> drawIcon" + this.getBallDesc() + " fontSize origin=" + fontSize);

            this.context.font = fontSize + "px Arial";
            metrics = this.context.measureText(content);
            width = roundNumber(metrics.width, 4);

            while (width > this.radiusTmp * ratio) {
                fontSize -= 1;
                this.context.font = fontSize + "px Arial";
                metrics = this.context.measureText(content);
                width = roundNumber(metrics.width, 4);
                if (fontSize < 12) break; // 避免 width 计算异常，导致死循环
            }
            while (width < sysConfig.girdSize * 1.0) { // sysConfig.girdSize * 1.2
                fontSize += 1;
                this.context.font = fontSize + "px Arial";
                metrics = this.context.measureText(content);
                width = roundNumber(metrics.width, 4);
                if (fontSize > 100) break; // 避免 width 计算异常，导致死循环
            }
            fontSize = roundNumber(fontSize, 4);
            //console.log(">>>> drawIcon" + this.getBallDesc() + " fontSize final=" + fontSize);
            this.iconSize = fontSize;
        }

        this.context.font = this.iconSize + "px Arial";

        // 突破效果
        //if (this.upgradeEffect > 0) this.context.font = (fontSize + 10) + "px Arial";

        if (this.isMainBall && this.roleId === Role.KUILEI.id && this.isMoving) {
            //if (!isKuileiPulling) this.context.fillText(content, this.x0 === 0 ? this.x : this.x0, this.y0 === 0 ? this.y : this.y0); // 本体位置 需要画在路劲层
            if (!isKuileiPulling) this.context.font = (this.iconSize - 3 * dpr) + "px Arial"; // 画完本体之后，调整图标大小，再画绳子娃娃图标
            this.context.fillText(content, this.x, this.y); // 绳子娃娃位置
        } else if (this.roleId === Role.SHUANGZI.id && content === '👬') { // 双子图标重画
            if (os.isPc || !isTwinLeftIconShow || !isTwinRightIconShow || !iconType) {
                this.context.fillText('🧍', roundNumber(this.x + (0.20 * sysConfig.girdSize), 4), roundNumber(this.y - (0.1 * sysConfig.girdSize), 4));
                this.context.fillText('🧍‍♂️', roundNumber(this.x - (0.20 * sysConfig.girdSize), 4), roundNumber(this.y + (0.1 * sysConfig.girdSize), 4));
            } else {
                this.context.fillText('🏃‍♂️‍➡️', roundNumber(this.x + (0.20 * sysConfig.girdSize), 4), roundNumber(this.y - (0.1 * sysConfig.girdSize), 4));
                this.context.fillText('🏃', roundNumber(this.x - (0.20 * sysConfig.girdSize), 4), roundNumber(this.y + (0.1 * sysConfig.girdSize), 4));
            }
        } else if (this.roleId === Role.ZHANAN.id) { // 光影 扎男
            // 多画几个
            //this.context.fillText(content, roundNumber(this.x - (0.20 * sysConfig.girdSize), 4), roundNumber(this.y - (0.2 * sysConfig.girdSize), 4)); // 左上
            this.context.fillText(content, this.x, roundNumber(this.y - (0.4 * sysConfig.girdSize), 4)); // 上
            this.context.fillText(content, this.x, this.y); // 中间
            //this.context.fillText(content, roundNumber(this.x + (0.20 * sysConfig.girdSize), 4), roundNumber(this.y + (0.2 * sysConfig.girdSize), 4)); // 右下
            this.context.fillText(content, this.x, roundNumber(this.y + (0.4 * sysConfig.girdSize), 4)); // 下
        } else if (this.roleId === Role.GOLDKING.id) { // 金角大王
            this.context.fillStyle = "#ffd700";
            this.context.fillText(content, this.x, this.y);
        }
        else this.context.fillText(content, this.x, this.y);
        this.context.restore();
    }

    // 绘制突破碰撞光圈效果
    drawUpgradeCircle(params) {
        //return; // 先不画
        //if (!this.isMainBall) return; // 非主角不画
        if (this.upgradeEffect < 1) return;
        if (!params) params = GlobalParams.getCleanParams();
        this.context.save();
        this.context.beginPath();
        if (params.composite) this.context.globalCompositeOperation = params.composite;
        let grd = this.context.createRadialGradient(this.x, this.y, roundNumber(0.1 * this.radiusTmp, 4), this.x, this.y, roundNumber(this.radiusTmp * 3, 4));
        grd.addColorStop(0.1, "#EEF0F2F0");
        grd.addColorStop(0.3, "#FFFE6150");
        grd.addColorStop(0.6, "#EEF0F280");
        grd.addColorStop(1, "#EEF0F200");
        this.context.arc(this.x, this.y, roundNumber(this.radiusTmp * 2.5, 4), 0, roundNumber(Math.PI * 2, 4), true);
        //this.context.fillStyle = "#EEF0F2"; // 设置颜色
        this.context.fillStyle = grd; // 使用渐变
        this.context.fill();
        this.context.restore();
        // TODO 画完后重置，需要等画完再重置，确保距离很近碰撞时，看不到碰撞效果
        //console.log(">>>> doDianyinSpeed upgradeEffect", this.upgradeEffect);
        //setTimeout(()=>{this.upgradeEffect = 0;}, 20);
        if (this.upgradeEffect > 2) this.upgradeEffect = 0; // 这样可以延迟重置
        if (this.upgradeEffect > 0) this.upgradeEffect += 1;
    }

    // 绘制当前主攻角色指示圈
    drawCurrentCircle(params) {
        if (!this.isMainBall) return; // 非主角不画
        if (userConfig.isTestOnlyOne) return; // 单个角色测试时不画
        if (!params) params = GlobalParams.getCleanParams();
        this.context.save();
        this.context.beginPath();
        if (params.composite) this.context.globalCompositeOperation = params.composite;
        this.context.arc(this.x, this.y, roundNumber(this.radiusTmp + 2 * dpr * sysConfig.pxRatio, 4), 0, roundNumber(Math.PI / 180 * 360, 4));
        this.context.strokeStyle = "#D75956";
        if (this.teamColor === 'b') this.context.strokeStyle = "#0A7AFD";
        this.context.closePath();
        this.context.lineWidth = roundNumber(0.085 * sysConfig.girdSize); // 0.0892
        this.context.stroke();
        this.context.restore();
    }

    // 绘制瞄准时被碰撞角色指示圈
    drawAimCircle(params) {
        if (this.isMainBall) return; // 瞄准时被碰撞角色为非主角
        if (userConfig.isTestOnlyOne) return; // 单个角色测试时不画
        if (!params) params = GlobalParams.getCleanParams();
        let context = selectedBall.context;
        context.save();
        context.beginPath();
        if (params.composite) context.globalCompositeOperation = params.composite;
        context.arc(this.x, this.y, roundNumber(this.radiusTmp - 1 * dpr * sysConfig.pxRatio, 4), 0, roundNumber(Math.PI / 180 * 360, 4));
        context.strokeStyle = "#D84646";
        if (this.teamColor === 'b') context.strokeStyle = "#2A7CE9";
        context.closePath();
        context.lineWidth = roundNumber(2 * dpr * sysConfig.pxRatio, 4);
        context.stroke();
        context.restore();
    }

    // 绘制角色血量条
    drawRoleBloodLine(params) {
        if (!userConfig.isShowRoleBloodLine) return;
        //if (userConfig.isTestOnlyOne) return; // 单个角色测试时不画
        if (!this.x || !this.y || this.x < 0 || this.y < 0 || !isFinite(this.x) || !isFinite(this.y)) return;
        if (this.roleId === Role.WUKONG.id && this.isRoleBuddy()) return; // 猴子分身不画
        if (!params) params = GlobalParams.getCleanParams();
        this.context.save();
        this.context.fillStyle = "#D84646";
        this.context.strokeStyle = "#00000050";
        this.context.lineWidth = roundNumber(0.25 * dpr * sysConfig.pxRatio, 4);
        if (this.teamColor === 'b') this.context.fillStyle = "#2A7CE9";
        // TODO 频繁绘制阴影，会影响性能，可以改用描边形式，用scene观察了功耗，有阴影确实功率最大值更高
        //this.context.shadowColor = '#00000050'; // 设置阴影
        //this.context.shadowBlur = roundNumber(0.5 * dpr * sysConfig.pxRatio, 4);
        //this.context.globalCompositeOperation = "destination-over";
        if (params.composite) this.context.globalCompositeOperation = params.composite;

        let roleNoWidth = roundNumber(0.6 * sysConfig.girdSize);
        let bloodLineWidth = roundNumber(2.6 * sysConfig.girdSize - roleNoWidth, 4);
        let bloodLineWidth2 = roundNumber(2.3 * sysConfig.girdSize, 4);
        let bloodLineHeight = roundNumber(0.40 * sysConfig.girdSize, 4);
        let borderRadius = 4;

        this.context.font = 10 * sysConfig.pxRatio * dpr + "px Arial";
        this.context.textAlign = "center";
        this.context.textBaseline = 'middle';

        // 角色本体坐标位置
        let realPos = { x: this.x, y: this.y };
        if (this.isMainBall && this.roleId === Role.KUILEI.id && this.isMoving && !isKuileiPulling) { // 傀儡画在本体上
            realPos.x = this.x0 === 0 ? this.x : this.x0;
            realPos.y = this.y0 === 0 ? this.y : this.y0;
        }

        // TODO roundRect 兼容性有问题，老机型/老浏览器不支持
        try {
            // 分身没有角色编号，只有普通血量条
            // 没有开启显示角色编号，只显示普通血量条
            if (this.isRoleBuddy() || !userConfig.isShowRoleBloodNo) {
                this.context.beginPath();
                this.context.roundRect(roundNumber(realPos.x - bloodLineWidth2 / 2, 4), roundNumber(realPos.y - this.radiusTmp - 0.3 * sysConfig.girdSize - bloodLineHeight, 4), bloodLineWidth2, bloodLineHeight, borderRadius);
                this.context.stroke();
                this.context.fill();
            } else {
                // 血量条
                this.context.beginPath();
                this.context.roundRect(roundNumber(realPos.x - (bloodLineWidth - roleNoWidth) / 2 - 1 * dpr, 4), roundNumber(realPos.y - this.radiusTmp - 0.3 * sysConfig.girdSize - bloodLineHeight, 4), bloodLineWidth, bloodLineHeight, borderRadius);
                this.context.stroke();
                this.context.fill();
                // 角色编号方框
                this.context.beginPath();
                this.context.roundRect(roundNumber(realPos.x - (bloodLineWidth + roleNoWidth) / 2 + 1 * dpr, 4), roundNumber(realPos.y - this.radiusTmp - 0.3 * sysConfig.girdSize - roleNoWidth + (roleNoWidth - bloodLineHeight) / 2, 4), roleNoWidth, roleNoWidth, borderRadius);
                this.context.stroke();
                this.context.fill();
                // 角色编号文字
                this.context.beginPath();
                this.context.fillStyle = "#fff";
                this.context.strokeText(this.getShowNo(), roundNumber(realPos.x - bloodLineWidth / 2 + 1 * dpr, 4), roundNumber(realPos.y - this.radiusTmp - 0.3 * sysConfig.girdSize - roleNoWidth / 2 + (roleNoWidth - bloodLineHeight) / 2, 4));
                this.context.fillText(this.getShowNo(), roundNumber(realPos.x - bloodLineWidth / 2 + 1 * dpr, 4), roundNumber(realPos.y - this.radiusTmp - 0.3 * sysConfig.girdSize - roleNoWidth / 2 + (roleNoWidth - bloodLineHeight) / 2, 4));
                this.context.stroke();
            }
        } catch (e) {
            doGlobalErrorMsg(e, false);
            //doGlobalError(e, (sysConfig && sysConfig.alertErrorCount)?sysConfig.alertErrorCount:3);
            // 使用原始方法绘制圆角矩形 fillRoundRect(cxt, x, y, width, height, radius, fillColor)
            this.context.beginPath();
            fillRoundRect(this.context, roundNumber(realPos.x - bloodLineWidth2 / 2, 4), roundNumber(realPos.y - this.radiusTmp - 0.3 * sysConfig.girdSize - bloodLineHeight, 4), bloodLineWidth2, bloodLineHeight, borderRadius, this.context.fillStyle);
            this.context.stroke();
            this.context.fill();
        }
        this.context.restore();
    }

    // canvas 图形动画的致命问题就是每次都要全部清除重画！就好像用电饭煲炒菜，能炒但是很无力！
    // 绘制角色+血量条区域矩形，用于后续【脏矩形】优化
    drawBallRect(params) {
        if (!params) params = GlobalParams.getCleanParams();
        this.context.save();
        this.context.beginPath();
        if (params.composite) this.context.globalCompositeOperation = params.composite;
        if (userConfig.isShowRoleBloodLine)
            this.context.strokeRect(this.x - this.radius, this.y - this.radius, this.radius * 2, this.radius * 2);
        else this.context.strokeRect(this.x - this.radius, this.y - this.radius, this.radius * 2, this.radius * 2);
        this.context.strokeStyle = "#000";
        this.context.lineWidth = 1 * dpr;
        this.context.setLineDash([3 * dpr, 3 * dpr]); // 虚线
        this.context.stroke();
        this.context.restore();
    }

    // 绘制起点位置
    drawBeginPoint(params) {
        if (!this.isMainBall) return; // 非主球不画
        if (!params) params = GlobalParams.getCleanParams();
        console.log(">>>> drawBeginPoint " + this.getBallDesc());
        // 画圆心点
        gamePathContext.save();
        gamePathContext.beginPath();
        //gamePathContext.globalCompositeOperation = "xor";
        if (params.composite) gamePathContext.globalCompositeOperation = params.composite;
        gamePathContext.arc(this.x0, this.y0, this.pathRadius, 0, roundNumber(Math.PI / 180 * 360, 4));
        gamePathContext.fillStyle = this.color;
        gamePathContext.closePath();
        gamePathContext.fill();
        gamePathContext.restore();
        // 画外部实线圆圈
        gamePathContext.save();
        gamePathContext.beginPath();
        //gamePathContext.globalCompositeOperation = "xor";
        gamePathContext.arc(this.x0, this.y0, this.radiusTmp, 0, roundNumber(Math.PI / 180 * 360, 4));
        gamePathContext.lineWidth = roundNumber(1 * dpr * sysConfig.pxRatio, 4);
        gamePathContext.strokeStyle = this.color;
        gamePathContext.fillStyle = this.color;
        gamePathContext.closePath();
        if (this.isMainBall && this.roleId === Role.KUILEI.id) gamePathContext.fill(); // 傀儡本体不会动
        else gamePathContext.stroke();
        gamePathContext.restore();
        // 重画被覆盖的角色图标
        this.drawIcon();
        if (this.isMainBall && this.roleId === Role.KUILEI.id) this.drawBeginIcon(); // 画傀儡本体图标
    }

    // 绘制分身起点位置
    drawBuddyBeginPoint(params) {
        if (!params) params = GlobalParams.getCleanParams();
        console.log(">>>> drawBuddyBeginPoint " + this.getBallDesc());
        let color = params.color;
        if (!color) color = this.color;
        let ctx = params.ctx;
        if (!ctx) ctx = gamePathContext;
        // 画圆心点
        ctx.save();
        ctx.beginPath();
        //ctx.globalCompositeOperation = "xor";
        if (params.composite) ctx.globalCompositeOperation = params.composite;
        ctx.arc(this.x0, this.y0, this.pathRadius, 0, roundNumber(Math.PI / 180 * 360, 4));
        ctx.fillStyle = color;
        ctx.closePath();
        ctx.fill();
        ctx.restore();
        // 画外部实线圆圈
        ctx.save();
        ctx.beginPath();
        //ctx.globalCompositeOperation = "xor";
        ctx.arc(this.x0, this.y0, this.radiusTmp, 0, roundNumber(Math.PI / 180 * 360, 4));
        ctx.lineWidth = roundNumber(1 * dpr * sysConfig.pxRatio, 4);
        ctx.strokeStyle = color;
        ctx.fillStyle = color;
        ctx.closePath();
        ctx.stroke();
        ctx.restore();
    }

    // 绘制起点图标
    drawBeginIcon(params) {
        if (!this.isMainBall) return; // 非主球不画
        console.log(">>>> drawBeginIcon " + this.getBallDesc());
        if (!params) params = GlobalParams.getCleanParams();
        let ctx = params.context;
        if (!ctx) ctx = gamePathContext;
        let content = Role.getRoleIconById(this.roleId);
        if (!content) return;

        ctx.save();
        ctx.beginPath();
        ctx.textAlign = "center";
        ctx.textBaseline = 'middle';
        ctx.font = this.iconSize + "px Arial";
        ctx.fillText(content, this.x, this.y);
        ctx.restore();
    }

    // 画连线撞击轨迹【画在路径层】
    drawLinePath(p1, p2) {
        if (!this.isMoving) return; // 没在运动不画
        if (!this.isMainBall && this.roleId !== Role.SHUANGZI.id) return; // 非主球不画，双子分身除外
        if (!this.isMainBall && this.roleId === Role.SHUANGZI.id && !userConfig.isTestOnlyOne && this.no > 1 && this.no < 5) return;
        if (!p1 || !p2) return;
        if (isKuileiPulling) return; // 傀儡拉回时不画
        gamePathContext.save();
        gamePathContext.beginPath();
        gamePathContext.globalCompositeOperation = "source-over";
        gamePathContext.moveTo(roundNumber(p1.x, 4), roundNumber(p1.y, 4));
        gamePathContext.lineTo(roundNumber(p2.x, 4), roundNumber(p2.y, 4));
        gamePathContext.strokeStyle = currTheme.plColor;
        if (userConfig.currRole === Role.SHUANGZI.id && !this.isMainBall && this.roleId === Role.SHUANGZI.id)
            gamePathContext.strokeStyle = currTheme.szbplColor; // 双子分身运动路径颜色
        if (this.roleId === Role.KUILEI.id)
            gamePathContext.strokeStyle = currTheme.klplColor; // 傀儡路径颜色
        gamePathContext.lineWidth = currTheme.plWidth;
        if (this.roleId === Role.KUILEI.id)
            gamePathContext.lineWidth = currTheme.klplWidth;
        gamePathContext.stroke();
        gamePathContext.restore();
    }

    // 绘制小球本体运动路径
    drawBallPath(p1, p2) {
        //if (!userConfig.isShowBallPath) return; // 方便直接显示路径
        if (this.isMainBall && this.roleId === Role.KUILEI.id) return; // 傀儡不画
        if (!this.isMoving) return;
        if (!this.isMainBall && this.roleId !== Role.SHUANGZI.id) return; // 非主球不画，双子分身除外
        if (!this.isMainBall && this.roleId === Role.SHUANGZI.id && !userConfig.isTestOnlyOne && this.no > 1 && this.no < 5) return;
        if (!p1 || !p2) return;
        if (isKuileiPulling) return; // 傀儡拉回时不画
        gamePathBallContext.save();
        gamePathBallContext.beginPath(); // 开始一条路径，或重置当前的路径。
        gamePathBallContext.globalCompositeOperation = "xor"; // 显示新的图层和旧的图层，不显示重叠的图层
        //gamePathBallContext.globalCompositeOperation = "destination-over"; // 新的图层在老的图层下面
        gamePathBallContext.moveTo(roundNumber(p1.x, 4), roundNumber(p1.y, 4));
        gamePathBallContext.lineTo(roundNumber(p2.x, 4), roundNumber(p2.y, 4));
        gamePathBallContext.strokeStyle = currTheme.rlColor;
        if (!this.isMainBall && this.roleId === Role.SHUANGZI.id)
            //gamePathBallContext.strokeStyle = currTheme.szbrlColor; // 双子分身本体路径颜色
            gamePathBallContext.strokeStyle = currTheme.rlColor; // 双子分身本体路径颜色可以跟本体一致
        gamePathBallContext.lineWidth = roundNumber(this.radius * 2, 4);
        //gamePathBallContext.lineCap = "round"; // 圆角
        gamePathBallContext.stroke();
        gamePathBallContext.restore();
        return;
        // 起点填充
        if (p1.x === this.x0 && p1.y === this.y0) { // 坐标判断会导致重复绘制
            gamePathBallContext.save();
            gamePathBallContext.beginPath();
            //gamePathBallContext.globalCompositeOperation = "destination-over";
            gamePathBallContext.globalCompositeOperation = "xor";
            gamePathBallContext.arc(p1.x, p1.y, this.radius, 0, roundNumber(Math.PI / 180 * 360, 4));
            gamePathBallContext.fillStyle = "#cfe0d380";
            gamePathBallContext.fill();
            gamePathBallContext.restore();
            // 起点重新绘制
            this.drawBeginPoint();
        }
    }

    // 画小圆点撞击轨迹
    drawPointPath() {
        if (!this.isMainBall) return;
        if (isKuileiPulling) return; // 傀儡拉回时不画
        gamePathContext.save();
        gamePathContext.beginPath();
        gamePathContext.arc(this.x, this.y, this.pathRadius, 0, roundNumber(Math.PI / 180 * 360, 4));
        gamePathContext.fillStyle = "#cfe0d350";
        gamePathContext.closePath();
        gamePathContext.fill();
        gamePathContext.restore();
    }

    // 单独绘制碰撞位置，在检查碰撞的时候调用【画在路径层】
    drawCollidedPos() {
        if (!this.isMainBall && this.roleId !== Role.SHUANGZI.id) return; // 非主球不画，双子分身除外
        if (!this.isMainBall && this.roleId === Role.SHUANGZI.id && !userConfig.isTestOnlyOne && this.no > 1 && this.no < 5) return;
        if (this.isMainBall && this.roleId === Role.KUILEI.id) return; // 傀儡不画碰撞点
        if (this.isMainBall && userConfig.isStopAfter2WallCollided && this.wallCollidedCount >= 2) return; // 碰撞两次停止时不画
        // 绘制外虚线
        gamePathContext.save();
        gamePathContext.beginPath();
        gamePathContext.arc(this.x, this.y, this.radius, 0, roundNumber(Math.PI / 180 * 360, 4));
        gamePathContext.lineWidth = currTheme.ccWidth;
        gamePathContext.strokeStyle = currTheme.ccColor;
        if (userConfig.currRole === Role.SHUANGZI.id && !this.isMainBall && this.roleId === Role.SHUANGZI.id)
            gamePathContext.strokeStyle = currTheme.szccColor; // 双子分身碰撞圈颜色
        gamePathContext.setLineDash([Math.round(3 * dpr * sysConfig.pxRatio), Math.round(3 * dpr * sysConfig.pxRatio)]); // 虚线
        gamePathContext.closePath();
        gamePathContext.stroke(); // 空心
        gamePathContext.restore();
        // 绘制圆心，不太明显，可以跟路径颜色一致
        gamePathContext.save();
        gamePathContext.beginPath();
        gamePathContext.arc(this.x, this.y, roundNumber(this.pathRadius / 2, 4), 0, roundNumber(Math.PI / 180 * 360, 4));
        //gamePathContext.fillStyle = this.color;
        gamePathContext.fillStyle = currTheme.plColor;
        gamePathContext.closePath();
        gamePathContext.fill();
        gamePathContext.restore();

        //if (userConfig.isShowBallPath) {
        // 绘制小球实体填充
        gamePathBallContext.save();
        gamePathBallContext.beginPath();
        //gamePathBallContext.globalCompositeOperation = "destination-over"; // 在下方
        gamePathBallContext.globalCompositeOperation = "xor"; // 显示新的图层和旧的图层，不显示重叠的图层
        gamePathBallContext.arc(this.x, this.y, this.radius, 0, roundNumber(Math.PI / 180 * 360, 4));
        //gamePathBallContext.fillStyle = this.color;
        //gamePathBallContext.fillStyle = "#cfe0d385";
        gamePathBallContext.fillStyle = currTheme.plColor;
        gamePathBallContext.closePath();
        gamePathBallContext.fill();
        gamePathBallContext.restore();
        //}
    }
}


// 将所有小球速度置零
function stopAllBalls(balls) {
    balls.some(ball => {
        ball.vx = 0;
        ball.vy = 0;
        ball.update();
    });
}


// 小球是否需要重绘和更新
function isBallDrawAndUpdate(ball, caseNo) {
    // 游戏没开始，肯定要画的
    if (!sysConfig.isGameBeginning) return true;

    // 主角在拖动和瞄准时，所有非主角不画
    if (caseNo === 2 && isMouseMoving && selectedBall && selectedBall.isMainBall) return false;
    // 非主角在拖动和瞄准时，主角也不画
    //if (caseNo === 1 && isMouseMoving && !selectedBall.isMainBall) return false;

    // 僵尸、幽灵不能改变其他角色位置；傀儡不拉回时，也不能改变其他角色位置
    if (caseNo === 2 && (userConfig.currRole === Role.JIANGJIANG.id || userConfig.currRole === Role.YLPAPA.id
        || (userConfig.currRole === Role.KUILEI.id && !isKuileiPulling))) {
        return checkAnyBallPosChanged(caseNo);
    }

    // 双子为主角时，本体和分身控制
    if (userConfig.currRole === Role.SHUANGZI.id && ball && ball.roleId === Role.SHUANGZI.id && ball.teamColor === balls[0].teamColor) { // 双子分身要同时运动
        // 双子本体
        if (ball.isMainBall) {

        } else { // 双子分身
            return (checkAnyBallPosChanged(caseNo) || checkAnyBallCollided(caseNo)) && !selectedBall;
        }
    }

    // 猴子及分身
    if (userConfig.currRole === Role.WUKONG.id && ball && ball.roleId === Role.WUKONG.id && ball.teamColor === balls[0].teamColor) {
        // 本体
        if (ball.isMainBall) {

        } else { // 分身
            return !selectedBall;
        }
    }

    return checkAnyBallPosChanged(caseNo) || checkAnyBallCollided(caseNo);
}


// 检测任意一个小球是否改变了位置
function checkAnyBallPosChanged(caseNo) {
    let result = false;
    if (!caseNo) caseNo = 0;

    // TODO 注意！！balls 变量在定义前使用，需要使用 var 定义才行，let 定义之前会报 undefined
    if (!balls || balls.length < 1) return result;

    let isCheckMain;
    switch (caseNo) {
        case 1: // 只检测主球
            return balls[0].isPosChanged();
        case 2: // 只检测非主球
            isCheckMain = false;
            break;
        default: // 检测所有
            isCheckMain = true;
    }

    for (let i = 0, len = balls.length; i < len; i++) {
        if (!isCheckMain && balls[i].isMainBall) continue;
        result = result || balls[i].isPosChanged();
        if (result) break;
    }

    return result;
}


// 检测任意一个小球是否有碰撞
function checkAnyBallCollided(caseNo) {
    let result = false;
    if (!caseNo) caseNo = 0;

    if (!balls || balls.length < 1) return result;

    let isCheckMain;
    switch (caseNo) {
        case 1: // 只检测主球
            return balls[0].collidedCount > 0;
        case 2: // 只检测非主球
            isCheckMain = false;
            break;
        default: // 检测所有
            isCheckMain = true;
    }

    for (let i = 0, len = balls.length; i < len; i++) {
        if (!isCheckMain && balls[i].isMainBall) continue;
        result = result || balls[i].collidedCount > 0;
        if (result) break;
    }

    return result;
}


// 检测是否为分身初始位置
function isRoleHideBody(ball) {
    if (!ball || ball.isMainBall) return false;
    //return !(isNumber(ball.x) && isNumber(ball.y) && ball.x0 !== Ball.BODY2POS.x && ball.y0 !== Ball.BODY2POS.y);
    return ball.x0 === Ball.BODY2POS.x && ball.y0 === Ball.BODY2POS.y;
}


// 重置角色字段属性值
function resetRoleField(roles) {
    if (!roles) roles = balls;
    if (!roles || roles.length < 1) return;
    for (let i = 0, len = roles.length; i < len; i++) {
        if (!roles[i]) continue;
        // 重置酷酷加速次数
        if (roles[i].roleId === Role.KUKU.id && roles[i].addCount) roles[i].addCount = 0;
        // 重置所有角色碰撞次数
        if (roles[i].collidedCount) roles[i].collidedCount = 0;
        if (roles[i].wallCollidedCount) roles[i].wallCollidedCount = 0;
        if (roles[i].roleCollidedCount) roles[i].roleCollidedCount = 0;
    }
    // 重置碰撞标志位
    setBallCollidingNos(roles);
}


// 备份或还原原始坐标
function setBallsPosBack(isBack) {
    if (!balls || balls.length < 1) return;
    for (let i = 0, len = balls.length; i < len; i++) {
        //if (balls[i].isMainBall) continue;
        if (isBack) {
            balls[i].x0 = balls[i].x;
            balls[i].y0 = balls[i].y;
        } else {
            if (balls[i].x0 > 0 && balls[i].y0 > 0) {
                balls[i].x = balls[i].x0;
                balls[i].y = balls[i].y0;
            }
            balls[i].x0 = 0;
            balls[i].y0 = 0;
        }
    }
}


// 初始化各个小球的碰撞标志位
function setBallCollidingNos(roles) {
    if (!roles) roles = balls;
    if (!roles || roles.length < 1) return;
    let len = roles.length;
    if (buddies && buddies.length > 0 && roles !== buddies) len += buddies.length;
    roles.forEach(b => {
        //b.collidingNos = new Array(len).fill(false);  // 频繁创建数组对象，会增加 GC 时间
        for (let i = 0; i < len; i++) {
            b.collidingNos[i] = false; // TODO b.collidingNos 存在扩大后没有正常缩小的问题
        }
    });
    if (!buddies || buddies.length < 1 || roles === buddies) return;
    buddies.forEach(b => {
        for (let i = 0; i < len; i++) {
            b.collidingNos[i] = false;
        }
    });
}


// 双子功能
function doTwins(ball) {
    preTwins(ball);
}


// 初始化双子分身
function preTwins(ball) {
    //let twinBall = balls[balls.length - 1];
    // 位置与本体一样
    twinBall.x = ball.x;
    twinBall.y = ball.y;
    twinBall.x0 = 0;
    twinBall.y0 = 0;
    // 速度与本体相反，分身就稍微后跑了一点，距离比本体少，手动加一点速度
    twinBall.v = ball.v; // checkFriction() 方法需要用于计算摩擦力
    twinBall.vx = -ball.vx * 1.0275;
    twinBall.vy = -ball.vy * 1.0275;
    //console.log(">>>> twinBall:", twinBall);
}


// 双子打完后，分身消失
function afterTwins(isShow) {
    if (userConfig.currRole !== Role.SHUANGZI.id) return;
    //console.log(">>>> afterTwins isShow=" + isShow);
    //let twinBall = balls[balls.length - 1];
    /*
    // 移除分身
    let b = balls.pop();
    if (b.roleId === Role.SHUANGZI.id && b.no !== ball.no) {
        // 符合条件，移除
    } else {
        balls.push(b); // 不符合条件，放回去
    }
    */
    // 移出画布之外即可
    if (!isShow) {
        twinBall.x = Ball.BODY2POS.x;
        twinBall.y = Ball.BODY2POS.y;
        twinBall.x0 = Ball.BODY2POS.x;
        twinBall.y0 = Ball.BODY2POS.y;
    }
    twinBall.vx = 0;
    twinBall.vy = 0;
}


// 双子分身是否还在显示
function isTwinBallShowStill() {
    if (!balls || balls.length < 1) return false;
    for (let i = 0, len = balls.length; i < len; i++) {
        if (!balls[i]) continue;
        if (balls[i].isMainBall) continue;
        if (!balls[i].roleId) continue;
        if (balls[i].roleId !== Role.SHUANGZI.id) continue;
        if (balls[i].teamColor !== balls[0].teamColor) continue;
        if (isNumber(balls[i].x) && isNumber(balls[i].y) && balls[i].x > 0 && balls[i].y > 0) return true;
    }
    return false;
}


// 校正被打出场地之外的角色坐标
// 注意！角色分身等特殊角色，可能就是需要设置场地外坐标，以达到开局隐藏的目的
// 【打完之后调用】，避免在 onMouseMove 这种监听类大量执行的方法中调用，减少性能开销
function adjustBallsPos() {
    if (!balls || balls.length < 1) return;
    let ball;
    for (let i = 0, len = balls.length; i < len; i++) {
        ball = balls[i];
        // 双子分身排除
        if (!ball.isMainBall && ball.roleId === Role.SHUANGZI.id) continue;
        // 小于0；大于场地宽高；在切角区域内
        if ((ball.x < 0 || ball.y < 0 || !isNumber(ball.x) || !isNumber(ball.y))
            || (ball.x > canvas.width || ball.y > canvas.height)
            //|| isInAngleArea(ball) > -1) {
        ) {
            // 重新随机位置
            putBallRandom(ball);
        }
    }
}


// 推开靠在一起的角色，避免两角色贴着碰撞穿透问题
// 拖动改变位置后调用
function pushCollidedBalls() {
    if (!balls || balls.length < 1) return;
    let ball;
    for (let i = 0, len = balls.length; i < len; i++) {
        ball = balls[i];
        // 双子分身排除
        if (!ball.isMainBall && ball.roleId === Role.SHUANGZI.id) continue;
        // 小于0；大于场地宽高；在切角区域内
        if ((ball.x < 0 || ball.y < 0 || !isNumber(ball.x) || !isNumber(ball.y))
            || (ball.x > canvas.width || ball.y > canvas.height)
            //|| isInAngleArea(ball) > -1) {
        ) {
            // 重新随机位置
            putBallRandom(ball);
        }
    }
}


// 获取一个球向另一个球的速度
function getPullBackSpeed() {
    if (!balls || balls.length < 1) return;
    let mainBall = balls[0];
    let ball, vxy;
    for (let i = 0, len = balls.length; i < len; i++) {
        if (i === 0) continue;
        ball = balls[i];
        if (ball.roleCollidedCount < 1) continue;
        vxy = getVxVy({ x: mainBall.x, y: mainBall.y }, { x: ball.x, y: ball.y }, null, mainBall);
        if (!vxy) continue;
        ball.vx = vxy.vx;
        ball.vy = vxy.vy;
        //console.log(">>>> getPullBackSpeed " + ball.getBallDesc() + "-vx=" + ball.vx + ", vy=" + ball.vy);
    }
    // 傀儡拉回时，自身没有速度
    if (mainBall.isMainBall && mainBall.roleId === Role.KUILEI.id) {
        mainBall.vx = 0;
        mainBall.vy = 0;
    }
}


// 是否为可穿透角色，僵尸、傀儡、游侠、剑士等
// 用于判断是否显示瞄准路径
function isRoleCanPierces() {
    return userConfig.isShowTryFullPath
        && (userConfig.currRole === Role.JIANGJIANG.id || userConfig.currRole === Role.KUILEI.id
            || userConfig.currRole === Role.HEIWA.id || userConfig.currRole === Role.DUODUO.id
            || userConfig.currRole === Role.YLPAPA.id);
}


// 用于判断是否在瞄准的时候穿透一次
function isTryCanPierces() {
    return userConfig.isPiercesTry
        && (userConfig.currRole === Role.JIANGJIANG.id || userConfig.currRole === Role.KUILEI.id
            || userConfig.currRole === Role.YLPAPA.id);
}


//////////////////////////////////////////////////////////////////////


//////////////////////////////////////////////////////////////////////
// 【Line切角线相关】 变量、方法区域
//////////////////////////////////////////////////////////////////////

// 四根切角线对象
class Line {
    constructor(context, options = {}) {
        this.context = context;
        this.x1 = options.x1 || 0;
        this.y1 = options.y1 || 0;
        this.x2 = options.x2 || 0;
        this.y2 = options.y2 || 0;
        this.lineWidth = options.lineWidth || 1.0;
        this.color = options.color || '#453678';
        // 旋转角度，Math.atan2() 返回从原点 (0,0) 到 (x,y) 点的线段与 x 轴正方向之间的平面角度 (弧度值)，也就是 Math.atan2(y,x)
        this.rotation = Math.atan2(this.y2 - this.y1, this.x2 - this.x1);
    }

    draw() {
        this.context.save();
        this.context.lineWidth = this.lineWidth;
        this.context.strokeStyle = this.color;
        this.context.beginPath();
        this.context.moveTo(this.x1, this.y1);
        this.context.lineTo(this.x2, this.y2);
        this.context.closePath();
        this.context.stroke();
        this.context.restore();
    }

    getBounds() {
        let minX = Math.min(this.x1, this.x2);
        let minY = Math.min(this.y1, this.y2);
        let maxX = Math.max(this.x1, this.x2);
        let maxY = Math.max(this.y1, this.y2);
        return {
            x: minX,
            y: minY,
            width: maxX - minX,
            height: maxY - minY
        }
    };
}

//////////////////////////////////////////////////////////////////////


//////////////////////////////////////////////////////////////////////
// 【Role角色相关】 变量、方法区域
//////////////////////////////////////////////////////////////////////

// 角色类
class Role {

    constructor(id, icon, fullName, shortName, oneName, cps) {
        this.id = id;
        this.icon = icon;
        this.fullName = fullName;
        this.shortName = shortName;
        this.oneName = oneName;
        this.cps = cps; // 常用搭配
    }

    /*
    添加角色要修改的地方
    1.Role 类角色定义
    2.initRoleCps 设置常用搭配
    3.initBallByRole 配置角色属性
    */

    //static HEIWA = {id:0, icon:"🍼", fullName:"圣婴大王", shortName:"黑娃", oneName:"娃", cps:null};
    static HEIWA = new Role(0, "👶🏽", "圣婴大王", "黑娃", "娃", null);
    static JIANGJIANG = new Role(1, "🧟‍♂", "波比僵僵", "僵尸", "僵", null);
    static DUODUO = new Role(2, "🥚", "风铃朵朵", "朵朵", "朵", null);
    static KUILEI = new Role(3, "🦊", "傀儡娃娃", "傀儡", "傀", null);
    static BAKE = new Role(4, "8g", "火焰巴克", "巴克", "巴", null); // 🧝‍♂️ 天神降临皮肤【尽可能不用氪金皮肤图标】
    static LULU = new Role(5, "🍰", "甜心露露", "露露", "露", null);
    static KUKU = new Role(6, "😎", "疾速酷酷", "酷酷", "酷", null);
    static YINGYING = new Role(7, "❄", "冰雪莹莹", "莹莹", "莹", null);
    static JIUWEIHU = new Role(8, "🦊", "狐尾纱", "狐尾", "纱", null);
    static SHUANGZI = new Role(9, "👬", "怪盗双子", "双子", "双", null);
    static X = new Role(10, "x", "自定角色", "自定", "x", null); // 自定义角色
    static YOUXIA = new Role(11, "🏹", "暗夜游侠", "游侠", "箭", null);
    static CHUZI = new Role(12, "🍗", "小食神", "厨子", "厨", null);
    static HUAQIANJI = new Role(13, "🚀", "花千机", "炮弹", "机", null);
    static WUGEGE = new Role(14, "🌿", "巫格格", "格格", "格", null);
    static JOKER = new Role(15, "🤡", "命运小丑", "小丑", "丑", null);
    static RABBIT = new Role(16, "🐇", "波斯公主", "兔子", "兔", null);
    static NURSE = new Role(17, "💉", "姬天使", "奶妈", "奶", null);
    static CAPTAIN = new Role(18, "🚢", "赤翎船长", "船长", "船", null);
    static LELE = new Role(19, "🥙", "太平乐", "乐乐", "乐", null);
    static MANWANG = new Role(20, "🏒", "蛮王", "蛮王", "蛮", null);
    static LINGLING = new Role(21, "🔔", "波比灵灵", "灵灵", "灵", null);
    static HUOWANG = new Role(22, "🔥", "烈焰王子", "火王", "火", null);
    static LEIMENG = new Role(23, "🐖", "雷德蒙的", "雷蒙", "猪", null);
    static DIANYIN = new Role(24, "🎵", "电音少女", "电音", "音", null);
    static XIXUEGUI = new Role(25, "🦇", "德古娜", "吸血", "娜", null);
    static GUISHUSHI = new Role(26, "🌸", "诡术师", "诡术", "诡", null);
    static MAGICLION = new Role(27, "🦁", "魔法狮", "狮子", "狮", null);
    static LANGZAI = new Role(28, "🐺", "狼崽", "狼崽", "狼", null);
    static BZGIRL = new Role(29, "👧", "暴走女孩", "女孩", "暴", null);
    static PUMPKIN = new Role(30, "🎃", "南瓜伯爵", "南瓜", "南", null);
    static QUANBA = new Role(31, "🥊", "拳霸", "拳霸", "拳", null);
    static HONGZHAJI = new Role(32, "🐔", "轰炸鸡", "炸鸡", "鸡", null);
    static SANTAIZI = new Role(33, "🐉", "三太子", "龙三", "龙", null);
    static ZHADANKE = new Role(34, "💣", "炸弹客", "炸弹", "客", null);
    static HONGSANSAN = new Role(35, "🍄", "红伞伞", "蘑菇", "蘑", null);
    static WUKONG = new Role(36, "🐒", "悟空", "猴子", "猴", null);
    static ZHANAN = new Role(37, "🗡️", "光影战士", "扎男", "扎", null);
    static XIUNV = new Role(38, "👱‍♀️", "战斗修女", "修女", "修", null);
    static TONY = new Role(39, "💇‍♂️", "托尼老师", "托尼", "托", null);
    static RENZHE = new Role(40, "🎯", "李小忍", "忍者", "忍", null);
    static NUANYANG = new Role(41, "🐏", "暖羊卷卷", "肥羊", "羊", null);
    static QIANGWEI = new Role(42, "👩‍🦽", "蔷薇少女", "萍萍", "蔷", null);
    static LANLAN = new Role(43, "🤺", "剑姬岚岚", "岚岚", "岚", null);
    static KAIER = new Role(44, "🔨", "圣锤凯尔", "凯尔", "锤", null);
    static SHITOUREN = new Role(45, "⛰️", "岭南巨人", "石头", "石", null);
    static TIEMIAN = new Role(46, "🦞", "铁面骑士", "龙虾", "虾", null);
    static MIAOJIANG = new Role(47, "🐈", "喵法师", "喵酱", "喵", null);
    static MUSHI = new Role(48, "⛪", "圣光牧师", "牧师", "牧", null);
    static WUNV = new Role(49, "🕯", "圣灵巫女", "巫女", "巫", null);
    static LIANGLIANG = new Role(50, "🧜‍♀️", "靓靓鱼", "鱼女", "靓", null);
    static LAILAI = new Role(51, "🧜‍♂️", "癞癞鱼", "鱼男", "癞", null);
    static ZHANGYUGE = new Role(52, "🐙", "章鱼先生", "章鱼", "章", null);
    static HUABANTU = new Role(53, "🛹", "潮玩明星", "滑板", "兔", null);
    static NIUXIAOMANG = new Role(54, "🐮", "牛小莽", "小牛", "牛", null);
    static LANPANG = new Role(55, "🌏", "蓝胖", "蓝胖", "蓝", null);
    static JIANSHI = new Role(56, "🗡", "流浪剑士", "剑士", "剑", null);
    static JUNDUN = new Role(57, "🛡", "军团之盾", "军盾", "盾", null);
    static YOUFANG = new Role(58, "🌩️", "游方术士", "雷电", "电", null);
    static MOUSE = new Role(59, "🐭", "纽扣骑士", "老鼠", "鼠", null);
    static YEREN = new Role(60, "🧔", "灵域萨满", "野人", "野", null);
    static BAIGUJING = new Role(61, "🧞‍♀️", "白骨夫人", "白骨", "骨", null);
    static TUYA = new Role(62, "👨‍🎨", "涂鸦战士", "涂鸦", "涂", null);
    static YLPAPA = new Role(63, "👻", "幽灵帕帕", "幽灵", "幽", null);
    static YURRONG = new Role(64, "🐣", "羽绒绒", "鸡仔", "绒", null);
    static LINGOU = new Role(65, "🦸‍♀️", "萌心灵偶", "灵偶", "偶", null);
    static GOLDKING = new Role(66, "金", "金角大王", "金角", "金", null);
    static DUDU = new Role(67, "🐕️", "嘟嘟上校", "嘟嘟", "嘟", null);
    static GEJI = new Role(68, "👩‍🎤", "百变歌姬", "歌姬", "歌", null);
    static YUANSU = new Role(69, "🧙‍♀", "元素师", "元素", "元", null);
    static TANGSENG = new Role(70, "🧑🏼‍🦲", "金蝉子", "唐僧", "禅", null);


    // 角色类型分类：超肉、肉、杀、肉杀、乱碰、被乱碰、陷阱、标记、自动打(毒素、喷火等技能)、回血、复活/名刀、加速、减速、加护盾、加伤害、减伤害、反弹伤害
    // 肉，血量在最高血量(638) * 80% 以上，或带回血，假定 638 * 0.8 -> 510+；超肉，90%+ 638 * 0.8 -> 570+ 或带回血
    static BLOOD540 = [Role.NURSE.id, Role.CHUZI.id, Role.HONGZHAJI.id, Role.JIUWEIHU.id, Role.BAKE.id, Role.KUKU.id, Role.JUNDUN.id, Role.YINGYING.id,
    Role.HUAQIANJI.id, Role.MANWANG.id, Role.BAIGUJING.id, Role.CAPTAIN.id, Role.NUANYANG.id, Role.QIANGWEI.id, Role.JOKER.id,];
    static BLOOD500 = [Role.MOUSE.id, Role.LIANGLIANG.id, Role.SHITOUREN.id, Role.MAGICLION.id, Role.PUMPKIN.id, Role.BZGIRL.id, Role.KUILEI.id,
    Role.LANPANG.id, Role.YEREN.id, Role.SANTAIZI.id, Role.WUNV.id, Role.LULU.id, Role.XIUNV.id,
    ];

    // 超杀，单回合本体伤害+技能伤害 180+
    static SUPER_KILLER = [Role.DIANYIN.id, Role.ZHANAN.id, Role.HONGZHAJI.id, Role.HEIWA.id, Role.BZGIRL.id, Role.JIANGJIANG.id,
    Role.LINGLING.id, Role.KUILEI.id, Role.TIEMIAN.id, Role.YLPAPA.id,];
    // 杀，单回合本体伤害+技能伤害 90+
    static KILLER = [Role.RABBIT.id, Role.RENZHE.id, Role.SHITOUREN.id, Role.MAGICLION.id, Role.KAIER.id, Role.QUANBA.id, Role.YINGYING.id,
    Role.HUABANTU.id, Role.CAPTAIN.id, Role.XIXUEGUI.id, Role.SHUANGZI.id, Role.LANLAN.id, Role.LANGZAI.id, Role.LEIMENG.id, Role.SANTAIZI.id,
    Role.WUGEGE.id, Role.NUANYANG.id, Role.QIANGWEI.id, Role.LINGOU.id,
    ];

    // 肉杀，血量(算回血)在 500+，单回合能稳定打出伤害 140+ 计算超肉+肉集合与超杀+杀集合的交集
    static BLOOOD_KILLER = arrayIntersect(arrayUnionSet(this.BLOOD540, this.BLOOD500), arrayUnionSet(this.SUPER_KILLER, this.KILLER));

    // 乱碰
    static CHAOS_MAKER = [Role.DIANYIN.id, Role.BZGIRL.id, Role.SHUANGZI.id, Role.KUILEI.id, Role.LANPANG.id, Role.LELE.id, Role.WUGEGE.id,
    Role.WUKONG.id, Role.HEIWA.id, Role.HUABANTU.id, Role.KUKU.id, Role.YURRONG.id,
    ];
    // 被乱碰
    static CHAOS_CONSUMER = [Role.RABBIT.id, Role.DIANYIN.id, Role.ZHANAN.id, Role.RENZHE.id, Role.YOUXIA.id, Role.JOKER.id, Role.NUANYANG.id,
    Role.TUYA.id, Role.YINGYING.id, Role.HEIWA.id, Role.CAPTAIN.id, Role.XIXUEGUI.id, Role.WUNV.id, Role.ZHADANKE.id,
    ];
    // 克制乱碰
    static CHAOS_BLOCKS = [Role.PUMPKIN.id, Role.HONGZHAJI.id, Role.ZHANAN.id, Role.RENZHE.id, Role.BAIGUJING.id, Role.GUISHUSHI.id, Role.HUOWANG.id,
    Role.HONGSANSAN.id, Role.ZHADANKE.id, Role.HUAQIANJI.id, Role.YEREN.id, Role.TUYA.id,
    ];

    // 陷阱
    static TRAP_MAKER = [Role.BAIGUJING.id, Role.GUISHUSHI.id, Role.HUOWANG.id, Role.YEREN.id, Role.JOKER.id, Role.HONGSANSAN.id, Role.ZHADANKE.id,
    Role.TUYA.id, Role.TONY.id,
    ];

    // 自身标记
    static MARK_MAKER_SELF = [Role.BAIGUJING.id, Role.CAPTAIN.id, Role.LANLAN.id,
    Role.LANGZAI.id, Role.HUOWANG.id, Role.MIAOJIANG.id, Role.WUNV.id, Role.YOUFANG.id, Role.XIUNV.id, Role.YLPAPA.id,
    ];
    // 本队标记
    static MARK_MAKER = [Role.YINGYING.id, Role.HUAQIANJI.id, Role.JUNDUN.id,];

    // 自动打(毒素、喷火等技能)
    static AUTO_ATTACK = [Role.RABBIT.id, Role.LIANGLIANG.id, Role.LAILAI.id, Role.SHITOUREN.id, Role.MAGICLION.id, Role.DUODUO.id,
    Role.MIAOJIANG.id, Role.SANTAIZI.id,
    ];

    // 自身回血
    static BLOOD_BACK_SELF = [Role.CHUZI.id, Role.CAPTAIN.id, Role.XIXUEGUI.id, Role.NUANYANG.id,];
    // 本队回血（要么只给队友加、要么本队都加）
    static BLOOD_BACK = [Role.ZHANAN.id, Role.NURSE.id, Role.GUISHUSHI.id, Role.JIUWEIHU.id,];

    // 复活/名刀
    static REBIRTH = [Role.BAKE.id, Role.MUSHI.id,];

    // 加速辅助
    static FAST_MAKER = [Role.KUKU.id, Role.LULU.id,];
    // 给对手减速
    static SLOW_MAKER = [Role.HONGSANSAN.id, Role.ZHADANKE.id, Role.MANWANG.id,];

    // 自身加护盾
    static SHIELD_MAKER_SELF = [];
    // 本队加护盾（要么只给队友加、要么本队都加）
    static SHIELD_MAKER = [Role.JUNDUN.id, Role.LEIMENG.id, Role.LULU.id, Role.YINGYING.id,];

    // 自身攻击力加成
    static ADD_ATTACK_SELF = [Role.KAIER.id, Role.NIUXIAOMANG.id, Role.QUANBA.id, Role.HEIWA.id, Role.BZGIRL.id, Role.JIANGJIANG.id, Role.YLPAPA.id, Role.LINGLING.id,
    Role.SHUANGZI.id, Role.HUAQIANJI.id, Role.LANLAN.id, Role.LEIMENG.id, Role.MUSHI.id, Role.TUYA.id, Role.TONY.id, Role.WUGEGE.id, Role.ZHANGYUGE.id,
    ];
    // 本队攻击力加成（要么只给队友加、要么本队都加）
    static ADD_ATTACK = [Role.MANWANG.id, Role.TUYA.id, Role.TONY.id, Role.WUGEGE.id, Role.XIUNV.id,];

    // 减对手伤害
    static SUB_ATTACK = [Role.LELE.id, Role.TUYA.id,];

    // 反弹伤害
    static TRANS_ATTACK = [Role.BAKE.id, Role.NUANYANG.id, Role.HONGSANSAN.id, Role.ZHADANKE.id,];


    static maxRoleId = -1;

    static getRoleById(id) {
        for (let item in Role) {
            if (!Role[item] || Role[item].id === undefined || Role[item].id < 0) continue;
            if (Role[item].id === id) return Role[item];
        }
        return null;
    }

    static getFullNameById(id) {
        for (let item in Role) {
            if (!Role[item] || Role[item].id === undefined || Role[item].id < 0) continue;
            //console.log(item + ".id = " + Role[item].id);
            //console.log(item + ".fullName = " + Role[item].fullName);
            if (Role[item].id === id) return Role[item].fullName;
        }
        return "";
    }

    static getIdByFullName(fName) {
        for (let item in Role) {
            if (!Role[item] || Role[item].fullName === undefined || Role[item].id < 0) continue;
            if (Role[item].fullName === fName) return Role[item].id;
        }
        return -1;
    }

    static getFullNameByKeyWord(kw) {
        if (!kw) return "";
        for (let item in Role) {
            if (!Role[item] || !Role[item].fullName || !Role[item].shortName) continue;
            if (Role[item].fullName.includes(kw) || Role[item].shortName.includes(kw)) return Role[item].fullName;
        }
        return "";
    }

    static getIdsByFullNames(fNames) {
        let ids = [];
        for (let i in fNames) {
            //console.log(">>>> Role.getIdsByFullNames fName=" + fNames[i]);
            //console.log(">>>> Role.getIdsByFullNames fName is string=" + (typeof fNames[i] === "string"));
            for (let item in Role) {
                if (!Role[item] || Role[item].fullName === undefined || Role[item].id < 0) continue;
                if (Role[item].fullName === fNames[i]) ids.push(Role[item].id);
            }
        }
        return ids;
    }

    static getFullNamesByIds(ids) {
        let fNames = [];
        for (let i in ids) {
            //console.log(">>>> Role.getFullNamesByIds id=" + ids[i]);
            //console.log(">>>> Role.getFullNamesByIds id is number=" + (typeof ids[i] === "number"));
            for (let item in Role) {
                if (!Role[item] || Role[item].id === undefined || Role[item].id < 0) continue;
                if (Role[item].id === Number(ids[i])) fNames.push(Role[item].fullName);
            }
        }
        //console.log(">>>> Role.getFullNamesByIds fNames=" + fNames);
        return fNames;
    }

    static getShortNameById(id) {
        for (let item in Role) {
            if (!Role[item] || Role[item].id === undefined || Role[item].id < 0) continue;
            if (Role[item].id === id) return Role[item].shortName;
        }
        return "";
    }

    static getRoleIconById(id) {
        for (let item in Role) {
            if (!Role[item] || Role[item].id === undefined || Role[item].id < 0) continue;
            if (Role[item].id === id) return Role[item].icon;
        }
        return "";
    }

    static getRoleArray() {
        let roleArr = [];
        for (let item in Role) {
            if (!Role[item] || Role[item].id === undefined || Role[item].id < 0) continue;
            if (Role[item].id > -1 && Role[item].id != 10) roleArr.push(item);
        }
        return roleArr;
    }

    static getRandomRoleId() {
        if (this.maxRoleId >= 0) return fullCloseInt(0, this.maxRoleId);
        for (let item in Role) {
            if (!Role[item] || Role[item].id === undefined || Role[item].id < 0) continue;
            //console.log(">>>> maxRoleId=" + this.maxRoleId);
            if (Role[item].id > this.maxRoleId) this.maxRoleId = Role[item].id;
        }
        return fullCloseInt(0, this.maxRoleId);
    }

    // 初始化合适搭配，最合适搭配 + 其他合适搭配
    static initRoleCps() {
        /*
        // TODO 分类拼接没有自定义数组那么自由！总会出现不合适却在里面，合适的又不在的麻烦！大量拼接还会消耗更多性能和内存
        // 乱碰+本队回血+超肉+肉杀+本队攻击加成+本队加护盾-去重-去本身
        this.HEIWA.cps = arrayMinus(arrayUnique(this.CHAOS_MAKER.concat(this.BLOOD_BACK).concat(this.BLOOD540).concat(this.BLOOOD_KILLER).concat(this.ADD_ATTACK).concat(this.SHIELD_MAKER).concat(this.REBIRTH)), [Role.HEIWA.id, Role.DIANYIN.id]);
        // 加速辅助+对手减速+本队回血+本队标记+超肉+肉杀+本队攻击加成+本队加护盾+复活-去重-去本身
        this.JIANGJIANG.cps = arrayMinus(arrayUnique(this.FAST_MAKER.concat(this.SLOW_MAKER).concat(this.BLOOD_BACK).concat(this.MARK_MAKER).concat(this.BLOOD540).concat(this.BLOOOD_KILLER).concat(this.ADD_ATTACK).concat(this.SHIELD_MAKER).concat(this.REBIRTH)), [Role.JIANGJIANG.id]);
        // 超肉+本队回血+复活-去重-去本身
        this.DUODUO.cps = arrayMinus(arrayUnique(this.BLOOD540.concat(this.BLOOD_BACK).concat(this.REBIRTH)), [Role.DUODUO.id, Role.KUKU.id, Role.YINGYING.id, Role.MANWANG.id, Role.BAIGUJING.id]);
        // 被乱碰-去重-去本身
        this.KUILEI.cps = arrayMinus(arrayUnique(this.CHAOS_CONSUMER), [Role.KUILEI.id]);
        // 自动打+超杀-去重-去本身
        this.BAKE.cps = arrayMinus(arrayUnique([Role.XIUNV.id].concat(this.SUPER_KILLER).concat(this.AUTO_ATTACK)), [Role.BAKE.id]);
        */
        this.HEIWA.cps = [Role.KUKU.id, Role.LELE.id, Role.LULU.id, Role.JIUWEIHU.id, Role.NURSE.id, Role.CHUZI.id, Role.TONY.id, Role.SHUANGZI.id, Role.WUGEGE.id, Role.WUKONG.id, Role.HUABANTU.id, Role.LANPANG.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id];
        this.JIANGJIANG.cps = [Role.KUKU.id, Role.LULU.id, Role.JIUWEIHU.id, Role.NURSE.id, Role.CHUZI.id, Role.MANWANG.id, Role.HUAQIANJI.id, Role.BAKE.id, Role.YINGYING.id, Role.WUGEGE.id, Role.ZHADANKE.id, Role.HONGSANSAN.id, Role.XIXUEGUI.id, Role.SANTAIZI.id];
        this.DUODUO.cps = [Role.HUAQIANJI.id, Role.BAKE.id, Role.CHUZI.id, Role.JOKER.id, Role.NURSE.id, Role.JIUWEIHU.id, Role.HONGZHAJI.id, Role.MIAOJIANG.id, Role.MUSHI.id];
        this.KUILEI.cps = [Role.YINGYING.id, Role.JOKER.id, Role.LINGLING.id, Role.RABBIT.id, Role.DIANYIN.id, Role.YOUXIA.id, Role.ZHANAN.id, Role.XIXUEGUI.id, Role.ZHADANKE.id, Role.YEREN.id, Role.BAIGUJING.id];
        this.BAKE.cps = [Role.DUODUO.id, Role.LINGLING.id, Role.RABBIT.id, Role.WUGEGE.id, Role.DIANYIN.id, Role.XIUNV.id, Role.JIANGJIANG.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id];
        this.LULU.cps = [Role.JIANGJIANG.id, Role.HEIWA.id, Role.TIEMIAN.id, Role.CAPTAIN.id, Role.SANTAIZI.id];
        this.KUKU.cps = [Role.HEIWA.id, Role.JIANGJIANG.id, Role.RABBIT.id, Role.DIANYIN.id, Role.HUOWANG.id, Role.TIEMIAN.id, Role.ZHANAN.id];
        this.YINGYING.cps = [Role.LELE.id, Role.CAPTAIN.id, Role.KUILEI.id, Role.SHUANGZI.id, Role.WUGEGE.id, Role.LEIMENG.id, Role.JIANGJIANG.id, Role.BZGIRL.id, Role.SANTAIZI.id];
        this.JIUWEIHU.cps = [Role.JIANGJIANG.id, Role.HEIWA.id, Role.ZHANAN.id, Role.DUODUO.id, Role.NURSE.id, Role.CHUZI.id, Role.HONGZHAJI.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id];
        this.SHUANGZI.cps = [Role.JOKER.id, Role.RABBIT.id, Role.YOUXIA.id, Role.HEIWA.id, Role.YINGYING.id, Role.HUOWANG.id, Role.DIANYIN.id, Role.LINGLING.id, Role.LANGZAI.id, Role.ZHANAN.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.ZHADANKE.id, Role.SANTAIZI.id, Role.YEREN.id, Role.BAIGUJING.id];
        this.X.cps = [Role.JOKER.id, Role.WUGEGE.id, Role.RABBIT.id, Role.SHUANGZI.id, Role.KUILEI.id, Role.LELE.id, Role.LEIMENG.id, Role.YINGYING.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id, Role.YEREN.id, Role.BAIGUJING.id]; // 自定义角色
        this.YOUXIA.cps = [Role.SHUANGZI.id, Role.ZHANAN.id, Role.LELE.id, Role.KUILEI.id, Role.WUGEGE.id, Role.WUKONG.id, Role.HUABANTU.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id];
        this.CHUZI.cps = [Role.HEIWA.id, Role.DIANYIN.id, Role.DUODUO.id, Role.NURSE.id, Role.JIUWEIHU.id, Role.MAGICLION.id, Role.YINGYING.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id];
        this.HUAQIANJI.cps = [Role.DUODUO.id, Role.JIANGJIANG.id, Role.NURSE.id, Role.JIUWEIHU.id, Role.RABBIT.id, Role.DIANYIN.id, Role.PUMPKIN.id, Role.HUOWANG.id, Role.QUANBA.id, Role.MUSHI.id];
        this.WUGEGE.cps = [Role.JOKER.id, Role.HEIWA.id, Role.LINGLING.id, Role.YOUXIA.id, Role.YINGYING.id, Role.JIANGJIANG.id, Role.ZHANAN.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id, Role.YEREN.id, Role.BAIGUJING.id];
        this.JOKER.cps = [Role.WUGEGE.id, Role.RABBIT.id, Role.SHUANGZI.id, Role.KUILEI.id, Role.LELE.id, Role.DIANYIN.id, Role.YINGYING.id, Role.LINGLING.id, Role.DUODUO.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.ZHADANKE.id, Role.XIUNV.id, Role.SANTAIZI.id, Role.YEREN.id, Role.BAIGUJING.id];
        this.RABBIT.cps = [Role.LELE.id, Role.JOKER.id, Role.BAKE.id, Role.KUILEI.id, Role.WUKONG.id, Role.SHUANGZI.id, Role.KUKU.id, Role.MAGICLION.id, Role.HUABANTU.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id];
        this.NURSE.cps = [Role.HEIWA.id, Role.JIANGJIANG.id, Role.HUAQIANJI.id, Role.KAIER.id, Role.TIEMIAN.id, Role.DUODUO.id, Role.CHUZI.id, Role.JIUWEIHU.id, Role.LEIMENG.id, Role.BZGIRL.id];
        this.CAPTAIN.cps = [Role.YINGYING.id, Role.CHUZI.id, Role.SHUANGZI.id, Role.LELE.id, Role.KUILEI.id, Role.LULU.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id];
        this.LELE.cps = [Role.HEIWA.id, Role.RABBIT.id, Role.JOKER.id, Role.DIANYIN.id, Role.ZHANAN.id, Role.YINGYING.id, Role.CAPTAIN.id, Role.HUOWANG.id, Role.YOUXIA.id, Role.LANGZAI.id, Role.LINGLING.id, Role.TIEMIAN.id, Role.ZHADANKE.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id, Role.YEREN.id, Role.BAIGUJING.id];
        this.MANWANG.cps = [Role.RABBIT.id, Role.HEIWA.id, Role.JIANGJIANG.id, Role.LELE.id, Role.DIANYIN.id];
        this.LINGLING.cps = [Role.BAKE.id, Role.JOKER.id, Role.YINGYING.id, Role.KUILEI.id, Role.CHUZI.id, Role.WUGEGE.id, Role.LEIMENG.id, Role.LANLAN.id, Role.JIUWEIHU.id, Role.GUISHUSHI.id, Role.BZGIRL.id, Role.SANTAIZI.id, Role.YEREN.id, Role.BAIGUJING.id];
        this.HUOWANG.cps = [Role.LELE.id, Role.SHUANGZI.id, Role.JOKER.id, Role.GUISHUSHI.id, Role.YINGYING.id, Role.KUKU.id, Role.MAGICLION.id, Role.PUMPKIN.id, Role.HUABANTU.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id, Role.YEREN.id, Role.BAIGUJING.id];
        this.LEIMENG.cps = [Role.HEIWA.id, Role.JOKER.id, Role.DIANYIN.id, Role.YINGYING.id, Role.JIUWEIHU.id, Role.RABBIT.id, Role.HUOWANG.id, Role.GUISHUSHI.id, Role.BZGIRL.id, Role.SANTAIZI.id, Role.YEREN.id, Role.BAIGUJING.id];
        this.DIANYIN.cps = [Role.LELE.id, Role.SHUANGZI.id, Role.KUILEI.id, Role.JOKER.id, Role.CHUZI.id, Role.QUANBA.id, Role.MAGICLION.id, Role.KUKU.id, Role.LEIMENG.id, Role.HUABANTU.id, Role.BZGIRL.id, Role.SANTAIZI.id];
        this.XIXUEGUI.cps = [Role.CHUZI.id, Role.JOKER.id, Role.BAKE.id, Role.LELE.id, Role.KUILEI.id, Role.SHUANGZI.id, Role.YINGYING.id, Role.HUABANTU.id, Role.JIANGJIANG.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id];
        this.GUISHUSHI.cps = [Role.LELE.id, Role.SHUANGZI.id, Role.JOKER.id, Role.HUOWANG.id, Role.YINGYING.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id, Role.YEREN.id, Role.BAIGUJING.id];
        this.MAGICLION.cps = [Role.CHUZI.id, Role.SHITOUREN.id, Role.PUMPKIN.id, Role.DIANYIN.id, Role.JOKER.id, Role.BAKE.id, Role.RABBIT.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id];
        this.LANGZAI.cps = [Role.CHUZI.id, Role.JOKER.id, Role.BAKE.id, Role.YINGYING.id, Role.KUILEI.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id, Role.YEREN.id, Role.BAIGUJING.id];
        this.BZGIRL.cps = [Role.ZHANAN.id, Role.CHUZI.id, Role.JOKER.id, Role.BAKE.id, Role.YINGYING.id, Role.KUILEI.id, Role.SHUANGZI.id, Role.LELE.id, Role.DIANYIN.id, Role.RABBIT.id, Role.LANGZAI.id, Role.WUGEGE.id, Role.PUMPKIN.id, Role.LEIMENG.id, Role.SANTAIZI.id, Role.YEREN.id, Role.BAIGUJING.id];
        this.PUMPKIN.cps = [Role.HUAQIANJI.id, Role.MAGICLION.id, Role.QUANBA.id, Role.GUISHUSHI.id, Role.HUOWANG.id, Role.LELE.id, Role.SHUANGZI.id, Role.RABBIT.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id, Role.YEREN.id, Role.BAIGUJING.id];
        this.QUANBA.cps = [Role.HUAQIANJI.id, Role.CHUZI.id, Role.PUMPKIN.id, Role.WUGEGE.id, Role.LELE.id, Role.SHUANGZI.id, Role.HUOWANG.id, Role.DIANYIN.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id, Role.YEREN.id, Role.BAIGUJING.id];
        this.HONGZHAJI.cps = [Role.JIUWEIHU.id, Role.HUAQIANJI.id, Role.DUODUO.id, Role.WUGEGE.id, Role.RABBIT.id, Role.YOUXIA.id, Role.CHUZI.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.YEREN.id, Role.BAIGUJING.id];
        this.SANTAIZI.cps = [Role.JOKER.id, Role.DIANYIN.id, Role.ZHANAN.id, Role.LELE.id, Role.WUGEGE.id, Role.RABBIT.id, Role.YOUXIA.id, Role.CHUZI.id, Role.HUOWANG.id, Role.GUISHUSHI.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.YEREN.id, Role.BAIGUJING.id];
        this.ZHADANKE.cps = [Role.HONGSANSAN.id, Role.YINGYING.id, Role.JIANGJIANG.id, Role.LELE.id, Role.WUGEGE.id, Role.SHUANGZI.id, Role.HUOWANG.id, Role.GUISHUSHI.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id, Role.YEREN.id];
        this.HONGSANSAN.cps = [Role.ZHADANKE.id, Role.PUMPKIN.id, Role.JIANGJIANG.id, Role.HUOWANG.id, Role.GUISHUSHI.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id, Role.YEREN.id];
        this.WUKONG.cps = [Role.DIANYIN.id, Role.RABBIT.id, Role.HEIWA.id, Role.XIUNV.id, Role.PUMPKIN.id, Role.ZHANAN.id, Role.HUOWANG.id, Role.GUISHUSHI.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.YEREN.id, Role.BAIGUJING.id];
        this.ZHANAN.cps = [Role.YOUXIA.id, Role.WUGEGE.id, Role.SHUANGZI.id, Role.WUKONG.id, Role.JIUWEIHU.id, Role.ZHANGYUGE.id, Role.HUABANTU.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id, Role.YEREN.id, Role.BAIGUJING.id];
        this.XIUNV.cps = [Role.BAKE.id, Role.WUKONG.id, Role.PUMPKIN.id, Role.WUGEGE.id, Role.HUOWANG.id, Role.GUISHUSHI.id, Role.ZHANGYUGE.id, Role.HUABANTU.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id, Role.YEREN.id, Role.BAIGUJING.id];
        this.TONY.cps = [Role.HEIWA.id, Role.WUKONG.id, Role.LELE.id, Role.SHUANGZI.id, Role.WUGEGE.id, Role.HUOWANG.id, Role.GUISHUSHI.id, Role.KUKU.id, Role.JIANGJIANG.id, Role.HUABANTU.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id];
        this.RENZHE.cps = [Role.JOKER.id, Role.WUKONG.id, Role.LELE.id, Role.SHUANGZI.id, Role.HUABANTU.id, Role.PUMPKIN.id, Role.WUGEGE.id, Role.YOUXIA.id, Role.KUKU.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id];
        this.NUANYANG.cps = [Role.JOKER.id, Role.YINGYING.id, Role.QIANGWEI.id, Role.CHUZI.id, Role.WUKONG.id, Role.PUMPKIN.id, Role.WUGEGE.id, Role.YOUXIA.id, Role.HUABANTU.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id];
        this.QIANGWEI.cps = [Role.JOKER.id, Role.YINGYING.id, Role.NUANYANG.id, Role.CHUZI.id, Role.WUKONG.id, Role.PUMPKIN.id, Role.WUGEGE.id, Role.YOUXIA.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id];
        this.LANLAN.cps = [Role.JOKER.id, Role.YINGYING.id, Role.LINGLING.id, Role.NUANYANG.id, Role.QIANGWEI.id, Role.CHUZI.id, Role.WUKONG.id, Role.PUMPKIN.id, Role.WUGEGE.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id, Role.YEREN.id, Role.BAIGUJING.id];
        this.KAIER.cps = [Role.NURSE.id, Role.JIUWEIHU.id, Role.JOKER.id, Role.QUANBA.id, Role.NUANYANG.id, Role.QIANGWEI.id, Role.CHUZI.id, Role.WUKONG.id, Role.PUMPKIN.id, Role.WUGEGE.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id, Role.YEREN.id, Role.BAIGUJING.id];
        this.SHITOUREN.cps = [Role.MAGICLION.id, Role.XIUNV.id, Role.MIAOJIANG.id, Role.NUANYANG.id, Role.QIANGWEI.id, Role.CHUZI.id, Role.PUMPKIN.id, Role.WUGEGE.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id, Role.YEREN.id, Role.BAIGUJING.id];
        this.TIEMIAN.cps = [Role.LULU.id, Role.NURSE.id, Role.JIUWEIHU.id, Role.LELE.id, Role.SHUANGZI.id, Role.CHUZI.id, Role.WUKONG.id, Role.PUMPKIN.id, Role.WUGEGE.id, Role.KUKU.id, Role.HUABANTU.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id];
        this.MIAOJIANG.cps = [Role.MAGICLION.id, Role.SHITOUREN.id, Role.NURSE.id, Role.JIUWEIHU.id, Role.DUODUO.id, Role.SHUANGZI.id, Role.CHUZI.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id];
        this.MUSHI.cps = [Role.KAIER.id, Role.QUANBA.id, Role.HUAQIANJI.id, Role.LELE.id, Role.SHUANGZI.id, Role.CHUZI.id, Role.PUMPKIN.id, Role.DIANYIN.id, Role.RABBIT.id, Role.HONGZHAJI.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id, Role.YEREN.id, Role.BAIGUJING.id];
        this.WUNV.cps = [Role.YINGYING.id, Role.CAPTAIN.id, Role.LELE.id, Role.SHUANGZI.id, Role.CHUZI.id, Role.WUKONG.id, Role.PUMPKIN.id, Role.JIANGJIANG.id, Role.HUOWANG.id, Role.GUISHUSHI.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id, Role.YEREN.id, Role.BAIGUJING.id];
        this.LIANGLIANG.cps = [Role.LAILAI.id, Role.MAGICLION.id, Role.BAKE.id, Role.NUANYANG.id, Role.QIANGWEI.id, Role.CAPTAIN.id, Role.CHUZI.id, Role.LEIMENG.id, Role.BZGIRL.id];
        this.LAILAI.cps = [Role.LIANGLIANG.id, Role.MAGICLION.id, Role.BAKE.id, Role.NUANYANG.id, Role.QIANGWEI.id, Role.CAPTAIN.id, Role.CHUZI.id, Role.LEIMENG.id, Role.BZGIRL.id];
        this.ZHANGYUGE.cps = [Role.HUOWANG.id, Role.GUISHUSHI.id, Role.DIANYIN.id, Role.RABBIT.id, Role.NUANYANG.id, Role.QIANGWEI.id, Role.CAPTAIN.id, Role.YINGYING.id, Role.PUMPKIN.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id, Role.YEREN.id, Role.BAIGUJING.id];
        this.HUABANTU.cps = [Role.HUOWANG.id, Role.GUISHUSHI.id, Role.HEIWA.id, Role.DIANYIN.id, Role.RABBIT.id, Role.NUANYANG.id, Role.QIANGWEI.id, Role.CAPTAIN.id, Role.YINGYING.id, Role.LINGLING.id, Role.PUMPKIN.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id, Role.YEREN.id, Role.BAIGUJING.id];
        this.NIUXIAOMANG.cps = [Role.HUOWANG.id, Role.GUISHUSHI.id, Role.JOKER.id, Role.DIANYIN.id, Role.RABBIT.id, Role.NUANYANG.id, Role.QIANGWEI.id, Role.CAPTAIN.id, Role.YINGYING.id, Role.LINGLING.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id, Role.YEREN.id, Role.BAIGUJING.id];
        this.LANPANG.cps = [Role.HUOWANG.id, Role.GUISHUSHI.id, Role.PUMPKIN.id, Role.HEIWA.id, Role.DIANYIN.id, Role.RABBIT.id, Role.XIXUEGUI.id, Role.NUANYANG.id, Role.QIANGWEI.id, Role.CAPTAIN.id, Role.YINGYING.id, Role.LINGLING.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id, Role.YEREN.id, Role.BAIGUJING.id];
        this.JIANSHI.cps = [Role.HUOWANG.id, Role.GUISHUSHI.id, Role.NUANYANG.id, Role.QIANGWEI.id, Role.CAPTAIN.id, Role.JIUWEIHU.id, Role.NURSE.id, Role.CHUZI.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id];
        this.JUNDUN.cps = [Role.DIANYIN.id, Role.RABBIT.id, Role.HEIWA.id, Role.ZHANAN.id, Role.JIANGJIANG.id, Role.NUANYANG.id, Role.QIANGWEI.id, Role.CAPTAIN.id, Role.LANLAN.id, Role.LINGLING.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id];
        this.YOUFANG.cps = [Role.JOKER.id, Role.HUOWANG.id, Role.NUANYANG.id, Role.QIANGWEI.id, Role.CAPTAIN.id, Role.CHUZI.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id];
        this.MOUSE.cps = [Role.DIANYIN.id, Role.RABBIT.id, Role.WUGEGE.id, Role.HUOWANG.id, Role.GUISHUSHI.id, Role.JIANGJIANG.id, Role.NUANYANG.id, Role.CAPTAIN.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id];
        this.YEREN.cps = [Role.DIANYIN.id, Role.RABBIT.id, Role.WUGEGE.id, Role.WUKONG.id, Role.LANPANG.id, Role.HUOWANG.id, Role.GUISHUSHI.id, Role.PUMPKIN.id, Role.LELE.id, Role.SHUANGZI.id, Role.HUABANTU.id, Role.LANPANG.id, Role.MAGICLION.id, Role.JIANGJIANG.id, Role.NUANYANG.id, Role.CAPTAIN.id, Role.XIUNV.id, Role.ZHADANKE.id, Role.HONGSANSAN.id, Role.LEIMENG.id, Role.BZGIRL.id, Role.SANTAIZI.id];
        this.BAIGUJING.cps = [Role.WUGEGE.id, Role.WUKONG.id, Role.LANPANG.id, Role.HUOWANG.id, Role.GUISHUSHI.id, Role.PUMPKIN.id, Role.LELE.id, Role.SHUANGZI.id, Role.KUILEI.id, Role.HUABANTU.id, Role.NIUXIAOMANG.id, Role.BZGIRL.id, Role.SANTAIZI.id, Role.YEREN.id];
        this.TUYA.cps = [Role.JIUWEIHU.id, Role.NURSE.id, Role.ZHANAN.id, Role.WUGEGE.id, Role.WUKONG.id, Role.LANPANG.id, Role.HUOWANG.id, Role.GUISHUSHI.id, Role.PUMPKIN.id, Role.LELE.id, Role.SHUANGZI.id, Role.KUILEI.id, Role.HUABANTU.id, Role.NIUXIAOMANG.id, Role.BZGIRL.id, Role.SANTAIZI.id, Role.YEREN.id];
        this.YLPAPA.cps = [Role.MANWANG.id, Role.KUKU.id, Role.LULU.id, Role.HUAQIANJI.id, Role.MUSHI.id, Role.DUODUO.id, Role.JIANGJIANG.id, Role.JIANSHI.id, Role.WUGEGE.id, Role.PUMPKIN.id, Role.CAPTAIN.id, Role.ZHADANKE.id];
        this.YURRONG.cps = [Role.DUODUO.id, Role.ZHANAN.id, Role.DIANYIN.id, Role.RABBIT.id, Role.HEIWA.id, Role.HUOWANG.id, Role.GUISHUSHI.id, Role.YEREN.id, Role.PUMPKIN.id, Role.HUAQIANJI.id, Role.YINGYING.id, Role.CAPTAIN.id, Role.JOKER.id, Role.ZHADANKE.id];
        this.LINGOU.cps = [Role.RABBIT.id, Role.DIANYIN.id, Role.HEIWA.id, Role.ZHANAN.id, Role.HUOWANG.id, Role.GUISHUSHI.id, Role.YEREN.id, Role.PUMPKIN.id, Role.YINGYING.id, Role.CAPTAIN.id, Role.JOKER.id, Role.ZHADANKE.id];
        this.GOLDKING.cps = [Role.RABBIT.id, Role.DIANYIN.id, Role.HEIWA.id, Role.LINGLING.id, Role.QUANBA.id, Role.CAPTAIN.id, Role.JOKER.id, Role.ZHADANKE.id];
        this.DUDU.cps = [Role.JUNDUN.id, Role.WUNV.id, Role.XIUNV.id, Role.CHUZI.id, Role.LEIMENG.id, Role.YEREN.id, Role.CAPTAIN.id, Role.JOKER.id, Role.TUYA.id, Role.LINGOU.id, Role.BAKE.id, Role.JIUWEIHU.id, Role.NUANYANG, Role.XIXUEGUI.id.id];
        this.GEJI.cps = [Role.LELE.id, Role.SHUANGZI.id, Role.HEIWA.id, Role.RABBIT.id, Role.DIANYIN.id, Role.RENZHE.id, Role.XIXUEGUI.id];
        this.YUANSU.cps = [Role.LELE.id, Role.SHUANGZI.id, Role.HEIWA.id, Role.RABBIT.id, Role.DIANYIN.id, Role.RENZHE.id, Role.XIXUEGUI.id, Role.WUGEGE.id, Role.KUILEI.id];
        this.TANGSENG.cps = [Role.HONGSANSAN.id, Role.LINGOU.id, Role.KUILEI.id, Role.HUOWANG.id, Role.GUISHUSHI.id, Role.YOUFANG.id, Role.MANWANG.id, Role.PUMPKIN.id, Role.JUNDUN.id, Role.MOUSE.id, Role.NUANYANG.id, Role.QIANGWEI.id, Role.HONGZHAJI.id, Role.BZGIRL.id, Role.CAPTAIN.id];

    }

}
// 设置主角常用搭配
Role.initRoleCps();


// 常用大奖赛搭配类
class RegularlyCollocation {

    constructor(id, group) {
        this.id = id;
        this.group = group;
    }

    // 🥚、🧟、❄️、🤡、8g 等TOP角色大奖赛常用组合，每个分配一百万个id
    // 🥚
    static group1000000 = new RegularlyCollocation(1000000, [Role.DUODUO.id, Role.BAKE.id]);
    static group1000001 = new RegularlyCollocation(1000001, [Role.DUODUO.id, Role.BAKE.id]);
    static group1000002 = new RegularlyCollocation(1000002, [Role.DUODUO.id, Role.HUAQIANJI.id]);
    static group1000003 = new RegularlyCollocation(1000003, [Role.DUODUO.id, Role.CHUZI.id]);
    static group1000004 = new RegularlyCollocation(1000004, [Role.DUODUO.id, Role.JOKER.id]);
    static group1000005 = new RegularlyCollocation(1000005, [Role.DUODUO.id, Role.HONGZHAJI.id]);
    static group1000006 = new RegularlyCollocation(1000006, [Role.DUODUO.id, Role.MIAOJIANG.id]);
    static group1000007 = new RegularlyCollocation(1000007, [Role.DUODUO.id, Role.NURSE.id]);
    static group1000008 = new RegularlyCollocation(1000008, [Role.DUODUO.id, Role.JIUWEIHU.id]);
    static group1000009 = new RegularlyCollocation(1000009, [Role.DUODUO.id, Role.MUSHI.id]);

    // 🧟
    static group2000000 = new RegularlyCollocation(2000000, [Role.JIANGJIANG.id, Role.MANWANG.id]);
    static group2000001 = new RegularlyCollocation(2000001, [Role.JIANGJIANG.id, Role.LULU.id]);
    static group2000002 = new RegularlyCollocation(2000002, [Role.JIANGJIANG.id, Role.KUKU.id]);
    static group2000003 = new RegularlyCollocation(2000003, [Role.JIANGJIANG.id, Role.JIUWEIHU.id]);
    static group2000004 = new RegularlyCollocation(2000004, [Role.JIANGJIANG.id, Role.NURSE.id]);
    static group2000005 = new RegularlyCollocation(2000005, [Role.JIANGJIANG.id, Role.BAKE.id]);
    static group2000006 = new RegularlyCollocation(2000006, [Role.JIANGJIANG.id, Role.YINGYING.id]);
    static group2000007 = new RegularlyCollocation(2000007, [Role.JIANGJIANG.id, Role.WUGEGE.id]);
    static group2000008 = new RegularlyCollocation(2000008, [Role.JIANGJIANG.id, Role.HUAQIANJI.id]);
    static group2000009 = new RegularlyCollocation(2000009, [Role.JIANGJIANG.id, Role.MANWANG.id]);
    static group2000010 = new RegularlyCollocation(2000010, [Role.JIANGJIANG.id, Role.ZHADANKE.id]);
    static group2000011 = new RegularlyCollocation(2000011, [Role.JIANGJIANG.id, Role.HONGSANSAN.id]);
    static group2000012 = new RegularlyCollocation(2000012, [Role.JIANGJIANG.id, Role.SANTAIZI.id]);

    // ❄️
    static group3000000 = new RegularlyCollocation(3000000, [Role.YINGYING.id, Role.CAPTAIN.id]);
    static group3000001 = new RegularlyCollocation(3000001, [Role.YINGYING.id, Role.LELE.id]);
    static group3000002 = new RegularlyCollocation(3000002, [Role.YINGYING.id, Role.CAPTAIN.id]);
    static group3000003 = new RegularlyCollocation(3000003, [Role.YINGYING.id, Role.KUILEI.id]);
    static group3000004 = new RegularlyCollocation(3000004, [Role.YINGYING.id, Role.WUGEGE.id]);
    static group3000005 = new RegularlyCollocation(3000005, [Role.YINGYING.id, Role.LINGLING.id]);
    static group3000006 = new RegularlyCollocation(3000006, [Role.YINGYING.id, Role.HUOWANG.id]);
    static group3000007 = new RegularlyCollocation(3000007, [Role.YINGYING.id, Role.LEIMENG.id]);
    static group3000008 = new RegularlyCollocation(3000008, [Role.YINGYING.id, Role.BZGIRL.id]);
    static group3000009 = new RegularlyCollocation(3000009, [Role.YINGYING.id, Role.XIXUEGUI.id]);
    static group3000010 = new RegularlyCollocation(3000010, [Role.YINGYING.id, Role.SHUANGZI.id]);
    static group3000011 = new RegularlyCollocation(3000011, [Role.YINGYING.id, Role.JIANGJIANG.id]);
    static group3000012 = new RegularlyCollocation(3000012, [Role.YINGYING.id, Role.ZHADANKE.id]);
    static group3000013 = new RegularlyCollocation(3000013, [Role.YINGYING.id, Role.HONGSANSAN.id]);
    static group3000014 = new RegularlyCollocation(3000014, [Role.YINGYING.id, Role.SANTAIZI.id]);

    // 🤡
    static group4000000 = new RegularlyCollocation(4000000, [Role.JOKER.id, Role.KUILEI.id]);
    static group4000001 = new RegularlyCollocation(4000001, [Role.JOKER.id, Role.WUGEGE.id]);
    static group4000002 = new RegularlyCollocation(4000002, [Role.JOKER.id, Role.RABBIT.id]);
    static group4000003 = new RegularlyCollocation(4000003, [Role.JOKER.id, Role.LELE.id]);
    static group4000004 = new RegularlyCollocation(4000004, [Role.JOKER.id, Role.SHUANGZI.id]);
    static group4000005 = new RegularlyCollocation(4000005, [Role.JOKER.id, Role.KUILEI.id]);
    static group4000006 = new RegularlyCollocation(4000006, [Role.JOKER.id, Role.LEIMENG.id]);
    static group4000007 = new RegularlyCollocation(4000007, [Role.JOKER.id, Role.GUISHUSHI.id]);
    static group4000008 = new RegularlyCollocation(4000008, [Role.JOKER.id, Role.DIANYIN.id]);
    static group4000009 = new RegularlyCollocation(4000009, [Role.JOKER.id, Role.XIXUEGUI.id]);
    static group4000010 = new RegularlyCollocation(4000010, [Role.JOKER.id, Role.LANGZAI.id]);
    static group4000011 = new RegularlyCollocation(4000011, [Role.JOKER.id, Role.BZGIRL.id]);
    static group4000012 = new RegularlyCollocation(4000012, [Role.JOKER.id, Role.HUOWANG.id]);
    static group4000013 = new RegularlyCollocation(4000013, [Role.JOKER.id, Role.XIUNV.id]);
    static group4000014 = new RegularlyCollocation(4000014, [Role.JOKER.id, Role.ZHADANKE.id]);
    static group4000015 = new RegularlyCollocation(4000015, [Role.JOKER.id, Role.HONGSANSAN.id]);
    static group4000016 = new RegularlyCollocation(4000016, [Role.JOKER.id, Role.MAGICLION.id]);
    static group4000017 = new RegularlyCollocation(4000017, [Role.JOKER.id, Role.SANTAIZI.id]);
    static group4000018 = new RegularlyCollocation(4000018, [Role.JOKER.id, Role.YINGYING.id]);
    static group4000019 = new RegularlyCollocation(4000019, [Role.JOKER.id, Role.LINGLING.id]);
    static group4000020 = new RegularlyCollocation(4000020, [Role.JOKER.id, Role.LANLAN.id]);
    static group4000021 = new RegularlyCollocation(4000021, [Role.JOKER.id, Role.HUABANTU.id]);
    static group4000022 = new RegularlyCollocation(4000022, [Role.JOKER.id, Role.BAIGUJING.id]);
    static group4000023 = new RegularlyCollocation(4000023, [Role.JOKER.id, Role.NUANYANG.id]);
    static group4000024 = new RegularlyCollocation(4000024, [Role.JOKER.id, Role.QIANGWEI.id]);
    static group4000025 = new RegularlyCollocation(4000025, [Role.JOKER.id, Role.ZHANAN.id]);

    // 8g
    static group5000000 = new RegularlyCollocation(5000000, [Role.BAKE.id, Role.DUODUO.id]);
    static group5000001 = new RegularlyCollocation(5000001, [Role.BAKE.id, Role.WUGEGE.id]);
    static group5000002 = new RegularlyCollocation(5000002, [Role.BAKE.id, Role.RABBIT.id]);
    static group5000003 = new RegularlyCollocation(5000003, [Role.BAKE.id, Role.LINGLING.id]);
    static group5000004 = new RegularlyCollocation(5000004, [Role.BAKE.id, Role.DIANYIN.id]);
    static group5000005 = new RegularlyCollocation(5000005, [Role.BAKE.id, Role.XIXUEGUI.id]);
    static group5000006 = new RegularlyCollocation(5000006, [Role.BAKE.id, Role.LEIMENG.id]);
    static group5000007 = new RegularlyCollocation(5000007, [Role.BAKE.id, Role.BZGIRL.id]);
    static group5000008 = new RegularlyCollocation(5000008, [Role.BAKE.id, Role.LANGZAI.id]);
    static group5000009 = new RegularlyCollocation(5000009, [Role.BAKE.id, Role.MAGICLION.id]);
    static group5000010 = new RegularlyCollocation(5000010, [Role.BAKE.id, Role.XIUNV.id]);
    static group5000011 = new RegularlyCollocation(5000011, [Role.BAKE.id, Role.LANLAN.id]);
    static group5000012 = new RegularlyCollocation(5000012, [Role.BAKE.id, Role.SANTAIZI.id]);

    // 🚢
    static group6000000 = new RegularlyCollocation(6000000, [Role.CAPTAIN.id, Role.YINGYING.id]);
    static group6000001 = new RegularlyCollocation(6000001, [Role.CAPTAIN.id, Role.BZGIRL.id]);
    static group6000002 = new RegularlyCollocation(6000002, [Role.CAPTAIN.id, Role.JOKER.id]);
    static group6000003 = new RegularlyCollocation(6000003, [Role.CAPTAIN.id, Role.JIANGJIANG.id]);
    static group6000004 = new RegularlyCollocation(6000004, [Role.CAPTAIN.id, Role.CHUZI.id]);
    static group6000005 = new RegularlyCollocation(6000005, [Role.CAPTAIN.id, Role.ZHANAN.id]);
    static group6000006 = new RegularlyCollocation(6000006, [Role.CAPTAIN.id, Role.HONGZHAJI.id]);
    static group6000007 = new RegularlyCollocation(6000007, [Role.CAPTAIN.id, Role.NUANYANG.id]);
    static group6000008 = new RegularlyCollocation(6000008, [Role.CAPTAIN.id, Role.QIANGWEI.id]);

    // 双子
    static group7000000 = new RegularlyCollocation(7000000, [Role.SHUANGZI.id, Role.JOKER.id]);
    static group7000001 = new RegularlyCollocation(7000001, [Role.SHUANGZI.id, Role.DIANYIN.id]);
    static group7000002 = new RegularlyCollocation(7000002, [Role.SHUANGZI.id, Role.RABBIT.id]);
    static group7000003 = new RegularlyCollocation(7000003, [Role.SHUANGZI.id, Role.HEIWA.id]);
    static group7000004 = new RegularlyCollocation(7000004, [Role.SHUANGZI.id, Role.YOUXIA.id]);
    static group7000005 = new RegularlyCollocation(7000005, [Role.SHUANGZI.id, Role.ZHANAN.id]);
    static group7000006 = new RegularlyCollocation(7000006, [Role.SHUANGZI.id, Role.YINGYING.id]);
    static group7000007 = new RegularlyCollocation(7000007, [Role.SHUANGZI.id, Role.CAPTAIN.id]);
    static group7000008 = new RegularlyCollocation(7000008, [Role.SHUANGZI.id, Role.RENZHE.id]);
    static group7000009 = new RegularlyCollocation(7000009, [Role.SHUANGZI.id, Role.BAIGUJING.id]);
    static group7000010 = new RegularlyCollocation(7000010, [Role.SHUANGZI.id, Role.LINGLING.id]);
    static group7000011 = new RegularlyCollocation(7000011, [Role.SHUANGZI.id, Role.XIXUEGUI.id]);
    static group7000012 = new RegularlyCollocation(7000012, [Role.SHUANGZI.id, Role.HUOWANG.id]);
    static group7000013 = new RegularlyCollocation(7000013, [Role.SHUANGZI.id, Role.YEREN.id]);

    // 🦊 傀儡
    static group8000000 = new RegularlyCollocation(8000000, [Role.KUILEI.id, Role.JOKER.id]);
    static group8000001 = new RegularlyCollocation(8000001, [Role.KUILEI.id, Role.YINGYING.id]);
    static group8000002 = new RegularlyCollocation(8000002, [Role.KUILEI.id, Role.DIANYIN.id]);
    static group8000003 = new RegularlyCollocation(8000003, [Role.KUILEI.id, Role.ZHANAN.id]);
    static group8000004 = new RegularlyCollocation(8000004, [Role.KUILEI.id, Role.YOUXIA.id]);
    static group8000005 = new RegularlyCollocation(8000005, [Role.KUILEI.id, Role.LINGLING.id]);
    static group8000006 = new RegularlyCollocation(8000006, [Role.KUILEI.id, Role.XIXUEGUI.id]);
    static group8000007 = new RegularlyCollocation(8000007, [Role.KUILEI.id, Role.RABBIT.id]);
    static group8000008 = new RegularlyCollocation(8000008, [Role.KUILEI.id, Role.BAIGUJING.id]);
    static group8000009 = new RegularlyCollocation(8000009, [Role.KUILEI.id, Role.RENZHE.id]);
    static group8000010 = new RegularlyCollocation(8000010, [Role.KUILEI.id, Role.WUNV.id]);

    // 🦊 狐尾
    static group9000000 = new RegularlyCollocation(9000000, [Role.JIUWEIHU.id, Role.JIANGJIANG.id]);
    static group9000001 = new RegularlyCollocation(9000001, [Role.JIUWEIHU.id, Role.NURSE.id]);
    static group9000002 = new RegularlyCollocation(9000002, [Role.JIUWEIHU.id, Role.HEIWA.id]);
    static group9000003 = new RegularlyCollocation(9000003, [Role.JIUWEIHU.id, Role.HONGZHAJI.id]);
    static group9000004 = new RegularlyCollocation(9000004, [Role.JIUWEIHU.id, Role.DUODUO.id]);
    static group9000005 = new RegularlyCollocation(9000005, [Role.JIUWEIHU.id, Role.LEIMENG.id]);
    static group9000006 = new RegularlyCollocation(9000006, [Role.JIUWEIHU.id, Role.ZHANAN.id]);
    static group9000007 = new RegularlyCollocation(9000007, [Role.JIUWEIHU.id, Role.TUYA.id]);
    static group9000008 = new RegularlyCollocation(9000008, [Role.JIUWEIHU.id, Role.CHUZI.id]);
    static group9000009 = new RegularlyCollocation(9000009, [Role.JIUWEIHU.id, Role.RABBIT.id]);
    static group9000010 = new RegularlyCollocation(9000010, [Role.JIUWEIHU.id, Role.BZGIRL.id]);
    static group9000011 = new RegularlyCollocation(9000011, [Role.JIUWEIHU.id, Role.LINGLING.id]);
    static group9000012 = new RegularlyCollocation(9000012, [Role.JIUWEIHU.id, Role.XIXUEGUI.id]);
    static group9000013 = new RegularlyCollocation(9000013, [Role.JIUWEIHU.id, Role.HUAQIANJI.id]);
    static group9000014 = new RegularlyCollocation(9000014, [Role.JIUWEIHU.id, Role.LANLAN.id]);
    static group9000015 = new RegularlyCollocation(9000015, [Role.JIUWEIHU.id, Role.JIANSHI.id]);
    static group9000016 = new RegularlyCollocation(9000016, [Role.JIUWEIHU.id, Role.WUGEGE.id]);

    // 光影 扎男
    static group10000000 = new RegularlyCollocation(10000000, [Role.ZHANAN.id, Role.JIUWEIHU.id]);
    static group10000001 = new RegularlyCollocation(10000001, [Role.ZHANAN.id, Role.WUKONG.id]);
    static group10000002 = new RegularlyCollocation(10000002, [Role.ZHANAN.id, Role.TUYA.id]);
    static group10000003 = new RegularlyCollocation(10000003, [Role.ZHANAN.id, Role.BZGIRL.id]);
    static group10000004 = new RegularlyCollocation(10000004, [Role.ZHANAN.id, Role.SHUANGZI.id]);
    static group10000005 = new RegularlyCollocation(10000005, [Role.ZHANAN.id, Role.JIANGJIANG.id]);
    static group10000006 = new RegularlyCollocation(10000006, [Role.ZHANAN.id, Role.HONGZHAJI.id]);
    static group10000007 = new RegularlyCollocation(10000007, [Role.ZHANAN.id, Role.NIUXIAOMANG.id]);
    static group10000008 = new RegularlyCollocation(10000008, [Role.ZHANAN.id, Role.DIANYIN.id]);
    static group10000009 = new RegularlyCollocation(10000009, [Role.ZHANAN.id, Role.RABBIT.id]);
    static group10000010 = new RegularlyCollocation(10000010, [Role.ZHANAN.id, Role.YOUXIA.id]);
    static group10000011 = new RegularlyCollocation(10000011, [Role.ZHANAN.id, Role.HUABANTU.id]);
    static group10000012 = new RegularlyCollocation(10000012, [Role.ZHANAN.id, Role.CAPTAIN.id]);
    static group10000013 = new RegularlyCollocation(10000013, [Role.ZHANAN.id, Role.XIXUEGUI.id]);
    static group10000014 = new RegularlyCollocation(10000014, [Role.ZHANAN.id, Role.WUGEGE.id]);
    static group10000015 = new RegularlyCollocation(10000015, [Role.ZHANAN.id, Role.JIANSHI.id]);
    static group10000016 = new RegularlyCollocation(10000016, [Role.ZHANAN.id, Role.SANTAIZI.id]);
    static group10000017 = new RegularlyCollocation(10000017, [Role.ZHANAN.id, Role.JOKER.id]);
    static group10000018 = new RegularlyCollocation(10000018, [Role.ZHANAN.id, Role.NUANYANG.id]);
    static group10000019 = new RegularlyCollocation(10000019, [Role.ZHANAN.id, Role.QIANGWEI.id]);
    static group10000020 = new RegularlyCollocation(10000020, [Role.ZHANAN.id, Role.WUNV.id]);


    // 其他强势搭配
    static group10000000000 = new RegularlyCollocation(10000000000, [Role.ZHADANKE.id, Role.HONGSANSAN.id]);
    static group10000000001 = new RegularlyCollocation(10000000001, [Role.CHUZI.id, Role.MAGICLION.id]);
    static group10000000002 = new RegularlyCollocation(10000000002, [Role.CHUZI.id, Role.NURSE.id]);
    static group10000000003 = new RegularlyCollocation(10000000003, [Role.CHUZI.id, Role.QUANBA.id]);
    static group10000000004 = new RegularlyCollocation(10000000004, [Role.LELE.id, Role.HEIWA.id]);
    static group10000000005 = new RegularlyCollocation(10000000005, [Role.LELE.id, Role.RABBIT.id]);
    static group10000000006 = new RegularlyCollocation(10000000006, [Role.LELE.id, Role.DIANYIN.id]);
    static group10000000007 = new RegularlyCollocation(10000000007, [Role.RABBIT.id, Role.MAGICLION.id]);
    static group10000000008 = new RegularlyCollocation(10000000008, [Role.RABBIT.id, Role.PUMPKIN.id]);
    static group10000000009 = new RegularlyCollocation(10000000009, [Role.MUSHI.id, Role.RABBIT.id]);
    static group10000000010 = new RegularlyCollocation(10000000010, [Role.MUSHI.id, Role.QUANBA.id]);
    static group10000000011 = new RegularlyCollocation(10000000011, [Role.HUAQIANJI.id, Role.QUANBA.id]);
    static group10000000012 = new RegularlyCollocation(10000000012, [Role.HUAQIANJI.id, Role.PUMPKIN.id]);
    static group10000000013 = new RegularlyCollocation(10000000013, [Role.HUAQIANJI.id, Role.NURSE.id]);
    static group10000000014 = new RegularlyCollocation(10000000014, [Role.BZGIRL.id, Role.DIANYIN.id]);
    static group10000000015 = new RegularlyCollocation(10000000015, [Role.BZGIRL.id, Role.RABBIT.id]);
    static group10000000016 = new RegularlyCollocation(10000000016, [Role.KUKU.id, Role.HEIWA.id]);
    static group10000000017 = new RegularlyCollocation(10000000017, [Role.KUKU.id, Role.TIEMIAN.id]);
    static group10000000018 = new RegularlyCollocation(10000000018, [Role.KUKU.id, Role.RABBIT.id]);
    static group10000000019 = new RegularlyCollocation(10000000019, [Role.KUKU.id, Role.DIANYIN.id]);
    static group10000000020 = new RegularlyCollocation(10000000020, [Role.LULU.id, Role.CAPTAIN.id]);
    static group10000000021 = new RegularlyCollocation(10000000021, [Role.SANTAIZI.id, Role.LEIMENG.id]);
    static group10000000022 = new RegularlyCollocation(10000000022, [Role.SANTAIZI.id, Role.DIANYIN.id]);
    static group10000000023 = new RegularlyCollocation(10000000023, [Role.SANTAIZI.id, Role.RABBIT.id]);
    // next 24


    static maxGroupId = 0;
    static groupSum = 0;


    static getMaxGroupId() {
        if (this.maxGroupId > 0) return this.maxGroupId;
        for (let item in RegularlyCollocation) {
            if (!RegularlyCollocation[item] || RegularlyCollocation[item].id === undefined || RegularlyCollocation[item].id < 0) continue;
            if (RegularlyCollocation[item].id > this.maxGroupId) this.maxGroupId = RegularlyCollocation[item].id;
        }
        return this.maxGroupId;
    }

    static getGroupSum() {
        if (this.groupSum > 0) return this.groupSum;
        for (let item in RegularlyCollocation) {
            if (!RegularlyCollocation[item] || RegularlyCollocation[item].id === undefined || RegularlyCollocation[item].id < 0) continue;
            if (RegularlyCollocation[item].id > 0) this.groupSum += 1;
        }
        //console.log(">>>> RegularlyCollocation groupSum=" + this.groupSum); // 41
        return this.groupSum;
    }

    static getNextGroupItem(id) {
        let currItem = null;
        let targetItem = null;
        for (let item in RegularlyCollocation) {
            if (!RegularlyCollocation[item] || RegularlyCollocation[item].id === undefined || RegularlyCollocation[item].id < 0) continue;
            if (currItem) {
                targetItem = RegularlyCollocation[item];
                return targetItem;
            }
            if (RegularlyCollocation[item].id === id) currItem = RegularlyCollocation[item];
        }
        return this.group1000000;
    }

    static getRandomGroup() {
        let idx = fullCloseInt(0, this.getGroupSum());
        //console.log(">>>> RegularlyCollocation getRandomGroup idx=" + idx);
        let i = 0;
        for (let item in RegularlyCollocation) {
            if (!RegularlyCollocation[item] || RegularlyCollocation[item].id === undefined || RegularlyCollocation[item].id < 0) continue;
            if (i === idx) return RegularlyCollocation[item].group;
            i++;
        }
        return this.group1000000.group;
    }

}

//////////////////////////////////////////////////////////////////////


//////////////////////////////////////////////////////////////////////
// 【场景主题】 变量、方法区域
//////////////////////////////////////////////////////////////////////    
// 主题类
class Theme {

    constructor(id, name, bgColor, bgImage, bgImageIdbKey, tbColor, tblColor, tblWidth, glColor, glmColor, glWidth, gnColor, gndColor, gnSize,
        plColor, plWidth, rlColor, klplColor, klplWidth, szbplColor, szbrlColor, ccColor, ccWidth, ccStyle, szccColor, wkShowColor) {
        this.id = id || 0; // 编号
        this.name = name || "默认主题"; // 名称
        this.bgColor = bgColor || "#7F70C3"; // 页面背景颜色
        this.bgImage = bgImage || ""; // 页面背景图片
        this.bgImageIdbKey = bgImageIdbKey || sysConfig.bgImageKey + this.id; // 页面背景图片indexedDB key
        this.tbColor = tbColor || "#8d93d8"; // table 台面背景颜色
        this.tblColor = tblColor || "#35357A"; // table line 台面边框线颜色
        this.tblWidth = tblWidth || roundNumber(6.00 * dpr); // TODO table line 台面边框线宽，根据设备 DPR 决定，在 init() 初始化的时候计算设置 0.27 * sysConfig.girdSizeCss * dpr
        this.glColor = glColor || "#8384D1D0"; // gird line 砖格线颜色
        this.glmColor = glmColor || "#6A6CBFD0"; // gird line middle 砖格线中间线颜色
        this.glWidth = glWidth || roundNumber(1.00 * dpr * (os.isTablet ? 1.618 : 1)); // gird line 砖格线宽，根据设备 DPR 决定
        this.gnColor = gnColor || "#D2CCF1"; // gird number 砖格坐标数值颜色
        this.gndColor = gndColor || "#D7D7DC"; // gird number dark 砖格坐标数值黑夜模式颜色
        this.gnSize = gnSize || 24; // TODO gird number 砖格坐标数值显示大小，初始化的时候计算 htmlFontSizeNum * dpr * sysConfig.pxRatio + "px serif"
        this.plColor = plColor || "#cfe0d380"; // point line 角色中心点运动路径颜色
        this.plWidth = plWidth || roundNumber(5.20 / 2 * dpr * (os.isTablet ? 1.618 : 1)); // point line 角色中心点运动路径宽度
        this.rlColor = rlColor || "#cfe0d325"; // role line 角色本体运动路径颜色
        this.klplColor = klplColor || "#D61C24"; // kuilei point line 傀儡中心点运动路径颜色
        this.klplWidth = klplWidth || roundNumber(7.00 / 2 * dpr * (os.isTablet ? 1.618 : 1)); // kuilei point line 傀儡中心点运动路径宽度
        this.szbplColor = szbplColor || "#EADF5580"; // shaungzi back role line 双子分身中心点运动路径颜色
        this.szbrlColor = szbrlColor || this.rlColor; // shaungzi back role line 双子分身本体运动路径颜色
        this.ccColor = ccColor || "#000000"; // collide circle 碰撞指示圈颜色
        this.ccWidth = ccWidth || roundNumber(1.00 * dpr * (os.isTablet ? 1.618 : 1)); // collide circle 碰撞指示圈宽度
        this.ccStyle = ccStyle || 0; // collide circle 碰撞指示圈样式，0-虚线；1-实线
        this.szccColor = szccColor || "#ffffffaa"; // shuangzi collide circle 双子分身碰撞指示圈颜色
        this.wkShowColor = wkShowColor || "#1B1D2230"; // 猴子分身提示路径颜色
    }


    static DEFAULT = new Theme(0, "默认主题", "#7F70C3");
    //static WINTER_NEW_YEAR = new Theme(2, "新年主题", "#7F70C3");
    static WINTER_SNOW = new Theme(1, "冰雪主题", "#C7D0E0", "", "", "#4B99C9", "#EEF0F2", 0, "#438EC2", "#3483B7", 0, "#687CA1", "#EEF0F2", 0, "#cfe0d380", 0, "#cfe0d325", "", 0, "#EADF5580", "", "", 0, 0, "", "#1B1D2230");
    static SPRING_RUSTICITY = new Theme(3, "田园主题", "#E6DD9C", "", "", "#9A9069", "#FBFAD0", 0, "#6B624060", "#6B6240D0", 0, "#252042", "#FBFAD0", 0, "#cfe0d380", 0, "#cfe0d325", "", 0, "#EADF5580", "", "", 0, 0, "", "#1B1D2230");
    static AUTUMN_INTERSTELLAR = new Theme(4, "星际主题", "#05132C", "", "", "#808080", "#D7D7DC", 0, "#696969A0", "#2F4F4FA0", 0, "#D7D7DC", "#D7D7DC", 0, "#cfe0d380", 0, "#cfe0d325", "", 0, "#EADF5580", "", "", 0, 0, "", "#1B1D2230");
    static SUMMER_SEASIDE = new Theme(5, "夏日主题", "#3C8BBB", "", "", "#FFBF6F", "#FAF9CB", 0, "#B7521AA0", "#B7521AD0", 0, "#2B117D", "#FBFAD0", 0, "#F9FBF580", 0, "#F9FBF540", "", 0, "#EADF5580", "", "", 0, 0, "", "#1B1D2230");

    static CURR_THEME_COPY = null;

    static maxId = 0;
    static getMaxId() {
        if (this.maxId) return this.maxId;
        for (let item in Theme) {
            if (!Theme[item] || Theme[item].id === undefined || Theme[item].id < 0) continue;
            if (Theme[item].id > this.maxId) this.maxId = Theme[item].id;
        }
        return this.maxId;
    }

    static getCustomTheme() {
        // 从缓存获取自定义主题
        let customThemeStr = localStorage.getItem("collide-try-custom-theme");
        if (customThemeStr) {
            try {
                let customTheme = JSON.parse(customThemeStr);
                if (customTheme) return customTheme;
            } catch (e) { }
        }
        //return this.getCurrTheme();
        return null;
    }

    static getCurrTheme(id) {
        if (!id && id !== 0) id = userConfig.sceneThemeMode;
        for (let item in Theme) {
            if (!Theme[item] || Theme[item].id === undefined || Theme[item].id < 0) continue;
            if (Theme[item].id === id) return Theme[item];
        }
        return this.DEFAULT;
    }

    static getCurrThemeCopy(id) {
        //this.setCurrThemeCopy(id);
        //return this.CURR_THEME_COPY;
        if (!id && id !== 0) id = userConfig.sceneThemeMode;
        for (let item in Theme) {
            if (!Theme[item] || Theme[item].id === undefined || Theme[item].id < 0) continue;
            if (Theme[item].id === id) {
                return JSON.parse(JSON.stringify(Theme[item]));
            }
        }
        return JSON.parse(JSON.stringify(this.DEFAULT));
    }

    static setCurrThemeCopy(id) {
        if (this.CURR_THEME_COPY) return;
        if (!id && id !== 0) id = userConfig.sceneThemeMode;
        for (let item in Theme) {
            if (!Theme[item] || Theme[item].id === undefined || Theme[item].id < 0) continue;
            if (Theme[item].id === id) {
                this.CURR_THEME_COPY = JSON.parse(JSON.stringify(Theme[item]));
                return;
            }
        }
        this.CURR_THEME_COPY = JSON.parse(JSON.stringify(this.DEFAULT));
    }

    static getNameById(id) {
        for (let item in Theme) {
            if (!Theme[item] || Theme[item].id === undefined || Theme[item].id < 0) continue;
            if (Theme[item].id === id) return Theme[item].name;
        }
        return this.DEFAULT.name;
    }

    static getBgColorById(id) {
        for (let item in Theme) {
            if (!Theme[item] || Theme[item].id === undefined || Theme[item].id < 0) continue;
            if (Theme[item].id === id) return Theme[item].bgColor;
        }
        return this.DEFAULT.bgColor;
    }

    // 重新计算属性值
    static reCalculate(theme) {
        if (!theme) return;
        theme.tblWidth = sysConfig.sceneLineWidth; // 台面边框线宽
        theme.gnSize = Math.round(htmlFontSizeNum * dpr * sysConfig.pxRatio * 0.8); // 砖格坐标数值字体大小
        theme.plWidth = roundNumber(0.11 * sysConfig.girdSize); // 角色运动路径线宽
        theme.klplWidth = roundNumber(0.18 * sysConfig.girdSize); // 傀儡运动路径线宽
        theme.ccWidth = roundNumber(0.05 * sysConfig.girdSize); // 瞄准、碰撞指示圈线宽

    }

    // 判断是否为颜色码
    static isColorCode(str) {
        if (!str || typeof str !== "string" || str.replaceAll(" ", "") === "") return false;
        if (!str.startsWith("#") || !(/^[A-Fa-f0-9]{3,8}$/.test(str.substring(1)))) return false;
        let len = str.substring(1).length; // 去掉#，3、4、6、8 正常可用
        if (len === 5 || len === 7) return false;
        return true;
    }

    // 设置台面颜色透明
    static setTbColor00(code) {
        if (!code || !this.isColorCode(code)) return code;
        // 不算#，3-补一位0；4-最后一位改0；6-补两位0；8-最后两位改0
        code = code.slice(1);
        if (code.length === 3) return this.getFullColorCode("#" + code + "0");
        if (code.length === 4) return this.getFullColorCode("#" + code.substring(0, 3) + "0");
        if (code.length === 6) return "#" + code + "00";
        if (code.length === 8) return "#" + code.substring(0, 6) + "00";
        return "#" + code;
    }

    // 获取不带透明度的颜色码+开头#
    static getColorCodeNormal(code) {
        if (!code || !this.isColorCode(code)) return code;
        // 不算#，3-每一位重复一次；4-前三位每一位重复一次；6-直接返回；8-截取前6位
        code = code.slice(1);
        if (code.length === 4) code = code.substring(0, 3);
        if (code.length === 3) return '#' + code[0] + code[0] + code[1] + code[1] + code[2] + code[2];
        if (code.length === 6) return '#' + code;
        if (code.length > 6) return '#' + code.substring(0, 6);
        return "#" + code;
    }

    // 颜色短码补全（8位形式）
    static getFullColorCode(code) {
        if (!code || !this.isColorCode(code)) return code;
        // 不算#，3、4 位短码，每一位重复一次
        code = code.slice(1);
        if (code.length == 3) return '#' + code[0] + code[0] + code[1] + code[1] + code[2] + code[2] + "ff";
        if (code.length == 4) return '#' + code[0] + code[0] + code[1] + code[1] + code[2] + code[2] + code[3] + code[3];
        if (code.length == 6) return '#' + code + "ff";
        return "#" + code;
    }

}

//////////////////////////////////////////////////////////////////////


//////////////////////////////////////////////////////////////////////
// 【点按模式按钮】 变量、方法区域
////////////////////////////////////////////////////////////////////// 
class ClickPlayBtn {
    constructor(x, y, radius, outRadius, color, outColor, outLineColor,
        fontColor, fontLineColor, content, fontSize, isReady) {
        this.x = x || 0;
        this.y = y || 0;
        this.radius = radius || roundNumber(sysConfig.girdSize * (1.68 - 0.4), 4); // 阴影半径
        this.outRadius = outRadius || roundNumber(sysConfig.girdSize * (1.68 - 0.1), 4); // 按钮半径
        this.color = color || "#DEC27BA0"; // 按钮颜色
        this.outColor = outColor || "#FAEDCE40"; // 阴影颜色
        this.outLineColor = outLineColor || "#5A5963"; // 边界线颜色
        this.fontColor = fontColor || "#FFFFFF"; // 文字颜色
        this.fontLineColor = fontLineColor || "#000000"; // 文字描边颜色
        this.content = content || "发射"; // 文字
        this.fontSize = fontSize || 12; // 文字大小
        this.isReady = isReady || false; // 是否已经准备发射
    }

    // 点按发射按钮阴影
    drawClickPlayBtnOut() {
        gameClickPlayContext.save();
        gameClickPlayContext.beginPath();
        gameClickPlayContext.fillStyle = clickPlayBtn.outColor;
        gameClickPlayContext.arc(gameClickPlayCanvas.width / 2, gameClickPlayCanvas.height / 2, clickPlayBtn.outRadius, 0, 2 * Math.PI);
        gameClickPlayContext.fill();
        gameClickPlayContext.closePath();
        gameClickPlayContext.restore();
    }

    // 点按发射按钮描边
    drawClickPlayBtnOutLine() {
        gameClickPlayContext.save();
        gameClickPlayContext.beginPath();
        gameClickPlayContext.lineWidth = roundNumber(1 * dpr * sysConfig.pxRatio, 4);
        gameClickPlayContext.setLineDash([Math.round(5 * dpr * sysConfig.pxRatio), Math.round(5 * dpr * sysConfig.pxRatio)]); // 虚线
        gameClickPlayContext.strokeStyle = this.outLineColor;
        gameClickPlayContext.arc(gameClickPlayCanvas.width / 2, gameClickPlayCanvas.height / 2, this.outRadius, 0, 2 * Math.PI);
        gameClickPlayContext.stroke();
        gameClickPlayContext.closePath();
        gameClickPlayContext.restore();
    }

    // 点按发射按钮
    drawClickPlayBtn() {
        //if (userConfig.currPlayOpt !== 1) return; // 1-点按模式

        // 画阴影
        this.drawClickPlayBtnOut();
        // 画边界线
        this.drawClickPlayBtnOutLine();

        gameClickPlayContext.save();
        gameClickPlayContext.beginPath();
        gameClickPlayContext.fillStyle = this.color;
        //gameClickPlayContext.rect(0, 0, 140, 140);
        gameClickPlayContext.arc(gameClickPlayCanvas.width / 2, gameClickPlayCanvas.height / 2, this.radius, 0, 2 * Math.PI);
        gameClickPlayContext.fill();
        gameClickPlayContext.closePath();
        gameClickPlayContext.restore();

        // 文字
        this.drawBtnText();
    }

    // 绘制文字
    drawBtnText() {
        gameClickPlayContext.save();
        gameClickPlayContext.fillStyle = this.fontColor;
        // 水平对齐方式 (center left right start end)
        gameClickPlayContext.textAlign = "center";
        // 垂直对齐的方式 (top bottom middle)
        gameClickPlayContext.textBaseline = 'middle';

        let fontSize = 16;
        let metrics, width, height;

        gameClickPlayContext.font = fontSize * dpr + "px Arial";
        metrics = gameClickPlayContext.measureText(this.content);
        width = roundNumber(metrics.width, 4);
        height = roundNumber(metrics.actualBoundingBoxAscent + metrics.actualBoundingBoxDescent, 4);

        while (width > 0.5 * gameClickPlayCanvas.width) {
            fontSize -= 1;
            gameClickPlayContext.font = fontSize * dpr + "px Arial";
            metrics = gameClickPlayContext.measureText(this.content);
            width = roundNumber(metrics.width, 4);
            height = roundNumber(metrics.actualBoundingBoxAscent + metrics.actualBoundingBoxDescent, 4);
            if (fontSize < 1) break; // 避免 height 计算异常，导致死循环
        }

        while (height < 0.2 * gameClickPlayCanvas.height) {
            fontSize += 1;
            gameClickPlayContext.font = fontSize * dpr + "px Arial";
            metrics = gameClickPlayContext.measureText(this.content);
            width = roundNumber(metrics.width, 4);
            height = roundNumber(metrics.actualBoundingBoxAscent + metrics.actualBoundingBoxDescent, 4);
            if (fontSize > 50) break; // 避免 height 计算异常，导致死循环
        }

        if (fontSize < 1 || fontSize > 50) { // 字体大小异常
            console.error(">>>> drawBtnText fontSize error.");
            fontSize = 16;
            gameClickPlayContext.font = fontSize * dpr + "px Arial";
        }

        console.log(">>>> drawBtnText fontSize=" + fontSize + ", width=" + width + ", height=" + height);

        // 文字样式
        gameClickPlayContext.font = "bold " + fontSize * dpr + "px Arial";
        //gameClickPlayContext.imageSmoothingEnabled = true; // 平滑边缘绘制，消除锯齿，但是对文字描边锯齿没用

        // 文字阴影
        //gameClickPlayContext.shadowColor = '#000'; // 阴影颜色
        //gameClickPlayContext.shadowBlur = dpr; // 模糊程度
        //gameClickPlayContext.shadowOffsetX = dpr; // 水平偏移
        //gameClickPlayContext.shadowOffsetY = dpr; // 垂直偏移

        // 文字描边
        gameClickPlayContext.strokeStyle = "#000";
        gameClickPlayContext.lineWidth = roundNumber(2 * dpr * sysConfig.pxRatio, 4);
        gameClickPlayContext.strokeText(this.content, gameClickPlayCanvas.width / 2, gameClickPlayCanvas.height / 2);

        // 写文字
        gameClickPlayContext.fillStyle = this.fontColor;
        gameClickPlayContext.fillText(this.content, gameClickPlayCanvas.width / 2, gameClickPlayCanvas.height / 2);

        gameClickPlayContext.restore();
    }
}

//////////////////////////////////////////////////////////////////////


//////////////////////////////////////////////////////////////////////
// 【应用初始化】 变量、方法区域
//////////////////////////////////////////////////////////////////////

// 四条切角线
var lines = [];
// 四条切角线中点坐标
var linesMiddlePoints = [];
// 小球/角色
var balls = [];
// 蛋
var eggs = [];
// 临时小球对象，用于知道坐标、半径创建球对象，使用常量避免频繁创建对象
var tempCheckBall;
// 分身对象，设置跟主球一样的context，便于拖动时清理画布
var twinBall;
// 猴子等角色分身
var buddies = [];
// 角色是否存在判断标识
var isDuoduoExist = false;
var isLuluExist = false;
var isShuangziExist = false;
// 分享的角色和坐标数据
var shareData = null;
// html根元素字体大小
var htmlEle, htmlFontSize, htmlFontSizeNum;
// 台面区域
var tablePolygon = [];
// emoji 大图形 size
var largeEmojiSizes = ['s', 'mm', 'm', 'fll', 'll', 'l', 'xl'];
// emoji 大图形坐标列表 [{x:0,y:0,radius:0,icon:'🐂',size:'l',posIdx:0}]
var largeEmojiPoints = [];
// 当前主题
var currTheme = null;
// 猴子分身坐标
var monkeysPos, monkeysTargetPos;
// 点按发射按钮，因为依赖砖格大小，初始化需要放到砖格大小计算完成之后
var clickPlayBtn = null;


onMounted(() => {
    tempCheckBall = new Ball(context);
    twinBall = new Ball(gameMainBallContext);
    htmlEle = document.getElementsByTagName('html')[0];
    htmlFontSize = window.getComputedStyle(htmlEle).fontSize || "12px";
    htmlFontSizeNum = Number(htmlFontSize.replace("px", ""));
})


// 初始化应用参数
function initAppParams() {
    // 设置应用全名（名称+版本名）
    setAppFullName();
    // 设置应用更新内容
    setAppUpdateContent();
    // 设置更新时间格式
    setUpdateDateFormat();
    // 隐藏关闭所有dialog弹窗，保证离线版刚打开不会一直有弹窗
    hideAllDialog();
    // 检测 WebStorage 是否正常可用
    if (!checkWebStorage()) return;
    // 保存一份dpr
    sysConfig.dpr = dpr;
    // 版本号校验
    doVersionThings();
    // 用户配置
    setUserConfig();
    // 设置初始主题
    setThemeBySeason();
    if (userConfig.isUseCustomTheme) currTheme = Theme.getCustomTheme();
    if (!currTheme) currTheme = Theme.getCurrThemeCopy();
    // 像素比例
    if (os.isTablet) sysConfig.pxRatio = 1.618;
    console.log(">>>> sysConfig.pxRatio=" + sysConfig.pxRatio);
    // 设置字体大小
    setFontSize();
    console.log(">>>> html font size=" + htmlFontSize);
    // 游戏台面占屏幕宽度的比例
    if (os.isTablet) sysConfig.sceneWidthRatio = 0.618;
    console.log(">>>> sysConfig.sceneWidthRatio=" + sysConfig.sceneWidthRatio);
    // 初始化画布大小、网格大小
    setPageSize();
    console.log(">>>> sysConfig.girdSize=" + sysConfig.girdSize);
    console.log(">>>> sysConfig.girdSizeCss=" + sysConfig.girdSizeCss);
    // 调整边框宽度为 0.3 * girdSize
    sysConfig.sceneLineWidth = roundNumber(0.27 * sysConfig.girdSize, 4);
    console.log(">>>> sysConfig.sceneLineWidth=" + sysConfig.sceneLineWidth);
    // 没有启用自定义主题时，重新计算主题中的动态属性
    if (!userConfig.isUseCustomTheme) Theme.reCalculate(currTheme);
    // 设置弹窗滚动区域高度
    setDialogScrollMaxHeight(1.80);
    // 画布居中
    canvasAutoCenter();
    // 设置点按发射按钮画布大小和位置
    clickPlayBtn = new ClickPlayBtn();
    setClickPlayCanvas();
    // 台面区域初始化，用于检测判断是否与emoji图形重叠
    tablePolygon = [
        { x: Math.round(sysConfig.cLeft * dpr + sysConfig.girdSize * 3), y: Math.round(sysConfig.cTop * dpr - currTheme.tblWidth + sysConfig.girdSize * 0) },
        { x: Math.round(sysConfig.cLeft * dpr + sysConfig.girdSize * 11), y: Math.round(sysConfig.cTop * dpr - currTheme.tblWidth + sysConfig.girdSize * 0) },
        { x: Math.round(sysConfig.cLeft * dpr + sysConfig.girdSize * 14 + currTheme.tblWidth), y: Math.round(sysConfig.cTop * dpr + sysConfig.girdSize * 3) },
        { x: Math.round(sysConfig.cLeft * dpr + sysConfig.girdSize * 14 + currTheme.tblWidth), y: Math.round(sysConfig.cTop * dpr + sysConfig.girdSize * 19) },
        { x: Math.round(sysConfig.cLeft * dpr + sysConfig.girdSize * 11), y: Math.round(sysConfig.cTop * dpr + currTheme.tblWidth + sysConfig.girdSize * 22) },
        { x: Math.round(sysConfig.cLeft * dpr + sysConfig.girdSize * 3), y: Math.round(sysConfig.cTop * dpr + currTheme.tblWidth + sysConfig.girdSize * 22) },
        { x: Math.round(sysConfig.cLeft * dpr + sysConfig.girdSize * 0 - currTheme.tblWidth), y: Math.round(sysConfig.cTop * dpr + sysConfig.girdSize * 19) },
        { x: Math.round(sysConfig.cLeft * dpr + sysConfig.girdSize * 0 - currTheme.tblWidth), y: Math.round(sysConfig.cTop * dpr + sysConfig.girdSize * 3) }
    ];
    // 猴子分身坐标初始化
    setMonkeysPos();
    // 初始化鼠标位置
    captureMouse(canvas);
    // 初始化台面切角
    initTableAngle();
}


// 初始化台面切角
function initTableAngle() {
    // 设置台面切角偏差距离。注意放在初始化切割斜边之前
    if (sysConfig.isWan8CocosTable) {
        // 使用多点精确控制方式
        setSysWan8CocosTableMoveVals();
    }
    console.log(">>>> sysConfig.wan8CocosTableMoveVals=" + sysConfig.wan8CocosTableMoveVals.toString());
    // 初始化切割斜边
    set4AngleLine();
    // 初始化设置四条切角线中点坐标
    set4AngleLineMiddlePoint(lines);
}


// 初始化角色
function initRoles() {
    // 导入了角色和坐标数据，不用选角色
    if (userConfig.shareRoleAndPos) {
        try {
            shareData = JSON.parse(userConfig.shareRoleAndPos);
            //console.log(shareData);
        } catch (e) { }
    }
    if (!shareData) setCurrRoleV2();
    if (userConfig.currRole < 0) userConfig.currRole = 0;
    // 只显示台面，隐藏主运动层、主球运动层、清空路径层
    if (userConfig.isJustShowTable) toggleOnlyTable(true);
    try {
        if (!shareData) throw new Error();
        // 设置分享角色和位置
        setShareRoleAndPos(shareData);
        // 设置当前主角
        if (balls && balls.length > 0) userConfig.currRole = balls[0].roleId;
        // TODO 导入角色也算选择角色
        if (userConfig.currRole > -1) localStorage.setItem('collide-try-role-chose', userConfig.currRole);
        console.log(">>>> 导入角色和位置操作完成");
    } catch (e) {
        console.log(">>>> setShareRoleAndPos error: " + e.message);
        // 设置主球
        setBallMain();
        // 设置其他小球
        if (!userConfig.isTestOnlyOne) setBallOthersByRole(userConfig.currRole);
        // 设置小丑分身【放在角色设置完成后】
        setRoleJoker();
    } finally {
        // 加载之后，清除导入数据【放到onMouseMove方法再处理】
        //clearShareRoleAndPos();
        // 标记角色已经选择完成
        if (userConfig.currRole > -1) sysConfig.isRoleChooseFinished = true;
    }
    // 设置双子分身
    if (userConfig.currRole === Role.SHUANGZI.id) setTwins();
    // 设置猴子分身
    if (userConfig.currRole === Role.WUKONG.id) setMonkeys();
    // 设置完所有角色之后，设置主角所属队颜色
    resetMainTeamColorRandom(userConfig.mainTeamColor);
    // 初始化角色碰撞标志位
    setBallCollidingNos();
    // 设置完角色后，检测角色是否存在
    checkRoleExist();
    // 露露加速 50%，手动调整一个跟实战相近的数值
    if (isLuluExist) balls[0].vRatio += 0.20;
    // 设置蛋
    if (isDuoduoExist) setEggs();
    // 设置速度
    setSpeed();
    // 设置摩擦力
    setFriction();
}


// 初始化一次
function initOnce() {
    // 角色运动路径判断显示
    if (userConfig.isShowBallMovePath) gamePathCanvas.style.display = "inherit";
    // 角色全路径判断显示
    if (userConfig.isShowBallPath) gamePathBallCanvas.style.display = "inherit";
    // 游戏桌面场景初始化，需要放在角色设置之后，因为场景会根据角色变化
    if (sysConfig.isRoleChooseFinished) gameSceneInit(); // 选择角色后才渲染场景，优化性能
}


// 初始化其他参数
function initOthers() {
    // TODO
}


// 不刷新页面【重新选角色】，重新初始化页面数据
function reInit(isImport, isKeepDialog) {
    // 停止当前回合运动状态
    resetBallsSpeed(balls);
    // 重置全局变量
    balls = [];
    eggs = [];
    // 重置分享数据
    shareData = null;
    let isDuoduoExistBak = isDuoduoExist;
    // 重新初始化角色
    initRoles();
    // 判断是否需要重新画台面，选择前后只要有朵朵就需要重画
    //if (isDuoduoExistBak || isDuoduoExist) reDrawTableAndEgg();
    // 为了避免后续各种判断，每次都重新画
    reDrawTableAndEgg();
    // 重置动画渲染相关变量
    resetAnimate();
    // 模拟重打清屏重新开始新的渲染
    if (isImport) directPlayAgain(true);
    else {
        directPlayAgain(false);
        // 解除 directPlayAgain() 选中的主球
        selectedBall = null;
    }
    // 重新渲染
    //isAnimated = false;
    //if (!isPlaying) animate();
    // 完成后关闭选择角色弹窗
    if (!isKeepDialog) switchChooseRoleDialog(false);
}


// TODO 应用初始化
function init() {
    // 初始化应用参数
    initAppParams();
    // 初始化选择角色
    initRoles();
    // 初始化一次的配置
    initOnce();
    // 初始化其他配置
    initOthers();

    //console.log(">>>> init sysConfig=" + JSON.stringify(sysConfig));
    //alert(">>>> init sysConfig=" + JSON.stringify(sysConfig));
}


onMounted(() => {
    // 当 HTML 文档加载完毕后，立刻执行某个方法
    // 通常用于 <body> 元素，在页面完全载入后(包括图片、css文件等等)执行脚本代码
    // 等图片加载完成？网络不好的话，有点悬啊
    //window.onload = function() {
    try {
        init();
    } catch (e) {
        // 处理错误事项
        if (e instanceof Error) {
            if (e.message.includes("手动结束程序")) { throw e; }
        }
        doGlobalError(e, (sysConfig && sysConfig.alertErrorCount) ? sysConfig.alertErrorCount : 3);
    }
    //}
})


// 设置应用名称
function setAppFullName() {
    let fullNameEles = document.getElementsByClassName('collide-try-app-full-name');
    if (!fullNameEles) return;
    let fullName = sysConfig.appName + "_" + sysConfig.versionName;
    for (let i = 0, len = fullNameEles.length; i < len; i++) {
        fullNameEles[i].innerText = fullName;
    }
}


// 设置更新时间格式
function setUpdateDateFormat() {
    let dateEles = document.getElementsByClassName('collide-try-update-date');
    if (!dateEles) return;
    let y = new Date().getFullYear();
    let result;
    for (let i = 0, len = dateEles.length; i < len; i++) {
        result = dateEles[i].innerText;
        if (result.startsWith(y)) dateEles[i].innerText = result.replaceAll((y + "-"), "");
    }
}


// 设置应用更新内容
function setAppUpdateContent() {
    let updateTitleEle = document.getElementById("update-content-title");
    if (!updateTitleEle) return;
    updateTitleEle.innerText = "🆕 " + sysConfig.versionName + " 更新";
    let updateTargetEle = document.getElementById("collide-try-update-content");
    if (!updateTargetEle) return;
    let updateContentEle = document.getElementById("collide-try-about-app-update-newest");
    if (!updateContentEle) return;
    let updateContentEleClone = updateContentEle.cloneNode(true);
    if (!updateContentEleClone) return;
    // 先清空子元素，避免重复添加
    let targetChildren = updateTargetEle.childNodes;
    if (targetChildren && targetChildren.length > 0) {
        for (let i = 0, len = targetChildren.length; i < len; i++) {
            updateTargetEle.removeChild(targetChildren[i]);
        }
    }
    updateTargetEle.appendChild(updateContentEleClone);
}


// 校验版本号，处理新增功能逻辑，更新版本要更新之前的缓存
function doVersionThings() {
    let collideTryVersionStr = localStorage.getItem('collide-try-version');
    let collideTryVersion = collideTryVersionStr ? Number(collideTryVersionStr) : 0;
    console.log(">>>> collide-try-version-old=" + collideTryVersion + ", collide-try-version-new=" + sysConfig.version);
    if (sysConfig.version > collideTryVersion) {
        // 更新 userConfig 缓存
        let localUserConfigStr = localStorage.getItem('collide-try-user-settings');
        let userConfigCache = null;
        if (localUserConfigStr) {
            userConfigCache = JSON.parse(localUserConfigStr);
        }
        if (userConfigCache) {
            for (let f in userConfig) {
                //console.log(f + " = " + userConfig[f]);
                // 个别特殊字段不受缓存影响，以代码配置为准
                if (f === 'tryFullPathPointNum') continue;
                if (f === 'animateAutoRestTime') continue;
                if (f === 'wan8CocosTableMoveVals') continue;
                if (f === 'isShowBallMovePath') continue;
                if (f === 'isShowBallPath') continue;
                if (f === 'isKuileiPullBack') continue;
                if (f === 'isShowTryFullPath') continue;
                //if (f === 'isShowRoleBloodLine') continue;
                //if (f === 'isShowRoleBloodNo') continue;
                if (userConfigCache[f] || typeof userConfigCache[f] === "boolean") userConfig[f] = userConfigCache[f];
            }
            // 更新 localStorage 中的 userConfig
            localStorage.setItem('collide-try-user-settings', JSON.stringify(userConfig));
            console.log(">>>> doVersionThings userConfig in localStorage updated.");
        }

        // 显示更新内容
        showUpdateContent(true);

        localStorage.setItem('collide-try-version', sysConfig.version); // 版本号存入缓存
        localStorage.removeItem("collide-try-init-error-count"); // 更新版本后重置错误计数
    }
}


// 初始化方法报错多次后，要处理的事情
function doGlobalError(e, count) {
    let collideTryInitErrorCountStr = localStorage.getItem('collide-try-init-error-count');
    let collideTryInitErrorCount = collideTryInitErrorCountStr ? Number(collideTryInitErrorCountStr) : 0;
    console.log(">>>> collideTryInitErrorCount=" + collideTryInitErrorCount);
    if (!count || count < 0) count = 3;
    if (collideTryInitErrorCount >= count || !isProd()) { // 错误达到指定次数
        /*
        // 清理所有缓存【之前参数配置会丢失】
        //localStorage.clear();
        sessionStorage.clear();
        for (let i = 0, len = localStorage.length; i < len; i++) {
            if (!localStorage.key(i)) continue;
            if (localStorage.key(i).includes("access-key")) continue;
            localStorage.removeItem(localStorage.key(i));
        }
        */
        // 超过次数弹窗提示
        if (collideTryInitErrorCount % count === 0 || !isProd()) doGlobalErrorMsg(e, true);
        // 达到五次弹窗提示尝试恢复默认设置
        if (collideTryInitErrorCount % 5 === 0)
            alert("💡 温馨提示：\n一直报错，可以尝试在设置里面恢复默认设置！");

    }

    collideTryInitErrorCount += 1;
    // 重置初始化错误计数
    if (collideTryInitErrorCount > 10) collideTryInitErrorCount = 0;

    localStorage.setItem('collide-try-init-error-count', collideTryInitErrorCount);
}


// 读取、设置用户配置
function setUserConfig() {
    let localUserConfigStr = localStorage.getItem('collide-try-user-settings');
    if (localUserConfigStr) {
        userConfig = JSON.parse(localUserConfigStr);
        // TODO 特殊字段不受缓存影响，以代码配置为准
        userConfig.tryFullPathPointNum = userConfigBack.tryFullPathPointNum;
        console.log(">>>> localStorage userConfig: " + JSON.stringify(userConfig));
    }
}


// 设置当前角色
function setCurrRole() {
    // 从 sessionStorage 读取，注意关闭页面，重新打开才会失效，浏览器标题栏右键“重新打开关闭页面”还是能获取到
    try {
        let roleValStr = sessionStorage.getItem('collide-try-role-chose');
        // 如果不是数字类型
        if (!(!isNaN(parseFloat(roleValStr)) && isFinite(roleValStr))) throw new Error(">>>> 角色选择出现错误！请重新选择或联系开发者");
        userConfig.currRole = Number(roleValStr);
    } catch (e) {
        //console.log(">>>> sessionStorage getItem error: " + e.message);
        userConfig.currRole = -1;
    }

    //if (!userConfig.currRole) { // 没获取到，则弹出选择角色框。注意 0 为 false
    if (userConfig.currRole < 0) {
        // sessionStorage 没找到，再从 localStorage 中取值
        try {
            let roleValStr = localStorage.getItem('collide-try-role-chose');
            // 如果不是数字类型
            if (!(!isNaN(parseFloat(roleValStr)) && isFinite(roleValStr))) throw new Error(">>>> 角色选择出现错误！请重新选择或联系开发者");
            userConfig.currRole = Number(roleValStr);
        } catch (e) {
            //console.log(">>>> localStorage getItem error: " + e.message);
            userConfig.currRole = -1;
        }
        // 还是没找到，再弹出角色选择窗
        if (userConfig.currRole < 0) {
            dialogMask.style.display = "unset"; // 显示选择角色遮罩层
            chooseRoleDialog.style.display = "unset"; // 显示选择角色弹窗
            //return;
            //alert(">>>> 角色选择出现错误！请联系开发者");
            //throw new Error("角色选择出现错误！请联系开发者");
        } else {
            // localStorage 找到了
            localStorage.removeItem("collide-try-role-chose");
            //sessionStorage.setItem('collide-try-role-chose', userConfig.currRole);
        }
    }

    // 标记角色选择完成
    if (userConfig.currRole > -1) sysConfig.isRoleChooseFinished = true;

    if (userConfig.isRandomRole || userConfig.isFlashRole) {
        if (userConfig.isRandomRole) userConfig.currRole = Role.getRandomRoleId();
        if (userConfig.isFlashRole) setRolesFlash(userConfig.gameRoleIds, true);
        // 存到 sessionStorage【PC浏览器刷新不会失效，关闭页面会失效】
        //if (userConfig.currRole > -1) sessionStorage.setItem('collide-try-role-chose', userConfig.currRole);
        // TODO 存到 localStorage，兼容一些浏览器（Via）刷新后 sessionStorage 失效，导致一直弹出选择角色问题
        //if (userConfig.currRole > -1) localStorage.setItem('collide-try-role-chose', userConfig.currRole);
        // localStorage 存储更新 userConfig 对象
        if (userConfig.currRole > -1) localStorage.setItem('collide-try-user-settings', JSON.stringify(userConfig));
    }

    console.log(">>>> userConfig.currRole=" + userConfig.currRole);
}


// 设置当前角色（不刷新页面版本，选择的角色永久存储在localStorage）
function setCurrRoleV2() {
    // 一直从 localStorage 读取
    try {
        let roleValStr = localStorage.getItem('collide-try-role-chose');
        // 如果不是数字类型
        if (!(!isNaN(parseFloat(roleValStr)) && isFinite(roleValStr))) throw new Error(">>>> 角色选择出现错误！请重新选择或联系开发者");
        userConfig.currRole = Number(roleValStr);
    } catch (e) {
        //console.log(">>>> localStorage getItem error: " + e.message);
        userConfig.currRole = -1;
    }
    // 还是没找到，再弹出角色选择窗
    if (userConfig.currRole < 0) {
        switchChooseRoleDialog(true);
        //return;
        //alert(">>>> 角色选择出现错误！请联系开发者");
        //throw new Error("角色选择出现错误！请联系开发者");
    }

    // 标记角色选择完成
    if (userConfig.currRole > -1) sysConfig.isRoleChooseFinished = true;

    if (userConfig.isRandomRole || userConfig.isFlashRole) {
        if (userConfig.isRandomRole) userConfig.currRole = Role.getRandomRoleId();
        if (userConfig.isFlashRole) setRolesFlash(userConfig.gameRoleIds, true);
        // 存到 sessionStorage 【刷新不会失效，关闭这个页面会失效】
        //if (userConfig.currRole > -1) sessionStorage.setItem('collide-try-role-chose', userConfig.currRole);
        // TODO 存到 localStorage，兼容一些浏览器（Via）刷新后 sessionStorage 失效，导致一直弹出选择角色问题
        //if (userConfig.currRole > -1) localStorage.setItem('collide-try-role-chose', userConfig.currRole);
        // localStorage 存储更新 userConfig 对象
        if (userConfig.currRole > -1) localStorage.setItem('collide-try-user-settings', JSON.stringify(userConfig));
    }

    console.log(">>>> userConfig.currRole=" + userConfig.currRole);
}


// userConfig.wan8CocosTableMoveVals 结合 girdSize 计算，赋值给 sysConfig.wan8CocosTableMoveVals
function setSysWan8CocosTableMoveVals() {
    if (userConfig.wan8CocosTableMoveVals.length === 1 && Number(userConfig.wan8CocosTableMoveVals[0]) === 0) {
        sysConfig.wan8CocosTableMoveVals = [0, 0, 0, 0, 0, 0, 0, 0];
    } else {
        for (let i = 0; i < userConfig.wan8CocosTableMoveVals.length; i++) {
            sysConfig.wan8CocosTableMoveVals[i] = roundNumber(userConfig.wan8CocosTableMoveVals[i] * sysConfig.girdSize, 4);
        }
    }
}


/*
首次进入游戏，未选择任何主题，根据时间季节设置主题
季节变化，更换对应主题，只改一次，在这个季节内可手动更换其他主题

按照阳历划分，春季通常是3、4、5月，夏季是6、7、8月，秋季是9、10、11月，冬季是12、1、2月。
按照农历划分，春季是农历的正月至三月，夏季是四月至六月，秋季是七月至九月，冬季是十月至十二月。
*/
function setThemeBySeason(date) {
    // 上一次设置主题时间月份
    let collideTryThemeTimeStr = localStorage.getItem('collide-try-theme-time');
    let collideTryThemeTime = collideTryThemeTimeStr ? Number(collideTryThemeTimeStr) : 0;
    console.log(">>>> collide-try-theme-time=" + collideTryThemeTime);
    if (!date) date = new Date();
    let m = date.getMonth() + 1;
    if (isMonthInSameSeason(collideTryThemeTime, m) && userConfig.sceneThemeMode >= 0) return; // 玩家手动设置了主题
    let currThemeMode = 0;
    if ([12, 1, 2].indexOf(m) > -1) { // 冬季，冰雪主题
        currThemeMode = 1;
    } else if ([3, 4, 5].indexOf(m) > -1) { // 春季，田园主题
        currThemeMode = 3;
    } else if ([6, 7, 8].indexOf(m) > -1) { // 夏季，夏日主题
        currThemeMode = 5;
    } else if ([9, 10, 11].indexOf(m) > -1) { // 秋季，星际主题（《星际穿越》上映时间 2014-11-07 正好是秋季）
        currThemeMode = 4;
    } else { // 默认主题
        currThemeMode = 0;
    }
    // 设置主题模式
    userConfig.sceneThemeMode = currThemeMode;
    // 保存设置主题的月份
    localStorage.setItem('collide-try-theme-time', m);
}


// 判断两个月份是否在同一个季节（阳历）
function isMonthInSameSeason(m1, m2) {
    let idx1 = Math.floor(m1 / 3);
    if (idx1 < 0 || idx1 >= 4) idx1 = 0;
    let idx2 = Math.floor(m2 / 3);
    if (idx2 < 0 || idx2 >= 4) idx2 = 0;
    return idx1 === idx2;
}


// 初始化角色、颜色、大小、半径、速度等参数
function initBallByRole(ball) {
    if (!ball.roleId) ball.roleId = Role.HEIWA.id;
    console.log(">>>> initBallByRole " + ball.getBallDesc());
    switch (ball.roleId) {
        //case Role.HEIWA.id: // 走默认处理
        case Role.JIANGJIANG.id:
            ball.color = "#362CBC";
            ball.sizeRatio = Ball.SIZERATIO.S; // 小
            ball.mRatio = Ball.WEIGHTRATIO.M;
            if (ball.isMainBall) ball.vRatio = userConfig.isTestOnlyOne ? 1.05 : Ball.SPEEDRATIO.L; // 速度比率，比黑娃慢一级，为了模拟加速效果，速度可以设置大一点
            //if (ball.isMainBall) ball.v = 63.00; // 初始化的时候根据 vRatio 计算
            break;
        case Role.DUODUO.id:
            ball.color = "#8C5E9D";
            ball.sizeRatio = Ball.SIZERATIO.L; // 大
            ball.mRatio = Ball.WEIGHTRATIO.S; // 轻
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        case Role.KUILEI.id:
            ball.color = "#E72E38";
            ball.sizeRatio = Ball.SIZERATIO.L; //  大
            ball.pathRadius = roundNumber((currTheme.klplWidth + 0.1 * sysConfig.girdSize) / 2); // + 0.1 * sysConfig.girdSize 弥补半径过小导致检测不到碰撞的误差。roundNumber(7.0 / 2 * dpr); // 傀儡绳子运动路径半径
            ball.tryRadius = roundNumber(0.7 * sysConfig.girdSize / 2); // 傀儡瞄准线半径
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.L; // 快
            //if (ball.isMainBall) userConfig.isShowBallPath = false; // 不显示全路径
            //if (ball.isMainBall) userConfig.isStopAfterCollided = false;
            break;
        case Role.BAKE.id:
            ball.color = "#FD5B2B"; // FD5B2B 默认皮肤颜色；EFE3E5 天神降临皮肤颜色
            ball.sizeRatio = Ball.SIZERATIO.L; //  大
            ball.mRatio = Ball.WEIGHTRATIO.L; // 重 实战发现，其实巴克和酷酷一样重
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.S; // 慢
            break;
        case Role.LULU.id:
            ball.color = "#C8728B"; // PaleVioletRed 脸红的淡紫红
            ball.sizeRatio = Ball.SIZERATIO.M; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        case Role.KUKU.id:
            ball.color = "#CB8140"; // 取的默认皮肤棒球棍深颜色
            ball.sizeRatio = Ball.SIZERATIO.L; // 大
            ball.mRatio = Ball.WEIGHTRATIO.L; // 重
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.S; // 慢
            break;
        case Role.YINGYING.id:
            ball.color = "#2962D9"; // 取的默认皮肤裙子深颜色
            ball.sizeRatio = Ball.SIZERATIO.L; // 大
            ball.mRatio = Ball.WEIGHTRATIO.S; // 轻
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        case Role.JIUWEIHU.id:
            ball.color = "#D76A75"; // 取的默认皮肤尾巴深颜色
            ball.sizeRatio = Ball.SIZERATIO.L; // 大
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.S; // 慢
            break;
        case Role.SHUANGZI.id:
            if (!ball.color) ball.color = "#3F375A"; // 取的默认皮肤右边角色的衣服颜色
            ball.sizeRatio = Ball.SIZERATIO.L; // 大
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.XL; // 快，实战貌似是极快
            break;
        case Role.X.id: // 自定义角色
            ball.color = "#305F6F";
            ball.sizeRatio = Ball.SIZERATIO.M; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        case Role.YOUXIA.id:
            ball.color = "#5A5B81"; // 取的默认皮肤衣服颜色
            ball.sizeRatio = Ball.SIZERATIO.S; // 小
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.L; // 快
            break;
        case Role.CHUZI.id:
            ball.color = "#93462A"; // 取的默认皮肤火腿深颜色
            ball.sizeRatio = Ball.SIZERATIO.M; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.S; // 慢
            break;
        case Role.HUAQIANJI.id:
            ball.color = "#4B466C"; // 取的默认皮肤铠甲中颜色
            ball.sizeRatio = Ball.SIZERATIO.XL; // 极大
            ball.mRatio = Ball.WEIGHTRATIO.XL; // 极重
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 0.05; // 无
            break;
        case Role.WUGEGE.id:
            ball.color = "#784820"; // 取的默认皮肤权杖深颜色
            ball.sizeRatio = Ball.SIZERATIO.S; // 小
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.L; // 快
            break;
        case Role.JOKER.id:
            if (!ball.color) ball.color = "#CD1420"; // 取的默认皮肤帽子颜色
            ball.sizeRatio = Ball.SIZERATIO.M; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        case Role.RABBIT.id:
            if (!ball.color) ball.color = "#EF5B87"; // 取的默认皮肤耳朵中度颜色
            ball.sizeRatio = Ball.SIZERATIO.XS; // 极小
            ball.mRatio = Ball.WEIGHTRATIO.XS; // 极轻
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.XL; // 极快
            break;
        case Role.NURSE.id: // 奶妈
            if (!ball.color) ball.color = "#BFD67B"; // 取的默认皮肤头发颜色
            ball.sizeRatio = Ball.SIZERATIO.S; // 小
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.L; // 快
            break;
        case Role.CAPTAIN.id:
            if (!ball.color) ball.color = "#4B49BD"; // 取的默认皮肤衣服颜色
            ball.sizeRatio = Ball.SIZERATIO.L; // 大
            ball.mRatio = Ball.WEIGHTRATIO.L; // 重
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.L; // 快
            break;
        case Role.LELE.id:
            if (!ball.color) ball.color = "#CF3B23"; // 取的默认皮肤衣服颜色
            ball.sizeRatio = Ball.SIZERATIO.M; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.L; // 极快，指碰到角色后；不加速时最多算快
            break;
        case Role.MANWANG.id:
            if (!ball.color) ball.color = "#BE9A8E"; // 取的默认皮肤护甲深颜色
            ball.sizeRatio = Ball.SIZERATIO.XL; // 极大
            ball.mRatio = Ball.WEIGHTRATIO.XL; // 极重
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.XS; // 极慢
            break;
        case Role.LINGLING.id:
            if (!ball.color) ball.color = "#DCD4E5"; // 取的默认皮肤头发中度颜色
            ball.sizeRatio = Ball.SIZERATIO.L; // 大
            ball.mRatio = Ball.WEIGHTRATIO.XS; // 极轻
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        case Role.HUOWANG.id:
            if (!ball.color) ball.color = "#FCA12E"; // 取的默认皮肤火焰深颜色
            ball.sizeRatio = Ball.SIZERATIO.M; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        case Role.LEIMENG.id:
            if (!ball.color) ball.color = "#FF7896"; // 取通行证皮肤头发中颜色
            ball.sizeRatio = Ball.SIZERATIO.M; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.L; // 快
            break;
        case Role.DIANYIN.id:
            if (!ball.color) ball.color = "#98516B"; // 取的默认皮肤头发颜色
            ball.sizeRatio = Ball.SIZERATIO.M; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.XS; // 极轻
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        case Role.XIXUEGUI.id:
            if (!ball.color) ball.color = "#1C2331"; // 取的默认皮肤衣服颜色
            ball.sizeRatio = Ball.SIZERATIO.M; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.XS; // 极轻
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        case Role.GUISHUSHI.id:
            if (!ball.color) ball.color = "#C47244"; // 取的默认皮肤头发颜色
            ball.sizeRatio = Ball.SIZERATIO.M; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.L; // 快
            break;
        case Role.MAGICLION.id:
            if (!ball.color) ball.color = "#F3C264"; // 取的默认皮肤脸部中度颜色
            ball.sizeRatio = Ball.SIZERATIO.S; // 小
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.XS; // 极慢
            break;
        case Role.LANGZAI.id:
            if (!ball.color) ball.color = "#1B1D21"; // 取的默认皮肤毛发中度颜色
            ball.sizeRatio = Ball.SIZERATIO.M; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.L; // 快
            break;
        case Role.BZGIRL.id:
            if (!ball.color) ball.color = "#5D524C"; // 取的默认皮肤头发颜色
            ball.sizeRatio = Ball.SIZERATIO.S; // 小
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.L; // 快
            break;
        case Role.PUMPKIN.id:
            if (!ball.color) ball.color = "#D46E0D"; // 签到送的皮肤脸部颜色
            ball.sizeRatio = Ball.SIZERATIO.M; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        case Role.QUANBA.id:
            if (!ball.color) ball.color = "#0282E6"; // 取的默认皮肤护具颜色
            ball.sizeRatio = Ball.SIZERATIO.S; // 小
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.L; // 快
            break;
        case Role.HONGZHAJI.id:
            if (!ball.color) ball.color = "#C0865B"; // 取的默认皮肤TNT箱子颜色
            ball.sizeRatio = Ball.SIZERATIO.XL; // 极大
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.XS; // 极慢
            break;
        case Role.SANTAIZI.id:
            if (!ball.color) ball.color = "#E14039"; // 取通行证皮肤衣服颜色
            ball.sizeRatio = Ball.SIZERATIO.S; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        case Role.ZHADANKE.id:
            if (!ball.color) ball.color = "#9B3620"; // 取的默认皮肤头发颜色
            ball.sizeRatio = Ball.SIZERATIO.S; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        case Role.HONGSANSAN.id:
            if (!ball.color) ball.color = "#B73B36"; // 取的默认皮肤帽子颜色
            ball.sizeRatio = Ball.SIZERATIO.S; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        case Role.WUKONG.id:
            if (!ball.color) ball.color = "#1B1D22"; // 取的默认皮肤头发深颜色-CC5F22
            ball.sizeRatio = Ball.SIZERATIO.S; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.XL; // 快，实战更接近极快
            break;
        case Role.ZHANAN.id:
            if (!ball.color) ball.color = "#4A406D"; // 取的默认皮肤飞行器翅膀颜色
            ball.sizeRatio = Ball.SIZERATIO.L; // 大
            ball.mRatio = Ball.WEIGHTRATIO.XL; // 极重
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.S; // 慢
            break;
        case Role.XIUNV.id:
            if (!ball.color) ball.color = "#453E3C"; // 取的默认皮肤头巾颜色
            ball.sizeRatio = Ball.SIZERATIO.M; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.L; // 重
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        case Role.TONY.id:
            if (!ball.color) ball.color = "#5C4BAD"; // 取的默认皮肤头发颜色
            ball.sizeRatio = Ball.SIZERATIO.ML; // 大
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        case Role.RENZHE.id:
            if (!ball.color) ball.color = "#B0683C"; // 取的默认皮肤毛发颜色
            ball.sizeRatio = Ball.SIZERATIO.S; // 小
            ball.mRatio = Ball.WEIGHTRATIO.XS; // 极轻
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.XL; // 极快
            break;
        case Role.NUANYANG.id:
            if (!ball.color) ball.color = "#D0C5D5"; // 取的默认皮肤毛发颜色
            ball.sizeRatio = Ball.SIZERATIO.L; // 大
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.S; // 慢
            break;
        case Role.QIANGWEI.id:
            if (!ball.color) ball.color = "#89735E"; // 取的默认皮肤头发颜色
            ball.sizeRatio = Ball.SIZERATIO.M; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.XL; // 极重
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        case Role.LANLAN.id:
            if (!ball.color) ball.color = "#B67B73"; // 取的默认皮肤头发颜色
            ball.sizeRatio = Ball.SIZERATIO.ML; // 偏大
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.XL; // 极快
            break;
        case Role.KAIER.id:
            if (!ball.color) ball.color = "#855E43"; // 取的默认皮肤帽子颜色
            ball.sizeRatio = Ball.SIZERATIO.ML; // 偏大
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        case Role.SHITOUREN.id:
            if (!ball.color) ball.color = "#75837F"; // 取的默认皮肤石头颜色
            ball.sizeRatio = Ball.SIZERATIO.XL; // 极大
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.XS; // 极慢
            break;
        case Role.TIEMIAN.id:
            if (!ball.color) ball.color = "#D69C36"; // 取的默认皮肤铁皮颜色
            ball.sizeRatio = Ball.SIZERATIO.XL; // 极大
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        case Role.MIAOJIANG.id:
            if (!ball.color) ball.color = "#FFA9A9"; // 取的默认皮肤耳朵颜色
            ball.sizeRatio = Ball.SIZERATIO.S; // 小
            ball.mRatio = Ball.WEIGHTRATIO.S; // 轻
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.L; // 快
            break;
        case Role.MUSHI.id:
            if (!ball.color) ball.color = "#A7B278"; // 取的默认皮肤书本颜色
            ball.sizeRatio = Ball.SIZERATIO.M; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        case Role.WUNV.id:
            if (!ball.color) ball.color = "#98747E"; // 取的默认皮肤面纱颜色
            ball.sizeRatio = Ball.SIZERATIO.M; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        case Role.LIANGLIANG.id:
            if (!ball.color) ball.color = "#ED736F"; // 取的默认皮肤头发颜色
            ball.sizeRatio = Ball.SIZERATIO.S; // 小
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        case Role.LAILAI.id:
            if (!ball.color) ball.color = "#AEB34F"; // 取的默认皮肤脸部颜色
            ball.sizeRatio = Ball.SIZERATIO.S; // 小
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        case Role.ZHANGYUGE.id:
            if (!ball.color) ball.color = "#87A8DE"; // 取的默认皮肤触手颜色
            ball.sizeRatio = Ball.SIZERATIO.S; // 小
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.XL; // 极快
            break;
        case Role.HUABANTU.id:
            if (!ball.color) ball.color = "#403B4A"; // 取的默认皮肤衣服颜色
            ball.sizeRatio = Ball.SIZERATIO.M; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.L; // 快，收回滑板后是极快
            break;
        case Role.NIUXIAOMANG.id:
            if (!ball.color) ball.color = "#E8AC85"; // 取的默认皮肤脸部颜色
            ball.sizeRatio = Ball.SIZERATIO.ML; // 偏大
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.XL; // 极快
            break;
        case Role.LANPANG.id:
            if (!ball.color) ball.color = "#4B8BE4"; // 取的默认皮肤T恤颜色
            ball.sizeRatio = Ball.SIZERATIO.L; // 大
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.XL; // 极快
            break;
        case Role.JIANSHI.id:
            if (!ball.color) ball.color = "#48728A"; // 取的默认皮肤剑身颜色
            ball.sizeRatio = Ball.SIZERATIO.M; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.S; // 轻
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.L; // 快
            break;
        case Role.JUNDUN.id:
            if (!ball.color) ball.color = "#607192"; // 取的默认皮肤头盔颜色
            ball.sizeRatio = Ball.SIZERATIO.L; // 大
            ball.mRatio = Ball.WEIGHTRATIO.L; // 重
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.S; // 慢
            break;
        case Role.YOUFANG.id:
            if (!ball.color) ball.color = "#D61D38"; // 取通行证皮肤头发中颜色
            ball.sizeRatio = Ball.SIZERATIO.S; // 小
            ball.mRatio = Ball.WEIGHTRATIO.S; // 轻
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.L; // 快
            break;
        case Role.MOUSE.id:
            if (!ball.color) ball.color = "#95D850"; // 取的默认皮肤领巾颜色
            ball.sizeRatio = Ball.SIZERATIO.XS; // 极小
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        case Role.YEREN.id:
            if (!ball.color) ball.color = "#747A51"; // 取通行证皮肤头发中颜色
            ball.sizeRatio = Ball.SIZERATIO.L; // 大
            ball.mRatio = Ball.WEIGHTRATIO.L; // 重
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        case Role.BAIGUJING.id:
            if (!ball.color) ball.color = "#D9D7E6"; // 取通行证皮肤头发中颜色
            ball.sizeRatio = Ball.SIZERATIO.M; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        case Role.TUYA.id:
            if (!ball.color) ball.color = "#A651EF"; // 取通行证皮肤头发中颜色
            ball.sizeRatio = Ball.SIZERATIO.M; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.XS; // 极轻
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.XL; // 极快
            break;
        case Role.YLPAPA.id:
            if (!ball.color) ball.color = "#817CCD"; // 取的默认皮肤衣服深颜色
            ball.sizeRatio = Ball.SIZERATIO.S; // 小
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.XL; // 快 速度加快一点
            break;
        case Role.YURRONG.id:
            if (!ball.color) ball.color = "#DBA9EC"; // 取通行证皮肤棉服颜色
            ball.sizeRatio = Ball.SIZERATIO.S; // 小
            ball.mRatio = Ball.WEIGHTRATIO.S; // 轻
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.L; // 快
            break;
        case Role.LINGOU.id:
            if (!ball.color) ball.color = "#BAD7FF"; // 取通行证皮肤头发颜色
            ball.sizeRatio = Ball.SIZERATIO.M; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.XL; // 极快
            break;
        case Role.GOLDKING.id:
            if (!ball.color) ball.color = "#9B9A5A"; // 取通行证皮肤头巾颜色
            ball.sizeRatio = Ball.SIZERATIO.M; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.S; // 轻
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        case Role.DUDU.id:
            if (!ball.color) ball.color = "#FC3D39"; // 取的通行证皮肤铠甲颜色
            ball.sizeRatio = Ball.SIZERATIO.M; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        case Role.GEJI.id:
            if (!ball.color) ball.color = "#E4BF93"; // 取默认皮肤头发颜色
            ball.sizeRatio = Ball.SIZERATIO.S; // 小
            ball.mRatio = Ball.WEIGHTRATIO.S; // 轻
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        case Role.YUANSU.id:
            if (!ball.color) ball.color = "#E90131"; // 取默认皮肤头发颜色
            ball.sizeRatio = Ball.SIZERATIO.M; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.S; // 轻
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.L; // 快
            break;
        case Role.TANGSENG.id:
            if (!ball.color) ball.color = "#B6721C"; // 取默认皮肤袈裟颜色
            ball.sizeRatio = Ball.SIZERATIO.M; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        default: // 默认是黑娃
            ball.color = "#74593A"; // 默认皮肤颜色(RosyBrown玫瑰棕)-CA9480；脸颊边缘脸红的颜色(IndianRed印度红)-A36E5D；黑(Black)-151A14；棕色头发(DarkOliveGreen暗橄榄绿)-74593A
            ball.sizeRatio = Ball.SIZERATIO.XS; // 极小 黑娃直径 1.8 格
            ball.mRatio = Ball.WEIGHTRATIO.XS; // 极轻
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.XL; // 极快
        //if (ball.isMainBall) ball.v = 60.00;
        //if (ball.isMainBall) userConfig.isShowBallPath = true; // 是否显示全路径
        //if (ball.isMainBall) userConfig.isStopAfterCollided = true;
    }

    // 公共属性设置
    ball.radius = roundNumber((sysConfig.girdSize * ball.sizeRatio / 2), 4);
    if (ball.roleId != Role.KUILEI.id) ball.tryRadius = ball.radius;
    ball.radiusTmp = ball.radius;
    ball.m = roundNumber(ball.mRatio * sysConfig.maxWeightVal, 4);

    console.log(">>>> initBallByRole ball: " + JSON.stringify(ball));

    // localStorage 存储更新 userConfig 对象
    //localStorage.setItem('collide-try-user-settings', JSON.stringify(userConfig));
}


// 设置字体大小
function setFontSize() {
    if (os.isTablet) {
        // 角色坐标悬浮条字体大小
        let eles = document.getElementsByClassName("collide-try-role-pos-line-font") || [];
        for (let i = 0, len = eles.length; i < len; i++) {
            eles[i].style.fontSize = Math.round(htmlFontSizeNum * sysConfig.pxRatio) + "px";
        }
    }
}


// 根据客户端类型，自动设置页面大小，保持 14:22 的比例
function setPageSize() {
    // 根据客户端类型适配
    //console.log(">>>> os isPc: " + os.isPc);
    if (os.isPc) {
        canvas.height = document.body.clientHeight * sysConfig.sceneWidthRatio; // 网页可见区域高，高多了多一点，导致有垂直滚动条。禁用滚动即可
        // TODO 画布显示大小，通过css样式缩小画布，解决图形模糊和锯齿问题
        //sysConfig.girdSizeCss = Math.round(canvas.height / 22);
        //sysConfig.cssWidth = Math.round(sysConfig.girdSizeCss * 14);
        //sysConfig.cssHeight = Math.round(sysConfig.girdSizeCss * 22);
        sysConfig.girdSizeCss = roundNumber(canvas.height / 22, 4);
        sysConfig.cssWidth = roundNumber(sysConfig.girdSizeCss * 14, 4);
        sysConfig.cssHeight = roundNumber(sysConfig.girdSizeCss * 22, 4);
        // 画布大小适配 dpr
        //sysConfig.girdSize = Math.round(canvas.height / 22 * dpr);
        //sysConfig.girdSize = Math.round(sysConfig.girdSizeCss * dpr);
        sysConfig.girdSize = roundNumber(sysConfig.girdSizeCss * dpr, 4);
    } else { // 其他，手机、平板
        // TODO 手机浏览器非全屏模式，高度看着没居中，但进入全屏模式后，水平、垂直都是居中的
        // 400-712-2.7
        //alert(">>>> 屏幕分辨率-width: " + window.screen.width + ", 屏幕分辨率-height: " + window.screen.height);
        //alert(">>>> 网页可见区域-width: " + document.body.clientWidth + ", 网页可见区域-height: " + document.body.clientHeight);
        //alert(">>>> 屏幕可用工作区域-width: " + window.screen.availWidth + ", 屏幕可用工作区域-height: " + window.screen.availHeight);
        //canvas.width = window.screen.width * sysConfig.sceneWidthRatio;
        canvas.width = document.body.clientWidth * sysConfig.sceneWidthRatio;
        //canvas.width = document.body.clientWidth * 0.8; // 网页可见区域宽
        //canvas.width = window.screen.availWidth * 0.8; // 屏幕可用工作区域宽度
        sysConfig.girdSizeCss = roundNumber(canvas.width / 14, 4);
        sysConfig.cssWidth = roundNumber(sysConfig.girdSizeCss * 14, 4);
        sysConfig.cssHeight = roundNumber(sysConfig.girdSizeCss * 22, 4);
        sysConfig.girdSize = roundNumber(sysConfig.girdSizeCss * dpr, 4);

        /*
        // TODO 不同手机浏览器工具栏高度不同，很可能导致可见高度显示不下画布！适配的高度不能超过网页可见高度，
        // 超过则按网页可见高度重新适配【正常情况高度不会显示不下】
        let ph = document.body.clientHeight;
        if (canvas.height > ph) {
            console.log(">>>> canvas 高度超出网页可见高度，按网页可见高度重新适配...");
            canvas.height = ph * 0.8;
            sysConfig.girdSizeCss = roundNumber(canvas.height / 22, 4);
            sysConfig.cssWidth = roundNumber(sysConfig.girdSizeCss * 14, 4);
            sysConfig.cssHeight = roundNumber(sysConfig.girdSizeCss * 22, 4);
            sysConfig.girdSize = roundNumber(sysConfig.girdSizeCss * dpr, 4);
        }
        */

        //alert(">>>> canvas width: " + canvas.width + ", canvas height: " + canvas.height);
    }


    canvas.width = roundNumber(sysConfig.girdSize * 14, 4);
    canvas.height = roundNumber(sysConfig.girdSize * 22, 4);
    canvas.style.width = sysConfig.cssWidth + 'px';
    canvas.style.height = sysConfig.cssHeight + 'px';
    // 直接用 scale 放大整个坐标系，相对来说就是放大了每个绘制操作
    //context.scale(dpr, dpr);
    console.log(">>>> canvas width: " + canvas.width + ", canvas height: " + canvas.height);
    console.log(">>>> canvas cssWidth: " + sysConfig.cssWidth + ", canvas cssHeight: " + sysConfig.cssHeight);


    // 静态场景大面积区域景物图形层画布设置全屏宽高
    gameSceneGraphCanvas.width = document.body.clientWidth * dpr;
    gameSceneGraphCanvas.height = document.body.clientHeight * dpr;
    gameSceneGraphCanvas.style.width = document.body.clientWidth + 'px';
    gameSceneGraphCanvas.style.height = document.body.clientHeight + 'px';

    // 静态场景景物图形层画布设置全屏宽高
    gameSceneEmojiCanvas.width = document.body.clientWidth * dpr;
    gameSceneEmojiCanvas.height = document.body.clientHeight * dpr;
    gameSceneEmojiCanvas.style.width = document.body.clientWidth + 'px';
    gameSceneEmojiCanvas.style.height = document.body.clientHeight + 'px';

    // 静态场景层画布复制【主运动层画布】宽高
    gameSceneCanvas.width = canvas.width;
    gameSceneCanvas.height = canvas.height;
    gameSceneCanvas.style.width = sysConfig.cssWidth + 'px';
    gameSceneCanvas.style.height = sysConfig.cssHeight + 'px';

    // 静态场景边界线画布设置全屏宽高
    gameSceneLinesCanvas.width = document.body.clientWidth * dpr;
    gameSceneLinesCanvas.height = document.body.clientHeight * dpr;
    gameSceneLinesCanvas.style.width = document.body.clientWidth + 'px';
    gameSceneLinesCanvas.style.height = document.body.clientHeight + 'px';

    // 静态场景边界线背景画布设置全屏宽高
    gameSceneLinesBgCanvas.width = document.body.clientWidth * dpr;
    gameSceneLinesBgCanvas.height = document.body.clientHeight * dpr;
    gameSceneLinesBgCanvas.style.width = document.body.clientWidth + 'px';
    gameSceneLinesBgCanvas.style.height = document.body.clientHeight + 'px';

    // 静态场景砖格边框层设置全屏宽高
    gameSceneCoordinateCanvas.width = document.body.clientWidth * dpr;
    gameSceneCoordinateCanvas.height = document.body.clientHeight * dpr;
    gameSceneCoordinateCanvas.style.width = document.body.clientWidth + 'px';
    gameSceneCoordinateCanvas.style.height = document.body.clientHeight + 'px';

    // 主球运动层画布复制【主运动层画布】宽高
    gameMainBallCanvas.width = canvas.width;
    gameMainBallCanvas.height = canvas.height;
    gameMainBallCanvas.style.width = sysConfig.cssWidth + 'px';
    gameMainBallCanvas.style.height = sysConfig.cssHeight + 'px';

    // 路径层画布复制【主运动层画布】宽高
    gamePathCanvas.width = canvas.width;
    gamePathCanvas.height = canvas.height;
    gamePathCanvas.style.width = sysConfig.cssWidth + 'px';
    gamePathCanvas.style.height = sysConfig.cssHeight + 'px';

    // 全路径层画布复制【主运动层画布】宽高
    gamePathBallCanvas.width = canvas.width;
    gamePathBallCanvas.height = canvas.height;
    gamePathBallCanvas.style.width = sysConfig.cssWidth + 'px';
    gamePathBallCanvas.style.height = sysConfig.cssHeight + 'px';

    // 遮罩层画布复制【主运动层画布】宽高
    gameMaskCanvas.width = canvas.width;
    gameMaskCanvas.height = canvas.height;
    gameMaskCanvas.style.width = sysConfig.cssWidth + 'px';
    gameMaskCanvas.style.height = sysConfig.cssHeight + 'px';


    // 选择角色弹窗复制宽度
    chooseRoleDialog.width = canvas.width;
    chooseRoleDialog.style.width = sysConfig.cssWidth + 'px';
    // 用户设置弹窗复制宽度
    userSettingDialog.width = canvas.width;
    userSettingDialog.style.width = sysConfig.cssWidth + 'px';
    // 主角设置提示弹窗复制宽度
    //gameSettingMainRoleDialog.width = canvas.width;
    //gameSettingMainRoleDialog.style.width = sysConfig.cssWidth + 'px';
    // 用户设置-关于应用弹窗复制宽度
    aboutAppDialog.width = canvas.width;
    aboutAppDialog.style.width = sysConfig.cssWidth + 'px';
    // 更新内容提示弹窗复制宽度
    updateContentDialog.width = canvas.width;
    updateContentDialog.style.width = sysConfig.cssWidth + 'px';
    // 操作指南提示弹窗复制宽度
    howToPlayDialog.width = canvas.width;
    howToPlayDialog.style.width = sysConfig.cssWidth + 'px';


    // 画布最开始是隐藏的，调整大小后，设置为默认显示
    gameSceneCanvas.style.display = "unset"; // 静态场景层画布恢复显示
    canvas.style.display = "unset"; // 主运动层恢复显示
    gameMainBallCanvas.style.display = "unset"; // 主球运动层画布恢复显示
    //gamePathCanvas.style.display = "unset"; // 路径层画布恢复显示
    //gamePathBallCanvas.style.display = "unset"; // 全路径层画布恢复显示
    gameMaskCanvas.style.display = "unset"; // 遮罩层景画布恢复显示
    document.body.style.overflow = 'hidden'; //禁止页面滚动，允许是 visible
}


// 设置弹窗可滚动区域高度【依赖 canvas 宽高】
// height = Math.round(width * 1.63)
function setDialogScrollMaxHeight(hRadio) {
    //let targetHeight = Math.round(canvas.width * hRadio);
    let targetCssHeight = Math.round(sysConfig.cssWidth * hRadio);
    //let targetCssHeight = Math.round(document.body.clientHeight * hRadio);

    // 高度不能超过或太接近页面可见高度
    //if (targetHeight >= gameSceneCanvas.height - 40) targetHeight = Math.round(gameSceneCanvas.height * 0.85);
    if (targetCssHeight >= document.body.clientHeight * 0.90) targetCssHeight = Math.round(document.body.clientHeight * 0.80);

    // 选择角色列表
    let targetElm = document.getElementById('role-list-area');
    if (targetElm) {
        targetElm.style.maxHeight = targetCssHeight + 'px';
    }
    // 参数设置列表
    targetElm = document.getElementById('user-setting-area');
    if (targetElm) {
        targetElm.style.maxHeight = targetCssHeight + 'px';
    }
    // 关于应用内容列表
    targetElm = document.getElementById('user-setting-about-app-content');
    if (targetElm) {
        targetElm.style.maxHeight = targetCssHeight + 'px';
    }
}


// canvas 画布居中显示，需要移动 canvas 画布坐标
function canvasAutoCenter() {
    if (os.isPc) { // PC 端
        // canvas 画布水平、垂直移动到中间
        let w = document.body.clientWidth;
        let h = document.body.clientHeight;
        console.log(">>>> clientWidth:" + w + ", clientHeight:" + h);
        sysConfig.cLeft = roundNumber((w - sysConfig.cssWidth) / 2, 4);
        sysConfig.cTop = roundNumber((h - sysConfig.cssHeight) / 2, 4);
        if (sysConfig.cLeft < 0) sysConfig.cLeft = 0;
        if (sysConfig.cTop < 0) sysConfig.cTop = 0;
        canvas.style.left = sysConfig.cLeft + "px";
        canvas.style.top = sysConfig.cTop + "px";
        console.log(">>>> sysConfig.cLeft:" + sysConfig.cLeft + ", sysConfig.cTop:" + sysConfig.cTop);
        //canvas.style.transform = "translate(" + (w - canvas.width) / 2 + "px, " + (h - canvas.height) / 2 + "px)";
        // 移动 canvas 坐标系，暂时不太会操作
        //context.translate(Math.round((w - canvas.width) / 2), Math.round((h - canvas.height) / 2));
    } else { // 移动端
        // canvas 画布水平、垂直移动到中间
        // 屏幕分辨率宽高
        //let w = window.screen.width;
        //let h = window.screen.height;
        // 网页可见区域宽高
        let w = document.body.clientWidth;
        let h = document.body.clientHeight;
        console.log(">>>> clientWidth:" + w + ", clientHeight:" + h);
        sysConfig.cLeft = roundNumber((w - sysConfig.cssWidth) / 2, 4);
        sysConfig.cTop = roundNumber((h - sysConfig.cssHeight) / 2, 4);
        if (sysConfig.cLeft < 0) sysConfig.cLeft = 0;
        if (sysConfig.cTop < 0) sysConfig.cTop = 0;
        canvas.style.left = sysConfig.cLeft + "px";
        canvas.style.top = sysConfig.cTop + "px";
        console.log(">>>> sysConfig.cLeft:" + sysConfig.cLeft + ", sysConfig.cTop:" + sysConfig.cTop);
    }

    // 静态场景层画布居中
    gameSceneCanvas.style.left = sysConfig.cLeft + "px";
    gameSceneCanvas.style.top = sysConfig.cTop + "px";
    // 主球运动层画布居中
    gameMainBallCanvas.style.left = sysConfig.cLeft + "px";
    gameMainBallCanvas.style.top = sysConfig.cTop + "px";
    // 路径层画布居中
    gamePathCanvas.style.left = sysConfig.cLeft + "px";
    gamePathCanvas.style.top = sysConfig.cTop + "px";
    // 全路径层画布居中
    gamePathBallCanvas.style.left = sysConfig.cLeft + "px";
    gamePathBallCanvas.style.top = sysConfig.cTop + "px";
    // 遮罩层画布居中
    gameMaskCanvas.style.left = sysConfig.cLeft + "px";
    gameMaskCanvas.style.top = sysConfig.cTop + "px";
}


// 设置点按发射按钮画布大小和位置
function setClickPlayCanvas() {
    // 设置图层为显示
    if (userConfig.currPlayOpt === 1) gameClickPlayCanvas.style.display = "unset";
    // 设置大小为 1.68 * 2 格
    gameClickPlayCanvas.width = roundNumber(sysConfig.girdSize * 1.68 * 2, 4);
    gameClickPlayCanvas.height = roundNumber(sysConfig.girdSize * 1.68 * 2, 4);
    gameClickPlayCanvas.style.width = roundNumber(sysConfig.girdSizeCss * 1.68 * 2, 4) + "px";
    gameClickPlayCanvas.style.height = roundNumber(sysConfig.girdSizeCss * 1.68 * 2, 4) + "px";

    // 设置位置，右下角，y距离下墙面2.2格，距离右墙面2.2格
    gameClickPlayCanvas.style.left = roundNumber(sysConfig.cLeft + sysConfig.girdSizeCss * 11.8, 4) + "px";
    gameClickPlayCanvas.style.top = roundNumber(sysConfig.cTop + sysConfig.girdSizeCss * (19.8 - 1.68 * 2), 4) + "px";
}


// 设置四根切角线
function set4AngleLine() {
    lines = []; // 避免重复添加
    // TODO 上面两个切角，起点选x坐标小的，确保旋转后小球碰撞前的相对坐标y为正
    lines.push(new Line(context, { // 左上
        x1: 0,
        y1: Math.round(sysConfig.girdSize * 3 + sysConfig.wan8CocosTableMoveVals[0]),
        x2: Math.round(sysConfig.girdSize * 3 + sysConfig.wan8CocosTableMoveVals[1]),
        y2: 0
    }));
    lines.push(new Line(context, { // 右上
        x1: Math.round(sysConfig.girdSize * 11 + sysConfig.wan8CocosTableMoveVals[2]),
        y1: 0,
        x2: canvas.width,
        y2: Math.round(sysConfig.girdSize * 3 + sysConfig.wan8CocosTableMoveVals[3])
    }));
    // 下面两个切角，起点选x坐标大的
    lines.push(new Line(context, { // 右下
        x2: Math.round(sysConfig.girdSize * 11 + sysConfig.wan8CocosTableMoveVals[5]),
        y2: canvas.height,
        x1: canvas.width,
        y1: Math.round(sysConfig.girdSize * 19 + sysConfig.wan8CocosTableMoveVals[4])
    }));
    lines.push(new Line(context, { // 左下
        x2: 0,
        y2: Math.round(sysConfig.girdSize * 19 + sysConfig.wan8CocosTableMoveVals[7]),
        x1: Math.round(sysConfig.girdSize * 3 + sysConfig.wan8CocosTableMoveVals[6]),
        y1: canvas.height
    }));
}


// 设置四条切角线中点坐标
function set4AngleLineMiddlePoint(lines) {
    linesMiddlePoints = []; // 避免重复添加
    lines.some(line => {
        let p = getLineMiddlePoint({ x: line.x1, y: line.y1 }, { x: line.x2, y: line.y2 });
        //console.log(">>>> p=" + JSON.stringify(p));
        linesMiddlePoints.push(p);
    });
}


// 求线段中点坐标
function getLineMiddlePoint(p1, p2) {
    let p = { x: 0, y: 0 };
    //p.x = Math.round(Math.min(p1.x, p2.x) + (Math.abs(p1.x - p2.x) / 2)); // 会导致一点点误差
    p.x = Math.min(p1.x, p2.x) + (Math.abs(p1.x - p2.x) / 2);
    //p.y = Math.round(Math.min(p1.y, p2.y) + (Math.abs(p1.y - p2.y) / 2));
    p.y = Math.min(p1.y, p2.y) + (Math.abs(p1.y - p2.y) / 2);
    return p;
}


// 求两点之间的距离
function getDistanceOf2Points(p1, p2) {
    let a = roundNumber(Math.abs(p2.x - p1.x), 4);
    let b = roundNumber(Math.abs(p2.y - p1.y), 4);
    let c = roundNumber(Math.sqrt(a * a + b * b), 4);
    return c;
}


// 获取离小球最近的一条切角线下标
function getOneAngleLineIndex(ball) {
    let idx = 0;
    let distance = canvas.height;
    for (let i = 0; i < linesMiddlePoints.length; i++) {
        let d = getDistanceOf2Points({ x: ball.x, y: ball.y }, { x: linesMiddlePoints[i].x, y: linesMiddlePoints[i].y });
        //console.log(">>>> distance=" + d);
        if (d < distance) {
            distance = d;
            idx = i;
        }
    }
    //console.log(">>>> line index=" + idx);
    return idx;
}


// 清除设置分享数据
function clearShareRoleAndPos() {
    // 加载之后，清除导入数据
    shareData = null;
    userConfig.shareRoleAndPos = "";
    localStorage.setItem('collide-try-user-settings', JSON.stringify(userConfig));
    console.log(">>>> clearShareRoleAndPos userConfig in localStorage updated.");
}


// 加载设置分享数据
function setShareRoleAndPos(shareData) {
    balls = [];
    let sBall;
    for (let i = 0, len = shareData.length; i < len; i++) {
        sBall = shareData[i];
        // 砖格转像素
        //let pos = {x:sBall.x, y:sBall.y};
        switchPxOrGird(sBall, 1);
        let ctx = context;
        if (sBall.m) ctx = gameMainBallContext;
        let shareBall = new Ball(ctx, {
            no: sBall.no,
            color: sBall.rc,
            teamColor: sBall.tc,
            roleId: sBall.rid,
            isMainBall: sBall.m ? true : false,
            x: roundNumber(sBall.x, 4),
            y: roundNumber(sBall.y, 4),
        });
        // 初始化其他参数
        initBallByRole(shareBall);

        shareBall.x0 = shareBall.x;
        shareBall.y0 = shareBall.y;
        balls.push(shareBall);
    }

    // 重置角色编号
    //resetMainTeamNo(balls);

    // 是否为一个角色测试
    if (balls.length < 4) userConfig.isTestOnlyOne = true;
    else userConfig.isTestOnlyOne = false;

    // 单独设置小丑分身颜色，因为导入导出数据没有记录角色颜色，roleId初始化角色里面没有配置分身
    setJoker2Color();
}


// 设置主球【改位置】
function setBallMain() {
    let mainBall = new Ball(gameMainBallContext, {
        no: 1,
        teamColor: 'b',
        roleId: userConfig.currRole, // 主球对应角色
        isMainBall: true, // 主球
        x: sysConfig.girdSize * 7, // 水平居中
        //x: sysConfig.girdSize * 1,
        //x: sysConfig.girdSize * 4,
        //x: sysConfig.girdSize * 5,
        y: sysConfig.girdSize * 11, // 垂直居中
        //y: sysConfig.girdSize * 9,
        //y: sysConfig.girdSize * 4,
        vx: 0,
        vy: 0
    });
    // 初始化其他参数
    initBallByRole(mainBall);
    // 设置随机位置坐标
    putBallRandom(mainBall);

    mainBall.x0 = mainBall.x;
    mainBall.y0 = mainBall.y;
    balls.push(mainBall);
}


// 随机放置角色小球
function putBallRandom(ball) {
    // 设置随机位置坐标
    let randomPoint = getRandomPoint(ball.radius);
    ball.x = randomPoint.x;
    ball.y = randomPoint.y;

    // 位置重叠检测
    while (checkBallsCollided(ball)) {
        console.log(">>>> putBallRandom checkBallsCollided " + ball.getBallDesc() + " collided.");
        randomPoint = getRandomPoint(ball.radius);
        ball.x = randomPoint.x;
        ball.y = randomPoint.y;
    }

    ball.x = roundNumber(ball.x, 4);
    ball.y = roundNumber(ball.y, 4);
}


// 随机放置所有角色小球
function putAllBallsRandom() {
    if (!balls || balls.length < 1) return;
    balls.some(ball => {
        // 双子分身除外
        if (ball.roleId === Role.SHUANGZI.id && ball.isRoleBuddy()) return;
        putBallRandom(ball);
    });
}


// 随机放置漩涡位置
function putWhirlpoolRandom() {

}


// 根据所选主角，初始化主角之外的三个角色
function setBallOthersByRole(roleId) {
    if (!roleId) roleId = Role.HEIWA.id;
    let otherRoles = [];

    if (userConfig.isFlashRole) { // 极速开始，常用组合
        let flashGroup = setRolesFlash(userConfig.gameRoleIds, false);
        otherRoles = flashGroup.slice(1);
    } else if (userConfig.isRandomRole) { // 全随机角色
        setRolesRandom(otherRoles);
    } else { // 主角+常用组合
        switch (roleId) {
            //case Role.HEIWA.id: // 走默认
            case Role.JIANGJIANG.id:
                //otherRoles = [Role.JIUWEIHU.id, Role.JIUWEIHU.id, Role.HEIWA.id];
                //otherRoles = [Role.LULU.id, Role.JIANGJIANG.id, Role.LULU.id];
                //otherRoles = [Role.LULU.id, Role.KUILEI.id, Role.YINGYING.id];
                //otherRoles = [Role.LULU.id, Role.DUODUO.id, Role.CHUZI.id];
                //otherRoles = [Role.LULU.id, Role.SHUANGZI.id, Role.YOUXIA.id];
                //otherRoles = [Role.KUKU.id, Role.DUODUO.id, Role.HUAQIANJI.id];
                //otherRoles = [Role.LULU.id, Role.KUILEI.id, Role.JOKER.id];
                //otherRoles = [Role.KUKU.id, Role.JOKER.id, Role.WUGEGE.id];
                //otherRoles = [Role.LULU.id, Role.BAKE.id, Role.DUODUO.id];
                //otherRoles = [Role.KUKU.id, Role.BAKE.id, Role.DUODUO.id];
                //otherRoles = [Role.KUKU.id, Role.JOKER.id, Role.RABBIT.id];
                otherRoles = [];
                let mainCp = Role.JIANGJIANG.cps[fullCloseInt(0, Role.JIANGJIANG.cps.length - 1)]; // 主角搭配
                //console.log(">>>> mainCp=", mainCp);
                otherRoles.push(mainCp);
                let otherCps = RegularlyCollocation.getRandomGroup(); // 对手搭配
                //console.log(">>>> otherCps=" + otherCps.toString());
                otherRoles = otherRoles.concat(otherCps);
                //if (sysConfig.isSayGoodbye && !isProd()) otherRoles = [Role.KUKU.id, Role.BAKE.id, Role.RABBIT.id];
                //console.log(">>>> otherRoles=" + otherRoles.toString());
                break;
            case Role.DUODUO.id:
                //otherRoles = [Role.BAKE.id, Role.KUILEI.id, Role.YINGYING.id];
                //otherRoles = [Role.BAKE.id, Role.DUODUO.id, Role.BAKE.id];
                otherRoles = [Role.DUODUO.cps[fullCloseInt(0, Role.DUODUO.cps.length - 1)]].concat(RegularlyCollocation.getRandomGroup());
                //if (sysConfig.isSayGoodbye && !isProd()) otherRoles = [Role.BAKE.id, Role.JOKER.id, Role.DIANYIN.id];
                break;
            case Role.KUILEI.id:
                //otherRoles = [Role.YINGYING.id, Role.BAKE.id, Role.DUODUO.id];
                //otherRoles = [Role.JOKER.id, Role.BAKE.id, Role.DUODUO.id];
                otherRoles = [Role.KUILEI.cps[fullCloseInt(0, Role.KUILEI.cps.length - 1)]].concat(RegularlyCollocation.getRandomGroup());
                //if (sysConfig.isSayGoodbye && !isProd()) otherRoles = [Role.JOKER.id, Role.JIANGJIANG.id, Role.MANWANG.id];
                break;
            case Role.SHUANGZI.id:
                //otherRoles = [Role.JOKER.id, Role.JOKER.id, Role.RABBIT.id];
                //otherRoles = [Role.JOKER.id, Role.SHUANGZI.id, Role.RABBIT.id];
                //otherRoles = [Role.JOKER.id, Role.LEIMENG.id, Role.JIUWEIHU.id];
                otherRoles = [Role.SHUANGZI.cps[fullCloseInt(0, Role.SHUANGZI.cps.length - 1)]].concat(RegularlyCollocation.getRandomGroup());
                //if (sysConfig.isSayGoodbye && !isProd()) otherRoles = [Role.DIANYIN.id, Role.BAKE.id, Role.RABBIT.id];
                break;
            case Role.KUKU.id:
                //otherRoles = [Role.HEIWA.id, Role.BAKE.id, Role.DUODUO.id];
                otherRoles = [Role.HEIWA.id].concat(RegularlyCollocation.getRandomGroup());
                //if (sysConfig.isSayGoodbye && !isProd()) otherRoles = [Role.HEIWA.id, Role.BAKE.id, Role.DUODUO.id];
                break;
            case Role.LELE.id:
                otherRoles = [Role.LELE.cps[fullCloseInt(0, Role.LELE.cps.length - 1)]].concat(RegularlyCollocation.getRandomGroup());
                //if (sysConfig.isSayGoodbye && !isProd()) otherRoles = [Role.HEIWA.id, Role.CAPTAIN.id, Role.YINGYING.id];
                break;
            default:
                //otherRoles = [Role.WUGEGE.id, Role.LULU.id, Role.WUGEGE.id];
                //otherRoles = [Role.KUKU.id, Role.LULU.id, Role.JIANGJIANG.id];
                //otherRoles = [Role.JIUWEIHU.id, Role.JIUWEIHU.id, Role.JIANGJIANG.id];
                //otherRoles = [Role.KUKU.id, Role.BAKE.id, Role.DUODUO.id];
                //otherRoles = [Role.RABBIT.id, Role.RABBIT.id, Role.BAKE.id];
                otherRoles = [Role.HEIWA.cps[fullCloseInt(0, Role.HEIWA.cps.length - 1)]].concat(RegularlyCollocation.getRandomGroup());
            //if (sysConfig.isSayGoodbye && !isProd()) otherRoles = [Role.LULU.id, Role.SANTAIZI.id, Role.LEIMENG.id];
        }
    }

    // 非随机模式，有指定角色，则替换角色id
    if (!userConfig.isRandomRole && isUseGameRoleIds()) {
        for (let i = 0, len = userConfig.gameRoleIds.length; i < len; i++) {
            if (i === 0) continue; // 第一个为主角，这里是设置主角之外的角色，所以排除主角
            //if (userConfig.gameRoleIds[i] < 0) continue;
            otherRoles[i - 1] = userConfig.gameRoleIds[i];
        }
    }

    // 检测角色id
    doCkeckOtherRoles(otherRoles);
    console.log(">>>> setBallOthersByRole otherRoles=" + otherRoles);

    // 公共设置
    setRoleOthers(otherRoles);
}


// 主角已经设置了，这里只用设置其他三个辅助角色及分身
function setRolesRandom(otherRoles) {
    let rid;
    for (let i = 2; i <= 4; i++) { // 设置 2、3、4 号角色
        // 同队角色不能一样。即编号1、2角色不能一样；3、4也不能一样
        rid = Role.getRandomRoleId();
        while (i === 2 && rid === userConfig.currRole) { // 不能和主角一样
            rid = Role.getRandomRoleId();
        }
        while (i === 4 && rid === otherRoles[1]) { // 不能和队友一样
            rid = Role.getRandomRoleId();
        }
        otherRoles.push(rid);
    }
}


// 设置极速开始，补全常用组合
function setRolesFlash(roleIds, isSetCurrRole) {
    if (!roleIds) roleIds = userConfig.gameRoleIds;
    let flashRoles = [];
    // 有指定角色，补全常用组合
    if (isUseGameRoleIds()) {
        // 第一队角色补全
        if (isUseGameRoleIdsFull(1)) { // 设置了俩
            flashRoles.push(roleIds[0]);
            flashRoles.push(roleIds[1]);
        } else if (roleIds[0] < 0 && roleIds[1] < 0) { // 俩都没设置
            if (isSetCurrRole) { // 重新选择主角
                flashRoles = flashRoles.concat(RegularlyCollocation.getRandomGroup()); // concat() 方法不会更改现有数组，而是返回一个新数组，其中包含已连接数组的值。
            } else {
                flashRoles.push(userConfig.currRole);
                let role = Role.getRoleById(userConfig.currRole);
                flashRoles.push(role.cps[fullCloseInt(0, role.cps.length - 1)]);
            }
        } else if (roleIds[0] > -1) { // 设置了第一个
            // 找到设置角色的常用搭配
            let role = Role.getRoleById(roleIds[0]);
            flashRoles.push(roleIds[0]);
            flashRoles.push(role.cps[fullCloseInt(0, role.cps.length - 1)]);
        } else if (roleIds[1] > -1) { // 设置了第二个
            let role = Role.getRoleById(roleIds[1]);
            flashRoles.push(role.cps[fullCloseInt(0, role.cps.length - 1)]);
            flashRoles.push(roleIds[1]);
        }
        // 第二队角色补全
        if (isUseGameRoleIdsFull(2)) {
            flashRoles.push(roleIds[2]);
            flashRoles.push(roleIds[3]);
        } else if (roleIds[2] < 0 && roleIds[3] < 0) {
            flashRoles = flashRoles.concat(RegularlyCollocation.getRandomGroup());
        } else if (roleIds[2] > -1) {
            let role = Role.getRoleById(roleIds[2]);
            flashRoles.push(roleIds[2]);
            flashRoles.push(role.cps[fullCloseInt(0, role.cps.length - 1)]);
        } else if (roleIds[3] > -1) {
            let role = Role.getRoleById(roleIds[3]);
            flashRoles.push(role.cps[fullCloseInt(0, role.cps.length - 1)]);
            flashRoles.push(roleIds[3]);
        }
    } else { // 全新常用组合
        // 第一队
        if (isSetCurrRole) { // 重新选择主角
            flashRoles = flashRoles.concat(RegularlyCollocation.getRandomGroup());
        } else {
            flashRoles.push(userConfig.currRole);
            let role = Role.getRoleById(userConfig.currRole);
            flashRoles.push(role.cps[fullCloseInt(0, role.cps.length - 1)]);
        }
        // 第二队
        flashRoles = flashRoles.concat(RegularlyCollocation.getRandomGroup());
    }

    // 设置主角id
    if (isSetCurrRole) userConfig.currRole = flashRoles[0];

    return flashRoles;
}


// 角色id检查，避免id为负数；避免同一队选中两个一样的角色
function doCkeckOtherRoles(otherRoles) {
    console.log(">>>> doCkeckOtherRoles before otherRoles=" + otherRoles);
    if (otherRoles.length > 3) otherRoles = otherRoles.slice(0, 3); // slice[tart, end) 开区间 不改变原数组
    // 第一队校验
    if (otherRoles[0] < 0 || otherRoles[0] === userConfig.currRole) {
        let role = Role.getRoleById(userConfig.currRole);
        otherRoles[0] = role.cps[fullCloseInt(0, role.cps.length - 1)];
    }
    // 第二队校验
    if (otherRoles[1] > -1 && otherRoles[2] > -1) { // 两个都设置了
        if (otherRoles[1] === otherRoles[2]) { // 俩角色一样
            let role = Role.getRoleById(otherRoles[1]);
            otherRoles[2] = role.cps[fullCloseInt(0, role.cps.length - 1)];
        }
    } else if (otherRoles[1] < 0 && otherRoles[2] < 0) { // 两个都没设置
        let group = RegularlyCollocation.getRandomGroup();
        otherRoles[1] = group[0];
        otherRoles[2] = group[1];
    } else if (otherRoles[1] > -1) { // 设置了第一个
        let role = Role.getRoleById(otherRoles[1]);
        otherRoles[2] = role.cps[fullCloseInt(0, role.cps.length - 1)];
    } else if (otherRoles[2] > -1) { // 设置了第二个
        let role = Role.getRoleById(otherRoles[2]);
        otherRoles[1] = role.cps[fullCloseInt(0, role.cps.length - 1)];
    }

    //console.log(">>>> doCkeckOtherRoles after otherRoles=" + otherRoles);
}


// 设置主角之外的角色
function setRoleOthers(otherRoles) {
    if (!otherRoles || otherRoles.length < 1) return;
    let idx = 2;
    otherRoles.some(rid => {
        // 非主球只能移动和被撞击
        let otherBall = new Ball(context, {
            no: idx,
            teamColor: idx > 2 ? 'r' : 'b',
            roleId: rid,
            isMainBall: false,
            x: 0,
            y: 0,
            vx: 0,
            vy: 0
        });
        // 初始化其他参数
        initBallByRole(otherBall);
        // 设置随机位置坐标
        putBallRandom(otherBall);
        otherBall.x0 = otherBall.x;
        otherBall.y0 = otherBall.y;
        balls.push(otherBall);
        idx += 1;
    });
}


// 设置小丑分身
function setRoleJoker() {
    let rid;
    for (let i = 0, len = balls.length; i < len; i++) { // len = balls.length 只取一次值，目前 len 可能为 1 或 4
        rid = balls[i].roleId;
        if (rid !== Role.JOKER.id) continue;

        let otherBall = new Ball(context, {
            no: balls.length + 1, // 这里的 balls.length 会在 balls.push 之后增加
            teamColor: i > 1 ? 'r' : 'b',
            color: '#A8A8A8A8', // 小丑分身单独颜色，取默认皮肤帽子颜色
            roleId: rid,
            isMainBall: false,
            x: 0,
            y: 0,
            vx: 0,
            vy: 0
        });
        // 初始化其他参数
        initBallByRole(otherBall);
        // 设置随机位置坐标
        putBallRandom(otherBall);
        otherBall.x0 = otherBall.x;
        otherBall.y0 = otherBall.y;
        balls.push(otherBall);
    }
}


// 导入分享数据后，设置小丑分身颜色
function setJoker2Color() {
    if (!balls || balls.length < 1) return;
    let ball;
    for (let i = 0, len = balls.length; i < len; i++) {
        ball = balls[i];
        if (ball.roleId !== Role.JOKER.id) continue;
        if (ball.isMainBall) continue;

        if (len < 4) { // 单独一个角色测试
            ball.color = '#A8A8A8A8';
        } else { // 四个角色
            if (ball.no < 5) continue;
            ball.color = '#A8A8A8A8';
        }
    }
}


// 设置双子分身
function setTwins() {
    if (!balls || balls.length < 1) return;
    // 双子分身
    twinBall.no = balls.length + 1;
    twinBall.roleId = Role.SHUANGZI.id;
    twinBall.color = '#CACAE3'; // 分身衣服颜色
    twinBall.teamColor = balls[0].teamColor;
    twinBall.x = Ball.BODY2POS.x;
    twinBall.y = Ball.BODY2POS.y;
    twinBall.x0 = Ball.BODY2POS.x;
    twinBall.y0 = Ball.BODY2POS.y;
    // 初始化其他参数
    initBallByRole(twinBall);
    balls.push(twinBall);
}


// 初始设置猴子分身坐标
function setMonkeysPos() {
    // 猴子分身位置坐标
    monkeysPos = [
        { x: 3.1 * sysConfig.girdSize, y: 2.9 * sysConfig.girdSize },
        { x: 11.5 * sysConfig.girdSize, y: 3.4 * sysConfig.girdSize },
        { x: 2.3 * sysConfig.girdSize, y: 18.4 * sysConfig.girdSize },
        { x: 11.1 * sysConfig.girdSize, y: 18.8 * sysConfig.girdSize }
    ];

    // 猴子分身目标点位置坐标
    monkeysTargetPos = [
        { x: 13 * sysConfig.girdSize, y: 11 * sysConfig.girdSize },
        { x: 7 * sysConfig.girdSize, y: 21 * sysConfig.girdSize },
        { x: 7 * sysConfig.girdSize, y: 1 * sysConfig.girdSize },
        { x: 1 * sysConfig.girdSize, y: 11 * sysConfig.girdSize }
    ];
}


// 设置猴子分身
function setMonkeys() {
    if (!balls || balls.length < 1) return;
    // 重置分身数组
    buddies = [];
    // 目前猴子有4个分身
    for (let i = 0, len = 4; i < len; i++) {
        let otherBall = new Ball(gameMainBallContext, {
            no: balls.length + i + 1,
            teamColor: balls[0].teamColor,
            color: '#CC5F22', //《黑神话：悟空》衣服颜色-1B1D22
            roleId: Role.WUKONG.id,
            isMainBall: false,
            x: 0,
            y: 0,
            vx: 0,
            vy: 0
        });
        // 初始化其他参数
        initBallByRole(otherBall);
        // 设置随机位置坐标
        //putBallRandom(otherBall);
        // 指定初始位置
        otherBall.x = monkeysPos[i].x;
        otherBall.y = monkeysPos[i].y;
        otherBall.x0 = otherBall.x;
        otherBall.y0 = otherBall.y;
        buddies.push(otherBall);
    }
}


// 判断猴子分身
function isMonkeys() {
    if (!buddies || buddies.length < 1) return false;
    for (let i = 0, len = buddies.length; i < len; i++) {
        if (buddies[i].roleId != Role.WUKONG.id) return false;
    }
    return true;
}


// 判断是否包含所有猴子分身
function isContainFullMonkeys() {
    if (!balls || balls.length < 1) return false;
    let count = 0;
    for (let i = 0, len = balls.length; i < len; i++) {
        if (balls[i].roleId == Role.WUKONG.id && !balls[i].isMainBall) count++;
    }
    if (count < 4) return false;
    return true;
}


// 重置分身属性变量
function resetBuddies() {
    if (!buddies || buddies.length < 1) return;
    // 重置角色字段属性值
    resetRoleField(buddies);
    // 重置速度和位置
    for (let i = 0, len = buddies.length; i < len; i++) {
        buddies[i].v = 0;
        buddies[i].vx = 0;
        buddies[i].vy = 0;
        buddies[i].x = 0
        buddies[i].y = 0
        buddies[i].x0 = 0
        buddies[i].y0 = 0
        if (isMonkeys()) { // 猴子分身
            buddies[i].x = monkeysPos[i].x;
            buddies[i].y = monkeysPos[i].y;
            buddies[i].x0 = buddies[i].x;
            buddies[i].y0 = buddies[i].y;
        }
    }
}


// 初始化猴子分身速度
function initBuddiesSpeed() {
    if (!buddies || buddies.length < 1) return;
    if (!isMonkeys()) return;
    if (balls[0].roleId != Role.WUKONG.id) return;
    if (balls[0].v <= 0) return;
    for (let i = 0, len = buddies.length; i < len; i++) {
        buddies[i].v = balls[0].v; // checkFriction() 方法需要用于计算摩擦力
        getVxVy({ x: monkeysTargetPos[i].x, y: monkeysTargetPos[i].y }, { x: monkeysPos[i].x, y: monkeysPos[i].y }, balls[0].v, buddies[i]);
    }
}


// 准备猴子分身
function preMonkeys() {
    if (!balls || balls.length < 1) return;
    // 创建分身，balls 数组加入 buddies
    if (!buddies || buddies.length < 1) setMonkeys();
    // 初始化参数
    initBuddiesSpeed();
    // balls 数组加入 buddies
    if (!isContainFullMonkeys()) balls = balls.concat(buddies);
}


// 猴子分身运动完成后
function afterMonkeys() {
    // balls 数组移除 buddies
    if (isContainFullMonkeys()) balls = balls.splice(0, balls.length - buddies.length);
    // 重置参数
    resetBuddies();
}


// 画猴子分身起始位置
function drawMonkeysStart() {
    if (!buddies || buddies.length < 1) return;
    if (!isMonkeys()) return;
    if (balls[0].roleId != Role.WUKONG.id) return;
    for (let i = 0, len = buddies.length; i < len; i++) {
        buddies[i].drawBuddyBeginPoint({ ctx: gameSceneContext, color: currTheme.wkShowColor ? currTheme.wkShowColor : "#1B1D2230" });
    }
}


// 画猴子分身运动方向
function drawMonkeysMoveLine() {
    if (!buddies || buddies.length < 1) return;
    if (!isMonkeys()) return;
    if (balls[0].roleId != Role.WUKONG.id) return;
    for (let i = 0, len = buddies.length; i < len; i++) {
        drawArrow(gameSceneContext, monkeysPos[i].x, monkeysPos[i].y, monkeysTargetPos[i].x, monkeysTargetPos[i].y, 30, roundNumber(0.80 * sysConfig.girdSize, 4), roundNumber(3.20 * dpr * sysConfig.pxRatio, 4), currTheme.wkShowColor ? currTheme.wkShowColor : "#1B1D2230"); // "#7F726E"
    }
}


// 随机设置主角所在队颜色
function resetMainTeamColorRandom(mtc) {
    if (!balls || balls.length < 1) return;
    if (!mtc) { // main team color
        let n = fullCloseInt(1, 100);
        if (n % 2 === 0) mtc = 'r';
        else mtc = 'b';
    }
    if (balls[0].teamColor === mtc) return;
    // teamColor 取反
    balls.some(ball => {
        if (ball.teamColor === 'r') ball.teamColor = 'b';
        else ball.teamColor = 'r';
    });
    // 参数设置角色输入框颜色跟着变化
    let roleInputEles = document.getElementsByClassName("div-input-game-roles");
    if (!roleInputEles || roleInputEles.length !== 4) return;
    let mtcNew = balls[0].teamColor;
    for (let i = 0, len = 4; i < len; i++) {
        // 如果主角在红队，则前两个输入框红色、后两个蓝色
        if (mtcNew === 'r') {
            if (i < 2) roleInputEles[i].classList.add("red");
            else roleInputEles[i].classList.remove("red");
        } else { // 如果主角在蓝队，则前两个输入框蓝色、后两个红色
            if (i < 2) roleInputEles[i].classList.remove("red");
            else roleInputEles[i].classList.add("red");
        }
        // 存在则删除，不存在则添加
        //roleInputEles[i].classList.toggle("red");
    }
    // 重置角色编号
    //resetMainTeamNo(balls);
}


// TODO 设置主角所在对编号【很多地方用到了初始编号做条件判断，之前的逻辑是主球编号一定是1，改动影响的地方比较多】
function resetMainTeamNo(balls) {
    if (!balls || balls.length < 1) return;
    if (userConfig.isTestOnlyOne) return;
    // 目前硬性规则，四个角色，蓝队编号1、2，红队编号3、4
    for (let i = 0, len = 4; i < len; i++) {
        if (balls[i].teamColor === 'b') {
            if (i % 2 === 0) balls[i].no = 1;
            else balls[i].no = 2;
        } else {
            if (i % 2 === 0) balls[i].no = 3;
            else balls[i].no = 4;
        }
    }
}


// 设置蛋
function setEggs() {
    if (!balls || balls.length < 1) return;
    eggs = [];
    for (let i = 0; i < balls.length; i++) {
        if (balls[i].roleId !== Role.DUODUO.id) continue;
        if (balls[i].teamColor === 'r') {
            eggs.push(new Ball(context, {
                roleId: Ball.SPECIALROLEID.eggId, // 蛋不对应角色
                x: 7 * sysConfig.girdSize,
                y: 22 * sysConfig.girdSize,
                vx: 0,
                vy: 0,
                radius: sysConfig.girdSize,
                color: '#CE605B',
                m: sysConfig.maxWeightVal, // 蛋不会动，给最大质量
            }));
        } else {
            eggs.push(new Ball(context, {
                roleId: Ball.SPECIALROLEID.eggId,
                x: 7 * sysConfig.girdSize,
                y: 0 * sysConfig.girdSize,
                vx: 0,
                vy: 0,
                radius: sysConfig.girdSize,
                color: '#2A7CE9',
                m: sysConfig.maxWeightVal,
            }));
        }
    }
}


// 不刷新页面，重新设置蛋
function resetEggs() {
    // 重新设置蛋
    setEggs();
    // gameSceneCanvas 场景层清空重画
    clearCanvasAll(gameSceneCanvas);
    // 填充背景色
    drawSceneBg();
    // 画网格，在背景色之后
    drawSceneGrid();
    // 夏日主题画间隔颜色的砖格
    if (userConfig.sceneThemeMode === 5) drawSceneGridRect();
    // 墙面切角
    clipTableAngles();
    // 画蛋
    drawEggs();
}


// 获取随机位置坐标点
function getRandomPoint(radius, targetCanvas) {
    if (!targetCanvas) targetCanvas = canvas;
    let p = { x: 0, y: 0 };
    p.x = randomPos(radius, "x", targetCanvas);
    p.y = randomPos(radius, "y", targetCanvas);
    while (!checkRandomPos(radius, p.x, p.y)) {
        p.x = randomPos(radius, "x", targetCanvas);
        p.y = randomPos(radius, "y", targetCanvas);
    }
    return p;
}


// [n,m)范围随机数 Math.random()*(m-n)+n
function randomPos(radius, need, targetCanvas) {
    // x [radius+1, targetCanvas.width-radius)
    if (need === "x") return fullOpen(radius + 1, targetCanvas.width - radius);
    // y [radius+1, targetCanvas.height-radius)
    if (need === "y") return fullOpen(radius + 1, targetCanvas.height - radius);
    return 0;
}


// 检测随机坐标
function checkRandomPos(radius, x, y) {
    //console.log(">>>> checkRandomPos x=" + x + ", y=" + y);
    tempCheckBall.x = x;
    tempCheckBall.y = y;
    tempCheckBall.radius = radius;
    // 粗略检测是否在四条切角线区域
    //if (isInAngleArea(tempCheckBall) > -1) return false;
    // 检测墙面碰撞
    if (checkWallCollided(tempCheckBall)) return false;
    // 检测切面碰撞
    if (checkLineCollided(tempCheckBall)) return false;
    return true;
}


// 检测新加入角色与场上角色坐标是否有冲突
function checkBallsCollided(newBall) {
    let result = false;
    balls.some(ball => {
        if (newBall !== ball) { // 不是自己
            if (is2CirclesCollided(newBall, ball)) {
                result = true;
                return true; // 只是退出了循环
            }
        }
    });
    if (result) return result;

    // 继续检测是否与蛋的位置冲突
    //if(eggs) console.log(eggs.length); // 设置角色的时候还没有设置蛋
    /*
    if (eggs && eggs.length > 0) {
        result = isBallAndEggCollided(newBall);
    }
    */

    // 小球区域不能碰到蛋的区域
    if (isInEggArea(newBall)) result = true;
    //console.log(">>>> checkBallsCollided isBallAndEggCollided=" + result + " > " + newBall.getBallDesc());

    return result;
}


// 根据手机DPR设置速度
function setSpeed() {
    if (!balls || balls.length < 1) return;
    let speed = 0;
    // 根据屏幕大小动态设置初始速度，如果速度不变，在小分辨率屏幕上跑的更远。60/644 = x/canvas.width x=60/644*canvas.width
    //speed = roundNumber(60 / 644 * canvas.width, 4);
    // 根据 dpr 动态设置初始速度 74/2.7 = x/dpr >>>> x=74/2.7*dpr
    //sysConfig.bounce = 2;
    console.log(">>>> sysConfig.bounce=" + sysConfig.bounce);
    if (sysConfig.bounce > 0) { // sysConfig.bounce=2，碰撞有损耗，横向直打距离正常（水平碰撞次数多），竖直距离偏大一些（竖直碰撞次数少）
        // TODO 还需要真机模拟校准
        speed = getHeiwaSpeedByDpr() * balls[0].vRatio + sysConfig.bounce * 4; // 娃横向直打会碰四次，加上损耗的四次
    } else { // sysConfig.bounce <= 0，碰撞无损耗，横向直打距离正常，竖直距离跟实战接近，但小球发射速度稍微慢一点
        // 设置主球速度，目前只支持主球可以发射
        speed = getHeiwaSpeedByDpr() * balls[0].vRatio;
    }
    // 配置了加速或减速
    if (userConfig.roleSpeedAddVal) {
        console.log(">>>> userConfig.roleSpeedAddVal=" + userConfig.roleSpeedAddVal);
        speed += userConfig.roleSpeedAddVal;
    }
    speed = roundNumber(speed, 4);
    console.log(">>>> main ball speed=" + speed);
    balls[0].v = speed;
}


// 获取原始速度
function getBallSpeed0(ball) {
    let speed = 0;
    // 根据屏幕大小动态设置初始速度，如果速度不变，在小分辨率屏幕上跑的更远。60/644 = x/canvas.width x=60/644*canvas.width
    //speed = roundNumber(60 / 644 * canvas.width, 4);
    // 根据 dpr 动态设置初始速度 74/2.7 = x/dpr >>>> x=74/2.7*dpr
    //sysConfig.bounce = 2;
    //console.log(">>>> sysConfig.bounce=" + sysConfig.bounce);
    if (sysConfig.bounce > 0) { // sysConfig.bounce=2，碰撞有损耗，横向直打距离正常（水平碰撞次数多），竖直距离偏大一些（竖直碰撞次数少）
        // TODO 还需要真机模拟校准
        speed = getHeiwaSpeedByDpr() * ball.vRatio + sysConfig.bounce * 4; // 娃横向直打会碰四次，加上损耗的四次
    } else { // sysConfig.bounce <= 0，碰撞无损耗，横向直打距离正常，竖直距离跟实战接近，但小球发射速度稍微慢一点
        // 设置主球速度，目前只支持主球可以发射
        speed = getHeiwaSpeedByDpr() * ball.vRatio;
    }
    speed = roundNumber(speed, 4);
    return speed;
}


// 根据手机dpr获取黑娃的速度，其他角色速度取黑娃相对值，比如僵尸的速度是黑娃的0.9倍
function getHeiwaSpeedByDpr() {
    // 不同设备黑娃横打的时间相同 t=d/v=46*girdSize/90.00=46*60.1714/99.3498≈27.86
    // 初始化时会根据 dpr 计算 girdSize 
    // v=d/t
    //let v = roundNumber(46 * sysConfig.girdSize / 27.86, 4);
    // 99.3498 / 842 = v / canvas.width
    let v = roundNumber(90.00 / 842 * canvas.width, 4);
    // 与帧率反相关 60Hz v2 = 60 / fps * v
    //v = roundNumber(60 / fpsCheckRst * v, 4);
    //console.log(">>>> getHeiwaSpeedByDpr v=" + v);
    return v;
}


// 根据canvas.width设置摩擦力
// f=μ×Fn 假设 μ 都一样，地面都是水平方向，Fn = μmg
function setFriction() {
    // 正相关 3.20 / 842 = f / canvas.width
    // dpr=2.7 canvas.width=842 sysConfig.friction=3.20
    sysConfig.friction = roundNumber(2.60 / 842 * canvas.width, 4);
    // 与帧率反相关 60Hz f = 60 / fps * sysConfig.friction
    //sysConfig.friction = roundNumber(60 / fpsCheckRst * sysConfig.friction, 4);
    console.log(">>>> sysConfig.friction=" + sysConfig.friction);
}


// 检测角色是否存在
function checkRoleExist() {
    isDuoduoExist = checkIsDuoduoExist();
    isLuluExist = checkIsLuluExist();
    isShuangziExist = checkIsShuangziExist();
}


// 静态游戏桌面场景初始化
function gameSceneInit() {
    let sceneInitTime0 = new Date().getTime();
    // 画游戏台面
    drawTable();
    console.log(">>>> gameSceneInit 游戏场景初始化耗时：" + (new Date().getTime() - sceneInitTime0) + " ms");
}


// 四个角色里面是否有朵朵，用于控制是否画蛋
// 设置一个变量，初始化的时候判断一次，不建议每次都调用判断方法
function checkIsDuoduoExist() {
    let result = false;
    balls.some(ball => {
        //console.log(">>>> ball.roleId=" + ball.roleId);
        if (ball.roleId === Role.DUODUO.id) {
            result = true;
            return true; // 只是退出循环
        }
    });
    return result;
}


// 是否有露露，判断是否画玻璃球
function checkIsLuluExist() {
    let result = false;
    balls.some(ball => {
        //console.log(">>>> ball.roleId=" + ball.roleId);
        if (ball.roleId === Role.LULU.id && ball.no === 2) {
            result = true;
            return true; // 只是退出循环
        }
    });
    return result;
}


// 是否有双子，仅限主球
function checkIsShuangziExist() {
    let result = false;
    balls.some(ball => {
        //console.log(">>>> ball.roleId=" + ball.roleId);
        if (ball.isMainBall && ball.roleId === Role.SHUANGZI.id) {
            result = true;
            return true; // 只是退出循环
        }
    });
    return result;
}


// 绘制游戏台面
function drawTable() {
    // 填充背景色
    drawSceneBg();
    // 画网格，在背景色之后
    drawSceneGrid();
    // 夏日主题画间隔颜色的砖格
    if (userConfig.sceneThemeMode === 5) drawSceneGridRect();
    // 墙面切角
    clipTableAngles();
    // 设置场景主题
    if (userConfig.currRole > -1) setSceneTheme(); // 未选择角色，不渲染场景，节省性能
    // 画台面边框，放在主题设置之后，确保边框覆盖emoji图形
    if (userConfig.isShowTableBorder) doDrawTableLines();
    // 画砖格坐标
    if (userConfig.isShowGridCoordinate) drawSceneCoordinate();
    // 画蛋
    if (isDuoduoExist) drawEggs();
    // 画猴子分身起点和运动方向
    if (userConfig.currRole == Role.WUKONG.id && userConfig.isShowWkPath) {
        drawMonkeysStart();
        drawMonkeysMoveLine();
    }
    if (userConfig.isShowSceneGraph && !userConfig.isUseCustomTheme) { // 是否显示场景图形
        // 夏日主题个别动物上台面
        if (userConfig.sceneThemeMode === 5) {
            drawIconRandom("🦀", "ss", 1, false, true, gameSceneCanvas);
            drawIconRandom("🦀", "xxs", 2, false, true, gameSceneCanvas);
        }
    }

    // 在点按发射钮图层，画发射按钮，全局只画一次
    clickPlayBtn.drawClickPlayBtn();
}


// 重新绘制游戏台面和场景
function reDrawTable(drawArr) {
    /*
    // 先清理画布
    clearCanvasAll(gameSceneCanvas); // 台面层
    clearCanvasAll(gameSceneLinesCanvas); // 台面边框层
    clearCanvasAll(gameSceneCoordinateCanvas); // 台面砖格坐标层
    clearCanvasAll(gameSceneEmojiCanvas); // emoji、svg 图形层
    // 其他操作
    // 大图形坐标列表重置，用来检测图形重叠
    largeEmojiPoints = [];
    // 再重新绘制
    drawTable();
    */
    const isAll = (!drawArr || drawArr.length < 1);
    // 1-重新绘制游戏台面
    if (isAll || drawArr.includes(1)) reDrawTableAndEgg();
    // 2-重画台面边框和砖格坐标
    if (isAll || drawArr.includes(2)) reDrawTableLineAndGirdNum();
    // 3-重新绘制场景图形（emoji、svg）
    if (isAll || drawArr.includes(3)) reDrawSceneGraph();
}


// 重新绘制游戏台面
function reDrawTableAndEgg() {
    // 先清理画布
    clearCanvasAll(gameSceneCanvas); // 台面层
    // 重新绘制台面
    // 填充背景色
    drawSceneBg();
    // 画网格，在背景色之后
    drawSceneGrid();
    // 夏日主题画间隔颜色的砖格
    if (userConfig.sceneThemeMode === 5) drawSceneGridRect();
    // 墙面切角
    clipTableAngles();
    // 画蛋
    if (isDuoduoExist) drawEggs();
    // 画猴子分身起点和运动方向
    if (userConfig.currRole == Role.WUKONG.id && userConfig.isShowWkPath) {
        drawMonkeysStart();
        drawMonkeysMoveLine();
    }
    if (userConfig.isShowSceneGraph && !userConfig.isUseCustomTheme) { // 是否显示场景图形
        // 重画场景中心图形
        if (userConfig.sceneThemeMode === 0) drawCenterGraphSvg("svg-default-center");
        if (userConfig.sceneThemeMode === 1) drawCenterGraphSvg("svg-snow");
        // 夏日主题个别动物上台面
        if (userConfig.sceneThemeMode === 5) {
            drawIconRandom("🦀", "ss", 1, false, true, gameSceneCanvas);
            drawIconRandom("🦀", "xxs", 2, false, true, gameSceneCanvas);
        }
    }
}


// 重新绘制场景图形（emoji、svg）
function reDrawSceneGraph() {
    // 先清空图形层画布
    clearCanvasAll(gameSceneEmojiCanvas); // emoji、svg 图形层
    clearCanvasAll(gameSceneGraphCanvas); // graph 特殊图形层
    // 大图形坐标列表重置，用来检测图形重叠
    largeEmojiPoints = [];
    // 设置场景主题，未选择角色，不渲染场景，节省性能
    if (userConfig.currRole > -1) setSceneTheme();
}


// 重画台面边框和砖格坐标
function reDrawTableLineAndGirdNum() {
    clearCanvasAll(gameSceneLinesCanvas); // 台面边框层
    clearCanvasAll(gameSceneLinesBgCanvas); // 台面边框背景层
    clearCanvasAll(gameSceneCoordinateCanvas); // 台面砖格坐标层
    // 画台面边框，放在主题设置之后，确保边框覆盖emoji图形
    if (userConfig.isShowTableBorder) doDrawTableLines();
    // 画砖格坐标
    if (userConfig.isShowGridCoordinate) drawSceneCoordinate();
}


// 画网格
// https://juejin.cn/post/6844904042062151688
function drawSceneGrid() {

    gameSceneContext.save();
    gameSceneContext.beginPath();
    gameSceneContext.lineWidth = currTheme.glWidth;
    //gameSceneContext.shadowColor = '#5A5030';
    //gameSceneContext.shadowBlur = 1 * dpr;

    // 1. 设置网格大小
    // girdSize

    // 2. 获取Canvas的width、height
    let CanvasWidth = gameSceneCanvas.width;
    let CanvasHeight = gameSceneCanvas.height;

    // 3. 采用遍历的方式，画水平线条
    //let xLineTotals = Math.floor(CanvasHeight / sysConfig.girdSize); // 计算需要绘画的x轴条数【会有一些误差，导致少画线问题】
    let xLineTotals = 22;
    for (let i = 0; i <= xLineTotals; i++) {
        gameSceneContext.beginPath(); // 开启路径，设置不同的样式
        gameSceneContext.moveTo(0, sysConfig.girdSize * i); // -0.5是为了解决像素模糊问题
        gameSceneContext.lineTo(CanvasWidth, sysConfig.girdSize * i);
        gameSceneContext.strokeStyle = currTheme.glColor;
        if (i === 11) gameSceneContext.strokeStyle = currTheme.glmColor;
        gameSceneContext.stroke();
    }

    // 4.采用遍历的方式，画垂直线条
    //let yLineTotals = Math.floor(CanvasWidth / sysConfig.girdSize); // 计算需要绘画y轴的条数
    let yLineTotals = 14;
    for (let j = 0; j <= yLineTotals; j++) {
        gameSceneContext.beginPath(); // 开启路径，设置不同的样式
        gameSceneContext.moveTo(sysConfig.girdSize * j, 0);
        gameSceneContext.lineTo(sysConfig.girdSize * j, CanvasHeight);
        gameSceneContext.strokeStyle = currTheme.glColor;
        if (j === 7) gameSceneContext.strokeStyle = currTheme.glmColor;
        gameSceneContext.stroke();
    }

    gameSceneContext.restore();
}


// 画间隔颜色的砖格
function drawSceneGridRect() {
    // 设置了背景图片不画
    if (indexedDB && userConfig.isUseCustomTheme) return; // && isAImageFileName(currTheme.bgImage)
    gameSceneContext.save();
    gameSceneContext.beginPath();
    gameSceneContext.lineWidth = roundNumber(1 * dpr * sysConfig.pxRatio, 4);
    //gameSceneContext.shadowColor = '#5A5030';
    //gameSceneContext.shadowBlur = 1 * dpr;

    // 1. 设置网格大小
    // girdSize

    // 2. 获取Canvas的width、height
    let CanvasWidth = gameSceneCanvas.width;
    let CanvasHeight = gameSceneCanvas.height;

    let xLineTotals = 22;
    let yLineTotals = 14;
    for (let i = 0; i < xLineTotals; i++) {
        for (let j = 0; j < yLineTotals; j++) {
            if (i % 2 === 0) { // 偶数行
                if (j % 2 === 0) { // 偶数列
                    gameSceneContext.fillStyle = "#FFA35D"; // 夏日主题-砖格深颜色填充
                } else { // 奇数列
                    gameSceneContext.fillStyle = "#FFC777"; // 夏日主题-砖格浅颜色填充
                }
            } else { // 奇数行-相反
                if (j % 2 !== 0) {
                    gameSceneContext.fillStyle = "#FFA35D"; // 夏日主题-砖格深颜色填充
                } else {
                    gameSceneContext.fillStyle = "#FFC777"; // 夏日主题-砖格浅颜色填充
                }
            }

            gameSceneContext.globalAlpha = Math.random(); // 随机透明度
            //if (gameSceneContext.fillStyle === "#FFC777") gameSceneContext.globalAlpha = 1.0; // 浅颜色填充不设置透明度
            gameSceneContext.fillRect(j * sysConfig.girdSize, i * sysConfig.girdSize, sysConfig.girdSize - gameSceneContext.lineWidth * Math.random(), sysConfig.girdSize - gameSceneContext.lineWidth * Math.random());

        }
    }

    gameSceneContext.restore();
}


// 画砖格坐标
function drawSceneCoordinate() {

    gameSceneCoordinateContext.save();
    gameSceneCoordinateContext.textAlign = "center";
    gameSceneCoordinateContext.textBaseline = 'middle';
    gameSceneCoordinateContext.font = currTheme.gnSize + "px serif";

    // 移动坐标系到画布中心
    //gameSceneCoordinateContext.translate(roundNumber(gameSceneCoordinateCanvas.width / 2), roundNumber(gameSceneCoordinateCanvas.height / 2));
    gameSceneCoordinateContext.translate(gameSceneCoordinateCanvas.width / 2, gameSceneCoordinateCanvas.height / 2);

    // 间隔宽度
    let sceneLineNumMargin = roundNumber(sysConfig.sceneLineWidth * 1.3, 4);
    if (userConfig.isShowTableBorder) sceneLineNumMargin += roundNumber(currTheme.tblWidth * 1.1);

    let CanvasWidth = gameSceneCanvas.width;
    let CanvasHeight = gameSceneCanvas.height;

    // 画左右边界砖格坐标
    let xLineTotals = 22; // 多少个横排
    let xLineNum = 8; // 开始值
    if (userConfig.isShowGridCoordinateFull) xLineNum = 11; // 显示完全坐标（包括切角砖格）
    for (let i = 1; i <= xLineTotals; i++) {
        // 切角砖格坐标不用画
        if (!userConfig.isShowGridCoordinateFull && ((i > -1 && i < 4) || (i > 19 && i <= 22))) continue;
        gameSceneCoordinateContext.beginPath(); // 开启路径，设置不同的样式
        gameSceneCoordinateContext.fillStyle = currTheme.gnColor; // 设置每个线条的颜色
        if (isDarkMode) gameSceneCoordinateContext.fillStyle = currTheme.gndColor;
        gameSceneCoordinateContext.fillText(xLineNum, -(CanvasWidth / 2 + sceneLineNumMargin), -(CanvasHeight / 2 + sysConfig.girdSize / 2) + sysConfig.girdSize * i);
        gameSceneCoordinateContext.fillText(xLineNum, (CanvasWidth / 2 + sceneLineNumMargin), -(CanvasHeight / 2 + sysConfig.girdSize / 2) + sysConfig.girdSize * i);
        if (i < 11) xLineNum--;
        if (i > 11) xLineNum++;
    }

    // 画上下边界砖格坐标
    let yLineTotals = 14; // 多少个竖排
    let yLineNum = 4; // 开始值
    if (userConfig.isShowGridCoordinateFull) yLineNum = 7; // 显示完全坐标（包括切角砖格）
    for (let j = 1; j <= yLineTotals; j++) {
        // 切角砖格坐标不用画
        if (!userConfig.isShowGridCoordinateFull && ((j > -1 && j < 4) || (j > 11 && j <= 14))) continue;
        gameSceneCoordinateContext.fillText(yLineNum, -(CanvasWidth / 2 + sysConfig.girdSize / 2) + sysConfig.girdSize * j, -(CanvasHeight / 2 + sceneLineNumMargin));
        gameSceneCoordinateContext.fillText(yLineNum, -(CanvasWidth / 2 + sysConfig.girdSize / 2) + sysConfig.girdSize * j, (CanvasHeight / 2 + sceneLineNumMargin));
        if (j < 7) yLineNum--;
        if (j > 7) yLineNum++;
    }

    gameSceneCoordinateContext.restore();
}


// 判断坐标是否在砖格坐标区域
function isInGirdNumArea(p) {
    if (!p) return false;

    let result = false;

    gameSceneCoordinateContext.save();
    gameSceneCoordinateContext.textAlign = "center";
    gameSceneCoordinateContext.textBaseline = 'middle';
    gameSceneCoordinateContext.font = currTheme.gnSize + "px serif";

    // 移动坐标系到画布中心
    //gameSceneCoordinateContext.translate(gameSceneCoordinateCanvas.width / 2, gameSceneCoordinateCanvas.height / 2);
    // 间隔宽度
    let sceneLineNumMargin = roundNumber(sysConfig.sceneLineWidth * 1.3, 4);
    if (userConfig.isShowTableBorder) sceneLineNumMargin += roundNumber(currTheme.tblWidth * 1.1);
    sceneLineNumMargin = sceneLineNumMargin / 4;

    // 获取坐标数值字体宽度
    let metrics, width;
    metrics = gameSceneCoordinateContext.measureText("11");
    width = roundNumber(metrics.width + sysConfig.girdSize * 0.4, 4);
    //console.log(width);

    // 检测点击坐标是否在砖格坐标数值区域
    if (
        ((p.y >= (sysConfig.cTop * dpr - sceneLineNumMargin - width) && p.y <= (sysConfig.cTop * dpr + canvas.height + sceneLineNumMargin + width)) // y 轴区域限制
            && ((p.x >= (sysConfig.cLeft * dpr - sceneLineNumMargin - width) && p.x <= (sysConfig.cLeft * dpr - sceneLineNumMargin)) // x 轴左半区域
                || (p.x >= (sysConfig.cLeft * dpr + canvas.width + sceneLineNumMargin) && p.x <= (sysConfig.cLeft * dpr + canvas.width + sceneLineNumMargin + width)) // x 轴右半区域
            ))
        ||
        ((p.x >= (sysConfig.cLeft * dpr - sceneLineNumMargin - width) && p.x <= (sysConfig.cLeft * dpr + canvas.width + sceneLineNumMargin + width)) // x 轴区域限制
            && ((p.y >= (sysConfig.cTop * dpr - sceneLineNumMargin - width) && p.y <= (sysConfig.cTop * dpr - sceneLineNumMargin)) // y 轴上半区域
                || (p.y >= (sysConfig.cTop * dpr + canvas.height + sceneLineNumMargin) && p.y <= (sysConfig.cTop * dpr + canvas.height + sceneLineNumMargin + width)))) // y 轴下半区域
    ) result = true;

    gameSceneCoordinateContext.restore();

    return result;
}


// 画场景背景色
function drawSceneBg() {
    // 设置了背景图片不画
    //if (indexedDB && userConfig.isUseCustomTheme && isAImageFileName(currTheme.bgImage)) return;
    gameSceneContext.save();
    gameSceneContext.fillStyle = currTheme.tbColor;
    gameSceneContext.fillRect(0, 0, gameSceneCanvas.width, gameSceneCanvas.height);
    // 设置dialog弹窗确认按钮颜色为场景背景色
    setDialogOkColor(gameSceneContext.fillStyle);
    gameSceneContext.restore();
}


// 四个切角剪切掉
function clipTableAngles() {
    // 左上角
    let p0 = { x: 0, y: 0 };
    let p1 = { x: sysConfig.girdSize * 3 + sysConfig.wan8CocosTableMoveVals[1], y: 0 }; // 玩吧撞击台面，刻意混淆调整了角度
    let p2 = { x: 0, y: sysConfig.girdSize * 3 + sysConfig.wan8CocosTableMoveVals[0] };
    let points = [p0, p1, p2];
    doGraphClip(points, gameSceneCanvas);

    // 右上角
    p0 = { x: sysConfig.girdSize * 11 + sysConfig.wan8CocosTableMoveVals[2], y: 0 };
    p1 = { x: gameSceneCanvas.width, y: 0 };
    p2 = { x: gameSceneCanvas.width, y: sysConfig.girdSize * 3 + sysConfig.wan8CocosTableMoveVals[3] };
    points = [p0, p1, p2];
    doGraphClip(points, gameSceneCanvas);

    // 右下角
    p0 = { x: gameSceneCanvas.width, y: sysConfig.girdSize * 19 + sysConfig.wan8CocosTableMoveVals[4] };
    p1 = { x: gameSceneCanvas.width, y: gameSceneCanvas.height };
    p2 = { x: sysConfig.girdSize * 11 + sysConfig.wan8CocosTableMoveVals[5], y: gameSceneCanvas.height };
    points = [p0, p1, p2];
    doGraphClip(points, gameSceneCanvas);

    // 左下角
    p0 = { x: sysConfig.girdSize * 3 + sysConfig.wan8CocosTableMoveVals[6], y: gameSceneCanvas.height };
    p1 = { x: 0, y: gameSceneCanvas.height };
    p2 = { x: 0, y: sysConfig.girdSize * 19 + sysConfig.wan8CocosTableMoveVals[7] };
    points = [p0, p1, p2];
    doGraphClip(points, gameSceneCanvas);

}


// 默认主题左右两个边框剪切掉
function clipDefaultTableLines() {
    // 左边框
    let p0 = { x: 0, y: 0 };
    let p1 = { x: gameSceneLinesCanvas.width / 2 - sysConfig.girdSize * 7, y: 0 };
    let p2 = { x: gameSceneLinesCanvas.width / 2 - sysConfig.girdSize * 7, y: gameSceneLinesCanvas.height };
    let p3 = { x: 0, y: gameSceneLinesCanvas.height };
    let points = [p0, p1, p2, p3];
    doGraphClip(points, gameSceneLinesCanvas);

    // 右边框
    p0 = { x: gameSceneLinesCanvas.width / 2 + sysConfig.girdSize * 7, y: 0 };
    p1 = { x: gameSceneLinesCanvas.width, y: 0 };
    p2 = { x: gameSceneLinesCanvas.width, y: gameSceneLinesCanvas.height };
    p3 = { x: gameSceneLinesCanvas.width / 2 + sysConfig.girdSize * 7, y: gameSceneLinesCanvas.height };
    points = [p0, p1, p2, p3];
    doGraphClip(points, gameSceneLinesCanvas);
}


// 执行图形剪切
function doGraphClip(points, tCanvas) {
    if (!points) return; // null [] undefined
    let ctx = tCanvas.getContext('2d');
    ctx.save();
    ctx.fillStyle = "#00000000"; // 透明
    ctx.beginPath();
    for (let i = 0; i < points.length; i++) {
        if (i === 0) ctx.moveTo(points[i].x, points[i].y);
        else ctx.lineTo(points[i].x, points[i].y);
    }
    ctx.clip(); // 裁剪
    ctx.clearRect(0, 0, tCanvas.width, tCanvas.height); // clip()指定了剪辑区域，这里只会清除指定区域内容
    ctx.fill();
    ctx.restore();
}


// 设置场景主题
function setSceneTheme() {
    switch (userConfig.sceneThemeMode) {
        case 1: // 冰雪主题
            if (userConfig.isShowSceneGraph) { // 是否显示场景图形
                // 桌面中心图形
                //drawCenterGraphIcon();
                drawCenterGraphSvg("svg-snow");
                // 冰雪主题景物图形
                drawIconUpAndDown("🎄", "l", 1);
                drawIconUpAndDown("🎄", "m", 1, true); // 随机
                drawIconUpAndDown("🎄", "mm", 1);
                drawIconUpAndDown("🎁", "s", 1, true); // 随机
                drawIconUpAndDown("🎁", "ss", 1);
                drawIconUpAndDown("🎁", "xs", 1);
                drawIconUpAndDown("⛄️", "m", 1);
                drawIconUpAndDown("⛄️", "s", 1, true); // 随机
                drawIconUpAndDown("⛄️", "ss", 1, true);
                drawIconUpAndDown("❄️", "xs", 2, true);
                drawIconUpAndDown("❄️", "xxs", 4, true);
                drawIconRandom("❄️", "xs", 10);
                drawIconRandom("❄️", "xxs", 10);
                drawIconRandom("❄️", "xxxs", 20);
                drawIconRandom("🎄", "mm", 1);
                drawIconRandom("🎁", "xs", 1);
                drawIconRandom("⛄️", "ss", 1);
            }
            break;
        case 2: // 新年主题
            break;
        case 3: // 田园主题
            if (userConfig.isShowSceneGraph) {
                // 花草树木，鸡鸭鹅狗猪牛羊【先后顺序可控制图形叠加效果】
                drawIconUpAndDown("🌹", "xxs", 4, true);
                drawIconRandom("🌹", "xxs", 8);
                drawIconUpAndDown("🌼", "xxs", 2, true);
                drawIconRandom("🌼", "xxs", 4);
                drawIconUpAndDown("🌷", "xxs", 4, true);
                drawIconRandom("🌷", "xxs", 8);
                drawIconUpAndDown("🌱", "xxs", 4, true);
                drawIconRandom("🌱", "xxxs", 4);
                drawIconUpAndDown("🌻", "mm", 1);
                drawIconRandom("🌻", "s", 2);
                drawIconRandom("🌾", "ss", 2);
                drawIconRandom("🌵", "mm", 1);
                drawIconRandom("🌵", "ss", 1);
                drawIconRandom("🥕", "xs", 4);
                drawIconRandom("🍄", "xxxs", 4);
                if (isWoodIconShow) drawIconRandom("🪵", "ss", 2);
                drawIconRandom("🥚", "xxs", 5);
                drawIconUpAndDown("🛵", "fll", 1, true, 2); // 随机、下方
                drawIconUpAndDown("🌳", "l", 1);
                drawIconRandom("🌳", "s", 1);
                drawIconRandom("🐕", "s", 2);
                drawIconRandom("🐖", "m", 1);
                drawIconRandom("🐖", "mm", 1, true, false);
                drawIconRandom("🐖", "mm", 1);
                drawIconRandom("🐂", "l", 1);
                drawIconRandom("🐂", "ll", 1, true, false);
                drawIconRandom("🐄", "l", 1);
                drawIconRandom("🐄", "ll", 1, true, false);
                drawIconRandom("🐏", "mm", 1);
                drawIconRandom("🐑", "mm", 1);
                drawIconRandom("🐑", "mm", 1, true, false);
                drawIconRandom("🐈", "ss", 1);
                drawIconRandom("🐇", "ss", 1);
                drawIconRandom("🐇", "xs", 1);
                drawIconRandom("🐍", "xs", 1);
                drawIconRandom("🐀", "xxs", 1);
                drawIconRandom("🐌", "xxxs", 4);
                drawIconRandom("🐝", "xxxs", 4);
                drawIconRandom("🦋", "xxs", 2);
                drawIconUpAndDown("🐓", "ss", 1, false, 1); // 只画上/左方
                drawIconRandom("🐓", "ss", 3);
                drawIconRandom("🦃", "ss", 5);
                drawIconUpAndDown("🦆", "ss", 1, false, 2); // 只画下/右方
                drawIconRandom("🦆", "ss", 3);
            }
            break;
        case 4: // 星际主题
            if (userConfig.isShowSceneGraph) {
                // 画星系光亮
                //drawGalaxyLight();
                // 画随机星系光亮
                globalParams.shadowColor = "#7F9BC2";
                globalParams.shadowBlur = 100 * dpr;
                drawGalaxyLightRandom(null, "mm", 1);
                drawGalaxyLightRandom(null, "s", 2);
                drawGalaxyLightRandom(null, "ss", 2);
                drawGalaxyLightRandom(null, "xs", 5);
                drawGalaxyLightRandom(null, "xxs", 10);
                drawGalaxyLightRandom(null, "xxxs", 15);
                drawIconUpAndDown("🛰️", "mm", 1);
                drawIconUpAndDown("🌏", "s", 1, false, 2); // 只画下/右方
                //drawIconRandom("🌏", "s", 1);
                //drawIconRandom("🌕", "xxs", 1); // 月球位置应该跟随地球
                if (isRingedIconShow)
                    drawIconUpAndDown("🪐", "s", 1, false, 2); // 只画下/右方
                drawIconRandom("☄️", "ss", 2);
                drawIconRandom("☄️", "xs", 2);
                drawIconRandom("⭐", "xxs", 10);
                drawIconRandom("⭐", "xxxs", 15);
                drawIconRandom("🛰️", "s", 2);
                drawIconRandom("🚀", "ss", 2);
                drawIconRandom("🛸", "s", 2);
                //drawIconRandom("👨‍🚀", "ss", 1);
                //drawIconRandom("👩‍🚀", "ss", 1);
                drawIconUpAndDown("👩‍🚀", "ss", 1, true, 1);
                drawIconUpAndDown("👨‍🚀", "ss", 1, true, 2);
            }
            break;
        case 5: // 夏日主题
            if (userConfig.isShowSceneGraph) {
                // 图形先后顺序可以控制叠加效果
                drawIconUpAndDown("🏝️", "l", 1, true);
                //drawIconUpAndDown("🏝️", "xl", 1, false, 1); // 只画上/左方
                drawIconUpAndDown("🛟", "ss", 1, true); // 救生圈
                drawIconUpAndDown("🌊", "ss", 1, true);
                drawIconUpAndDown("🏖️", "s", 1, true);
                drawIconUpAndDown("🏄", "s", 1, true, 1);
                drawIconUpAndDown("🏄‍♀️", "s", 1, true, 2);
                drawIconRandom("🛟", "ss", 1); // 救生圈
                drawIconRandom("🏄", "s", 1); // 不允许跟台面重叠，出现概率会小一些
                drawIconRandom("🏄", "s", 1, true, false); // 增大出现的概率
                drawIconRandom("🏄‍♀️", "s", 1);
                drawIconRandom("🏄‍♀️", "s", 1, true, false);
                drawIconRandom("🏊", "s", 1);
                drawIconRandom("🏊", "s", 1, true, false);
                drawIconRandom("🏊‍♀️", "s", 1);
                drawIconRandom("🏊‍♀️", "s", 1, true, false);
                drawIconRandom("🌊", "ss", 2);
                drawIconRandom("🌊", "xxs", 5);
                drawIconRandom("🐚", "xxxs", 4);
                drawIconRandom("⛵️", "m", 2);
                drawIconRandom("⛵️", "m", 1, true, false);
                drawIconRandom("🚤", "m", 2);
                drawIconRandom("🚤", "m", 1, true, false);
                drawIconRandom("🪂", "m", 2);
                drawIconRandom("🪂", "m", 1, true, false);
                //drawIconRandom("🐳", "m", 1); // 场地太挤了
                drawIconRandom("🐋", "m", 1);
                drawIconRandom("🦈", "s", 1);
                drawIconRandom("🐬", "s", 1);
                drawIconRandom("🐟", "xxs", 15);
                drawIconRandom("🦞", "xxs", 2);
                drawIconRandom("🦀", "xxs", 4);
                drawIconRandom("🐡", "xxs", 2);
                drawIconRandom("🐙", "xxs", 2);
                drawIconRandom("🦑", "xxs", 2);
                drawIconRandom("🪼", "xxs", 2); // 水母
                drawIconRandom("🪸", "ss", 2); // 珊瑚
                drawIconRandom("🪸", "xxs", 8); // 珊瑚
                drawIconRandom("🐢", "ss", 1);
                drawSvgUpAndDown("svg-yl-duck", "s", 1, true);
            }
            break;
        default: // 默认主题
            if (userConfig.isShowSceneGraph) {
                // 中心图形
                drawCenterGraphSvg("svg-default-center");
                // 指定位置画石头和骨头
                drawStoneGraphDefault();
                // 画骨头
                drawSvgUpAndDown("svg-bone", "mm", 1, false, 1);
                drawSvgUpAndDown("svg-bone", "s", 1, false, 2);
                drawSvgUpAndDown("svg-bone", "xxs", 2, true);
                drawSvgRandom("svg-bone", "s", 1, true, true);
                drawSvgRandom("svg-bone", "xs", 2, true, true);
                drawSvgRandom("svg-bone", "xxs", 6, true, true);
                // 画石头
                /*
                if (isRockIconShow) {
                    drawIconUpAndDown("🪨", "mm", 1);
                    drawIconUpAndDown("🪨", "s", 1);
                    drawIconRandom("🪨", "s", 2);
                    drawIconRandom("🪨", "ss", 6);
                    drawIconRandom("🪨", "xxs", 15);
                }
                */
                // 改为画svg石头
                drawSvgUpAndDown("svg-stone", "s", 2, false, 1);
                drawSvgUpAndDown("svg-stone", "ss", 2, false, 2);
                drawSvgUpAndDown("svg-stone", "xxs", 4, true);
                drawSvgRandom("svg-stone", "ss", 2, false, true);
                drawSvgRandom("svg-stone", "xxs", 6, false, true);
            }
    }

    // 默认主题剪掉左右边框
    //if (userConfig.sceneThemeMode === 0) clipDefaultTableLines();
    // 设置主题背景颜色
    setBodyBackgroundColor(Theme.getBgColorById(userConfig.sceneThemeMode));
    // 设置自定义背景颜色
    setBodyBackgroundColor(currTheme.bgColor);
}


// 设置body背景颜色
function setBodyBackgroundColor(hex) {
    if (!Theme.isColorCode(hex)) return; // 颜色码格式不正确
    if (indexedDB && userConfig.isUseCustomTheme && isAImageFileName(currTheme.bgImage)) return; // 设置背景图片则返回
    document.body.style.backgroundColor = hex;
}


function doDrawTableLines() {
    globalParams.shadowColor = "#352e6160";
    //if (userConfig.sceneThemeMode === 1 && isLightMode) globalParams.shadowColor = "#819BC3"; // 冰雪主题边框阴影
    // 填充一次台面背景颜色
    drawTableLines(true);
    globalParams.shadowBlur = 6 * dpr;
    drawTableLines();
    globalParams.shadowBlur = 1 * dpr;
    drawTableLines();
}


// 边框阴影只用画一次，性能影响不大
// gameSceneLines画布全屏，坐标移到正中间
function drawTableLines(isFill) {
    gameSceneLinesContext.save();
    if (globalParams) { // 设置阴影
        gameSceneLinesContext.shadowColor = globalParams.shadowColor;
        gameSceneLinesContext.shadowBlur = globalParams.shadowBlur;
    }
    gameSceneLinesContext.strokeStyle = currTheme.tblColor; // 边框颜色
    gameSceneLinesContext.lineWidth = currTheme.tblWidth; // 边框线宽
    // 移动坐标系到场景中心
    gameSceneLinesContext.translate(roundNumber(gameSceneLinesCanvas.width / 2, 4), roundNumber(gameSceneLinesCanvas.height / 2, 4));
    gameSceneLinesContext.beginPath();
    gameSceneLinesContext.moveTo(-sysConfig.girdSize * 4 - currTheme.tblWidth / 4 + sysConfig.wan8CocosTableMoveVals[1], -sysConfig.girdSize * 11 - currTheme.tblWidth / 2); // 起点，上边框左端点
    gameSceneLinesContext.lineTo(sysConfig.girdSize * 4 + currTheme.tblWidth / 4 + sysConfig.wan8CocosTableMoveVals[2], -sysConfig.girdSize * 11 - currTheme.tblWidth / 2); // 上边框
    gameSceneLinesContext.lineTo(sysConfig.girdSize * 7 + currTheme.tblWidth / 2, -sysConfig.girdSize * 8 - currTheme.tblWidth / 4 + sysConfig.wan8CocosTableMoveVals[3]); // 右上角斜边框
    gameSceneLinesContext.lineTo(sysConfig.girdSize * 7 + currTheme.tblWidth / 2, sysConfig.girdSize * 8 + currTheme.tblWidth / 4 + sysConfig.wan8CocosTableMoveVals[4]); // 右边框
    gameSceneLinesContext.lineTo(sysConfig.girdSize * 4 + currTheme.tblWidth / 4 + sysConfig.wan8CocosTableMoveVals[5], sysConfig.girdSize * 11 + currTheme.tblWidth / 2); // 右下角斜边框
    gameSceneLinesContext.lineTo(-sysConfig.girdSize * 4 - currTheme.tblWidth / 4 + sysConfig.wan8CocosTableMoveVals[6], sysConfig.girdSize * 11 + currTheme.tblWidth / 2); // 下边框
    gameSceneLinesContext.lineTo(-sysConfig.girdSize * 7 - currTheme.tblWidth / 2, sysConfig.girdSize * 8 + currTheme.tblWidth / 4 + sysConfig.wan8CocosTableMoveVals[7]); // 左下角斜边框
    gameSceneLinesContext.lineTo(-sysConfig.girdSize * 7 - currTheme.tblWidth / 2, -sysConfig.girdSize * 8 - currTheme.tblWidth / 4 + sysConfig.wan8CocosTableMoveVals[0]); // 左边框
    gameSceneLinesContext.closePath(); // 闭合路径，左上角斜边框
    if (!isFill) {
        gameSceneLinesContext.stroke();
    } else {
        // 由于边框和场景用的不是一个坐标系，为了避免边框误差出现缝隙，填充一层背景颜色
        // 采用内容复制的方式
        // 先隐藏边框图层
        gameSceneLinesCanvas.style.display = "none";
        // 清除画布内容，注意，这里清空画布，会导致没有内容
        //clearCanvasAll(gameSceneLinesCanvas);
        // 填充边框背景
        gameSceneLinesContext.fillStyle = currTheme.tbColor; // 台面背景颜色
        //gameSceneLinesContext.globalCompositeOperation = "source-over";
        gameSceneLinesContext.fill();

        // 复制到边框背景图层画布
        gameSceneLinesBgContext.save();
        const dataURL = gameSceneLinesCanvas.toDataURL();
        const image = new Image();
        image.src = dataURL;
        image.onload = function () {
            gameSceneLinesBgContext.drawImage(image, 0, 0);
        };
        gameSceneLinesBgContext.restore();
        // 再次清空边框层画布
        clearCanvasAll(gameSceneLinesCanvas);
        // 还原边框层显示
        gameSceneLinesCanvas.style.display = "inherit";
    }
    gameSceneLinesContext.restore();
}


// 【中心布局ICON】
// 中心雪花❄️ 画在游戏场景画布上  3 * sysConfig.girdSize ≤ height ≤ 5 * sysConfig.girdSize
// 雪花因为字体原因，会出现不能完全居中
function drawCenterGraphIcon(icon, size, num) {
    gameSceneContext.save();
    gameSceneContext.fillStyle = "#EEF0F220";
    // 水平对齐方式 (center left right start end)
    gameSceneContext.textAlign = "center";
    // 垂直对齐的方式 (top bottom middle)
    gameSceneContext.textBaseline = 'middle';

    let content = "❄";
    let fontSize = 8;
    let metrics, width, height;

    gameSceneContext.font = fontSize * dpr + "px serif";
    metrics = gameSceneContext.measureText(content);
    width = roundNumber(metrics.width, 4);
    height = roundNumber(metrics.actualBoundingBoxAscent + metrics.actualBoundingBoxDescent, 4);

    while (height > 5 * sysConfig.girdSize) {
        fontSize -= 1;
        gameSceneContext.font = fontSize * dpr + "px serif";
        metrics = gameSceneContext.measureText(content);
        width = roundNumber(metrics.width, 4);
        height = roundNumber(metrics.actualBoundingBoxAscent + metrics.actualBoundingBoxDescent, 4);
        if (fontSize < 1) break; // 避免 height 计算异常，导致死循环
    }

    while (height < 3 * sysConfig.girdSize) {
        fontSize += 1;
        gameSceneContext.font = fontSize * dpr + "px serif";
        metrics = gameSceneContext.measureText(content);
        width = roundNumber(metrics.width, 4);
        height = roundNumber(metrics.actualBoundingBoxAscent + metrics.actualBoundingBoxDescent, 4);
        if (fontSize > 50) break; // 避免 height 计算异常，导致死循环
    }

    if (fontSize < 1 || fontSize > 50) { // 字体大小异常
        console.error(">>>> drawTableCenterGraph fontSize error.");
        fontSize = 7;
        gameSceneContext.font = fontSize * dpr + "px serif";
    }

    console.log(">>>> center graph fontSize=" + fontSize + ", width=" + width + ", height=" + height);
    gameSceneContext.fillText(content, gameSceneCanvas.width / 2, gameSceneCanvas.height / 2);
    gameSceneContext.restore();
}


// 【中心布局SVG】
// 中心雪花❄️ 画在游戏场景画布上  3 * sysConfig.girdSize ≤ height ≤ 5 * sysConfig.girdSize
function drawCenterGraphSvg(svgId) {
    gameSceneContext.save();
    //gameSceneContext.fillStyle = "#EEF0F220"; // 在 svg 中配置 fill 颜色，这里设置没用
    // 水平对齐方式 (center left right start end)
    gameSceneContext.textAlign = "center";
    // 垂直对齐的方式 (top bottom middle)
    gameSceneContext.textBaseline = 'middle';
    //gameSceneContext.globalCompositeOperation = "source-over";

    let svgEle = document.getElementById(svgId);
    if (!svgEle) return;
    let svg_xml = (new XMLSerializer()).serializeToString(svgEle);
    //console.log(">>>> svg_xml:", svg_xml);
    let img = new Image();
    img.src = "data:image/svg+xml;base64," + window.btoa(svg_xml);
    //console.log(">>>> img.src:", img.src);

    // 避免获取到 width、height 为 0
    img.onload = function () {
        if (!img || !img.width || !img.height) return;
        let scale, width, height;
        scale = getCenterImgScale(img);
        if (scale <= 0) return;
        width = roundNumber(img.width * scale, 4);
        height = roundNumber(img.height * scale, 4);

        gameSceneContext.drawImage(img, gameSceneCanvas.width / 2 - width / 2, gameSceneCanvas.height / 2 - height / 2, width, height); // 大图缩小，不会变模糊
    }
    gameSceneContext.restore();
}


// 获取中心图形缩放比例
function getCenterImgScale(img) {
    let scale, width, height;
    scale = 0.5;
    width = img.width;
    height = img.height;
    //console.log(">>>> getCenterImgScale origin width=" + width);

    if (width) {
        while (width > 4.6 * sysConfig.girdSize) {
            scale -= 0.05;
            width = roundNumber(img.width * scale, 4);
            height = roundNumber(img.height * scale, 4);
            if (scale <= 0) break; // 避免计算异常，导致死循环
        }
        while (width < 3 * sysConfig.girdSize) {
            scale += 0.05;
            width = roundNumber(img.width * scale, 4);
            height = roundNumber(img.height * scale, 4);
            if (scale > 1) break;
        }
    }
    scale = roundNumber(scale, 4);

    //console.log(">>>> getCenterImgScale scale=" + scale);
    //console.log(">>>> getCenterImgScale final width=" + width);
    return scale;
}


// 获取字符、icon显示大小
function getFontSize(begin, end, size) {
    let fontSize = { begin: (begin ? begin : 0), end: (end ? end : 0) };
    if (size === "xl") { fontSize.begin = (fontSize.begin + 2.0) * sysConfig.girdSize; fontSize.end = (fontSize.end + 5) * sysConfig.girdSize; }
    if (size === "l") { fontSize.begin = (fontSize.begin + 1.5) * sysConfig.girdSize; fontSize.end = (fontSize.end + 4) * sysConfig.girdSize; }
    if (size === "ll") { fontSize.begin = (fontSize.begin + 1.0) * sysConfig.girdSize; fontSize.end = (fontSize.end + 3) * sysConfig.girdSize; }
    if (size === "fll") { fontSize.begin = (fontSize.begin + 2.0) * sysConfig.girdSize; fontSize.end = (fontSize.end + 3) * sysConfig.girdSize; }
    if (size === "m") { fontSize.begin = (fontSize.begin + 1) * sysConfig.girdSize; fontSize.end = (fontSize.end + 2.3) * sysConfig.girdSize; }
    if (size === "mm") { fontSize.begin = (fontSize.begin + 0.8) * sysConfig.girdSize; fontSize.end = (fontSize.end + 1.8) * sysConfig.girdSize; }
    if (size === "s") { fontSize.begin = (fontSize.begin + 0.6) * sysConfig.girdSize; fontSize.end = (fontSize.end + 1.5) * sysConfig.girdSize; }
    if (size === "ss") { fontSize.begin = (fontSize.begin + 0.4) * sysConfig.girdSize; fontSize.end = (fontSize.end + 0.8) * sysConfig.girdSize; }
    if (size === "xs") { fontSize.begin = (fontSize.begin + 0.3) * sysConfig.girdSize; fontSize.end = (fontSize.end + 0.6) * sysConfig.girdSize; }
    if (size === "xxs") { fontSize.begin = (fontSize.begin + 0.15) * sysConfig.girdSize; fontSize.end = (fontSize.end + 0.4) * sysConfig.girdSize; }
    if (size === "xxxs") { fontSize.begin = (fontSize.begin + 0.10) * sysConfig.girdSize; fontSize.end = (fontSize.end + 0.25) * sysConfig.girdSize; }

    fontSize.begin = Math.round(fontSize.begin);
    fontSize.end = Math.round(fontSize.end);
    return fontSize;
}


// 获取图形可视区域大小，默认为场地高度的一半左右
function getGraphViewAreaSize() {
    let graphViewAreaSize = roundNumber(sysConfig.girdSize * 5, 4); // 8.5
    if (!os.isPc && sysConfig.cTop * dpr > graphViewAreaSize) graphViewAreaSize = sysConfig.cTop * dpr;
    if (os.isPc && sysConfig.cLeft * dpr > graphViewAreaSize) graphViewAreaSize = sysConfig.cLeft * dpr;
    return Math.round(graphViewAreaSize);
}


// 判断【全屏】坐标是否与台面重叠
// 不画与台面重叠的 emoji 图形，能节省几十毫秒的时间
function isInTableAreaFull(p, width) {
    if (!p) return false;
    if (!isNumber(p.x) || !isNumber(p.y)) return false;
    let x = Math.round(p.x);
    let y = Math.round(p.y);
    //if (x <= sysConfig.cLeft * dpr + gameSceneEmojiCanvas.width / 2) x = Math.round(x + width);
    //else x = Math.round(x - width);
    //if (y <= sysConfig.cTop * dpr + gameSceneEmojiCanvas.height / 2) y = Math.round(y + width);
    //else y = Math.round(y - width);
    //if (x <= 0 || y <= 0) return false;
    //drawTableArea(gameSceneEmojiCanvas);
    let circle = { position: p, radius: width / 2 };
    //return pointInPolygon(p, tablePolygon);
    return polygonCircle(tablePolygon, circle);
}


// 全屏画布台面（粗略）
function drawTableArea(targetCanvas) {
    let ctx = targetCanvas.getContext('2d');
    ctx.save();
    ctx.beginPath();
    ctx.lineTo((sysConfig.cLeft * dpr + sysConfig.girdSize * 3), (sysConfig.cTop * dpr - currTheme.tblWidth + sysConfig.girdSize * 0));
    ctx.lineTo((sysConfig.cLeft * dpr + sysConfig.girdSize * 11), (sysConfig.cTop * dpr - currTheme.tblWidth + sysConfig.girdSize * 0));
    ctx.lineTo((sysConfig.cLeft * dpr + sysConfig.girdSize * 14 + currTheme.tblWidth), (sysConfig.cTop * dpr + sysConfig.girdSize * 3));
    ctx.lineTo((sysConfig.cLeft * dpr + sysConfig.girdSize * 14 + currTheme.tblWidth), (sysConfig.cTop * dpr + sysConfig.girdSize * 19));
    ctx.lineTo((sysConfig.cLeft * dpr + sysConfig.girdSize * 11), (sysConfig.cTop * dpr + currTheme.tblWidth + sysConfig.girdSize * 22));
    ctx.lineTo((sysConfig.cLeft * dpr + sysConfig.girdSize * 3), (sysConfig.cTop * dpr + currTheme.tblWidth + sysConfig.girdSize * 22));
    ctx.lineTo((sysConfig.cLeft * dpr + sysConfig.girdSize * 0 - currTheme.tblWidth), (sysConfig.cTop * dpr + sysConfig.girdSize * 19));
    ctx.lineTo((sysConfig.cLeft * dpr + sysConfig.girdSize * 0 - currTheme.tblWidth), (sysConfig.cTop * dpr + sysConfig.girdSize * 3));
    ctx.closePath();

    ctx.strokeStyle = '#000000';
    ctx.lineWidth = 1 * dpr;
    ctx.stroke();
    ctx.restore();
}


// 获取 emoji/svg 图形坐标
function getEmojiPos(icon, size, width, height, posIdx, isSvg, targetCanvas, isCheck) {
    if (!targetCanvas) targetCanvas = gameSceneEmojiCanvas;
    let graphViewAreaSize = getGraphViewAreaSize(); // emoji 展示区域大小
    let diam = width > height ? width : height; // 直径取最大的
    let pos = { x: 0, y: 0, radius: Math.round(diam / 2), icon: icon, size: size, posIdx: posIdx };
    let centerPointPer = isSvg ? 1 : 2;
    switch (posIdx) {
        case 1: // 上/左方
            if (!os.isPc) { // 移动端/平板
                pos.x = Math.round(fullOpen(width / 2, targetCanvas.width - width / 2));
                pos.y = Math.round(fullOpen(sysConfig.cTop * dpr - graphViewAreaSize + height / 2, sysConfig.cTop * dpr - height / centerPointPer - currTheme.tblWidth));
            } else { // PC
                pos.x = Math.round(fullOpen(sysConfig.cLeft * dpr - graphViewAreaSize + width / 2, sysConfig.cLeft * dpr - width / centerPointPer - currTheme.tblWidth));
                pos.y = Math.round(fullOpen(height / 2, targetCanvas.height - height / 2));
            }
            break;
        case 2: // 下/右方
            if (!os.isPc) { // 移动端/平板
                pos.x = Math.round(fullOpen(width / 2, targetCanvas.width - width / 2));
                pos.y = Math.round(fullOpen(targetCanvas.height - sysConfig.cTop * dpr + height / centerPointPer + currTheme.tblWidth, targetCanvas.height + (graphViewAreaSize - sysConfig.cTop * dpr) - height / 2));
            } else { // PC
                pos.x = Math.round(fullOpen(targetCanvas.width - sysConfig.cLeft * dpr + width / centerPointPer + currTheme.tblWidth, targetCanvas.width + (graphViewAreaSize - sysConfig.cLeft * dpr) - width / 2));
                pos.y = Math.round(fullOpen(height / 2, targetCanvas.height - height / 2));
            }
            break;
        default: // 全屏
            pos.x = Math.round(fullOpen(width / 2, targetCanvas.width - width / 2));
            pos.y = Math.round(fullOpen(height / 2, targetCanvas.height - height / 2));

    }
    if (isSvg) { // SVG 图形原点在左上角，检测相交需要把坐标移至中心
        pos.x = Math.round(pos.x + width / 2);
        pos.y = Math.round(pos.y + height / 2);
    }

    // 大图形重叠检测 默认主题不检测
    if (userConfig.sceneThemeMode > 0 && largeEmojiSizes.indexOf(size) > -1 && largeEmojiPoints && largeEmojiPoints.length > 0) {
        for (let i = 0, len = largeEmojiPoints.length; i < len; i++) {
            if (is2CirclesCollided(pos, largeEmojiPoints[i])) {
                console.log(">>>> " + posIdx + "-" + icon + "-" + size + "-图形重叠 -> " + i + "-" + JSON.stringify(largeEmojiPoints[i]));
                sysConfig.emojiCrossRetryCount -= 1;
                if (sysConfig.emojiCrossRetryCount < 1) {
                    sysConfig.emojiCrossRetryCount = 3;
                    return null;
                }
                pos = getEmojiPos(icon, size, width, height, posIdx, isSvg, targetCanvas, true);
                break;
            }
        }
    }

    if (isCheck) return pos; // 递归检测，直接返回坐标
    if (!pos) return pos;

    if (largeEmojiSizes.indexOf(size) > -1)
        largeEmojiPoints.push(pos); // 没有重叠则加入列表

    if (isSvg) { // SVG 图形检测完之后，原点还原至左上角
        pos.x = Math.round(pos.x - width / 2);
        pos.y = Math.round(pos.y - height / 2);
    }

    // 检测次数重置
    sysConfig.emojiCrossRetryCount = 3;

    return pos;
}


// 【上下布局ICON】
function drawIconUpAndDown(icon, size, num, isNumRd, posIdx) {
    if (!posIdx) posIdx = 0; // 1-只画上/左方；2-只画下/右方；其他-都画

    gameSceneEmojiContext.save();
    //gameSceneEmojiContext.fillStyle = "#3ACC57"; // 这个颜色会覆盖图形原有颜色
    // 水平对齐方式 (center left right start end)
    gameSceneEmojiContext.textAlign = "center";
    // 垂直对齐的方式 (top,bottom,middle)
    gameSceneEmojiContext.textBaseline = 'middle';

    let fontSize = getFontSize(0, 0, size);
    let graphViewAreaSize = getGraphViewAreaSize();
    let metrics, width, height, count;

    if (posIdx !== 2) {
        // 上/左方空白区域
        if (isNumRd) num = fullCloseInt(0, num);
        for (let i = 0; i < num; i++) {
            gameSceneEmojiContext.font = fullOpen(fontSize.begin, fontSize.end) + "px serif";
            metrics = gameSceneEmojiContext.measureText(icon);
            width = roundNumber(metrics.width, 4);
            if (!width || width < 0) continue;
            height = roundNumber(metrics.actualBoundingBoxAscent + metrics.actualBoundingBoxDescent, 4);
            //console.log(">>>> graph width=" + width + ", height=" + height);
            count = Math.round(sysConfig.cTop * dpr / height); // 能容纳多少个
            if (os.isPc) count = Math.round(sysConfig.cLeft * dpr / width);
            //console.log(">>>> count=" + count);
            // if (count < 1) continue; // 不考虑 count，则图形可以超出边界
            // emoji 图形原点在中心
            //gameSceneEmojiContext.fillText(icon, 0, 0);
            //if (!os.isPc) gameSceneEmojiContext.fillText(icon, fullOpen(width / 2, gameSceneEmojiCanvas.width - width / 2), fullOpen(sysConfig.cTop * dpr - graphViewAreaSize + height / 2, sysConfig.cTop * dpr - height / 2 - currTheme.tblWidth));
            //if (os.isPc) gameSceneEmojiContext.fillText(icon, fullOpen(sysConfig.cLeft * dpr - graphViewAreaSize + width / 2, sysConfig.cLeft * dpr - width / 2 - currTheme.tblWidth), fullOpen(height / 2, gameSceneEmojiCanvas.height - height / 2));
            let fillPos = getEmojiPos(icon, size, width, height, 1, false, gameSceneEmojiCanvas);
            if (!fillPos) continue;
            gameSceneEmojiContext.fillText(icon, fillPos.x, fillPos.y);
            gameSceneEmojiContext.beginPath();
        }
    }

    if (posIdx !== 1) {
        // 下/右方空白区域
        if (isNumRd) num = fullCloseInt(0, num);
        for (let i = 0; i < num; i++) {
            gameSceneEmojiContext.font = fullOpen(fontSize.begin, fontSize.end) + "px serif";
            metrics = gameSceneEmojiContext.measureText(icon);
            width = roundNumber(metrics.width, 4);
            if (!width || width < 0) continue;
            height = roundNumber(metrics.actualBoundingBoxAscent + metrics.actualBoundingBoxDescent, 4);
            count = Math.round(sysConfig.cTop * dpr / height);
            if (os.isPc) count = Math.round(sysConfig.cLeft * dpr / width);
            //if (count < 1) continue;
            //if (!os.isPc) gameSceneEmojiContext.fillText(icon, fullOpen(width / 2, gameSceneEmojiCanvas.width - width / 2), fullOpen(gameSceneEmojiCanvas.height - sysConfig.cTop * dpr + height / 2 + currTheme.tblWidth, gameSceneEmojiCanvas.height + (graphViewAreaSize - sysConfig.cTop * dpr) - height / 2));
            //if (os.isPc) gameSceneEmojiContext.fillText(icon, fullOpen(gameSceneEmojiCanvas.width - sysConfig.cLeft * dpr + width / 2 + currTheme.tblWidth, gameSceneEmojiCanvas.width + (graphViewAreaSize - sysConfig.cLeft * dpr) - width / 2), fullOpen(height / 2, gameSceneEmojiCanvas.height - height / 2));
            let fillPos = getEmojiPos(icon, size, width, height, 2, false, gameSceneEmojiCanvas);
            if (!fillPos) continue;
            gameSceneEmojiContext.fillText(icon, fillPos.x, fillPos.y);
            gameSceneEmojiContext.beginPath();
        }
    }

    gameSceneEmojiContext.restore();
}


// 【全屏随机布局ICON】
function drawIconRandom(icon, size, num, isNumRd, isInner, targetCanvas) {
    if (!targetCanvas) targetCanvas = gameSceneEmojiCanvas;
    let ctx = targetCanvas ? targetCanvas.getContext('2d') : gameSceneEmojiContext;
    ctx.save();
    //ctx.fillStyle = "#3ACC57";
    // 水平对齐方式 (center left right start end)
    ctx.textAlign = "center";
    // 垂直对齐的方式 (top,bottom,middle)
    ctx.textBaseline = 'middle';

    // 保持跟上下布局一样
    let fontSize = getFontSize(0, 0, size);

    let metrics, width, height, count;
    if (isNumRd) num = fullCloseInt(1, num);
    for (let i = 0; i < num; i++) {
        ctx.font = fullOpen(fontSize.begin, fontSize.end) + "px serif";
        metrics = ctx.measureText(icon);
        width = roundNumber(metrics.width, 4);
        if (!width || width < 0) continue;
        height = roundNumber(metrics.actualBoundingBoxAscent + metrics.actualBoundingBoxDescent, 4);
        count = Math.round(sysConfig.cTop / height);
        if (count < 1) continue;
        //let fillPos = {x:fullOpen(width / 2, targetCanvas.width - width / 2), y:fullOpen(height / 2, targetCanvas.height - height / 2)};
        let fillPos = getEmojiPos(icon, size, width, height, 0, false, targetCanvas);
        if (!fillPos) continue;
        // 不画在台面内部且图形与台面有重叠，则不画
        //if (isInner === undefined) isInner = true;
        if (!isInner && isInTableAreaFull(fillPos, width)) continue;
        //gameSceneCanvas.style.display = "none";
        //console.log(fillPos);
        //console.log(width);
        //if (icon === '🐄') fillPos = {x:0, y:0}; // emoji 图形的原点在中心
        ctx.fillText(icon, fillPos.x, fillPos.y);
        ctx.beginPath();
    }
    ctx.restore();
}


// 【上下布局SVG】
function drawSvgUpAndDown(svgId, size, num, isNumRd, posIdx) {
    if (!posIdx) posIdx = 0;

    gameSceneEmojiContext.save();
    gameSceneEmojiContext.fillStyle = "#FAF8F9"; // 在 svg 中配置 fill 颜色
    // 水平对齐方式 (center left right start end)
    gameSceneEmojiContext.textAlign = "center";
    // 垂直对齐的方式 (top,bottom,middle)
    gameSceneEmojiContext.textBaseline = 'middle';

    let fontSize = getFontSize(0, 0, size);
    let graphViewAreaSize = getGraphViewAreaSize();

    let svg_xml = (new XMLSerializer()).serializeToString(document.getElementById(svgId));
    //console.log(">>>> svg_xml:", svg_xml);
    let img = new Image();
    img.src = "data:image/svg+xml;base64," + window.btoa(svg_xml);
    //console.log(">>>> img.src:", img.src);

    img.onload = function () {
        let scale, width, height, count;
        scale = 1;
        width = img.width;
        height = img.height;

        if (height) {
            if (posIdx !== 2) {
                // 上/左方空白区域
                if (isNumRd) num = fullCloseInt(1, num);
                for (let i = 0; i < num; i++) {
                    if (i === 0)
                        scale = roundNumber(fullOpen(fontSize.begin, fontSize.end) / (sysConfig.girdSize * 8), 4);
                    else
                        scale = roundNumber(fullOpen(fontSize.begin, fontSize.end) / (sysConfig.girdSize * 10), 4);
                    width = roundNumber(img.width * scale, 4);
                    if (!width || width < 0) continue;
                    height = roundNumber(img.height * scale, 4);
                    count = Math.round(sysConfig.cTop * dpr / height);
                    if (os.isPc) count = Math.round(sysConfig.cLeft * dpr / width);
                    //if (count < 1) continue;
                    // 随机旋转角度，0 ~ 360
                    //let rotate = fullCloseInt(0, 360);
                    //gameSceneEmojiContext.rotate((rotate * Math.PI) / 180);
                    //if (!os.isPc) gameSceneEmojiContext.drawImage(img, 0, 0, img.width, img.height, fullOpen(width / 2, gameSceneEmojiCanvas.width - width / 2), fullOpen(sysConfig.cTop * dpr / 4, sysConfig.cTop * dpr - height / 2), width, height);
                    //if (os.isPc) gameSceneEmojiContext.drawImage(img, 0, 0, img.width, img.height, fullOpen(width / 2, sysConfig.cLeft * dpr - width / 2), fullOpen(height / 2, gameSceneEmojiCanvas.height - height / 2), width, height);
                    // SVG 图形原点在左上角
                    //gameSceneEmojiContext.drawImage(img, 0, 0, img.width, img.height, 0, 0, width, height);
                    //if (!os.isPc) gameSceneEmojiContext.drawImage(img, 0, 0, img.width, img.height, fullOpen(width / 2, gameSceneEmojiCanvas.width - width / 2), fullOpen(sysConfig.cTop * dpr - graphViewAreaSize + height / 2, sysConfig.cTop * dpr - height - currTheme.tblWidth), width, height);
                    //if (os.isPc) gameSceneEmojiContext.drawImage(img, 0, 0, img.width, img.height, fullOpen(sysConfig.cLeft * dpr - graphViewAreaSize + width / 2, sysConfig.cLeft * dpr - width - currTheme.tblWidth), fullOpen(height / 2, gameSceneEmojiCanvas.height - height / 2), width, height);
                    let fillPos = getEmojiPos(svgId, size, width, height, 1, true, gameSceneEmojiCanvas);
                    if (!fillPos) continue;
                    gameSceneEmojiContext.drawImage(img, 0, 0, img.width, img.height, fillPos.x, fillPos.y, width, height);
                    //gameSceneEmojiContext.rotate((-rotate * Math.PI) / 180); // 画完之后旋转回去
                    gameSceneEmojiContext.beginPath();
                }
            }

            if (posIdx !== 1) {
                // 下/右方空白区域
                if (isNumRd) num = fullCloseInt(1, num);
                for (let i = 0; i < num; i++) {
                    scale = roundNumber(fullOpen(fontSize.begin, fontSize.end) / (sysConfig.girdSize * 10), 4);
                    width = roundNumber(img.width * scale, 4);
                    if (!width || width < 0) continue;
                    height = roundNumber(img.height * scale, 4);
                    count = Math.round(sysConfig.cTop * dpr / height);
                    if (os.isPc) count = Math.round(sysConfig.cLeft * dpr / width);
                    //if (count < 1) continue;
                    //if (!os.isPc) gameSceneEmojiContext.drawImage(img, 0, 0, img.width, img.height, fullOpen(width / 2, gameSceneEmojiCanvas.width - width / 2), fullOpen(gameSceneEmojiCanvas.height - sysConfig.cTop * dpr + height + currTheme.tblWidth, gameSceneEmojiCanvas.height + (graphViewAreaSize - sysConfig.cTop * dpr) - height / 2), width, height);
                    //if (os.isPc) gameSceneEmojiContext.drawImage(img, 0, 0, img.width, img.height, fullOpen(gameSceneEmojiCanvas.width - sysConfig.cLeft * dpr + width + currTheme.tblWidth, gameSceneEmojiCanvas.width + (graphViewAreaSize - sysConfig.cLeft * dpr) - width / 2), fullOpen(height / 2, gameSceneEmojiCanvas.height - height / 2), width, height)
                    let fillPos = getEmojiPos(svgId, size, width, height, 2, true, gameSceneEmojiCanvas);
                    if (!fillPos) continue;
                    gameSceneEmojiContext.drawImage(img, 0, 0, img.width, img.height, fillPos.x, fillPos.y, width, height);
                    gameSceneEmojiContext.beginPath();
                }
            }
        }
    }

    gameSceneEmojiContext.restore();
}


// 【全屏随机布局SVG】
function drawSvgRandom(svgId, size, num, isNumRd, isInner, targetCanvas) {
    gameSceneEmojiContext.save();
    gameSceneEmojiContext.fillStyle = "#FAF8F9"; // 在 svg 中配置 fill 颜色
    // 水平对齐方式 (center left right start end)
    gameSceneEmojiContext.textAlign = "center";
    // 垂直对齐的方式 (top,bottom,middle)
    gameSceneEmojiContext.textBaseline = 'middle';

    let fontSize = getFontSize(0, 0, size);

    let svg_xml = (new XMLSerializer()).serializeToString(document.getElementById(svgId));
    //console.log(">>>> svg_xml:", svg_xml);
    let img = new Image();
    img.src = "data:image/svg+xml;base64," + window.btoa(svg_xml);
    //console.log(">>>> img.src:", img.src);

    img.onload = function () {
        let scale, width, height, count;
        scale = 1;
        width = img.width;
        height = img.height;

        if (height) {
            if (isNumRd) num = fullCloseInt(1, num);
            for (let i = 0; i < num; i++) {
                if (i % 5 === 1)
                    scale = roundNumber(fullOpen(fontSize.begin, fontSize.end) / (sysConfig.girdSize * 8), 4);
                else
                    scale = roundNumber(fullOpen(fontSize.begin, fontSize.end) / (sysConfig.girdSize * 10), 4);
                width = roundNumber(img.width * scale, 4);
                if (!width || width < 0) continue;
                height = roundNumber(img.height * scale, 4);
                count = Math.round(sysConfig.cTop * dpr / height);
                if (os.isPc) count = Math.round(sysConfig.cLeft * dpr / width);
                //if (count < 1) continue;
                //let fillPos = {x:fullOpen(width / 2, gameSceneEmojiCanvas.width - width / 2), y:fullOpen(height / 2, gameSceneEmojiCanvas.height - height / 2)};
                let fillPos = getEmojiPos(svgId, size, width, height, 0, true, gameSceneEmojiCanvas);
                if (!fillPos) continue;
                // 不画在台面内部且图形与台面有重叠，则不画
                if (!isInner && isInTableAreaFull(fillPos, width)) continue;
                gameSceneEmojiContext.drawImage(img, 0, 0, img.width, img.height, fillPos.x, fillPos.y, width, height);
                gameSceneEmojiContext.beginPath();
            }
        }
    }

    gameSceneEmojiContext.restore();
}


// 【指定位置画SVG】
function drawSvgWithPos(svgId, size, pos) {
    gameSceneEmojiContext.save();
    // 水平对齐方式 (center left right start end)
    gameSceneEmojiContext.textAlign = "center";
    // 垂直对齐的方式 (top,bottom,middle)
    gameSceneEmojiContext.textBaseline = 'middle';
    gameSceneEmojiContext.beginPath();

    // 坐标系移动到中心
    gameSceneEmojiContext.translate(roundNumber(gameSceneEmojiCanvas.width / 2, 4), roundNumber(gameSceneEmojiCanvas.height / 2, 4));
    // 具体操作
    doDrawSvgWithPos(svgId, size, pos);

    gameSceneEmojiContext.restore();
}

function doDrawSvgWithPos(svgId, size, pos) {
    let svg_xml = (new XMLSerializer()).serializeToString(document.getElementById(svgId));
    //console.log(">>>> svg_xml:", svg_xml);
    let img = new Image();
    img.src = "data:image/svg+xml;base64," + window.btoa(svg_xml);
    //console.log(">>>> img.src:", img.src);

    img.onload = function () {
        let scale, width, height;
        scale = roundNumber(size / (sysConfig.girdSize * 10), 4);
        width = roundNumber(img.width * scale, 4);
        if (!width || width < 0) return;
        height = roundNumber(img.height * scale, 4);
        gameSceneEmojiContext.drawImage(img, pos.x, pos.y, width, height);
    }
}


// 默认主题指定位置画石头
function drawStoneGraphDefault() {
    gameSceneEmojiContext.save();
    // 水平对齐方式 (center left right start end)
    gameSceneEmojiContext.textAlign = "center";
    // 垂直对齐的方式 (top,bottom,middle)
    gameSceneEmojiContext.textBaseline = 'middle';
    gameSceneEmojiContext.beginPath();
    // 设置阴影
    gameSceneEmojiContext.shadowColor = "#2D2560";
    gameSceneEmojiContext.shadowBlur = 20 * dpr;

    // 左上角
    // 原始坐标点
    let pos0 = { x: sysConfig.cLeft * dpr - sysConfig.girdSize * 0.8, y: sysConfig.cTop * dpr + sysConfig.girdSize * 0.5 };
    doDrawSvgWithPos("svg-stone", sysConfig.girdSize * fullOpen(1, 2), pos0);
    // 相对原始坐标移动
    let pos01 = { x: pos0.x + sysConfig.girdSize * 1.6, y: pos0.y + sysConfig.girdSize * 0.1 };
    doDrawSvgWithPos("svg-stone", sysConfig.girdSize * fullOpen(0, 1.4), pos01);
    let pos02 = { x: pos0.x - sysConfig.girdSize * 0.2, y: pos0.y + sysConfig.girdSize * 1.4 };
    doDrawSvgWithPos("svg-stone", sysConfig.girdSize * fullOpen(0, 1.4), pos02);
    // 右上角
    pos0 = { x: sysConfig.cLeft * dpr + sysConfig.girdSize * 11, y: sysConfig.cTop * dpr - sysConfig.girdSize * 0.5 };
    doDrawSvgWithPos("svg-stone", sysConfig.girdSize * fullOpen(1, 2), pos0);
    // 相对原始坐标移动
    pos01 = { x: pos0.x - sysConfig.girdSize * 0.6, y: pos0.y - sysConfig.girdSize * 0.2 };
    doDrawSvgWithPos("svg-stone", sysConfig.girdSize * fullOpen(0, 1.4), pos01);
    pos02 = { x: pos0.x + sysConfig.girdSize * 1.6, y: pos0.y + sysConfig.girdSize * 1.4 };
    //doDrawSvgWithPos("svg-stone", sysConfig.girdSize * fullOpen(0, 1.2), pos02);
    // 左下角
    pos0 = { x: sysConfig.cLeft * dpr + sysConfig.girdSize * 0.2, y: sysConfig.cTop * dpr + sysConfig.girdSize * 20 };
    doDrawSvgWithPos("svg-stone", sysConfig.girdSize * fullOpen(1, 2), pos0);
    // 相对原始坐标移动
    pos01 = { x: pos0.x - sysConfig.girdSize * 1.0, y: pos0.y + sysConfig.girdSize * 1.3 };
    //doDrawSvgWithPos("svg-stone", sysConfig.girdSize * fullOpen(0, 1.4), pos01);
    pos02 = { x: pos0.x + sysConfig.girdSize * 1.2, y: pos0.y + sysConfig.girdSize * 1.0 };
    doDrawSvgWithPos("svg-stone", sysConfig.girdSize * fullOpen(0, 1.2), pos02);
    // 右下角
    pos0 = { x: sysConfig.cLeft * dpr + sysConfig.girdSize * 13, y: sysConfig.cTop * dpr + sysConfig.girdSize * 18 };
    doDrawSvgWithPos("svg-stone", sysConfig.girdSize * fullOpen(1, 2), pos0);
    // 相对原始坐标移动
    pos01 = { x: pos0.x - sysConfig.girdSize * 1.0, y: pos0.y + sysConfig.girdSize * 1.2 };
    doDrawSvgWithPos("svg-stone", sysConfig.girdSize * fullOpen(0, 1.4), pos01);
    pos02 = { x: pos0.x - sysConfig.girdSize * 0.6, y: pos0.y + sysConfig.girdSize * 2 };
    //doDrawSvgWithPos("svg-stone", sysConfig.girdSize * fullOpen(0, 1.0), pos02);

    gameSceneEmojiContext.restore();
}


// 默认主题指定位置画骨头
function drawBoneGraphDefault() {

}


// 星际主题画星系光亮
function drawGalaxyLight() {
    gameSceneGraphContext.save();
    // 随机旋转角度，0 ~ 360
    let rotate = fullCloseInt(0, 360);
    gameSceneGraphContext.rotate((rotate * Math.PI) / 180);
    // 阴影
    gameSceneGraphContext.shadowColor = '#7F9BC2';
    gameSceneGraphContext.shadowBlur = 700;
    // 渐变
    //let grd = gameSceneGraphContext.createLinearGradient(0.9 * gameSceneGraphCanvas.width, 0.1 * gameSceneGraphCanvas.height,0.1 * gameSceneGraphCanvas.width, 0.9 * gameSceneGraphCanvas.height);
    //grd.addColorStop(0, "#05132C");
    //grd.addColorStop(0.5, "#05132C");
    //grd.addColorStop(1, "#EEF0F2");
    gameSceneGraphContext.beginPath();
    gameSceneGraphContext.moveTo(0.9 * gameSceneGraphCanvas.width, 0.01 * gameSceneGraphCanvas.height); // 起点
    gameSceneGraphContext.quadraticCurveTo(0.8 * gameSceneGraphCanvas.width, 0.4 * gameSceneGraphCanvas.height, 0.01 * gameSceneGraphCanvas.width, 0.6 * gameSceneGraphCanvas.height);
    gameSceneGraphContext.quadraticCurveTo(0.78 * gameSceneGraphCanvas.width, 0.4 * gameSceneGraphCanvas.height, 0.9 * gameSceneGraphCanvas.width, 0.01 * gameSceneGraphCanvas.height);

    gameSceneGraphContext.lineWidth = 2 * dpr; // 设置线宽
    gameSceneGraphContext.fillStyle = "#EEF0F2"; // 设置颜色
    //gameSceneGraphContext.fillStyle = grd; // 使用渐变
    //gameSceneGraphContext.strokeStyle = "#EEF0F2"; // 设置颜色
    //gameSceneGraphContext.stroke();
    gameSceneGraphContext.fill();
    gameSceneGraphContext.restore();
}


// 星际主题全屏随机画星系光亮
function drawGalaxyLightRandom(icon, size, num, isNumRd) {
    gameSceneGraphContext.save();

    let fontSize = getFontSize(0, 0, size);

    if (globalParams) { // 设置阴影
        gameSceneGraphContext.shadowColor = globalParams.shadowColor;
        gameSceneGraphContext.shadowBlur = globalParams.shadowBlur;
    }
    // 渐变
    //let grd = gameSceneGraphContext.createLinearGradient(0.9 * gameSceneGraphCanvas.width, 0.1 * gameSceneGraphCanvas.height,0.1 * gameSceneGraphCanvas.width, 0.9 * gameSceneGraphCanvas.height);
    let grd, x, y, r;
    if (isNumRd) num = fullCloseInt(1, num);
    for (let i = 0; i < num; i++) {
        r = roundNumber(fullOpen(fontSize.begin, fontSize.end) / 2, 4);
        x = fullOpen(r, gameSceneEmojiCanvas.width - r);
        y = fullOpen(r, gameSceneEmojiCanvas.height - r);
        grd = gameSceneGraphContext.createRadialGradient(x, y, 0.1 * r, x, y, r);
        grd.addColorStop(0.1, "#EEF0F2F0");
        grd.addColorStop(0.5, "#EEF0F280");
        grd.addColorStop(1, "#EEF0F200");
        gameSceneGraphContext.beginPath();
        //gameSceneGraphContext.arc(this.x0, this.y0, this.pathRadius, Math.PI / 180 * 0, Math.PI / 180 * 360);
        gameSceneGraphContext.arc(x, y, r, 0, Math.PI * 2, true);
        //gameSceneGraphContext.fillStyle = "#EEF0F2"; // 设置颜色
        gameSceneGraphContext.fillStyle = grd; // 使用渐变
        gameSceneGraphContext.fill();
    }
    gameSceneGraphContext.restore();
}


// 画场地上大面积景物图形【不好画，以后再搞】
function drawSceneGraph(icon, size) {
    gameSceneGraphContext.save();
    let topLeftRatio = roundNumber(sysConfig.cTop / sysConfig.cLeft * 1.6, 4);
    //console.log(">>>> topLeftRatio=" + topLeftRatio);
    // 阴影
    gameSceneGraphContext.shadowColor = '#7F9BC2';
    gameSceneGraphContext.shadowBlur = 15;
    gameSceneGraphContext.beginPath();
    //gameSceneGraphContext.moveTo(0.4 * sysConfig.cLeft, 0.4 * sysConfig.cLeft * topLeftRatio); // 起点
    //gameSceneGraphContext.quadraticCurveTo(gameSceneGraphCanvas.width / 8 - 0.4 * sysConfig.cLeft, 0.3 * sysConfig.cLeft * topLeftRatio, gameSceneGraphCanvas.width / 2.4 - 0.4 * sysConfig.cLeft, 0.35 * sysConfig.cLeft * topLeftRatio);

    gameSceneGraphContext.fillStyle = "#EEF0F2"; // 设置颜色
    //gameSceneGraphContext.strokeStyle = "#EEF0F2"; // 设置颜色
    //gameSceneGraphContext.stroke();
    gameSceneGraphContext.fill();
    gameSceneGraphContext.restore();
}


// 画蛋
function drawEggs() {
    //console.log(eggs);
    if (!eggs || eggs.length < 1) return;
    for (let i = 0; i < eggs.length; i++) {
        gameSceneContext.save();
        gameSceneContext.beginPath();
        gameSceneContext.arc(eggs[i].x, eggs[i].y, eggs[i].radius, Math.PI / 180 * 0, Math.PI / 180 * 360);
        gameSceneContext.lineWidth = 2 * dpr;
        gameSceneContext.strokeStyle = eggs[i].color;
        //gameSceneContext.setLineDash([3, 3]); // 虚线
        gameSceneContext.closePath();
        gameSceneContext.stroke(); // 空心
        gameSceneContext.restore();
    }
}


//////////////////////////////////////////////////////////////////////


//////////////////////////////////////////////////////////////////////
// 【选择角色、参数设置】 变量、方法区域
//////////////////////////////////////////////////////////////////////

// 选择角色
function chooseRole(ele, roleId) {

    // 选角色开始之前，先输入访问密钥，授权访问
    if (!checkCoreCode("do2BallsCollidedMV2", true)) return;

    //console.log(">>>> collide-try-role-chose: " + roleId);
    //if (roleId === Role.SHUANGZI.id) {alert("👬：敬请期待~哈哈哈哈😄"); return;}
    if (roleId === Role.YOUXIA.id) { alert("🏹：咱有练的必要吗？🤔"); return; }
    if (roleId === Role.HUAQIANJI.id) { alert("🚀：炮弹反弹一次都不会吗？😂"); return; }

    userConfig.currRole = roleId;
    userConfig.isRandomRole = false;
    userConfig.isFlashRole = false;

    if (roleId === -2) { // 极速开始，采用设置里面配置的角色。如果没有配置，则使用常用组合
        userConfig.isFlashRole = true;
        setRolesFlash(userConfig.gameRoleIds, true);
    } else if (roleId < 0) { // 随机角色，完全随机
        roleId = Role.getRandomRoleId();
        userConfig.currRole = roleId;
        userConfig.isRandomRole = true;
    }

    // 存到 sessionStorage【PC浏览器刷新不会失效，关闭页面会失效】
    //if (userConfig.currRole > -1) sessionStorage.setItem('collide-try-role-chose', userConfig.currRole);
    // TODO 存到 localStorage，兼容一些浏览器（Via）刷新后 sessionStorage 失效，导致一直弹出选择角色问题
    if (userConfig.currRole > -1) localStorage.setItem('collide-try-role-chose', userConfig.currRole);
    // 更新 localStorage 中的 userConfig
    if (userConfig.currRole > -1) localStorage.setItem('collide-try-user-settings', JSON.stringify(userConfig));
    // 刷新页面
    //location.reload();
    // 不刷新页面重新选角色
    reInit();
    // 显示操作指南弹窗
    if (sysConfig.isRoleChooseFinished) showHowToPlay(true);
    // 显示左上角重新选择角色提示
    if (sysConfig.isRoleChooseFinished) showReChooseRoleEntryDialog();
}


// 弹窗选择角色是否完成
function isRoleChooseFinished() {
    let choseRoleIdStr = sessionStorage.getItem('collide-try-role-chose');
    if (!choseRoleIdStr) choseRoleIdStr = localStorage.getItem('collide-try-role-chose');
    if (!choseRoleIdStr) return false;
    if (Number(choseRoleIdStr) > -1) return true;
    return false;
}


// 判断指定弹窗是否正在显示
function isDialogShowing(dialogEle) {
    let isShowing = false;
    if (dialogEle && dialogEle.style.display && dialogEle.style.display !== "none") { // 正在显示
        isShowing = true;
    }
    return isShowing;
}


// 切换弹窗显示或隐藏
function switchDialogShow(dialogEle, isShow, params) {
    //console.log(dialogEle);
    if (!params) params = { display: "unset" };
    if (!params.display) params.display = "unset";
    if (!dialogEle && params.dialogEleId) dialogEle = document.getElementById(params.dialogEleId);
    if (!dialogEle) return;
    if (isShow) { // 显示，display 有多种值可以让元素显示
        dialogEle.style.display = params.display;
    } else { // 关闭
        dialogEle.style.display = "none";
    }
}


// 显示左上角重新选择角色入口提示
function showReChooseRoleEntryDialog() {
    // 有其他弹窗时，不显示
    if (isDialogShowing(chooseRoleDialog) || isDialogShowing(userSettingDialog) || isDialogShowing(howToPlayDialog)) return;
    let t0 = localStorage.getItem('collide-try-re-choose-role-entry-time');
    if (!t0) t0 = "0";
    t0 = Number(t0);
    if (t0 > 0) { // 已经弹过提示了，不再提示
        return;
    }
    switchDialogShow(reChooseRoleEntryDialog, true);
}

// 关闭左上角重新选择角色入口提示，不再提示
function closeReChooseRoleEntryDialog() {
    switchDialogShow(reChooseRoleEntryDialog, false, { display: "none" });
    localStorage.setItem('collide-try-re-choose-role-entry-time', new Date().getTime());
    // 提示完左边重选角色入口，再提示右边的设置入口
    showGameSettingEntryDialog();
}


// 显示右上角设置入口提示
function showGameSettingEntryDialog() {
    // 有其他弹窗时，不显示
    if (isDialogShowing(chooseRoleDialog) || isDialogShowing(userSettingDialog)) return;
    let t0 = localStorage.getItem('collide-try-game-settings-entry-time');
    if (!t0) t0 = "0";
    t0 = Number(t0);
    if (t0 > 0) { // 已经弹过提示了，不再提示
        return;
    }
    switchDialogShow(gameSettingEntryDialog, true);
}


// 关闭右上角设置入口提示，不再提示
function closeGameSettingEntryDialog() {
    switchDialogShow(gameSettingEntryDialog, false, { display: "none" });
    localStorage.setItem('collide-try-game-settings-entry-time', new Date().getTime());
}


// 显示设置主角提示
function showGameSettingMainRoleDialog() {
    // 有参数设置弹窗时，才显示
    if (!isDialogShowing(userSettingDialog)) return;
    let t0 = localStorage.getItem('collide-try-game-settings-main-role-time');
    if (!t0) t0 = "0";
    t0 = Number(t0);
    if (t0 > 0) { // 已经弹过提示了，不再提示
        return;
    }
    switchDialogShow(gameSettingMainRoleDialog, true);
}


// 关闭设置主角提示，不再提示
function closeGameSettingMainRoleDialog() {
    switchDialogShow(gameSettingMainRoleDialog, false, { display: "none" });
    localStorage.setItem('collide-try-game-settings-main-role-time', new Date().getTime());
}


// 显示更新内容
function showUpdateContent(isShow) {
    if (isShow) { // 显示
        // 先减少显示选择角色弹窗高度，避免内容重叠
        chooseRoleDialog.style.height = "0%";
        updateContentDialog.style.display = "unset";
    } else { // 关闭
        updateContentDialog.style.display = "none";
        chooseRoleDialog.style.height = "max-content";
    }
}


// 显示一次操作指南弹窗
function showHowToPlay(isShow) {
    if (isShow) { // 显示
        // 只提示一次
        let howToPlayTimeStr = localStorage.getItem('collide-try-how-to-play-time');
        if (howToPlayTimeStr) return;
        // 有其他弹窗时，不显示
        if (isDialogShowing(chooseRoleDialog) || isDialogShowing(userSettingDialog)) return;
        howToPlayDialog.style.display = "unset";
        dialogMask.style.display = "unset";
    } else { // 关闭
        howToPlayDialog.style.display = "none";
        dialogMask.style.display = "none";
        // 设置弹窗时间，用来判断是否显示过
        localStorage.setItem('collide-try-how-to-play-time', new Date().getTime());
        /*
        // 首次进入游戏，操作指南关闭之后，直接进入一次设置
        let localUserConfigTimeStr = localStorage.getItem('collide-try-user-settings-time');
        if (!localUserConfigTimeStr) {
            switchUserSettingDialog(true);
        }
        */
        // 显示左上角重选角色入口提示
        showReChooseRoleEntryDialog();
    }
}


// 切换显示选择角色弹窗
function switchChooseRoleDialog(isShow) {
    // 弹窗右上角显示按钮判断
    switchChooseRoleBtnShow();
    if (isShow) { // 显示
        dialogMask.style.display = "unset"; // 显示选择角色遮罩层
        chooseRoleDialog.style.display = "unset"; // 显示选择角色弹窗
    } else { // 关闭
        if (userConfig.currRole < 0) return; // 没选择角色不能关闭
        dialogMask.style.display = "none"; // 隐藏选择角色遮罩层
        chooseRoleDialog.style.display = "none"; // 隐藏选择角色弹窗
    }
}


// 根据是否已经选过角色，判断选择角色弹窗右上角是设置⚙入口，还是关闭❎按钮
function switchChooseRoleBtnShow() {
    if (userConfig.currRole < 0) { // 第一次进入页面或者清缓存重置后，显示设置入口
        document.getElementById("choose-role-to-setting-entry").style.display = "unset";
        document.getElementById("choose-role-close-btn").style.display = "none";
    } else { // 点击左上角进入的重新选择角色，显示关闭按钮
        document.getElementById("choose-role-to-setting-entry").style.display = "none";
        document.getElementById("choose-role-close-btn").style.display = "unset";
    }
}


// 切换显示用户设置弹窗
function switchUserSettingDialog(isShow) {
    if (isShow) { // 显示
        // 初始化页面默认值
        initUserSettingDialogVal();
        dialogMask.style.display = "unset";
        userSettingDialog.style.display = "unset";
        if (isDialogShowing(chooseRoleDialog)) { // 正在显示选角色弹窗
            // 先减少显示选择角色弹窗高度，避免内容重叠
            chooseRoleDialog.style.height = "1%";
        }
    } else { // 关闭
        userSettingDialog.style.display = "none";
        if (isDialogShowing(chooseRoleDialog)) {
            // 只更新设置时间，但不刷新页面
            reloadAfterUserConfigSettingFinished(new Date().getTime(), false);
            // 关闭参数设置弹窗后，再重新恢复选择角色弹窗原本高度
            chooseRoleDialog.style.height = "max-content";
        } else {
            // 关闭遮罩
            dialogMask.style.display = "none";
            // 更新设置时间，刷新页面
            reloadAfterUserConfigSettingFinished(new Date().getTime(), true);
        }
        // 自动收起自定义主题参数
        //toggleCustomTheme(null, false);
    }
}


// 切换显示canvas图层元素
function switchCanvasShow(canvasEle, isShow) {
    if (!canvasEle) return;

    // 开启或关闭场景边框，如果砖格坐标已经在显示，砖格坐标需要清空重画
    if (canvasEle === gameSceneLinesCanvas) {
        if (userConfig.isShowGridCoordinate) {
            clearCanvasAll(gameSceneCoordinateCanvas);
            drawSceneCoordinate();
        }
    }

    if (isShow) { // 显示
        // 开启场景边框，最好清空重画一次，避免之前没画
        if (canvasEle === gameSceneLinesCanvas) {
            clearCanvasAll(gameSceneLinesCanvas);
            clearCanvasAll(gameSceneLinesBgCanvas);
            doDrawTableLines();
            // 显示边框背景层
            switchCanvasShow(gameSceneLinesBgCanvas, true);
        }
        // 开启砖格坐标，最好清空重画一次，避免显示没有边框时位置
        if (canvasEle === gameSceneCoordinateCanvas) {
            clearCanvasAll(gameSceneCoordinateCanvas);
            drawSceneCoordinate();
        }
        canvasEle.style.display = "inherit";
    } else { // 关闭
        // 关闭场景边框，把边框背景图层清空隐藏
        if (canvasEle === gameSceneLinesCanvas) {
            clearCanvasAll(gameSceneLinesBgCanvas);
            switchCanvasShow(gameSceneLinesBgCanvas, false);
        }
        canvasEle.style.display = "none";
    }
}


// 初始化角色参数弹窗变量值
function initUserSettingDialogVal() {
    try {
        let ele;
        for (let f in userConfig) {
            //console.log(f + " = " + userConfig[f]);
            ele = document.getElementById(f);
            if (f === "currRole") {

            } else if (f === "sceneThemeMode") { // 主题名称
                setSceneThemeText(userConfig[f]);
            } else if (f === "currPlayOpt") { // 当前操作方式
                setCurrPlayOptText(userConfig[f]);
            } else if (f === "mainTeamColor") { // 主角所在队颜色
                setMainTeamColorText(userConfig[f]);
            } else if (f === "gameRoleIds") { // 指定角色名称
                setGameRoleIdsText(userConfig[f]);
            } else if (f === "shareRoleAndPos") { // 导入/导出角色和坐标
                setShareContent(userConfig[f]);
            } else if (typeof userConfig[f] === "string" || typeof userConfig[f] === "number" || userConfig[f] instanceof Array) { // 字符串、数值、数组类型
                if (ele && userConfig[f]) ele.value = userConfig[f].toString();
            } else if (typeof userConfig[f] === "boolean") { // 布尔类型
                if (f === "isShowBallMovePath") togglePathBallMoveShow(userConfig[f]); // 切换运动路径层显示或隐藏
                if (f === "isShowBallPath") togglePathBallShow(userConfig[f]); // 切换全路径层显示或隐藏
                if (f === "isUseCustomTheme" && userConfig[f]) switchCustomThemeCheckbox(userConfig[f]); // 切换自定义主题开关
                if (!ele) continue;
                if (userConfig[f]) ele.setAttribute("checked", true);
                else ele.removeAttribute("checked");
            }
        }

        // 输入了正确的访问密钥才显示【下载离线版】
        // vue 暂时不支持保存  && !isVue()
        if (checkAccessKey()) {
            document.getElementById("collide-try-save-html").style.display = "list-item";
        } else {
            document.getElementById("collide-try-save-html").style.display = "none";
        }

        // 告别信息
        if (sysConfig.isSayGoodbye) {
            let eles = document.getElementsByClassName("collide-try-goodbye") || [];
            for (let i = 0, len = eles.length; i < len; i++) {
                eles[i].style.display = "inherit"; // 继承父标签display属性
            }
        }

    } catch (e) { // userConfig 配置中，并不是所有字段都对应了页面设置，document.getElementById(f) 找不到会报异常，可以忽略
        doGlobalError(e, (sysConfig && sysConfig.alertErrorCount) ? sysConfig.alertErrorCount : 3);
    }
}


// 切换自定义主题参数设置显示/隐藏
function toggleCustomTheme(ele, isShow) {
    let oneCustomThemeLi = document.querySelector(".user-setting-item-expand");
    if (!oneCustomThemeLi) return;
    let customThemeItems = document.getElementsByClassName("user-setting-item-expand");
    if (!customThemeItems || customThemeItems.length < 1) return;
    let svgArrow = document.getElementById("toggleCustomThemeSvgArrow");
    let isShowing = oneCustomThemeLi.style.display && oneCustomThemeLi.style.display !== "none";
    if (isShowing) { // 显示->关闭
        if (isShow === false || typeof isShow === 'undefined') {
            for (let i = 0, len = customThemeItems.length; i < len; i++) {
                customThemeItems[i].style.display = "none";
            }
            // 箭头旋转到指向下
            svgArrow.style.transform = 'inherit';
        }
    } else { // 关闭->显示
        if (isShow === true || typeof isShow === 'undefined') {
            for (let i = 0, len = customThemeItems.length; i < len; i++) {
                customThemeItems[i].style.display = "flex";
            }
            // 设置默认颜色和取色器
            setColorPicker();
            // 箭头旋转到指向上
            svgArrow.style.transform = 'rotate(180deg)';
        }
    }
}


// 设置默认颜色和取色器
function setColorPicker() {
    var colorItems = document.getElementsByClassName("theme-color-item");
    if (!colorItems || colorItems.length < 1)
        return;
    // 设置默认颜色
    /*
    for (let i = 0, len = colorItems.length; i < len; i++) {
        if (colorItems[i].value)
            colorItems[i].style.backgroundColor = colorItems[i].value;
        //colorItems[i].value = "";
    }
    */
    // 设置取色器
    Colorpicker.create({
        bindClass: 'theme-color-item',
        //initColor: '',
        change: function (elem, hex) {
            // console.log(elem, hex);
            //elem.style.backgroundColor = hex;
            elem.value = hex;
            if (elem.fireEvent) {
                elem.fireEvent('onchange');
            } else { // google chrome
                let ev = document.createEvent("HTMLEvents");
                //event.initEvent(eventType,canBubble,cancelable)
                //eventType:字符串值，事件的类型
                //canBubble：事件是否冒泡
                //cancelable：是否可以用preventDefault()方法取消事件
                ev.initEvent("change", false, true);
                elem.dispatchEvent(ev);
            }
        },
        show: function (elem, hex) {
            // 打开取色器，暂时隐藏设置弹窗
            dialogMask.style.display = "none";
            userSettingDialog.style.display = "none";
        },
        hide: function (elem, hex) {
            // 关闭取色器，恢复设置弹窗显示
            dialogMask.style.display = "unset";
            userSettingDialog.style.display = "unset";
        }
    });
}


// 根据 currTheme，初始化设置自定义主题的参数值
function setCustomThemeVals() {
    if (!userConfig.isUseCustomTheme) return;
    if (!currTheme) return;
    try {
        let ele;
        for (let f in currTheme) {
            ele = document.getElementById(f);
            if (!ele) continue;
            // 颜色码转小写
            if (currTheme[f] && typeof currTheme[f] === "string" && currTheme[f].startsWith("#")) currTheme[f] = currTheme[f].toLocaleLowerCase();
            ele.value = currTheme[f];
        }
    } catch (e) {
        console.log(e.message);
    }
}


// 重置主题
function resetThemeDefault() {
    if (confirm("⚠️ 确定要重置自定义主题参数吗？（建议先导出当前参数配置，以便下次重新调整）")) { // 确认
        // 重画场景 方法内部会设置为之前选择的主题
        resetPageBg();
        // 创建一个新主题
        currTheme = Theme.getCurrThemeCopy();
        currTheme.id = Theme.getMaxId() + 1;
        currTheme.name = "自定义主题01";
        currTheme.bgImageIdbKey = sysConfig.bgImageKey + currTheme.id;
        //currTheme.tbColor = Theme.setTbColor00(currTheme.tbColor); // 台面背景透明
        // 更新页面显示
        setCustomThemeVals();
        // 清空 indexedDB 图片存储
        if (indexedDB) clearTable(tbName);
        // 更新存储
        localStorage.setItem("collide-try-custom-theme", JSON.stringify(currTheme));
        localStorage.setItem("collide-try-user-settings", JSON.stringify(userConfig));
    } else { // 取消

    }
}


// 切换【启用自定义主题】开关
function switchCustomThemeCheckbox(isShow) {
    let customThemeItems = document.getElementsByClassName("custom-theme-item");
    if (!customThemeItems || customThemeItems.length < 1) return;
    let pageBgImageIcon = document.getElementById("pageBgImageIcon");
    let customThemeInOut = document.getElementById("customThemeInOut");
    let customThemeInitStatus = document.getElementById("customThemeInitStatus");
    let resetThemeDefault = document.getElementById("resetThemeDefault");
    if (isShow) {
        // 文字颜色、输入框、文件图标恢复正常、显示主题导入导出
        for (let i = 0, len = customThemeItems.length; i < len; i++) {
            customThemeItems[i].classList.remove("user-setting-item-disabled");
            customThemeItems[i].removeAttribute("disabled");
        }
        pageBgImageIcon.style.display = "inherit";
        customThemeInOut.style.display = "inherit";
        resetThemeDefault.style.display = "unset";
        // 启用自定义主题
        userConfig.isUseCustomTheme = true;
        // 从当前对象新建一个自定义主题对象
        let customTheme = Theme.getCustomTheme();
        if (!customTheme) { // 缓存没找到，创建新的主题
            customTheme = Theme.getCurrThemeCopy();
            customTheme.id = Theme.getMaxId() + 1; // 这里的 customTheme.id 跟 customTheme.bgImageIdbKey 关联
            customTheme.name = "自定义主题01";
            customTheme.bgImageIdbKey = sysConfig.bgImageKey + customTheme.id;
            customTheme.tbColor = Theme.setTbColor00(customTheme.tbColor); // 台面背景透明
        }
        // 判断使用新id，避免跟应用自带主题id冲突
        if (customTheme.id <= Theme.getMaxId()) customTheme.id = Theme.getMaxId() + 1;
        //if (currTheme.id === customTheme.id) return; // 主题相同，不重复设置
        // 根据自定义主题参数是否初始化完成
        // 以及判断 currTheme 和缓存中的 customTheme 是否有变化，有变化才执行设置
        if (customThemeInitStatus.value === "1" && isObjEquals(currTheme, customTheme)) return;
        currTheme = customTheme;
        // currTheme 同步到自定义主题
        setCustomThemeVals();
        // 更新显示自定义主题
        reDrawTableAndEgg(); // 重画台面和蛋
        reDrawTableLineAndGirdNum(); // 重画台面边框和砖格坐标
        resetPageBgColor(currTheme.bgColor); // 重置页面背景颜色
        doPageBgImage(currTheme.bgImage); // 背景图片在读取数据库成功的时候会设置
        // 标记自定义主题参数初始化完成
        customThemeInitStatus.value = "1";
        // 存储自定义主题
        localStorage.setItem("collide-try-custom-theme", JSON.stringify(currTheme));
        // localStorage 存储更新 userConfig 对象
        //localStorage.setItem('collide-try-user-settings', JSON.stringify(userConfig));
    } else {
        // 文字变灰色，输入框不能点击，隐藏文件图标、隐藏主题导入导出
        for (let i = 0, len = customThemeItems.length; i < len; i++) {
            customThemeItems[i].classList.add("user-setting-item-disabled");
            customThemeItems[i].setAttribute("disabled", "disabled");
        }
        pageBgImageIcon.style.display = "none";
        customThemeInOut.style.display = "none";
        resetThemeDefault.style.display = "none";
        // 停用自定义主题
        //userConfig.isUseCustomTheme = false;
        // 重置页面背景
        resetPageBg();
        // 重置自定义主题参数显示
        //setCustomThemeVals();
        // 删除自定义主题存储，可以留着，方便下次启用时继续编辑
        //localStorage.removeItem('collide-try-custom-theme');
        // localStorage 存储更新 userConfig 对象
        //localStorage.setItem('collide-try-user-settings', JSON.stringify(userConfig));
    }
}


// 切换显示switch开关，并设置参数值
function switchCheckbox(label, key, params) {
    if (!label) return;
    //console.log(label);
    // 判断是否已选择
    //let switchEle = document.getElementById(key);
    //let switchEle = label.firstElementChild;
    //let switchEle = label.target.firstElementChild;
    let switchEle = document.getElementById(key);
    let checked = switchEle.getAttribute("checked");
    //console.log(checked);
    //console.log(">>>> userConfig: ", userConfig);
    let isShow = false;
    if (checked) { // 开关已打开，点击后关闭
        switchEle.removeAttribute("checked");
        isShow = false;
        userConfig[key] = false;
        if (key === "isKuileiPullBack") userConfig.isKuileiPullBack = false;
        if (key === "isShowBallMovePath") { // 角色运动路径关闭，关联的角色全路径也一起关闭
            userConfig.isShowBallPath = false;
            document.getElementById("isShowBallPath").removeAttribute("checked");
            togglePathBallShow(isShow);
        }
        if (key === "isShowGridCoordinate") { // 砖格坐标总开关关闭，关联的砖格全坐标开关也关闭
            userConfig.isShowGridCoordinateFull = false;
            //document.getElementById("isShowGridCoordinateFull").removeAttribute("checked");
        }
        if (key === "isShowGridCoordinateFull") { // 砖格全坐标开关关闭，关联的砖格坐标总开关保持原样，并判断是否显示坐标
            if (userConfig.isShowGridCoordinate) isShow = true;
        }
    } else { // 开关未打开，点击后打开
        switchEle.setAttribute("checked", true);
        isShow = true;
        userConfig[key] = true;
        if (key === "isShowBallPath") { // 角色全路径打开，依赖的角色运动路径也一起打开
            userConfig.isShowBallMovePath = true;
            document.getElementById("isShowBallMovePath").setAttribute("checked", true);
            togglePathBallMoveShow(isShow);
        }
        if (key === "isShowGridCoordinateFull") { // 砖格全坐标开关打开，关联的砖格坐标总开关也得打开
            userConfig.isShowGridCoordinate = true;
            document.getElementById("isShowGridCoordinate").setAttribute("checked", true);
        }
    }

    // canvas图层切换显示
    if (params && params.canvasEle) switchCanvasShow(params.canvasEle, isShow);
    // 角色运动路径
    if (key === "isShowBallMovePath") togglePathBallMoveShow(isShow);
    // 角色球体路径
    if (key === "isShowBallPath") togglePathBallShow(isShow);
    // 血量条切换显示
    if (key === "isShowRoleBloodLine" || key === "isShowRoleBloodNo")
        flushAllRoleOnce();
    // 启用自定义主题开关
    if (key === "isUseCustomTheme") switchCustomThemeCheckbox(isShow);
    // 显示猴子分身提示
    if (key === "isShowWkPath") reDrawTableAndEgg();

    // 只显示撞击台面
    if (key === "isJustShowTable") {
        // 隐藏/显示图层的方式
        toggleOnlyTable(isShow);
        //if (!balls || balls.length < 1) sysConfig.isNeedReload = true;
        // 重新初始化
        //reInit(false, true);
        // 重新渲染
        //animate();
    }
    // 切换显示场景图形
    if (key === "isShowSceneGraph") toggleSceneGraph(isShow, true);

    // 切换到单个角色测试，需要刷新页面的设置
    //if (key === "isTestOnlyOne") sysConfig.isNeedReload = true;
    if (key === "isTestOnlyOne") {
        clearCanvasAll(canvas); // 清空主运动层画布
        // 重新初始化
        reInit(false, true);
    }

    // localStorage 存储更新 userConfig 对象
    localStorage.setItem('collide-try-user-settings', JSON.stringify(userConfig));

}


// 点击按钮，下拉菜单在 显示/隐藏 之间切换
function toggleDropdown() {
    document.getElementById("themeDropdown").classList.toggle("show");
}


// 切换操作方式，拖拽或点按，默认拖拽
function toggleCurrPlayOpt() {
    let val = userConfig.currPlayOpt;
    if (!isNumber(val)) return;
    if (val === 1) { // 1-点按
        // 当前为点按，点击后切换为默认的拖拽
        val = 0;
        // 隐藏发射按钮
        gameClickPlayCanvas.style.display = "none";
    } else { // 其他默认为拖拽
        // 当前为拖拽，点击后切换为点按
        val = 1;
        // 显示发射按钮
        gameClickPlayCanvas.style.display = "unset";
    }

    setCurrPlayOptText(val);
    userConfig.currPlayOpt = val;
    localStorage.setItem('collide-try-user-settings', JSON.stringify(userConfig));
}


// 切换主角所在队颜色
function toggleTeamColor() {

    let val = userConfig.mainTeamColor;
    if (val === 'r') val = 'b';
    else val = 'r';

    /*
    let colorTxt = "红色";
    if (val === 'b') colorTxt = "蓝色";
    // 提示确认
    if (confirm("💡 点击确定，即可将主角队颜色切换到【" + colorTxt + "】")) { // 确认
        
    } else { // 取消
        return;
    }
    */

    // 参数设置项文字
    setMainTeamColorText(val);
    // 角色队友颜色、设置角色框颜色
    resetMainTeamColorRandom(val);
    // 有朵朵，需要重新画蛋
    if (isDuoduoExist) resetEggs();

    // 角色血量条开启，需要重新渲染角色
    if (userConfig.isShowRoleBloodLine) {
        /*
        if (selectedBall && selectedBall.isChgPosFinished) 
            selectedBall.isChgPosFinished = false; // 标记为未拖动完成
        directPlayAgain(false);
        */
        // 重画一次角色即可
        flushAllRoleOnce();
    }

    // 更新设置
    userConfig.mainTeamColor = val;
    localStorage.setItem('collide-try-user-settings', JSON.stringify(userConfig));
}


// 切换只显示撞击台面，隐藏角色层
function toggleOnlyTable(isShow) {
    // 清空路径层
    //clearCanvasAll(gamePathCanvas);
    //clearCanvasAll(gamePathBallCanvas);
    if (isShow) { // 只显示台面
        canvas.style.display = "none";
        gameMainBallCanvas.style.display = "none";
        gamePathCanvas.style.display = "none";
        gamePathBallCanvas.style.display = "none";
    } else { // 取消只显示台面
        canvas.style.display = "unset";
        gameMainBallCanvas.style.display = "unset";
        gamePathCanvas.style.display = "unset";
        gamePathBallCanvas.style.display = "unset";
    }
}


// 切换显示场景图形，隐藏emoji等图形层
function toggleSceneGraph(isShow, isReDraw) {
    if (isShow) { // 显示
        gameSceneGraphCanvas.style.display = "unset";
        gameSceneEmojiCanvas.style.display = "unset";
        if (isReDraw && isCanvasBlank(gameSceneEmojiCanvas)) { // 需要重画且画布为空，再重新绘制图形
            setSceneTheme();
        }
    } else { // 不显示
        gameSceneGraphCanvas.style.display = "none";
        gameSceneEmojiCanvas.style.display = "none";
    }
}


// 设置场景主题值
function setSceneThemeVal(ele, val) {
    //console.log(ele);
    if (!ele) return;
    if (val === undefined || val < 0) return;
    if (val === userConfig.sceneThemeMode) return;

    if (val === 2) { // 新年主题暂未实现
        alert("🏮：敬请期待哦~");
        return;
    }

    userConfig.sceneThemeMode = val;
    setSceneThemeText(val);

    // localStorage 存储更新 userConfig 对象
    localStorage.setItem('collide-try-user-settings', JSON.stringify(userConfig));

    // 修改了主题，需要刷新页面
    //sysConfig.isNeedReload = true;
    // 不刷新重画主题
    resetPageBg();
}


// 设置场景主题文字
function setSceneThemeText(val) {
    switch (val) {
        case 1:
            document.getElementById("sceneThemeMode").innerText = "冰雪主题";
            break;
        case 2:
            document.getElementById("sceneThemeMode").innerText = "新年主题";
            break;
        case 3:
            document.getElementById("sceneThemeMode").innerText = "田园主题";
            break;
        case 4:
            document.getElementById("sceneThemeMode").innerText = "星际主题";
            break;
        case 5:
            document.getElementById("sceneThemeMode").innerText = "夏日主题";
            break;
        default:
            document.getElementById("sceneThemeMode").innerText = "默认主题";
    }
}


// 设置当前操作方式文字
function setCurrPlayOptText(val) {
    let ele = document.getElementById("currPlayOpt");
    if (val === 1) { // 1-点按
        ele.innerText = "点按";
    } else { // 其他-默认拖拽
        ele.innerText = "拖拽";
    }
}


// 设置主角所在队颜色文字
function setMainTeamColorText(val) {
    //if (!val) return; // 这种校验返回，因为看不到后续的报错信息，反而影响排查
    let ele = document.getElementById("mainTeamColor");
    if (val === 'r') {
        ele.innerText = "红色";
        ele.classList.add("red");
    } else {
        ele.innerText = "蓝色";
        ele.classList.remove("red");
    }
}


// 切换显示运动路径层画布
function togglePathBallMoveShow(isShow) {
    if (isShow && userConfig.isJustShowTable) return; // 只显示台面时，不显示路径
    switchCanvasShow(gamePathCanvas, isShow);
}


// 切换显示本体路径层画布
function togglePathBallShow(isShow) {
    if (isShow && userConfig.isJustShowTable) return; // 只显示台面时，不显示路径
    switchCanvasShow(gamePathBallCanvas, isShow);
}


// 设置有变动，才刷新页面
function reloadAfterUserConfigSettingFinished(time, isReload) {
    let t0 = localStorage.getItem('collide-try-user-settings-time');
    if (!t0) t0 = "0";
    t0 = Number(t0);
    if (time > t0) {
        localStorage.setItem('collide-try-user-settings-time', time);
        if (isReload && sysConfig.isNeedReload) location.reload();
    }
}


// 指定游戏角色文本显示
function setGameRoleIdsText(val) {
    //console.log(">>>> setGameRoleIdsText val=" + val);
    //console.log(">>>> setGameRoleIdsText instanceof Array=" + (val instanceof Array));
    if (!val || val.length < 1) return;
    let ele, fName;
    for (let i = 0, len = val.length; i < len; i++) {
        //console.log(">>>> setGameRoleIdsText id=" + val[i]);
        if (val[i] < 0) continue;
        ele = document.getElementById("gameRoleId" + (i + 1));
        if (!ele) continue;
        fName = Role.getFullNameById(val[i]);
        if (!fName) continue;
        ele.innerText = fName;
        //ele.setAttribute("placeholder", fName);
        ele.setAttribute("value", fName);
    }
}


// 是否启用【指定游戏角色】
function isUseGameRoleIds() {
    let result = false;
    userConfig.gameRoleIds.some(id => {
        if (id > -1) {
            result = true;
            return true; // 退出循环 return false 也是退出循环，some 遍历没有 continue
        }
    });
    return result;
}


// 指定游戏角色是否完整，1-红队俩；2-蓝队俩；3-全部
function isUseGameRoleIdsFull(no) {
    let result = false;

    switch (no) {
        case 1:
            if (userConfig.gameRoleIds[0] > -1 && userConfig.gameRoleIds[1] > -1) result = true;
            break;
        case 2:
            if (userConfig.gameRoleIds[2] > -1 && userConfig.gameRoleIds[3] > -1) result = true;
            break;
        default:
            if (userConfig.gameRoleIds[0] > -1 && userConfig.gameRoleIds[1] > -1 && userConfig.gameRoleIds[2] > -1 && userConfig.gameRoleIds[3] > -1) result = true;
    }

    return result;
}


// 导入/导出角色和坐标
var rolePosInput = document.getElementById("shareRoleAndPos");
var rpShareCopy = document.getElementById("rpShareCopy");
var rpShareImport = document.getElementById("rpShareImport");

onMounted(() => {
    if (!rolePosInput) rolePosInput = document.getElementById("shareRoleAndPos");
    if (!rpShareCopy) rpShareCopy = document.getElementById("rpShareCopy");
    if (!rpShareImport) rpShareImport = document.getElementById("rpShareImport");
})

// 重置分享内容
function resetShareContent() {
    rolePosInput.removeAttribute('readonly', 'readonly');
    rolePosInput.value = "";
    // 切换到显示【导入】按钮
    rpShareCopy.style.display = "none";
    rpShareImport.style.display = "unset";
}

// 设置显示内容
function setShareContent() {
    if (!balls || balls.length < 1) return;
    let shareObjArr = [];
    balls.some(ball => {
        // 双子分身不用设置
        if (ball.roleId === Role.SHUANGZI.id && ball === twinBall) return;
        let shareObj = { rid: -1, x: 0, y: 0, m: 0, no: 0, tc: 'r' };
        shareObj.rid = ball.roleId;
        // 像素转砖格
        let pos = { x: ball.x, y: ball.y };
        switchPxOrGird(pos, 0);
        shareObj.x = pos.x;
        shareObj.y = pos.y;
        shareObj.m = ball.isMainBall ? 1 : 0;
        shareObj.no = ball.no;
        shareObj.tc = ball.teamColor;
        shareObjArr.push(shareObj);
    });
    rolePosInput.value = JSON.stringify(shareObjArr);
    // 切换到显示【复制】按钮
    rpShareCopy.style.display = "unset";
    rpShareImport.style.display = "none";
}

// 复制分享内容
function copyShareContent() {
    rolePosInput.setAttribute('readonly', 'readonly');
    rolePosInput.setSelectionRange(0, 9999);
    rolePosInput.select();
    document.execCommand('copy');
    rpShareCopy.innerText = "✓";
    rpShareCopy.disabled = true;
    setTimeout(() => {
        rpShareCopy.innerText = "复制";
        rpShareCopy.disabled = false;
        rolePosInput.removeAttribute('readonly', 'readonly');
    }, 5000);
}

// 检查导入内容
function checkShareContent() {
    if (!rolePosInput.value || rolePosInput.value.replaceAll(" ", "") === "") return false;
    let result = false;
    try {
        let shareObjArr = JSON.parse(rolePosInput.value);
        result = true;
    } catch (e) { }
    return result;
}

// 确认导入角色和坐标
function importShareContent() {
    if (!checkShareContent()) {
        alert("请检查粘贴内容是否完整，或者改动是否正确！");
        return;
    }
    userConfig.shareRoleAndPos = rolePosInput.value;
    // 更新缓存
    localStorage.setItem('collide-try-user-settings', JSON.stringify(userConfig));
    console.log(">>>> importShareContent userConfig in localStorage updated.");
    rpShareImport.innerText = "✓";
    rpShareImport.disabled = true;

    // 需要重新刷新页面
    //sysConfig.isNeedReload = true;
    // 不刷新页面导入角色和坐标
    reInit(true, true);

    setTimeout(() => {
        rpShareImport.innerText = "导入";
        rpShareImport.disabled = false;
    }, 5000);
}


// 测试 some 遍历
function testSomeList() {
    let arr = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
    console.log(">>>> testSomeList arr:", arr);
    arr.some(id => {
        if (id === 6) {
            //return true; // 退出循环，后面不再执行
            return false; // continue
            //return; // continue
        }
        console.log(">>>> testSomeList:", id);
    });
    console.log(">>>> testSomeList end.");
}
//testSomeList();


// 测试 forEach 遍历
function testForEachList() {
    let arr = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
    console.log(">>>> testForEachList arr:", arr);
    arr.forEach(id => {
        if (id === 6) {
            //return true; // continue
            return false; // continue
            //return; // continue
        }
        console.log(">>>> testForEachList:", id);
    });
    console.log(">>>> testForEachList end.");
}
//testForEachList()


// gameRoleIds 输入控制
var gameRoleIdEles;
onMounted(() => {
    gameRoleIdEles = document.getElementsByClassName('div-input-game-roles');
    for (let i = 0, len = gameRoleIdEles.length; i < len; i++) {
        let ele = gameRoleIdEles[i];
        // 输入监听
        ele.addEventListener("input", (e) => { // 注意，input 事件每次接收到的是新内容
            // 处理事件默认行为，防止事件冒泡
            doEventDefault(e);
            //console.log(e.target);
            // 获取输入框内容
            let inVal = e.target.innerText;
            inVal = inVal.replaceAll(" ", "");
            e.target.innerText = inVal;

            // 限制长度
            if (inVal.length > 10) {
                inVal = inVal.slice(0, 11);
            }

            // 角色全称自动补全
            let newVal = Role.getFullNameByKeyWord(inVal);
            console.log(">>>> e.target newVal=" + newVal);
            inVal = newVal;
            e.target.innerText = inVal;
            if (!newVal) return;

            // 默认值更新
            e.target.setAttribute("value", inVal);

            // 旧值
            let oldVal = userConfig.gameRoleIds[i];
            //console.log(">>>> e.target oldVal=" + oldVal);
            // id转全称
            let oldFName = Role.getFullNameById(oldVal);
            //console.log(">>>> e.target oldFName=" + oldFName);
            // 两值相等不处理
            if (inVal === oldFName) return;
            // 同队角色校验
            if (!checkSomeRoleInTeam(inVal, i)) { // 不通过
                inVal = "";
                e.target.innerText = inVal;
                alert("同队角色不能一样哦！");
                return;
            }

            doGameRoleIds(inVal, i);
        });

        // 按键按下松手监听，按下聚焦；退格键删除选择
        ele.addEventListener("keydown", (e) => { // focus 移动端不能自动聚焦；keydown 长按会触发多次，keyup 只触发一次
            // 处理事件默认行为，防止事件冒泡
            doEventDefault(e);
            //console.log(e.target);
            e.target.innerText = "";
            //ele.innerText = "";
            e.target.focus();
            //ele.focus();

            //console.log(">>>> e.keyCode=" + e.keyCode);
            // 退格键删除选择角色，并更新存储
            if (e.keyCode === 8) {
                e.target.innerText = "";
                e.target.setAttribute("value", "");
                if (userConfig.gameRoleIds[i] !== -1) doGameRoleIds("", i);
            }
        });

        // 失焦监听，为空设置默认值
        ele.addEventListener("blur", (e) => {
            // 处理事件默认行为，防止事件冒泡
            doEventDefault(e);
            //console.log(e.target);
            let text = e.target.innerText;
            if (text) return;
            let value = e.target.getAttribute("value");
            let placeholder = e.target.getAttribute("placeholder");
            if (placeholder) e.target.innerText = placeholder;
            //if (value) e.target.innerText = value;
        });

    }
})


// 校验同队角色是否可行，同队角色不能一样
function checkSomeRoleInTeam(val, idx) {
    let roleName1, roleName2, roleName3, roleName4;
    roleName1 = gameRoleIdEles[0].innerText;//.replaceAll(" ", "");
    roleName2 = gameRoleIdEles[1].innerText;
    roleName3 = gameRoleIdEles[2].innerText;
    roleName4 = gameRoleIdEles[3].innerText;

    if (idx < 2 && roleName1 && roleName2 && !roleName1.includes("输入") && !roleName2.includes("输入")) { // 不为空格，且不是默认值
        if (roleName1 === roleName2) return false;
    }
    if (idx > 1 && roleName3 && roleName4 && !roleName3.includes("输入") && !roleName4.includes("输入")) {
        if (roleName3 === roleName4) return false;
    }
    return true;
}


// gameRoleIds 保存
function doGameRoleIds(val, idx) {
    console.log(">>>> doGameRoleIds gameRoleIds input=" + val);
    // 更新配置值
    userConfig.gameRoleIds[idx] = Role.getIdByFullName(val);

    // localStorage 存储更新 userConfig 对象
    localStorage.setItem('collide-try-user-settings', JSON.stringify(userConfig));
    console.log(">>>> doGameRoleIds userConfig.gameRoleIds in localStorage updated.");

    // 指定了游戏角色，需要刷新页面
    //sysConfig.isNeedReload = true;

    // 如果设置了主角，不刷新直接进极速模式
    if (val && idx === 0) {
        // 提示主角需要在【极速开始】选项才会生效
        showGameSettingMainRoleDialog();
        userConfig.isFlashRole = true;
        setRolesFlash(userConfig.gameRoleIds, true);
    }
    // 改变了非主角，不刷新重新初始化角色数据
    reInit(false, true);
}


// 重置指定角色
function resetGameRoleIds(ele) {
    let hasValue = false;
    for (let i = 0, len = gameRoleIdEles.length; i < len; i++) {
        let ele = gameRoleIdEles[i];
        let value = ele.getAttribute("value");
        hasValue = hasValue || value;
        let placeholder = ele.getAttribute("placeholder");
        ele.innerText = placeholder;
        ele.setAttribute("value", "");
        userConfig.gameRoleIds[i] = -1;
    }
    if (!hasValue) return;

    // localStorage 存储更新 userConfig 对象
    localStorage.setItem('collide-try-user-settings', JSON.stringify(userConfig));
    console.log(">>>> resetGameRoleIds userConfig.gameRoleIds in localStorage updated.");

    // 重置指定游戏角色，需要刷新页面
    //sysConfig.isNeedReload = true;

    // 不刷新，按当前选择主角或模式重新初始化角色数据
    reInit(false, true);
}


// roleSpeedAddVal 角色加速或减速
onMounted(() => {
    const roleSpeedAddValInput = document.getElementById("roleSpeedAddVal");
    roleSpeedAddValInput.addEventListener("change", (e) => {
        // 处理事件默认行为，防止事件冒泡
        doEventDefault(e);
        // 获取输入框内容
        let inVal = e.target.value;
        inVal = inVal.replaceAll(" ", "");
        e.target.value = inVal;
        if (!inVal) {
            inVal = "0";
            e.target.value = inVal;
        }
        if (!Number.isInteger(Number(inVal))) {
            alert("请输入整数");
            return;
        }
        if (Number(inVal) < -20 || Number(inVal) > 200) {
            alert("数值范围：-20~200");
            return;
        }
        // 旧值
        let oldVal = userConfig.roleSpeedAddVal.toString();
        // 两值相等不处理
        if (inVal === oldVal) return;

        doRoleSpeedAddVal(inVal);
    });
})


// 执行处理角色加速/减速
function doRoleSpeedAddVal(str) {
    //console.log(">>>> doRoleSpeedAddVal roleSpeedAddVal input=" + str);
    // 更新配置值
    userConfig.roleSpeedAddVal = Number(str);
    // localStorage 存储更新 userConfig 对象
    localStorage.setItem('collide-try-user-settings', JSON.stringify(userConfig));
    console.log(">>>> doRoleSpeedAddVal userConfig.roleSpeedAddVal in localStorage updated.");

    // 更新主球速度，不用刷新页面
    setSpeed();
}


// animate 死循环自动退出
onMounted(() => {
    const animateAutoRestTimeInput = document.getElementById("animateAutoRestTime");
    animateAutoRestTimeInput.addEventListener("change", (e) => {
        // 处理事件默认行为，防止事件冒泡
        doEventDefault(e);
        // 获取输入框内容
        let inVal = e.target.value;
        inVal = inVal.replaceAll(" ", "");
        e.target.value = inVal;
        if (!inVal) {
            alert("自动恢复时间不能为空");
            return;
        }
        if (!isATimeValValidByRegExp(inVal)) {
            alert("请输入大于零的整数");
            return;
        }
        if (Number(inVal) < 5) {
            inVal = "5";
            e.target.value = inVal;
        }
        // 旧值
        let oldVal = userConfig.animateAutoRestTime.toString();
        // 两值相等不处理
        if (inVal === oldVal) return;

        doAnimateAutoRestTime(inVal);
    });
})


// 处理自动恢复时间输入内容
function doAnimateAutoRestTime(str) {
    //console.log(">>>> doAnimateAutoRestTime animateAutoRestTime input=" + str);
    // 更新配置值
    userConfig.animateAutoRestTime = Number(str);
    // localStorage 存储更新 userConfig 对象
    localStorage.setItem('collide-try-user-settings', JSON.stringify(userConfig));
    console.log(">>>> doAnimateAutoRestTime userConfig.animateAutoRestTime in localStorage updated.");
}


// 自定义主题input输入框
onMounted(() => {
    const themeParamInputItems = document.getElementsByClassName("custom-theme-item-input");
    for (let i = 0, len = themeParamInputItems.length; i < len; i++) {
        let ele = themeParamInputItems[i];
        ele.addEventListener("click", (e) => {
            if (!e || !e.target || !e.target.id) return;
            doEventDefault(e);
            if (!userConfig.isUseCustomTheme) return;

        });
        ele.addEventListener("change", (e) => {
            //console.log(e.target.id);
            if (!e || !e.target || !e.target.id) return;
            doEventDefault(e);
            if (!userConfig.isUseCustomTheme) return;
            let inVal = e.target.value;
            inVal = inVal.replaceAll(" ", "");
            e.target.value = inVal;
            if (e.target.id === "name") { // 主题名称
                if (inVal.length < 1) {
                    alert("主题名称不能为空");
                    return;
                }
                if (inVal.length > 7) {
                    alert("主题名称长度不能超过7");
                    return;
                }
            } else if (e.target.id === "bgImage") { // 主题背景图片
                if (!isAImageFileName(inVal)) {
                    alert("请检查背景图片格式(jpg/jpeg/png/gif)");
                    return;
                }
            } else if (["tblWidth", "glWidth", "gnSize", "plWidth", "ccWidth"].includes(e.target.id)) { // 数值输入框
                if (inVal.length < 1) {
                    inVal = 0;
                    e.target.value = inVal;
                }
                if (!isNumber(inVal)) {
                    alert("请输入正确的数值");
                    return;
                }
                if (inVal.length > 5) {
                    alert("数值长度不能超过5");
                    return;
                }
                // 输入框默认字符类型转换为数值类型
                inVal = Number(inVal);
                inVal = roundNumber(inVal);
            } else if (e.target.id.toLocaleLowerCase().indexOf("color")) { // 颜色码类型输入框
                if (inVal !== "" && !Theme.isColorCode(inVal)) {
                    alert("请输入正确的颜色码（格式：#ffffffff）");
                    return;
                }
                // 颜色码统一小写
                inVal = inVal.toLocaleLowerCase();
                e.target.value = inVal;
            }
            else if (e.target.id.toLocaleLowerCase().indexOf("color")) { // 颜色码类型输入框
                if (inVal !== "" && !Theme.isColorCode(inVal)) {
                    alert("请输入正确的颜色码（格式：#ffffffff）");
                    return;
                }
                // 颜色码统一小写
                inVal = inVal.toLocaleLowerCase();
                e.target.value = inVal;
            }
            // 旧值
            let oldVal = currTheme[e.target.id];
            // 两值相等不处理
            if (inVal === oldVal) return;
            // 更新到 currTheme
            currTheme[e.target.id] = inVal;

            if (e.target.id === "name") { // 主题名称，不处理

            } else if (e.target.id === "bgColor") { // 处理背景颜色
                doPageBg(inVal);
            } else if (["tbColor", "glColor", "glmColor", "wkShowColor", "glWidth"].includes(e.target.id)) { // 处理台面参数变动
                // 更新主题参数，只重画台面
                doUpdateCustomTheme([1]);
            } else if (["tblColor", "tblWidth"].includes(e.target.id)) { // 处理台面边框参数变动
                // 更新主题参数，只重画边框
                doUpdateCustomTheme([2]);
            } else if (["gnColor", "gndColor", "gnSize"].includes(e.target.id)) { // 处理台面砖格坐标参数变动
                // 更新主题参数，只重画砖格坐标数值
                doUpdateCustomTheme([2]);
            }

            // 存储更新 localStorage
            localStorage.setItem("collide-try-custom-theme", JSON.stringify(currTheme));
            console.log(">>>> 自定义主题参数 currTheme." + e.target.id + " 已更新存储到 localStorage");
            //localStorage.setItem("collide-try-user-settings", JSON.stringify(userConfig));
            //console.log(">>>> 自定义主题参数 userConfig in localStorage updated.");
        });
    }
})

/*
// 处理输入法把弹窗顶上去的问题
const vh = window.visualViewport.height;
if (!os.isPc) window.visualViewport.addEventListener('resize', function () {
    // 变动大于 10%，且input聚焦，才调整
    if ((vh - window.visualViewport.height) / vh >= 0.10
        && pageBgInput == document.activeElement) {
        userSettingDialog.style.top = "50vh";
    } else {
        userSettingDialog.style.top = "0";
    }
});
*/

// 处理修改背景颜色
function doPageBg(code) {
    if (typeof code !== "string") {
        //if (isAImageFileName(currTheme.bgImage)) { // 之前是图片背景
        // 恢复设置图片背景时关闭的场景图形
        userConfig.isShowSceneGraph = true;
        // 场景图形层显示
        toggleSceneGraph(true);
        // 恢复到自带主题
        currTheme = Theme.getCurrTheme();
        // 重新计算变化属性值
        Theme.reCalculate(currTheme);
        // 重新绘制游戏台面
        reDrawTable(code);
        // 设置完成
        console.log(">>>> resetPageBg finished.");
        //}
    }

    // 重置body背景图片
    resetBodyImage(code, false);
}

// 重置页面背景图片
function resetBodyImage(bgColor, isStore) {
    currTheme.bgImage = ""; // 主题图片清空
    document.body.style.backgroundImage = null; // body图片清空
    // 重置页面背景颜色
    resetPageBgColor(bgColor);
    if (isStore) {
        localStorage.setItem("collide-try-custom-theme", JSON.stringify(currTheme));
    }
}

// 重置页面背景
function resetPageBg(code) {
    doPageBg(code);
}


// 重置页面背景颜色
function resetPageBgColor(code) {
    if (Theme.isColorCode(code)) setBodyBackgroundColor(code); // 设置背景颜色
    else setBodyBackgroundColor(Theme.getBgColorById(userConfig.sceneThemeMode)); // 恢复所选主题默认的背景颜色
}


// 更新主题修改
function doUpdateCustomTheme(code) {
    // 重新绘制游戏台面
    reDrawTable(code);
}


// 导入导出主题配置
onMounted(() => {
    const customThemeInputFile = document.getElementById("customThemeInputFile");
    const customThemeConfigItems = document.getElementsByClassName("custom-theme-conf-inout");
    for (let i = 0, len = customThemeConfigItems.length; i < len; i++) {
        let ele = customThemeConfigItems[i];
        ele.addEventListener("click", (e) => {
            //console.log(e.target.id);
            if (!e || !e.target || !e.target.id) return;
            doEventDefault(e);
            if (!userConfig.isUseCustomTheme) return;
            if (e.target.id === "customThemeInput") { // 导入
                customThemeInputFile.click();
            } else if (e.target.id === "customThemeOutput") { // 导出
                saveStringContentToFile(JSON.stringify(currTheme));
            }
        });
    }
    customThemeInputFile.addEventListener("click", (e) => {
        // 处理事件默认行为，防止事件冒泡 【会导致不能弹出文件管理器】
        //doEventDefault(e);

    });
    customThemeInputFile.addEventListener("change", function () {
        if (customThemeInputFile.files[0]) {
            let fName = customThemeInputFile.files[0].name;
            //fName = getFileShortName(fName, 5);
            //console.log(fName);
            if (!fName) {
                alert("主题配置文件名称识别失败");
                return;
            }
            let size = customThemeInputFile.files[0].size;
            if (size > 1 * 1024 * 1024) { // 限制1M以内
                alert("主题配置文件不大于1M");
                return;
            }

            try {
                importThemeConfig(customThemeInputFile.files[0]);
            } catch (e) {
                alert("导入主题配置失败");
                console.log(">>>> 导入主题配置失败：" + e.message);
            }
        } else {
            //console.log("未选择文件");
        }
    });
})


// 指定页面背景图片
onMounted(() => {
    const pageBgImageIcon = document.getElementById("pageBgImageIcon");
    const pageBgImageFile = document.getElementById("pageBgImageFile");
    pageBgImageIcon.addEventListener("click", (e) => {
        // 处理事件默认行为，防止事件冒泡
        doEventDefault(e);
        // 点击文件图标触发选择文件点击事件
        pageBgImageFile.click();
    });
    pageBgImageFile.addEventListener("click", (e) => {
        // 处理事件默认行为，防止事件冒泡 【会导致不能弹出文件管理器】
        //doEventDefault(e);
        //alert("请选择一张图片");
        pageBgImageFile.value = ""; // 清空已选择的文件，没效果
        if (!userConfig.isUseCustomTheme) return;
        if (!indexedDB) {
            alert("你的浏览器不支持 IndexedDB V" + dbVersion + "，请更换其他浏览器重试");
        }
    });
    if (indexedDB) pageBgImageFile.addEventListener("change", (event) => {
        if (pageBgImageFile.files[0]) {
            let fName = pageBgImageFile.files[0].name;
            fName = getFileShortName(fName, 5);
            //console.log(fName);
            if (!fName) {
                alert("图片名称识别失败");
                return;
            }
            let size = pageBgImageFile.files[0].size;
            if (size > 10 * 1024 * 1024) { // 限制10M以内
                alert("图片不能大于10M");
                return;
            }

            try {
                // 存入IndexedDB
                //alert(pageBgImageFile.files[0] instanceof Blob);
                putImageInDb(pageBgImageFile.files[0], currTheme.bgImageIdbKey);
                // 从IndexedDB读取图片，并设置body图片背景
                doPageBgImage(fName, false);
                // 清空已选择的文件，解决第二次选择相同的文件不会触发change
                event.target.value = ""; // 没效果
                pageBgImageFile.value = ""; // 没效果
            } catch (e) {
                alert("设置背景图片失败：\n" + e.stack);
                doGlobalErrorMsg(e, false);
            }
        } else {
            //console.log("未选择文件");
        }
    });
})


// 处理修改背景图片
function doPageBgImage(fName, isOnlySetBg) {

    if (!userConfig.isUseCustomTheme || !isAImageFileName(fName)) return;

    let transaction = IDB.transaction([tbName], 'readwrite');
    let tableStore = transaction.objectStore(tbName);
    // 从indexedDB读取图片设置背景
    doSetBodyBgImage(tableStore, fName);

    if (!isOnlySetBg) {
        //if (!isAImageFileName(currTheme.bgImage)) { // 之前不是图片背景
        // 更新存储背景图片
        currTheme.bgImage = fName;
        // 台面设置为透明
        currTheme.tbColor = Theme.setTbColor00(currTheme.tbColor);
        // 设置场景图形不显示
        userConfig.isShowSceneGraph = false;
        // 场景图形层隐藏
        toggleSceneGraph(false);
        // 重新绘制游戏台面
        reDrawTable();
        // 设置完成
        console.log(">>>> doPageBgImage finished.");
        //}
    }

    // 更新自定义主题存储
    localStorage.setItem("collide-try-custom-theme", JSON.stringify(currTheme));
    // localStorage 存储更新 userConfig 对象
    localStorage.setItem('collide-try-user-settings', JSON.stringify(userConfig));
}


// 执行设置图片背景操作
function doSetBodyBgImage(tableStore, fName) {
    let getKeyReq = tableStore.get(currTheme.bgImageIdbKey);
    getKeyReq.onsuccess = (event) => {
        // 注意是异步回调，不阻塞主线程
        let blob = event.target.result;
        if (blob) {
            let url = window.URL.createObjectURL(blob);
            //console.log(url);
            // 设置 body 图片背景
            document.body.style.backgroundImage = `url('${url}')`; // 图片地址
            document.body.style.backgroundPosition = "center"; // 图片位置
            if (os.isPc) {
                document.body.style.backgroundRepeat = "repeat"; // 图片平铺
                document.body.style.backgroundSize = "contain"; // 填充页面
            } else {
                document.body.style.backgroundRepeat = "no-repeat"; // 图片不平铺
                document.body.style.backgroundSize = "cover"; // 单个封面
            }
            // 设置文件名称显示
            document.getElementById("bgImage").value = fName;
        } else { // 文件获取失败
            document.getElementById("bgImage").value = "";
        }
    }
    getKeyReq.onerror = function (event) {
        document.getElementById("bgImage").value = "";
    }
}


// 斜边倾斜偏差输入框失去焦点时，保存数据
onMounted(() => {
    const wan8CocosTableMoveValsInput = document.getElementById("wan8CocosTableMoveVals");
    wan8CocosTableMoveValsInput.addEventListener("change", (e) => {
        // 处理事件默认行为，防止事件冒泡
        doEventDefault(e);
        // 获取输入框内容
        let inVal = e.target.value;
        inVal = inVal.replaceAll(" ", "");
        e.target.value = inVal;
        if (!inVal) {
            alert("斜边倾斜偏差输入内容不能为空");
            return;
        }
        // 旧值
        let oldVal = userConfig.wan8CocosTableMoveVals.toString();
        // 两值相等不处理
        if (inVal === oldVal) return;

        doWan8CocosTableMoveVals(inVal);
    });
})


// 处理斜边倾斜偏差输入内容
function doWan8CocosTableMoveVals(str) {
    //console.log(">>>> doWan8CocosTableMoveVals wan8CocosTableMoveVals input=" + str);
    if (!isMoveValValidByRegExp(str)) {
        alert("斜边倾斜偏差输入内容格式不符合要求");
        return;
    }
    if (!isMoveValValidBySplit(str)) return;

    // 更新配置值
    userConfig.wan8CocosTableMoveVals = str.split(",");
    // localStorage 存储更新 userConfig 对象
    localStorage.setItem('collide-try-user-settings', JSON.stringify(userConfig));
    console.log(">>>> doWan8CocosTableMoveVals userConfig.wan8CocosTableMoveVals in localStorage updated.");

    // 修改了台面斜边倾斜角度，需要刷新页面
    //sysConfig.isNeedReload = true;

    // 初始化台面切角
    initTableAngle();
    // 重画台面
    reDrawTableAndEgg();
    clearCanvasAll(gameSceneLinesCanvas);
    clearCanvasAll(gameSceneLinesBgCanvas);
    if (userConfig.isShowTableBorder) doDrawTableLines();
}


// 正则校验斜边倾斜偏差输入内容
function isMoveValValidByRegExp(str) {
    return /^([\-]?[0]{1}[\.]?[\d]*[\,]?[\s]*)*$/.test(str);
}


// 正则校验大于0的正整数
function isATimeValValidByRegExp(str) {
    return /^[1-9]\d*$/.test(str);
}


// 分割校验斜边倾斜偏差输入内容
function isMoveValValidBySplit(str) {
    //str = str.replaceAll(" ", "");
    let wan8CocosTableMoveValsIn = str.split(",");
    // 分割后是否有值
    if (!wan8CocosTableMoveValsIn) {
        alert("斜边倾斜偏差输入内容有误");
        return false;
    }
    // 是否只设置了一个0
    if (wan8CocosTableMoveValsIn.length === 1 && Number(wan8CocosTableMoveValsIn[0]) === 0) {
        // 允许设置一个0
    } else if (wan8CocosTableMoveValsIn.length != 8) {
        alert("斜边倾斜偏差值个数有误");
        return false;
    }
    // 单个值是否符合要求
    for (let i = 0; i < wan8CocosTableMoveValsIn.length; i++) {
        let num = Number(wan8CocosTableMoveValsIn[i]);
        //console.log(">>>> num[" + i + "]=" + num);
        if (!num && num !== 0) {
            alert("斜边倾斜偏差必须为数值");
            return false;
        }
        if (num < -0.5 || num > 0.5) {
            alert("斜边倾斜偏差绝对值不能超过0.5");
            return false;
        }
    }
    return true;
}


// 恢复默认设置
function resetUserSettings() {
    if (confirm("⚠️ 确定要恢复默认设置吗？")) { // 确认
        // 清除 localStorage sessionStorage 中，站点自身存储的数据
        Object.keys(localStorage).forEach(item => item.startsWith('collide-try') ? localStorage.removeItem(item) : '');
        Object.keys(sessionStorage).forEach(item => item.startsWith('collide-try') ? sessionStorage.removeItem(item) : '');
        // clear() 会清除当前网页域名下的缓存数据！影响本站其他应用缓存数据！注意，所有 html 本地文件，只算一个 file:// 域
        //localStorage.clear();
        //sessionStorage.clear();
        // 删除 IndexedDB 数据库【会导致IDB undefined，刷新页面没用，重启浏览器才能恢复正常】
        // TODO 最好是清除表数据就行了，数据库和表留着，避免重新创建
        if (indexedDB) clearTable(tbName);
        // 刷新页面【vue 重新加载后，历史记录清空】
        location.reload();
        // href 或 replace 都可以替换当前 history 跳转页面，避免一步一步返回
        //window.location.href = "#";
        //window.location.replace("#");
        // replaceState 替换 history 中的 state
        //window.history.replaceState(null, "", "#");
        //window.history.go(0);
    } else { // 取消

    }
}


// 导入主题配置
function importThemeConfig(file) {
    let reader = new FileReader();
    reader.readAsText(file, "UTF-8"); // TODO 注意是异步读取文件内容，几 KB 的小文件还是很快的
    reader.onload = function (e) {
        //let content = e.target.result;
        let content = reader.result;
        //console.log(content);
        if (!content) return;
        let customThemeIn;
        try {
            customThemeIn = JSON.parse(content);
            console.log(">>>> importThemeConfig: " + content);
            if (customThemeIn.id <= Theme.getMaxId()) {
                alert("导入主题与应用自带主题冲突");
                console.log(">>>> 导入主题与应用自带主题冲突 id: " + customThemeIn.id + "-" + Theme.getNameById(customThemeIn.id));
                return;
            }
        } catch (e2) {
            alert("配置文件解析失败");
            console.log(">>>> importThemeConfig JSON.parse error: " + e.message);
            return;
        }

        if (currTheme.id <= Theme.getMaxId()) {
            alert("应用自带的主题不支持修改");
            console.log(">>>> 应用自带的主题不支持修改 id: " + currTheme.id + "-" + Theme.getNameById(currTheme.id));
            return;
        }

        for (let f in currTheme) {
            currTheme[f] = customThemeIn[f];
        }

        // 有图片则设置背景图片并重画台面
        if (isAImageFileName(currTheme.bgImage) && currTheme.bgImageIdbKey) doPageBgImage(currTheme.bgImage);
        // 没有图片则清空之前的图片，并重画台面
        else {
            // 重置body背景图片
            resetBodyImage(currTheme.bgColor, false);
            // 重画整个台面（台面、边框、坐标、图形）
            reDrawTable();
        }

        // 刷新页面数据显示
        setCustomThemeVals();

        // 更新 localStorage 中的 currTheme
        localStorage.setItem('collide-try-custom-theme', JSON.stringify(currTheme));
        console.log(">>>> importThemeConfig currTheme in localStorage updated.");

        alert("主题配置导入完成");
        //location.reload();
        // 设置完成
        console.log(">>>> importThemeConfig finished.");
    }
    reader.onerror = function (e) {
        //console.log(reader.error);
        console.log(">>>> importThemeConfig error: " + e.message);
    }
}


// 保存文本内容到文件
function saveStringContentToFile(content) {
    if (!content) return;
    let objectURL, aTag, blob, file;
    try {
        let fName = "collide-try-theme-" + currTheme.name + "-" + sysConfig.version + ".txt";
        if (!objectURL) file = new File([content], {
            type: "text/plain;charset=utf-8"
        });
        // 生成链接
        if (!objectURL) objectURL = (window.URL || window.webkitURL).createObjectURL(file);
        // 创建一个 a 标签Tag
        aTag = document.createElement('a');
        //aTag.style.display = 'none';
        //aTag.setAttribute('id', 'blob-download-save-to-local');
        // 设置文件的下载地址
        aTag.href = objectURL;
        console.log(">>>> saveStringContentToFile aTag.href=" + aTag.href);
        //aTag.target = '_blank';
        //document.body.appendChild(aTag);
        // 设置保存后的文件名称
        aTag.download = fName;
        console.log(">>>> saveStringContentToFile aTag.download=" + aTag.download);
        //if (!os.isPc) alert(">>>> saveLocalHtml aTag.download=" + aTag.download);
        // 点击触发
        aTag.click();
        //aTag.remove();
        //document.body.removeChild(aTag);
    } catch (e) {
        doGlobalError(e, (sysConfig && sysConfig.alertErrorCount) ? sysConfig.alertErrorCount : 3);
    } finally {
        setTimeout(function () {
            // 释放掉blob对象，减少内存占用 TODO 【移动端因为太快释放了资源，导致一直提示“处理 blob 数据中...”，不能正常下载】
            if (objectURL) URL.revokeObjectURL(objectURL);
            // 移除元素，body没有添加就不用移除
            //if (aTag) aTag.remove();
        }, 20000); // 20 秒后再执行
    }
}


// 保存当前网页
// https://blog.csdn.net/qq_45677671/article/details/125905454
// https://www.jianshu.com/p/ee5e2963f243
function saveLocalHtml(ele) {

    if (!checkAccessKey()) return;

    let isConfirm = false;
    let t0 = localStorage.getItem('collide-try-save-remote-html-time');
    if (!t0) t0 = "0";
    t0 = Number(t0);
    if (t0 <= 0) { // 提示另外保存方法
        let titleEle = document.getElementsByTagName("title")[0];
        let fileFullName = "xxxx.html";
        if (titleEle) fileFullName = titleEle.innerText + ".html";
        if (!fileFullName.includes("角度练习")) fileFullName = "xxxx.html";
        //if (confirm("💡 温馨提示：\n如果长时间没反应，可能是链接不可用了，使用电脑浏览器 Ctrl+S 也可以保存离线版哦！")) { // 确认
        if (confirm("💡 温馨提示：\n点【确定】后，会弹出下载对话框，请自行将对话框中的文件格式改为【" + fileFullName + "】，文件名可以随意，但文件后缀一定要为 “.html” 才能打开运行哦！")) { // 确认
            //localStorage.setItem('collide-try-save-remote-html-time', new Date().getTime());
            isConfirm = true;
        } else { // 取消
            isConfirm = false;
        }
    }
    if (!isConfirm) return;

    // 移除body的style属性
    let bodyStyle = document.body.getAttribute('style');
    if (bodyStyle) document.body.removeAttribute('style');
    // 选择角色弹窗是否正在显示
    let chooseShowing = isDialogShowing(chooseRoleDialog);
    // 切换参数设置与选择角色弹窗
    switchUserSettingDialog(false);
    // 隐藏关闭所有dialog弹窗，保证离线版刚打开不会一直有弹窗
    hideAllDialog();

    // 没有输入正确的访问密钥，移除核心方法
    if (!checkAccessKey()) {
        let eles = document.getElementsByClassName("collide-try-core-code");
        if (eles) removeCoreScript(eles, null);
    }

    let objectURL, aTag;
    try {
        let titleEle = document.getElementsByTagName('title')[0];
        let htmlStr = htmlEle.outerHTML;
        let blob, file;
        /*
        if (!objectURL) blob = new Blob([htmlStr], {
            type: "text/plain;charset=utf-8"
        });
        */
        if (!objectURL) file = new File([htmlStr], titleEle.innerText + ".html", {
            type: "text/plain;charset=utf-8"
        });
        // 生成链接
        if (!objectURL) objectURL = (window.URL || window.webkitURL).createObjectURL(file);
        // 创建一个 a 标签Tag
        aTag = document.createElement('a');
        //aTag.style.display = 'none';
        //aTag.setAttribute('id', 'blob-download-save-to-local');
        // 设置文件的下载地址
        aTag.href = objectURL;
        console.log(">>>> saveLocalHtml aTag.href=" + aTag.href);
        //aTag.target = '_blank';
        //document.body.appendChild(aTag);
        // 设置保存后的文件名称
        aTag.download = document.getElementsByTagName('title')[0].innerText + ".html";
        //aTag.download = file.name;
        console.log(">>>> saveLocalHtml aTag.download=" + aTag.download);
        //if (!os.isPc) alert(">>>> saveLocalHtml aTag.download=" + aTag.download);
        // 点击触发
        aTag.click();
        //aTag.remove();
        //document.body.removeChild(aTag);
    } catch (e) {
        doGlobalError(e, (sysConfig && sysConfig.alertErrorCount) ? sysConfig.alertErrorCount : 3);
    } finally {
        setTimeout(function () {
            // 释放掉blob对象，减少内存占用 TODO 【移动端因为太快释放了资源，导致一直提示“处理 blob 数据中...”，不能正常下载】
            if (objectURL) URL.revokeObjectURL(objectURL);
            // 移除元素，body没有添加就不用移除
            //if (aTag) aTag.remove();
        }, 20000); // 20 秒后再执行
    }

    // 操作完成后，再恢复原样
    if (bodyStyle) document.body.setAttribute('style', bodyStyle);
    if (chooseShowing) switchDialogShow(chooseRoleDialog, true);
    switchUserSettingDialog(true);

}


// 下载网络文件
function saveRemoteHtml(ele) {

    if (!checkAccessKey()) {
        alert("请先输入正确的访问密钥！");
        return;
    }

    let isConfirm = false;
    let t0 = localStorage.getItem('collide-try-save-remote-html-time');
    if (!t0) t0 = "0";
    t0 = Number(t0);
    if (t0 <= 0) { // 提示另外保存方法
        //alert("💡 温馨提示：\n联网请求下载一个离线版文件（几百KB），如果长时间没反应，可能是链接不可用了，使用电脑浏览器 Ctrl+S 也可以保存离线版哦！");
        if (confirm("💡 温馨提示：\n联网请求下载一个离线版文件（几百KB），如果长时间没反应，可能是链接不可用了，使用电脑浏览器 Ctrl+S 也可以保存离线版哦！")) { // 确认
            //localStorage.setItem('collide-try-save-remote-html-time', new Date().getTime());
            isConfirm = true;
        } else { // 取消
            isConfirm = false;
        }
    }
    if (!isConfirm) return;

    let titleEle = document.getElementsByTagName('title')[0];
    let accessKey = localStorage.getItem('collide-try-access-key'); // TODO accessKey 更新后，nginx 也要同步更新 hashCode
    let url = "https://www.m1yellow.cn/collide-try?k=" + hashCode(accessKey) + "&f=" + titleEle.innerText + ".html"; // collide-try 末尾会自动加上 /
    console.log(">>>> saveRemoteHtml url=" + url);
    window.location.href = url; // 手机移动端下载后会停留在空白页面
    // 返回原来地址，移动端还是没用
    //history.back();
}


// 隐藏关闭所有dialog弹窗
function hideAllDialog() {
    let dialogs = document.getElementsByClassName("collide-try-dialog");
    //console.log(dialogs);
    if (!dialogs || dialogs.length < 1) return;
    for (let i = 0, len = dialogs.length; i < len; i++) {
        dialogs[i].style.display = "none";
    }
}


// 目前已有的自定义dialog弹窗确认按钮颜色，设置为跟撞击台面一样的颜色
// 在 drawSceneBg() 设置完背景色的时候调用
function setDialogOkColor(cVal) {
    let dialogOks = document.getElementsByClassName("collide-try-dialog-ok");
    //console.log(dialogOks);
    if (!dialogOks || dialogOks.length < 1) return;
    if (!cVal) cVal = "chartreuse";
    for (let i = 0, len = dialogOks.length; i < len; i++) {
        dialogOks[i].style.background = cVal;
    }
}


//////////////////////////////////////////////////////////////////////


//////////////////////////////////////////////////////////////////////
// 【工具类相关】 变量、方法区域 共用函数 通用函数 公共函数 函数区域
//////////////////////////////////////////////////////////////////////

// 是否为数值类型
function isNumber(value) {
    return !isNaN(parseFloat(value)) && isFinite(value);
}

// 保留指定小数位数，默认两位
function roundNumber(num, decimals = 2) {
    if (isNaN(num)) return -1;
    if (typeof num === 'string') num = Number(num);
    if (num === 0) return 0;
    return Math.round(num * Math.pow(10, decimals)) / Math.pow(10, decimals);
}


// 指定小数位，不够补0
function roundNumberStr(num, decimals = 2) {
    let f = Math.round(num * Math.pow(10, decimals)) / Math.pow(10, decimals);
    let s = f.toString();
    let rs = s.indexOf('.');
    if (rs < 0) {
        s += '.';
    }
    for (let i = s.length - s.indexOf('.'); i <= decimals; i++) {
        s += "0";
    }
    return s;
}


// 获取(n,m)范围随机数
// https://cloud.tencent.com/developer/article/1629795
function fullOpen(n, m) {
    if (m <= n) return n;
    let result = Math.random() * (m - n) + n;
    while (result === n) {
        result = Math.random() * (m - n) + n;
    }
    return result;
}


// [n, m] 整数 Math.random() -> [0, 1) 之间的伪随机浮点数
function fullCloseInt(n, m) {
    return Math.floor(Math.random() * (m - n + 1)) + n;
}
/*
for (let i = 0; i < 100; i++) {
    console.log(Role.getRandomRoleId());
}
*/


// 随机生成指定长度字符串
function randomString(len) {
    var str = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789';
    var result = '';
    for (var i = 0; i < len; i++)
        result += str[Math.floor(Math.random() * str.length)];
    return result;
}


// 字符串哈希
// https://segmentfault.com/q/1010000042400796
function hashCode(str) {
    var hash = 0, i, chr;
    if (str.length === 0) return hash;
    for (i = 0; i < str.length; i++) {
        chr = str.charCodeAt(i);
        hash = ((hash << 5) - hash) + chr;
        hash |= 0; // Convert to 32bit integer
    }
    return Math.abs(hash);
}


//https://blog.csdn.net/qq_45039540/article/details/112554604
//交集
function arrayIntersect(a, b) {
    return a.filter(function (v) { return b.indexOf(v) > -1 });
}
//差集
function arrayMinus(a, b) {
    return a.filter(function (v) { return b.indexOf(v) == -1 });
}
//补集
function arrayComplement(a, b) {
    return a.filter(function (v) { return !(b.indexOf(v) > -1) }).concat(b.filter(function (v) { return !(a.indexOf(v) > -1) }));
}
//并集
function arrayUnionSet(a, b) {
    return a.concat(b.filter(function (v) { return !(a.indexOf(v) > -1) }));
}
//去重
function arrayUnique(array) {
    let n = [];
    for (let i = 0; i < array.length; i++) {
        if (n.indexOf(array[i]) == -1) n.push(array[i]);
    }
    return n;
}


// 两平面⚪是否碰撞 两圆碰撞 两球碰撞
function is2CirclesCollided(ball0, ball1) {
    return (ball0.x - ball1.x) ** 2 + (ball0.y - ball1.y) ** 2 <= (ball0.radius + ball1.radius) ** 2 + sysConfig.epsilon;
}


// 判断两个对象是否相等
function isObjEquals(s, t) {
    return !isObjectChanged(s, t);
}

// 判断对象是否改变
// https://blog.csdn.net/qq_25742631/article/details/105581625
function isObjectChanged(source, comparison) {
    const iterable = (data) => ['Object', 'Array'].includes(getDataType(data));
    if (!iterable(source)) {
        throw new Error(`source should be a Object or Array , but got ${getDataType(source)}`);
    }

    if (getDataType(source) !== getDataType(comparison)) {
        return true;
    }

    const sourceKeys = Object.keys(source);

    const comparisonKeys = Object.keys({
        ...source,
        ...comparison
    });

    if (sourceKeys.length !== comparisonKeys.length) {
        return true;
    }

    return comparisonKeys.some(key => {
        if (iterable(source[key])) {
            return isObjectChanged(source[key], comparison[key]);
        } else {
            return source[key] !== comparison[key];
        }
    });
}

// 判断数据类型
function getDataType(data) {
    const temp = Object.prototype.toString.call(data);
    const type = temp.match(/\b\w+\b/g);
    return (type.length < 2) ? 'Undefined' : type[1];
}


// https://juejin.cn/post/6844904025587105800
// https://docs.cocos.com/creator/3.8/api/zh/class/Intersection2D?id=polygonCircle
/**
 * !#en Test polygon and circle
 * !#zh 多边形与圆形是否相交
 * @method polygonCircle
 * @param {Vec2[]} polygon - The Polygon, a set of points
 * @param {Object} circle - Object contains position and radius
 * @return {boolean}
 * @typescript polygonCircle(polygon: Vec2[], circle: {position: Vec2, radius: number}): boolean
 */
function polygonCircle(polygon, circle) {
    // 先判断圆心有没有在多边形内，如果在，一定相交
    var position = circle.position;
    if (pointInPolygon(position, polygon)) {
        return true;
    }
    // 否则遍历多边形的每一条边，如果圆形到边的距离小于圆的半径，则相交
    for (var i = 0, l = polygon.length; i < l; i++) {
        var start = i === 0 ? polygon[polygon.length - 1] : polygon[i - 1];
        var end = polygon[i];

        if (pointLineDistance(position, start, end, true) < circle.radius) {
            return true;
        }
    }

    return false;
}


/**
 * !#en Test whether the point is in the polygon
 * !#zh 测试一个点是否在一个多边形中
 * @method pointInPolygon
 * @param {Vec2} point - The point
 * @param {Vec2[]} polygon - The polygon, a set of points
 * @return {boolean}
 */
function pointInPolygon(point, polygon) {
    // 射线法判断点是否在多边形内
    // 点射线（向右水平）与多边形相交点的个数为奇数则认为该点在多边形内
    // 点射线（向右水平）与多边形相交点的个数为偶数则认为该点不在多边形内
    var inside = false;
    var x = point.x;
    var y = point.y;

    // use some raycasting to test hits
    // https://github.com/substack/point-in-polygon/blob/master/index.js
    var length = polygon.length;

    for (var i = 0, j = length - 1; i < length; j = i++) {
        var xi = polygon[i].x, yi = polygon[i].y,
            xj = polygon[j].x, yj = polygon[j].y,
            intersect = ((yi > y) !== (yj > y)) && (x < (xj - xi) * (y - yi) / (yj - yi) + xi);
        if (intersect) inside = !inside;
    }

    return inside;
}


/**
 * !#en Calculate the distance of point to line.
 * !#zh 计算点到直线的距离。如果这是一条线段并且垂足不在线段内，则会计算点到线段端点的距离。
 * @method pointLineDistance
 * @param {Vec2} point - The point
 * @param {Vec2} start - The start point of line
 * @param {Vec2} end - The end point of line
 * @param {boolean} isSegment - whether this line is a segment
 * @return {number}
 */
function pointLineDistance0(point, start, end, isSegment) {
    var dx = end.x - start.x;
    var dy = end.y - start.y;
    var d = dx * dx + dy * dy;
    var t = ((point.x - start.x) * dx + (point.y - start.y) * dy) / d;
    var p;

    if (!isSegment) {
        p = cc.v2(start.x + t * dx, start.y + t * dy);
    } else {
        if (d) {
            if (t < 0) p = start;
            else if (t > 1) p = end;
            else p = cc.v2(start.x + t * dx, start.y + t * dy);
        } else {
            p = start;
        }
    }

    dx = point.x - p.x;
    dy = point.y - p.y;

    return Math.sqrt(dx * dx + dy * dy);
}


// https://wenku.csdn.net/answer/c6b3a1a81b2048048988115b13bd5e74#:~:text=%E5%88%A4%E6%96%AD%E5%9C%86%E6%98%AF%E5%90%A6%E4%B8%8E%E5%A4%9A%E8%BE%B9%E5%BD%A2%E7%9A%84%E8%BE%B9%E7%9B%B8%E4%BA%A4%E3%80%82%20%E5%A6%82%E6%9E%9C%E5%9C%86%E5%BF%83%E5%88%B0%E8%BE%B9%E7%9A%84%E8%B7%9D%E7%A6%BB%E5%B0%8F%E4%BA%8E%E7%AD%89%E4%BA%8E%E5%8D%8A%E5%BE%84%EF%BC%8C%E5%88%99%E8%A1%A8%E7%A4%BA%E7%9B%B8%E4%BA%A4%E3%80%82%20%E5%88%A4%E6%96%AD%E5%9C%86%E6%98%AF%E5%90%A6%E5%9C%A8%E5%A4%9A%E8%BE%B9%E5%BD%A2%E5%86%85%E9%83%A8%E3%80%82,%E5%8F%AF%E4%BB%A5%E4%BD%BF%E7%94%A8%E5%B0%84%E7%BA%BF%E6%B3%95%EF%BC%8C%E4%BB%8E%E5%9C%86%E5%BF%83%E5%8F%91%E5%87%BA%E4%B8%80%E6%9D%A1%E5%B0%84%E7%BA%BF%EF%BC%8C%E5%A6%82%E6%9E%9C%E4%B8%8E%E5%A4%9A%E8%BE%B9%E5%BD%A2%E7%9A%84%E8%BE%B9%E4%BA%A4%E7%82%B9%E7%9A%84%E6%95%B0%E9%87%8F%E4%B8%BA%E5%A5%87%E6%95%B0%EF%BC%8C%E5%88%99%E8%A1%A8%E7%A4%BA%E5%9C%86%E5%9C%A8%E5%A4%9A%E8%BE%B9%E5%BD%A2%E5%86%85%E9%83%A8%E3%80%82%20%E6%A0%B9%E6%8D%AE%E6%AD%A5%E9%AA%A42%E5%92%8C%E6%AD%A5%E9%AA%A43%E7%9A%84%E7%BB%93%E6%9E%9C%E6%9D%A5%E5%88%A4%E6%96%AD%E5%9C%86%E4%B8%8E%E5%A4%9A%E8%BE%B9%E5%BD%A2%E6%98%AF%E5%90%A6%E7%9B%B8%E4%BA%A4%E3%80%82%20%E5%A6%82%E6%9E%9C%E6%9C%89%E4%B8%80%E6%9D%A1%E8%BE%B9%E7%9B%B8%E4%BA%A4%E6%88%96%E5%9C%86%E5%9C%A8%E5%A4%9A%E8%BE%B9%E5%BD%A2%E5%86%85%E9%83%A8%EF%BC%8C%E5%88%99%E8%A1%A8%E7%A4%BA%E7%9B%B8%E4%BA%A4%EF%BC%8C%E5%90%A6%E5%88%99%E4%B8%8D%E7%9B%B8%E4%BA%A4%E3%80%82
function pointLineDistance(point, start, end) {
    let x = point.x;
    let y = point.y;
    let x1 = start.x;
    let y1 = start.y;
    let x2 = end.x;
    let y2 = end.y;
    let cross = (x2 - x1) * (x - x1) + (y2 - y1) * (y - y1);
    if (cross <= 0) {
        return Math.sqrt((x - x1) * (x - x1) + (y - y1) * (y - y1));
    }
    let d2 = (x2 - x1) * (x2 - x1) + (y2 - y1) * (y2 - y1);
    if (cross >= d2) {
        return Math.sqrt((x - x2) * (x - x2) + (y - y2) * (y - y2));
    }
    let r = cross / d2;
    let px = x1 + (x2 - x1) * r;
    let py = y1 + (y2 - y1) * r;
    return Math.sqrt((x - px) * (x - px) + (y - py) * (y - py));
}


// https://codereview.stackexchange.com/questions/192477/circle-line-segment-collision
// 线段与圆是否相交，由于线段是定长的，检测不准确。向量形式的检测后续再研究
// Function to check intercept of line seg and circle
// A,B end points of line segment
// C center of circle
// radius of circle
// returns true if touching or crossing else false   
function doesLineInterceptCircle(A, B, C, radius) {
    var dist;
    const v1x = B.x - A.x;
    const v1y = B.y - A.y;
    const v2x = C.x - A.x;
    const v2y = C.y - A.y;
    // get the unit distance along the line of the closest point to
    // circle center
    const u = (v2x * v1x + v2y * v1y) / (v1y * v1y + v1x * v1x);


    // if the point is on the line segment get the distance squared
    // from that point to the circle center
    if (u >= 0 && u <= 1) {
        dist = (A.x + v1x * u - C.x) ** 2 + (A.y + v1y * u - C.y) ** 2;
    } else {
        // if closest point not on the line segment
        // use the unit distance to determine which end is closest
        // and get dist square to circle
        dist = u < 0 ?
            (A.x - C.x) ** 2 + (A.y - C.y) ** 2 :
            (B.x - C.x) ** 2 + (B.y - C.y) ** 2;
    }
    return dist < radius * radius;
}


// canvas制作圆角矩形（包括填充矩形的功能）兼容旧机型和浏览器
// https://juejin.cn/post/6977212150439739423
/**该方法用来绘制一个有填充色的圆角矩形 
*@param cxt:canvas的上下文环境 
*@param x:左上角x轴坐标 
*@param y:左上角y轴坐标 
*@param width:矩形的宽度 
*@param height:矩形的高度 
*@param radius:圆的半径 
*@param fillColor:填充颜色 
**/
function fillRoundRect(cxt, x, y, width, height, radius, /*optional*/ fillColor) {
    //圆的直径必然要小于矩形的宽高          
    if (2 * radius > width || 2 * radius > height) { return false; }

    cxt.save();
    cxt.translate(x, y);
    //绘制圆角矩形的各个边  
    drawRoundRectPath(cxt, width, height, radius);
    cxt.fillStyle = fillColor || "#000"; //若是给定了值就用给定的值否则给予默认值  
    cxt.fill();
    cxt.restore();
}


/**该方法用来绘制圆角矩形 
 *@param cxt:canvas的上下文环境 
 *@param x:左上角x轴坐标 
 *@param y:左上角y轴坐标 
 *@param width:矩形的宽度 
 *@param height:矩形的高度 
 *@param radius:圆的半径 
 *@param lineWidth:线条粗细 
 *@param strokeColor:线条颜色 
 **/
function strokeRoundRect(cxt, x, y, width, height, radius, /*optional*/ lineWidth, /*optional*/ strokeColor) {
    //圆的直径必然要小于矩形的宽高          
    if (2 * radius > width || 2 * radius > height) { return false; }

    cxt.save();
    cxt.translate(x, y);
    //绘制圆角矩形的各个边  
    drawRoundRectPath(cxt, width, height, radius);
    cxt.lineWidth = lineWidth || 2; //若是给定了值就用给定的值否则给予默认值2  
    cxt.strokeStyle = strokeColor || "#000";
    cxt.stroke();
    cxt.restore();
}

function drawRoundRectPath(cxt, width, height, radius) {
    cxt.beginPath(0);
    //从右下角顺时针绘制，弧度从0到1/2PI  
    cxt.arc(width - radius, height - radius, radius, 0, Math.PI / 2);

    //矩形下边线  
    cxt.lineTo(radius, height);

    //左下角圆弧，弧度从1/2PI到PI  
    cxt.arc(radius, height - radius, radius, Math.PI / 2, Math.PI);

    //矩形左边线  
    cxt.lineTo(0, radius);

    //左上角圆弧，弧度从PI到3/2PI  
    cxt.arc(radius, radius, radius, Math.PI, Math.PI * 3 / 2);

    //上边线  
    cxt.lineTo(width - radius, 0);

    //右上角圆弧  
    cxt.arc(width - radius, radius, radius, Math.PI * 3 / 2, Math.PI * 2);

    //右边线  
    cxt.lineTo(width, height - radius);
    cxt.closePath();
}


/**
 * 将颜色值rgb格式转换为hex的格式
 * @param {rgb} rgb 需要转换的rgb字符串
 * @return {string} 带#的颜色码
 */
function rgbToHex(rgb) {
    if (!rgb) return "";
    let arr = rgb
        .replace("rgb", "")
        .replace("(", "")
        .replace(")", "")
        .replaceAll(" ", "")
        .split(",");
    // 转十六进制
    let h = parseInt(arr[0]).toString(16).padStart(2, '0');
    let e = parseInt(arr[1]).toString(16).padStart(2, '0');
    let x = parseInt(arr[2]).toString(16).padStart(2, '0');
    let a = arr[3] ? (Math.round(255 * Number(arr[3])).toString(16).padStart(2, '0')) : "ff";
    return ("#" + h + e + x + a).toLocaleLowerCase();
}
//let rgb = "rgb(5, 19, 44)";
//console.log(rgbToHex(rgb)); // #05132c
//let rgb = "rgb(5, 19, 44, 0.5)";
//console.log(rgbToHex(rgb)); // #05132c80


/**
 * 将颜色值hex格式转换为rgb的格式
 * @param {hex} hex 字符串
 * @return {string} rgb 字符串
 */
function hexToRgb(hex) {
    var a = parseInt(((hex.indexOf('#') > -1 && hex.length == 9) ? hex.substring(7, 9) : "FF"), 16) * (1 / 255);
    var hex = parseInt(((hex.indexOf('#') > -1) ? hex.substring(1, 7) : hex), 16);
    //return {r: hex >> 16, g: (hex & 0x00FF00) >> 8, b: (hex & 0x0000FF), a: Number(a.toFixed(2))};
    return `rgb(${hex >> 16}, ${(hex & 0x00FF00) >> 8}, ${(hex & 0x0000FF)}, ${a.toFixed(2)})`;
}
//let hex = "#05132c";
//console.log(hexToRgb(hex)); // rgb(5, 19, 44, 1.00)
//let hex = "#05132c80";
//console.log(hexToRgb(hex)); // rgb(5, 19, 44, 0.50)


// 文件名缩短
function getFileShortName(name, len) {
    if (!name || typeof name !== 'string' || name.replaceAll(" ", "") === "") return "";
    if (name.length <= len) return name;
    let nameSegs = name.split(".");
    if (nameSegs.length < 2) return name;
    let suffix = nameSegs[nameSegs.length - 1].replaceAll(" ", "");
    if (suffix) suffix = "." + suffix;
    if (name.length - suffix.length <= len) return name;
    let result = name.substring(0, len) + "~" + suffix;
    return result;
}


// 判断是否为图片，简单从文件名后缀判断
function isAImageFileName(name) {
    if (!name || typeof name !== 'string' || name.replaceAll(" ", "") === "") return false;
    let nameSegs = name.split(".");
    if (nameSegs.length < 2) return false;
    let suffix = nameSegs[nameSegs.length - 1];
    suffix = suffix.replaceAll(" ", "").toLowerCase();
    if (["jpg", "jpeg", "png", "gif"].indexOf(suffix) < 0) return false;
    return true;
}


// 画箭头
//https://fedev.cn/canvas/drawing-arrow.html
function drawArrow(ctx, fromX, fromY, toX, toY, theta, headlen, width, color) {

    theta = typeof (theta) != 'undefined' ? theta : 30;
    headlen = typeof (theta) != 'undefined' ? headlen : 10;
    width = typeof (width) != 'undefined' ? width : 1;
    color = typeof (color) != 'color' ? color : '#000';

    // 计算各角度和对应的P2,P3坐标
    var angle = Math.atan2(fromY - toY, fromX - toX) * 180 / Math.PI,
        angle1 = (angle + theta) * Math.PI / 180,
        angle2 = (angle - theta) * Math.PI / 180,
        topX = headlen * Math.cos(angle1),
        topY = headlen * Math.sin(angle1),
        botX = headlen * Math.cos(angle2),
        botY = headlen * Math.sin(angle2);

    ctx.save();
    ctx.beginPath();

    var arrowX = fromX - topX,
        arrowY = fromY - topY;

    ctx.moveTo(arrowX, arrowY);
    ctx.moveTo(fromX, fromY);
    ctx.lineTo(toX, toY);
    arrowX = toX + topX;
    arrowY = toY + topY;
    ctx.moveTo(arrowX, arrowY);
    ctx.lineTo(toX, toY);
    arrowX = toX + botX;
    arrowY = toY + botY;
    ctx.lineTo(arrowX, arrowY);
    ctx.strokeStyle = color;
    ctx.lineWidth = width;
    ctx.stroke();
    ctx.restore();
}


//////////////////////////////////////////////////////////////////////


//////////////////////////////////////////////////////////////////////
// 【碰撞边界检测】 变量、方法区域
//////////////////////////////////////////////////////////////////////

let concurrentCollided = false;

// 墙面碰撞检测
// isCheck 表示是否为路径检测，目前路径检测只需要拿到第一个碰撞点即可返回
function checkWalls(ball, isCheck) {

    ball.isWallCollided = false; // 重置碰撞标志

    // 备份碰撞点坐标和速度
    ball.collidedP0.x = ball.x;
    ball.collidedP0.y = ball.y;
    // 速度只在第一个检测中备份
    ball.collidedV0.x = ball.vx;
    ball.collidedV0.y = ball.vy;

    // 墙面碰撞了，还要判断切面、蛋切面是否也碰撞了
    let lc = false; // 切线碰撞检测
    let ec = false; // 蛋切面碰撞检测

    // 初始坐标检测，分身初始位置，不检测碰撞
    if (!isRoleHideBody(ball)) {
        // 边界反弹【碰撞后速度反向】
        //console.log(">>>> ball.x - ball.radius = " + (ball.x - ball.radius));
        if (ball.x - ball.radius <= 0) { // 左墙面
            ball.isCollided = true; // 碰撞
            ball.isWallCollided = true;
            if (!isCheck) ball.collidedCount += 1; // 总碰撞次数 +1
            if (!isCheck) ball.wallCollidedCount += 1; // 墙壁碰撞次数 +1
            ball.x = ball.radius + 1 * dpr; // 1 * dpr 避免碰撞圈画出墙面
            // 改变了x的位置，还要找到对应的y位置
            setXOrY(ball, ball.collidedP0, false);
            console.log(">>>> 左墙面-" + ball.getBallDesc() + "-撞击点坐标：x=" + ball.x + ", y=" + ball.y);
            // TODO 墙面碰撞坐标更新后，还要获取切面碰撞状态，如果切面也碰撞了，别改变运动速度方向
            lc = checkLineCollided(ball);
            //if (isDuoduoExist) ec = checkEggCollided(ball);
            // 碰撞检测或者模拟运动，拿到第一个碰撞点，就可以直接返回了
            if (isCheck && !lc && !ec && recordCollidedPoint(ball) && !isRoleCanPierces()) return true;
            // 绘画碰撞虚线圆圈
            if (!lc && !ec && (!selectedBall || !isRoleCanPierces())) ball.drawCollidedPos();
            // TODO 能量损耗【只改变一个方向的速度大小，会导致入射、出射角度不满足反射定律】
            //ball.vx *= -sysConfig.bounce;
            if (!lc && !ec) ball.vx *= -1; // 速度反向
            // 反弹系数作用在合速度上
            checkBounce(ball);
        } else if (ball.x + ball.radius >= canvas.width) { // 右墙面
            ball.isCollided = true;
            ball.isWallCollided = true;
            if (!isCheck) ball.collidedCount += 1;
            if (!isCheck) ball.wallCollidedCount += 1;
            ball.x = canvas.width - ball.radius - 1 * dpr;
            setXOrY(ball, ball.collidedP0, false);
            console.log(">>>> 右墙面-" + ball.getBallDesc() + "-撞击点坐标：x=" + ball.x + ", y=" + ball.y);
            lc = checkLineCollided(ball);
            //if (isDuoduoExist) ec = checkEggCollided(ball);
            if (isCheck && !lc && !ec && recordCollidedPoint(ball) && !isRoleCanPierces()) return true;
            if (!lc && !ec && (!selectedBall || !isRoleCanPierces())) ball.drawCollidedPos();
            if (!lc && !ec) ball.vx *= -1;
            checkBounce(ball);
        }

        if (ball.y - ball.radius <= 0) { // 上墙面
            ball.isCollided = true;
            ball.isWallCollided = true;
            if (!isCheck) ball.collidedCount += 1;
            if (!isCheck) ball.wallCollidedCount += 1;
            ball.y = ball.radius + 1 * dpr;
            setXOrY(ball, ball.collidedP0, true);
            console.log(">>>> 上墙面-" + ball.getBallDesc() + "-撞击点坐标：x=" + ball.x + ", y=" + ball.y);
            lc = checkLineCollided(ball);
            if (isDuoduoExist && isCheckEgg(ball, isCheck)) ec = checkEggCollided(ball);
            if (isCheck && !lc && !ec && recordCollidedPoint(ball) && !isRoleCanPierces()) return true;
            if (!lc && !ec && (!selectedBall || !isRoleCanPierces())) ball.drawCollidedPos();
            if (!lc && !ec) ball.vy *= -1;
            checkBounce(ball);
        } else if (ball.y + ball.radius >= canvas.height) { // 下墙面
            //console.log(">>>> 下墙面-撞击点：" + ball.radius);
            ball.isCollided = true;
            ball.isWallCollided = true;
            if (!isCheck) ball.collidedCount += 1;
            if (!isCheck) ball.wallCollidedCount += 1;
            ball.y = canvas.height - ball.radius - 1 * dpr;
            setXOrY(ball, ball.collidedP0, true);
            console.log(">>>> 下墙面-" + ball.getBallDesc() + "-撞击点坐标：x=" + ball.x + ", y=" + ball.y);
            lc = checkLineCollided(ball);
            if (isDuoduoExist && isCheckEgg(ball, isCheck)) ec = checkEggCollided(ball);
            if (isCheck && !lc && !ec && recordCollidedPoint(ball) && !isRoleCanPierces()) return true;
            if (!lc && !ec && (!selectedBall || !isRoleCanPierces())) ball.drawCollidedPos();
            if (!lc && !ec) ball.vy *= -1;
            checkBounce(ball);
        }
    }

    ball.isCheckFinished = false;
    //console.log(">>>> checkWalls isCheckFinished=" + ball.isCheckFinished);
    drawAndUpdate(ball, isCheck); // 绘制小球并更新速度
}


// 单独检测墙面是否碰撞
function checkWallCollided(ball, isChPos) {
    // 角色分身初始位置，不用管
    if (isRoleHideBody(ball)) return false;

    if (ball.x - ball.radius <= 0) { // 左墙面
        //console.log(">>>> 左墙面-撞击点坐标：x=" + ball.x + ", y=" + ball.y);
        if (isChPos) ball.x = ball.radius + 1 * dpr;
        return true;
    } else if (ball.x + ball.radius >= canvas.width) { // 右墙面
        //console.log(">>>> 右墙面-撞击点坐标：x=" + ball.x + ", y=" + ball.y);
        if (isChPos) ball.x = canvas.width - ball.radius - 1 * dpr;
        return true;
    }

    if (ball.y - ball.radius <= 0) { // 上墙面
        //console.log(">>>> 上墙面-撞击点坐标：x=" + ball.x + ", y=" + ball.y);
        if (isChPos) ball.y = ball.radius + 1 * dpr;
        return true;
    } else if (ball.y + ball.radius >= canvas.height) { // 下墙面
        //console.log(">>>> 下墙面-撞击点坐标：x=" + ball.x + ", y=" + ball.y);
        if (isChPos) ball.y = canvas.height - ball.radius - 1 * dpr;
        return true;
    }
    return false;
}


// 切角边碰撞检测
function checkLines(ball, isCheck) {
    //console.log(">>>> checkLines ball: " + JSON.stringify(ball));
    ball.isLineCollided = false; // 碰撞标识重置

    // 判断是否在切角范围内
    let angleIdx = isInAngleArea(ball);
    if (angleIdx > -1 && !isRoleHideBody(ball)) {
        console.log(">>>> angleIdx=" + angleIdx);
        let lineIndex = getOneAngleLineIndex(ball);
        let line = lines[lineIndex];
        // TODO 每次都循环检测四条线，有些浪费性能，后续有时间可以根据运动方向/角度，只检测可能碰到的边
        //lines.some(line => {
        let bounds = line.getBounds();
        // 判断小球是否在线段区域内
        if (ball.x + ball.radius > bounds.x && ball.x - ball.radius < bounds.x + bounds.width) {
            //console.log(">>>> ball in dounds.");
            let cos = Math.cos(line.rotation);
            let sin = Math.sin(line.rotation);
            // 位置以（line.x1，line.y1）为坐标原点来旋转坐标
            let pos = rotate(ball.x - line.x1, ball.y - line.y1, sin, cos, true); // 切角斜边坐标系旋转到水平
            let vel = rotate(ball.vx, ball.vy, sin, cos, true); // 小球速度方向同样要旋转

            ball.collidedP0.x = pos.x;
            ball.collidedP0.y = pos.y;

            // 当小球中心距离斜面的距离小于半径的时说明已经相碰撞了
            //console.log(">>>> Math.abs(pos.y)=" + Math.abs(pos.y));
            console.log(">>>> line" + lineIndex + " pos.y=" + pos.y);
            // TODO 小球碰撞前后在边界上下的距离都大于半径，导致认为没碰撞，其实是速度大于半径导致 ——> ⚪|⚪
            //if (Math.abs(pos.y) < ball.radius) { // 这个判断只适用在矩形内的线段，不适用切角边界
            if (pos.y - ball.radius <= 0) {
                console.log(">>>> line" + lineIndex + " ball Collided.");
                ball.isCollided = true; // 碰撞
                ball.isLineCollided = true;
                if (!isCheck) ball.collidedCount += 1;
                if (!isCheck) ball.wallCollidedCount += 1;

                // 判断小球是上面碰撞还是下面碰撞
                if (pos.y - vel.y <= 0) { // 下？
                    //pos.y = -ball.radius;
                    console.log(">>>> line" + lineIndex + "-下墙面");
                    // 切角边界只取正数，打不到下墙面
                    pos.y = ball.radius + 1 * dpr;
                } else { // 上
                    console.log(">>>> line" + lineIndex + "-上墙面");
                    pos.y = ball.radius + 1 * dpr;
                }

                // TODO 移动小球位置时，小球没有速度
                // 改变了y的位置，还要找到对应的x位置
                //console.log(">>>> vel.x=" + vel.x + ", vel.y=" + vel.y);
                let angle = Math.atan2(vel.y, vel.x);
                //console.log(">>>> angle=" + angle);
                let x = (ball.collidedP0.y - pos.y) / Math.tan(angle);
                //console.log(">>>> x=" + x);
                if (isNumber(x) && isNumber(pos.x - x)) pos.x -= x;
                //console.log(">>>> pos.x=" + pos.x + ", pos.y=" + pos.y);

                //vel.y *= -sysConfig.bounce; // 能量损耗
                vel.y *= -1; // 反向
                // 旋转回去
                let velF = rotate(vel.x, vel.y, sin, cos, false);
                let posF = rotate(pos.x, pos.y, sin, cos, false);
                ball.x = line.x1 + posF.x;
                ball.y = line.y1 + posF.y;

                // 如果只是检测碰撞，或者模拟撞击路线，可以直接返回了，避免下面绘制动画浪费性能
                // 注意，这里的 return true 只是退出了循环遍历，没有退出 checkLines 方法
                //if (isCheck && recordCollidedPoint(ball)) throw new Error("检测碰撞完成-中断循环", {cause:1000}); // cause 的值可以是任何类型
                console.log(">>>> line" + lineIndex + "-" + ball.getBallDesc() + "-撞击点坐标：x=" + ball.x + ", y=" + ball.y);
                if (isCheck && recordCollidedPoint(ball) && !isRoleCanPierces()) return true; // 非循环方法，直接返回结束整个方法

                // 运动状态在检测碰撞之后再改变
                // 切角边是后面检测的，墙面&切面都检测完成后，判断是否同时碰撞两个墙面
                if (concurrentCollided && ball.isMainBall && checkWallCollided(ball)) { // 同时碰撞了切面、墙面，速度直接反向
                    console.log(">>>> 撞墙角，同时碰撞了墙面和切面，速度直接反向");
                    ball.vx = -ball.collidedV0.x;
                    ball.vy = -ball.collidedV0.y;
                    // 因为是恢复了墙面碰撞前的备份值，需要单独计算一次碰撞损耗
                    checkBounce(ball);
                } else {
                    ball.vx = velF.x;
                    ball.vy = velF.y;
                    // TODO 没有同时碰撞，矫正速度过快，穿透斜面碰到墙的问题
                    if (!isCheck && ball.isWallCollided) ball.collidedCount -= 1;
                    if (!isCheck && ball.isWallCollided) ball.wallCollidedCount -= 1;
                }

                // 反弹系数作用在合速度上
                checkBounce(ball);
                // 绘画碰撞虚线圆圈
                if (!selectedBall || !isRoleCanPierces()) ball.drawCollidedPos();

                // 四条切角线一次只会碰到一条，碰撞后直接退出循环检测
                //return true; // TODO 只有一条线的话不用返回

            }
        }
        //});
    }

    ball.isCheckFinished = false;
    drawAndUpdate(ball, isCheck); // 绘制小球并更新速度
}


// 单独检测切面是否碰撞
function checkLineCollided(ball, isChPos) {

    // 判断是否在切角范围内
    let angleIdx = isInAngleArea(ball);
    if (angleIdx > -1 && !isRoleHideBody(ball)) {
        let lineIndex = getOneAngleLineIndex(ball);
        let line = lines[lineIndex];
        // TODO 每次都循环检测四条线，有些浪费性能，后续有时间可以根据运动方向/角度，只检测可能碰到的边
        //lines.some(line => {
        let bounds = line.getBounds();
        // 判断小球是否在线段区域内
        if (ball.x + ball.radius > bounds.x && ball.x - ball.radius < bounds.x + bounds.width) {
            //console.log(">>>> ball in dounds.");
            let cos = Math.cos(line.rotation);
            let sin = Math.sin(line.rotation);
            // 位置以（line.x1，line.y1）为坐标原点来旋转坐标
            let pos = rotate(ball.x - line.x1, ball.y - line.y1, sin, cos, true); // 切角斜边坐标系旋转到水平
            let vel = rotate(ball.vx, ball.vy, sin, cos, true); // 小球速度方向同样要旋转

            // 当小球中心距离斜面的距离小于半径的时说明已经相碰撞了
            //console.log(">>>> line" + lineIndex + " pos.y=" + pos.y);
            // TODO 小球碰撞前后在边界上下的距离都大于半径，导致认为没碰撞，其实是速度大于半径导致 ——> ⚪|⚪
            //if (Math.abs(pos.y) < ball.radius) { // 这个判断只适用在矩形内的线段，不适用切角边界
            if (pos.y - ball.radius <= 0) {
                //console.log(">>>> checkLineCollided line" + lineIndex + " ball Collided.");
                // 判断小球是上面碰撞还是下面碰撞
                if (pos.y - vel.y <= 0) { // 下？
                    //pos.y = -ball.radius;
                    //console.log(">>>> checkLineCollided line" + lineIndex + "-下墙面");
                    // 切角边界只取正数，打不到下墙面
                    pos.y = ball.radius + 1 * dpr;
                } else { // 上
                    //console.log(">>>> checkLineCollided line" + lineIndex + "-上墙面");
                    pos.y = ball.radius + 1 * dpr;
                }

                if (isChPos) {
                    // 旋转回去
                    let velF = rotate(vel.x, vel.y, sin, cos, false);
                    let posF = rotate(pos.x, pos.y, sin, cos, false);
                    ball.x = line.x1 + posF.x;
                    ball.y = line.y1 + posF.y;
                }

                return true;
            }
        }
        //});
    }

    return false;
}


// 检测球与球碰撞
// animate balls.forEach 循环调用
function checkOtherBalls(ball, isCheck) {
    //console.log(">>>> checkOtherBalls out " + ball.getBallDesc());

    ball.isBallCollided = false; // 碰撞标识重置

    // 瞄准阶段，可穿透角色，或者开启了瞄准穿透，不检测碰撞
    if (!selectedBall || !isRoleCanPierces() && !isTryCanPierces())
        balls.forEach(b => {
            /*
            只检测序号比ball大的，即可保证组合不重复，12 和 21 算重复
            外层 1 2 3 4
            内层 2 3 4
            */
            if (b.no <= ball.no) return;
            //console.log(">>>> checkOtherBalls in " + b.getBallDesc());

            // ball 可以是 balls 数组中的球，也可以是 tryMoveBall，tryMoveBall 是新的对象，默认为【主球】，不在 balls 数组中
            // 目前只支持主球、副球碰撞，不存在两主球碰撞的情况
            if (ball === tryMoveBall && b.isMainBall) return; // 退出单次循环，相当于 continue
            // 自己碰自己也不算
            if (ball !== tryMoveBall && b === ball) return;

            //console.log(">>>> checkOtherBalls " + ball.getBallDesc() + "-" + b.collidingNos[ball.no - 1]);
            if (isCollisionBallAndBall(ball, b) || isCrossedCollision(ball, b, isCheck)) { // TODO 处理正在碰撞被当成很多次碰撞问题。animate 60 帧内会调用很多次方法，导致穿一次被计算成很多次
                if (!isCheck) console.log(">>>> checkOtherBalls ball Collided > " + b.getBallDesc());
                ball.isBallCollided = true;
                ball.isCollided = true;
                if (!isCheck) ball.collidedCount += 1;
                if (!isCheck) ball.roleCollidedCount += 1;
                if (!isCheck) b.collidedCount += 1;
                if (!isCheck) b.roleCollidedCount += 1;

                // TODO 矫正碰撞时位置，解决重叠问题
                /*
                //if (isCheck || userConfig.currRole != Role.JIANGJIANG.id && userConfig.currRole != Role.KUILEI.id) {
                if (userConfig.currRole != Role.JIANGJIANG.id && userConfig.currRole != Role.KUILEI.id) {
                    let angle = getAngleOf2BallCollided(ball, b); // 正数【小球顺序有影响】
                    let collidedPoint = get2BallCollidedXYByAngle(angle, ball.radius + b.radius);
                    //console.log(">>>> get2BallCollidedXYByAngle, x=" + collidedPoint.x + ", y=" + collidedPoint.y);
                    // 重新设置小球位置
                    ball.x = b.x - collidedPoint.x;
                    ball.y = b.y - collidedPoint.y;
                }
                */

                // 有一个小球没有速度的情况，只调整有速度小球的坐标位置
                adjustMovingBallPos(ball, b);

                /*
                //console.log(">>>> do2BallsCollidedMV2 params=" + JSON.stringify(collideParams));
                if (userConfig.currRole === Role.JIANGJIANG.id || userConfig.currRole === Role.YLPAPA.id) {
                    //do2BallsCollidedMV2(ball, b, isCheck, false, collideParams);
                    doBackToBorderBallsCollided(ball, b, isCheck);
                } else if (userConfig.currRole === Role.KUILEI.id) {
                    if (isKuileiPulling) do2BallsCollidedMV2(ball, b, true, false, collideParams);
                    //else do2BallsCollidedMV2(ball, b, isCheck, false, collideParams);
                    else doBackToBorderBallsCollided(ball, b, isCheck);
                } else {
                    doBackToBorderBallsCollided(ball, b, isCheck);
                    //if (ball.isMainBall) doBackToBorderBallsCollided(ball, b, true);
                }
                */

                // TODO 显示瞄准碰撞指示圈【瞄准时会不停地拖动检测，导致指示圈有闪动，后续再搞】
                // 还要考虑同时碰墙、碰蛋、碰多个角色时怎么显示
                //if (isCheck) b.drawAimCircle();

                console.log(">>>> checkOtherBalls-" + ball.getBallDesc() + "-撞击点坐标：x=" + ball.x + ", y=" + ball.y);
                if (isCheck && recordCollidedPoint(ball)) return true; // 注意只是结束循环

                // 碰到就停止
                if (userConfig.isStopAfterCollided) {
                    // 调整碰撞位置
                    //doBackToBorderBallsCollided(ball, b, true);
                    b.vx = 0;
                    b.vy = 0;
                    //b.isMoving = false;
                    // 使用新方式调整碰撞位置
                    adjustMovingBallPos(ball, b);
                    ball.vx = 0;
                    ball.vy = 0;
                    //ball.isMoving = false;
                    return true;
                }

                // 主角只碰一次角色
                if (userConfig.isRoleCollidedOnce) {
                    // 只有外层传入的ball才可能为主球，内层b不会是主球
                    if (ball.isMainBall && ball.roleCollidedCount >= 2 || b.isMainBall && b.roleCollidedCount >= 2) {
                        // 调整碰撞位置
                        //doBackToBorderBallsCollided(ball, b, true);
                        ball.vx = 0;
                        ball.vy = 0;
                        //ball.isMoving = false;
                        // 如果这时候ball的速度刚好停止，这个调整坐标方法不会执行，会出现重叠
                        adjustMovingBallPos(ball, b);
                        b.vx = 0;
                        b.vy = 0;
                        //b.isMoving = false;
                        return true;
                    }
                }

                // 处理小球碰撞后速度                
                if (userConfig.currRole === Role.JIANGJIANG.id) {
                    // 简单模拟僵尸穿透加速、减速
                    doJiangjiangSpeed(ball, b);
                } else if (userConfig.currRole === Role.YLPAPA.id) {
                    // 处理帕帕速度
                    doPapaSpeed(ball, b);
                } else if (userConfig.currRole === Role.KUILEI.id) {
                    //console.log(">>>> checkOtherBalls isKuileiPulling=" + isKuileiPulling);
                    if (isKuileiPulling) do2BallsCollidedMV2(ball, b, false, true, collideParams);
                } else {
                    do2BallsCollidedMV2(ball, b, false, true, collideParams);
                }

                // 酷酷加速
                doKukuSpeed(ball, b);
                // 电音突破加速
                doDianyinSpeed(ball, b);
                // 太平乐加速
                doLeleSpeed(ball, b);

                // 碰撞速度削减
                checkBounce(ball); // TODO 自定义一个损耗，避免打完贴着一直不停的问题
                // 绘画碰撞虚线圆圈
                //if (!isCheck) ball.drawCollidedPos();
            }
        });

    if (!isDuoduoExist) ball.isCheckFinished = true; // 不检测蛋，则检测完球碰撞之后，所有检测完成
    drawAndUpdate(ball, isCheck); // 绘制小球并更新速度
}


// 判断是否为速度过快穿透导致未检测到碰撞。没有碰撞的时机太多了，时刻检测耗电很大
// 穿透检测：当前帧没碰撞但继续运动会有碰撞点，下一帧也没碰撞，但找不到碰撞点
function isCrossedCollision(ball, b, isCheck) {
    if (!isCheck) return false; // 只在瞄准阶段判断
    if (!ball || !b) return false;
    if (!ball.isMainBall) return false; // 只检测外层ball为主球的情况，其他非主球穿透的概率很小，节省性能
    // 只有一个小球有速度才检测
    const targetBall = getMovingBall(ball, b);
    if (!targetBall) return false;

    // 当前帧不能为穿透后的位置，调整位置后回到穿透前，然后又检测到穿透，陷入死循环【瞄准时稳定没啥问题，开打时会卡在原地循环】
    // 当前帧两小球没有碰撞，isCollisionBallAndBall 已经检测了
    //const cFlag = is2CirclesCollided(ball, b);
    //if (cFlag) return false;
    // 判断当前帧位置是否可能碰撞
    const currCollidedPos = getCurrFrameCollidedPos(ball, b);
    if (currCollidedPos) return false;
    // 获取上一帧碰撞坐标
    const preCollidedPos = getPreOrNextFrameCollidedPos(ball, b, 0);
    // 如果上一帧也没有碰撞坐标则不用检测，有则说明是穿透过来的，调整坐标位置回退到上一个碰撞点，执行碰撞逻辑
    if (!preCollidedPos) return false;
    return isCheck;

    /*
    // 当前帧为碰撞前的位置，判断下一帧是否为穿透【瞄准时不稳定有闪动，开打时会出现乱调整位置】
    // 当前帧两小球没有碰撞，isCollisionBallAndBall 已经检测了
    //const cFlag = is2CirclesCollided(ball, b);
    //if (cFlag) return false;
    // 判断当前帧位置是否可能碰撞，没有碰撞点则不用管
    const currCollidedPos = getCurrFrameCollidedPos(ball, b);
    if (!currCollidedPos) return false;
    
    // 下一帧无碰撞且不可能会碰撞，实际只需要满足不可能碰撞就行了
    // 获取下一帧坐标位置
    //const targetBall = getMovingBall(ball, b);
    //const nextPos = getPreOrNextFramePos(targetBall, 1);
    //const nFlag = is2CirclesCollided(nextPos, targetBall.no === ball.no ? b : ball);
    //if (nFlag) return false;
    // 获取下一帧碰撞点坐标位置，已经重叠碰撞不返回碰撞点
    const nextCollidedPos = getPreOrNextFrameCollidedPos(ball, b, 1);
    // 下一帧能找到碰撞点，说明还没有穿透
    if (nextCollidedPos) return false;
    return true;
    */
}


// 单独检测球与球碰撞
function checkOtherBallCollided(ball, isChPos) {
    let result = false;
    balls.some(b => {
        if (ball === tryMoveBall && b.isMainBall) return; // 类似于continue，终止当次循环。使用抛异常的方式，终止forEach整个循环
        if (ball !== tryMoveBall && b === ball) return;
        //if (isCollisionBallAndBall(ball, b)) { // 碰撞了
        if (is2CirclesCollided(ball, b)) {
            if (isChPos) {
                let angle = getAngleOf2BallCollided(ball, b); // 正数
                let collidedPoint = get2BallCollidedXYByAngle(angle, ball.radius + b.radius);
                //console.log(">>>> get2BallCollidedXYByAngle, x=" + collidedPoint.x + ", y=" + collidedPoint.y);
                // 重新设置小球位置
                ball.x = b.x - collidedPoint.x;
                ball.y = b.y - collidedPoint.y;
            }
            result = true;
            return true; // 只是退出循环
        }
    });
    return result;
}


// 判断是否达到速度上限
function isSpeedMax(ball) {
    let speed0 = getBallSpeed0(ball);
    if (ball.isMainBall && ball.roleId === Role.JIANGJIANG.id) { // 僵尸主打时，上限为原始速度的 1.6 倍
        if (ball.vx ** 2 + ball.vy ** 2 > (speed0 * 1.4) ** 2) return true; // 1.3 直打酷酷速度有点不够，1.5 又有点多了，需要更多实战观察验证
    } else { // 1.5
        if (ball.vx ** 2 + ball.vy ** 2 > (speed0 * 1.3) ** 2) return true; // 1.2
    }
    return false;
}


// 酷酷为队友加速60%/30%，突破后，自身加速50%
function isKukuCollided(ball0, ball1) {
    let result = false;
    // 是否同队
    if (ball0.teamColor !== ball1.teamColor) return result;
    // 是否有酷酷
    if (ball0.roleId !== Role.KUKU.id && ball1.roleId !== Role.KUKU.id) return result;
    // 是否有主球
    if (!ball0.isMainBall && !ball1.isMainBall) return result;
    result = true;
    return result;
}


// 僵尸碰撞
function isJiangjiangCollided(ball0, ball1) {
    let result = false;
    // 是否有僵僵
    if (ball0.roleId !== Role.JIANGJIANG.id && ball1.roleId !== Role.JIANGJIANG.id) return result;
    // 是否有主球
    if (!ball0.isMainBall && !ball1.isMainBall) return result;
    result = true;
    return result;
}


// 小丑碰撞
function isJoker2Collided(ball0, ball1) {
    let result = false;
    // 是否有小丑
    if (ball0.roleId !== Role.JOKER.id && ball1.roleId !== Role.JOKER.id) return result;
    // 是否有小丑分身
    if (ball0.no <= 4 && ball1.no <= 4) return result;
    // 是否有主球
    if (!ball0.isMainBall && !ball1.isMainBall) return result;
    // 是否为同队，同队不算，不减速
    //if (ball0.teamColor === ball1.teamColor) return result;
    result = true;
    return result;
}


// 电音碰撞
function isDianyinCollided(ball0, ball1) {
    if (!balls || balls.length < 1) return false;
    let result = false;
    // 是否同队
    if (ball0.teamColor === ball1.teamColor) return result;
    // 是否有电音
    if (ball0.roleId !== Role.DIANYIN.id && ball1.roleId !== Role.DIANYIN.id) return result;
    // 是否有主球【非主球碰到一样加速】
    //if (!ball0.isMainBall && !ball1.isMainBall) return result;
    // 是否有小丑分身，碰小丑分身不加速
    if ((ball0.roleId === Role.JOKER.id && ball0.no > 4)
        || (ball1.roleId === Role.JOKER.id && ball1.no > 4)) return result;
    // 电音碰撞对象是否存活，目前还没有血量伤害功能，先不管
    // 电音需要是主角或者跟主角一队
    let isRoleRight = false;
    if ((ball0.roleId === Role.DIANYIN.id && (ball0.isMainBall || ball0.teamColor === balls[0].teamColor))
        || (ball1.roleId === Role.DIANYIN.id && (ball1.isMainBall || ball1.teamColor === balls[0].teamColor))) isRoleRight = true;

    //console.log(">>>> isRoleRight", isRoleRight);
    if (!isRoleRight) return result;

    result = true;
    return result;
}


// 太平乐碰撞
function isLeleCollided(ball0, ball1) {
    let result = false;
    // 是否有太平乐
    if (ball0.roleId !== Role.LELE.id && ball1.roleId !== Role.LELE.id) return result;
    // 是否有主球
    if (!ball0.isMainBall && !ball1.isMainBall) return result;
    // 是否有小丑分身，碰小丑分身不加速
    if ((ball0.roleId === Role.JOKER.id && ball0.no > 4)
        || (ball1.roleId === Role.JOKER.id && ball1.no > 4)) return result;
    // 太平乐需要是主角
    let isRoleRight = false;
    if ((ball0.roleId === Role.LELE.id && ball0.isMainBall)
        || (ball1.roleId === Role.LELE.id && ball1.isMainBall)) isRoleRight = true;
    if (!isRoleRight) return result;
    // 碰到的角色需要是存活的【血量伤害系统还没实现先不管】

    result = true;
    return result;
}


// 处理酷酷加速
function doKukuSpeed(ball0, ball1) {
    if (!isKukuCollided(ball0, ball1)) return;
    // 为碰撞的队友加速60%【速度太快，手动调整比例】
    const kukuTeammateRatio = 1.6;
    // 突破后酷酷自身加速50%
    const kukuSelfRatio = 1.5;
    if (ball0.roleId === Role.KUKU.id) { // ball0 为酷酷
        if (ball0.addCount < 10) {
            if (ball0.isMainBall) {
                // 限制速度上限
                if (!isSpeedMax(ball0)) {
                    ball0.vx *= kukuSelfRatio;
                    ball0.vy *= kukuSelfRatio;
                }
                if (!isSpeedMax(ball1)) {
                    ball1.vx *= kukuTeammateRatio;
                    ball1.vy *= kukuTeammateRatio;
                }
            } else {
                if (!isSpeedMax(ball1)) {
                    ball1.vx *= kukuTeammateRatio;
                    ball1.vy *= kukuTeammateRatio;
                }
            }
            ball0.addCount++; // 每回合最多加速10次
        }
    } else { // ball1 为酷酷
        if (ball1.addCount < 10) {
            if (ball1.isMainBall) {
                if (!isSpeedMax(ball1)) {
                    ball1.vx *= kukuSelfRatio;
                    ball1.vy *= kukuSelfRatio;
                }
                if (!isSpeedMax(ball0)) {
                    ball0.vx *= kukuTeammateRatio;
                    ball0.vy *= kukuTeammateRatio;
                }
            } else {
                if (!isSpeedMax(ball0)) {
                    ball0.vx *= kukuTeammateRatio;
                    ball0.vy *= kukuTeammateRatio;
                }
            }
            ball1.addCount++;
        }
    }
}


// 处理僵僵加速、减速
function doJiangjiangSpeed(ball0, ball1) {
    if (userConfig.currRole !== Role.JIANGJIANG.id) return;
    if (!isJiangjiangCollided(ball0, ball1)) return;
    if (isKukuCollided(ball0, ball1)) return; // 和酷酷碰撞，走酷酷加速逻辑
    // 碰角色加速 20%
    const body1Ratio = 1 + 0.20; // 横向单角色能穿 6 次
    // 碰小丑分身减速 10%
    const body2Ratio = 1 - 0.15;
    if (ball0.roleId === Role.JIANGJIANG.id && ball0.isMainBall) {
        if (isJoker2Collided(ball0, ball1)) { // 碰到了小丑分身
            ball0.vx *= body2Ratio;
            ball0.vy *= body2Ratio;
        } else {
            if (!isSpeedMax(ball0)) {
                ball0.vx *= body1Ratio;
                ball0.vy *= body1Ratio;
            }
        }
    }
}


// 处理幽灵帕帕加速、减速
function doPapaSpeed(ball0, ball1) {
    if (userConfig.currRole !== Role.YLPAPA.id) return;
    if (isKukuCollided(ball0, ball1)) return; // 和酷酷碰撞，走酷酷加速逻辑
    // 碰角色加速 0
    const body1Ratio = 1 + 0;
    // 碰小丑分身减速 0
    const body2Ratio = 1 + 0;
    if (ball0.roleId === Role.YLPAPA.id && ball0.isMainBall) {
        if (isJoker2Collided(ball0, ball1)) { // 碰到了小丑分身
            ball0.vx *= body2Ratio;
            ball0.vy *= body2Ratio;
        } else {
            if (!isSpeedMax(ball0)) {
                ball0.vx *= body1Ratio;
                ball0.vy *= body1Ratio;
            }
        }
    }
}


// 处理电音加速
function doDianyinSpeed(ball0, ball1) {
    if (!isDianyinCollided(ball0, ball1)) return;
    //console.log(">>>> doDianyinSpeed isDianyinCollided=true");
    // 突破后，碰到存活对手，自身加速20%，手动调整比例，跟实战对比
    let dianyinRatio = 0.2, addSpeed, speed0; // 改为原始速度的比例
    if (ball0.roleId === Role.DIANYIN.id) { // ball0 为电音
        ball0.upgradeEffect = 1; // 设置突破效果
        if (!isSpeedMax(ball0)) {
            speed0 = getBallSpeed0(ball0);
            addSpeed = speed0 * dianyinRatio;
            //console.log(">>>> doDianyinSpeed addSpeed", addSpeed);
            let vRate = 1 + addSpeed / Math.sqrt(ball0.vx * ball0.vx + ball0.vy * ball0.vy);
            //console.log(">>>> doDianyinSpeed ball0 vRate", vRate);
            ball0.vx *= vRate;
            ball0.vy *= vRate;
        }
    } else { // ball1 为电音
        ball1.upgradeEffect = 1;
        if (!isSpeedMax(ball1)) {
            speed0 = getBallSpeed0(ball1);
            addSpeed = speed0 * dianyinRatio;
            let vRate = 1 + addSpeed / Math.sqrt(ball1.vx * ball1.vx + ball1.vy * ball1.vy);
            //console.log(">>>> doDianyinSpeed ball1 vRate", vRate);
            ball1.vx *= vRate;
            ball1.vy *= vRate;
        }
    }
}


// 处理太平乐加速
function doLeleSpeed(ball0, ball1) {
    if (userConfig.currRole !== Role.LELE.id) return;
    if (!isLeleCollided(ball0, ball1)) return;
    // 突破后，碰到存活角色（队友和对手都算），自身加速30%，后面加强到40%了，手动调整比例，跟实战对比
    const leleRatio = 1.50; // 30%->1.5 40%->2.0 太快
    if (ball0.roleId === Role.LELE.id) { // ball0 为太平乐
        if (!isSpeedMax(ball0)) {
            ball0.vx *= leleRatio;
            ball0.vy *= leleRatio;
        }
    }
}


// 检测碰蛋处理
function checkEggs(ball, isCheck) {

    ball.isEggCollided = false; // 碰撞标识重置

    if (isCheckEgg(ball, isCheck) && isInEggArea(ball)) {
        eggs.forEach(e => {
            //if (isCollisionBallAndBall(ball, e)) {
            if (is2CirclesCollided(ball, e)) {
                console.log(">>>> checkEggs egg ball Collided.");
                ball.isEggCollided = true;
                ball.isCollided = true;
                //if (!isCheck) ball.collidedCount += 1; // 蛋不算游戏角色
                if (!isCheck) ball.wallCollidedCount += 1;

                ball.collidedP0.x = ball.x;
                ball.collidedP0.y = ball.y;

                /*
                let angle = getAngleOf2BallCollided(ball, e); // 正数
                let collidedPoint = get2BallCollidedXYByAngle(angle, ball.radius + e.radius);
                //console.log(">>>> get2BallCollidedXYByAngle, x=" + collidedPoint.x + ", y=" + collidedPoint.y);
                // 重新设置小球位置
                ball.x = e.x - collidedPoint.x;
                ball.y = e.y - collidedPoint.y;
                // 改变了y的位置，还要找到对应的x位置
                //setXOrY(ball, collidedP0, true);
                */

                // 位置调整有偏差
                //do2BallsCollidedMV2(ball, e, true, false, collideParams);
                // 使用回退方式调整位置
                //doBackToBorderBallsCollided(ball, e, true);
                // 使用新的计算方式调整坐标位置
                adjustMovingBallPos(ball, e);

                console.log(">>>> checkEggs-" + ball.getBallDesc() + "-撞击点坐标：x=" + ball.x + ", y=" + ball.y);
                if (isCheck && recordCollidedPoint(ball)) return true;

                // 碰到就停止
                if (userConfig.isStopAfterCollided) {
                    ball.vx = 0;
                    ball.vy = 0;
                    return true;
                }

                if (concurrentCollided && ball.isMainBall && checkWallCollided(ball)) { // 同时碰撞了墙面、蛋切面，速度直接反向
                    console.log(">>>> 撞墙角，同时碰撞了墙面和蛋切面，速度直接反向");
                    ball.vx = -ball.collidedV0.x;
                    ball.vy = -ball.collidedV0.y;
                } else {
                    // 计算小球反弹速度和反向
                    do2BallsCollidedMV2(ball, e, false, true, collideParams);
                    // 蛋不会动
                    e.vx = 0;
                    e.vy = 0;
                    // 碰蛋反弹加速
                    //checkEggBounce(ball);
                }

                // 绘画碰撞虚线圆圈
                ball.drawCollidedPos();
            }
        });
    }

    ball.isCheckFinished = true; // 检测完成
    drawAndUpdate(ball, isCheck); // 绘制小球并更新速度
}


// 单独检测蛋切面是否碰撞
function checkEggCollided(ball, isChPos) {
    let result = false;
    if (isCheckEgg(ball, true) && isInEggArea(ball)) {
        eggs.some(e => {
            //if (isCollisionBallAndBall(ball, e)) {
            if (is2CirclesCollided(ball, e)) {
                console.log(">>>> checkEggCollided Collided.");
                if (isChPos) {
                    let angle = getAngleOf2BallCollided(ball, e); // 正数
                    let collidedPoint = get2BallCollidedXYByAngle(angle, ball.radius + e.radius);
                    //console.log(">>>> get2BallCollidedXYByAngle, x=" + collidedPoint.x + ", y=" + collidedPoint.y);
                    // 重新设置小球位置
                    ball.x = e.x - collidedPoint.x;
                    ball.y = e.y - collidedPoint.y;
                    //do2BallsCollidedMV2(ball, e, true, false, collideParams);
                }
                result = true;
                return true; // 只是退出循环
            }
        });
    }
    return result;
}


// 是否碰到蛋区域
function isInEggArea(ball) {
    let posCheck = ((ball.y - ball.radius <= 1 * sysConfig.girdSize || ball.y + ball.radius >= 21 * sysConfig.girdSize) && ball.x + ball.radius >= 6 * sysConfig.girdSize && ball.x - ball.radius <= 8 * sysConfig.girdSize);
    return posCheck;
}


// 是否需要检测碰蛋
// 非主角要检测
// 僵尸、幽灵，瞄准时检测
// 傀儡绳子，瞄准或拉回时检测
// 其他主角要检测
function isCheckEgg(ball, isCheck) {
    //return !ball.isMainBall || (ball.roleId !== Role.JIANGJIANG.id && ball.roleId !== Role.YLPAPA.id && (ball.roleId !== Role.KUILEI.id || isKuileiPulling));
    if (!ball.isMainBall) return true;
    if (ball.roleId === Role.JIANGJIANG.id || ball.roleId === Role.YLPAPA.id) {
        if (isCheck && !userConfig.isShowTryFullPath) return true;
        return false;
    }
    if (ball.roleId === Role.KUILEI.id) {
        if (isCheck && !userConfig.isShowTryFullPath || isKuileiPulling) return true;
        return false;
    }

    return true;
}


// 检测是否碰撞了自己
// 傀儡碰到自己后，绳索会立即停止
function checkSelfCollided(ball) {
    if (ball.isMainBall && ball.roleId === Role.KUILEI.id && !isKuileiPulling) {
        if (ball.wallCollidedCount < 1) return; // 至少碰墙面一次才会反弹碰到自己 
        tempCheckBall.roleId = ball.roleId;
        tempCheckBall.x = ball.x0;
        tempCheckBall.y = ball.y0;
        tempCheckBall.radius = ball.radiusTmp;
        // 检测碰撞
        if (is2CirclesCollided(ball, tempCheckBall)) {
            // 碰到自己，绳索立即停止
            ball.wallCollidedCount = 3;
        }
    }
}


// 小球带质量碰撞反弹
// friction:sysConfig.friction friction:roundNumber(0.8677 / 842 * canvas.width, 4)
var collideParams = { friction: 0.70, bounce: 0.70, eggId: -1, verCode: 0 };
onMounted(() => {
    //collideParams.friction = sysConfig.friction;
    collideParams.friction = roundNumber(0.8677 / 842 * canvas.width, 4);
    // 简单模拟摩擦力 f=0.2*m
    let m0 = balls.length > 0 ? balls[0].m : 70;
    collideParams.bounce = sysConfig.bounce ? sysConfig.bounce : (sysConfig.friction + 0.2 * m0);
    collideParams.eggId = Ball.SPECIALROLEID.eggId;
    collideParams.verCode = sysConfig.version;
    if (!collideParams.bounce) collideParams.bounce = 0.70;
    if (!collideParams.eggId) collideParams.eggId = -1;
    console.log(">>>> do2BallsCollidedMV2 params=" + JSON.stringify(collideParams));
});
//var dotCount = 0;
//function do2BallsCollidedMV2(ball0, ball1, isChPos, isChVel, params) {}


// 小球绘制及速度状态更新
function drawAndUpdate(ball, isCheck) {
    // 所有碰撞检测未完成，不绘制，也不更新速度，直接返回
    if (!ball.isCheckFinished) return;

    // 画被瞄准角色指示圈
    /* TODO 有很多空闲时间再研究向量了，不在自己的专业领域，真的很耗费时间精力！！
    if (isCheck) balls.forEach(b => {
        if (b.isMainBall) return; // continue
        // 检测拖动点到主球圆心的线段与非主球是否相交
        let start = {x: mouse.x, y: mouse.y}; // 线段起点-拖动点
        let end = {x: ball.x, y: ball.y}; // 线段终点-主球圆心
        let o = {x: b.x, y: b.y}; // 非主球圆心
        // 定长线段检测与圆相交，不能满足实际需求，实际需要的是检测变长线段与圆相交【真的没时间折腾了，先放一放，并且加了指示圈也没有好多少】
        if (doesLineInterceptCircle(start, end, o, b.radius)) b.drawAimCircle();
    });
    */

    // 小球位置没动不画
    if (ball.isMainBall) { // 只检测主球
        if (!isBallDrawAndUpdate(ball, 1)) return;
    } else { // 检测非主球
        if (!isBallDrawAndUpdate(ball, 2)) return;
    }

    if (userConfig.isStopAfter2WallCollided && ball.isMainBall && ball.wallCollidedCount >= 2) { // 碰两次后停止，用于测试观察角度
        ball.vx = 0;
        ball.vy = 0;
    }

    if (!isCheck) { // 检测碰撞点，不用画，优化性能
        ball.draw(); // 绘制小球
        ball.drawLinePath(ball.prePoint, { x: ball.x, y: ball.y }); // 绘制小球撞击轨迹-正常直线
        ball.drawBallPath(ball.prePoint, { x: ball.x, y: ball.y }); // 绘制小球撞击轨迹-本体直线
        if (ball.isWallCollided || ball.isLineCollided || ball.isBallCollided || ball.isEggCollided) ball.preCollided = { x: ball.x, y: ball.y }; // 备份碰撞点
        ball.prePoint = { x: ball.x, y: ball.y }; // 备份运动点
        //ball.drawPointPath(); // 绘制小球圆点撞击轨迹
    }
    ball.update(); // 更新小球运动状态
}


// 所有碰撞检测完成之后，要处理的事情
function doAfterCollidCheck() {
    // TODO
}


// 判断小球是否在四个切角（矩形）范围内。注意，这里只是粗略判断
function isInAngleArea(ball) {
    let idx = -1;
    // 左上角
    if ((ball.x - ball.radius <= sysConfig.girdSize * 3) && (ball.y - ball.radius <= sysConfig.girdSize * 3)) idx = 0;
    // 右上角
    if ((ball.x + ball.radius >= sysConfig.girdSize * 11) && (ball.y - ball.radius <= sysConfig.girdSize * 3)) idx = 1;
    // 右下角
    if ((ball.x + ball.radius >= sysConfig.girdSize * 11) && (ball.y + ball.radius >= sysConfig.girdSize * 19)) idx = 2;
    // 左下角
    if ((ball.x - ball.radius <= sysConfig.girdSize * 3) && (ball.y + ball.radius >= sysConfig.girdSize * 19)) idx = 3;
    //console.log(">>>> isInAngleArea idx=" + idx);
    return idx;
}


// 原理：同一条线上的点，倾斜角度相同
// 改变了y的位置，还要找到对应的x位置，相反也一样。flag=true 通过y改变x；flag=false 通过x改变y
// 切角边因为旋转了坐标系，单独处理
function setXOrY(ball, collidedP0, flag) {
    let angle = Math.atan2(ball.vy, ball.vx);
    if (flag) { // y->x
        let x = (collidedP0.y - ball.y) / Math.tan(angle);
        //console.log(">>>> x=" + x);
        // TODO 防止调整出错
        if (isNumber(x) && isNumber(ball.x - x)) ball.x -= x;
    } else { // x->y
        let y = (collidedP0.x - ball.x) * Math.tan(angle);
        //console.log(">>>> y=" + y);
        if (isNumber(y) && isNumber(ball.y - y)) ball.y -= y;
    }
}


// 摩擦力作用，整个台面
// requestAnimationFrame 60 帧，每帧调用一次，摩擦力是固定值，但单位时间内走的距离远的，摩擦力总和大。在同样的一帧时间内，摩擦力跟速度正相关
function checkFriction(ball) {
    if (sysConfig.friction <= 0) return;
    if (ball.isMainBall && ball.roleId === Role.KUILEI.id && !isKuileiPulling) return; // 傀儡的绳子不受摩擦力影响，拉回时影响
    // 求合速度
    let v = Math.sqrt(ball.vx * ball.vx + ball.vy * ball.vy);
    //if (v > 0 ) console.log(">>>> v=" + v);
    //if (v <= 0) return;
    // 模拟实战打完后缓慢停止运动效果
    // 摩擦力跟实时速度正相关，v0 / f0 = v1 / f1 -> f1 = v1 / (v0 / f0)
    let f1 = v / (ball.v / sysConfig.friction);
    if (!f1 || !isNumber(f1) || f1 < (0.5 / 842) * canvas.width) f1 = (0.5 / 842) * canvas.width; // 避免摩擦力太小，导致很久才停下来
    if (v > f1) {
        v -= f1;
    } else {
        v = 0;
    };
    // 合速度分解
    let angle = Math.atan2(ball.vy, ball.vx);
    ball.vx = Math.cos(angle) * v;
    ball.vy = Math.sin(angle) * v;
}


// 反弹系数速度损耗，每弹一次，速度会变慢一点
function checkBounce(ball, bounceVal) {
    if (!bounceVal && sysConfig.bounce <= 0) return;
    if (ball.isMainBall && ball.roleId === Role.KUILEI.id && !isKuileiPulling) return; // 傀儡的绳子不减速，拉回时影响
    if (ball.vx === 0 && ball.vy === 0) return;
    let v = Math.sqrt(ball.vx * ball.vx + ball.vy * ball.vy);
    //if (v > 0 ) console.log(">>>> v=" + v);
    let val = bounceVal ? bounceVal : sysConfig.bounce;
    if (v > val) {
        //console.log(">>>> checkBounce v=" + v);
        v -= val;
    } else {
        v = 0;
    };
    let angle = Math.atan2(ball.vy, ball.vx);
    ball.vx = Math.cos(angle) * v;
    ball.vy = Math.sin(angle) * v;
}


// 碰蛋反弹加速
function checkEggBounce(ball, eggBounceVal) {
    if (sysConfig.eggBounce <= 0) return;
    if (ball.isMainBall && (ball.roleId === Role.KUILEI.id && !isKuileiPulling || ball.roleId === Role.JIANGJIANG.id || ball.roleId === Role.YLPAPA.id)) return;
    if (ball.vx === 0 && ball.vy === 0) return;
    let v = Math.sqrt(ball.vx * ball.vx + ball.vy * ball.vy);
    let val = eggBounceVal ? eggBounceVal : sysConfig.eggBounce;
    v = v * (1 + val);
    let angle = Math.atan2(ball.vy, ball.vx);
    ball.vx = Math.cos(angle) * v;
    ball.vy = Math.sin(angle) * v;
}


// 两球碰撞检测（圆与圆碰撞）【目前检测判断还存在个别碰撞穿透问题】
function isCollisionBallAndBall(ball0, ball1) {
    // 俩球都没速度，不算碰撞
    if (ball0.vx === 0 && ball0.vy === 0 && ball1.vx === 0 && ball1.vy === 0) return false;
    let result = false;
    // 傀儡碰撞判断半径取绳子的半径
    let KLRadius;
    if (ball0.isMainBall && ball0.roleId === Role.KUILEI.id) {
        if (isKuileiPulling) KLRadius = ball0.radiusTmp;
        else KLRadius = ball0.pathRadius; // pathRadius-绳子路径半径，拉回之前默认的是 tryRadius-瞄准圈半径
    }
    // 双子本体与分身不会碰撞，会穿透
    let twinCheck = isTwinSelf(ball0, ball1);
    //console.log(">>>> isCollisionBallAndBall twinCheck=" + twinCheck);
    result = !twinCheck && (ball0.x - ball1.x) ** 2 + (ball0.y - ball1.y) ** 2 <= ((KLRadius ? KLRadius : ball0.radius) + ball1.radius) ** 2 + sysConfig.epsilon;
    //console.log(">>>> isCollisionBallAndBall 2 balls check result=" + result);

    // 如果是碰蛋检测，直接返回
    if (ball1.roleId === Ball.SPECIALROLEID.eggId) return result;

    // 备份一下碰撞状态
    let colliding01 = ball0.collidingNos[ball1.no - 1];

    if (result) {
        if (ball0.collidingNos) ball0.collidingNos[(ball1.no - 1) < 0 ? 0 : (ball1.no - 1)] = true;
        //if (ball1.collidingNos) ball1.collidingNos[(ball0.no - 1) < 0 ? 0 : (ball0.no - 1)] = true;
    } else {
        if (ball0.collidingNos) ball0.collidingNos[(ball1.no - 1) < 0 ? 0 : (ball1.no - 1)] = false;
        //if (ball1.collidingNos) ball1.collidingNos[(ball0.no - 1) < 0 ? 0 : (ball0.no - 1)] = false;
    }

    // 自己不算，ball.collidingNos 中，ball.no-1 是自己
    if (ball0.collidingNos) ball0.collidingNos[(ball0.no - 1) < 0 ? 0 : (ball0.no - 1)] = false;
    if (ball1.collidingNos) ball1.collidingNos[(ball1.no - 1) < 0 ? 0 : (ball1.no - 1)] = false;

    //console.log(">>>> isCollisionBallAndBall ball0:", ball0.collidingNos);
    //console.log(">>>> isCollisionBallAndBall ball1:", ball1.collidingNos);

    // 正在碰撞不重复检测【只对可穿透的角色生效，僵尸、幽灵、傀儡未拉回时】
    if ((userConfig.currRole === Role.JIANGJIANG.id || userConfig.currRole === Role.YLPAPA.id
        || (userConfig.currRole === Role.KUILEI.id && !isKuileiPulling))
        && colliding01 && colliding01 === ball0.collidingNos[ball1.no - 1]) result = false;

    //console.log(">>>> isCollisionBallAndBall final result=" + result);
    return result;
}


// 是否为双子本体与分身碰撞
function isTwinSelf(ball0, ball1) {
    let twinCheck = ball0.roleId === ball1.roleId && ball0.roleId === Role.SHUANGZI.id && ball0.teamColor === ball1.teamColor && ball0.no !== ball1.no;
    return twinCheck;
}


// 角色是否碰到了蛋（最多两个蛋）
function isBallAndEggCollided(ball) {
    if (!eggs || eggs.length < 1) return false;
    let result = false;
    eggs.some(egg => {
        if (is2CirclesCollided(ball, egg)) {
            result = true;
            return true; // 只是退出了循环
        }
    });
    return result;
}


// 两球碰撞时，圆心连线与x轴的夹角。注意两球顺序，看打印结果，取正数顺序
// ball0 为运动小球，ball1 为被撞小球
function getAngleOf2BallCollided(ball0, ball1) {
    let dx = ball1.x - ball0.x;
    let dy = ball1.y - ball0.y;
    let angle = Math.atan2(dy, dx);
    //console.log(">>>> getAngleOf2BallCollided=" + angle);
    return angle;
}


// 两球正好碰撞，通过夹角获取小球圆心与蛋圆心的相对距离x、y
// d 为俩球圆心距离
function get2BallCollidedXYByAngle(angle, d) {
    let x = Math.cos(angle) * d;
    let y = Math.sin(angle) * d;
    return { x: x, y: y };
}

//////////////////////////////////////////////////////////////////////


//////////////////////////////////////////////////////////////////////
// 【动画渲染控制】 变量、方法区域
//////////////////////////////////////////////////////////////////////

// 选中的小球
var selectedBall = null; // var 全局变量，定义顺序不影响前面方法使用
// 尝试运动的小球
//window.onload = function () {};
var tryMoveBall;
onMounted(() => {
    if (balls && balls.length > 0) tryMoveBall = new Ball(context, {
        no: balls[0].no,
        roleId: balls[0].roleId,
        isMainBall: true,
        x: 0,
        y: 0,
        vx: 0,
        vy: 0,
        radius: balls[0].radius,
        color: balls[0].color
    });
})
// 尝试运动的小球，第一次碰撞坐标
let tryMoveBallFirstCollidedPos = { x: 0, y: 0 };
let tryMoveBallFirstCollidedPosBack = { x: 0, y: 0 };
// 尝试运动的小球，碰撞点坐标
let tryMoveBallCollidedPoints = [];
// 控制绘制运动轨迹
let isAnimated = false; // 渲染完成
let isMoving = true; // 是否在运动
let isPlaying = true; // 是否在玩
let isKuileiPulling = false; // 傀儡是否正在拉回


// 重置动画渲染相关变量
function resetAnimate() {
    selectedBall = null;
    if (balls && balls.length > 0) tryMoveBall = new Ball(context, {
        no: balls[0].no,
        roleId: balls[0].roleId,
        isMainBall: true,
        x: 0,
        y: 0,
        vx: 0,
        vy: 0,
        radius: balls[0].radius,
        color: balls[0].color
    });
    tryMoveBallFirstCollidedPos = { x: 0, y: 0 };
    tryMoveBallCollidedPoints = [];
    isAnimated = false;
    //isMoving = true;
    //isPlaying = true;
    isKuileiPulling = false;
}


// 动画渲染入口
onMounted(() => {
    animate();
})


// 控制帧率
var fps = 60;
var fpsInterval = 1000 / fps;
var fpsLast = new Date().getTime();

// 动画渲染主函数。注意！多次调用这个渲染函数，会导致动画变快！即倍速快放的效果
// TODO 减少图形重复绘制渲染，可以很好地节省CPU性能
function animate() {
    if (!balls || balls.length < 1) return;

    // 检测是否在玩
    checkIsPlaying();

    // 闲置没玩了，或者长时间瞄准不动时，停止渲染，优化CPU性能
    if (!isPlaying) {
        // TODO 屏幕多点触碰，可能会出现程序异常情况（目前限制了多点触碰）：主球有速度但是不运动，导致不执行 resetBallsSpeed，出现死循环！
        // 有运动碰撞才处理停止事项；因为单独碰蛋不算碰撞，会导致 resetBallsSpeed 不能执行，出现卡死！ selectedBall 为 null 时，主球开始运动
        if (!selectedBall || checkAnyBallCollided(0)) {
            //doAfterBallStopped(balls);
            resetBallsSpeed(balls);
        }
        // 没有碰撞，就只是停止 animate 渲染
        return;
    }

    // 不停地渲染，相对来说比较耗性能
    // 执行次数通常是每秒 60 次，当页面处于未激活的状态下，该页面的屏幕绘制任务也会被浏览器暂停
    requestAnimationFrame(animate);
    //console.log(">>>> requestAnimationFrame 动画渲染 >>>>");

    // 帧率 90 120，需要进行帧率控制
    if (fpsCtrlFlag) {
        let fpsNow = new Date().getTime();
        let elapsed = fpsNow - fpsLast;
        if (elapsed <= fpsInterval) return; // 帧率时间不够，不往下执行
        fpsLast = fpsNow - (elapsed % fpsInterval); // 校正帧率时间
    }

    // 清空运动层画布【TODO 目前存在位置没变会重复画一次的问题，可以看到小丑分身透明度变化】
    doClearMoveCanvas();

    balls.forEach(ball => {
        if (selectedBall === ball) {
            //console.log(">>>> ball=" + JSON.stringify(ball));
            //balls.forEach(draw);
            //console.log(">>>> animate mainBall.x=" + ball.x + ", mainBall.y=" + ball.y);
            ball.draw();
        } else {
            try {
                checkSelfCollided(ball); // 自身碰撞检测
                checkWalls(ball, false); // 墙面碰撞检测
                checkLines(ball, false); // 切面碰撞检测
                checkOtherBalls(ball, false); // 球碰撞检测
                if (isDuoduoExist) checkEggs(ball, false); // 蛋碰撞检测
                checkFriction(ball); // 摩擦力作用
                doAfterCollidCheck(); // 检测完成后处理业务
            } catch (e) {
                doGlobalError(e, (sysConfig && sysConfig.alertErrorCount) ? sysConfig.alertErrorCount : 3);
            }
        }
    });

    // TODO 动画，动、画分开独立控制。在检查碰撞方法中可以更细粒度控制

    // 绘制
    //lines.forEach(draw); // 画了切角填充，切角线可以不画了
    //balls.forEach(draw); // 放检查碰撞方法中细粒度控制

    // 移动位置完成后，绘制移动轨迹提示
    //if (selectedBall) console.log(">>>> isChgPosFinished:" + selectedBall.isChgPosFinished);
    if (selectedBall && selectedBall.isChgPosFinished && selectedBall.isMainBall) {
        showMovePath();
    }

    // 渲染完成
    isAnimated = true;
}


// 小球绘制
function draw(ball) {
    ball.draw();
}


// 清空运动层画布
function doClearMoveCanvas() {
    // 清除主球运动层画布
    if (isBallDrawAndUpdate(null, 1)) { // 主球有运动
        console.log(">>>> doClearMoveCanvas gameMainBallCanvas");
        clearCanvasAll(gameMainBallCanvas);
    }
    // 清除主运动层画布
    if (isBallDrawAndUpdate(null, 2)) { // 非主球有运动
        console.log(">>>> doClearMoveCanvas canvas");
        clearCanvasAll(canvas);
    }
}


// 清空路径层画布
function doClearPathCanvas() {
    if (isBallDrawAndUpdate(null, 1)) { // 主球有运动
        // 清除球路径
        console.log(">>>> doClearPathCanvas gamePathBallCanvas");
        clearCanvasAll(gamePathBallCanvas);
        // 清除线路径
        console.log(">>>> doClearPathCanvas gamePathCanvas");
        clearCanvasAll(gamePathCanvas);
    }
}


// 清空画布所有内容
function clearCanvasAll(cvs) {
    // 指定区域清除，对于移动了坐标系原点的情况不适用
    /*
    let ctx = cvs.getContext('2d');
    ctx.clearRect(0, 0, cvs.width, cvs.height);
    ctx.beginPath(); // 开启新path，避免旧的path残留
    */

    // 重置画布高度，内容会被自动移除
    let w = cvs.width;
    let h = cvs.height;
    cvs.width = w;
    cvs.height = h;
}


// 刷新一次所有角色渲染，不影响路径和场景
function flushAllRoleOnce() {
    if (!balls || balls.length < 1) return;
    // 清空角色所在图层
    clearCanvasAll(canvas); // 角色运动层
    clearCanvasAll(gameMainBallCanvas); // 主角运动层
    // 重画
    balls.some(ball => {
        ball.draw();
    });
}


// 检测是否在玩
function checkIsPlaying() {
    isMoving = checkIsMoving();
    //console.log(">>>> isAnimated=" + isAnimated);
    console.log(">>>> isMoving=" + isMoving);
    //console.log(">>>> isFirstCollidedPointFounded=" + isFirstCollidedPointFounded);
    if (!isAnimated || isMoving) { // 没有渲染完成，或者速度还在变化，说明在玩
        isPlaying = true;
    } else {
        isPlaying = false;
    }

    // TODO 瞄准不动时，优化CPU性能
    if (isAnimated && isMoving && isFirstCollidedPointFounded) {
        isPlaying = false; // 注意，这里会停止渲染，后续需要再次手动调用 animate() 进行渲染
    }

    console.log(">>>> isPlaying=" + isPlaying);
}


// 检测多个小球是否在运动
function checkIsMoving() {
    let result = false;
    // 检测tryMoveBall
    //if (tryMoveBall) result = result || (tryMoveBall.vx > 0 || tryMoveBall.vy > 0);
    if (tryMoveBall) result = result || tryMoveBall.isMoving;
    if (result) return result;
    // 检测ball
    if (balls && balls.length > 0) balls.some(ball => {
        result = result || (ball.vx > 0 || ball.vy > 0);
        result = result || ball.isMoving;
        if (result) return true; // 只是退出了循环
    });
    return result;
}


// animate 单次执行次数过多，可能是出现了死循环，将所有小球速度置零
function resetBallsSpeed(balls) {
    // 重置所有角色速度，更新运动状态
    stopAllBalls(balls);
    // 处理停止事项 animate() 会调用
    doAfterBallStopped(balls);
    // 再检测一次 animate 状态
    checkIsPlaying();
    if (!isMoving && !isPlaying) console.log(">>>> 本回合结束 >>>>");
}


// 处理准备 tryMoveBall
function preTryMoveBall(num) {
    if (!tryMoveBall || !tryMoveBall.isMainBall) return;
    // tryMoveBall 颜色跟主球同步
    tryMoveBall.teamColor = balls[0].teamColor;
    if (tryMoveBall.roleId !== Role.KUILEI.id) return;
    // 调整半径
    switch (num) {
        case 0: // 还原
            tryMoveBall.radius = balls[0].radiusTmp;
            balls[0].radius = balls[0].radiusTmp;
            break;
        case 1: // 调整半径
            tryMoveBall.radius = balls[0].tryRadius; // 瞄准圈半径
            balls[0].radius = balls[0].tryRadius;
            break;
        default:

    }
}


// 重置tryMoveBall
function resetTryMoveBall() {
    if (!balls || balls.length < 1) return;
    if (!tryMoveBall) return;
    tryMoveBall.teamColor = balls[0].teamColor;
    tryMoveBall.v = balls[0].v;
    tryMoveBall.vx = 0;
    tryMoveBall.vy = 0;
    tryMoveBall.isMoving = false;
    tryMoveBall.isChgPosFinished = false;
}


// 尝试移动，找到第一个碰撞坐标，用于控制运动轨迹显示
let isFirstCollidedPointFounded = false;
function doTryMoveBallFirstCollidedPos() {
    if (!tryMoveBall || !selectedBall.isChgPosFinished) return;
    //console.log(">>>> doTryMoveBallFirstCollidedPos...");
    // 模拟小球运动
    // TODO 可能循环几次到四五十次，才能找到，非常耗性能！听到CPU风扇加速声响了！！【需要优化】
    let count = 0; // 蛮王极慢，循环了 36 次左右
    //while (!tryMoveBall.isCollided) {
    while (!isTryMoveBallRecordFinished()) {
        try {
            checkWalls(tryMoveBall, true); // 墙面碰撞检测
            checkLines(tryMoveBall, true); // 切面碰撞检测
            checkOtherBalls(tryMoveBall, true); // 球碰撞检测
            if (isDuoduoExist) checkEggs(tryMoveBall, true); // 蛋碰撞检测
            checkFriction(tryMoveBall); // 摩擦力作用
            doAfterCollidCheck(); // 检测完成后处理业务
        } catch (e) {
            doGlobalError(e, (sysConfig && sysConfig.alertErrorCount) ? sysConfig.alertErrorCount : 3);
        }

        // 达到次数后，就算没找到，也退出，避免死循环
        count++;
        if (count >= 100) break;
    }
    console.log(">>>> doTryMoveBallFirstCollidedPos count=" + count);
    console.log(">>>> 找到第一个撞击点坐标：x=" + tryMoveBallFirstCollidedPos.x + ", y=" + tryMoveBallFirstCollidedPos.y);
    isFirstCollidedPointFounded = true;
    // 重置标志
    if (tryMoveBall.isCollided) tryMoveBall.isCollided = false;
    // 重置速度
    doTryMoveBallFinished();
}


// 重叠碰撞时，调整有速度小球的坐标位置，只适用有一个小球有速度的情况，两球都有速度在核心碰撞方法调整
function adjustMovingBallPos(ball0, ball1, isCheck) {
    // 计算实际碰撞点坐标
    const pos = getPreOrNextFrameCollidedPos(ball0, ball1, 0);
    if (!pos) return;
    // 将运动小球坐标调整为实际碰撞点坐标
    const targetBall = getMovingBall(ball0, ball1);
    if (!targetBall) return;
    targetBall.x = pos.x;
    targetBall.y = pos.y;
}


// 获取两个小球之间有速度的小球
// null-两球都没有速度；0-两球都有速度；targetBall-有速度的小球
function getMovingBall(ball0, ball1) {
    if (!ball0 || !ball1) return null;
    if (ball0.vx + ball0.vy + ball1.vx + ball1.vy === 0) return null; // 都没有速度不检测
    if (ball0.vx + ball0.vy !== 0 && ball1.vx + ball1.vy !== 0) return 0; // 都有速度也不检测
    let targetBall = ball0; // targetBall 引用地址指向 ball0
    if (ball1.vx + ball1.vy !== 0) targetBall = ball1; // 只处理有速度的
    return targetBall;
}


// 获取当前帧碰撞点坐标
function getCurrFrameCollidedPos(ball0, ball1) {
    const targetBall = getMovingBall(ball0, ball1);
    if (!targetBall) return null;
    return calculateCircleCollision(targetBall, targetBall.no === ball0.no ? ball1 : ball0);
}


// 获取上一帧或下一帧碰撞点坐标
function getPreOrNextFrameCollidedPos(ball0, ball1, idx) {
    const targetBall = getMovingBall(ball0, ball1);
    if (!targetBall) return null;
    switch (idx) {
        case 0:
            const preBall = getPreOrNextFramePos(targetBall, 0);
            if (!preBall) return null;
            return calculateCircleCollision(preBall, targetBall.no === ball0.no ? ball1 : ball0);
        case 1:
            const nextBall = getPreOrNextFramePos(targetBall, 1);
            if (!nextBall) return null;
            return calculateCircleCollision(nextBall, targetBall.no === ball0.no ? ball1 : ball0);
        default:
            return null;
    }
}


// 获取上一帧或下一帧位置坐标信息
function getPreOrNextFramePos(targetBall, idx) {
    if (!targetBall) return null;
    switch (idx) {
        case 0:
            return doGetPreFramePos(targetBall);
        case 1:
            return doGetNextFramePos(targetBall);
        default:
            return null;
    }
}


function doGetPreFramePos(ball) {
    if (!ball) return null;
    if (ball.vx * ball.vy === 0) return null;
    let vRatio = 1.2;
    let preBall = {
        x: ball.x - ball.vx * vRatio,
        y: ball.y - ball.vy * vRatio,
        vx: ball.vx * vRatio, // 注意，这个速度不是实际上一帧的，已经减去了摩擦力，乘以 1.2 大致还原上一帧的速度
        vy: ball.vy * vRatio,
        radius: ball.radius
    };
    return preBall;
}


function doGetNextFramePos(ball) {
    if (!ball) return null;
    if (ball.vx * ball.vy === 0) return null;
    let tmpBall = {
        v: ball.v,
        vx: ball.vx,
        vy: ball.vy,
    };
    // 处理摩擦力
    checkFriction(tmpBall);
    let nextBall = {
        x: ball.x + tmpBall.vx,
        y: ball.y + tmpBall.vy,
        vx: tmpBall.vx,
        vy: tmpBall.vy,
        radius: ball.radius
    };
    return nextBall;
}


// 两球碰撞后，主球位置后退到碰撞边界
function doBackToBorderBallsCollided(ball0, ball1, isCheck) {
    if (!ball0 || !ball1) return;
    if (!ball0.vx && !ball0.vy) return;
    if (!isCheck) return;
    let count = 0; // 循环计数，避免死循环
    let bvx = 0, bvy = 0, bpx = 1, bvxyp = Math.abs(roundNumber(ball0.vx / ball0.vy)); // 后退的速度方向和大小 可能会有除0异常，但为0的情况后续没用到，没影响
    //if (!isNumber(bvxyp)) alert(bvxyp); // Infinity
    while (is2CirclesCollided(ball0, ball1)) {
        // 把速度大的设置为 bpx
        if (Math.abs(ball0.vx) >= Math.abs(ball0.vy)) {
            // 每次后退比例
            if (ball0.vx > 0) bvx = bpx;
            if (ball0.vx < 0) bvx = -bpx;
            if (ball0.vy > 0) bvy = roundNumber(bpx / bvxyp, 4);
            if (ball0.vy < 0) bvy = -roundNumber(bpx / bvxyp, 4);
        } else {
            if (ball0.vx > 0) bvx = roundNumber(bpx * bvxyp, 4);
            if (ball0.vx < 0) bvx = -roundNumber(bpx * bvxyp, 4);
            if (ball0.vy > 0) bvy = bpx;
            if (ball0.vy < 0) bvy = -bpx;
        }
        // 反向移动
        ball0.x -= bvx;
        ball0.y -= bvy;

        // 假定角色最大 3 格，每格最大 70 像素，count 最大 200 左右
        count++;
        if (count >= 200) break;
    }
    console.log(">>>> doBackToBorderBallsCollided count=" + count);

    // 取上一次碰撞坐标，因为 while 结束之后，是两球没有碰撞时的坐标，需要加一点点
    if (bvx || bvy) {
        ball0.x += bvx;
        ball0.y += bvy;
    }
}


// 尝试运动小球碰撞的记录是否完成
function isTryMoveBallRecordFinished() {
    // 僵尸、傀儡等穿透角色，取 userConfig.tryFullPathPointNum 配置值
    if (isRoleCanPierces()) {
        if (userConfig.currRole === Role.KUILEI.id && tryMoveBallCollidedPoints.length >= 3) return true;
        //if (userConfig.currRole === Role.JIANGJIANG.id && tryMoveBallCollidedPoints.length >= userConfig.tryFullPathPointNum + 1) return true;
        if (tryMoveBallCollidedPoints.length >= userConfig.tryFullPathPointNum) return true;
    } else { // 其他角色只取第一个碰撞点
        if (tryMoveBallFirstCollidedPos.x > 0 && tryMoveBallFirstCollidedPos.y > 0) return true;
    }
    return false;
}


// 尝试运动小球任务完成处理事项
function doTryMoveBallFinished() {
    if (!tryMoveBall) return;
    tryMoveBall.vx = 0;
    tryMoveBall.vy = 0;
}


// 计算圆碰撞/获取两小球碰撞点坐标
function calculateCircleCollision(ball0, ball1) {
    const movingCircle = {
        x: roundNumber(ball0.x, 4),
        y: roundNumber(ball0.y, 4),
        radius: roundNumber(ball0.radius, 4) // 注意！有的角色瞄准半径和本体半径不一样，傀儡、游侠、花千机等
    };

    const staticCircle = {
        x: roundNumber(ball1.x, 4),
        y: roundNumber(ball1.y, 4),
        radius: roundNumber(ball1.radius, 4)
    };

    const velocity = {
        x: roundNumber(ball0.vx, 4),
        y: roundNumber(ball0.vy, 4),
    };

    // 计算圆心之间的距离向量
    const dx = staticCircle.x - movingCircle.x;
    const dy = staticCircle.y - movingCircle.y;
    const distance = Math.sqrt(dx * dx + dy * dy);

    // 如果圆心距离已经小于两圆半径之和，说明已经碰撞
    if (distance <= staticCircle.radius + movingCircle.radius) {
        // 可以尝试回退到刚好碰撞点位置
        return null;
    }

    // 计算速度向量长度
    const speed = Math.sqrt(velocity.x * velocity.x + velocity.y * velocity.y);

    // 如果速度为0，则不会发生碰撞
    if (speed === 0) {
        return null;
    }

    // 计算速度向量的单位向量
    const unitVelocity = {
        x: velocity.x / speed,
        y: velocity.y / speed
    };

    // 计算圆心连线在速度方向上的投影长度
    const projection = dx * unitVelocity.x + dy * unitVelocity.y;

    // 如果投影为负，移动圆正在远离静止圆，不会发生碰撞
    if (projection < 0) {
        return null;
    }

    // 计算圆心连线的垂直分量长度
    const perpendicular = Math.sqrt(distance * distance - projection * projection);

    // 如果垂直距离大于两圆半径之和，则不会发生碰撞
    if (perpendicular > staticCircle.radius + movingCircle.radius) {
        //collisionResult.textContent = "移动圆不会与静止圆碰撞，它们会错过彼此。";
        //collisionPoint.textContent = `垂直距离: ${perpendicular.toFixed(2)}，最小距离: ${staticCircle.radius + movingCircle.radius}`;
        return null;
    }

    // 计算碰撞点沿速度方向的距离
    const approach = projection - Math.sqrt(Math.pow(staticCircle.radius + movingCircle.radius, 2) - perpendicular * perpendicular);

    // 如果approach为负，表示移动圆已经越过了碰撞点
    if (approach < 0) {
        return null;
    }

    // 计算碰撞点的坐标
    const collisionX = roundNumber(movingCircle.x + unitVelocity.x * approach, 4);
    const collisionY = roundNumber(movingCircle.y + unitVelocity.y * approach, 4);

    // 返回碰撞点坐标
    return { x: collisionX, y: collisionY };

    /*
    // 计算碰撞时间
    const timeToCollision = approach / speed;
    
    // 计算碰撞时移动圆的位置
    const movingCircleAtCollision = {
        x: movingCircle.x + velocity.x * timeToCollision,
        y: movingCircle.y + velocity.y * timeToCollision
    };
    */

    // 显示结果
    //collisionResult.textContent = `将会发生碰撞！碰撞时间: ${timeToCollision.toFixed(2)} 单位时间后`;
    //collisionPoint.textContent = `碰撞点坐标: (${collisionX.toFixed(2)}, ${collisionY.toFixed(2)})，移动圆圆心位置: (${movingCircleAtCollision.x.toFixed(2)}, ${movingCircleAtCollision.y.toFixed(2)})`;
}


// 记录碰撞点坐标
function recordCollidedPoint(ball) {
    //console.log(">>>> recordCollidedPoint ball: " + JSON.stringify(ball));
    if (!tryMoveBallCollidedPoints) tryMoveBallCollidedPoints = [];
    // 不能穿透的角色，只记录第一个撞击点坐标
    if (!isRoleCanPierces() && tryMoveBallCollidedPoints.length > 0) tryMoveBallCollidedPoints = [];
    if (tryMoveBallCollidedPoints.length === 0) {
        tryMoveBallFirstCollidedPos.x = ball.x;
        tryMoveBallFirstCollidedPos.y = ball.y;
        tryMoveBallCollidedPoints[0] = tryMoveBallFirstCollidedPos;
        // 备份第一次碰撞点坐标
        tryMoveBallFirstCollidedPosBack.x = tryMoveBallFirstCollidedPos.x;
        tryMoveBallFirstCollidedPosBack.y = tryMoveBallFirstCollidedPos.y;
    } else {
        tryMoveBallCollidedPoints.push({ x: ball.x, y: ball.y });
    }
    console.log(">>>> recordCollidedPoint 记录撞击点[" + tryMoveBallCollidedPoints.length + "]坐标：x=" + ball.x + ", y=" + ball.y);
    return true;
}


// 主角色运动完成后，要处理的事情
// function doAfterBallStopped(balls) {}
function doAfterBallStopped(balls) {
    if (!balls || balls.length < 1) return;
    for (let i = 0, len = balls.length; i < len; i++) {
        console.log('>>>> doAfterBallStopped ' + balls[i].getBallDesc());
        // 傀儡打完后
        if (userConfig.currRole === Role.KUILEI.id && balls[i].roleId === Role.KUILEI.id && balls[i].isMainBall)
            doKuilei(balls[i]);
    }

    // 双子打完后
    if (userConfig.currRole === Role.SHUANGZI.id) afterTwins(selectedBall ? false : true);

    // 猴子本体打完后
    if (userConfig.currRole === Role.WUKONG.id) afterMonkeys();

    // 重置角色字段属性值，主要是碰撞次数清零
    resetRoleField();

    // 运动结束，遮罩层调到最下，避免挡住拖动 【放最后】
    changeCanvasIndex(gameMaskCanvas, -2);

    // 重置超时计时器
    autoStopTimer && clearTimeout(autoStopTimer);
    //console.log(">>>> autoStopTimer:", autoStopTimer);
    autoStopTimer = null;
}


// 调整指定图层z-index
function changeCanvasIndex(target, idx) {
    target.style.zIndex = idx;
}


// TODO 开打后，超时自动停止，防止程序异常，导致高耗电！
// 在 doAfterBallStopped、resetBallsSpeed 等游戏结束的地方，也要清理重置定时器
var autoStopTimer;
function autoStopTimeout(sec) {
    let sTime = new Date().getTime();
    autoStopTimer && clearTimeout(autoStopTimer);
    if (!sec) sec = userConfig.animateAutoRestTime;
    if (!sec) sec = 20;
    autoStopTimer = setTimeout(() => {
        resetBallsSpeed(balls);
        let eTime = new Date().getTime();
        let runTime = Math.round((eTime - sTime) / 1000);
        console.log('>>>> autoStopTimeout: ' + runTime);
        alert('👉 本回合运行了 ' + runTime + ' 秒，已超时自动结束。');
    }, sec * 1000);
}


// 处理傀儡打完后业务逻辑
function doKuilei(ball) {
    if (!ball || userConfig.currRole !== Role.KUILEI.id || !ball.isMainBall || ball.roleId !== Role.KUILEI.id || ball.wallCollidedCount < 2) return;
    if (isKuileiPulling) { // 傀儡拉回之前已经还原过一次了，拉回打完直接重置状态返回就行
        // 重置拉回状态
        isKuileiPulling = false;
        return;
    }
    // 还原 tryMoveBall
    preTryMoveBall(0);
    // 坐标回到起点
    setBallPosToBeginPoint(ball);
    //globalParams.composite = "source-over";
    //ball.drawIcon(globalParams);
    //ball.drawRoleBloodLine(globalParams);
    //ball.drawCurrentCircle();
}


// 处理傀儡打完后拉回业务逻辑
function doKuileiPullBack(ball) {
    if (!ball || userConfig.currRole !== Role.KUILEI.id || !ball.isMainBall
        || ball.roleId !== Role.KUILEI.id || ball.wallCollidedCount < 2
        || !userConfig.isKuileiPullBack || isKuileiPulling
        || ball.roleCollidedCount < 1) return;
    // 清空路径层画布 这里会导致傀儡主球画面闪动一下，因为主球原始位置画在路径层
    // 先在主球层画一次当前位置
    ball.draw();
    doClearPathCanvas();
    // 傀儡先停止运动
    ball.vx = 0;
    ball.vy = 0;
    // 傀儡绳子复位
    doKuilei(ball);
    // 设置角色拉回速度
    getPullBackSpeed();
    // 重置角色字段属性值
    //resetRoleField();
    // 重置各个小球的碰撞标志位
    //setBallCollidingNos();
    // 设置傀儡拉回标志
    isKuileiPulling = true;
}


// 设置小球位置到原始起点
function setBallPosToBeginPoint(ball) {
    ball.x = ball.x0;
    ball.y = ball.y0;
    // TODO 手动产生一个很小的变动(要确保roundNumber能改变数值)，坐标一样会导致主球路径在拉回时清理不掉
    ball.x0 -= 0.0005;
}


// 根据鼠标与小球连线角度，获取vx、vy
function getVxVy(p1, p2, v, ball) {
    if (!ball) return { vx: 0, vy: 0 };
    let targetBall = ball;
    //if (!targetBall) targetBall = balls[0];
    // 获取两点连线与X轴的夹角 1-近点；2-远点
    let angle = getAngleX({
        x: p1 ? p1.x : targetBall.x,
        y: p1 ? p1.y : targetBall.y
    }, {
        x: p2 ? p2.x : mouse.x,
        y: p2 ? p2.y : mouse.y
    });
    //console.log('>>>> angleX=' + angle);
    // 主角A、撞击点B、触摸点C，计算AB、AC的夹角
    let angleV = getAngleV(targetBall, tryMoveBallFirstCollidedPosBack, mouse);
    // 点按操作模式
    //clickOffset.x = 0; clickOffset.y = 0;
    if (userConfig.currPlayOpt === 1 && (!isDragging || angleV < 135))
        angle = getAngleX({
            x: p1 ? p1.x : (mouse.x - clickOffset.x),
            y: p1 ? p1.y : (mouse.y - clickOffset.y)
        }, {
            x: p2 ? p2.x : targetBall.x,
            y: p2 ? p2.y : targetBall.y
        });
    //console.log('>>>> angle=' + angle);

    // 已知角度、速度v，求 vx vy
    let radians = angle * Math.PI / 180;
    let vx = Math.cos(radians) * (v ? v : targetBall.v);
    let vy = Math.sin(radians) * (v ? v : targetBall.v);
    //console.log('>>>> vx=' + vx + '; vy=' + vy);

    // TODO 运动方向取反，模拟玩吧撞击王者
    if (ball) {
        ball.vx = -vx;
        ball.vy = -vy;
    }

    vx = roundNumber(vx, 4);
    vy = roundNumber(vy, 4);

    return { vx: -vx, vy: -vy };
}


// 显示轨迹提示
function showMovePath() {
    if (!selectedBall || !tryMoveBallCollidedPoints || tryMoveBallCollidedPoints.length < 1) return;
    let collidedPoint, p1, p2;
    for (let i = 0, len = tryMoveBallCollidedPoints.length; i < len; i++) {
        collidedPoint = tryMoveBallCollidedPoints[i];
        if (!collidedPoint) continue;
        if (collidedPoint.x <= 0 || collidedPoint.y <= 0) continue;
        // 第一个碰撞点
        if (i === 0) p1 = { x: selectedBall.x, y: selectedBall.y }; // 球位置
        else p1 = { x: tryMoveBallCollidedPoints[i - 1].x, y: tryMoveBallCollidedPoints[i - 1].y };
        p2 = { x: tryMoveBallCollidedPoints[i].x, y: tryMoveBallCollidedPoints[i].y }; // 碰撞点坐标
        drawLine2Point(p1, p2);
    }
}


// 绘制瞄准路径、瞄准圈，小球中心点与碰撞点连线
// 获取了第一个碰撞点，就不用反向，直接连接球位置与第一个撞击点位置即可
function drawLine2Point(p1, p2) {
    if (!selectedBall || !selectedBall.isMainBall) return; // 非主球不画
    let context = selectedBall.context;
    context.save();
    context.beginPath();
    context.globalCompositeOperation = "destination-over";
    context.moveTo(p1.x, p1.y); // 起始位置
    context.lineTo(p2.x, p2.y); // 结束位置
    context.strokeStyle = currTheme.rlColor;
    context.lineWidth = selectedBall.radius * 2;
    if (selectedBall.isMainBall && selectedBall.roleId === Role.KUILEI.id) context.lineWidth = selectedBall.tryRadius * 2;
    context.lineCap = "round"; // 圆角
    //context.closePath(); // 闭合路径后是矩形
    context.stroke();
    context.restore();
    // 瞄准碰撞点画虚线圈
    context.save();
    context.beginPath();
    context.arc(p2.x, p2.y, selectedBall.tryRadius, Math.PI / 180 * 0, Math.PI / 180 * 360);
    context.lineWidth = currTheme.ccWidth;
    let tcColor = Theme.getColorCodeNormal(currTheme.plColor) + "A0";
    context.strokeStyle = Theme.isColorCode(tcColor) ? tcColor : "#F9FBF5A0";
    context.setLineDash([Math.round(6 * dpr * sysConfig.pxRatio), Math.round(3 * dpr * sysConfig.pxRatio)]);
    if (selectedBall.isMainBall && selectedBall.roleId === Role.KUILEI.id) context.setLineDash([Math.round(2 * dpr * sysConfig.pxRatio), Math.round(2 * dpr * sysConfig.pxRatio)]);
    context.closePath();
    context.stroke(); // 空心
    context.restore();
    // 起点被直线覆盖了，重画一次
    //selectedBall.draw();
}


// 获取两点连线与X轴的夹角 1-近点；2-远点
const getAngleX = ({ x: x1, y: y1 }, { x: x2, y: y2 }) => {
    let angle = Math.atan2(y2 - y1, x2 - x1) * 180 / (Math.PI);
    //angle = angle < 0 ? angle + 360 : angle;
    return angle;
}
// 获取两点连线与Y轴的夹角 1-近点；2-远点
const getAngleY = ({ x: x1, y: y1 }, { x: x2, y: y2 }) => {
    let angle = Math.atan2(x2 - x1, y2 - y1) * 180 / (Math.PI);
    angle = angle < 0 ? angle + 360 : angle;
    return angle;
}

// 线段AB、AC相交于A，求两线段的夹角
function getAngleV(A, B, C) {
    // 计算向量AB和AC
    let AB = { x: B.x - A.x, y: B.y - A.y };
    let AC = { x: C.x - A.x, y: C.y - A.y };

    // 计算向量的点积
    let dotProduct = AB.x * AC.x + AB.y * AC.y;

    // 计算向量的模
    let magnitudeAB = Math.sqrt(AB.x * AB.x + AB.y * AB.y);
    let magnitudeAC = Math.sqrt(AC.x * AC.x + AC.y * AC.y);

    // 计算夹角的余弦值
    let cosTheta = dotProduct / (magnitudeAB * magnitudeAC);

    // 计算夹角（弧度）
    let theta = Math.acos(cosTheta);

    // 将弧度转换为角度
    let angleInDegrees = theta * (180 / Math.PI);

    return angleInDegrees;
}

//////////////////////////////////////////////////////////////////////


//////////////////////////////////////////////////////////////////////
// 【点击、拖动监听事件】 变量、方法区域
//////////////////////////////////////////////////////////////////////
// 长按定时器
var longPressTimer = 0;
// 长按坐标
var longPressPoint = { x: 0, y: 0 };
// 小球拖动前的坐标
var oldBallPos = { x: 0, y: 0 };
// 点按模式触摸点与上一个碰撞点的偏移量
var clickOffset = { x: 0, y: 0 };
// 鼠标按下并拖动
var isMouseMoving = false;
// 是否正在拖动
var isDragging = false;
// 记录触摸开始的时间和位置
var touchStartTime = 0;
var touchStartX = 0;
var touchStartY = 0;
// 移动端开始触摸事件
var currTouchPointNum = 0;


// 事件顺序：touchstart-touchmove-touchend-mousedown-mouseup-click
// mousedown事件触发时绑定mousemove、mouseup事件，mouseup事件触发时，解除mousemove、mouseup事件
onMounted(() => {
    if (os.isPc) canvas.addEventListener('mousedown', (e) => {

        if (userConfig.currPlayOpt !== 1 && isMoving) return; // 处于移动或运动状态
        touchStartTime = Date.now(); // 记录触摸开始时间
        touchStartX = mouse.x; // 记录触摸开始位置的 X 坐标
        touchStartY = mouse.y; // 记录触摸开始位置的 Y 坐标
        //isDragging = true;
        // 计算触摸点与端点 B 的偏移量
        if (tryMoveBallFirstCollidedPosBack.x <= 0 && tryMoveBallFirstCollidedPosBack.y <= 0) {
            clickOffset.x = 0;
            clickOffset.y = 0;
        } else {
            clickOffset.x = mouse.x - tryMoveBallFirstCollidedPosBack.x;
            clickOffset.y = mouse.y - tryMoveBallFirstCollidedPosBack.y;
        }

        doEventDefault(e); // 处理事件默认行为

        //balls.some(ball => {
        // 添加事件来模拟拖拽
        // 注意，移除和添加的函数名必须一模一样，不能带参数，否则不能正常移除
        canvas.removeEventListener('mousemove', onMouseOrTouchMove, false);
        canvas.addEventListener('mousemove', onMouseOrTouchMove, false);
        canvas.removeEventListener('mouseup', onMouseUp, false);
        canvas.addEventListener('mouseup', onMouseUp, false);
        //return true;
        //});

        // 鼠标左键按下，设置长按定时器
        longPressTimer && clearTimeout(longPressTimer);
        longPressTimer = setTimeout(() => { doLongPress(e) }, 500);

    }, false);


    if (!os.isPc) canvas.addEventListener('touchstart', (e) => {
        //isDragging = true;
        //const touch = e.touches[0]; // 获取第一个触摸点
        getClickPos(e);
        touchStartTime = Date.now(); // 记录触摸开始时间
        touchStartX = mouse.x; // 记录触摸开始位置的 X 坐标
        touchStartY = mouse.y; // 记录触摸开始位置的 Y 坐标
        // 计算触摸点与端点 B 的偏移量
        if (tryMoveBallFirstCollidedPosBack.x <= 0 && tryMoveBallFirstCollidedPosBack.y <= 0) {
            clickOffset.x = 0;
            clickOffset.y = 0;
        } else {
            clickOffset.x = mouse.x - tryMoveBallFirstCollidedPosBack.x;
            clickOffset.y = mouse.y - tryMoveBallFirstCollidedPosBack.y;
        }
        doEventDefault(e);
        currTouchPointNum = e.touches.length;
        // 目前只支持单点触碰
        if (currTouchPointNum !== 1) return;
        // 触摸开始，设置长按定时器
        longPressPoint.x = mouse.x;
        longPressPoint.y = mouse.y;
        longPressTimer && clearTimeout(longPressTimer);
        longPressTimer = setTimeout(() => { doLongPress(e) }, 500);
    }, false);


    // 砖格坐标画布开始触摸事件
    if (!os.isPc) gameSceneCoordinateCanvas.addEventListener('touchstart', (e) => {
        //console.log(e);
        doEventDefault(e);
        currTouchPointNum = e.touches.length;
        // 目前只支持单点触碰
        if (currTouchPointNum !== 1) return;
        //getClickPos(e);

    }, false);
})


// 拖拽移动业务处理
function onMouseMove(isPlay2) {

    // 如果是导入，标记移动完成
    if (userConfig.shareRoleAndPos) {
        selectMainBall(); // 选中主球
        selectedBall.isChgPosFinished = true; // 标记移动完成
        setBallsPosBack(false); // 还原原始位置坐标
        clearShareRoleAndPos(); // 清除导入数据
    }

    if (!selectedBall) return;
    console.log(">>>> onMouseMove " + selectedBall.getBallDesc());

    // 标记鼠标正在拖动
    isMouseMoving = true;
    // 双击不算拖动
    if (isPlay2) isMouseMoving = false;

    // 标记游戏开始
    sysConfig.isGameBeginning = true;

    // 拖动时清空了画布，需要重新渲染界面
    isAnimated = false;
    if (!isPlaying) animate(); // 动画渲染后，isAnimated 标识为 true

    // 清空运动层画布
    //doClearMoveCanvas();
    // 清空路径层画布
    doClearPathCanvas();

    // 重置之前找到的撞击点坐标【必须放这】
    tryMoveBallFirstCollidedPos.x = 0;
    tryMoveBallFirstCollidedPos.y = 0;
    tryMoveBallCollidedPoints = [];

    // 双击重打进来的，不处理拖动
    //if (isPlay2 || !isMouseMoving) return;

    //console.log(">>>> onMouseMove isChgPosFinished=" + selectedBall.isChgPosFinished);
    if (!selectedBall.isChgPosFinished) { // 还在拖动
        //console.log(">>>> onMouseMove mouse.x=" + mouse.x + ", mouse.y=" + mouse.y);
        if (!isPlay2) {
            selectedBall.x = mouse.x;
            selectedBall.y = mouse.y;
        }
        //selectedBall.x0 = mouse.x;
        //selectedBall.y0 = mouse.y;

        // 双子分身位置处理
        afterTwins(false);

        // 小球碰撞检测，放最前面，避免小球位置超出墙面边界
        checkOtherBallCollided(selectedBall, true);
        // 四面墙检测
        checkWallCollided(selectedBall, true);
        // 四个切面检测
        checkLineCollided(selectedBall, true);
        // 蛋切面碰撞检测
        if (isDuoduoExist) checkEggCollided(selectedBall, true);

        //console.log(">>>> onMouseMove selectedBall.x=" + selectedBall.x + ", selectedBall.y=" + selectedBall.y);

        // 坐标提示跟随显示
        setRolePosLineFollowing(selectedBall, true);

        // 短时间误碰，重新渲染
        isAnimated = false;
        if (!isPlaying) animate();
        // 清空路径层画布
        doClearPathCanvas();

    } else { // 拖动完成，动态显示小球运动方向
        // 坐标提示跟随关闭
        setRolePosLineFollowing(selectedBall, false);

        // 获取小球分速度 vx、vy
        if (isRoleCanPierces()) { // 能穿透的角色，速度设置大一些，加快拿到前5个碰撞点，减少延迟
            tryMoveBall.v = 200; // 再往上快可能会出现路径不准
            getVxVy(null, null, tryMoveBall.v, selectedBall);
        } else { // 其他角色
            getVxVy(null, null, null, selectedBall);
        }
        // 更新移动的球
        tryMoveBall.x = roundNumber(selectedBall.x, 4);
        tryMoveBall.y = roundNumber(selectedBall.y, 4);
        //tryMoveBall.x0 = tryMoveBall.x;
        //tryMoveBall.y0 = tryMoveBall.y;
        tryMoveBall.vx = roundNumber(selectedBall.vx, 4);
        tryMoveBall.vy = roundNumber(selectedBall.vy, 4);
        // 准备 tryMoveBall
        preTryMoveBall(1);
        // 尝试模拟运动找到第一个撞击点
        doTryMoveBallFirstCollidedPos();
    }
}


// 角色坐标提示跟随角色移动
let rolePosXEle, rolePosYEle, rolePosLineTimer;
function setRolePosLineFollowing(ball, isShow) {
    if (!userConfig.isShowRoleMovePos) return;
    //if (!ball) return;

    // 清理定时器
    rolePosLineTimer && clearTimeout(rolePosLineTimer);

    let girdCount = 2.5;
    if (userConfig.isShowRoleBloodLine) girdCount = 3.2;
    //rolePosLine.style.left = (screenPos.x - rolePosLine.getBoundingClientRect().width / 2).toFixed(2) + "px";
    //rolePosLine.style.top = (screenPos.y - sysConfig.girdSizeCss * girdCount).toFixed(2) + "px";
    rolePosLine.style.left = (ball.x / dpr + sysConfig.cLeft - rolePosLine.getBoundingClientRect().width / 2).toFixed(2) + "px";
    rolePosLine.style.top = (ball.y / dpr + sysConfig.cTop - sysConfig.girdSizeCss * girdCount).toFixed(2) + "px";

    if (!rolePosXEle) rolePosXEle = document.getElementById("rolePosX");
    if (!rolePosYEle) rolePosYEle = document.getElementById("rolePosY");
    let pos = { x: ball.x, y: ball.y };
    switchPxOrGird(pos, 0);
    //switchPxOrGird(pos, 1);
    rolePosXEle.innerText = pos.x.toFixed(2);
    rolePosYEle.innerText = pos.y.toFixed(2);

    if (isShow) rolePosLine.style.display = "unset";
    else rolePosLine.style.display = "none";
}


// 坐标换算
function switchPxOrGird(p, no) {
    switch (no) {
        case 1: // gird to px
            // x
            if (p.x >= 0) {
                p.x += 7;
            } else {
                p.x = 7 + p.x;
            }
            //y
            if (p.y >= 0) {
                p.y = 11 - p.y;
            } else {
                p.y = 11 - p.y;
            }

            p.x = roundNumber(p.x * sysConfig.girdSize, 2);
            p.y = roundNumber(p.y * sysConfig.girdSize, 2);
            break;
        default: // px to gird
            p.x = roundNumber((p.x / sysConfig.girdSize - 7), 2);
            p.y = roundNumber(((p.y / sysConfig.girdSize - 11) * -1), 2);
    }
}


function onMouseUp(e) {
    //console.log(e);
    isDragging = false;
    // PC 端移动完成后模拟一次点击
    doClick(e);
    // 鼠标左键抬起，重置长按定时器
    longPressTimer && clearTimeout(longPressTimer);
    longPressTimer = 0;
    // 清除事件
    canvas.removeEventListener('mousemove', onMouseOrTouchMove, false);
    canvas.removeEventListener('mouseup', onMouseUp, false);
}


function onMouseOrTouchMove(e) {
    //console.log(e);
    isDragging = true;
    doEventDefault(e);
    // 解决部分机型，手指没有move，touchmove事件仍会被调用的问题
    // 太精确的全等会导致触摸稍微抖动一下就会重置定时器，导致长按不灵敏
    //if (longPressPoint.x !== mouse.x || longPressPoint.y !== mouse.y) {
    // 允许手指有半径为10像素的范围抖动
    if (!is2CirclesCollided({ x: longPressPoint.x, y: longPressPoint.y, radius: 10 }, { x: mouse.x, y: mouse.y, radius: 10 })) {
        // 有拖动行为，重置长按定时器
        longPressTimer && clearTimeout(longPressTimer);
        longPressTimer = 0;
    }
    selectBall();
    onMouseMove();
}


function onTouchEnd() {
    isDragging = false;
    // 清除事件
    canvas.removeEventListener('touchmove', onMouseOrTouchMove, false);
    canvas.removeEventListener('touchend', onTouchEnd, false);
}

// 选中小球
function selectBall(pos) {
    if (selectedBall) return;
    balls.some(ball => {
        if (isBallSelected(ball, pos)) {
            selectedBall = ball;
            oldBallPos.x = ball.x;
            oldBallPos.y = ball.y;
            return true;
        }
    });
}


// 移动端拖动事件
// touchstart --> mousedown 手指在元素按下
// touchmove --> mousemove 手指在元素按下之后，在屏幕中移动
// touchend --> mouseup 手指在元素按下之后，在屏幕中抬起
onMounted(() => {
    if (!os.isPc) canvas.addEventListener('touchmove', (e) => {
        if (currTouchPointNum !== 1) return;
        onMouseOrTouchMove(e);
    }, false);
})


onMounted(() => {
    // 单击开始往指定方向运动
    // 事件顺序 mousedown、mouseup、click，前一个事件执行完毕才会执行下一个事件
    if (os.isPc) canvas.addEventListener('click', (e) => {
        doEventDefault(e);
        getClickPos(e);
        const touchEndX = mouse.x; // 触摸结束位置的 X 坐标
        const touchEndY = mouse.y; // 触摸结束位置的 Y 坐标
        const touchEndTime = Date.now(); // 记录触摸结束时间

        // 计算触摸移动的距离
        const deltaX = touchEndX - touchStartX;
        const deltaY = touchEndY - touchStartY;
        const distance = Math.sqrt(deltaX * deltaX + deltaY * deltaY);

        // 计算触摸持续时间
        const duration = touchEndTime - touchStartTime;

        // 判断是否为单击事件
        if (duration < 300 && distance < 10) { // 300ms 内且移动距离小于 10px
            //alert("PC Click"); // PC 端移动结束时会出发点击事件
            doClick(e, true);
        }

    }, false);

    // 双击允许拖动小球位置
    if (os.isPc) canvas.addEventListener('dblclick', (e) => {
        doEventDefault(e);
        doDbClick(e);

    }, false);

    // 砖格坐标层点击事件，点击坐标，切换长短显示
    if (os.isPc) gameSceneCoordinateCanvas.addEventListener('click', (e) => {
        doEventDefault(e);
        // 切换完全坐标
        //getClickPos(e);
    }, false);

    // 点按发射按钮点击监听
    if (os.isPc) gameClickPlayCanvas.addEventListener('click', (e) => {
        doEventDefault(e);
        // 发射处理
        doClickPlay(e);
    }, false);

    // 砖格坐标双击切换显示
    if (os.isPc) gameSceneCoordinateCanvas.addEventListener('dblclick', (e) => {
        doEventDefault(e);
        // 切换完全坐标
        let p = getClickPos(e);
        if (isInGirdNumArea(p)) {
            userConfig.isShowGridCoordinateFull = !userConfig.isShowGridCoordinateFull;
            switchCanvasShow(gameSceneCoordinateCanvas, true);
            localStorage.setItem('collide-try-user-settings', JSON.stringify(userConfig));
        }
    }, false);

    // 单击遮罩层关闭最上层弹窗监听事件
    if (os.isPc) dialogMask.addEventListener('click', (e) => {
        doEventDefault(e);
        doCloseTopDialog(e);
    }, false);
})


// 移动端单、双击事件
onMounted(() => {
    let lastTouchEnd = 0;
    if (!os.isPc) canvas.addEventListener('touchend', (e) => {
        //console.log(e);
        //alert(e.touches.length);
        isDragging = false;
        doEventDefault(e);
        //if (e.type !== "touchend" && e.touches.length !== 0) return;
        if (currTouchPointNum !== 1) return;
        // 触摸结束，重置长按定时器
        longPressTimer && clearTimeout(longPressTimer);
        longPressTimer = 0;

        //const touch = e.changedTouches[0]; // 获取第一个触摸点
        //const touchEndX = touch.clientX; // 触摸结束位置的 X 坐标
        //const touchEndY = touch.clientY; // 触摸结束位置的 Y 坐标
        //const touchEndTime = Date.now(); // 记录触摸结束时间
        //getClickPos(e);
        const touchEndX = mouse.x; // 触摸结束位置的 X 坐标
        const touchEndY = mouse.y; // 触摸结束位置的 Y 坐标
        const touchEndTime = Date.now(); // 记录触摸结束时间

        // 计算触摸移动的距离
        const deltaX = touchEndX - touchStartX;
        const deltaY = touchEndY - touchStartY;
        const distance = Math.sqrt(deltaX * deltaX + deltaY * deltaY);

        // 计算触摸持续时间
        const duration = touchEndTime - touchStartTime;

        // 判断是否为单击事件
        let isClicked = false;
        if (duration < 300 && distance < 10) { // 300ms 内且移动距离小于 10px
            //alert(">>>> 单击了"); // TODO 双击会触发两次单击
            isClicked = true;
            doClick(e, true);
        }

        if (touchEndTime - lastTouchEnd <= 300) { // 200~300
            //alert(">>>> 双击了");
            doDbClick(e);
        } else {
            //alert(">>>> 鼠标抬起触发单击了");
            if (!isClicked) doClick(e);
        }
        lastTouchEnd = touchEndTime;
    }, false);


    // 移动端点按发射按钮点击监听
    var lastTouchEndClickBtn = 0;
    if (!os.isPc) gameClickPlayCanvas.addEventListener('touchend', (e) => {
        doEventDefault(e);
        let now = (new Date()).getTime();
        if (now - lastTouchEndClickBtn <= 300) { // 200~300
            //alert(">>>> 双击了");
            //doDbClick(e);
        } else {
            //alert(">>>> 单击了");
            // 发射处理
            doClickPlay(e);
        }
        lastTouchEndClickBtn = now;
    }, false);


    // 砖格坐标层点击事件，点击坐标，切换长短显示
    if (!os.isPc) gameSceneCoordinateCanvas.addEventListener('touchend', (e) => {
        //console.log(e);
        //alert(e.touches.length);
        doEventDefault(e);
        if (currTouchPointNum !== 1) return;

        let now = (new Date()).getTime();
        if (now - lastTouchEnd <= 300) { // 200~300
            //alert(">>>> 双击了");
            // 切换完全坐标
            let p = getClickPos(e);
            if (isInGirdNumArea(p)) {
                userConfig.isShowGridCoordinateFull = !userConfig.isShowGridCoordinateFull;
                switchCanvasShow(gameSceneCoordinateCanvas, true);
                localStorage.setItem('collide-try-user-settings', JSON.stringify(userConfig));
            }
        } else {
            //alert(">>>> 单击了");
        }
        lastTouchEnd = now; // 共用一个事件标志会导致判断错乱问题，目前业务不多，没有冲突，先这样
    }, false);


    // 单击遮罩层关闭最上层弹窗监听事件
    if (!os.isPc) dialogMask.addEventListener('touchend', (e) => {
        doEventDefault(e);
        let now = (new Date()).getTime();
        if (now - lastTouchEnd <= 300) { // 200~300
            //alert(">>>> 双击了");
        } else {
            //alert(">>>> 单击了");
            doCloseTopDialog(e);
        }
        lastTouchEnd = now;
    }, false);
})


// 点按发射按钮点击
function doClickPlay(e) {
    if (!selectedBall) return; // 没用选中球
    if (selectedBall.vx === 0 && selectedBall.vy === 0) return; // 没有拖动完成时，没有速度
    // 点击范围判断，不同的画布坐标系不一致
    //if (!is2CirclesCollided(ball0, ball1)) return;
    clickPlayBtn.isReady = true;
    doClick(e);
}


// 关闭最上层弹窗
function doCloseTopDialog(e) {
    doBack(true);
}


// 单击后处理逻辑
function doClick(e, isClick) {

    // 三连击计数
    //preTripleClick(e);
    // 鼠标或手指抬起，标记鼠标没有在拖动
    isMouseMoving = false;

    if (!selectedBall) return; // 没用选中球
    if (userConfig.isJustShowTable) return; // 只显示台面，不处理点击事件
    // 点按模式点击时模拟拖动
    if (isClick && userConfig.currPlayOpt === 1 && !clickPlayBtn.isReady) {
        // 点击调整位置时，偏移归零
        clickOffset.x = 0; clickOffset.y = 0;
        // 模拟一次移动
        onMouseMove();
        // 需重新渲染
        isAnimated = false;
        if (!isPlaying) animate();
    }

    //console.log(">>>> isChgPosFinished=" + selectedBall.isChgPosFinished);
    //if (selectedBall) console.log(">>>> isBallReady=" + isBallReady(selectedBall));
    if (selectedBall.isChgPosFinished && isBallReady(selectedBall)) {
        console.log(">>>> doClick is readying >>>>");
        // 重置拖动标识
        selectedBall.isChgPosFinished = false;
        //if (userConfig.isJustTrying) return; // 只瞄准不打
        // 设置起点
        //selectedBall.x0 = selectedBall.x;
        //selectedBall.y0 = selectedBall.y;
        selectedBall.preCollided = { x: selectedBall.x, y: selectedBall.y };
        selectedBall.prePoint = { x: selectedBall.x, y: selectedBall.y };
        // 更新主球移动位置坐标
        oldBallPos.x = selectedBall.x;
        oldBallPos.y = selectedBall.y;
        // 备份原始位置坐标
        setBallsPosBack(true);
        // 初始化双子分身，只瞄准不打不设置
        if (selectedBall.isMainBall && selectedBall.roleId === Role.SHUANGZI.id && !userConfig.isJustTrying) doTwins(selectedBall);
        // 猴子分身
        if (selectedBall.isMainBall && selectedBall.roleId === Role.WUKONG.id && !userConfig.isJustTrying) preMonkeys();
        // 重置角色字段属性值
        resetRoleField();
        // 瞄准松手开打之前，再次更新速度，避免瞄准看到的跟实际打的方向因为手抖导致偏差
        if (tryMoveBallFirstCollidedPos.x > 0 && tryMoveBallFirstCollidedPos.y > 0)
            getVxVy(tryMoveBallFirstCollidedPos, { x: selectedBall.x, y: selectedBall.y }, null, selectedBall);
        // 傀儡绳子因为没有加受摩擦力，速度需要降一点，不然看着太快
        /*
        if (selectedBall.isMainBall && selectedBall.roleId === Role.KUILEI.id && !isKuileiPulling) {
            selectedBall.vx *= Ball.SPEEDRATIO.L;
            selectedBall.vy *= Ball.SPEEDRATIO.L;
        }
        */
        // 清空selectedBall后开始运动
        if (!userConfig.isJustTrying) {
            selectedBall.draw();
            selectedBall.update();
        }
        selectedBall = null;
        // 重置tryMoveBall
        resetTryMoveBall();
        // 重置是否找到第一次撞击点标识
        isFirstCollidedPointFounded = false;
        // 重新渲染
        if (!isPlaying) animate();
        // 开始运动，置顶遮罩，避免误碰
        changeCanvasIndex(gameMaskCanvas, 2);
        // 超时自动停止
        autoStopTimeout();
        // 重置各个小球的碰撞标志位
        setBallCollidingNos();
        // 重置傀儡拉回标志
        isKuileiPulling = false;
        // 只瞄准不打
        if (userConfig.isJustTrying) doJustTrying();
        // 点按发射标识重置
        clickPlayBtn.isReady = false;
        // 隐藏发射按钮
        if (userConfig.currPlayOpt === 1) gameClickPlayCanvas.style.display = "none";
        // 第一个碰撞点备份重置
        tryMoveBallFirstCollidedPosBack.x = 0; tryMoveBallFirstCollidedPosBack.y = 0;
    }

    // 判断球位置是否改动
    if (isBallMoved(selectedBall)) { // 拖动完成
        if (selectedBall.isMainBall) selectedBall.isChgPosFinished = true; // 主球才会有拖动完成，会发射，发射后才可以再次拖动
        if (!selectedBall.isMainBall) selectedBall = null; // 非主球拖动完成后，不发射，可以多次拖动
        // 自动隐藏坐标条
        rolePosLineTimer = setTimeout(() => { rolePosLine.style.display = 'none' }, 3000);
    }

    // 鼠标抬起的click事件，点按发射偏移坐标重置
    clickOffset.x = 0; clickOffset.y = 0;
    // 显示发射按钮
    if (userConfig.currPlayOpt === 1 && selectedBall && selectedBall.isChgPosFinished) gameClickPlayCanvas.style.display = "unset";
}


// 双击后处理逻辑【移动端双击还有点问题】
function doDbClick(e) {
    if (userConfig.isJustShowTable) return; // 只显示台面，不处理点击事件
    // 三连击计数
    //preTripleClick(e, true);
    // 双击主球，免拖动，直接开打
    directPlayAgain(true);
}


// 三连击，不用太快点【不稳定，会触发单击、双击的事件，导致功能混乱】
let tripleClick = 0;
let tripleClickTimer = 0;
function doTripleClick(e) {
    if (userConfig.isJustShowTable) return; // 只显示台面，不处理点击事件
    //alert(">>>> 三连击");
    // 所有角色重新设置随机位置
    putAllBallsRandom();
    // 重新渲染
    isAnimated = false;
    if (!isPlaying) animate();
}


// 三连击准备
function preTripleClick(e, isDbClick) {
    if (isDbClick) tripleClick += 2;
    else tripleClick += 1;
    if (tripleClick >= 4) { // TODO 目前双击事件会多出一次单击
        tripleClickTimer && clearTimeout(tripleClickTimer);
        tripleClick = 0;
        tripleClickTimer = 0;
        doTripleClick(e);
        return;
    }
    tripleClickTimer && clearTimeout(tripleClickTimer);
    tripleClickTimer = setTimeout(() => {
        tripleClickTimer && clearTimeout(tripleClickTimer);
        tripleClick = 0;
        tripleClickTimer = 0;
    }, 500);
}


// 长按处理
function doLongPress(e) {
    //console.log(e);
    if (!userConfig.isLongPressRandom) return;
    // 在瞄准阶段不能重置
    if (selectedBall && selectedBall.isChgPosFinished) return;
    // 移动端目前只支持单点触碰
    if (!os.isPc && currTouchPointNum !== 1) return;
    // 只显示台面，不处理点击事件
    if (userConfig.isJustShowTable) return;
    // 按角色不重置，只能按空白区域
    if (isBallsSelected(balls)) return;
    //alert(">>>> 长按");
    // 所有角色重新设置随机位置
    putAllBallsRandom();
    // 选中主球
    selectMainBall();
    // 还原tryMoveBall半径
    preTryMoveBall(0);
    // 重置tryMoveBall速度状态
    resetTryMoveBall();
    // 主球速度重置
    selectedBall.vx = 0;
    selectedBall.vy = 0;
    selectedBall.isMoving = false;
    // 标记主球未移动完成【这里必须放在onMouseMove之前】
    selectedBall.isChgPosFinished = false;
    // 模拟拖动，重新渲染改变位置后的画面
    onMouseMove(true);
    // 不选中主球
    selectedBall = null;
    // 阻断后续事件
    doEventDefault(e);
    // 角色坐标关闭
    rolePosLine.style.display = "none";
}


// 处理事件冒泡和默认行为
function doEventDefault(e) {
    e = e || window.event;
    if (!e) return;

    //console.log(">>>> doEventDefault ", e);
    // 打印调用堆栈
    //if (!isProd()) printStack();

    // 阻止事件冒泡，但不会阻止浏览器默认行为
    if (e.stopPropagation) { // 非IE
        e.stopPropagation();
    } else { // IE
        e.cacelBubble = true;
    }

    let ele = e.target;
    if (ele && ele.tagName && ele.tagName.toLowerCase() === "a") return; // a 链接
    if (ele && ele.tagName && ele.tagName.toLowerCase() === "input") return; // input file 选择

    // 阻止浏览器默认行为
    if (e.preventDefault) { // 非IE
        if (e.cancelable) e.preventDefault();
    } else { // IE
        e.returnValue = false;
    }
}


// 判断球位置是否改动
function isBallMoved(ball) {
    if (!ball) return false;
    if (ball.x != oldBallPos.x || ball.y != oldBallPos.y) {
        // 拖动完成
        return true;
    }
    return false;
}


// 小球是否准备就绪，vx、vy 不为零
function isBallReady(ball) {
    if (!ball) return false;
    if (userConfig.currPlayOpt === 1 && !clickPlayBtn.isReady) return false;
    if (ball.vx !== 0 || ball.vy !== 0) {
        // 速度准备就绪
        return true;
    }
    return false;
}


// 判断鼠标是否点击了小球
function isBallSelected(ball, pos) {
    // 通过鼠标位置到圆心的距离判断
    //console.log(">>>> mouse.x=" + mouse.x + ", mouse.y=" + mouse.y);
    //console.log(">>>> ball.x=" + ball.x + ", ball.y=" + ball.y);
    let d;
    if (pos) d = getDistanceOf2Points({ x: pos.x, y: pos.y }, { x: ball.x, y: ball.y });
    else d = getDistanceOf2Points({ x: mouse.x, y: mouse.y }, { x: ball.x, y: ball.y });
    //console.log(">>>> isBallSelected d=" + d);
    if (d <= ball.radius) return true;
    return false;
}


// 判断鼠标是否挨到了任意一个小球
function isBallsSelected(checkBalls, pos) {
    if (!checkBalls || checkBalls.length < 1) return false;
    let ball;
    for (let i = 0, len = checkBalls.length; i < len; i++) {
        ball = checkBalls[i];
        let d;
        if (pos) d = getDistanceOf2Points({ x: pos.x, y: pos.y }, { x: ball.x, y: ball.y });
        else d = getDistanceOf2Points({ x: mouse.x, y: mouse.y }, { x: ball.x, y: ball.y });
        //console.log(">>>> isBallSelected d=" + d);
        if (d <= ball.radius) return true;
    }
    return false;
}


// 选中主球，只支持一个主球
function selectMainBall() {
    let mainBall = balls[0];
    selectedBall = mainBall;
    //oldBallPos.x = mainBall.x;
    //oldBallPos.y = mainBall.y;
}


// 处理只瞄准不打事宜
function doJustTrying() {
    if (!userConfig.isJustTrying) return;
    if (!balls || balls.length < 1) return;
    let selectedBall = balls[0];
    selectedBall.vx = 0;
    selectedBall.vy = 0;
    // 还原 tryMoveBall
    preTryMoveBall(0);
    doAfterBallStopped(balls);
    // 手动偏移一点点位置坐标，好让角色重新渲染
    selectedBall.y -= 0.0000000001;
}


// 打完一次后，免拖动，【原位置】再次开打
function directPlayAgain(isChgPosFinished) {
    if (!userConfig.isDbclickBack) return;
    if (selectedBall && selectedBall.isChgPosFinished) return;
    if (checkIsMoving()) return; // 解决多点触碰，单击开打后又触发双击重置，导致无限循环
    // 获取点击坐标
    let pos = clickPos;
    // 是否点击了主球【移动端可能点不准】
    //if (!isBallSelected(balls[0], pos)) return;
    console.log(">>>> directPlayAgain >>>>");
    // 选中主球
    selectMainBall();
    // 还原原始位置坐标
    setBallsPosBack(false);
    // 模拟拖动
    onMouseMove(true);
    // 重画一次
    //selectedBall.draw();
    // 标记主球移动完成
    selectedBall.isChgPosFinished = isChgPosFinished;
    // 重新渲染
    //isAnimated = false;
    //if (!isPlaying) animate();
    // 角色坐标关闭
    rolePosLine.style.display = "none";
}


//////////////////////////////////////////////////////////////////////

</script>
