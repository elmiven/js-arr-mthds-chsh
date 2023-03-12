# JS array methods
<details>
  
<summary>srcs:</summary>
<https://www.w3schools.com/jsref/jsref_obj_array.asp>  
<https://www.freecodecamp.org/news/the-javascript-array-handbook/>  
<https://learn.javascript.ru/array-methods#preobrazovanie-massiva>  


</details>


**.valueOf()** *//default method*  
default method of the array return the array.Returns the primitive value of an array

**.isArray()**  
Determine if a value is an array

## Get Elemets: 

**.length**  
property sets or returns the number of elements in an array

**arr[index]**    
**arr[arr.length-1]**   
get elm and get the last element (or you can get elm from the end this way)

**[arr.at](https://github.com/atapas/js-array-at-method)**   
new method allows to access elemnts w negative from the end of arr

**array[Indx][NstdIndx]**  
get nested elemet by indexes 

**[, , , , [, , , "banana"]] = arr**  
get nested array destructuring assignment syntax

**[tomato, mashroom,  , potato="potato"] = [el1, el2, el3]**   
Destructuring assignment w skipped elm and default val

**[first, second] = [second, first]**  
swap elements w destructuring  assignment

[tomato, mashroom, ***...rest***]    
...rest operator

<br>

## Create/Copy/Modify an Arryay:

**const var = [el1, el2, el3]**  
literal syntax  
**const var = new Array (e1,,e2,e3)**  
new keyword //new Array(2) will create empty aray with length 2   

**.of(val1, val2, obj, etc...)**  
creates a new array using any number of elements of any type  
`Array.of(2,false,'test',{'name':'Alex'})`  

**.from(arr-likeObj)**  
converts an arr-like-obj to an arr, so you can perform array methods on it  
`const collection = Array.from(document.getElementsByTagName('li'))` 

**.split(delim)**  
creates Array from the string using delimiters

**.join(delim)**  
join elemts into string with exact separator-delimiter // "," delimiter by defaullt  
**.toString(delim)**  
Convert an array to a string "," - delimiter  

**.slice(start, end)**   
creates shallow copy (*immutable for original*)  
**[...arr]**  
spread operator also creates copy!

**.contact(arr1, arr2?)**  
merge arays (*immutable for original*)  
`const merged = first.concat(second,third);` 

**[...arr1, ...arr2]**   
merge two arays using spread operator

<br>

## Add/Delete/Update Elements:  

**.push(el)** | **.pop(el)** | **.unshift(el)** | **.shift(el)**  
insert/delete elements in/from the array  

**.reverse()**  
reverses the elements' positions! 
(mutate the original array!) 

**[.sort](https://github.com/atapas/js-array-sorting)**(comparator-fn)**  
by default converts elms into strs and compare them based on UTF-16 code units vals 
default sort is ascending  
method accepts an optional comparator functions:  
`numbers.sort((a,b)=>(a-b)); //ascending coparator`   
`numbers.sort((a,b)=>(b-a)); //descending comparator`  

**[.fill](https://github.com/atapas/array-fill-color-cards)**(*value, start, end*)**  
fill elemts of arrray w static vals  
`const colors =['red','blue','green'];`   
`colors.fill('pink',1,3); // ["red", "pink", "pink"]`  
//fills all the arr els with a static value  
//mutate/modifies the original array!  

**.copyWithin(*target, start, end*)**   
Copies array elements within the array, to and from specified positions  
copies array elements to another position in the array  
```
const array1 = ['a', 'b', 'c', 'd', 'e'];  
// Copy to index 0 the element from index 3 to 4  
console.log(array1.copyWithin(0, 3, 5));  
// Expected output: Array ["d", "b", "c", "d", "e"]  
// Copy to index 1 all elements from index 3 to the end  
console.log(array1.copyWithin(1, 3));  
// Expected output: Array ["d", "d", "e", "d", "e"]

```

**[.splice(indx, howmany, item1?, itemX?)](https://www.w3schools.com/jsref/jsref_splice.asp)** *//add, update, and remove*      
The main purpose to delete elms, but it also using to add and replace elms at arbtry positions  
*(mutable for original!)*  
```
names.splice(1,0,'zack');  
//adding an element zack at the index 1 wo deleting any elms  
```
```
const names = ['tom','alex','bob'];  
const deleted = names.splice(2,1,'zack');  
console.log(names); // ["tom", "alex", "zack"] //mutated original arr!  
console.log(deleted);// ["bob"]  
//we are removing one element from the index2(3rd el) and adding a new element, zack.  
The splice() method returns an array with the deleted element, bob.  

```   



<br>

## Iterator methods  
*All the array iterator methods take a function as an argument. You need to specify the logic to iterate and apply in that function.*  
**for** elm **of** arr  
**for(){}**  

**.forEach(func)**  
Calls a function for each array element  
вызывает func для каждого элемента. Ничего не возвращает.  

**.entries()**
Returns a key/value pair Array Iteration Object

**.keys()** 
Returns a Array Iteration Object, containing the keys of the original array


<br>

## TRANSFORMATORS: filter, map, reduce

**.filter()**  
creates a new *shallow copy* of the arr w all the els that satisfies the condition mentioned in the function  
`const femaleStudents = students  
  .filter((element,index)=>{returnelement.gender ==='F';} )`   

**.map()**  
creates a new shallow copy of the arr by iterating through the elements and applying logic we provided in the function as an argument  

**.reduce(fn(ttl, currentVal, currentIndex, arr), initialVal)** | **.reduceRight()**  
Reduce the vals of an array to a single value *(immutable for original!)*  
используются для вычисления единого значения на основе всего массива  
`consttotal =students.reduce((accumulator, student, currentIndex, array)=>{accumulator =accumulator +student.paid;return(accumulator);},0);`  
- accumulator – результат предыдущего вызова этой функции, равен initial при первом вызове (если передан initial),  
- item – очередной элемент массива,  
- index – его позиция,  
- array – сам массив.  


<br>

## SEARCHERS: find, findIndex, includes, indexOf

**.find(fn)**  
returns the first matched el frm the arr that satisfies the condition in the fn.  
`const student = students.find( (element,index)=>{return element.age <30;} );`    
`console.log(student);`    

**.findIndex(fn)**  
returns the index of el we find using the find() method.  
If no els match the condition, the findIndex() method returns -1.  


**.includes('val')**  
find element  
`names.includes('tom');` //returns true   

**.indexOf('val')**| **.lastIndexOf()**  
return index of first occurence of element,  
`names.indexOf('alex');`  // returns 1  

**.some()** 
returns a bool val based on at least one el in the arr passing the condition in the fn. 
```let hasStudentBelow30 = students.some(  
(element, index)=>{returnelement.age <30;});  
console.log(hasStudentBelow30); // true  
```

**.every()**  
detects if every element of the array satisfies the condition passed in the function  
```const atLeastTwoCourses =students.every(  
(elements, index)=>{return elements.courses.length >=2;});  
```

**[.prototype](https://www.w3schools.com/jsref/jsref_prototype_array.asp) ** //property available with all JavaScript objects  
allows you to add properties and methods to arrays  

