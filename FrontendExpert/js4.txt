class EventTarget {
  // Write your code here.
  constructor(){
    this.listeners={}
  }
  addEventListener(name, callback) {
    if(!this.listeners.hasOwnProperty(name)){
      this.listeners[name]=new Set([callback]) //same event listener(event listeners of same name) can only be added many times, but only affect once. remaining have no effect
    } else {
      this.listeners[name].add(callback); //allows multiple events listeners for same event(name)
    }
  }

  removeEventListener(name, callback) {
    this.listeners[name]?.delete(callback);//checks if name exists, otherwise results to undefined instead of throwing error. else deletes
  }

  dispatchEvent(name) {
    this.listeners[name]?.forEach(callback => {
      callback();
    });
  }
}

// Do not edit the line below.
exports.EventTarget = EventTarget;
