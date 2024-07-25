//a debounce function is a higher order function. that is, it'll return another function
//that returned function is a transformed version of the callback function
//it works the same as callback function except it leaves a delay  
//immediate will let the function run without delay for the first call alone
//if we call the function once, it starts the timer, but if function is called again, then it resets the delay
function debounce(callback, delay, immediate = false) {
    let timerID; //a closure (as it is accessible by iner function). useful to clear timer in next call
  
    //inner function has to be anonymous function and not arrow function. since arrow functions don't support this binding. if we try to use arrow here, it'll pass entire debounce function as this binding. we don't want that
    //so using anonymous function will make sure that each call to the debounced function gets its own 'this' context below
    return function(...args){ //rest parameter. gets array of args, i.e., any and all args, and then passes them as individual parameters to the callback function
      clearTimeout(timerID); // doesn't make it null or undefined. just stops timer from running
      const shouldCallImmediately = timerID == null && immediate;
      if(shouldCallImmediately) {
        callback.apply(this, args);
      }
      //timerID = setTimeout(callback, delay);this line doesn't help us as it 1) doesn't support arguments and 2) loses the this binding and instead points to global scope
      timerID = setTimeout(() => {
        if (!immediate){
        //callback(...args); but doing this will still leave out this binding
        callback.apply(this, args); //call() or apply() can be used to create this binding (interesting read:https://medium.com/@omergoldberg/javascript-call-apply-and-bind-e5c27301f7bb)
      //...args is not needed as .apply() takes it in as an array anyway
        }
        timerID = null;
      }, delay);
    };
  }
  //The debounce function helps control how often a specific function (callback) is executed. It does this by setting a timer for a certain period (delay). If the function is called again before this time is up, the timer is reset. This means the function only runs after the delay has passed without any new calls. There's also an option (immediate) to make the function run immediately the first time it's called, but then wait for the delay on subsequent calls.
  // Do not edit the line below.
  exports.debounce = debounce;
  