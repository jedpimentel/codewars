Leon said to do a codewars 'rankup' challenge each day, and to go through these:

https://github.com/bpesquet/thejsway

https://medium.com/the-node-js-collection/modern-javascript-explained-for-dinosaurs-f695e9747b70

https://zellwk.com/blog/crud-express-mongodb/

TODO: organize this

https://www.codewars.com/kata/52742f58faf5485cae000b9a/train/javascript
```js
function formatDuration (seconds) {
  if(seconds == 0) {
    return 'now'
  }
  const minuteDuration = 60
  const hourDuration = minuteDuration * 60
  const dayDuration = hourDuration * 24
  const yearDuration = dayDuration * 365
  
  let years = Math.floor(seconds / yearDuration)
  seconds %= yearDuration
  
  let days = Math.floor(seconds / dayDuration)
  seconds %= dayDuration
  
  let hours = Math.floor(seconds / hourDuration)
  seconds %= hourDuration
  
  let minutes = Math.floor(seconds / minuteDuration)
  seconds %= minuteDuration
  
  function pluralize(number, string) {
    if (number == 0) {
      return '';
    }
    if (number == 1) {
      return number + ' ' + string;
    }
    if (number > 1) {
      return number + ' ' + string + 's';
    }
  }
    
    let raw = [pluralize(years, 'year'), pluralize(days, 'day'), pluralize(hours, 'hour'), pluralize(minutes, 'minute'), pluralize(seconds, 'second')]
    let clean = []
    while(raw.length) {
      let entry = raw.shift()
      if(entry) {
        clean.push(entry)
      }
    }
    let last = clean.pop()
    if(clean.length == 0) {
      return last
    }
    return clean.join(', ') + ' and ' + last
    
}
```
## Coordinates Validator
https://www.codewars.com/kata/5269452810342858ec000951
```js
function isValidCoordinates(coordinates){
  if (coordinates.match(/[a-z]/i)) {
    return false
  }
  if(coordinates.includes('- ')) {
    return false
  }
//   let arr = coordinates.split(' ').join('').split('N').join('').split('E').join('').split(',')
  let arr = coordinates.split(' ').join('').split(',')
  if(arr.length > 2) {
    return false
  }
  
  let latitude = Number(arr[0])
  let longitude = Number(arr[1])
  
  console.log(coordinates)
  console.log(arr)
  console.log(arr[0], latitude)
  console.log(arr[1], longitude)
  if(latitude < -90 || 90 < latitude) {
    console.log('lat sux')
    return false
  }
  if(longitude < -180 || 180 < longitude) {
    console.log('lon sux')
    return false
  }
  if(isNaN(latitude) || isNaN(longitude)) {
    console.log('is nan, returning false')
    return false
  }
  console.log('is valid')
  return true;
}
```
