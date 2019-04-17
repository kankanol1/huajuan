# 怦然心动

#### 引入jQuery库，
```
    <script src="./js/jquery-1.12.4.js"></script>

```
也可不引入，自己编写动画函数.

#### 绘制移动svg图片
```
    heartL = [];
    for (let i=0;i<10;i++){
        let oImg = document.createElement('img');
        oImg.src = imgL[i%ingL.length];
        oImg.calssName = 'fImg';
        oImg.style.left = Math.random() * cW + "px";
        oImg.style.top = Math.random() * cH + "px";
        oImg.style.position = 'fixed';
        oImg.style.width = 50+ 'px';
        oImg.style.width = 50 + 'px';
        oImg.style.zIndex = 10;
        oImg.setAttribute('dataX',(0.5-Math.random()) * speed );
        oImg.setAttribute('dataY',(0.5-Math.random()) * speed );

        heartL.push(oImg);
        document.querySelector('body').appendChild(oImg);
    }
```
#### 然后设置动画函数
```
  setInterval(function(){
        for(let i=0;i<heartL.length;i++){
            // console.log(parseFloat(heartL[i].style.left),parseFloat(heartL[i].getAttribute('dataX')));
            heartL[i].style.left =  parseFloat(heartL[i].style.left) + parseFloat(heartL[i].getAttribute('dataX'))+ 'px';
            heartL[i].style.top =  parseFloat(heartL[i].style.top)+ parseFloat(heartL[i].getAttribute('dataY')) + 'px';
            if(parseFloat(heartL[i].style.left)<0 || parseFloat(heartL[i].style.left)>cW){
                heartL[i].setAttribute('dataX',- parseFloat(heartL[i].getAttribute('dataX')));
            }
            if(parseFloat(heartL[i].style.top)<0 || parseFloat(heartL[i].style.top)>cH){
                heartL[i].setAttribute('dataY',- parseFloat(heartL[i].getAttribute('dataY')));
            }

        }

    },100/6);
```
#### 怦然心动样式
```
/*----------------------------------怦然心动-------------------------------*/
@keyframes kankan {
    0% {width: 30px;}
    25% {width: 70px;}
    100% {width: 30px;}
}

@-webkit-keyframes kankan /* Safari 与 Chrome */ {
    0% {width: 30px;}
    25% {width: 70px;}
    100% {width: 30px;}
}
.change {
    animation: kankan 1s;
    -webkit-animation: kankan 1s;
    animation-iteration-count: infinite;

}
```
