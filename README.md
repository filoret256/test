# test task
test to Make function 

function must return arrays of numbers from first argument that in summ must be as second argument
  first argument array if numbers
  second argument is summ number
  return array of number arrays

well at interview that task is simple you need just to return of 2 numbers that at summ will be a second argument
but i go futher ( it tooks about hour :( )
function return more arrays if second argument(summ) can contains more than 2 numbers

const tt = (arr,n) => {
  let result = [];
  let inerArray = [];
  let searchArray = [];
  arr.forEach(el => {
    inerArray.push([el]);
    });
  
  let moreSearch = [];


  while (inerArray.length >0){
    
    moreSearch.length = 0;
    
    for (let y = 0; y < inerArray.length; y++) {
      
      searchArray.length = 0;
      arr.forEach(el => searchArray.push(el));
      inerArray[y].flat(Infinity).forEach( e=> searchArray = searchArray.filter( f => f!=e ) )

      for(let x = 0; x < searchArray.length; x++) {
      
        let sumA = 0, sumB = searchArray[x];

        inerArray[y].flat(Infinity).forEach( e => sumA += e );

        if ( sumA + sumB === n ) result.push( [inerArray[y], searchArray[x]].flat(Infinity) );
        
        if ( sumA + sumB < n ) moreSearch.push( [inerArray[y] , searchArray[x] ].flat(Infinity) );
      }
    }
    
    inerArray.length = 0;
    
    moreSearch.forEach( e=>{
      inerArray.push(e);
    });
            

  }
  
  let final = [];
  result.forEach(e => final[ e.sort().join('') ] = e);
  return final.filter(e => e!=undefined);
}

console.log( tt([1,2,3,4,5],10) );


