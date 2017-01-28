# jsClock

[live link](https://skdkim.github.io/jsClock/)

![ss1](https://github.com/skdkim/jsClock/blob/master/images/clock1.jpg)

## About

JS Clock is a clock made of Vanilla JS, HTML, and CSS.

It uses Javascript to manipulate the CSS inorder to make clock hands move in realtime.

## Code Sample

```javascript
    const secondHand = document.querySelector('.second-hand');
    const minuteHand = document.querySelector('.min-hand');
    const hourHand = document.querySelector('.hour-hand');

    let setDate = () => {
      const now = new Date();
      const seconds = now.getSeconds();
      const minutes = now.getMinutes();
      const hours = now.getHours();

      const secondsDeg = (seconds / 60) * 360 + 90;
      
      // the extra addition of ((seconds/60)*6) here is to allow the 
      // minute hand to lean towards the weighted time depending on the seconds
      const minutesDeg = (minutes / 60) * 360 + ((seconds/60)*6) + 90;
      
      // the extra addition of ((minutes/60)*30) here is to allow the 
      // hour hand to lean towards the weighted time depending on how close
      // the current time is to the next hour
      const hoursDeg = (hours / 12) * 360 + ((minutes/60)*30) + 90;

      secondHand.style.transform = `rotate(${secondsDeg}deg)`;
      minuteHand.style.transform = `rotate(${minutesDeg}deg)`;
      hourHand.style.transform = `rotate(${hoursDeg}deg)`;
    }

    setInterval(setDate, 1000);
```
