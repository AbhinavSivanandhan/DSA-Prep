Array functions
Array.prototype.myMap = function (callback) {
    const results=[];
    for(let i=0;i<this.length;i++){
      results.push(callback(this[i],i,this));
    }
    return results;
  };
  
  Array.prototype.myFilter = function (callback) {
    const results=[];
    for(let i=0;i<this.length;i++){
      if(callback(this[i],i,this) === true){
        results.push(this[i]);
      }
    }
    return results;
  };
  
  Array.prototype.myReduce = function (callback, initialValue) {
    let accumulator = initialValue;
    for(let i = 0; i<this.length; i++){
      if ( i === 0 && initialValue === undefined) {
        accumulator=this[i];
      } else {
      accumulator=callback(accumulator, this[i], i, this);
      }
    }
    return accumulator;
  };
  