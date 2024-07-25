function arrayReader(value, result){
    value.forEach(num => {
    //console.log(num);
    if(typeof num != 'object'){
      result.push(num)
    }
    else if(num instanceof Array){
      arrayReader(num, result);
    }
    else{
      resultObj={}
      result.push(resultObj);
      objectReader(num, resultObj)
    }
    })
}
function objectReader(obj, result){
    for(key in obj){
        //console.log(key, obj[key]);
        if(key != null){ //covers null and undefined cases
            //if(obj[key] != null){
                if(typeof obj[key] != 'object'){
                    result[key]=obj[key];
                } else if(obj[key]==null){
                    result[key]=obj[key]
                } else if(obj[key] instanceof Array){
                    resultArr=[];
                    result[key]=resultArr;
                    arrayReader(obj[key],resultArr);
                } else{
                    objectReader(obj[key],result);
                }
            //}
        }
    }
}

function flatten(value) {
  //console.log(value);
  if(value instanceof Array){
    const result=[];
    arrayReader(value, result);
    return result;
  } else if(typeof value != 'object' || value === null){ //for primitive values
    return value;
  } else if(typeof value == 'object'){
    const result = {};
    console.log('objectReader initially chosen');
    objectReader(value, result)
    return result;
  }
 // return 
  
}

// Do not edit the line below.
exports.flatten = flatten;
