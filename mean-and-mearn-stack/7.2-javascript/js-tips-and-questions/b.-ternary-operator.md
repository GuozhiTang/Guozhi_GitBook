# b. Ternary Operator

* One point which is needed to know:

```javascript
var isMember = false;
console.log("Current fee: " + isMember ? "$2.00" : "$10.00");
```

* For this example, we want to show that if a user is a member, then the fee is $2, otherwise, the fee is $10.
* However, if we write like this, the result is `"$2.00"`.
* It is because `"?"` operator's piriority is lower that `"+"`, so that the actural code is:

```javascript
"Current fee: false" ? "$2.00" : "$10.00"
```

* In Javascript, all the strings are true.
* \(if it is not `false`, `0`, `undefined`, `NaN`, `""` or `null`\)

