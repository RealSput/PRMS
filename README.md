# PRMS
A SPWN library for creating asynchronous trigger functions

# Usage
```rs
extract import "prms.spwn"

// create counter
i = counter()
i.display(45, 45)

// create two promises (can return a value without stopping the entire macro)
pr1 = promise((resolve) {
    wait(1)
    resolve('promise 1')
    i += 5
})
pr2 = promise((resolve) {
    wait(2)
    resolve('promise 2')
    i += 10
})

res = await([pr1, pr2], (result, group) {
    // compile-time code goes here
    $.print(result) // prints results of all promises
    $.print(group) // prints group of current context 
})

// runtime code goes here (to be ran after all promises resolve)
wait(1)
i += 100
```
