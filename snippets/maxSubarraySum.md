---
title: maxSubarraySum
tags: array,intermediate,recursion
firstSeen: 2021-12-05 T16:37:00-04:00
---

Explain briefly what the snippet does.

- This snippet takes an array of numbers and returns the highest sum from a sub array from the given array 
- there is a checkmax and checkindex array where checkmax is for storing sums of all possible sub array sums
- checkindex is used to store the indexes of the checked subarray sum, if it is already checked then it just skips for the next recursion
- the checkmax array has no sorted elements, so we just sort them and print the last value

```js

let checkmax=[];
let checkindex=[];
function ifdontexist(given)
{
    let sum=given.reduce((a,b)=>a+b,0);
    if(!checkmax.includes(sum))
    {
	checkmax.push(sum);
    }
}

function iterations(given,start,end){
    if(!checkindex.includes([start,end]))
    {
	checkindex.push([start,end]);
	ifdontexist(given.slice(start,end+1));
    }
    if(start<end)
    {
	iterations(given,start+1,end);
	iterations(given,start,end-1);
    }
}
function maxSubarraySum(nums)
{
    iterations(nums,0,nums.length);
    console.log(checkmax.sort(function(a, b) { return a > b ? 1 : -1})[checkmax.length-1]);
}

```

```js

maxSubarraySum([-1.3,2.7,5,0]);//Expected output 7.7

```
