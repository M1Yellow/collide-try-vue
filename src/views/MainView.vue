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
    z-index: 1;
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
}

.in-one-line {
    display: flex;
    flex-wrap: nowrap;
    flex-direction: row;
    align-content: center;
    justify-content: center;
    align-items: stretch;
}

.each-item-border-bottom {
    width: 100%;
    display: inline-block;
    border-bottom: 1px solid #ddd;
    text-align: left;
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
    margin-top: -2px;
    /* 解决标题边框透明问题 */
    padding: 10px 10px 25px 10px;
    border-radius: 0 0 10px 10px;
}

.collide-try-close-btn-dialog-content pre {
    width: 100%;
    text-align: left;
    font-size: 16px;
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
}

#role-list-head-msg {
    padding: 3px 0 2px 0;
    font-size: 24px;
}

#role-list-head-desc {
    padding: 0 0 5px 0;
    font-size: 10px;
}

#role-list-head-setting-icon {
    width: 100%;
    position: absolute;
    font-size: 22px;
    top: 4px;
    left: -4px;
    text-align: right;
}

#role-list-head-setting-icon span {
    font-size: 22px;
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
    grid-template-columns: 46px 170px;
    grid-template-rows: 100%;
    align-content: center;
    justify-content: center;
    align-items: baseline;
    justify-items: stretch;
    padding-left: 10px;
}

.role-list-icon-name span {
    font-size: 20px;
}

.role-list-icon {
    text-align: center;
    vertical-align: middle;
}

.role-list-name {
    text-align: left;
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
    margin-right: 7px;
    z-index: 1002;
}

#role-shuangzi-2 {
    margin-left: 7px;
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
}

#user-setting-head-msg {
    padding: 5px 0 5px 0;
    font-size: 24px;
}

#user-setting-head-desc {
    padding: 0 0 3px 0;
    font-size: 10px;
}

#user-setting-close-icon {
    position: absolute;
    width: 100%;
    font-size: 18px;
    top: 6px;
    left: -6px;
    text-align: right;
}

#user-setting-close-icon span {
    font-size: 18px;
    cursor: pointer;
}

.user-setting-item {
    padding: 6px 10px;
    font-size: 18px;
    text-align: left;
}

.user-setting-item-msg-left {
    font-size: 16px;
}

.user-setting-item-switch-right button {
    font-size: 12px;
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
    top: 3px;
    vertical-align: middle;
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
    line-height: 2;
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
    width: 20px;
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
    -webkit-transition: .2s;
    transition: .2s;
}

.slider:before {
    position: absolute;
    content: "";
    height: 14px;
    width: 14px;
    left: 3px;
    bottom: 2px;
    background-color: white;
    -webkit-transition: .2s;
    transition: .2s;
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
            <!-- mask 运动遮罩层 -->
            <canvas id="game-mask" ref="gameMask" width="420" height="660"
                style="width: 420px; height: 660px;"><!-- 遮罩层，避免运动时操作小球，手动调整图层顺序 -->
                Canvas not supported
            </canvas>
        </div>
        <!-- 弹窗遮罩 -->
        <div id="dialog-mask" ref="dialogMask" class="collide-try-dialog"></div>
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
                <div id="role-list-head-setting-icon"><span @click="switchUserSettingDialog(true);">⚙️</span></div>
                <div id="role-list-head-desc">（重新打开页面/刷新即可再次选角色）</div>
            </div>
            <ul id="role-list-area">
                <li id="role-heiwa" class="role-list" @click="chooseRole($event.target, Role.HEIWA.id);">
                    <div class="role-list-icon-name"><span class="role-list-icon">🍼</span><span
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
                <li id="role-lele" class="role-list" @click="chooseRole($event.target, Role.LELE.id);">
                    <div class="role-list-icon-name"><span class="role-list-icon">🥙</span><span
                            class="role-list-name">太平乐（乐乐）</span></div>
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
                <div id="user-setting-head-desc"></div>
            </div>
            <ul id="user-setting-area">
                <li class="user-setting-item" id="user-setting-item-1st">
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
                <li class="user-setting-item">
                    <span class="user-setting-item-msg-left">主角所在队颜色</span>
                    <span class="user-setting-item-switch-right">
                        <button class="dropbtn red" @click="toggleTeamColor()" id="mainTeamColor">红色</button>
                    </span>
                </li>
                <li class="user-setting-item">
                    <span class="user-setting-item-msg-left">只用一个角色测试</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isTestOnlyOne');">
                            <input type="checkbox" id="isTestOnlyOne">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item">
                    <span class="user-setting-item-msg-left">显示角色运动路径</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isShowBallMovePath');">
                            <input type="checkbox" id="isShowBallMovePath">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item">
                    <span class="user-setting-item-msg-left">显示角色本体路径</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isShowBallPath');">
                            <input type="checkbox" id="isShowBallPath">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item">
                    <span class="user-setting-item-msg-left">只瞄准不打</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isJustTrying');">
                            <input type="checkbox" id="isJustTrying">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item">
                    <span class="user-setting-item-msg-left">碰到角色即停止</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isStopAfterCollided');">
                            <input type="checkbox" id="isStopAfterCollided">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item">
                    <span class="user-setting-item-msg-left">碰墙两次即停止</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isStopAfter2WallCollided');">
                            <input type="checkbox" id="isStopAfter2WallCollided">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item">
                    <span class="user-setting-item-msg-left">只显示撞击台面</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isJustShowTable');">
                            <input type="checkbox" id="isJustShowTable">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item">
                    <span class="user-setting-item-msg-left">显示场景图形</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isShowSceneGraph');">
                            <input type="checkbox" id="isShowSceneGraph">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item">
                    <span class="user-setting-item-msg-left">显示台面边框</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch"
                            @click="switchCheckbox($event, 'isShowTableBorder', { canvasEle: gameSceneLinesCanvas });">
                            <input type="checkbox" id="isShowTableBorder">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item">
                    <span class="user-setting-item-msg-left">显示砖格坐标</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch"
                            @click="switchCheckbox($event, 'isShowGridCoordinate', { canvasEle: gameSceneCoordinateCanvas });">
                            <input type="checkbox" id="isShowGridCoordinate">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item">
                    <span class="user-setting-item-msg-left">显示角色血量条</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isShowRoleBloodLine');">
                            <input type="checkbox" id="isShowRoleBloodLine">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item">
                    <span class="user-setting-item-msg-left">傀儡拉回</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isKuileiPullBack');">
                            <input type="checkbox" id="isKuileiPullBack">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item">
                    <span class="user-setting-item-msg-left">瞄准穿透</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isPiercesTry');">
                            <input type="checkbox" id="isPiercesTry">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item">
                    <span class="user-setting-item-msg-left">瞄准显示路径</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isShowTryFullPath');">
                            <input type="checkbox" id="isShowTryFullPath">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item">
                    <span class="user-setting-item-msg-left">双击屏幕回退</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isDbclickBack');">
                            <input type="checkbox" id="isDbclickBack">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item">
                    <span class="user-setting-item-msg-left">长按重置角色位置</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isLongPressRandom');">
                            <input type="checkbox" id="isLongPressRandom">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item">
                    <span class="user-setting-item-msg-left">显示角色坐标(单位：格)</span>
                    <span class="user-setting-item-switch-right">
                        <label class="switch" @click="switchCheckbox($event, 'isShowRoleMovePos');">
                            <input type="checkbox" id="isShowRoleMovePos">
                            <div class="slider round"></div>
                        </label>
                    </span>
                </li>
                <li class="user-setting-item">
                    <span class="user-setting-item-msg-left">分享/导入角色及坐标</span><span class="reset-btn"
                        @click="resetShareContent(this);" title="重置分享"> 🔄 </span>
                    <div class="user-setting-item-input-area in-one-line">
                        <input type="text" id="shareRoleAndPos" value="" maxlength="1000"
                            placeholder="粘贴内容后点击导入，刷新页面生效">
                        <button class="collide-try-btn bg-lv1" id="rpShareCopy" @click="copyShareContent();">复制</button>
                        <button class="collide-try-btn bg-lv2" id="rpShareImport" @click="importShareContent();"
                            style="display: none;">导入</button>
                    </div>
                </li>
                <li class="user-setting-item">
                    <span class="user-setting-item-msg-left">指定游戏角色(输入角色名)</span><span class="reset-btn"
                        @click="resetGameRoleIds(this);" title="重置角色"> 🔄 </span>
                    <div class="user-setting-item-input-area">
                        <div class="div-input-game-roles default red" contenteditable="true" id="gameRoleId1"
                            placeholder="输入主角" value="">输入主角</div>
                        <div class="div-input-game-roles default red" contenteditable="true" id="gameRoleId2"
                            placeholder="输入队友" value="">输入队友</div>
                        <div class="div-input-game-roles default" contenteditable="true" id="gameRoleId3"
                            placeholder="输入对手1" value="">输入对手1</div>
                        <div class="div-input-game-roles default" contenteditable="true" id="gameRoleId4"
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
                    <span class="user-setting-item-msg-left">角色加速或减速(-20~200)</span>
                    <div class="user-setting-item-input-area">
                        <input type="text" id="roleSpeedAddVal" value="0" maxlength="3">
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
                class="each-item-border-bottom collide-try-close-btn-dialog-title">
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
            <div id="collide-try-how-to-play-title" class="each-item-border-bottom collide-try-close-btn-dialog-title">
                <b>👇 操作指南</b><span>（先这样再那样🤪）</span>
            </div>
            <div id="collide-try-how-to-play-content" class="collide-try-close-btn-dialog-content">
                <pre>
                ① 拖动角色摆好位置
                ② 再拖动主角瞄准，松手开打
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
            <div id="user-setting-about-app-title" class="each-item-border-bottom">
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
<b class="collide-try-app-full-name">玩吧-撞击王者-角色角度练习器</b>
<b>👨‍💻 Author: THeLiGht_ Group</b>
<b>📧 Contact: m1yellow@163.com</b>

1️⃣ 目前支持一个主打角色、三个辅助角色，主要适用于黑娃、僵僵、朵朵、傀儡、双子、太平乐等角色『角度』和『走位』练习
2️⃣ 血量条仅用来区分队伍，因为血量伤害体系很复杂，目前不考虑去实现
3️⃣ 角色运动速度和距离可能和实战有一定差距，做到一模一样很难
4️⃣ 可能存在个别角度（碰墙角）反弹有点问题，请以实战数据为准
5️⃣ 兼容手机、平板、电脑浏览器


<b class="each-item-border-bottom">🆕 V4.2.2 更新：</b>
<pre id="collide-try-about-app-update-newest">
1. 新增了【操作指南】说明，首次进入游戏时提示
2. 调整了双子图标（有显示问题可以反馈一下）
3. 更新了【关于应用】内容
</pre>
                <b class="each-item-border-bottom">V4.2.1 更新：</b>
                1. 新增了【瞄准穿透】开关，弥补傀儡、僵尸等可穿透角色瞄准时的流畅灵敏度
                2. 补全角色录入（62个）

                <b class="each-item-border-bottom">V4.2.0 更新：</b>
                1. 新增了【夏日主题】
                2. 主题模式随季节自动切换
                3. 补全角色录入（61个）

                <b class="each-item-border-bottom">V4.1.5 更新：</b>
                1. 新增了【显示角色运动路径】开关功能
                2. 修复了移动端多点触碰可能出现卡死的问题
                3. 加入了超时自动结束（默认20秒），避免程序一直卡死消耗性能
                4. 【保存离线版】（不用联网）改为【下载离线版】（要联网，更可靠）
                5. 内置了访问密钥，目前不用输入密钥都可以玩了
                6. 还在退游中，玩友们珍重勿念哈

                <b class="each-item-border-bottom">V4.1.4 更新：</b>
                1. 兼容适配平板浏览器
                2. 角色图标、场景主题图形大小调整
                3. 加入了『告别』信息，退游一段时间

                <b class="each-item-border-bottom">V4.1.3 更新：</b>
                1. 新增了【显示角色坐标】功能
                2. 新增了【分享/导入角色及坐标】功能

                <b class="each-item-border-bottom">V4.1.2 更新：</b>
                1. 离线版调整为不需要输入访问密钥
                2. 新增了切换【主角所在队颜色】功能
                3. 优化了【只显示撞击台面】、【显示场景图形】开关，免刷新页面

                <b class="each-item-border-bottom">V4.1.1 更新：</b>
                1. 新增了【显示砖格坐标】功能
                2. 新增了【长按重置角色位置】功能
                3. 优化了【显示台面边框】、【显示砖格坐标】开关，免刷新页面

                <b class="each-item-border-bottom">V4.1.0 更新：</b>
                1. 新增了【瞄准显示路径】功能
                2. 修复了【只瞄准不打】时的拖动问题
                3. 加入了更新提示
                4. 优化了拖动、瞄准时的动画渲染，减少性能消耗

                <b class="each-item-border-bottom">V4.0.3 更新：</b>
                1. 实现了傀儡拉回功能
                2. 新增了太平乐练习选项

                <b class="each-item-border-bottom">V4.0.2 更新：</b>
                1. 修复了僵尸、傀儡瞄准时穿透问题
                2. 实现了电音突破加速效果
                3. 加入了访问密钥（玩友私聊获取即可哦）

                <b class="each-item-border-bottom">V4.0.1 更新：</b>
                1. 新增【保存离线版】功能
                2. 设置主角时，提示使用【极速开始】才生效

                <b class="each-item-border-bottom">V4.0.0 更新：</b>
                1. 可以在设置里面指定任意角色
                2. 新增【双击屏幕回退】重打功能
                3. 游戏界面右上角加入隐形设置按钮，多项设置不用刷新页面
                4. 新增【关于应用】信息
                5. 角色动画分层优化，减少性能消耗

                <b class="each-item-border-bottom">🔗 参考文章：</b>
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
<b class="each-item-border-bottom">几个游戏公平建议：</b>
① 开局在选择角色框下方加入“石头剪刀布”选项，谁赢谁先手！系统不要帮选，不选则后手，选完在游戏界面公示！
② 1号位先打，2号位后打，交给玩家自己决定，玩家就想1号位先打就这么难？
③ 开局角色位置、🌿、💣、🍄 等陷阱位置，请完全随机！哪有那么巧就刚好给直线？
④ 加入『允许发言交流』勾选框，只要有一个玩家不勾选，就不能发言和发表情！
⑤ 加入《撞王等级资格证》机制，根据上一个赛季和当前赛季最高段位自动区分，大奖赛【大师】以下段位加入撞王等级匹配规则，避免 20、30 多级的玩家频繁对阵满级大佬被气走！留住新用户才有得 ⭕ 啊！[狗头]
⑥ 中奖概率有偏爱就不提了！回馈衣食父母也没错 👌

你在教我做事？
游戏公平！玩的人更多！格局打开！


<b class="each-item-border-bottom">不公平！BUG太多！太浪费时间精力！</b>
• 牺牲公平换利益，实在是玩不过！每天都会被不公平和各种BUG气炸！（越是在乎，看得越清，就会越气）

• 工作、生活已经够累了，还要比来比去！游戏娱乐放松了个啥？游戏社交真的能交到好朋友或奔现对象？

• 40级以下，技巧不够、没角色或者只有标配组合，很难打赢高配组合，大概率白送；40级以上，几乎都是高配，先手和开局位置至关重要，两局甚至三局不给先手，大概率连跪！先手和开局好位置给谁，懂的都懂！


<b class="each-item-border-bottom">所以呢？还玩吗？</b>
• <b>清楚自己为什么玩这个游戏！</b>不公平的事情多了去了！怕浪费时间精力就减少做任务/冲分的局数，或者跟好友过一下日常任务、切磋几局练习角色技巧，再或者每天登录签到就行了！

• <b>目标段位期望太高会玩得很累！</b>角色搭配没凑齐高配，撞击技巧（角度、连击、落点）熟练度不够（角色 > 技巧 = 运气[氪金]），遇到满级大佬或者突破&高配组合确实很难赢（毕竟他们已经玩了几年了）！很多 20、30 多级的玩家大奖赛频繁对阵满级大佬，输到怀疑人生，没挺过这段艰难的瓶颈期就气到【注销】了！

• <b>大奖赛“日三”，十局完不成就放下吧！</b>平均一大局（3小局）7 分钟，10 局就一个多小时，20 局两小时以上，每天几个小时玩游戏是挺奢侈的了！用一半的游戏时间经营打理现实生活，会不会更有意义？

•【角色拼不过】+【一个劲儿不认输】，新手角色跟高配角色比拼，就像“鸡蛋碰石头”和高等数学，打不过就是打不过！不会就是不会！<b>这个【拼角色】的游戏别太较劲硬肝！40级之前，角色兑换路线和技巧练习才是关键！</b>


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


//////////////////////////////////////////////////////////////////////
// 【框架全局】 变量、方法区域
//////////////////////////////////////////////////////////////////////

// TODO 当前应用环境，发布时记得修改。prod-正式环境，不打日志；dev-开发环境；debug-调试环境
const currActive = "dev";
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

    return mouse;
};


// 获取鼠标点击坐标
let clickPos = null;
function getClickPos(e) {
    if (!e || e.type === "touchend") return;
    //console.log(e);
    //console.log(e.target);
    let element = e.target;
    let offsetLeft = element.offsetLeft;
    let offsetTop = element.offsetTop;
    //console.log(">>>> getClickPos offsetLeft:" + offsetLeft + ", offsetTop:" + offsetTop);
    clickPos = { x: 0, y: 0 };
    let x, y;
    if (e.pageX && typeof e.pageX === "number") {
        x = e.pageX;
        y = e.pageY;
    } else if (e.touches[0]) {
        x = e.touches[0].pageX;
        y = e.touches[0].pageY;
    }
    x -= offsetLeft;
    y -= offsetTop;
    clickPos.x = x * dpr;
    clickPos.y = y * dpr;
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
function doBack() {
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
    if (isUpdateContentDialogShowing) {
        showUpdateContent(false);
        return;
    }

    // 关闭操作指南弹窗
    if (isHowToPlayDialogShowing) {
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
            alert("👉 刷新页面重选角色，关掉页面退出游戏");
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


let accessKey = null;
let accessMsg = "🔑 请输入访问密钥";
let codeStr = null;
let encodeStr = "fAE9aAJXpmYCxrWJL/hIKhFvLVbtb19viIlXp6sR7qDxD6UBQWc+vruy9Epl0tPXaPsyI2wW6CNUo5obVRzs0wJCo5WgBw69wQaZPFfZtfESR82dt9xbGPckk+nFxF3ijxZ/H7U7sR57exzLtj7+RZcjydXakdUOSy4E7yrImi8mE8pA9xk+6CN2BM/aEXwwwf6LADE1st2NRoLrlOQ7QZ4uGrDzCHBvs8ZpiheUqhlKtMXY2NaiiKqXiZkDv68AOxK9+wTqc0sWueM6z0vwX7uIixVPCdPTgs/U3C+d2Jv4w9Umnn4HYxHsKEPAQhOctiOzXtcvp4Tdu4cWQknrxQaaWELqjlHuOKT3fJjhHrDCO2ZrqhwGjGnJeCc3AhosXu+7ADa8RSPSV9UHyr0mwgZ5T0z/pvaR5xlivfPMtGF0/U1FIh1onqpSRpeqipqwoTU2OuKXTxfyqZRKxFjk5qhZJO569JdABFrYjOrRaBUTxB/+mfmrT254WJT0uoG0WqOhH27Br6vsJCAy4pmcTVW3xq4eWuZZfjOZTZDt+O7AKDM5Ex9HkRwj3O3xrU0XYlp4ZE1VLforNVzFsYIRIEnKSgcDd3uQuiJRm8vnxASXcFC8Tel6Bo08EVylUle4Uj4/tPab8Xtx8FKvfDicCmvtMQb1FliU0pWjzOH3B6y53Uhl0k446HJgLH7k0E8FER8Rsj4NXpYbfx7F4cLdT66Ci3oTSUqfCPb7yMXgRSMYAOA3ONKxYtmFBhIL2w0YhvcHBcAwla3CpTMt6mhtSn62kHURYBkRaTqyOoBJRP24A2xSDi6/9TSZBkyyJFDwP7i0p9nZj+FPo+ua7yI7QNhR1vRv9jv6zpUV2hI/ahHd/dlVYTY9qS0IGlAy7w2IgUpz7qA1jjltcUg1OGBxF/0S6iJvc1BVEpYijh2H/D7QnA1HIf8a5wjZYC1uv4Z+sd12DWzFGNqZY82kUcDYLhsQNmAc8pSlOc4=";
let superKeyEnStr = "zQN6114c/2W74lv7PvypKZh8zsei8CbICQZNtqrBJyxW0xwV350Wig==";
//superKeyEnStr = Aes.Ctr.encrypt("", "", 256);
//console.log('>>>> superKeyEnStr', superKeyEnStr);
//encodeStr = Aes.Ctr.encrypt(codeStr, "", 256);
//console.log('>>>> encodeStr', encodeStr);

// 检测核心代码和密钥
function checkCoreCode(method, isDialog) {

    // 本地版本不检测
    if (isLocalVersion()) return true;

    if (!method || typeof method !== 'string' || method.length > 50) return false;
    for (let i = 0, len = 100; i < len; i++) {
        // 先从 localStorage 获取 accessKey
        accessKey = localStorage.getItem('collide-try-access-key', accessKey);
        // TODO 目前开放使用
        accessKey = "gSLtYnCZNLWAgUxQh0byWDt55xhGj6HU";

        if (isDialog) {
            // 没找到，再弹窗提示输入【访问密钥】
            // 单击取消按钮，prompt() 方法将返回 null，单击确认按钮，prompt() 将返回输入的文本，弹窗时会暂停 JavaScript 执行
            if (!accessKey) accessKey = prompt(accessMsg);
            //console.log(">>>> accessKey=" + accessKey);
            if (accessKey === null) { // 点了取消
                accessMsg = "🔑 请输入访问密钥";
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
            if (accessKey.toLowerCase().includes("thelight")) accessKey = Aes.Ctr.decrypt(superKeyEnStr, accessKey, 256);
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
            //doGlobalError(e, (sysConfig && sysConfig.alertErrorCount)?sysConfig.alertErrorCount:3);
            doGlobalErrorMsg(e, false);
            accessMsg = "❌ 访问密钥错误";
            localStorage.removeItem('collide-try-access-key');
            if (!isDialog) {
                accessMsg = "🔑 请输入访问密钥";
                break;
            }
        }
    }
    return false;
}

// 页面元素、脚本、文件加载完成之后再执行，避免获取不到元素
window.onload = function () {
    checkCoreCode("do2BallsCollidedMV2", false);
}


// 检测输入的访问密钥是否正确
function checkAccessKey() {

    // 本地版本不检测
    if (isLocalVersion()) return true;

    let result = false;
    // 校验是否输入了密钥
    accessKey = localStorage.getItem('collide-try-access-key', accessKey);
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
let gameSceneCoordinateCanvas = document.getElementById('game-scene-coordinate'); // 静态场景砖格坐标布
let canvas = document.getElementById('game-main'); // 主运动层画布
let gameMainBallCanvas = document.getElementById('game-main-ball'); // 主球运动层画布，主球和其他球分开
let gamePathCanvas = document.getElementById('game-path'); // 角色中线路径层画布（一条细线）
let gamePathBallCanvas = document.getElementById('game-path-ball'); // 角色全路径层画布（路径线宽为角色直径）
let gameMaskCanvas = document.getElementById('game-mask'); // 遮罩层画布
// 获取上下文
let gameSceneGraphContext = gameSceneGraphCanvas ? gameSceneGraphCanvas.getContext('2d') : null;
let gameSceneEmojiContext = gameSceneEmojiCanvas ? gameSceneEmojiCanvas.getContext('2d') : null;
let gameSceneContext = gameSceneCanvas ? gameSceneCanvas.getContext('2d') : null;
let gameSceneLinesContext = gameSceneLinesCanvas ? gameSceneLinesCanvas.getContext('2d') : null;
let gameSceneCoordinateContext = gameSceneCoordinateCanvas ? gameSceneCoordinateCanvas.getContext('2d') : null;
let context = canvas ? canvas.getContext('2d') : null;
let gameMainBallContext = gameMainBallCanvas ? gameMainBallCanvas.getContext('2d') : null;
let gamePathContext = gamePathCanvas ? gamePathCanvas.getContext('2d') : null;
let gamePathBallContext = gamePathBallCanvas ? gamePathBallCanvas.getContext('2d') : null;
let gameMaskContext = gameMaskCanvas ? gameMaskCanvas.getContext('2d') : null;
// 弹窗元素
let dialogMask = document.getElementById('dialog-mask'); // 选择角色弹窗遮罩
let chooseRoleDialog = document.getElementById('choose-role-dialog'); // 选择角色弹窗
let userSettingDialog = document.getElementById('user-setting-dialog'); // 参数设置弹窗
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
    gameSceneCoordinateCanvas = document.getElementById('game-scene-coordinate'); // 静态场景砖格坐标布
    canvas = document.getElementById('game-main'); // 主运动层画布
    gameMainBallCanvas = document.getElementById('game-main-ball'); // 主球运动层画布，主球和其他球分开
    gamePathCanvas = document.getElementById('game-path'); // 角色中线路径层画布（一条细线）
    gamePathBallCanvas = document.getElementById('game-path-ball'); // 角色全路径层画布（路径线宽为角色直径）
    gameMaskCanvas = document.getElementById('game-mask'); // 遮罩层画布

    gameSceneGraphContext = gameSceneGraphCanvas.getContext('2d');
    gameSceneEmojiContext = gameSceneEmojiCanvas.getContext('2d');
    gameSceneContext = gameSceneCanvas.getContext('2d');
    gameSceneLinesContext = gameSceneLinesCanvas.getContext('2d');
    gameSceneCoordinateContext = gameSceneCoordinateCanvas.getContext('2d');
    context = canvas.getContext('2d');
    gameMainBallContext = gameMainBallCanvas.getContext('2d');
    gamePathContext = gamePathCanvas.getContext('2d');
    gamePathBallContext = gamePathBallCanvas.getContext('2d');
    gameMaskContext = gameMaskCanvas.getContext('2d');

    dialogMask = document.getElementById('dialog-mask'); // 选择角色弹窗遮罩
    chooseRoleDialog = document.getElementById('choose-role-dialog'); // 选择角色弹窗
    userSettingDialog = document.getElementById('user-setting-dialog'); // 参数设置弹窗
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
    appName: "玩吧-撞击王者-角色角度练习器",
    // 程序版本号
    version: Number(packageVersion.replaceAll(".", "") + "240801"),
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
    // 设置游戏台面边界宽度，取 0.3 * girdSizeCss
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
    // 碰撞损耗，玩吧角色碰墙或者碰其他角色，看着似乎没有损耗。checkBounce方法，作用在合速度上
    bounce: 0,
    // 蛋有弹性，碰撞可增加一定百分比的速度
    eggBounce: 0.2, // v * eggBounce 50 * 0.2 = 10
    // 摩擦力 0.05 0.24 一个接近0.9的系数能很好的模拟出摩擦力的效果
    friction: 0.575,
    // 角色重量极重，对应数值，默认 100，其他角色相对这个值的比率取值
    maxWeightVal: 100,
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
    // 主角所在队颜色
    mainTeamColor: 'r',
    // 是否随机角色，完全随机
    isRandomRole: false,
    // 是否极速开始，挑选常用组合
    isFlashRole: false,
    // 是否只用一个角色测试
    isTestOnlyOne: false,
    // 是否显示小球运动路径
    isShowBallMovePath: true,
    // 是否显示小球本体路径
    isShowBallPath: false,
    // 碰到另一个小球是否停止运动
    isStopAfterCollided: false,
    // 只瞄准不打，用于截图分享
    isJustTrying: false,
    // 碰两次后停止，用于测试观察角度
    isStopAfter2WallCollided: false,
    // 只显示台面
    isJustShowTable: false,
    // 是否显示台面边框
    isShowTableBorder: true,
    // 是否显示砖格坐标
    isShowGridCoordinate: true,
    // 是否显示场景图形
    isShowSceneGraph: true,
    // 是否显示角色血量条
    isShowRoleBloodLine: true,
    // 是否双击屏幕回退
    isDbclickBack: true,
    // 傀儡拉回
    isKuileiPullBack: false,
    // 瞄准穿透(提升流畅)，只对僵尸、傀儡等可穿透角色有效
    isPiercesTry: false,
    // 瞄准显示路径，只对僵尸、傀儡等可穿透角色有效
    isShowTryFullPath: false,
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
    // 斜边角度倾斜偏差（单位：格），用户设置看到的是这里的数值。第一个值对应点(0, 3)，其他点往顺时针方向递增
    //wan8CocosTableMoveVals: [0,0.05,-0.025,-0.025,0.05,-0.025,0.025,0.025], // 注意 undefined 找不到值，或者数值不对，需要清除 localStorage 缓存
    wan8CocosTableMoveVals: [0, 0.05, -0.05, -0.05, 0.12, -0.025, 0.025, 0.08],

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
        this.no = options.no || 0; // 角色id编号，从1开始
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
    static WEIGHTRATIO = { XS: 0.20, S: 0.40, M: 0.60, L: 0.80, XL: 1.00 }
    // 分身初始位置
    static BODY2POS = { x: -1000, y: -1000 }
    // 特殊角色id
    static SPECIALROLEID = { eggId: -1 }


    // 碰撞后立马更新，避免多次碰撞后才更新
    update() {
        this.vx += this.ax;
        this.vy += this.ay;
        this.x += this.vx;
        this.y += this.vy;
        console.log(">>>> Ball update " + this.getBallDesc() + " x=" + this.x + ", y=" + this.y);
        console.log(">>>> Ball update " + this.getBallDesc() + " x0=" + this.x0 + ", y0=" + this.y0);
        console.log(">>>> Ball update " + this.getBallDesc() + " vx=" + this.vx + ", vy=" + this.vy);
        console.log(">>>> Ball update " + this.getBallDesc() + " collidedCount=" + this.collidedCount);
        console.log(">>>> Ball update " + this.getBallDesc() + " wallCollidedCount=" + this.wallCollidedCount);
        console.log(">>>> Ball update " + this.getBallDesc() + " roleCollidedCount=" + this.roleCollidedCount);
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

    // 是否改变了位置
    isPosChanged() {
        return this.x !== this.x0 || this.y !== this.y0;
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
            this.context.arc(this.x, this.y, this.tryRadius, Math.PI / 180 * 0, Math.PI / 180 * 360);
            this.context.fillStyle = "#415D9C";
        } else {
            this.context.arc(this.x, this.y, this.radiusTmp, Math.PI / 180 * 0, Math.PI / 180 * 360);
            this.context.fillStyle = this.color;
        }
        this.context.fill(); // fill 实心；stroke 空心
        // 有露露，为僵僵加上玻璃球
        if (isLuluExist && this.roleId === Role.JIANGJIANG.id && this.id < 0) { // this.id < 0 先不画玻璃球了
            //this.context.globalCompositeOperation = "source-over";
            this.context.arc(this.x, this.y - this.radius / 4, this.radius + 8 * dpr, Math.PI / 180 * 0, Math.PI / 180 * 360);
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
        if (this.iconSize < 10) {
            let metrics, width, ratio;
            ratio = 1.4;
            if (this.roleId === Role.HEIWA.id || this.roleId === Role.BAKE.id
                || this.roleId === Role.X.id || this.roleId === Role.DUODUO.id
                || this.roleId === Role.HUAQIANJI.id) ratio = 1.2;
            let fontSize = roundNumber(sysConfig.girdSize * ratio, 4);
            console.log(">>>> drawIcon" + this.getBallDesc() + " fontSize origin=" + fontSize);

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
            while (width < sysConfig.girdSize * 1.2) {
                fontSize += 1;
                this.context.font = fontSize + "px Arial";
                metrics = this.context.measureText(content);
                width = roundNumber(metrics.width, 4);
                if (fontSize > 100) break; // 避免 width 计算异常，导致死循环
            }
            fontSize = roundNumber(fontSize, 4);
            console.log(">>>> drawIcon" + this.getBallDesc() + " fontSize final=" + fontSize);
            this.iconSize = fontSize;
        } else {
            this.context.font = this.iconSize + "px Arial";
        }

        // 突破效果
        //if (this.upgradeEffect > 0) this.context.font = (fontSize + 10) + "px Arial";

        if (this.isMainBall && this.roleId === Role.KUILEI.id && this.isMoving) {
            this.context.fillText(content, this.x, this.y);
            //this.context.fillText(content, this.x0 === 0 ? this.x : this.x0, this.y0 === 0 ? this.y : this.y0);
        } else if (this.roleId === Role.SHUANGZI.id && content === '👬') { // 双子图标重画
            if (os.isPc || !isTwinLeftIconShow || !isTwinRightIconShow || !iconType) {
                this.context.fillText('🧍', this.x + (0.20 * sysConfig.girdSize), this.y - (0.1 * sysConfig.girdSize));
                this.context.fillText('🧍‍♂️', this.x - (0.20 * sysConfig.girdSize), this.y + (0.1 * sysConfig.girdSize));
            } else {
                this.context.fillText('🏃‍♂️‍➡️', this.x + (0.20 * sysConfig.girdSize), this.y - (0.1 * sysConfig.girdSize));
                this.context.fillText('🏃', this.x - (0.20 * sysConfig.girdSize), this.y + (0.1 * sysConfig.girdSize));
            }
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
        let grd = this.context.createRadialGradient(this.x, this.y, 0.1 * this.radiusTmp, this.x, this.y, this.radiusTmp * 3);
        grd.addColorStop(0.1, "#EEF0F2F0");
        grd.addColorStop(0.3, "#FFFE6150");
        grd.addColorStop(0.6, "#EEF0F280");
        grd.addColorStop(1, "#EEF0F200");
        //this.context.arc(this.x, this.y, this.pathRadius, Math.PI / 180 * 0, Math.PI / 180 * 360);
        this.context.arc(this.x, this.y, this.radiusTmp * 2.5, 0, Math.PI * 2, true);
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
        this.context.arc(this.x, this.y, roundNumber(this.radiusTmp + 2 * dpr * sysConfig.pxRatio, 4), Math.PI / 180 * 0, Math.PI / 180 * 360);
        this.context.strokeStyle = "#D75956";
        if (this.teamColor === 'b') this.context.strokeStyle = "#0A7AFD";
        this.context.closePath();
        this.context.lineWidth = 2 * dpr * sysConfig.pxRatio;
        this.context.stroke();
        this.context.restore();
    }

    // 绘制瞄准时被碰撞角色指示圈
    drawTryCollidedCircle(params, ball) {
        if (ball.isMainBall) return; // 瞄准时被碰撞角色为非主角
        if (userConfig.isTestOnlyOne) return; // 单个角色测试时不画
        if (!params) params = GlobalParams.getCleanParams();
        let context = selectedBall.context;
        context.save();
        context.beginPath();
        if (params.composite) context.globalCompositeOperation = params.composite;
        context.arc(ball.x, ball.y, roundNumber(ball.radiusTmp - 1 * dpr * sysConfig.pxRatio, 4), Math.PI / 180 * 0, Math.PI / 180 * 360);
        context.strokeStyle = "#D75956";
        if (ball.teamColor === 'b') context.strokeStyle = "#0A7AFD";
        context.closePath();
        context.lineWidth = 2 * dpr * sysConfig.pxRatio;
        context.stroke();
        context.restore();
    }

    // 绘制角色血量条
    drawRoleBloodLine(params) {
        if (!userConfig.isShowRoleBloodLine) return;
        //if (userConfig.isTestOnlyOne) return; // 单个角色测试时不画
        if (!this.x || !this.y || this.x < 0 || this.y < 0 || !isFinite(this.x) || !isFinite(this.y)) return;
        if (!params) params = GlobalParams.getCleanParams();
        this.context.save();
        this.context.beginPath();
        this.context.fillStyle = "#D84646";
        if (this.teamColor === 'b') this.context.fillStyle = "#2A7CE9";
        // TODO 频繁绘制阴影，会影响性能，可以改用描边形式
        //this.context.shadowColor = '#60221D60'; // 设置阴影
        //this.context.shadowBlur = 1 * dpr;
        //this.context.globalCompositeOperation = "destination-over";
        if (params.composite) this.context.globalCompositeOperation = params.composite;
        // TODO roundRect 兼容性有问题，老机型/老浏览器不支持
        try {
            //this.context.save00();
            if (this.isMainBall && this.roleId === Role.KUILEI.id && this.isMoving && !isKuileiPulling) this.context.roundRect((this.x0 === 0 ? this.x : this.x0) - roundNumber(2.3 * sysConfig.girdSize / 2, 4), (this.y0 === 0 ? this.y : this.y0) - this.radiusTmp - roundNumber(0.7 * sysConfig.girdSize, 4), roundNumber(2.3 * sysConfig.girdSize, 4), roundNumber(0.39 * sysConfig.girdSize, 4), 2);
            else this.context.roundRect(this.x - roundNumber(2.3 * sysConfig.girdSize / 2, 4), this.y - this.radiusTmp - roundNumber(0.7 * sysConfig.girdSize, 4), roundNumber(2.3 * sysConfig.girdSize, 4), roundNumber(0.39 * sysConfig.girdSize, 4), 2);
        } catch (e) {
            doGlobalErrorMsg(e, false);
            //doGlobalError(e, (sysConfig && sysConfig.alertErrorCount)?sysConfig.alertErrorCount:3);
            // 使用原始方法绘制圆角矩形
            if (this.isMainBall && this.roleId === Role.KUILEI.id && this.isMoving && !isKuileiPulling) fillRoundRect(this.context, (this.x0 === 0 ? this.x : this.x0) - roundNumber(2.3 * sysConfig.girdSize / 2, 4), (this.y0 === 0 ? this.y : this.y0) - this.radiusTmp - roundNumber(0.7 * sysConfig.girdSize, 4), roundNumber(2.3 * sysConfig.girdSize, 4), roundNumber(0.39 * sysConfig.girdSize, 4), 2, this.context.fillStyle);
            else fillRoundRect(this.context, this.x - roundNumber(2.3 * sysConfig.girdSize / 2, 4), this.y - this.radiusTmp - roundNumber(0.7 * sysConfig.girdSize, 4), roundNumber(2.3 * sysConfig.girdSize, 4), roundNumber(0.39 * sysConfig.girdSize, 4), 2, this.context.fillStyle);
        }
        this.context.fill();
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
        gamePathContext.arc(this.x0, this.y0, this.pathRadius, Math.PI / 180 * 0, Math.PI / 180 * 360);
        gamePathContext.fillStyle = this.color;
        gamePathContext.closePath();
        gamePathContext.fill();
        gamePathContext.restore();
        // 画外部实线圆圈
        gamePathContext.save();
        gamePathContext.beginPath();
        //gamePathContext.globalCompositeOperation = "xor";
        gamePathContext.arc(this.x0, this.y0, this.radiusTmp, Math.PI / 180 * 0, Math.PI / 180 * 360);
        gamePathContext.lineWidth = 1 * dpr * sysConfig.pxRatio;
        gamePathContext.strokeStyle = this.color;
        gamePathContext.fillStyle = this.color;
        gamePathContext.closePath();
        if (this.isMainBall && this.roleId === Role.KUILEI.id) gamePathContext.fill(); // 傀儡本体不会动
        else gamePathContext.stroke();
        gamePathContext.restore();
        // 重画被覆盖的角色图标
        this.drawIcon();
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
        gamePathContext.moveTo(p1.x, p1.y);
        gamePathContext.lineTo(p2.x, p2.y);
        gamePathContext.strokeStyle = "#cfe0d380";
        if (userConfig.sceneThemeMode === 5) // 夏日主题
            gamePathContext.strokeStyle = "#F9FBF580";
        if (userConfig.currRole === Role.SHUANGZI.id && !this.isMainBall && this.roleId === Role.SHUANGZI.id) gamePathContext.strokeStyle = "#EADF5580"; // 双子分身路径颜色
        if (this.roleId === Role.KUILEI.id) gamePathContext.strokeStyle = "#D61C24"; // 傀儡路径颜色
        gamePathContext.lineWidth = this.pathRadius * sysConfig.pxRatio;
        gamePathContext.stroke();
        gamePathContext.restore();
    }

    // 绘制小球本体运动路径
    drawBallPath(p1, p2) {
        //if (!userConfig.isShowBallPath) return;
        if (!this.isMoving) return;
        if (!this.isMainBall && this.roleId !== Role.SHUANGZI.id) return; // 非主球不画，双子分身除外
        if (!this.isMainBall && this.roleId === Role.SHUANGZI.id && !userConfig.isTestOnlyOne && this.no > 1 && this.no < 5) return;
        if (!p1 || !p2) return;
        if (isKuileiPulling) return; // 傀儡拉回时不画
        gamePathBallContext.save();
        gamePathBallContext.beginPath(); // 开始一条路径，或重置当前的路径。
        gamePathBallContext.globalCompositeOperation = "xor";
        //gamePathBallContext.globalCompositeOperation = "destination-over"; // 新的图层在老的图层下面
        gamePathBallContext.moveTo(p1.x, p1.y);
        gamePathBallContext.lineTo(p2.x, p2.y);
        gamePathBallContext.strokeStyle = "#cfe0d325";
        if (userConfig.sceneThemeMode === 5) // 夏日主题
            gamePathBallContext.strokeStyle = "#F9FBF540";
        //if (!this.isMainBall && this.roleId === Role.SHUANGZI.id) gamePathBallContext.strokeStyle = "#EADF5525"; // 双子分身路径颜色
        gamePathBallContext.lineWidth = this.radius * 2;
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
            gamePathBallContext.arc(p1.x, p1.y, this.radius, Math.PI / 180 * 0, Math.PI / 180 * 360);
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
        gamePathContext.arc(this.x, this.y, this.pathRadius, Math.PI / 180 * 0, Math.PI / 180 * 360);
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
        // 绘制外虚线
        gamePathContext.save();
        gamePathContext.beginPath();
        gamePathContext.arc(this.x, this.y, this.radius, Math.PI / 180 * 0, Math.PI / 180 * 360);
        gamePathContext.lineWidth = 1 * dpr * sysConfig.pxRatio;
        gamePathContext.strokeStyle = "#000";
        if (userConfig.currRole === Role.SHUANGZI.id && !this.isMainBall && this.roleId === Role.SHUANGZI.id) gamePathContext.strokeStyle = "#fffa"; // 双子分身碰撞圈颜色
        gamePathContext.setLineDash([3 * dpr * sysConfig.pxRatio, 3 * dpr * sysConfig.pxRatio]); // 虚线
        gamePathContext.closePath();
        gamePathContext.stroke(); // 空心
        gamePathContext.restore();
        // 绘制圆心
        gamePathContext.save();
        gamePathContext.beginPath();
        gamePathContext.arc(this.x, this.y, roundNumber(this.pathRadius / 2, 4), Math.PI / 180 * 0, Math.PI / 180 * 360);
        //gamePathContext.fillStyle = this.color;
        gamePathContext.fillStyle = "#cfe0d380";
        if (this.isMainBall && this.roleId === Role.KUILEI.id) gamePathContext.fillStyle = "#D61C24";
        gamePathContext.closePath();
        gamePathContext.fill();
        gamePathContext.restore();

        //if (userConfig.isShowBallPath) {
        // 绘制小球实体填充
        gamePathBallContext.save();
        gamePathBallContext.beginPath();
        gamePathBallContext.globalCompositeOperation = "destination-over";
        gamePathBallContext.arc(this.x, this.y, this.radius, Math.PI / 180 * 0, Math.PI / 180 * 360);
        //gamePathBallContext.fillStyle = this.color;
        gamePathBallContext.fillStyle = "#cfe0d385";
        gamePathBallContext.closePath();
        gamePathBallContext.fill();
        gamePathBallContext.restore();
        //}
    }
}


// 小球是否需要重绘和更新
function isBallDrawAndUpdate(ball, caseNo) {
    // 游戏没开始，肯定要画的
    if (!sysConfig.isGameBeginning) return true;

    // 主角在拖动和瞄准时，所有非主角不画
    if (caseNo === 2 && isMouseMoving && selectedBall.isMainBall) return false;
    // 非主角在拖动和瞄准时，主角也不画
    //if (caseNo === 1 && isMouseMoving && !selectedBall.isMainBall) return false;

    // 僵尸不能改变其他角色位置；傀儡不拉回时，也不能改变其他角色位置
    if (caseNo === 2 && (userConfig.currRole === Role.JIANGJIANG.id || (userConfig.currRole === Role.KUILEI.id && !isKuileiPulling))) {
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
function resetRoleField() {
    if (!balls || balls.length < 1) return;
    for (let i = 0, len = balls.length; i < len; i++) {
        if (!balls[i]) continue;
        // 重置酷酷加速次数
        if (balls[i].roleId === Role.KUKU.id && balls[i].addCount) balls[i].addCount = 0;
        // 重置所有角色碰撞次数
        if (balls[i].collidedCount) balls[i].collidedCount = 0;
        if (balls[i].wallCollidedCount) balls[i].wallCollidedCount = 0;
        if (balls[i].roleCollidedCount) balls[i].roleCollidedCount = 0;
    }
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
function setBallCollidingNos() {
    if (!balls || balls.length < 1) return;
    let len = balls.length;
    balls.forEach(b => {
        for (let i = 0; i < len; i++) {
            //if (!b.collidingNos) b.collidingNos = [];
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
            || userConfig.currRole === Role.HEIWA.id || userConfig.currRole === Role.DUODUO.id);
}


// 用于判断是否在瞄准的时候穿透一次
function isTryCanPierces() {
    return userConfig.isPiercesTry
        && (userConfig.currRole === Role.JIANGJIANG.id || userConfig.currRole === Role.KUILEI.id);
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
    static HEIWA = new Role(0, "🍼", "圣婴大王", "黑娃", "娃", null);
    static JIANGJIANG = new Role(1, "🧟‍♂", "波比僵僵", "僵尸", "僵", null);
    static DUODUO = new Role(2, "🥚", "风铃朵朵", "朵朵", "朵", null);
    static KUILEI = new Role(3, "🦊", "傀儡娃娃", "傀儡", "傀", null);
    static BAKE = new Role(4, "8g", "火焰巴克", "巴克", "巴", null);
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
    static WUKONG = new Role(36, "🐵", "悟空", "猴子", "猴", null);
    static ZHANAN = new Role(37, "🔪", "光影战士", "扎男", "扎", null);
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


    static maxRoleId = -1;

    static getRoleById(id) {
        for (let item in Role) {
            if (Role[item].id === id) return Role[item];
        }
        return null;
    }

    static getFullNameById(id) {
        for (let item in Role) {
            //console.log(item + ".id = " + Role[item].id);
            //console.log(item + ".fullName = " + Role[item].fullName);
            if (Role[item].id === id) return Role[item].fullName;
        }
        return "";
    }

    static getIdByFullName(fName) {
        for (let item in Role) {
            if (Role[item].fullName === fName) return Role[item].id;
        }
        return -1;
    }

    static getFullNameByKeyWord(kw) {
        if (!kw) return "";
        for (let item in Role) {
            if (!Role[item].fullName || !Role[item].shortName) continue;
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
                if (Role[item].id === Number(ids[i])) fNames.push(Role[item].fullName);
            }
        }
        //console.log(">>>> Role.getFullNamesByIds fNames=" + fNames);
        return fNames;
    }

    static getShortNameById(id) {
        for (let item in Role) {
            if (Role[item].id === id) return Role[item].shortName;
        }
        return "";
    }

    static getRoleIconById(id) {
        for (let item in Role) {
            if (Role[item].id === id) return Role[item].icon;
        }
        return "";
    }

    static getRoleArray() {
        let roleArr = [];
        for (let item in Role) {
            if (Role[item].id > -1 && Role[item].id != 10) roleArr.push(item);
        }
        return roleArr;
    }

    static getRandomRoleId() {
        if (this.maxRoleId >= 0) return fullCloseInt(0, this.maxRoleId);
        for (let item in Role) {
            //console.log(">>>> maxRoleId=" + this.maxRoleId);
            if (Role[item].id > this.maxRoleId) this.maxRoleId = Role[item].id;
        }
        return fullCloseInt(0, this.maxRoleId);
    }

    static initRoleCps() {
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
        // TODO 后续需要抽取分类，不然很难维护
    }

}
// 设置主角常用搭配
Role.initRoleCps();


// 常用搭配类
class RegularlyCollocation {

    constructor(id, group) {
        this.id = id;
        this.group = group;
    }

    // 🥚、🧟、❄️、🤡、8g 每个分配一百万个id
    static group1000001 = new RegularlyCollocation(1000001, [Role.DUODUO.id, Role.BAKE.id]);
    static group1000002 = new RegularlyCollocation(1000002, [Role.DUODUO.id, Role.HUAQIANJI.id]);
    static group1000003 = new RegularlyCollocation(1000003, [Role.DUODUO.id, Role.CHUZI.id]);
    static group1000004 = new RegularlyCollocation(1000004, [Role.DUODUO.id, Role.JOKER.id]);
    static group1000005 = new RegularlyCollocation(1000005, [Role.DUODUO.id, Role.HONGZHAJI.id]);
    static group1000006 = new RegularlyCollocation(1000006, [Role.DUODUO.id, Role.MIAOJIANG.id]);
    static group1000007 = new RegularlyCollocation(1000007, [Role.DUODUO.id, Role.NURSE.id]);
    static group1000008 = new RegularlyCollocation(1000008, [Role.DUODUO.id, Role.JIUWEIHU.id]);

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

    static group5000000 = new RegularlyCollocation(5000000, [Role.BAKE.id, Role.DUODUO.id]);
    static group5000001 = new RegularlyCollocation(5000001, [Role.BAKE.id, Role.WUGEGE.id]);
    static group5000002 = new RegularlyCollocation(5000002, [Role.BAKE.id, Role.RABBIT.id]);
    static group5000003 = new RegularlyCollocation(5000003, [Role.BAKE.id, Role.LINGLING.id]);
    static group5000004 = new RegularlyCollocation(5000004, [Role.BAKE.id, Role.DIANYIN.id]);
    static group5000005 = new RegularlyCollocation(5000005, [Role.BAKE.id, Role.XIXUEGUI.id]);
    static group5000006 = new RegularlyCollocation(5000006, [Role.BAKE.id, Role.LEIMENG.id]);
    static group5000007 = new RegularlyCollocation(5000007, [Role.BAKE.id, Role.BZGIRL.id]);
    static group5000008 = new RegularlyCollocation(5000008, [Role.BAKE.id, Role.LANGZAI.id]);
    static group5000009 = new RegularlyCollocation(5000009, [Role.BAKE.id, Role.BZGIRL.id]);
    static group5000010 = new RegularlyCollocation(5000010, [Role.BAKE.id, Role.XIUNV.id]);
    static group5000011 = new RegularlyCollocation(5000011, [Role.BAKE.id, Role.LANLAN.id]);
    static group5000012 = new RegularlyCollocation(5000012, [Role.BAKE.id, Role.SANTAIZI.id]);


    // 其他强势搭配
    static group100000001 = new RegularlyCollocation(100000001, [Role.JIUWEIHU.id, Role.LEIMENG.id]);
    static group100000002 = new RegularlyCollocation(100000002, [Role.JIUWEIHU.id, Role.NURSE.id]);
    static group100000003 = new RegularlyCollocation(100000003, [Role.JIUWEIHU.id, Role.HONGZHAJI.id]);
    static group100000004 = new RegularlyCollocation(100000004, [Role.CHUZI.id, Role.MAGICLION.id]);
    static group100000005 = new RegularlyCollocation(100000005, [Role.BZGIRL.id, Role.DIANYIN.id]);
    static group100000006 = new RegularlyCollocation(100000006, [Role.ZHADANKE.id, Role.HONGSANSAN.id]);
    static group100000007 = new RegularlyCollocation(100000007, [Role.LELE.id, Role.RABBIT.id]);
    static group100000008 = new RegularlyCollocation(100000008, [Role.LELE.id, Role.DIANYIN.id]);
    static group100000009 = new RegularlyCollocation(100000009, [Role.LULU.id, Role.CAPTAIN.id]);
    static group100000010 = new RegularlyCollocation(100000010, [Role.KUKU.id, Role.TIEMIAN.id]);
    static group100000011 = new RegularlyCollocation(100000011, [Role.RABBIT.id, Role.MAGICLION.id]);
    static group100000012 = new RegularlyCollocation(100000012, [Role.RABBIT.id, Role.PUMPKIN.id]);
    static group100000013 = new RegularlyCollocation(100000013, [Role.QUANBA.id, Role.HUAQIANJI.id]);
    static group100000014 = new RegularlyCollocation(100000014, [Role.QUANBA.id, Role.CHUZI.id]);
    static group100000015 = new RegularlyCollocation(100000015, [Role.SANTAIZI.id, Role.DIANYIN.id]);
    static group100000016 = new RegularlyCollocation(100000016, [Role.SANTAIZI.id, Role.RABBIT.id]);
    static group100000017 = new RegularlyCollocation(100000017, [Role.KUKU.id, Role.RABBIT.id]);
    static group100000018 = new RegularlyCollocation(100000018, [Role.KUKU.id, Role.DIANYIN.id]);
    static group100000019 = new RegularlyCollocation(100000019, [Role.NURSE.id, Role.CHUZI.id]);
    static group100000020 = new RegularlyCollocation(100000020, [Role.JIUWEIHU.id, Role.CHUZI.id]);


    static maxGroupId = 0;
    static groupSum = 0;


    static getMaxGroupId() {
        if (this.maxGroupId > 0) return this.maxGroupId;
        for (let item in RegularlyCollocation) {
            if (!RegularlyCollocation[item].id) continue;
            if (RegularlyCollocation[item].id > this.maxGroupId) this.maxGroupId = RegularlyCollocation[item].id;
        }
        return this.maxGroupId;
    }

    static getGroupSum() {
        if (this.groupSum > 0) return this.groupSum;
        for (let item in RegularlyCollocation) {
            if (!RegularlyCollocation[item].id) continue;
            if (RegularlyCollocation[item].id > 0) this.groupSum += 1;
        }
        //console.log(">>>> RegularlyCollocation groupSum=" + this.groupSum); // 41
        return this.groupSum;
    }

    static getNextGroupItem(id) {
        let currItem = null;
        let targetItem = null;
        for (let item in RegularlyCollocation) {
            if (!RegularlyCollocation[item].id) continue;
            if (currItem) {
                targetItem = RegularlyCollocation[item];
                return targetItem;
            }
            if (RegularlyCollocation[item].id === id) currItem = RegularlyCollocation[item];
        }
        return group1000001;
    }

    static getRandomGroup() {
        let idx = fullCloseInt(1, this.getGroupSum());
        //console.log(">>>> RegularlyCollocation getRandomGroup idx=" + idx);
        let i = 1;
        for (let item in RegularlyCollocation) {
            if (!RegularlyCollocation[item].id) continue;
            if (i === idx) return RegularlyCollocation[item].group;
            i++;
        }
        return group1000001.group;
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
// 角色是否存在判断标识
var isDuoduoExist = false;
var isLuluExist = false;
var isShuangziExist = false;
// 分享的角色和坐标数据
var shareData = null;
// html根元素字体大小
var htmlEle, htmlFontSize, htmlFontSizeNum;

onMounted(() => {
    tempCheckBall = new Ball(context);
    twinBall = new Ball(gameMainBallContext);
    htmlEle = document.getElementsByTagName('html')[0];
    htmlFontSize = window.getComputedStyle(htmlEle).fontSize || "12px";
    htmlFontSizeNum = Number(htmlFontSize.replace("px", ""));
})


// 应用初始化
function init() {
    // 设置应用全名（名称+版本名）
    setAppFullName();
    // 设置应用更新内容
    setAppUpdateContent();
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
    // 调整边框宽度为 0.3 * girdSizeCss
    sysConfig.sceneLineWidth = roundNumber(0.27 * sysConfig.girdSizeCss, 4);
    console.log(">>>> sysConfig.sceneLineWidth=" + sysConfig.sceneLineWidth);
    // 设置弹窗滚动区域高度
    setDialogScrollMaxHeight(1.70);
    // 画布居中
    canvasAutoCenter();
    // 初始化鼠标位置
    captureMouse(canvas);
    // 根据用户选择设置当前角色
    //userConfig.currRole = Role.HEIWA.id;
    //userConfig.currRole = Role.JIANGJIANG.id;
    // 导入了角色和坐标数据，不用选角色
    if (userConfig.shareRoleAndPos) {
        try {
            shareData = JSON.parse(userConfig.shareRoleAndPos);
            console.log(shareData);
        } catch (e) { }
    }
    if (!shareData) setCurrRole();
    if (userConfig.currRole < 0) userConfig.currRole = 0;
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
    // 只显示台面，不设置角色【控制台报错可以不用管】
    if (!userConfig.isJustShowTable && userConfig.currRole > -1) {
        try {
            if (!shareData) throw new Error(">>>> 分享角色和坐标数据异常");
            // 设置分享角色和位置
            setShareRoleAndPos(shareData);
            // 设置当前主角
            if (balls && balls.length > 0) userConfig.currRole = balls[0].roleId;
            // 标记角色已经选择完成
            sysConfig.isRoleChooseFinished = true;
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
        }
        // 设置双子分身
        if (userConfig.currRole === Role.SHUANGZI.id) setTwins();
        // 设置完所有角色之后，设置主角所属队颜色
        resetMainTeamColorRandom(userConfig.mainTeamColor);
        // 初始化角色碰撞标志位
        setBallCollidingNos();
        // 设置完角色后，检测角色是否存在
        checkRoleExist();
        // 僵尸露露组合，加快速度
        if (userConfig.currRole === Role.JIANGJIANG.id && isLuluExist) balls[0].vRatio = 1.03;
        // 设置蛋
        if (isDuoduoExist) setEggs();
        // 设置速度
        setSpeed();
        // 设置摩擦力
        setFriction();
    }
    // 角色运动路径判断显示
    if (userConfig.isShowBallMovePath) gamePathCanvas.style.display = "inherit";
    // 角色全路径判断显示
    if (userConfig.isShowBallPath) gamePathBallCanvas.style.display = "inherit";
    // 游戏桌面场景初始化，需要放在角色设置之后，因为场景会根据角色变化
    if (sysConfig.isRoleChooseFinished) gameSceneInit(); // 选择角色后才渲染场景，优化性能
    // 显示操作指南弹窗
    if (sysConfig.isRoleChooseFinished) showHowToPlay(true);
}


onMounted(() => {
    try {
        init();
    } catch (e) {
        // 处理错误事项
        if (e instanceof Error) {
            if (e.message.includes("手动结束程序")) { throw e; }
        }
        doGlobalError(e, (sysConfig && sysConfig.alertErrorCount) ? sysConfig.alertErrorCount : 3);
    }
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
                // 个别特殊字段不受缓存影响，以配置为准
                if (f === 'tryFullPathPointNum') continue;
                if (f === 'animateAutoRestTime') continue;
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
            ball.radius = roundNumber((sysConfig.girdSize * ball.sizeRatio / 2), 4);
            ball.mRatio = Ball.WEIGHTRATIO.M;
            if (ball.isMainBall) ball.vRatio = userConfig.isTestOnlyOne ? 1.05 : Ball.SPEEDRATIO.L; // 速度比率，比黑娃慢一级，为了模拟加速效果，速度可以设置大一点
            //if (ball.isMainBall) ball.v = 63.00; // 初始化的时候根据 vRatio 计算
            break;
        case Role.DUODUO.id:
            ball.color = "#8C5E9D";
            ball.sizeRatio = Ball.SIZERATIO.L; // 大
            ball.radius = roundNumber((sysConfig.girdSize * ball.sizeRatio / 2), 4);
            ball.mRatio = Ball.WEIGHTRATIO.S; // 轻
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        case Role.KUILEI.id:
            ball.color = "#E72E38";
            ball.sizeRatio = Ball.SIZERATIO.L; //  大
            ball.pathRadius = roundNumber(7.0 / 2 * dpr, 4); // 傀儡绳子运动路径半径
            ball.tryRadius = roundNumber(0.7 * sysConfig.girdSize / 2, 4); // 傀儡瞄准线半径
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.XL; // 快/极快，算绳子的速度
            //if (ball.isMainBall) userConfig.isShowBallPath = false; // 不显示全路径
            //if (ball.isMainBall) userConfig.isStopAfterCollided = false;
            break;
        case Role.BAKE.id:
            ball.color = "#FD5B2B";
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
            if (!ball.color) ball.color = "#342F41"; // 取的默认皮肤头发颜色
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
            if (!ball.color) ball.color = "#B9C6CE"; // 取的默认皮肤衣服颜色
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
            if (!ball.color) ball.color = "#CC5F22"; // 取的默认皮肤头发深颜色
            ball.sizeRatio = Ball.SIZERATIO.S; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.L; // 快
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
            if (!ball.color) ball.color = "#6D2665"; // 取的默认皮肤头发颜色
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
            if (!ball.color) ball.color = "#FFA803"; // 取的默认皮肤牛角颜色
            ball.sizeRatio = Ball.SIZERATIO.L; // 大
            ball.mRatio = Ball.WEIGHTRATIO.L; // 重
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        case Role.BAIGUJING.id:
            if (!ball.color) ball.color = "#5A4A71"; // 取的默认皮肤头发颜色
            ball.sizeRatio = Ball.SIZERATIO.M; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.M; // 中等
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.M; // 中等
            break;
        case Role.TUYA.id:
            if (!ball.color) ball.color = "#3F3B41"; // 取的默认皮肤头发颜色
            ball.sizeRatio = Ball.SIZERATIO.M; // 中等
            ball.mRatio = Ball.WEIGHTRATIO.XS; // 极轻
            if (ball.isMainBall) ball.vRatio = Ball.SPEEDRATIO.XL; // 极快
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
    ball.m = ball.mRatio * sysConfig.maxWeightVal;

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
        canvas.width = window.screen.width * sysConfig.sceneWidthRatio;
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
    let targetHeight = Math.round(canvas.width * hRadio);
    let targetCssHeight = Math.round(sysConfig.cssWidth * hRadio);
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


// 设置四根切角线
function set4AngleLine() {
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
            x: sBall.x,
            y: sBall.y,
        });
        // 初始化其他参数
        initBallByRole(shareBall);

        shareBall.x0 = shareBall.x;
        shareBall.y0 = shareBall.y;
        balls.push(shareBall);
    }

    // 是否位一个角色测试
    if (balls.length < 4) userConfig.isTestOnlyOne = true;
    else userConfig.isTestOnlyOne = false;

    // 单独设置小丑分身颜色
    setJoker2Color();
}


// 设置主球【改位置】
function setBallMain() {
    let mainBall = new Ball(gameMainBallContext, {
        no: 1,
        teamColor: 'r',
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
}


// 随机放置所有角色小球
function putAllBallsRandom() {
    if (!balls || balls.length < 1) return;
    balls.some(ball => {
        // 双子分身除外
        if (!ball.isMainBall && ball.roleId === Role.SHUANGZI.id) return;
        putBallRandom(ball);
    });
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
                if (sysConfig.isSayGoodbye && !isProd()) otherRoles = [Role.KUKU.id, Role.BAKE.id, Role.RABBIT.id];
                //console.log(">>>> otherRoles=" + otherRoles.toString());
                break;
            case Role.DUODUO.id:
                //otherRoles = [Role.BAKE.id, Role.KUILEI.id, Role.YINGYING.id];
                //otherRoles = [Role.BAKE.id, Role.DUODUO.id, Role.BAKE.id];
                otherRoles = [Role.DUODUO.cps[fullCloseInt(0, Role.DUODUO.cps.length - 1)]].concat(RegularlyCollocation.getRandomGroup());
                if (sysConfig.isSayGoodbye && !isProd()) otherRoles = [Role.BAKE.id, Role.JOKER.id, Role.DIANYIN.id];
                break;
            case Role.KUILEI.id:
                //otherRoles = [Role.YINGYING.id, Role.BAKE.id, Role.DUODUO.id];
                //otherRoles = [Role.JOKER.id, Role.BAKE.id, Role.DUODUO.id];
                otherRoles = [Role.KUILEI.cps[fullCloseInt(0, Role.KUILEI.cps.length - 1)]].concat(RegularlyCollocation.getRandomGroup());
                if (sysConfig.isSayGoodbye && !isProd()) otherRoles = [Role.JOKER.id, Role.JIANGJIANG.id, Role.MANWANG.id];
                break;
            case Role.SHUANGZI.id:
                //otherRoles = [Role.JOKER.id, Role.JOKER.id, Role.RABBIT.id];
                //otherRoles = [Role.JOKER.id, Role.SHUANGZI.id, Role.RABBIT.id];
                //otherRoles = [Role.JOKER.id, Role.LEIMENG.id, Role.JIUWEIHU.id];
                otherRoles = [Role.SHUANGZI.cps[fullCloseInt(0, Role.SHUANGZI.cps.length - 1)]].concat(RegularlyCollocation.getRandomGroup());
                if (sysConfig.isSayGoodbye && !isProd()) otherRoles = [Role.DIANYIN.id, Role.BAKE.id, Role.RABBIT.id];
                break;
            case Role.KUKU.id:
                //otherRoles = [Role.HEIWA.id, Role.BAKE.id, Role.DUODUO.id];
                otherRoles = [Role.HEIWA.id].concat(RegularlyCollocation.getRandomGroup());
                if (sysConfig.isSayGoodbye && !isProd()) otherRoles = [Role.HEIWA.id, Role.BAKE.id, Role.DUODUO.id];
                break;
            case Role.LELE.id:
                otherRoles = [Role.LELE.cps[fullCloseInt(0, Role.LELE.cps.length - 1)]].concat(RegularlyCollocation.getRandomGroup());
                if (sysConfig.isSayGoodbye && !isProd()) otherRoles = [Role.HEIWA.id, Role.CAPTAIN.id, Role.YINGYING.id];
                break;
            default:
                //otherRoles = [Role.WUGEGE.id, Role.LULU.id, Role.WUGEGE.id];
                //otherRoles = [Role.KUKU.id, Role.LULU.id, Role.JIANGJIANG.id];
                //otherRoles = [Role.JIUWEIHU.id, Role.JIUWEIHU.id, Role.JIANGJIANG.id];
                //otherRoles = [Role.KUKU.id, Role.BAKE.id, Role.DUODUO.id];
                //otherRoles = [Role.RABBIT.id, Role.RABBIT.id, Role.BAKE.id];
                otherRoles = [Role.HEIWA.cps[fullCloseInt(0, Role.HEIWA.cps.length - 1)]].concat(RegularlyCollocation.getRandomGroup());
                if (sysConfig.isSayGoodbye && !isProd()) otherRoles = [Role.LULU.id, Role.SANTAIZI.id, Role.LEIMENG.id];
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
        // 红队角色补全
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
        // 蓝队角色补全
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
        // 红队
        if (isSetCurrRole) { // 重新选择主角
            flashRoles = flashRoles.concat(RegularlyCollocation.getRandomGroup());
        } else {
            flashRoles.push(userConfig.currRole);
            let role = Role.getRoleById(userConfig.currRole);
            flashRoles.push(role.cps[fullCloseInt(0, role.cps.length - 1)]);
        }
        // 蓝队
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
    // 红队校验
    if (otherRoles[0] < 0 || otherRoles[0] === userConfig.currRole) {
        let role = Role.getRoleById(userConfig.currRole);
        otherRoles[0] = role.cps[fullCloseInt(0, role.cps.length - 1)];
    }
    // 蓝队校验
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
            teamColor: idx > 2 ? 'b' : 'r',
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
    for (let i = 0, len = balls.length; i < len; i++) {
        rid = balls[i].roleId;
        if (rid !== Role.JOKER.id) continue;

        let otherBall = new Ball(context, {
            no: balls.length + 1,
            teamColor: i > 1 ? 'b' : 'r',
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
    for (let i = 0, len = roleInputEles.length; i < len; i++) {
        // 存在则删除，不存在则添加
        roleInputEles[i].classList.toggle("red");
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
    //console.log(">>>> checkBallsCollided isBallAndEggCollided=" + result + " > " + ball.getBallDesc());

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
    // 不同设备黑娃横打的时间相同 t=d/v=46*girdSize/48.412=46*42/48.412≈39.907
    // 初始化时会根据 dpr 计算 girdSize 
    // v=d/t
    let v = roundNumber(46 * sysConfig.girdSize / 39.907, 4);
    //console.log(">>>> getHeiwaSpeedByDpr v=" + v);
    return v;
}


// 根据canvas.width设置摩擦力
function setFriction() {
    // 正相关 0.6008 / 583 = f / canvas.width
    // dpr=2 canvas.width=588 sysConfig.friction=0.606
    sysConfig.friction = roundNumber(0.6008 / 583 * canvas.width, 4);
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
    // 画游戏台面
    drawTable();
    // 画蛋
    if (isDuoduoExist) drawEggs();
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
    // 夏日主题个别动物上台面
    if (userConfig.sceneThemeMode === 5) {
        drawIconRandom("🦀", "ss", 1, false, gameSceneCanvas);
        drawIconRandom("🦀", "xxs", 2, false, gameSceneCanvas);
        //drawIconRandom("🦞", "ss", 1, false, gameSceneCanvas);
        //drawIconRandom("🦞", "xxs", 1, false, gameSceneCanvas);
        //drawIconRandom("🐢", "ss", 1, false, gameSceneCanvas);
    }

}


// 画网格
// https://juejin.cn/post/6844904042062151688
function drawSceneGrid() {

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

    // 3. 采用遍历的方式，画水平线条
    //let xLineTotals = Math.floor(CanvasHeight / sysConfig.girdSize); // 计算需要绘画的x轴条数【会有一些误差，导致少画线问题】
    let xLineTotals = 22;
    for (let i = 0; i <= xLineTotals; i++) {
        gameSceneContext.beginPath(); // 开启路径，设置不同的样式
        gameSceneContext.moveTo(0, sysConfig.girdSize * i); // -0.5是为了解决像素模糊问题
        gameSceneContext.lineTo(CanvasWidth, sysConfig.girdSize * i);
        gameSceneContext.strokeStyle = "#8384D1D0"; // 默认主题
        if (i === 11) gameSceneContext.strokeStyle = "#6A6CBFD0"; // 中间线突出一点
        if (userConfig.sceneThemeMode === 1) { // 冰雪主题
            gameSceneContext.strokeStyle = "#438EC2";
            if (i === 11) gameSceneContext.strokeStyle = "#3483B7";
        } else if (userConfig.sceneThemeMode === 3) { // 田园主题
            gameSceneContext.strokeStyle = "#6B624060";
            if (i === 11) gameSceneContext.strokeStyle = "#6B6240D0";
        } else if (userConfig.sceneThemeMode === 4) { // 星际主题
            gameSceneContext.strokeStyle = "#696969A0";
            if (i === 11) gameSceneContext.strokeStyle = "#2F4F4FA0";
        } else if (userConfig.sceneThemeMode === 5) { // 夏日主题
            gameSceneContext.strokeStyle = "#B7521AA0";
            if (i === 11) gameSceneContext.strokeStyle = "#B7521AD0";
        }
        gameSceneContext.stroke();
    }

    // 4.采用遍历的方式，画垂直线条
    //let yLineTotals = Math.floor(CanvasWidth / sysConfig.girdSize); // 计算需要绘画y轴的条数
    let yLineTotals = 14;
    for (let j = 0; j <= yLineTotals; j++) {
        gameSceneContext.beginPath(); // 开启路径，设置不同的样式
        gameSceneContext.moveTo(sysConfig.girdSize * j, 0);
        gameSceneContext.lineTo(sysConfig.girdSize * j, CanvasHeight);
        gameSceneContext.strokeStyle = "#8384D1D0"; // 默认主题
        if (j === 7) gameSceneContext.strokeStyle = "#6A6CBFD0";
        if (userConfig.sceneThemeMode === 1) { // 冰雪主题
            gameSceneContext.strokeStyle = "#438EC2";
            if (j === 7) gameSceneContext.strokeStyle = "#3483B7";
        } else if (userConfig.sceneThemeMode === 3) { // 田园主题
            gameSceneContext.strokeStyle = "#6B624060";
            if (j === 7) gameSceneContext.strokeStyle = "#6B6240D0";
        } else if (userConfig.sceneThemeMode === 4) { // 星际主题
            gameSceneContext.strokeStyle = "#696969A0";
            if (j === 7) gameSceneContext.strokeStyle = "#2F4F4FA0";
        } else if (userConfig.sceneThemeMode === 5) { // 夏日主题
            gameSceneContext.strokeStyle = "#B7521AA0";
            if (j === 7) gameSceneContext.strokeStyle = "#B7521AD0";
        }
        gameSceneContext.stroke();
    }

    gameSceneContext.restore();
}


// 画间隔颜色的砖格
function drawSceneGridRect() {
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
    gameSceneCoordinateContext.font = htmlFontSizeNum * dpr * sysConfig.pxRatio + "px serif";

    // 移动坐标系到场景中心
    //gameSceneCoordinateContext.translate(roundNumber(gameSceneCoordinateCanvas.width / 2), roundNumber(gameSceneCoordinateCanvas.height / 2));
    gameSceneCoordinateContext.translate(gameSceneCoordinateCanvas.width / 2, gameSceneCoordinateCanvas.height / 2);

    // 间隔宽度
    let sceneLineRealWidth = roundNumber(sysConfig.sceneLineWidth * dpr * 1.3, 4);
    if (userConfig.isShowTableBorder) sceneLineRealWidth += roundNumber(sysConfig.sceneLineWidth * dpr * 1.1, 4);

    let CanvasWidth = gameSceneCanvas.width;
    let CanvasHeight = gameSceneCanvas.height;

    // 画左右边界砖格坐标
    let xLineTotals = 22;
    let xLineNum = 8;
    for (let i = 0; i < xLineTotals; i++) {
        // 切角砖格坐标不用画
        if ((i > -1 && i < 4) || (i > 19 && i < 22)) continue;
        gameSceneCoordinateContext.beginPath(); // 开启路径，设置不同的样式
        gameSceneCoordinateContext.fillStyle = "#D2CCF1"; // 设置每个线条的颜色
        if (isDarkMode) gameSceneCoordinateContext.fillStyle = "#D7D7DC";
        if (userConfig.sceneThemeMode === 1) { // 冰雪主题
            gameSceneCoordinateContext.fillStyle = "#687CA1"; // 5A63D1
            if (isDarkMode) gameSceneCoordinateContext.fillStyle = "#EEF0F2";
        } else if (userConfig.sceneThemeMode === 3) { // 田园主题
            gameSceneCoordinateContext.fillStyle = "#252042";
            if (isDarkMode) gameSceneCoordinateContext.fillStyle = "#FBFAD0";
        } else if (userConfig.sceneThemeMode === 4) { // 星际主题
            gameSceneCoordinateContext.fillStyle = "#D7D7DC";
            if (isDarkMode) gameSceneCoordinateContext.fillStyle = "#D7D7DC";
        } else if (userConfig.sceneThemeMode === 5) { // 夏日主题
            gameSceneCoordinateContext.fillStyle = "#2B117D";
            if (isDarkMode) gameSceneCoordinateContext.fillStyle = "#FBFAD0";
        }
        gameSceneCoordinateContext.fillText(xLineNum + "", -(CanvasWidth / 2 + sceneLineRealWidth), -(CanvasHeight / 2 + sysConfig.girdSize / 2) + sysConfig.girdSize * i);
        gameSceneCoordinateContext.fillText(xLineNum + "", (CanvasWidth / 2 + sceneLineRealWidth), -(CanvasHeight / 2 + sysConfig.girdSize / 2) + sysConfig.girdSize * i);
        if (i < 11) xLineNum--;
        if (i > 11) xLineNum++;
    }

    // 画上下边界砖格坐标
    let yLineTotals = 14;
    let yLineNum = 4;
    for (let j = 0; j < yLineTotals; j++) {
        // 切角砖格坐标不用画
        if ((j > -1 && j < 4) || (j > 11 && j < 14)) continue;
        gameSceneCoordinateContext.beginPath();
        gameSceneCoordinateContext.fillStyle = "#D2CCF1";
        if (isDarkMode) gameSceneCoordinateContext.fillStyle = "#D7D7DC";
        if (userConfig.sceneThemeMode === 1) { // 冰雪主题
            gameSceneCoordinateContext.fillStyle = "#687CA1";
            if (isDarkMode) gameSceneCoordinateContext.fillStyle = "#EEF0F2";
        } else if (userConfig.sceneThemeMode === 3) { // 田园主题
            gameSceneCoordinateContext.fillStyle = "#252042";
            if (isDarkMode) gameSceneCoordinateContext.fillStyle = "#FBFAD0";
        } else if (userConfig.sceneThemeMode === 4) { // 星际主题
            gameSceneCoordinateContext.fillStyle = "#D7D7DC";
            if (isDarkMode) gameSceneCoordinateContext.fillStyle = "#D7D7DC";
        } else if (userConfig.sceneThemeMode === 5) { // 夏日主题
            gameSceneCoordinateContext.fillStyle = "#2B117D";
            if (isDarkMode) gameSceneCoordinateContext.fillStyle = "#FBFAD0";
        }
        gameSceneCoordinateContext.fillText(yLineNum + "", -(CanvasWidth / 2 + sysConfig.girdSize / 2) + sysConfig.girdSize * j, -(CanvasHeight / 2 + sceneLineRealWidth));
        gameSceneCoordinateContext.fillText(yLineNum + "", -(CanvasWidth / 2 + sysConfig.girdSize / 2) + sysConfig.girdSize * j, (CanvasHeight / 2 + sceneLineRealWidth));
        if (j < 7) yLineNum--;
        if (j > 7) yLineNum++;
    }

    gameSceneCoordinateContext.restore();
}


// 画场景背景色
function drawSceneBg() {
    gameSceneContext.save();
    gameSceneContext.fillStyle = "#8d93d8"; // 默认主题-场地背景色
    if (userConfig.sceneThemeMode === 1)
        gameSceneContext.fillStyle = "#4B99C9"; // 冰雪主题-场地背景色
    else if (userConfig.sceneThemeMode === 3)
        gameSceneContext.fillStyle = "#9A9069"; // 田园主题-场地背景色
    else if (userConfig.sceneThemeMode === 4)
        gameSceneContext.fillStyle = "Gray"; // 星际主题-场地背景色
    else if (userConfig.sceneThemeMode === 5)
        gameSceneContext.fillStyle = "#FFBF6F"; // 夏日主题-场地背景色
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
            document.body.style.backgroundColor = '#C7D0E0';
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
            document.body.style.backgroundColor = '#C7D0E0';
            break;
        case 3: // 田园主题
            document.body.style.backgroundColor = '#E6DD9C';
            if (userConfig.isShowSceneGraph) {
                // 花草树木，鸡鸭鹅狗猪牛羊【先后顺序可控制图形叠加效果】
                drawIconUpAndDown("🌹", "xxs", 4, true);
                drawIconRandom("🌹", "xxs", 8);
                drawIconRandom("🌼", "xxs", 5);
                drawIconUpAndDown("🌷", "xxs", 4, true);
                drawIconRandom("🌷", "xxs", 8);
                drawIconUpAndDown("🌻", "mm", 1);
                drawIconRandom("🌻", "s", 2);
                drawIconRandom("🥕", "xs", 4);
                drawIconRandom("🍄", "xxxs", 4);
                if (isWoodIconShow) drawIconRandom("🪵", "ss", 2);
                drawIconRandom("🥚", "xxs", 5);
                drawIconUpAndDown("🌳", "l", 1);
                drawIconRandom("🌳", "s", 1);
                drawIconRandom("🐕", "s", 2);
                drawIconRandom("🐖", "m", 1);
                drawIconRandom("🐖", "mm", 1);
                drawIconRandom("🐂", "l", 1);
                drawIconRandom("🐏", "mm", 1);
                drawIconRandom("🐑", "mm", 1);
                drawIconRandom("🐈", "ss", 1);
                drawIconRandom("🐇", "ss", 1);
                drawIconRandom("🐇", "xs", 1);
                drawIconRandom("🐍", "xs", 1);
                drawIconRandom("🐌", "xxxs", 4);
                drawIconRandom("🐝", "xxxs", 4);
                drawIconRandom("🦋", "xxs", 2);
                drawIconUpAndDown("🐓", "ss", 1, false, 1); // 只画上/左方
                drawIconRandom("🐓", "ss", 2);
                drawIconRandom("🦃", "ss", 4);
                drawIconUpAndDown("🦆", "ss", 1, false, 2); // 只画下/右方
                drawIconRandom("🦆", "ss", 2);
            }
            break;
        case 4: // 星际主题
            document.body.style.backgroundColor = '#05132C';
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
                //drawIconRandom("👨‍🚀", "ss", 1);
                //drawIconRandom("👩‍🚀", "ss", 1);
                drawIconUpAndDown("👩‍🚀", "ss", 1, true, 1);
                drawIconUpAndDown("👨‍🚀", "ss", 1, true, 2);
            }
            break;
        case 5: // 夏日主题
            document.body.style.backgroundColor = '#3C8BBB'; // 00ABDE
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
                drawIconRandom("🏄", "s", 1);
                drawIconRandom("🏄‍♀️", "s", 1);
                drawIconRandom("🏊", "s", 1);
                drawIconRandom("🏊‍♀️", "s", 1);
                drawIconRandom("🌊", "ss", 2);
                drawIconRandom("🌊", "xxs", 5);
                drawIconRandom("🐚", "xxxs", 4);
                drawIconRandom("⛵️", "m", 2);
                drawIconRandom("🪂", "m", 2);
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
            document.body.style.backgroundColor = '#7F70C3';
            //sysConfig.sceneLineWidth -= 2; // 边框窄一点
            if (userConfig.isShowSceneGraph) {
                // 中心图形
                drawCenterGraphSvg("svg-default-center");
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
                drawSvgUpAndDown("svg-stone", "s", 1);
                drawSvgUpAndDown("svg-stone", "ss", 1);
                drawSvgUpAndDown("svg-stone", "xxs", 2);
                drawSvgRandom("svg-stone", "ss", 2);
                drawSvgRandom("svg-stone", "xxs", 6);
                // 指定位置画石头和骨头
                drawStoneGraphDefault();
                // 画骨头
                drawSvgUpAndDown("svg-bone", "mm", 1, true);
                drawSvgUpAndDown("svg-bone", "s", 1);
                drawSvgRandom("svg-bone", "s", 1);
                drawSvgRandom("svg-bone", "xs", 2);
                drawSvgRandom("svg-bone", "xxs", 6);
            }
    }

    /* 额外处理 */
    // 默认主题剪掉左右边框
    //if (userConfig.sceneThemeMode === 0) clipDefaultTableLines();
}


function doDrawTableLines() {
    globalParams.shadowColor = "#352e6160";
    //if (userConfig.sceneThemeMode === 1 && isLightMode) globalParams.shadowColor = "#819BC3"; // 冰雪主题边框阴影
    globalParams.shadowBlur = 6 * dpr;
    drawTableLines();
    globalParams.shadowBlur = 1 * dpr;
    drawTableLines();
}


// 边框阴影只用画一次，性能影响不大
// gameSceneLines画布全屏，坐标移到正中间
function drawTableLines() {
    gameSceneLinesContext.save();
    if (globalParams) { // 设置阴影
        gameSceneLinesContext.shadowColor = globalParams.shadowColor;
        gameSceneLinesContext.shadowBlur = globalParams.shadowBlur;
    }
    gameSceneLinesContext.strokeStyle = "#35357A"; // 默认主题边框
    if (userConfig.sceneThemeMode === 1)
        gameSceneLinesContext.strokeStyle = "#EEF0F2"; // 冰雪主题边框
    else if (userConfig.sceneThemeMode === 3)
        gameSceneLinesContext.strokeStyle = "#FBFAD0"; // 田园主题边框
    else if (userConfig.sceneThemeMode === 4)
        gameSceneLinesContext.strokeStyle = "#D7D7DC"; // 星际主题边框 EBEBE9
    else if (userConfig.sceneThemeMode === 5)
        gameSceneLinesContext.strokeStyle = "#FAF9CB"; // 夏日主题边框 FAF9CB
    let sceneLineRealWidth = roundNumber(sysConfig.sceneLineWidth * dpr, 4); // 不同设备实际线宽
    gameSceneLinesContext.lineWidth = sceneLineRealWidth; // 设置线宽
    // 移动坐标系到场景中心
    gameSceneLinesContext.translate(roundNumber(gameSceneLinesCanvas.width / 2, 4), roundNumber(gameSceneLinesCanvas.height / 2, 4));
    gameSceneLinesContext.beginPath();
    gameSceneLinesContext.moveTo(-sysConfig.girdSize * 4 + sysConfig.wan8CocosTableMoveVals[1], -sysConfig.girdSize * 11 - sceneLineRealWidth / 2); // 起点，对应左上第二个点
    gameSceneLinesContext.lineTo(sysConfig.girdSize * 4 + sysConfig.wan8CocosTableMoveVals[2], -sysConfig.girdSize * 11 - sceneLineRealWidth / 2);
    gameSceneLinesContext.lineTo(sysConfig.girdSize * 7 + sceneLineRealWidth / 2, -sysConfig.girdSize * 8 + sysConfig.wan8CocosTableMoveVals[3]);
    gameSceneLinesContext.lineTo(sysConfig.girdSize * 7 + sceneLineRealWidth / 2, sysConfig.girdSize * 8 + sysConfig.wan8CocosTableMoveVals[4]);
    gameSceneLinesContext.lineTo(sysConfig.girdSize * 4 + sysConfig.wan8CocosTableMoveVals[5], sysConfig.girdSize * 11 + sceneLineRealWidth / 3);
    gameSceneLinesContext.lineTo(-sysConfig.girdSize * 4 + sysConfig.wan8CocosTableMoveVals[6], sysConfig.girdSize * 11 + sceneLineRealWidth / 3);
    gameSceneLinesContext.lineTo(-sysConfig.girdSize * 7 - sceneLineRealWidth / 2, sysConfig.girdSize * 8 + sysConfig.wan8CocosTableMoveVals[7]);
    gameSceneLinesContext.lineTo(-sysConfig.girdSize * 7 - sceneLineRealWidth / 2, -sysConfig.girdSize * 8 + sysConfig.wan8CocosTableMoveVals[0]);
    gameSceneLinesContext.closePath(); // 闭合路径
    gameSceneLinesContext.stroke();
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
            height = roundNumber(metrics.actualBoundingBoxAscent + metrics.actualBoundingBoxDescent, 4);
            //console.log(">>>> graph width=" + width + ", height=" + height);
            count = Math.round(sysConfig.cTop * dpr / height); // 能容纳多少个
            if (os.isPc) count = Math.round(sysConfig.cLeft * dpr / width);
            //console.log(">>>> count=" + count);
            // if (count < 1) continue; // 不考虑 count，则图形可以超出边界
            //if (!os.isPc) gameSceneEmojiContext.fillText(icon, fullOpen(width / 2, gameSceneEmojiCanvas.width - width / 2), fullOpen(sysConfig.cTop * dpr / 4, sysConfig.cTop * dpr - height));
            //if (os.isPc) gameSceneEmojiContext.fillText(icon, fullOpen(width / 2, sysConfig.cLeft * dpr - width), fullOpen(height / 2, gameSceneEmojiCanvas.height - height / 2));
            if (!os.isPc) gameSceneEmojiContext.fillText(icon, fullOpen(width / 2, gameSceneEmojiCanvas.width - width / 2), fullOpen(sysConfig.cTop * dpr - graphViewAreaSize + height / 2, sysConfig.cTop * dpr - height / 2));
            if (os.isPc) gameSceneEmojiContext.fillText(icon, fullOpen(sysConfig.cLeft * dpr - graphViewAreaSize + width / 2, sysConfig.cLeft * dpr - width / 2), fullOpen(height / 2, gameSceneEmojiCanvas.height - height / 2));
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
            height = roundNumber(metrics.actualBoundingBoxAscent + metrics.actualBoundingBoxDescent, 4);
            count = Math.round(sysConfig.cTop * dpr / height);
            if (os.isPc) count = Math.round(sysConfig.cLeft * dpr / width);
            //if (count < 1) continue;
            //if (!os.isPc) gameSceneEmojiContext.fillText(icon, fullOpen(width / 2, gameSceneEmojiCanvas.width - width / 2), fullOpen(gameSceneEmojiCanvas.height - sysConfig.cTop * dpr + height / 2, gameSceneEmojiCanvas.height - height / 2));
            //if (os.isPc) gameSceneEmojiContext.fillText(icon, fullOpen(gameSceneEmojiCanvas.width - sysConfig.cLeft * dpr + width / 2, gameSceneEmojiCanvas.width), fullOpen(height / 2, gameSceneEmojiCanvas.height - height / 2));
            if (!os.isPc) gameSceneEmojiContext.fillText(icon, fullOpen(width / 2, gameSceneEmojiCanvas.width - width / 2), fullOpen(gameSceneEmojiCanvas.height - sysConfig.cTop * dpr + height / 2, gameSceneEmojiCanvas.height + (graphViewAreaSize - sysConfig.cTop * dpr) - height / 2));
            if (os.isPc) gameSceneEmojiContext.fillText(icon, fullOpen(gameSceneEmojiCanvas.width - sysConfig.cLeft * dpr + width / 2, gameSceneEmojiCanvas.width + (graphViewAreaSize - sysConfig.cLeft * dpr) - width / 2), fullOpen(height / 2, gameSceneEmojiCanvas.height - height / 2));
            gameSceneEmojiContext.beginPath();
        }
    }

    gameSceneEmojiContext.restore();
}


// 【全屏随机布局ICON】
function drawIconRandom(icon, size, num, isNumRd, targetCanvas) {
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
        height = roundNumber(metrics.actualBoundingBoxAscent + metrics.actualBoundingBoxDescent, 4);
        count = Math.round(sysConfig.cTop / height);
        if (count < 1) continue;
        ctx.fillText(icon, fullOpen(width / 2, targetCanvas.width - width / 2), fullOpen(height / 2, targetCanvas.height - height / 2));
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
                    height = roundNumber(img.height * scale, 4);
                    count = Math.round(sysConfig.cTop * dpr / height);
                    if (os.isPc) count = Math.round(sysConfig.cLeft * dpr / width);
                    //if (count < 1) continue;
                    // 随机旋转角度，0 ~ 360
                    //let rotate = fullCloseInt(0, 360);
                    //gameSceneEmojiContext.rotate((rotate * Math.PI) / 180);
                    //if (!os.isPc) gameSceneEmojiContext.drawImage(img, 0, 0, img.width, img.height, fullOpen(width / 2, gameSceneEmojiCanvas.width - width / 2), fullOpen(sysConfig.cTop * dpr / 4, sysConfig.cTop * dpr - height / 2), width, height);
                    //if (os.isPc) gameSceneEmojiContext.drawImage(img, 0, 0, img.width, img.height, fullOpen(width / 2, sysConfig.cLeft * dpr - width / 2), fullOpen(height / 2, gameSceneEmojiCanvas.height - height / 2), width, height);
                    if (!os.isPc) gameSceneEmojiContext.drawImage(img, 0, 0, img.width, img.height, fullOpen(width / 2, gameSceneEmojiCanvas.width - width / 2), fullOpen(sysConfig.cTop * dpr - graphViewAreaSize + height / 2, sysConfig.cTop * dpr - height / 2), width, height);
                    if (os.isPc) gameSceneEmojiContext.drawImage(img, 0, 0, img.width, img.height, fullOpen(sysConfig.cLeft * dpr - graphViewAreaSize + width / 2, sysConfig.cLeft * dpr - width / 2), fullOpen(height / 2, gameSceneEmojiCanvas.height - height / 2), width, height);
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
                    height = roundNumber(img.height * scale, 4);
                    count = Math.round(sysConfig.cTop * dpr / height);
                    if (os.isPc) count = Math.round(sysConfig.cLeft * dpr / width);
                    //if (count < 1) continue;
                    //if (!os.isPc) gameSceneEmojiContext.drawImage(img, 0, 0, img.width, img.height, fullOpen(width / 2, gameSceneEmojiCanvas.width - width / 2), fullOpen(gameSceneEmojiCanvas.height - sysConfig.cTop * dpr + height / 2, gameSceneEmojiCanvas.height - height / 2), width, height);
                    //if (os.isPc) gameSceneEmojiContext.drawImage(img, 0, 0, img.width, img.height, fullOpen(gameSceneEmojiCanvas.width - sysConfig.cLeft * dpr + width / 2, gameSceneEmojiCanvas.width), fullOpen(height / 2, gameSceneEmojiCanvas.height - height / 2), width, height)
                    if (!os.isPc) gameSceneEmojiContext.drawImage(img, 0, 0, img.width, img.height, fullOpen(width / 2, gameSceneEmojiCanvas.width - width / 2), fullOpen(gameSceneEmojiCanvas.height - sysConfig.cTop * dpr + height / 2, gameSceneEmojiCanvas.height + (graphViewAreaSize - sysConfig.cTop * dpr) - height / 2), width, height);
                    if (os.isPc) gameSceneEmojiContext.drawImage(img, 0, 0, img.width, img.height, fullOpen(gameSceneEmojiCanvas.width - sysConfig.cLeft * dpr + width / 2, gameSceneEmojiCanvas.width + (graphViewAreaSize - sysConfig.cLeft * dpr) - width / 2), fullOpen(height / 2, gameSceneEmojiCanvas.height - height / 2), width, height)
                    gameSceneEmojiContext.beginPath();
                }
            }
        }
    }

    gameSceneEmojiContext.restore();
}


// 【全屏随机布局SVG】
function drawSvgRandom(svgId, size, num, isNumRd) {
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
                height = roundNumber(img.height * scale, 4);
                count = Math.round(sysConfig.cTop * dpr / height);
                if (os.isPc) count = Math.round(sysConfig.cLeft * dpr / width);
                //if (count < 1) continue;
                gameSceneEmojiContext.drawImage(img, 0, 0, img.width, img.height, fullOpen(width / 2, gameSceneEmojiCanvas.width - width / 2), fullOpen(height / 2, gameSceneEmojiCanvas.height - height / 2), width, height);
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
    location.reload();
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
        // 显示右上角设置入口提示
        showGameSettingEntryDialog();
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
            doDrawTableLines();
        }
        // 开启砖格坐标，最好清空重画一次，避免显示没有边框时位置
        if (canvasEle === gameSceneCoordinateCanvas) {
            clearCanvasAll(gameSceneCoordinateCanvas);
            drawSceneCoordinate();
        }
        canvasEle.style.display = "inherit";
    } else { // 关闭
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
    } else { // 开关未打开，点击后打开
        switchEle.setAttribute("checked", true);
        isShow = true;
        userConfig[key] = true;
        if (key === "isShowBallPath") { // 角色全路径打开，依赖的角色运动路径也一起打开
            userConfig.isShowBallMovePath = true;
            document.getElementById("isShowBallMovePath").setAttribute("checked", true);
            togglePathBallMoveShow(isShow);
        }
    }

    // canvas图层切换显示
    if (params && params.canvasEle) switchCanvasShow(params.canvasEle, isShow);
    // 角色运动路径
    if (key === "isShowBallMovePath") togglePathBallMoveShow(isShow);
    // 角色球体路径
    if (key === "isShowBallPath") togglePathBallShow(isShow);
    // 血量条切换显示
    if (key === "isShowRoleBloodLine") directPlayAgain(false);
    // 只显示撞击台面
    if (key === "isJustShowTable") {
        toggleOnlyTable(isShow);
        if (!balls || balls.length < 1) sysConfig.isNeedReload = true;
    }
    // 切换显示场景图形
    if (key === "isShowSceneGraph") toggleSceneGraph(isShow);

    // 需要刷新页面的设置
    if (key === "isTestOnlyOne") sysConfig.isNeedReload = true;

    // localStorage 存储更新 userConfig 对象
    localStorage.setItem('collide-try-user-settings', JSON.stringify(userConfig));

}


// 点击按钮，下拉菜单在 显示/隐藏 之间切换
function toggleDropdown() {
    document.getElementById("themeDropdown").classList.toggle("show");
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
        directPlayAgain(false);
    }

    // 更新设置
    userConfig.mainTeamColor = val;
    localStorage.setItem('collide-try-user-settings', JSON.stringify(userConfig));
}


// 切换只显示撞击台面，隐藏角色层
function toggleOnlyTable(isShow) {
    // 清空路径层
    clearCanvasAll(gamePathCanvas);
    clearCanvasAll(gamePathBallCanvas);
    if (isShow) { // 只显示台面
        canvas.style.display = "none";
        gameMainBallCanvas.style.display = "none";
    } else { // 取消只显示台面
        canvas.style.display = "unset";
        gameMainBallCanvas.style.display = "unset";
    }
}


// 切换显示场景图形，隐藏emoji等图形层
function toggleSceneGraph(isShow) {
    if (isShow) { // 显示
        gameSceneGraphCanvas.style.display = "unset";
        if (isCanvasBlank(gameSceneEmojiCanvas)) { // 空画布，需要重新绘制
            setSceneTheme();
        } else {
            gameSceneEmojiCanvas.style.display = "unset";
        }
    } else { // 不显示
        gameSceneGraphCanvas.style.display = "none";
        gameSceneEmojiCanvas.style.display = "none";
    }
}


// 设置场景主题值
function setSceneThemeVal(ele, val) {
    if (!ele) return;
    //console.log(ele);

    if (val === 2) { // 新年主题暂未实现
        alert("🏮：敬请期待哦~");
        return;
    }

    userConfig.sceneThemeMode = val;
    setSceneThemeText(val);

    // localStorage 存储更新 userConfig 对象
    localStorage.setItem('collide-try-user-settings', JSON.stringify(userConfig));

    // 修改了主题，需要刷新页面
    sysConfig.isNeedReload = true;
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
    switchCanvasShow(gamePathCanvas, isShow);
}


// 切换显示本体路径层画布
function togglePathBallShow(isShow) {
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
    sysConfig.isNeedReload = true;

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
    sysConfig.isNeedReload = true;

    // 设置了主角，提示主角需要在【极速开始】选项才会生效
    if (val && idx === 0) showGameSettingMainRoleDialog();
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
    sysConfig.isNeedReload = true;
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
    sysConfig.isNeedReload = true;
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

    if (!checkAccessKey()) return;

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
    let url = "https://www.m1yellow.cn/collide-try?download=1&f=" + titleEle.innerText + ".html";
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
// 【工具类相关】 变量、方法区域
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


// [n, m] 整数
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


// 两平面⚪是否碰撞
function is2CirclesCollided(ball0, ball1) {
    return (ball0.x - ball1.x) ** 2 + (ball0.y - ball1.y) ** 2 <= (ball0.radius + ball1.radius) ** 2;
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
            if (isDuoduoExist && isCheckEgg(ball)) ec = checkEggCollided(ball);
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
            if (isDuoduoExist && isCheckEgg(ball)) ec = checkEggCollided(ball);
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
            if (isCollisionBallAndBall(ball, b)) { // TODO 处理正在碰撞被当成很多次碰撞问题。animate 60 帧内会调用很多次方法，导致穿一次被计算成很多次
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

                if (userConfig.currRole === Role.JIANGJIANG.id) {
                    do2BallsCollidedMV2(ball, b, isCheck, false, collideParams);
                } else if (userConfig.currRole === Role.KUILEI.id) {
                    if (isKuileiPulling) do2BallsCollidedMV2(ball, b, true, false, collideParams);
                    else do2BallsCollidedMV2(ball, b, isCheck, false, collideParams);
                } else do2BallsCollidedMV2(ball, b, true, false, collideParams);

                // 显示瞄准碰撞指示圈【瞄准时不停地检测，导致指示圈有闪动，后续再搞】
                //if (isCheck) ball.drawTryCollidedCircle(null, b);

                console.log(">>>> checkOtherBalls-" + ball.getBallDesc() + "-撞击点坐标：x=" + ball.x + ", y=" + ball.y);
                if (isCheck && recordCollidedPoint(ball)) return true; // 注意只是结束循环

                // 碰到就停止
                if (userConfig.isStopAfterCollided) {
                    ball.vx = 0;
                    ball.vy = 0;
                    //ball.isMoving = false;
                    b.vx = 0;
                    b.vy = 0;
                    //b.isMoving = false;
                    return true;
                }

                // 处理小球碰撞后速度                
                if (userConfig.currRole === Role.JIANGJIANG.id) {
                    // 简单模拟僵尸穿透加速、减速
                    doJiangjiangSpeed(ball, b);
                } else if (userConfig.currRole === Role.KUILEI.id) {
                    //console.log(">>>> checkOtherBalls isKuileiPulling=" + isKuileiPulling);
                    if (isKuileiPulling) do2BallsCollidedMV2(ball, b, false, true, collideParams);
                } else {
                    //do2BallsCollided(ball, b);
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
        if (ball.vx ** 2 + ball.vy ** 2 > (speed0 * 1.3) ** 2) return true;
    } else { // 1.5
        if (ball.vx ** 2 + ball.vy ** 2 > (speed0 * 1.2) ** 2) return true;
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
    const kukuTeammateRatio = 1.4;
    // 突破后酷酷自身加速50%
    const kukuSelfRatio = 1.3;
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
    // 碰角色加速 4%
    const body1Ratio = 1 + 0.09;
    // 碰小丑分身减速 2%
    const body2Ratio = 1 - 0.07;
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


// 处理电音加速
function doDianyinSpeed(ball0, ball1) {
    if (!isDianyinCollided(ball0, ball1)) return;
    //console.log(">>>> doDianyinSpeed isDianyinCollided=true");
    // 突破后，碰到存活对手，自身加速20%，手动调整比例，跟实战对比
    //const dianyinRatio = 1.40;
    let dianyinRatio, speed0; // 改为原始速度的比例
    if (ball0.roleId === Role.DIANYIN.id) { // ball0 为电音
        ball0.upgradeEffect = 1; // 设置突破效果
        if (!isSpeedMax(ball0)) {
            speed0 = getBallSpeed0(ball0);
            dianyinRatio = speed0 * 0.18; // 20% 偏快，手动调整
            //console.log(">>>> doDianyinSpeed dianyinRatio", dianyinRatio);
            //ball0.vx *= dianyinRatio;
            //ball0.vy *= dianyinRatio;
            ball0.vx += (ball0.vx >= 0 ? dianyinRatio : -dianyinRatio);
            ball0.vy += (ball0.vy >= 0 ? dianyinRatio : -dianyinRatio);
        }
    } else { // ball1 为电音
        ball1.upgradeEffect = 1;
        if (!isSpeedMax(ball1)) {
            speed0 = getBallSpeed0(ball1);
            dianyinRatio = speed0 * 0.18;
            ball1.vx += (ball1.vx >= 0 ? dianyinRatio : -dianyinRatio);
            ball1.vy += (ball1.vy >= 0 ? dianyinRatio : -dianyinRatio);
        }
    }
}


// 处理太平乐加速
function doLeleSpeed(ball0, ball1) {
    if (userConfig.currRole !== Role.LELE.id) return;
    if (!isLeleCollided(ball0, ball1)) return;
    // 突破后，碰到存活角色（队友和对手都算），自身加速30%，手动调整比例，跟实战对比
    const leleRatio = 1.50;
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

    if (isCheckEgg(ball) && isInEggArea(ball)) {
        eggs.forEach(e => {
            if (isCollisionBallAndBall(ball, e)) {
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

                do2BallsCollidedMV2(ball, e, true, false, collideParams);

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
                    //do2BallsCollided(ball, e);
                    do2BallsCollidedMV2(ball, e, false, true, collideParams);
                    // 蛋不会动
                    e.vx = 0;
                    e.vy = 0;
                    // 蛋反弹加速
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
    if (isCheckEgg(ball) && isInEggArea(ball)) {
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
    let posCheck = ((ball.y <= 2 * sysConfig.girdSize || ball.y >= 20 * sysConfig.girdSize) && ball.x >= 5 * sysConfig.girdSize && ball.x <= 9 * sysConfig.girdSize);
    return posCheck;
}


// 是否需要检测碰蛋
function isCheckEgg(ball) {
    return !ball.isMainBall || ball.roleId !== Role.JIANGJIANG.id && (ball.roleId !== Role.KUILEI.id || isKuileiPulling);
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


// 计算两球碰撞后速度和方向【不带质量】
function do2BallsCollided(ball0, ball1) {
    let dvx = ball0.vx - ball1.vx;
    let dvy = ball0.vy - ball1.vy;
    let d_x = ball0.x - ball1.x;
    let d_y = ball0.y - ball1.y;
    let xx_yy = d_x * d_x + d_y * d_y;
    let DVx = (dvx * d_x * d_x + dvy * d_x * d_y) / xx_yy;
    let DVy = (dvy * d_y * d_y + dvx * d_x * d_y) / xx_yy;
    ball0.vx = ball0.vx - DVx;
    ball0.vy = ball0.vy - DVy;
    ball1.vx = ball1.vx + DVx;
    ball1.vy = ball1.vy + DVy;
}


// 小球带质量碰撞反弹
var collideParams = { bounce: 0.70, eggId: -1 };
onMounted(() => {
    collideParams.bounce = sysConfig.bounce ? sysConfig.bounce : (sysConfig.friction + 0.00);
    collideParams.eggId = Ball.SPECIALROLEID.eggId;
    if (!collideParams.bounce) collideParams.bounce = 0.70;
    if (!collideParams.eggId) collideParams.eggId = -1;
    console.log(">>>> do2BallsCollidedMV2 params=" + JSON.stringify(collideParams));
})
//function do2BallsCollidedMV2(ball0, ball1, isChPos, isChVel, params) {}


// 小球绘制及速度状态更新
function drawAndUpdate(ball, isCheck) {
    // 所有碰撞检测未完成，不绘制，也不更新速度，直接返回
    if (!ball.isCheckFinished) return;
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
function checkFriction(ball) {
    if (sysConfig.friction <= 0) return;
    if (ball.isMainBall && ball.roleId === Role.KUILEI.id && !isKuileiPulling) return; // 傀儡的绳子不受摩擦力影响，拉回时影响
    let v = Math.sqrt(ball.vx * ball.vx + ball.vy * ball.vy);
    //if (v > 0 ) console.log(">>>> v=" + v);
    let angle = Math.atan2(ball.vy, ball.vx);
    if (v > sysConfig.friction) {
        v -= sysConfig.friction;
    } else {
        v = 0;
    };
    ball.vx = Math.cos(angle) * v;
    ball.vy = Math.sin(angle) * v;
}


// 反弹系数速度损耗，每弹一次，速度会变慢一点
function checkBounce(ball, bounceVal) {
    if (!bounceVal && sysConfig.bounce <= 0) return;
    if (ball.isMainBall && ball.roleId === Role.KUILEI.id && !isKuileiPulling) return; // 傀儡的绳子不减速，拉回时影响
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
function checkEggBounce(ball) {
    if (sysConfig.eggBounce <= 0) return;
    if (ball.isMainBall && (ball.roleId === Role.KUILEI.id && !isKuileiPulling || ball.roleId === Role.JIANGJIANG.id)) return;
    if (ball.vx <= 0 && ball.vy <= 0) return;

    ball.vx = ball.vx >= 0 ? ball.vx + sysConfig.eggBounce : ball.vx - sysConfig.eggBounce;
    ball.vy = ball.vy >= 0 ? ball.vy + sysConfig.eggBounce : ball.vy - sysConfig.eggBounce;
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
        else KLRadius = ball0.pathRadius;
    }
    // 双子本体与分身不会碰撞，会穿透
    let twinCheck = isTwinSelf(ball0, ball1);
    result = !twinCheck && (ball0.x - ball1.x) ** 2 + (ball0.y - ball1.y) ** 2 <= ((KLRadius ? KLRadius : ball0.radius) + ball1.radius) ** 2;

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

    // 正在碰撞不重复检测【只对僵尸和傀儡未拉回时生效】
    if ((userConfig.currRole === Role.JIANGJIANG.id || (userConfig.currRole === Role.KUILEI.id && !isKuileiPulling)) &&
        colliding01 && colliding01 === ball0.collidingNos[ball1.no - 1]) result = false;

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
// 尝试运动的小球，碰撞点坐标
let tryMoveBallCollidedPoints = [];
// 控制绘制运动轨迹
let isAnimated = false; // 渲染完成
let isMoving = true; // 是否在运动
let isPlaying = true; // 是否在玩
let isKuileiPulling = false; // 傀儡是否正在拉回


// 动画渲染入口
onMounted(() => {
    animate();
})


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
    let ctx = cvs.getContext('2d');
    ctx.clearRect(0, 0, cvs.width, cvs.height);
    ctx.beginPath(); // 开启新path，避免旧的path残留
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
    balls.some(ball => {
        ball.vx = 0;
        ball.vy = 0;
        ball.update();
    });
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
            tryMoveBall.radius = balls[0].tryRadius;
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
        console.log(">>>> doTryMoveBallFirstCollidedPos count=" + count);
        if (count > 100) break;
    }
    console.log(">>>> 找到第一个撞击点坐标：x=" + tryMoveBallFirstCollidedPos.x + ", y=" + tryMoveBallFirstCollidedPos.y);
    isFirstCollidedPointFounded = true;
    // 重置标志
    if (tryMoveBall.isCollided) tryMoveBall.isCollided = false;
    // 重置速度
    doTryMoveBallFinished();
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
        // 双子打完后
        if (userConfig.currRole === Role.SHUANGZI.id && balls[i].roleId === Role.SHUANGZI.id && balls[i].isMainBall)
            afterTwins(selectedBall ? false : true);
    }

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
    // 清空路径层画布
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
    // TODO 手动产生一个很小的变动，坐标一样会导致主球路径清理不掉
    ball.x0 -= 0.000001;
}


// 根据鼠标与小球连线角度，获取vx、vy
//function getVxVy(p1, p2) {}
function getVxVy(p1, p2, v, ball) {
    if (!ball) return { vx: 0, vy: 0 };
    let targetBall = ball;
    //if (!targetBall) targetBall = balls[0];
    // 获取角度，鼠标位置、球位置，两点连线与y轴的角度
    // 1-近点（主球）；2-远点
    //let angle = getAngle({x:mouse.x, y:mouse.y},{x:targetBall.x, y:targetBall.y});
    let angle = getAngleX({
        x: p1 ? p1.x : targetBall.x,
        y: p1 ? p1.y : targetBall.y
    }, {
        x: p2 ? p2.x : mouse.x,
        y: p2 ? p2.y : mouse.y
    });
    //console.log('>>>> angle=' + angle);

    // 已知角度、速度v，求 vx vy
    let radians = angle * Math.PI / 180;
    let vx = Math.cos(radians) * (v ? v : targetBall.v);
    let vy = Math.sin(radians) * (v ? v : targetBall.v);
    //console.log('>>>> vx=' + vx + '; vy=' + vy);

    // TODO 运动反向取反，模拟玩吧撞击王者
    if (ball) {
        ball.vx = -vx;
        ball.vy = -vy;
    }

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


// 绘制瞄准线，小球中心点与碰撞点连线
// 获取了第一个碰撞点，就不用反向，直接连接球位置与第一个撞击点位置即可
function drawLine2Point(p1, p2) {
    if (!selectedBall || !selectedBall.isMainBall) return; // 非主球不画
    let context = selectedBall.context;
    context.save();
    context.beginPath();
    context.globalCompositeOperation = "destination-over";
    context.moveTo(p1.x, p1.y); // 起始位置
    context.lineTo(p2.x, p2.y); // 结束位置
    context.strokeStyle = '#cfe0d330';
    if (userConfig.sceneThemeMode === 5) // 夏日主题
        context.strokeStyle = "#F9FBF540";
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
    context.lineWidth = 1 * dpr * sysConfig.pxRatio;
    context.strokeStyle = "#E6ECFF75";
    if (userConfig.sceneThemeMode === 5) // 夏日主题
        context.strokeStyle = "#F9FBF5A0";
    context.setLineDash([6 * dpr * sysConfig.pxRatio, 3 * dpr * sysConfig.pxRatio]);
    if (selectedBall.isMainBall && selectedBall.roleId === Role.KUILEI.id) context.setLineDash([2 * dpr * sysConfig.pxRatio, 2 * dpr * sysConfig.pxRatio]);
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

//////////////////////////////////////////////////////////////////////


//////////////////////////////////////////////////////////////////////
// 【点击、拖动事件】 变量、方法区域
//////////////////////////////////////////////////////////////////////
// 长按定时器
let longPressTimer = 0;
// 长按坐标
let longPressPoint = { x: 0, y: 0 };
// 小球拖动前的坐标
let oldBallPos = { x: 0, y: 0 };
// 移动端开始触摸事件
let currTouchPointNum = 0;


// 事件顺序：touchstart-touchmove-touchend-mousedown-mouseup-click
// mousedown事件触发时绑定mousemove、mouseup事件，mouseup事件触发时，解除mousemove、mouseup事件
onMounted(() => {
    if (os.isPc) canvas.addEventListener('mousedown', (e) => {

        if (isMoving) return; // 运动状态

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
        //console.log(e);
        doEventDefault(e);
        currTouchPointNum = e.touches.length;
        // 目前只支持单点触碰
        if (currTouchPointNum !== 1) return;
        getClickPos(e);
        // 触摸开始，设置长按定时器
        longPressPoint.x = mouse.x;
        longPressPoint.y = mouse.y;
        longPressTimer && clearTimeout(longPressTimer);
        longPressTimer = setTimeout(() => { doLongPress(e) }, 500);
    }, false);
})


// 鼠标按下并拖动
var isMouseMoving = false;
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
            tryMoveBall.v = 200;
            getVxVy(null, null, tryMoveBall.v, selectedBall);
        } else { // 其他角色
            getVxVy(null, null, null, selectedBall);
        }
        // 更新移动的球
        tryMoveBall.x = selectedBall.x;
        tryMoveBall.y = selectedBall.y;
        //tryMoveBall.x0 = selectedBall.x;
        //tryMoveBall.y0 = selectedBall.y;
        tryMoveBall.vx = selectedBall.vx;
        tryMoveBall.vy = selectedBall.vy;
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


function onMouseUp() {
    // 鼠标左键抬起，重置长按定时器
    longPressTimer && clearTimeout(longPressTimer);
    longPressTimer = 0;
    // 清除事件
    canvas.removeEventListener('mousemove', onMouseOrTouchMove, false);
    canvas.removeEventListener('mouseup', onMouseUp, false);
}


function onMouseOrTouchMove(e) {
    //console.log(e);
    doEventDefault(e);
    // 解决部分机型，手指没有move，touchmove事件仍会被调用的问题
    if (longPressPoint.x !== mouse.x || longPressPoint.y !== mouse.y) {
        // 有拖动行为，重置长按定时器
        longPressTimer && clearTimeout(longPressTimer);
        longPressTimer = 0;
    }
    selectBall();
    onMouseMove();
}


function onTouchEnd() {
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


// 单击开始往指定方向运动
// 事件顺序 mousedown、mouseup、click，前一个事件执行完毕才会执行下一个事件
onMounted(() => {
    if (os.isPc) canvas.addEventListener('click', (e) => {
        doEventDefault(e);
        getClickPos(e);
        doClick(e);

    }, false);
})


// 双击允许拖动小球位置
onMounted(() => {
    if (os.isPc) canvas.addEventListener('dblclick', (e) => {
        doEventDefault(e);
        doDbClick(e);

    }, false);
})


// 移动端单、双击事件
onMounted(() => {
    let lastTouchEnd = 0;
    if (!os.isPc) canvas.addEventListener('touchend', (e) => {
        //console.log(e);
        //alert(e.touches.length);
        doEventDefault(e);
        //if (e.type !== "touchend" && e.touches.length !== 0) return;
        if (currTouchPointNum !== 1) return;
        // 触摸结束，重置长按定时器
        longPressTimer && clearTimeout(longPressTimer);
        longPressTimer = 0;

        let now = (new Date()).getTime();
        if (now - lastTouchEnd <= 300) { // 200~300
            //alert(">>>> 双击了");
            doDbClick(e);
        } else {
            //alert(">>>> 单击了");
            doClick(e);
        }
        lastTouchEnd = now;
    }, false);
})


// 单击后处理逻辑
function doClick(e) {

    // 三连击计数
    //preTripleClick(e);
    // 鼠标或手指抬起，标记鼠标没有在拖动
    isMouseMoving = false;

    if (!selectedBall) return; // 没用选中球

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
        // 初始化双子分身
        if (selectedBall.isMainBall && selectedBall.roleId === Role.SHUANGZI.id) doTwins(selectedBall);
        // 重置角色字段属性值
        resetRoleField();
        // 瞄准松手开打之前，再次更新速度，避免瞄准看到的跟实际打的方向因为手抖导致偏差
        if (tryMoveBallFirstCollidedPos.x > 0 && tryMoveBallFirstCollidedPos.y > 0)
            getVxVy(tryMoveBallFirstCollidedPos, { x: selectedBall.x, y: selectedBall.y }, null, selectedBall);
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
    }
    // 判断球位置是否改动
    if (isBallMoved(selectedBall)) { // 拖动完成
        if (selectedBall.isMainBall) selectedBall.isChgPosFinished = true; // 主球才会有拖动完成，会发射，发射后才可以再次拖动
        if (!selectedBall.isMainBall) selectedBall = null; // 非主球拖动完成后，不发射，可以多次拖动
        // 自动隐藏坐标条
        rolePosLineTimer = setTimeout(() => { rolePosLine.style.display = 'none' }, 3000);
    }
}


// 双击后处理逻辑【移动端双击还有点问题】
function doDbClick(e) {
    // 三连击计数
    //preTripleClick(e, true);
    // 双击主球，免拖动，直接开打
    directPlayAgain(true);
}


// 三连击，不用太快点【不稳定，会触发单击、双击的事件，导致功能混乱】
let tripleClick = 0;
let tripleClickTimer = 0;
function doTripleClick(e) {
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
    // 移动端目前只支持单点触碰
    if (!os.isPc && currTouchPointNum !== 1) return;
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
    if (ele && ele.tagName && ele.tagName.toLowerCase() === "a") return;

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
