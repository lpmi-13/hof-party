# HOF Party!

Lots of times, the idea of first class functions and Higher Order Functions are taught in a very technical and theoretical way. As a complement, this repo aims to give learners a way to actually practice composing these functions themselves.

Things that are unfamiliar are difficult, and things that are familiar are easy.

So let's get familiar!

## Web interface

This is a single page react application that shows a prompt like:
```
// write a function called `partial` that makes 
// the following snippet work
const add = ( a, b ) => a + b

const add5 = partial( add, 5 )
add5( 4 ) // 9
```

and the user has an input to write out the required higher order function like:
```
const partial = ( fn, a ) => (b) => fn( a, b )
```

the interface will give feedback on whether the function was written correctly, and what the output was.

### extended practice

The next step is where things get more interesting.

Instead of just using addition or subtraction, we can start to move into more meaningful concepts like "put something inside of a house"...obviously it will be a house object here...but you get the idea.

We would see something like:
```
// write a function called takeItToTheHouse that makes
// the following snippet work

let House = class House {
  constructor(price, rooms) {
    this.price = price;
    this.rooms = rooms;
  }
}

const putInsideHouse = (a, b) => { return new House( a, b ) }

const mcMansion = takeItToTheHouse(putInsideHouse, 1000000)
mcMansion(['bedroom', 'bedroom', 'bedroom', 'bedroom', 'kitchen', 'kitchen', 'dining room'])

// House {
//  price: 1000000,
//  rooms:
//   [ 'bedroom',
//     'bedroom',
//     'bedroom',
//     'bedroom',
//     'kitchen',
//     'kitchen',
//     'dining room' ] }
```

the beauty part is that this new function has the exact same function signature as the previous one:
`const takeItToTheHouse = ( fn, a ) => (b) => fn( a, b )`

TO BE DETERMINED:
The best way to play around with different types of higher order functions
and how to get the learners to manipulate them in very small ways while still
practicing creating them, based on more meaningful terms than add/subtract/etc

possible options:
- put in a house
- adding a greeting at the beginning
- make 5 copies of a thing



another example:

I can design the curried function of volume to be this:

```
function volume(l) {
    return (w, h) => {
        return l * w * h
    }
}
```

So it can be called like this:

```
const hCy = volume(70);
hCy(203,142);
hCy(220,122);
hCy(120,123);
```
or

```
volume(70)(90,30);
volume(70)(390,320);
volume(70)(940,340);
```

THIS IS NICE, SINCE IT'S A REAL WORLD IDEA...NEED TO FIND MORE/BETTER EXAMPLES
INVOLVING PEOPLE

and here's an example that's basically a react higher order component
```
> const wrapped = ( a, b) => { return `<${a}>${b}</${a}>`}
> const partial = (fn, a) => (b) => fn(a,b)
undefined
> const divvit = partial(wrapped, `div`)
undefined
> divvit('this is inside a div')
'<div>this is inside a div</div>'

