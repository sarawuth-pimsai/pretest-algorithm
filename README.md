# Algorithm
## Pair Array Number
### Example
#### Inputs
```
array1 = [0, 2, 4, 5, 6, 5]
const array2 = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 1, 2, 3, 4]
const sum = 1
```
#### Output
```
[ [ 0, 1 ] ]
```
#### Coding
```javascript
const trans = (arr) => {
    let data = {}
    let max = arr[0];
    let min = arr[0];
    for(let i = 0; i<arr.length; i++) {
        const key = arr[i]
        if(!data[key]){
            data[key] = [key]
        } else {
            data[key].push(key)
        }
        if(key > max) {
            max = key
        } 
        if(key < min) {
            min = key
        }
    }
    return {min, max, data}
}
const pair = (array1, array2, sum) => {
    let result = []
    const {min, max, data} = trans(array2)
    for(i = 0; i < array1.length; i++){
        const index = sum - array1[i]
        if(max < index || index < min || index > sum || index < 0) continue
        // if(data[index]) result.push([array1[i], data[index][0]])
        if(data[index]) {
            for(let j = 0; j < data[index].length; j++) {
                result.push([array1[i], data[index][j]])
            }
        }
    }
    return result
}
const array1 = [0, 2, 4, 5, 6, 5]
const array2 = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 1, 2, 3, 4]
const sum = 1
const result = pair(array1, array2, sum)
console.log(result)
```
