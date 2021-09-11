# Welcome to Javascript Cade

## Section 1: Random Numbers
Using node.js, given a random number between 1 and 11 via the following function, return a random number between 1 and 13. 

You may only use `random11()` to generate your random number.

```
const random11 = () => {
    return Math.rand() * 10 + 1;   
}
```
**Challenge:** *Complete this challenge using at most 2 operations*

---

## Section 2: Reverse a String
Using node.js, given a *ascii* string, reverse the string. 

```
console.log(stringReverse('abacus')) // sucaba
console.log(stringReverse('Fief')) // feiF
console.log(stringReverse('Severus Snape')) // epanS sureveS
```

**Challenge:** *Complete this challenge in a single line of code*

---

## Section 3: Digit Adder
Using node.js, given any integer, add up its constituent digits. If the input is not an integer, return undefined.

```
console.log(digitAdder(301)) // 4
console.log(digitAdder(91923)) // 24
console.log(digitAdder("213")) // undefined
```

**Challenge:** *Using the ternary operator and built-in javascript functions, complete this challenge in one line*

---

## Section 4: Second Largest
Given an array of numbers, return the second largest number.

```
    [3, 1, 4] => 3
    [2, 1, 4, 5, 23, 9, 11] => 11
    [8, 18, 213, "bubbles", 6] => 18   
```

**Challenge:** *Write a function to return the n-th largest number instead (indexed from 0)*

```
    nthLargest([2, 0, 1, 4, 4], 2) => 2
    nthLargest([312, 719, 7190], 0) => 7190
    nthLargest([6, 12, 18, 7, 14, 21], 6) => undefined
```
---

## Section 5: Querystring Parsing
Given a url, make an object which contains all the parameters from the query string. Generally a url with a query string will be written in this format

` https://google.com/kittens?name=Muffins&age=6`

Given this, return the object

```
{
    name: "Muffins",
    age: "6"
}
```

**Challenge:** *Make this function able to parse integers and booleans. For example:*

`https://google.com/kittens?age=1&sold=false&name=Mittens`

*should return*

```
{
    age: 1,
    sold: false,
    name: "Mittens"
}
```

---

## Section 6: Days From Now
Write an html page *(no node.js required)* where when you click a button, data is read from an input text box, and the output of the function is returned in the output div.

The function you must write takes one input, a number, and returns the date that many days from now.

**Challenge:** *Write this function so it can handle decimals, too.*

## Section 7: Pick a Card, Any Card
Using Node.js, make two classes: A Card class and a CardDeck class.

### Card
A card has the following properties
```
{
    value: Number,
    suit: String,
    name: String
}
```
The value of a card must be its Blackjack equivalent. For Aces, you can use 1 or 11.

This card should have the following methods

`Card.add(n)`

This should add the current card's value with the input `n`, and return the summed value.

### CardDeck
The card deck class is a collection of Cards. The CardDeck must have the following methods.

`CardDeck.draw()`

This function must return a card and remove it from the collection.

`CardDeck.shuffle()`

This function must return the deck back to 1 of each standard playing card (excluding jokers).

**Challenge:** For the `Card.add` function, allow an ace to be worth both 1 and 11. Furthermore, if both results are under 21, return an array with both results.

```
// let a equal a Seven of Diamonds
// let b equal an Ace of Spades

a.add(b.value) => [8, 18]
b.add(a.value) => [8, 18]
```

---

## Section 8: Fibonacci and Other Sets
Given the set F(0, 1, ...), calculate F(n) where F(n) = F(n-1) + F(n-2).

```
    // 0, 1, 1, 2, 3, 5, 8, 13, ...
    F(0) => 0
    F(1) => 1
    F(2) => 1
    F(3) => 2
    F(7) => 13
    F(9) => 34
    ...
```

**Challenge:** *Create a function which can use any starting set of numbers, not just [0,1], and then returns the resulting value*

```
    // Starting Set 2, 2
    // 2, 2, 4, 6, 10, 16, 26, 42, ...

    F([2, 2], 3) => 6

    // Starting Set 1, 8
    // 1, 8, 9, 17, 26, 43, 69, 112, ...
    F([1, 8], 6) => 69

```

---
## Section 9: Axios API Call and Filtering
Given the following spell API, use Axios to retrieve all of the data.

Once you have all the data, console log an array of all spells which have a spelllevel of "6" and are spells which are druid, and druid only.

> API: https://ck-spells.herokuapp.com/read

### Spell Schema
```
{
    "spellname": String,
    "spelllevel": String,
    "spellschool": String,
    "spellritual": Boolean,
    "spelltags": [String],
    "castingtime": String,
    "spellrange": String,
    "spellcomponents": {
        "componentVerbal": Boolean,
        "componentSomatic": Boolean,
        "componentMaterial": Boolean,
        "componentCosted": Boolean,
        "componentMaterialText": String
    },
    "spellduration": {
        "durationtime": String,
        "concentration": Boolean
    },
    "spelldetails": [String],
    "spellupcast": String,
    "classes": [String]
}
```

To check that you have all the correct spells, visit https://spells.collinkrueger.com and type the following query in the search bar

`z*:druid & l:6`

**Challenge:** *Now log a list of spells which are level 6 and druid spells (this time, the spells can also belong to other classes as well).*

*To check your work, use this query at the link above: `z:druid & l:6`*

---
## Section 10: Spell Filtering
Given the API from section 9, retrieve the data via axios, and write the following function.

Given the following signature `function filterData(data, data_match)`, write a function which takes in the spell data from the api, and an object, and returns all the spells which fit all the criteria.

For example:
```
    {spelllevel: "4", spellschool: "Abjuration"}
    // equivalent query: l:4 & school:Abjuration

    {spellschool: "Necromancy", spellritual: false}
    // equivalent query: school:Necromancy & rit:false

    {spellname: "Bones of the Earth"}
    // should only return Bones of the Earth Spell
    
    {spellname: "Bones of the Earth", spellschool: "Evocation"}
    // will return an empty array, because no such spell exists.
```

**Challenge:** Create a second function with the following signature `function filterData(data, data_match, data_exclude)`. This function works the same way as the previous function, but data_exclude is a new parameter which is a object which you exclude from the filter. For example:

```
    data_match: {spellschool: "Necromancy"}
    data_exclude: {spelllevel: "6"}
    // this will return all necromancy spells which aren't level 6
    // equivalent query: school:Necromancy & !l:6
```

---
## Open Project: Portfolio
Using HTML/CSS/JavaScript, create a portfolio, either for yourself or a fictional person. The portfolio should have at least the following features.

- Navigation Bar to different pages
- At least 3 different pages
- Multiple articles, separated accordingly
- Fully Styled
- Three JavaScript Events
- Contact Form (doesn't need to submit to anywhere)
- Multiple Classes and ID tags.

**Challenge:** Create a carousel of images. You might want to look into jQuery. The Internet is your tool. Feel free to research, but don't just copy and paste code.

