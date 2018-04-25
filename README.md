This is not gonna be fun.

I'd rather be working on my game.

TODO: organize this

https://www.codewars.com/kata/52742f58faf5485cae000b9a/train/javascript

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
