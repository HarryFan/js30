```markdown
# [JS30] 第一天：JavaScript 鼓點套件
這堂課的重點是：怎麼播放音效、搞定 CSS 操作、還有聽懂 transitionend 這玩意兒。

## 瞧瞧按鍵去哪兒了
要知道你敲了啥鍵，得先在 `window` 上掛個 `keydown` 的監聽器，這樣一來，按鍵信息就跑不掉啦。

```javascript
window.addEventListener('keydown', (e) => {
  e.key; // 這裡可以知道你按的是哪個字母
  e.keyCode; // 這個則是按鍵的代碼，也挺重要的
});
```

## 敲鼓點，放音樂
用 `<audio>` 標籤放個鼓聲怎麼樣？按下特定鍵時，就讓音樂飛起來。

```html
<audio data-key="65" src="https://pjchender.github.io/JavaScript30/01%20-%20JavaScript%20Drum%20Kit/sounds/boom.wav"></audio>
```

```javascript
const audio = document.querySelector("audio[data-key='65']");
audio.currentTime = 0; // 把音樂倒帶到開頭
audio.play(); // 音樂起飛
```

## 讓元素穿衣服（加 class）
有沒有想過，讓網頁的元素換個裝？用 `classList` 的 `add`、`remove` 或 `toggle` 方法就能輕鬆實現。

```javascript
const block = document.querySelector('.block');

// 對了，這就是給元素穿上、脫下、換裝 'active' 這件衣服的方法
block.classList.add('active');
block.classList.remove('active');
block.classList.toggle('active');
```

## 有感覺的時候就會動
CSS 的 transition 做完動作後，我們可以用 `transitionend` 事件來捕捉這個瞬間。看看是哪個 CSS 屬性讓它動了心。

```javascript
const block = document.querySelector('.block');
block.addEventListener('transitionend', (e) => {
  console.log(e.propertyName); // 這裡會告訴你是哪個 CSS 屬性讓事件發生
});
```
