<template>
    <div class="app-container">
        <div class="l-lottery">
            <div style="display:flex; font-size: 40px; justify-content: center; color:#ffe800;height: 80px;align-items: end;">
                幸运大抽奖
            </div>
            <div style="display:flex; justify-content: center; color:#ffe800;height: 30px;align-items: end;">
              您有{{state.num}}次抽奖机会
            </div>
            <div class="l-box">
                <!-- <h2 class="title">周年庆回馈</h2> -->
                <div class="l-circle-pan-box">
                    <div
                        class="l-circle-pan-box-inner"
                        :style="{ transform: `rotate(${state.degNum}deg)` }"
                    >
                        <div
                            class="num-item"
                            v-for="(item, index) in lotteryList"
                            :key="index"
                            :class="['num-item' + index]"
                            :style="item"
                        >
                            <span class="num-item-text">{{ item.desc }}</span>
                            <div class="num-item-name">
                                {{ item.name }}
                                <img
                                    :src="(item.img)"
                                    style="width: 20px"
                                    alt=""
                                />
                            </div>
                        </div>
                    </div>
                    <img
                        class="l-circle-btn"
                        src="./assets/images/circle_btn.png"
                        @click="handlePreStartClick"
                    />
                    <!-- <img class="l-head-icon" src="./assets/images/sanjiao.png" /> -->
                </div>
            </div>
          
            <div class="info">
            <div class="contentBlock drawList">
                <!-- <a
                    href="javascript:;"
                    class="more"
                    onclick="dw.showDrawListWin();"
                    >查看更多&gt;&gt;</a
                > -->
                <h3>他们都中奖啦</h3>
                <div id="drawList">
                    <ul>
                        <li class="item" style="margin-top: 0px">
                            <span class="avatar"
                                ><img
                                    src="https://s1.lezhi99.com/static/image/no_avatar.png" /></span
                            ><span class="nickname">贵宾{{getRandomInt(1000,9999)}}</span
                            ><span class="prize">50元元优惠券</span
                            ><span class="date">{{formatDateToMMDD(getRandomDateLastWeek())}}</span>
                        </li>
                        <li class="item" style="margin-top: 0px">
                            <span class="avatar"
                                ><img
                                    src="https://s1.lezhi99.com/static/image/no_avatar.png" /></span
                            ><span class="nickname">贵宾{{getRandomInt(1000,9999)}}</span
                            ><span class="prize">酒店1晚</span
                            ><span class="date">{{formatDateToMMDD(getRandomDateLastWeek())}}</span>
                        </li>
                        <li class="item" style="margin-top: 0px">
                            <span class="avatar"
                                ><img
                                    src="https://s1.lezhi99.com/static/image/no_avatar.png" /></span
                            ><span class="nickname">贵宾{{getRandomInt(1000,9999)}}</span
                            ><span class="prize">悍马糖一颗</span
                            ><span class="date">{{formatDateToMMDD(getRandomDateLastWeek())}}</span>
                        </li>
                        <li class="item" style="margin-top: 0px">
                            <span class="avatar"
                                ><img
                                    src="https://s1.lezhi99.com/static/image/no_avatar.png" /></span
                            ><span class="nickname">贵宾{{getRandomInt(1000,9999)}}</span
                            ><span class="prize">50元优惠券</span
                            ><span class="date">{{formatDateToMMDD(getRandomDateLastWeek())}}</span>
                        </li>
                        <li class="item" style="margin-top: 0px">
                            <span class="avatar"
                                ><img
                                    src="https://s1.lezhi99.com/static/image/no_avatar.png" /></span
                            ><span class="nickname">贵宾{{getRandomInt(1000,9999)}}</span
                            ><span class="prize">10元优惠券</span
                            ><span class="date">{{formatDateToMMDD(getRandomDateLastWeek())}}</span>
                        </li>
                        <li class="item" style="margin-top: 0px">
                            <span class="avatar"
                                ><img
                                    src="https://s1.lezhi99.com/static/image/no_avatar.png" /></span
                            ><span class="nickname">贵宾{{getRandomInt(1000,9999)}}</span
                            ><span class="prize">酒店1晚</span
                            ><span class="date">{{formatDateToMMDD(getRandomDateLastWeek())}}</span>
                        </li>
                        <li class="item" style="margin-top: 0px">
                            <span class="avatar"
                                ><img
                                    src="https://s1.lezhi99.com/static/image/no_avatar.png" /></span
                            ><span class="nickname">贵宾{{getRandomInt(1000,9999)}}</span
                            ><span class="prize">姐妹花</span
                            ><span class="date">{{formatDateToMMDD(getRandomDateLastWeek())}}</span>
                        </li>
                        <li class="item" style="margin-top: 0px">
                            <span class="avatar"
                                ><img
                                    src="https://s1.lezhi99.com/static/image/no_avatar.png" /></span
                            ><span class="nickname">贵宾{{getRandomInt(1000,9999)}}</span
                            ><span class="prize">10元优惠券</span
                            ><span class="date">{{formatDateToMMDD(getRandomDateLastWeek())}}</span>
                        </li>
                        <li class="item" style="margin-top: 0px">
                            <span class="avatar"
                                ><img
                                    src="https://s1.lezhi99.com/static/image/no_avatar.png" /></span
                            ><span class="nickname">贵宾{{getRandomInt(1000,9999)}}</span
                            ><span class="prize">酒店1晚</span
                            ><span class="date">{{formatDateToMMDD(getRandomDateLastWeek())}}</span>
                        </li>
                        <li class="item" style="margin-top: 0px">
                            <span class="avatar"
                                ><img
                                    src="https://s1.lezhi99.com/static/image/no_avatar.png" /></span
                            ><span class="nickname">贵宾{{getRandomInt(1000,9999)}}</span
                            ><span class="prize">延时喷雾一瓶</span
                            ><span class="date">{{formatDateToMMDD(getRandomDateLastWeek())}}</span>
                        </li>
                        <li class="item" style="margin-top: 0px">
                            <span class="avatar"
                                ><img
                                    src="https://s1.lezhi99.com/static/image/no_avatar.png" /></span
                            ><span class="nickname">贵宾{{getRandomInt(1000,9999)}}</span
                            ><span class="prize">50元优惠券</span
                            ><span class="date">{{formatDateToMMDD(getRandomDateLastWeek())}}</span>
                        </li>
                        <li class="item" style="margin-top: 0px">
                            <span class="avatar"
                                ><img
                                    src="https://s1.lezhi99.com/static/image/no_avatar.png" /></span
                            ><span class="nickname">贵宾{{getRandomInt(1000,9999)}}</span
                            ><span class="prize">姐妹花</span
                            ><span class="date">{{formatDateToMMDD(getRandomDateLastWeek())}}</span>
                        </li>
                        <li class="item" style="margin-top: 0px">
                            <span class="avatar"
                                ><img
                                    src="https://s1.lezhi99.com/static/image/no_avatar.png" /></span
                            ><span class="nickname">贵宾{{getRandomInt(1000,9999)}}</span
                            ><span class="prize">酒店1晚</span
                            ><span class="date">{{formatDateToMMDD(getRandomDateLastWeek())}}</span>
                        </li>
                        <li class="item" style="margin-top: 0px">
                            <span class="avatar"
                                ><img
                                    src="https://s1.lezhi99.com/static/image/no_avatar.png" /></span
                            ><span class="nickname">贵宾{{getRandomInt(1000,9999)}}</span
                            ><span class="prize">延时喷雾一瓶</span
                            ><span class="date">{{formatDateToMMDD(getRandomDateLastWeek())}}</span>
                        </li>
                        <li class="item" style="margin-top: 0px">
                            <span class="avatar"
                                ><img
                                    src="https://s1.lezhi99.com/static/image/no_avatar.png" /></span
                            ><span class="nickname">贵宾{{getRandomInt(1000,9999)}}</span
                            ><span class="prize">酒店1晚</span
                            ><span class="date">{{formatDateToMMDD(getRandomDateLastWeek())}}</span>
                        </li>
                    </ul>
                </div>
            </div>
            <div id="description" class="contentBlock description">
              <h3>活动说明</h3>
              <div class="content">为回馈新老客户以及三周年店庆特推出抽奖活动，每人限抽奖一次，奖品在办理入会后联系客服领取。</div>
            </div>
            </div>
           
        </div>
    </div>
</template>

<script setup lang="ts">
import { reactive, ref } from 'vue'

const lotteryList = reactive([
    { desc: 'iphone', img: 'iphone.png' },
    { name: '优惠券', desc: '10元', img: '' },
    { name: '鼓励奖', desc: '再来一次', img: ''  },
    { name: '优惠券', desc: '50元', img: ''  },
    { desc: '酒店1晚', img: 'hotel.png' },
    { desc: '姐妹花', img: 'sister.png' },
    { name: '一颗', desc: '悍马糖', img: ''  },
    { name: '一瓶', desc: '延时喷雾', img: ''  }
])

const state = reactive({
    isStart: false,
    circleNum: 0,
    currentLottery: {},
    degNum: 180,
    num:!localStorage.getItem('num') ? 1 : 0
})

console.log(localStorage.getItem('num'));


function getRandomInt(min, max) {
    min = Math.ceil(min); // 向上取整
    max = Math.floor(max); // 向下取整
    return Math.floor(Math.random() * (max - min + 1)) + min; // 包含min和max
}


function getRandomDateLastWeek() {
    const today = new Date(); // 当前日期和时间
    const randomDays = Math.floor(Math.random() * 7) + 1; // 生成1到7的随机整数，确保不包含今天
    const randomDate = new Date(today.getTime() - randomDays * 24 * 60 * 60 * 1000); // 计算随机天数前的日期

    return randomDate;
}

function formatDateToMMDD(date) {
    const month = date.getMonth() + 1;  // getMonth() 返回0（一月）到11（十二月）之间的一个整数。
    const day = date.getDate();        // getDate() 返回月份中的第几天（从1到31）。

    // 为了确保月份和日期始终是两位数，可以使用padStart()方法。
    const formattedMonth = month.toString().padStart(2, '0');
    const formattedDay = day.toString().padStart(2, '0');

    return `${formattedMonth}-${formattedDay}`;
}





function getStyle() {
    const w = 276 // 原型的宽度
    const len = lotteryList.length
    //中心点横坐标
    var dotLeft = (w - 95) / 2
    //中心点纵坐标
    var dotTop = (w - 100) / 2
    var radius = w / 2
    var avd = 360 / len
    var ahd = (avd * Math.PI) / 180
    lotteryList.forEach((item: any, index) => {
        item.left = Math.sin(ahd * index) * radius + dotLeft + 'px'
        item.top = Math.cos(ahd * index) * radius + dotTop + 'px'
        let deg = 180 - index * 45 + index + 'deg'

        item.transform = `rotate(${deg})`
    })
}
function startClick() {
    if (!state.isStart&&state.num>0) {
        state.isStart = true;

        localStorage.setItem('num','0');
        state.num = 0;

        // localStorage.setItem('num',"0")

        state.circleNum += 7
        state.isStart = true

        const index = Math.floor(Math.random() * lotteryList.length)
        console.log(index)
        state.degNum = state.circleNum * 360 + 4 * 45 + 180

        const current = lotteryList[4]

        setTimeout(() => {
            alert(`恭喜您，获得了${current.desc}`)
        }, 4500)
        state.isStart = false
    }
}

getStyle()

function handlePreStartClick() {
    startClick()
}

</script>

<style lang="scss">
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
body,
html,
#app,
.app-container {
    width: 100%;
    height: 100%;
    overflow-y: auto;
    overflow-x: hidden;
    background: #e73454;
}

.l-lottery {
    position: relative;
    width: 100%;
    height: 100%;
    background: url('./assets/images/bg.png') no-repeat;
    background-size: 100% auto;

    .l-box {
        width: 100%;
        flex-direction: row;
        justify-content: center;
        height: 400px;
        align-items: center;

        .title {
            text-align: center;
        }
    }
    .l-circle-pan-box {
        position: absolute;
        left: 50%;
        top: 120px;
        width: 276px;
        height: 276px;
        border-radius: 50%;
        transform: translateX(-50%);
    }
    .l-circle-pan-box-inner {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        border-radius: 50%;
        background: url('./assets/images/circle_pan_blank.png') no-repeat;
        background-size: 100% 100%;
        transition: all 4s;
    }
    .l-circle-btn {
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -55%);
        width: 95px;
        height: 100px;
    }
    .l-head-icon {
        position: absolute;
        left: 50%;
        top: 0px;
        transform: translate(-53%, -60%);
        width: 100px;
        height: 80px;
        width: 86px;
        height: 77px;
    }
    .num-item {
        position: absolute;
        width: 100px;
        height: 100px;
        // background-color: red;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        padding-top: 80px;
    }
    .num-item-name {
        color: #e73454;
        font-size: 12px;
        font-weight: 700;
    }
    .num-item-text {
        color: #b55e28;
        font-size: 13px;
        margin-top: 6px;
        font-weight: 700;
    }

    .info{
      width: 100%;
      display: flex;
      justify-content: center;
      flex-direction: column;
      align-items: center;
    }
    ul,
    li {
        padding: 0;
        margin: 0;
        list-style: none;
    }
    h1,
    h2,
    h3,
    h4,
    h5 {
        margin: 0;
        padding: 0;
    }

    /*é›†ä¸­å¤„ç†æ–‡æœ¬åž‚ç›´å‰§ä¸­*/
    #userInfo .user button em {
        font-size: calc(3.5vw * 5);
        width: 14vw;
    }
    #userInfo .user button.quit em {
        font-size: calc(3.5vw * 5);
        width: 7vw;
    }

    /*éŸ³ä¹å¼€å…³*/
    #audioSwitch {
        position: fixed;
        right: 0;
        top: 0px;
        margin: 3vw;
        z-index: 999;
        border-radius: 50%;
        display: none;
        -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
    }
    #audioSwitch {
        width: 9vw;
        height: 9vw;
        overflow: hidden;
        background: url(img/default/audioSwitch.png?rm=3) no-repeat
            rgba(0, 0, 0, 0.7);
        background-size: 100%;
        border: 1px solid rgba(255, 255, 255, 0.7);
    }
    #audioSwitch.stop {
        background-position: left bottom;
    }
    #audioSwitch.on {
        background-position: 0 0;
        animation: reverseRotataZ 6s linear infinite;
        -webkit-animation: reverseRotataZ 6s linear infinite;
    }
    @keyframes reverseRotataZ {
        0% {
            -webkit-transform: rotateZ(0deg);
        }
        100% {
            -webkit-transform: rotateZ(-360deg);
        }
    }

    /*å¤´éƒ¨*/
    .head {
    }
    .head .logo {
        width: 100vw;
        height: 42vw;
        margin: 0vw 0 0vw 0;
        background: url(img/default/logo.png?r=6) center center;
        background-size: 100% auto;
        background-repeat: no-repeat;
        transform: rotate(0deg);
    }

    /*logoæŠ–åŠ¨*/
    .head .logo {
        animation: logoTrembl 5s;
        animation-iteration-count: infinite;
        transform: rotate(-1deg);
    }
    @keyframes logoTrembl {
        0% {
            transform: rotate(-1deg);
        }
        50% {
            transform: rotate(1deg);
        }
        100% {
            transform: rotate(-1deg);
        }
    }

    /*è½¬ç›˜*/
    #transfer {
        width: 90vw;
        height: 90vw;
        margin-left: 3vw;
        background: url(img/default/transferBg.png?r=3);
        background-size: 100% 100%;
        border-radius: 3vw;
        box-shadow: 1px 2px 2px rgba(0, 0, 0, 0.1);
    }
    #transfer ul {
        padding: 4.8vw 0 0 6.8vw;
        display: table;
    }
    #transfer ul li {
        float: left;
        width: 24.2vw;
        height: 24.2vw;
        background: url(img/default/transferGrid.png?r=3);
        background-size: 100% 200%;
    }
    #transfer ul li {
        margin: 2vw 2vw 0 0;
        text-align: center;
        overflow: hidden;
        font-size: 3vw;
    }
    #transfer ul li.hit {
        background-position: 0 100%;
        color: #ff0000;
    }
    #transfer ul li.hide {
        opacity: 0.8;
    }
    #transfer ul li img {
        width: 15vw;
        height: 15vw;
        display: block;
        margin: 1.5vw auto 0.5vw auto;
    }
    #transfer ul #transferBut {
        background-image: url(img/default/transferBut.png);
        background-size: 100% 100%;
    }
    #transfer ul #transferBut.click {
    }

    /*ç”¨æˆ·ä¿¡æ¯*/
    #userInfo {
        display: table;
        width: 93vw;
        padding: 4vw 2vw 2vw 2vw;
        border-radius: 5px;
    }
    #userInfo {
        color: #333;
        text-align: center;
    }
    #userInfo .user {
        margin: 0 0 0 0;
        font-size: 4.5vw;
        color: #333;
    }
    #userInfo .user .noLogin {
        padding-top: 5vw;
    }
    #userInfo .user span {
        display: inline-block;
    }
    #userInfo .user .avatar {
        background-size: cover;
        width: 6vw;
        height: 6vw;
        border-radius: 50%;
        border: 1px solid #ebd46c;
        margin: 0 1vw -1.5vw 0;
    }
    #userInfo .user button {
        border: 0;
        background: #ea2121;
        font-size: 3.5vw;
        color: #fff;
        line-height: 8vw;
        padding: 0 4vw;
        margin: 0 0 0 2vw;
        border-radius: 2vw;
    }
    #userInfo .user button {
        transform: translateY(2vw);
    }
    #userInfo .user button.quit {
        background: #fe7c1e;
    }
    #userInfo .numInfo {
        background: #ffdf7a;
        color: #333;
        display: table;
        margin: 5vw auto auto auto;
        padding: 2vw 5vw;
        border-radius: 4vw;
        font-size: 4vw;
        line-height: 4vw;
    }
    #userInfo .numInfo i {
        display: inline-block;
        float: left;
        background: #ea2121;
        border-radius: 50%;
        width: 2vw;
        height: 2vw;
        margin: 0.9vw 2vw 0 0;
    }
    #userInfo .numInfo span {
        color: #ea2121;
        font-weight: bold;
    }
    #userInfo .noAvatar {
        background-image: url(img/default/noAvatar.png?r=2);
    }

    .mainDiv {
        display: block;
        margin: auto;
        display: table;
    }

    /*ä¸­å¥–æ¦œå•*/
    .drawList {
        margin-top: 4vw;
    }

    #drawList {
        width: 96vw;
        height: 102vw;
        margin: 0;
        border-radius: 0 0 1.5vw 1.5vw;
        overflow: hidden;
        background: #feefcc;
        padding: 1vw 0;
        overflow: hidden;
    }
    #drawList .drawListBody {
        display: table;
        width: 92vw;
    }
    #drawList ul {
        height: 102vw;
        width: 95.5vw;
        overflow: hidden;
    }
    #drawList ul li {
        display: table;
        width: 90vw;
        height: 41px;
        padding: 0 0;
        border-bottom: 1px #e7c09c dashed;
        margin-left: 2vw;
    }
    #drawList ul li span {
        float: left;
        font-size: 14px;
        line-height: 6vw;
        margin-top: 2.5vw;
    }
    #drawList ul li .avatar {
        line-height: 1;
    }
    #drawList ul li .avatar img {
        width: 6vw;
        height: 6vw;
        border-radius: 50%;
        margin-left: 2vw;
    }
    #drawList ul li .nickname {
        margin-left: 5px;
        width: 25vw;
    }
    #drawList ul li .prize {
        width: 38vw;
    }
    #drawList ul li .date {
    }

    /*å†…å®¹å—*/
    .contentBlock {
        margin-bottom: 3vw;
        border: 0 solid #efcb39;
        border-radius: 2vw;
        width: 96vw;
    }
    .contentBlock h3 {
        border-radius: 2vw 2vw 0 0;
        background-image: linear-gradient(#fa531f, #d93318);
    }
    .contentBlock h3 {
        padding: 0 10vw 0 3vw;
        font-size: 4vw;
        color: #ffe800;
        line-height: 11vw;
    }
    .contentBlock .content {
        line-height: 1.8;
        background: #feefcc;
        border-radius: 0 0 1.5vw 1.5vw;
        padding: 3vw;
    }
    .toLottery {
        transform-style: preserve-3d;
    }
    .contentBlock .more {
        float: right;
        margin-right: 4vw;
        color: #fff;
        font-size: 4vw;
        line-height: 11vw;
    }

    #drawList {
    width: 100%;
    height: 200px; /* 容器的固定高度，可以根据需要调整 */
    overflow: hidden;
    position: relative;
}

#drawList ul {
    position: absolute;
    width: 100%;
    animation: slideUp 20s linear infinite; /* 持续时间和动画函数可以根据需要调整 */
}

/* 定义动画关键帧 */
@keyframes slideUp {
    from {
        bottom: -100%; /* 开始时ul完全在容器外部 */
    }
    to {
        bottom: 100%; /* 结束时ul完全移出容器顶部 */
    }
}

}
</style>
