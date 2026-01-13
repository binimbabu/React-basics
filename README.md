state used to update the user interface.

const [advice, setAdvice] = useState("");

Here 'advice' is the value and setAdvice is the setter.

useEffect takes 2 arguments first is the function which need to be loaded when the component is to be loaded and second argument is the dependency array (below is empty [] ).

  useEffect(function () {
    getAdvice();
  }, []);


props are parameters to the function

<Message count={count} />

count is the name we use to pass as props (<Message count={count} />) and function Message accepts argument as props.

function Message(props) {
  return (
    <p>
      You have read <strong>{props.count}</strong> pieces of advice
    </p>
  );
}

Example:-

import { useEffect, useState } from "react";

export default function App() {
  const [advice, setAdvice] = useState("");
  const [count, setCount] = useState(0);

  async function getAdvice() {
    const res = await fetch("https://api.adviceslip.com/advice");
    res.json().then((data) => {
      setAdvice(data.slip.advice);
      setCount((c) => c + 1);
    });
  }
  useEffect(function () {
    getAdvice();
  }, []);
  return (
    <div>
      <h1>{advice}</h1>
      <button onClick={getAdvice}>Get Advice</button>
      <Message count={count} />
    </div>
  );
}

function Message(props) {
  return (
    <p>
      You have read <strong>{props.count}</strong> pieces of advice
    </p>
  );
}

1. What is React?
React is a front-end and open-source JavaScript library which is useful in developing user interfaces specifically for applications with a single page. It is helpful in building complex and reusable user interface(UI) components of mobile and web applications as it follows the component-based approach.

The important features of React are:

It supports server-side rendering.
It will make use of the virtual DOM (The Virtual DOM (VDOM) is a lightweight, in-memory representation of the actual browser DOM.
It’s basically a JavaScript object that describes what the UI should look like.) rather than real DOM (Data Object Model) as RealDOM manipulations are expensive.
It follows unidirectional data binding or data flow.
It uses reusable or composable UI components for developing the view.

2. What are the advantages of using React?
MVC is generally abbreviated as Model View Controller.

Use of Virtual DOM to improve efficiency: React uses virtual DOM to render the view. As the name suggests, virtual DOM is a virtual representation of the real DOM. Each time the data changes in a react app, a new virtual DOM gets created. Creating a virtual DOM is much faster than rendering the UI inside the browser. Therefore, with the use of virtual DOM, the efficiency of the app improves.
Gentle learning curve: React has a gentle learning curve when compared to frameworks like Angular. Anyone with little knowledge of javascript can start building web applications using React.
SEO friendly: React allows developers to develop engaging user interfaces that can be easily navigated in various search engines. It also allows server-side rendering, which boosts the SEO of an app.
Reusable components: React uses component-based architecture for developing applications. Components are independent and reusable bits of code. These components can be shared across various applications having similar functionality. The re-use of components increases the pace of development.
Huge ecosystem of libraries to choose from: React provides you with the freedom to choose the tools, libraries, and architecture for developing an application based on your requirement.


3. What are the limitations of React?
The few limitations of React are as given below:

React is not a full-blown framework as it is only a library.
The components of React are numerous and will take time to fully grasp the benefits of all.
It might be difficult for beginner programmers to understand React.
Coding might become complex as it will make use of inline templating and JSX.


What is a Single Page Application (SPA)?

A Single Page Application is a web app that loads only one HTML page (index.html) from the server, and then dynamically updates the page content in the browser using JavaScript — without reloading the entire page.

So, instead of the browser fetching new HTML pages for every link or action, the JavaScript code changes what’s shown on the page instantly.


why is react Single page application


A Single Page Application is a web app that loads only one HTML page (index.html) from the server, and then dynamically updates the page content in the browser using JavaScript — without reloading the entire page.
So, instead of the browser fetching new HTML pages for every link or action, the JavaScript code changes what’s shown on the page instantly.


Why React is Used for SPAs

React was designed to build dynamic, client-side applications that run inside a single page.

Here’s why:

1. Virtual DOM Updates Only What’s Needed

React keeps a lightweight copy of the DOM called the Virtual DOM.
When state changes, React:

Compares (diffs) the new Virtual DOM with the previous one

Updates only the changed parts in the real DOM
→ Fast and efficient UI updates without reloading the page.

2. Client-Side Routing

React apps use libraries like React Router.
When you navigate (e.g., /about, /profile), React Router:

Changes the URL in the browser (using history.pushState)

Loads the new component
👉 No network request for a new page, so the app feels instant.

3. Single HTML Entry Point

Every React app (created with Vite, Next.js, or Create React App) starts with a single file:


<!-- index.html -->
<div id="root"></div>


4. State Management

React maintains app state (data) in memory using hooks like:


const [count, setCount] = useState(0);

When you change data, React re-renders just the affected components.
No page refresh is needed to reflect changes.

5. Better UX (User Experience)

Because only parts of the UI update:

Navigation is faster

The app feels like a native app

No flickering or full reloads




React

React is extremely popular declarative component based state driven JavaScript library for building user interfaces created by Facebook.
Components are the building blocks of user interfaces in React such as buttons, input fields, search bars and so on. react takes the components are draw the webpage.
JSX describes how components look like and how they work using a declarative syntax called JSX. React tells how a component should look like based on current data and state. JSX a syntax that combines HTML, CSS , JavaScript as well as referencing other components.
React does not touches DOM. But DOM is interacted using state driven.
State render UI and if we click something on the webpage say a button click then the state is updated and state re-renders UI.
React reacts to state changes by re-rendering the UI.
React is a library because React is only a view layer. Need to pick multiple external libraries to build a complex application (eg: for routing or data fetching). Complete framework like Nextjs has external libraries.
React renders components on a webpage based on the current state. Keeps the Ui sync with state by re-rendering when the state changes.






   <script
      src="https://unpkg.com/react@18/umd/react.development.js"
      crossorigin
    ></script>

here React is called


Below ReactDOM is used

 <script
      src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"
      crossorigin
    ></script>


In the below code portion

React.createElement("header", null, `Hello React! It's ${time}`)


header is the element to be created , props is given as null, The content inside the header tag is 'Hello React! It's ${time}'


React.useEffect(function () {
          setInterval(function () {
            setTime(new Date().toLocaleTimeString());
          }, 1000);
        }, []);


the above code is to update the date in header tag in UI automatically every 1 second by the use of useEffect

Full Example of React and ReactDOM


<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Hello React!</title>
  </head>
  <body>
    <div id="root"></div>

    <script
      src="https://unpkg.com/react@18/umd/react.development.js"
      crossorigin
    ></script>
    <script
      src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"
      crossorigin
    ></script>

    <script>
      function App() {
        // const time = new Date().toLocaleTimeString();
        const [time, setTime] = React.useState(new Date().toLocaleTimeString());

        React.useEffect(function () {
          setInterval(function () {
            setTime(new Date().toLocaleTimeString());
          }, 1000);
        }, []);

        return React.createElement("header", null, `Hello React! It's ${time}`);
      }

      const root = ReactDOM.createRoot(document.getElementById("root"));
      root.render(React.createElement(App));
    </script>
  </body>
</html>




Vite is a modern build tool that contains a template for setting up react application. Vite is extremely fast hot module replacement and bundling.








JavaScript



Throttle in JavaScript

Throttle ensures a function is executed at most once in a specified time interval, even if it is triggered multiple times.
Useful for performance optimization when events fire repeatedly, such as:

scroll

resize

mousemove

keypress

📌 Example of Throttle Implementation
function throttle(fn, delay) {
  let last = 0;

  return function (...args) {
    const now = Date.now();
    if (now - last >= delay) {
      last = now;
      fn.apply(this, args);
    }
  };
}

📌 Usage Example (Throttle scroll event)
function handleScroll() {
  console.log("Scrolling...", Date.now());
}

window.addEventListener("scroll", throttle(handleScroll, 1000));

✔ Behavior

Even if the user scrolls continuously, handleScroll runs once every 1 second.





Debounce in JavaScript

Debounce ensures a function is executed only after a specified period of inactivity.
It prevents a function from running too often and waits until the event stops firing.

📍 Common use cases

Search-as-you-type input box

Auto-saving form

Window resize

Button click prevention

✅ Debounce Implementation
function debounce(fn, delay) {
  let timer;

  return function (...args) {
    clearTimeout(timer); // reset timer on every call
    timer = setTimeout(() => {
      fn.apply(this, args); // execute when no activity happens
    }, delay);
  };
}

🔧 Usage Example
function handleSearch(e) {
  console.log("Searching for:", e.target.value);
}

const debouncedSearch = debounce(handleSearch, 500);

document.getElementById("search").addEventListener("input", debouncedSearch);




Difference between var, let, and const in JavaScript:

🟦 var
Characteristics:

Function scoped

Can be redeclared and updated

Hoisted (initialized with undefined during hoisting)

Can cause bugs in modern code due to scope issues

Example:
var x = 10;
var x = 20;  // Redeclaration allowed
console.log(x); // 20

Hoisting behavior:
console.log(a); // undefined
var a = 5;

🟩 let
Characteristics:

Block scoped ({ })

Can be updated, but cannot be redeclared in the same scope

Hoisted but not initialized (Temporal Dead Zone before declaration)

Example:
let y = 10;
y = 20;     // Update allowed
// let y = 30;  // Redeclaration NOT allowed (in same scope)
console.log(y); // 20

Hoisting behavior:
console.log(b); // ReferenceError (Temporal Dead Zone)
let b = 15;

🟥 const
Characteristics:

Block scoped

Cannot be updated or redeclared

Must be initialized at the time of declaration

Objects and arrays declared as const can be mutated, but not reassigned

Example:
const z = 50;
// z = 100;  // ❌ Not allowed
console.log(z); // 50

Mutating arrays/objects with const:
const arr = [1, 2, 3];
arr.push(4);     // Allowed (mutation)
console.log(arr); // [1, 2, 3, 4]

// arr = [5, 6];  // ❌ Reassignment not allowed

📌 Key Differences Summary
Feature	var	let	const
Scope	Function scope	Block scope	Block scope
Redeclaration	✔ Allowed	❌ Not allowed	❌ Not allowed
Reassignment	✔ Allowed	✔ Allowed	❌ Not allowed
Hoisting	Yes (initialized with undefined)	Yes (TDZ)	Yes (TDZ)
Must initialize	❌ No	❌ No	✔ Yes
🧠 Example illustrating scope difference:
if (true) {
  var p = 10;
  let q = 20;
  const r = 30;
}

console.log(p); // 10 (accessible outside block)
console.log(q); // ReferenceError
console.log(r); // ReferenceError

🎯 When to use what?
Use	Keyword
Variables that need reassignment	let
Constant values or objects/arrays not reassigned	const
Avoid (legacy code support only)	var






Closures



A closure is formed when an inner function remembers variables from its outer function even after the outer function has returned.

Closures allow:

Data privacy

Function factories

Maintaining state

Example
function outer() {
  let count = 0;

  function inner() {
    count++;
    console.log(count);
  }

  return inner;
}

const counter = outer(); // outer() returns inner()
counter(); // 1
counter(); // 2
counter(); // 3

How it works

Even though outer() has finished executing, the variable count is kept alive, because inner() uses it.








Hoisting



Hoisting means JavaScript moves function declarations and variable declarations to the top of their scope during the compile phase.

But:

var is hoisted but initialized with undefined

let and const are hoisted but not initialized (Temporal Dead Zone)

Function declarations are fully hoisted

Function expressions are NOT fully hoisted

Example 1: var hoisting
console.log(a); // undefined
var a = 10;


Reason:

var a;     // hoisted
console.log(a);
a = 10;

Example 2: let / const hoisting (TDZ)
console.log(b); // ❌ ReferenceError
let b = 20;


b exists but is in the Temporal Dead Zone until initialization.

Example 3: Function declaration hoisting
greet(); // Works

function greet() {
  console.log("Hello");
}


Function declarations are fully hoisted.

Example 4: Function expression not hoisted
sayHi(); // ❌ TypeError
var sayHi = function() {
  console.log("Hi");
};






Currying


Currying transforms a function with multiple arguments into a sequence of functions, each taking one argument.

Example:
f(a, b) → f(a)(b)

Used for:

Reusability

Function composition

Partial application

Example
function multiply(a) {
  return function(b) {
    return a * b;
  };
}

const double = multiply(2);
console.log(double(5)); // 10

const triple = multiply(3);
console.log(triple(5)); // 15

Arrow function version
const add = a => b => c => a + b + c;

console.log(add(1)(2)(3)); // 6

Practical example (currying for reusable filters)
const matchAge = minAge => user => user.age >= minAge;

const isAdult = matchAge(18);

console.log(isAdult({ name: "John", age: 20 })); // true
console.log(isAdult({ name: "Amy", age: 16 })); // false











Destructuring Objects and Arrays in JavaScript



const data = [
  {
    id: 1,
    title: "The Lord of the Rings",
    publicationDate: "1954-07-29",
    author: "J. R. R. Tolkien",
    genres: [
      "fantasy",
      "high-fantasy",
      "adventure",
      "fiction",
      "novels",
      "literature",
    ],
    hasMovieAdaptation: true,
    pages: 1216,
    translations: {
      spanish: "El señor de los anillos",
      chinese: "魔戒",
      french: "Le Seigneur des anneaux",
    },
    reviews: {
      goodreads: {
        rating: 4.52,
        ratingsCount: 630994,
        reviewsCount: 13417,
      },
      librarything: {
        rating: 4.53,
        ratingsCount: 47166,
        reviewsCount: 452,
      },
    },
  },
  {
    id: 2,
    title: "The Cyberiad",
    publicationDate: "1965-01-01",
    author: "Stanislaw Lem",
    genres: [
      "science fiction",
      "humor",
      "speculative fiction",
      "short stories",
      "fantasy",
    ],
    hasMovieAdaptation: false,
    pages: 295,
    translations: {},
    reviews: {
      goodreads: {
        rating: 4.16,
        ratingsCount: 11663,
        reviewsCount: 812,
      },
      librarything: {
        rating: 4.13,
        ratingsCount: 2434,
        reviewsCount: 0,
      },
    },
  },
  {
    id: 3,
    title: "Dune",
    publicationDate: "1965-01-01",
    author: "Frank Herbert",
    genres: ["science fiction", "novel", "adventure"],
    hasMovieAdaptation: true,
    pages: 658,
    translations: {
      spanish: "",
    },
    reviews: {
      goodreads: {
        rating: 4.25,
        ratingsCount: 1142893,
        reviewsCount: 49701,
      },
    },
  },
  {
    id: 4,
    title: "Harry Potter and the Philosopher's Stone",
    publicationDate: "1997-06-26",
    author: "J. K. Rowling",
    genres: ["fantasy", "adventure"],
    hasMovieAdaptation: true,
    pages: 223,
    translations: {
      spanish: "Harry Potter y la piedra filosofal",
      korean: "해리 포터와 마법사의 돌",
      bengali: "হ্যারি পটার এন্ড দ্য ফিলোসফার্স স্টোন",
      portuguese: "Harry Potter e a Pedra Filosofal",
    },
    reviews: {
      goodreads: {
        rating: 4.47,
        ratingsCount: 8910059,
        reviewsCount: 140625,
      },
      librarything: {
        rating: 4.29,
        ratingsCount: 120941,
        reviewsCount: 1960,
      },
    },
  },
  {
    id: 5,
    title: "A Game of Thrones",
    publicationDate: "1996-08-01",
    author: "George R. R. Martin",
    genres: ["fantasy", "high-fantasy", "novel", "fantasy fiction"],
    hasMovieAdaptation: true,
    pages: 835,
    translations: {
      korean: "왕좌의 게임",
      polish: "Gra o tron",
      portuguese: "A Guerra dos Tronos",
      spanish: "Juego de tronos",
    },
    reviews: {
      goodreads: {
        rating: 4.44,
        ratingsCount: 2295233,
        reviewsCount: 59058,
      },
      librarything: {
        rating: 4.36,
        ratingsCount: 38358,
        reviewsCount: 1095,
      },
    },
  },
];

function getBooks() {
  return data;
}

function getBook(id) {
  return data.find((d) => d.id === id);
}

const books = getBook(2);
const { title, author } = books;

console.log(title, author);

const [primarygenr, secondarygen] = genres;
console.log(primarygenr, secondarygen);



const { title, author } = books; this called destructuring from object here title and author should have the same property name in 'data' object. So we get the title and author from the books object instance for id =2 (const books = getBook(2); )


Array destructuring done as follows where genres will return the first and second genres for id = 2 are placed in primarygenr and secondarygen

const books = getBook(2);
const { title, author, genres } = books;
const [primarygenr, secondarygen] = genres;
console.log(primarygenr, secondarygen);



Rest operator

To get all other array elements we can use rest operator. Here for id = 2 'genres' is an array where we want to get all the values after getting the first and second location of genres with primarygen and secondarygen. and after use the rest operator with different array name i.e here 'otherGenres' and rest operator can be placed at the end of destructuring.

const books = getBook(2);
const { title, author, genres } = books;

console.log(title, author);


Output

[ 'The Cyberiad', 'Stanislaw Lem' ]


const books = getBook(2);
const { title, author, genres } = books;

console.log(title, author);
const [primarygenr, secondarygen, ...otherGenres] = genres;
console.log(primarygenr, secondarygen, otherGenres);

Output

[
  'science fiction', 'humor', [ 'speculative fiction', 'short stories', 'fantasy' ]
]


Spread operator for array

To get all elements in the array and assign that to a different array we can use spread operator.


const books = getBook(2);
const { title, author, genres } = books;

const newGenre = [...genres];
console.log(newGenre);

Output

[
  'science fiction', 'humor', 'speculative fiction', 'short stories', 'fantasy'
]

Spread operator for object

When we want to add additional property to 'books' property along with already existing books property values for id =1. Additionally pages: 2000 the already existing pages property which we get from spread operator will be replaced with new value to pages property in 'bookOne' as 2000. Whenever we want to update the already existing property value to different value we should place the spread operator first.

const bookOne = getBook(1);
const updatedBook = { ...bookOne, newPublicationData: "1992-11-22", pages: 2000 };
console.log(updatedBook);

Output

{
  id: 1,
  title: 'The Lord of the Rings',
  publicationDate: '1954-07-29',
  author: 'J. R. R. Tolkien',
  genres: [
    'fantasy',
    'high-fantasy',
    'adventure',
    'fiction',
    'novels',
    'literature'
  ],
  hasMovieAdaptation: true,
  pages: 2000,
  translations: {
    spanish: 'El señor de los anillos',
    chinese: '魔戒',
    french: 'Le Seigneur des anneaux'
  },
  reviews: {
    goodreads: { rating: 4.52, ratingsCount: 630994, reviewsCount: 13417 },
    librarything: { rating: 4.53, ratingsCount: 47166, reviewsCount: 452 }
  },
  newPublicationData: '1992-11-22'
}






Template literal

Template literal is denoted by backtick ``. ${title} is the JavaScript expression. The javascript expression written inside backtick

const literalValue = `Bini Babu`;
console.log(literalValue);


const books = getBook(2);
const { title, author, genres } = books;
const literalValue = `${title} Bini Babu`;
console.log(literalValue);

Output

'The Cyberiad Bini Babu'



Ternary operator


const books = getBook(2);
const { title, author, genres, pages } = books;
const terValue = pages > 200 ? "Greater than 200" : "Less than 200";
console.log(terValue);

Output

'Greater than 200'





Arrow function


Traditional function written in this way

const books = getBook(2);
const { title, author, genres, pages, publicationDate } = books;

function publishDate(str) {
  return str.split("-")[0];
}
console.log(publishDate(publicationDate));

Output

'1965'


Arrow function example


const getYear = (str) =>
{
 return str.split("-")[0];
}
console.log(getYear(publicationDate));

Output

'1965'






Short circuiting and logical operators


Logical &&

console.log(true && 'Say Something')

Output

'Say Something'

Here (console.log(true && 'Say Something')) since we use logical && the first value is true it goes to second value and print 'Say Something'.


Since we give false initially in (console.log(false && "Say Something");) then it does not go to 'Say Something' and the output is false. Since we use logical && operator.

console.log(false && "Say Something");

output
false


Example

const books = getBook(2);
const { title, author, genres, pages, publicationDate, hasMovieAdaptation } =
  books;
console.log(hasMovieAdaptation && "Say Something");

Output

false


truthy values are anything thats not falsy value
falsy value are 0, '', null, undefined

example

console.log('jonas' && "Say Something");

Output

'Say Something'

since 'jonas' is truthy value the console will print the second that is 'Say Something'


Logical ||

console.log(true || "Say Something");

Output
true

console.log(false || "Say Something");

Output

'Say Something'

When the first value is true and an logical OR operator is used then first value is printed. But if the first value is false and logical OR operator is used then second argument is evaluated.


example

console.log(bookOne.translations.english);

Output
undefined


example

const english = bookOne.translations.english || 'Not transalated';
console.log(english);

Output

'Not transalated'

Because 'bookOne.translations.english' is undefined hence 'Not transalated' value will be assigned to 'english' variable.



console.log(book.reviews.libranything.reviewsCount);
// Output: 0


const countWrong = book.reviews.libranything.reviewsCount || 'no data';
console.log(countWrong);
// Output: 'no data'

Even if book.reviews.libranything.reviewsCount has value 0 since 0 is falsy hence the second value is evaluated to overcome this we use Nullish Coalescing Operator '??'


const count = book.reviews.libranything.reviewsCount ?? 'no data';
console.log(count);
// Output: 0


When the first operand is 0 or '' empty string then Nullish Coalescing Operator will return the first operand . But when the first operand is null or undefined then second operand is evaluated

The default 'no data' is only used if the value is null or undefined.

Logical operators && and || in JavaScript implement short circuiting, returning the first value that determines the outcome without evaluating the second.
The && operator short circuits when the first operand is falsy, returning it immediately.
The || operator short circuits when the first operand is truthy, returning it immediately.
The nullish coalescing operator ?? returns the second operand only if the first is null or undefined, avoiding issues with falsy values like zero or empty strings.





Optional chaining (?)


function bookCount(book) {
  var goodCount = book.reviews.goodreads?.reviewsCount;
 var libraryCount = book.reviews.librarything?.reviewsCount ?? 0;
  return goodCount + libraryCount;
}
console.log(bookCount(books));

Output
812

If  book.reviews.goodreads and book.reviews.librarything exists or not null or not undefined only then the reviewsCount are extracted and sum up.
var libraryCount = book.reviews.librarything?.reviewsCount ?? 0; In this nullish coalescing operator ?? used if value is book.reviews.librarything?.reviewsCount is null or undefined then the value will be set 0.




Map

map is used to create a new array from the original array by applying a operation on each elements in the array.

const x = [1,2,3,4].map((el)=> el*2)
console.log(x)

Output
[ 2, 4, 6, 8 ]

Here 'el' is the current value in the array.


const books = getBooks();
const title = books.map((value) => value.title);
console.log(title);

Output

[
  'The Lord of the Rings', 'The Cyberiad', 'Dune', 'Harry Potter and the Philosopher\'s Stone',
  'A Game of Thrones'
]



const books = getBooks();
const title = books.map((value) => {
  return {
     author: value.author,
    title: value.title,
    reviewCount: bookCount(value)
  };
});
console.log(title);

Output

[
  {
    author: 'J. R. R. Tolkien',
    title: 'The Lord of the Rings',
    reviewCount: 13869
  },
  {
    author: 'Stanislaw Lem',
    title: 'The Cyberiad',
    reviewCount: 812
  },
  { author: 'Frank Herbert', title: 'Dune', reviewCount: 49701 },
  {
    author: 'J. K. Rowling',
    title: 'Harry Potter and the Philosopher\'s Stone',
    reviewCount: 142585
  },
  {
    author: 'George R. R. Martin',
    title: 'A Game of Thrones',
    reviewCount: 60153
  }
]






Filter

const books = getBooks();
const longBooks = books.filter((book) => book.pages > 500);
console.log(longBooks);

Here each 'book' will filter pages thats greater than 500 then it will return true and those book will be picked up  and will place in new array 'longBooks'. If pages less than 500 exists that will return false and will not pick up those book and will not place in new array 'longBooks'.
filter will go through each array element. Second filter will filter each book where hasMovieAdaptation returns true.


const books = getBooks();
const longBooks = books
  .filter((book) => book.pages > 500)
  .filter((book) => book.hasMovieAdaptation)
  .map((val) => val.title);
console.log(longBooks);

Output

[ 'The Lord of the Rings', 'Dune', 'A Game of Thrones' ]



const books = getBooks();
const adventureBook = books.filter((book) => book.genres.includes('adventure')).map((book) => book.title);
console.log(adventureBook);

Output
[ 'The Lord of the Rings', 'Dune', 'Harry Potter and the Philosopher\'s Stone' ]




Reduce

reduce is used to reduce the whole array into a single value. In the below code we use reduce to count the number of pages each book has. reduce method has 2 arguments first is the function and second argument is the starter value.


const books = getBooks();
const pagesAllBook = books.reduce((accum, book) => accum + book.pages, 0);
console.log(pagesAllBook);

Output
3227

'accum' starts with value 0 and adds with the pagesnumber of each 'book.pages' and each pages sum will be stored in accum. 'book' is the current value.





Sort

sorts the elements. Below in the sort there is 2 arguments 'a' and 'b' where 'a' is the current value and 'b' is the next value. When a -b is negative then the smaller number will be placed first and then larger number and is placed in ascending order. sort mutates (changes) the original array.

const arr = [4, 2, 9, 5, 1];
const sortedArr = arr.sort((a, b) => a - b);
console.log(sortedArr);
console.log(arr);

Output

[ 1, 2, 4, 5, 9 ]
[ 1, 2, 4, 5, 9 ]


Since sort mutates (changes) the original array we can use slice which will make a copy of original array and sorting done on the copy of the array. Like shown below.

const arr = [4, 2, 9, 5, 1];
const sortedArr = arr.slice().sort((a, b) => a - b);
console.log(sortedArr);
console.log(arr);

Output

[ 1, 2, 4, 5, 9 ]

[4, 2, 9, 5, 1]

Sort book by descending order of pages property shown below

const books = getBooks();
const sortPages = books.slice().sort((a, b) => b.pages - a.pages);
console.log(sortPages);





Working With Immutable Arrays


In React, many operations need to be immutable, meaning we do not manipulate the underlying data structure directly. Therefore, it is quite important to know how to add elements to an array, delete elements, and update elements all without mutating the original underlying array.

//Add book object to array

const books = getBooks();
const newBook = {
  id: 6,
  title: "The Harry potter and the chamber of secrets",
  author: "J K Rowling",
};
const bookAfterAdd = [...books, newBook];
console.log(bookAfterAdd);

Here we added 'newBook' book object into already existing 'books' array of books.

Deleting book with id = 3

//Add book object to array
const books = getBooks();
const newBook = {
  id: 6,
  title: "The Harry potter and the chamber of secrets",
  author: "J K Rowling",
};
const bookAfterAdd = [...books, newBook];
//console.log(bookAfterAdd);

const bookDelete = bookAfterAdd.filter((book) => book.id !== 3);
console.log(bookDelete);

To update inside an array we use map

//Add book object to array
const books = getBooks();
const newBook = {
  id: 6,
  title: "The Harry potter and the chamber of secrets",
  author: "J K Rowling",
};
const bookAfterAdd = [...books, newBook];
//console.log(bookAfterAdd);

//delete book
const bookDelete = bookAfterAdd.filter((book) => book.id !== 3);
//console.log(bookDelete);

//update book

const bookUpdate = bookDelete.map((book)=> book.id === 1 ? {} : book)


Here in the update ( bookDelete.map((book)=> book.id === 1 ? {} : book) ) where the id = 1 will have empty object and otherwise the corresponding book is returned.



const bookUpdate = bookDelete.map((book) =>
  book.id === 1 ? { ...book, pages: 2000 } : book
);
console.log(bookUpdate);


Here we updated for book with id = 1 with pages as 2000.






Asynchronous JavaScript: Promises

 function called fetch into which we can pass the URL of an API. Since the fetch returns a promise we have to call 'then'. As soon as the promise is called 'then' is called when data is reached. Since 'res.json()' is also returning a promise we have to call again 'then'

fetch("https://jsonplaceholder.typicode.com/todos")
  .then((res) => res.json())
  .then((data) => console.log(data));



1. Promise.resolve(value)

Returns a promise that is resolved with the provided value.

Promise.resolve("Success").then(console.log);
// Output: Success

2. Promise.reject(reason)

Returns a promise that is rejected with the provided reason.

Promise.reject("Error occurred").catch(console.error);
// Output: Error occurred

3. Promise.all(iterable)

Runs multiple promises in parallel and returns a single promise that:

Resolves when all promises resolve

Rejects immediately if any promise rejects

const p1 = Promise.resolve(1);
const p2 = Promise.resolve(2);
const p3 = Promise.resolve(3);

Promise.all([p1, p2, p3]).then(console.log);
// Output: [1, 2, 3]

4. Promise.allSettled(iterable)

Waits for all promises to settle (resolve or reject) and returns an array describing results.

const p1 = Promise.resolve("Success");
const p2 = Promise.reject("Failed");

Promise.allSettled([p1, p2]).then(console.log);
/*
[
  { status: "fulfilled", value: "Success" },
  { status: "rejected", reason: "Failed" }
]
*/

5. Promise.race(iterable)

Returns the result of the first settled promise (resolved or rejected).

const p1 = new Promise(res => setTimeout(res, 100, "p1"));
const p2 = new Promise(res => setTimeout(res, 50, "p2"));

Promise.race([p1, p2]).then(console.log);  
// Output: p2

6. Promise.any(iterable)

Returns the first fulfilled promise; ignores rejections.
If all reject, it returns an AggregateError.

const p1 = Promise.reject("Error");
const p2 = Promise.resolve("Success");

Promise.any([p1, p2]).then(console.log);
// Output: Success

7. Promise.finally(callback)

Runs a callback when the promise settles (resolved OR rejected).

fetch("https://example.com/api")
  .then(res => console.log("Done"))
  .catch(err => console.error(err))
  .finally(() => console.log("Cleanup done"));

🎯 Summary Table
Method	Behavior
Promise.resolve()	Creates a resolved promise
Promise.reject()	Creates a rejected promise
Promise.all()	Waits for all to resolve or rejects fast
Promise.allSettled()	Waits for all and gives detailed results
Promise.race()	Returns first settled promise
Promise.any()	Returns first fulfilled promise
Promise.finally()	Executes cleanup on settle
💡 Real-use Example with Promise.all
async function loadData() {
  try {
    const [users, posts, comments] = await Promise.all([
      fetch("/users").then(res => res.json()),
      fetch("/posts").then(res => res.json()),
      fetch("/comments").then(res => res.json())
    ]);

    console.log(users, posts, comments);
  } catch (error) {
    console.error("API error:", error);
  }
}


Asynchronous JavaScript: Async/Await


we create an async function by prefixing it with the async keyword. For example, we can define a function called getTodos as an async function.

Inside this async function, we can use the await keyword to pause execution until a promise resolves. For example, we can await the fetch call directly inside the function.

When using await inside an async function, JavaScript does not immediately move on to the next line. Instead, it pauses execution until the awaited promise resolves, unlike the default behavior where JavaScript moves immediately to the next line without waiting.

This pause makes the function look more like normal synchronous JavaScript code. We can store the result of the awaited promise into a variable, such as response, making the code more legible and easier to understand.

Similarly, we can await the JSON parsing of the response and store it in a variable called data. Then, we can log this data to the console.

Finally, we call the async function to execute the data fetching and logging.



async function getTodos() {
  const res = await fetch("https://jsonplaceholder.typicode.com/todos");
  const data = await res.json();
  console.log(data);
}
getTodos();








Working with components, props, and JSX


Rendering the Root Component and Strict Mode

Webpack bundler looks for the entry point to the project through 'index.js'

Purpose of Strict Mode
Strict Mode renders all components twice during development to help find certain bugs and checks if outdated parts of the React API are being used. While not groundbreaking, it is a good practice to always activate Strict Mode when developing React applications






Components as Building Blocks

React application are entirely made of components. Components are building blocks of user interfaces. Components are piece of that has its own data, logic and appearance (how it works and looks). To build complex UI's by building multiple components and combining them. Components can be reused , nested inside each other and pass data between them.


function App() {
  return (
    <div>
      <h1>Welcome to React</h1>
      <Pizza />
    </div>
  );
}

function Pizza() {
  return <h2>Pizza</h2>;
}

Pizza function is nested in App function (i.e  <Pizza />)



What is JSX

JSX is a declarative syntax that we use to describe what components look like and how they work based on their data and logic. So, it's all about the component's appearance. In practice, this means that each component must return one block of JSX, which React will then use to render the component on the user interface.
JSX is an extension of JavaScript that allows to Embed Javascript, CSS and React components into HTML.
JSX converted to JavaScript using Babel. This conversion is necessary because the browser isn't aware of JSX. JSX is declarative it describes what Ui should look like using JSX based on current data. React is an abstraction away from DOM and never touches DOM. UI as a reflection of current data.





Styling in components

Inline style

function Header() {
  return (
    <h1
      style={{
        color: "red",
        fontSize: "32px",
        textAlign: "center",
        textTransform: "uppercase",
      }}
    >
      React Pizza App
    </h1>
  );
}




Using Variables for Styles

function Header() {
  const style = {
    color: "red",
    fontSize: "32px",
    textAlign: "center",
    textTransform: "uppercase",
  };
  return <h1 style={style}>React Pizza App</h1>;
}



Importing CSS Files

Webpack takes the imported css files ad injecting them into the application.


import "./index.css";

function App() {
  return (
    <div className="container">
      <Header />
      <Menu />
      <Footer />
    </div>
  );
}

function Header() {
  return (
    <header className="header">
      <h1>React Pizza App</h1>
    </header>
  );
}

function Menu() {
  return (
    <main className="menu">
      <h2>Our Menu</h2>
      <Pizza />
      <Pizza />
      <Pizza />
      <Pizza />
    </main>
  );
}
function Footer() {
  const hour = new Date().getHours();
  const openhour = 12;
  const closeHour = 22;
  const isOpen = hour >= openhour && hour <= closeHour;
  // else alert("Sorry we are closed");
  return (
    <footer className="footer">
      We are currently open at {new Date().toLocaleTimeString()}
    </footer>
  );
}

function Pizza() {
  return (
    <div>
      <img src="pizzas/spinaci.jpg" alt="Spinach" />
      <h3>Pizza</h3>
      <p>Tomato, mozarella, ham, aragula, and burrata cheese</p>
    </div>
  );
}






Passing and Receiving Props

Props essentially allow us to pass data between components, particularly from parent components to child components. We can imagine props as a communication channel between a parent and a child component.

To define props, we do it in two steps: first, we pass the props into the component, and second, we receive the props in the component that we pass them into

Full example:-

function Menu() {
  return (
    <main className="menu">
      <h2>Our Menu</h2>
      <Pizza
        name="Pizza"
        ingredient="Tomato, mozarella, ham, aragula, and burrata cheese"
        photoName="pizzas/spinaci.jpg"
        price={10}
      />
      <Pizza
        name="Pizza funghi"
        photoName="pizzas/funghi.jpg"
        ingredient="Tomato Basil"
        price={20}
      />
    </main>
  );
}

function Pizza(props) {
  return (
    <div className="pizza">
      <img src={props.photoName} alt={props.name} />
      <div>
        <h3>{props.name}</h3>
        <p>{props.ingredient}</p>
        <span>{props.price + 3}</span>
      </div>
    </div>
  );
}

Here we pass props as shown below

 <Pizza
        name="Pizza"
        ingredient="Tomato, mozarella, ham, aragula, and burrata cheese"
        photoName="pizzas/spinaci.jpg" price={10}
      />


We receive props as below

function Pizza(props)

place the props like this (i.e src={props.photoName})

<img src={props.photoName} alt={props.name} />


price={10} is given to denote its a number


Props are used to pass data from parent components to child components. Props is an essential tool to configure and customize components. With props parent components control how child components look and work. In props we can pass single values, arrays, objects, functions, even other components.
Components include data, logic and appearance. Data consists of Props and state. Where state is internal data that can be updated by the components logic and props is data coming from outside and can only be updated by parent component. Props are read only, they are immutable. To mutate props we need state. State is used for data change. Props are immutable because if props changes then parent component also changes. Components have to be pure function in terms of state and props (should not change the outside or parent component). This Allows React to optimize apps, avoid bugs.
React uses one way data flow ( which means data can flow only from parent to child component by using props but not the opposite way). React is one way data flow because it makes application more predictable and easier to understand for developers, makes application to debug easily, two way data flow is less efficient.






Rules of JSX

JSX works like HTML, but we can enter 'JavaScript mode' by using {} for text or attributes.
We can place JavaScript expression inside {}. Examples: reference variables, create arrays or objects, map(), ternary operator.
Statements (like if/else, for, switch) aren't allowed in JSX.
JSX produces a JavaScript expression. But we can write JSX anywhere inside a component ( in if/else, assign to variables, pass it into functions). A piece of JSX can only have one root element. If you need more use <React.Fragment> (or short <>)


Difference between JSX and HTML

className instead of HTML's class.
htmlFor instead of HTML's for
Every tags need to be closed (<img /> )
All eventHandlers and other properties need to be camelCased (example onClick, onMouseOver)
CSS inline styles are written like this {{<style>}}
(to reference a variable and then an object)
CSS property names are also camelCased
Comments need to be {}







Rendering Lists


function Menu() {
  return (
    <main className="menu">
      <h2>Our Menu</h2>
      <ul className="pizzas">
        {pizzaData.map((pizza) => (
          <Pizza pizzaObj={pizza} key={pizza.name} />
        ))}
      </ul>
    </main>
  );
}

function Pizza(props) {
  return (
    <li className="pizza">
      <img src={props.pizzaObj.photoName} alt={props.pizzaObj.name} />
      <div>
        <h3>{props.pizzaObj.name}</h3>
        <p>{props.pizzaObj.ingredient}</p>
        <span>{props.pizzaObj.price}</span>
      </div>
    </li>
  );
}



Full example

import React from "react";
import ReactDOM from "react-dom/client";
//import ReactDOM from "react-dom"; //react version before 18
import "./index.css";

const pizzaData = [
  {
    name: "Focaccia",
    ingredients: "Bread with italian olive oil and rosemary",
    price: 6,
    photoName: "pizzas/focaccia.jpg",
    soldOut: false,
  },
  {
    name: "Pizza Margherita",
    ingredients: "Tomato and mozarella",
    price: 10,
    photoName: "pizzas/margherita.jpg",
    soldOut: false,
  },
  {
    name: "Pizza Spinaci",
    ingredients: "Tomato, mozarella, spinach, and ricotta cheese",
    price: 12,
    photoName: "pizzas/spinaci.jpg",
    soldOut: false,
  },
  {
    name: "Pizza Funghi",
    ingredients: "Tomato, mozarella, mushrooms, and onion",
    price: 12,
    photoName: "pizzas/funghi.jpg",
    soldOut: false,
  },
  {
    name: "Pizza Salamino",
    ingredients: "Tomato, mozarella, and pepperoni",
    price: 15,
    photoName: "pizzas/salamino.jpg",
    soldOut: true,
  },
  {
    name: "Pizza Prosciutto",
    ingredients: "Tomato, mozarella, ham, aragula, and burrata cheese",
    price: 18,
    photoName: "pizzas/prosciutto.jpg",
    soldOut: false,
  },
];

function App() {
  return (
    <div className="container">
      <Header />
      <Menu />
      <Footer />
    </div>
  );
}

function Header() {
  return (
    <header className="header">
      <h1>React Pizza App</h1>
    </header>
  );
}

function Menu() {
  return (
    <main className="menu">
      <h2>Our Menu</h2>
      <ul className="pizzas">
        {pizzaData.map((pizza) => (
          <Pizza pizzaObj={pizza} key={pizza.name} />
        ))}
      </ul>
    </main>
  );
}

function Pizza(props) {
  return (
    <li className="pizza">
      <img src={props.pizzaObj.photoName} alt={props.pizzaObj.name} />
      <div>
        <h3>{props.pizzaObj.name}</h3>
        <p>{props.pizzaObj.ingredient}</p>
        <span>{props.pizzaObj.price}</span>
      </div>
    </li>
  );
}

function Footer() {
  const hour = new Date().getHours();
  const openhour = 12;
  const closeHour = 22;
  const isOpen = hour >= openhour && hour <= closeHour;
  // else alert("Sorry we are closed");
  return (
    <footer className="footer">
      We are currently open at {new Date().toLocaleTimeString()}
    </footer>
  );
}

//react from version 18 onwards
const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);

//react version before 18
//React.render(<App />, document.getElementById("root"))











Conditional Rendering With &&
 

function Menu() {
  const pizzas = pizzaData;
  const numPizzas = pizzas.length;
  return (
    <main className="menu">
      <h2>Our Menu</h2>
      {numPizzas > 0 && (
        <ul className="pizzas">
          {pizzas.map((pizza) => (
            <Pizza pizzaObj={pizza} key={pizza.name} />
          ))}
        </ul>
      )}
    </main>
  );
}

function Pizza(props) {
  return (
    <li className="pizza">
      <img src={props.pizzaObj.photoName} alt={props.pizzaObj.name} />
      <div>
        <h3>{props.pizzaObj.name}</h3>
        <p>{props.pizzaObj.ingredient}</p>
        <span>{props.pizzaObj.price}</span>
      </div>
    </li>
  );
}

function Footer() {
  const hour = new Date().getHours();
  const openhour = 12;
  const closeHour = 22;
  const isOpen = hour >= openhour && hour <= closeHour;
  // else alert("Sorry we are closed");
  return (
    <footer className="footer">
      {isOpen && (
        <div className="order">
          <p>We are currently open until {closeHour}:00</p>
          <button className="btn">Order Now</button>
        </div>
      )}
    </footer>
  );
}




Conditional Rendering With Ternaries


function Menu() {
  const pizzas = pizzaData;
  const numPizzas = pizzas.length;
  return (
    <main className="menu">
      <h2>Our Menu</h2>
      {numPizzas > 0 ? (
        <ul className="pizzas">
          {pizzas.map((pizza) => (
            <Pizza pizzaObj={pizza} key={pizza.name} />
          ))}
        </ul>
      ) : (
        <p>We are working on the menu please come later</p>
      )}
    </main>
  );
}

function Pizza(props) {
  return (
    <li className="pizza">
      <img src={props.pizzaObj.photoName} alt={props.pizzaObj.name} />
      <div>
        <h3>{props.pizzaObj.name}</h3>
        <p>{props.pizzaObj.ingredient}</p>
        <span>{props.pizzaObj.price}</span>
      </div>
    </li>
  );
}

function Footer() {
  const hour = new Date().getHours();
  const openhour = 12;
  const closeHour = 22;
  const isOpen = hour >= openhour && hour <= closeHour;
  // else alert("Sorry we are closed");
  return (
    <footer className="footer">
      {isOpen ? (
        <div className="order">
          <p>We are currently open until {closeHour}:00</p>
          <button className="btn">Order Now</button>
        </div>
      ) : (
        <p>
          We are happy you between {openhour} and {closeHour}
        </p>
      )}
    </footer>
  );
}





Conditional Rendering With Multiple Returns


function Footer() {
  const hour = new Date().getHours();
  const openhour = 12;
  const closeHour = 22;
  const isOpen = hour >= openhour && hour <= closeHour;

  if (!isOpen) return <p>Closed</p>;
  // else alert("Sorry we are closed");
  return (
    <footer className="footer">
      {isOpen ? (
        <div className="order">
          <p>We are currently open until {closeHour}:00</p>
          <button className="btn">Order Now</button>
        </div>
      ) : (
        <p>
          We are happy you between {openhour} and {closeHour}
        </p>
      )}
    </footer>
  );
}



function Pizza(props) {
  if (props.pizzaObj.soldOut) return null;
  return (
    <li className="pizza">
      <img src={props.pizzaObj.photoName} alt={props.pizzaObj.name} />
      <div>
        <h3>{props.pizzaObj.name}</h3>
        <p>{props.pizzaObj.ingredient}</p>
        <span>{props.pizzaObj.price}</span>
      </div>
    </li>
  );
}








Extracting JSX Into a New Component



function Footer() {
  const hour = new Date().getHours();
  const openhour = 12;
  const closeHour = 22;
  const isOpen = hour >= openhour && hour <= closeHour;

  return (
    <footer className="footer">
      {isOpen ? (
        <Order closeHour={closeHour} />
      ) : (
        <p>
          We are happy you between {openhour} and {closeHour}
        </p>
      )}
    </footer>
  );
}

function Order(props) {
  return (
    <div className="order">
      <p>We are currently open until {props.closeHour}:00</p>
      <button className="btn">Order Now</button>
    </div>
  );
}





Destructuring Props

Each time that we pass some props into a component, that component will then automatically receive this object of props, which will contain all the props that we passed in.

Actually, all components receive this props object. So even here in the footer, where we don't pass any props in, we can define that and we can log it to the console. It will be empty then.

What we want to do now is to avoid having to write props. whatever all the time in our component.



function Menu() {
  const pizzas = pizzaData;
  const numPizzas = pizzas.length;
  return (
    <main className="menu">
      <h2>Our Menu</h2>
      {numPizzas > 0 ? (
        <ul className="pizzas">
          {pizzas.map((pizza) => (
            <Pizza pizzaObj={pizza} key={pizza.name} />
          ))}
        </ul>
      ) : (
        <p>We are working on the menu please come later</p>
      )}
    </main>
  );
}

function Pizza({ pizzaObj }) {
  if (pizzaObj.soldOut) return null;
  return (
    <li className="pizza">
      <img src={pizzaObj.photoName} alt={pizzaObj.name} />
      <div>
        <h3>{pizzaObj.name}</h3>
        <p>{pizzaObj.ingredient}</p>
        <span>{pizzaObj.price}</span>
      </div>
    </li>
  );
}


We should use 'pizzaObj' which we pass in <Pizza pizzaObj={pizza} key={pizza.name} /> in function Pizza({ pizzaObj }) this is destructuring of not using props


Another example


function Footer() {
  const hour = new Date().getHours();
  const openhour = 12;
  const closeHour = 22;
  const isOpen = hour >= openhour && hour <= closeHour;
  // else alert("Sorry we are closed");
  return (
    <footer className="footer">
      {isOpen ? (
        <Order closeHour={closeHour} openhour={openhour} />
      ) : (
        <p>
          We are happy you between {openhour} and {closeHour}
        </p>
      )}
    </footer>
  );
}

function Order({ closeHour, openhour }) {
  return (
    <div className="order">
      <p>We are currently open {openhour} from {closeHour}:00</p>
      <button className="btn">Order Now</button>
    </div>
  );
}


function Order({ closeHour, openhour }) where we removed the use of props and just closeHour and openhour.





React Fragments


React Fragments are a feature in React that allow developers to group multiple elements from a component's render method without introducing an additional wrapper DOM node. Denoted by <>  and </> or   <React.Fragment> </React.Fragment>.
At some cases we cannot given multiple HTML elements inside a JSX, since as per rule JSX expressions must have one parent element. So to overcome this issue we use React Fragments.

Example

function Menu() {
  const pizzas = pizzaData;
  const numPizzas = pizzas.length;
  return (
    <main className="menu">
      <h2>Our Menu</h2>

      {numPizzas > 0 ? (
        <>
          <p>
            Authentic Italian cuisine. 6 Creative dishes to choose from. All
            from our stone oven, all organic, all delicious
          </p>
          <ul className="pizzas">
            {pizzas.map((pizza) => (
              <Pizza pizzaObj={pizza} key={pizza.name} />
            ))}
          </ul>
        </>
      ) : (
        <p>We are working on the menu please come later</p>
      )}
    </main>
  );
}






Setting Classes and Text Conditionally

function Pizza({ pizzaObj }) {
  return (
    <li className={`pizza ${pizzaObj.soldOut ? "sold-out" : ""}`}>
      <img src={pizzaObj.photoName} alt={pizzaObj.name} />
      <div>
        <h3>{pizzaObj.name}</h3>
        <p>{pizzaObj.ingredient}</p>
        <span>{pizzaObj.soldOut ? "SOLD OUT" : pizzaObj.price}</span>
      </div>
    </li>
  );
}

<span>{pizzaObj.soldOut ? "SOLD OUT" : pizzaObj.price}</span> this piece of code giving soldOut message if soldOut is true.


  <li className={`pizza ${pizzaObj.soldOut ? "sold-out" : ""}`}>
 
here based on a condition we can give className.







Handling Events the React way


const messages = [
  "Learn React ⚛️",
  "Apply for jobs 💼",
  "Invest your new income 🤑",
];

export default function App() {
  const step = 1;
  function handlePrevious() {
    alert("Previous");
  }
  function handleNext() {
    alert("Next");
  }
  return (
    <div className="steps">
      <div className="numbers">
        <div className={`${step >= 1 ? "active" : ""}`}>1</div>
        <div className={`${step >= 2 ? "active" : ""}`}>2</div>
        <div className={`${step >= 3 ? "active" : ""}`}>3</div>
      </div>
      <p className="message">
        Step {step} : {messages[step - 1]}
      </p>
      <div className="buttons">
        <button
          style={{ backgroundColor: "#7950f2", color: "#fff" }}
          onClick={handlePrevious}
        >
          Previous
        </button>
        <button
          style={{ backgroundColor: "#7950f2", color: "#fff" }}
          onClick={handleNext}
        >
          Next
        </button>
      </div>
    </div>
  );
}



Here in this piece of code ' onClick={handlePrevious}' we are passing function name 'handlePrevious' in onClick event.







State in React

State is a data that a component can hold over time, necessary for information that it needs to remember throughout the app's lifecycle. State can be called as the components memory. State is all pieces of state

Examples of state can be simple things like a notification count, the text content of an input field, or the active tab in a tab component. It can also be more complex data, for example, the content of a shopping cart. What all these pieces of state have in common is that in the application, the user can easily change these values. For example, when they read a notification, the count will go down by one, or when they click on another tab, that tab will become active. Each of these components needs to be able to hold this data over time, over the lifecycle of the application. For that reason, each of these pieces of information is a piece of state.

 A piece of state, or a state variable, is just one single actual variable in the component that we can define in our code. On the other hand, the term state itself refers to the entire state that the component is in, like the entire condition at a certain point in time. Basically, the general term state is all the pieces of state together. In practice, we usually use the terms state, piece of state, and state variable quite interchangeably.

When we update a state in a component this will make React to re-render the component in the user interface. Which means it will give new updated view. A web page comprises different components and the group of each components give the entire view or webpage. State will sync User interface with the component data. When state changed the Ui is changed.
State allows developers to update  the component view by re-rendering it, persist local variable's between renders.

State variable created using useState. useState has arguments first argument is the default value. Second argument is the function which returns the state variable.

 In the below example the default value is 1 that is why we give 1 inside useState and setStep as the function which returns the state variable (here state variable is step)

let [step, setStep] = useState(1);

The above code is defining the state variable use the useState function.
We used the state (i.e <div className={`${step >= 1 ? "active" : ""}`}>1</div>
 )
Then update state variable suing setState (i.e in below example setStep(step + 1); )


Full example

import { useState } from "react";

const messages = [
  "Learn React ⚛️",
  "Apply for jobs 💼",
  "Invest your new income 🤑",
];

export default function App() {
  let [step, setStep] = useState(1);
  let [test, setTest] = useState({ name: "Bini" });
  function handlePrevious() {
    if (step > 1) setStep(step - 1);
  }
  function handleNext() {
    if (step < 3) setStep(step + 1);
    setTest({ name: "Babu" });
  }
  return (
    <div className="steps">
      <div className="numbers">
        <div className={`${step >= 1 ? "active" : ""}`}>1</div>
        <div className={`${step >= 2 ? "active" : ""}`}>2</div>
        <div className={`${step >= 3 ? "active" : ""}`}>3</div>
      </div>
      <p className="message">
        Step {step} : {messages[step - 1]} - {test.name}
      </p>
      <div className="buttons">
        <button
          style={{ backgroundColor: "#7950f2", color: "#fff" }}
          onClick={handlePrevious}
        >
          Previous
        </button>
        <button
          style={{ backgroundColor: "#7950f2", color: "#fff" }}
          onClick={handleNext}
        >
          Next
        </button>
      </div>
    </div>
  );
}

useState is a hook in React because they start with use keyword. useState can be used initially/top in the component function.
Hooks must be called only at the top level of the component function, not inside loops, conditions, or nested functions.

For example, calling useState inside an if statement or another function will cause errors. state variable using its setState not by manually (i.e setStep in above example). Update the state using only setState here in this example setStep

Array state can be handled in the following way

let [test, setTest] = useState({ name: "Bini" });
setTest({ name: "Babu" });





Mechanics of State

DOM/view cannot be changed by React directly rather React uses State. In react a view is updated by re-rendering the component whenever the underlying data changes. Re-rendering means React calls the component function again each time the component is rendered. Conceptually, we can imagine React removing the entire view and replacing it with a new one each time a re-render needs to happen. State value is preserved throughout the re-render. Even though a component can be rendered and re-rendered many times, the state will not reset unless the component disappears from the UI entirely, which is called unmounting.
When state is updated the component is re-rendered.
When in the view there is a button click happening. In the button click an event handler updates the state using set and re-renders the component and updates the view.
React reacts to state changes by re-rendering the UI.

Full updated example
 
import { useState } from "react";

const messages = [
  "Learn React ⚛️",
  "Apply for jobs 💼",
  "Invest your new income 🤑",
];

export default function App() {
  let [step, setStep] = useState(1);
  let [isOpen, setOpen] = useState(true);
  //let [test, setTest] = useState({ name: "Bini" });
  function handlePrevious() {
    if (step > 1) setStep((st) => st - 1);
  }
  function handleNext() {
    if (step < 3) setStep((st) => st + 1);
    // setTest({ name: "Babu" });
  }
  function close() {
    setOpen((isOpenVal) => !isOpenVal);
  }
  return (
    <>
      <button className="close" onClick={close}>
        &times;
      </button>
      {isOpen && (
        <div className="steps">
          <div className="numbers">
            <div className={`${step >= 1 ? "active" : ""}`}>1</div>
            <div className={`${step >= 2 ? "active" : ""}`}>2</div>
            <div className={`${step >= 3 ? "active" : ""}`}>3</div>
          </div>
          <p className="message">
            Step {step} : {messages[step - 1]}
          </p>
          <div className="buttons">
            <button
              style={{ backgroundColor: "#7950f2", color: "#fff" }}
              onClick={handlePrevious}
            >
              Previous
            </button>
            <button
              style={{ backgroundColor: "#7950f2", color: "#fff" }}
              onClick={handleNext}
            >
              Next
            </button>
          </div>
        </div>
      )}
    </>
  );
}




Each component has and manages its own state no matter how many times we render the same component.
State is isolated with each other on the component that it uses. Example below

import { useState } from "react";

const messages = [
  "Learn React ⚛️",
  "Apply for jobs 💼",
  "Invest your new income 🤑",
];

export default function App() {
  return (
    <div>
      <Steps />
      <Steps />
    </div>
  );
}

function Steps() {
  let [step, setStep] = useState(1);
  let [isOpen, setOpen] = useState(true);
  //let [test, setTest] = useState({ name: "Bini" });
  function handlePrevious() {
    if (step > 1) setStep((st) => st - 1);
  }
  function handleNext() {
    if (step < 3) setStep((st) => st + 1);
    // setTest({ name: "Babu" });
  }
  function close() {
    setOpen((isOpenVal) => !isOpenVal);
  }
  return (
    <div>
      <button className="close" onClick={close}>
        &times;
      </button>
      {isOpen && (
        <div className="steps">
          <div className="numbers">
            <div className={`${step >= 1 ? "active" : ""}`}>1</div>
            <div className={`${step >= 2 ? "active" : ""}`}>2</div>
            <div className={`${step >= 3 ? "active" : ""}`}>3</div>
          </div>
          <p className="message">
            Step {step} : {messages[step - 1]}
          </p>
          <div className="buttons">
            <button
              style={{ backgroundColor: "#7950f2", color: "#fff" }}
              onClick={handlePrevious}
            >
              Previous
            </button>
            <button
              style={{ backgroundColor: "#7950f2", color: "#fff" }}
              onClick={handleNext}
            >
              Next
            </button>
          </div>
        </div>
      )}
    </div>
  );
}

With state we view Ui as a reflection of data changing over time
We describe that reflection of data using state, event handlers and JSX.


Practical guidelines about state

State variable should track any data that component has over time. For this in Vanilla JavaScript we use let, var, [], {}
When the component need to be dynamic , create a state and update the state say in the event handler function.
Dont use state variables everytime for also creating a simple variable because state updates will re-render the UI which leads to performance issues.






Select in react

 <select>
        {Array.from({ length: 20 }, (_, i) => i + 1).map((num) => (
          <option value={num} key={num}>
            {num}
          </option>
        ))}
      </select>

select takes array from where first argument is length 20 then second argument is map function. Inside the map function (in Array.from)  first argument is current value (i.e here _ ) , second argument is the index. Second map (outside of Array.from) has option and 'num' as value.




Form in react


function Form() {
  function handleSubmit(event) {
    event.preventDefault(); //prevents reloading of the page
  }
  return (
    <form className="add-form" onSubmit={handleSubmit}>
      <h3>What do you need for your trip</h3>
      <select>
        {Array.from({ length: 20 }, (_, i) => i + 1).map((num) => (
          <option value={num} key={num}>
            {num}
          </option>
        ))}
      </select>
      <input type="text" placeholder="Item .." />
      <button>Add</button>
    </form>
  );
}

form listens to event (i.e by handleSubmit onSubmit function event) when we add value to 'input' field or when button 'Add' is clicked.

To get form elements (i.e here select value, input value we use controlled elements)

Controlled elements

 By default, input fields such as input and select maintain their own state inside the DOM, specifically within the HTML element itself. This makes it difficult to read their values and leaves the state in the DOM, which is not ideal for many reasons. In React, we prefer to keep all state in a central place, inside the React application, not in the DOM.

To achieve centralized state management, we use a technique called controlled elements. With this technique, React controls and owns the state of input fields, not the DOM. To implement controlled elements, we follow three steps:

Create a piece of state.
Use that state as the value of the input field.
Update the state when the input changes.

example

const [description, setDescription] = useState("");
 <input
        type="text"
        placeholder="Item .."
        value={description}
        onChange={(event) => setDescription(event.target.value)}
      />


value of input field is ( value={description} ) and onChange event value is set i setDescription state with event.target.value. So whatever we type in form input field will come in the 'description' state by firing onChange event in setDescription (which sets the 'description' state). So we need both the 'value' and 'onChange' in input field.

In select

<select
        value={quantity}
        onChange={(event) => setQuantity(event.target.value)}
      >
        {Array.from({ length: 20 }, (_, i) => i + 1).map((num) => (
          <option value={num} key={num}>
            {num}
          </option>
        ))}
      </select>


In select value={num} will pass value to event.target.value inside setQuantity(event.target.value) , value={num} gets the value but to be update with the new selection of select value change we need to use setQuantity in onChange event.
Since 'event.target.value' is returning string we can convert to number using 'Number(event.target.value)'.

Controlled elements steps done the following way

Create a piece of state. (eg const [description, setDescription] = useState("");
)
Use that state as the value of the input field. ( eg  value={description} )
Update the state when the input changes. (eg  onChange={(event) => setDescription(event.target.value) )


After this in the 'handleSubmit' function of onSubmit

function handleSubmit(event) {
    event.preventDefault();
    if (!description) return; //prevents reloading of the page
    const newItem = { description, quantity, packed: false, id: Date.now() };
    console.log(newItem);
    setDescription("");
    setQuantity(1);
  }

newItem will get value after we enter the description and quantity in the form

If description not added in the form then the form values should not return anything, for that we give below piece of code

  if (!description) return;

After the form is to submitted we need to clear the form for that we use the code below

  setDescription("");
    setQuantity(1);

Example

function App() {
  return (
    <div className="app">
      <Logo />
      <Form />
      <PackingList />
      <Stats />
    </div>
  );
}

function Form() {
  const [description, setDescription] = useState("");
  const [quantity, setQuantity] = useState(1);
  function handleSubmit(event) {
    event.preventDefault();
    if (!description) return; //prevents reloading of the page
    const newItem = { description, quantity, packed: false, id: Date.now() };
    console.log(newItem);
    setDescription("");
    setQuantity(1);
  }
  return (
    <form className="add-form" onSubmit={handleSubmit}>
      <h3>What do you need for your trip</h3>
      <select
        value={quantity}
        onChange={(event) => setQuantity(Number(event.target.value))}
      >
        {Array.from({ length: 20 }, (_, i) => i + 1).map((num) => (
          <option value={num} key={num}>
            {num}
          </option>
        ))}
      </select>
      <input
        type="text"
        placeholder="Item .."
        value={description}
        onChange={(event) => setDescription(event.target.value)}
      />
      <button>Add</button>
    </form>
  );
}

function PackingList() {
  return (
    <div className="list">
      <ul>
        {initialItems.map((item) => (
          <Item item={item} key={item.id} />
        ))}
      </ul>
    </div>
  );
}


To pass 'Form' function data to 'PackingList' function we cannot use props. Where 'Form' and 'PackingList' are siblings. props can transfer down the tree from parent to child not child to parent or between siblings.


State vs Props

State is an internal data which is owned by component because state is created inside component. State can be updated by the component itself.
Updating state causes component to re-render.

Props are external data owned by parent component. Props are communication channel between parent and child components where parent component can pass data to child component. Props are read only so that cannot be modified by the receiving component.

Let's analyze this in a code example. One of the props passed to the Question component is called "upVotes". That upVotes variable is actually state in the parent component. It is created using the useState Hook, and therefore upVotes is in fact state.
If this piece of state is updated, of course the Question component, which owns the state, will be re-rendered. But it makes sense that the child component, which receives that state as props, should also be re-rendered.







State Management

State management used in cases where one way data flow, child to parent communication, accessing global state, when to use state, types of state local vs global, where to place each piece of state.

Fundamentals of State Management

State management - Deciding when to create pieces of state, what types of state are necessary, where to place each piece of state and how data flows through the app. State are of 2 types local and global state.
Local state are state needed only by one or few components mostly child components and sibling components. State that is defined in a component and only that component and child components have access to it (by passing via props). Example search text field where only text field is aware of what data is typed into it. Always start with local state interms of usage and move to global state when required.
Global state - State that many different components requires access to. When we define a state global then that state is accessible to every component in the entire application (global state shared between all the components, so we can also call this global state as shared state). We can define global state using Context API and external global state Redux. For example in an e-commerce website shopping cart is a global state. Because shopping cart is shared in each product in e-commerce state.

When to create State and Where to place State facts analyzes can be done as follows
1. Need to store data
2. Will data change at some point
  2.1  Will data change at some point-> No
  if data doesn't change at some point then we use regular 'const' variable
  2.2  Will data change at some point-> Yes
   If data changes at some point or in future then is it possible to compute or calculate new data from existing piece of state or props then we should derive state
   2.2.1 If updating the state using existing props and state,
   should it re-render component -> No
       2.2.1.1 using 'useRef' will persist the data over time like regular state but doesn't re-render the component.
   2.2.2 If updating the state using existing props and state,
   should it re-render component -> Yes
       2.2.2.1 create a new state using 'useState' in the component and place the new state created into the component where you are building.
       2.2.2.1.1 where to place the state in the component
            2.2.2.1.1.1 If state is to be used by the same component where we created state -> Yes
             2.2.2.1.1.1.1 Leave in the same component.
           2.2.2.1.1.2 If state is to be required by the child component where we created state in parent component  -> Yes
             2.2.2.1.1.2.1 Pass to child via props.
           2.2.2.1.1.3 If state is to be required by the parent component or sibling component where we created state in child component  -> Yes
             2.2.2.1.1.3.1 Lift state up to first common parent component. ( this is called in React as lifting state up)
           2.2.2.1.1.4 If state is to be required by the sibling components (require all along the component tree)  -> Yes
            2.2.2.1.1..4.1 Then we use global state
 






Thinking About State and Lifting State Up



const newItem = { description, quantity, packed: false, id: Date.now() };
handleAddItems(newItem);

 We need to add item 'newItem' to the 'PackingList'. So we need to create new state with empty array (since the items in the packing list is empty initially)

 const [items, setItems] = useState([]);


function handleAddItems(item){
    setItems((items)=>[...items, item])
  }

Here 'items' is the current array of existing items and 'item' is the new item to added. We cannot use 'push' instead state is immutable.




  function Form() {
  const [description, setDescription] = useState("");
  const [quantity, setQuantity] = useState(1);
  const [items, setItems] = useState([]);
  function handleAddItems(item) {
    setItems((items) => [...items, item]);
  }
  function handleSubmit(event) {
    event.preventDefault();
    if (!description) return; //prevents reloading of the page
    const newItem = { description, quantity, packed: false, id: Date.now() };
    handleAddItems(newItem);
    console.log(newItem);
    setDescription("");
    setQuantity(1);
  }
  return (
    <form className="add-form" onSubmit={handleSubmit}>
      <h3>What do you need for your trip</h3>
      <select
        value={quantity}
        onChange={(event) => setQuantity(Number(event.target.value))}
      >
        {Array.from({ length: 20 }, (_, i) => i + 1).map((num) => (
          <option value={num} key={num}>
            {num}
          </option>
        ))}
      </select>
      <input
        type="text"
        placeholder="Item .."
        value={description}
        onChange={(event) => setDescription(event.target.value)}
      />
      <button>Add</button>
    </form>
  );
}

function PackingList() {
  return (
    <div className="list">
      <ul>
        {initialItems.map((item) => (
          <Item item={item} key={item.id} />
        ))}
      </ul>
    </div>
  );
}


function App() {
  return (
    <div className="app">
      <Logo />
      <Form />
      <PackingList />
      <Stats />
    </div>
  );
}



We need to pass 'items' state ( const [items, setItems] = useState([]);) from 'Form' component to 'PackingList' component. We cannot pass the data from 'Form' component to 'PackingList' component using Props because 'Form' component is a sibling component to 'PackingList' not a parent component. Solution to this passing state between sibling is lifting state up. That is taking the state ( const [items, setItems] = useState([]);) and move the state to closest parent component (which is the App component ). App component is the parent to both 'Form' Component and "PackingList' component. And also 'handleAddItems' to be moved to App component.

example

function App() {
  const [items, setItems] = useState([]);
  function handleAddItems(item) {
    setItems((items) => [...items, item]);
  }
  return (
    <div className="app">
      <Logo />
      <Form onAddItems={handleAddItems} />
      <PackingList items={items} />
      <Stats />
    </div>
  );
}

Accept 'onAddItems' as props in 'Form' component and call 'onAddItems' in 'Form' component and passing 'newItem' in this method of 'onAddItems' argument. (  onAddItems(newItem); ). 'handleAddItems' assist in adding the items of the form and updates the state, So, we pass 'onAddItems' as Props to 'Form' component and (onAddItems(newItem);) in 'Form' component
will update the state'items' in 'App' component thats the immediate parent component. Hence when the updated state is passed as Props to 'PackingList' component.

function Form({ onAddItems }) {
  const [description, setDescription] = useState("");
  const [quantity, setQuantity] = useState(1);

  function handleSubmit(event) {
    event.preventDefault();
    if (!description) return; //prevents reloading of the page
    const newItem = { description, quantity, packed: false, id: Date.now() };
    onAddItems(newItem);
    console.log(newItem);
    setDescription("");
    setQuantity(1);
  }
  return (
    <form className="add-form" onSubmit={handleSubmit}>
      <h3>What do you need for your trip</h3>
      <select
        value={quantity}
        onChange={(event) => setQuantity(Number(event.target.value))}
      >
        {Array.from({ length: 20 }, (_, i) => i + 1).map((num) => (
          <option value={num} key={num}>
            {num}
          </option>
        ))}
      </select>
      <input
        type="text"
        placeholder="Item .."
        value={description}
        onChange={(event) => setDescription(event.target.value)}
      />
      <button>Add</button>
    </form>
  );
}


Lifting State Up means when we want to share multiple states between sibling components then we move state and setState to immediate common parent component.




Child to parent communication

Deleting item where the 'close' symbol is in 'Item' component, but the state is in 'App' component.

 function handleDeleteItems(id) {
    setItems((items) => items.filter((item) => item.id !== id));
  }




'handleDeleteItems' function in App component. Pass 'handleDeleteItems ' as Props to 'PackingList' in App component.


function App() {
  const [items, setItems] = useState([]);
  function handleAddItems(item) {
    setItems((items) => [...items, item]);
  }
  function handleDeleteItems(id) {
    setItems((items) => items.filter((item) => item.id !== id));
  }
  return (
    <div className="app">
      <Logo />
      <Form onAddItems={handleAddItems} />
      <PackingList items={items} onDeleteItems={handleDeleteItems} />
      <Stats />
    </div>
  );
}



   ' <PackingList items={items} onDeleteItems={handleDeleteItems} />'

Now 'handleDeleteItems' as has been passed as 'onDeleteItems' into 'PackingList' component. 'onDeleteItems' should be passed as props from 'PackingList' component to 'Item' component.

 function PackingList({ items, onDeleteItems }) {
  return (
    <div className="list">
      <ul>
        {items.map((item) => (
          <Item item={item} key={item.id} onDeleteItems={onDeleteItems} />
        ))}
      </ul>
    </div>
  );
}


we have to pass 'id' in the 'onDeleteItems', so we need to pass as a callback function in onClick event in 'Close' button (like  <button onClick={() => onDeleteItems(item.id)}>❌</button> ). Here, 'onDeleteItems' will be called only if the button is clicked.

function Item({ item, onDeleteItems }) {
  return (
    <li>
      <span style={item.packed ? { textDecoration: "line-through" } : {}}>
        {item.quantity} &nbsp;
        {item.description}
        <button onClick={() => onDeleteItems(item.id)}>❌</button>
      </span>
    </li>
  );
}


to add checkbox we add checkbox in 'Item' component

function Item({ item, onDeleteItems }) {
  return (
    <li>
      <input type="checkbox" />
      <span style={item.packed ? { textDecoration: "line-through" } : {}}>
        {item.quantity} &nbsp;
        {item.description}
        <button onClick={() => onDeleteItems(item.id)}>❌</button>
      </span>
    </li>
  );
}


Add 'toggleItem' function which will get the id where checkbox is checked and toggle the packed property when the checkbox is checked and unchecked in 'App' component. like below

function toggleItem(id) {
    setItems((items) =>
      items.map((item) =>
        item.id === id ? { ...item, packed: !item.packed } : item
      )
    );
  }


And we pass 'toggleItem' function as props to 'PackingList' component like below

 <PackingList
        items={items}
        onDeleteItems={handleDeleteItems}
        onToggleItem={toggleItem}
      />

example of App:-

function App() {
  const [items, setItems] = useState([]);
  function handleAddItems(item) {
    setItems((items) => [...items, item]);
  }
  function handleDeleteItems(id) {
    setItems((items) => items.filter((item) => item.id !== id));
  }
  function toggleItem(id) {
    setItems((items) =>
      items.map((item) =>
        item.id === id ? { ...item, packed: !item.packed } : item
      )
    );
  }
  return (
    <div className="app">
      <Logo />
      <Form onAddItems={handleAddItems} />
      <PackingList items={items} onDeleteItems={handleDeleteItems} />
      <Stats />
    </div>
  );
}

The we pass onToggleItem as Props from 'PackingItem' component to 'Item' component (like  <Item item={item} key={item.id onDeleteItems={onDeleteItems} onToggleItem={onToggleItem} /> )


function PackingList({ items, onDeleteItems, onToggleItem }) {
  return (
    <div className="list">
      <ul>
        {items.map((item) => (
          <Item
            item={item}
            key={item.id}
            onDeleteItems={onDeleteItems}
            onToggleItem={onToggleItem}
          />
        ))}
      </ul>
    </div>
  );
}

In 'Item' component we will onChange event for checkbox input we will pass the id as a function return statement with id to the 'onToggleItem'
(i.e   <input type="checkbox" onChange={() => onToggleItem(item.id)} /> )

example

function Item({ item, onDeleteItems, onToggleItem }) {
  return (
    <li>
      <input type="checkbox" onChange={() => onToggleItem(item.id)} />
      <span style={item.packed ? { textDecoration: "line-through" } : {}}>
        {item.quantity} &nbsp;
        {item.description}
        <button onClick={() => onDeleteItems(item.id)}>❌</button>
      </span>
    </li>
  );
}




Derived State

State that is computed from an existing piece of state or from props is called derived state.

For example:

const [cart, setCart] = useState([
{name: "JavaScript", price:15.99},
{name: "Java", price : 20.00}
])

const [numItems, setNumItems] = useState(2);
const [totalPrice, SetTotalPrice] = useState(35.99);

In the below example 'cart' should have only 2 items each time when item is added or deleted, since 'numItems' state is set as 2. Similarly 'cart' should have only totalPrice set as 35.99 each time when item is added or deleted.
Here cart, numItems, totalPrice are 3 separate pieces of state even though numItems, totalPrice depend on cart.
Need to keep them all in sync (update together)
3 state updates will cause 3 re-renders .

Instead of above example we can re-write as follows

const [cart, setCart] = useState([
{name: "JavaScript", price:15.99},
{name: "Java", price : 20.00}
])

const numItems = cart.length;
const totalPrice = cart.reduce((acc, cur) => acc + cur.price, 0);


Here numItems, totalPrice can be regular variables instead of using useState each. These numItems, totalPrice are examples of derived state.
most of the time, we cannot derive state, but whenever you have a situation like this one, where one state can easily be computed from another, always prefer derived state.

Do not create two state variables if you actually only need one. This is a very common beginner mistake, but now you will be able to avoid it.


numItems is an example of derived state as by the 'items.length' can calculate the length of items.

 const [items, setItems] = useState([]);
  const numItems = items.length;


example of App component

function App() {
  const [items, setItems] = useState([]);
  function handleAddItems(item) {
    setItems((items) => [...items, item]);
  }
  function handleDeleteItems(id) {
    setItems((items) => items.filter((item) => item.id !== id));
  }
  function toggleItem(id) {
    setItems((items) =>
      items.map((item) =>
        item.id === id ? { ...item, packed: !item.packed } : item
      )
    );
  }
  return (
    <div className="app">
      <Logo />
      <Form onAddItems={handleAddItems} />
      <PackingList
        items={items}
        onDeleteItems={handleDeleteItems}
        onToggleItem={toggleItem}
      />
      <Stats items={items} />
    </div>
  );
}

Example of Stats component


function Stats({ items }) {
  if (!items.length) // if no items then display the following paragraph
    return (
      <p className="stats">
        <em>Start adding some items to your packing list</em>
      </p>
    );
//if items exists then the following lines are executed
  const numItems = items.length;
  const numPacked = items.filter((item) => item.packed).length;
  const percentPacked = Math.round((numPacked / numItems) * 100);
  return (
    <footer className="stats">
      <em>
        {percentPacked === 100
          ? "You got everything ready to go"
          : `You have ${numItems} items on your list, and you already  packed ${numPacked} (${percentPacked}%)`}
      </em>
    </footer>
  );
}




Sorting Items

Add the following code in 'PackagingList' component

 <div className="actions">
        <select value={sortBy} onChange={(event) => setSortBy(event.target.value)}>
          <option value="input">Sort by input order</option>
          <option value="description">Sort by description</option>
          <option value="packed">Sort by packed status</option>
        </select>
      </div>

Then add 'sortBy' state in 'PackagingList' component (i.e

  const [sortBy, setSortBy] = useState("input"); )

here 'sortBy' state is initiallized to "input" which is the first option in 'select' which we wrote. Sorting base on input order, description and packed state code is as follows

let sortedItem;
  if (sortBy === "input") sortedItem = items;
  if (sortBy === "description") {
    sortedItem = items
      .slice()
      .sort((a, b) => a.description.localeCompare(b.description));
  }
  if (sortBy === "packed") {
    sortedItem = items
      .slice()
      .sort((a, b) => Number(a.packed) - Number(b.packed));
  }



Full example of PackingList component

function PackingList({ items, onDeleteItems, onToggleItem }) {
  const [sortBy, setSortBy] = useState("input");
  let sortedItem;
  if (sortBy === "input") sortedItem = items;
  if (sortBy === "description") {
    sortedItem = items
      .slice()
      .sort((a, b) => a.description.localeCompare(b.description));
  }
  if (sortBy === "packed") {
    sortedItem = items
      .slice()
      .sort((a, b) => Number(a.packed) - Number(b.packed));
  }
  return (
    <div className="list">
      <ul>
        {sortedItem.map((item) => (
          <Item
            item={item}
            key={item.id}
            onDeleteItems={onDeleteItems}
            onToggleItem={onToggleItem}
          />
        ))}
      </ul>
      <div className="actions">
        <select
          value={sortBy}
          onChange={(event) => setSortBy(event.target.value)}
        >
          <option value="input">Sort by input order</option>
          <option value="description">Sort by description</option>
          <option value="packed">Sort by packed status</option>
        </select>
      </div>
    </div>
  );
}


and 'sortedItem' is map in jsx of PackingList component



Clearing the list

the following line of code is clearing the items added in App component

 function handleReset() {
    const confirm = window.confirm("Are you sue you want to delete all items");
    if (confirm) setItems([]);
  }




Child Props


Motivation for the Children Prop
With so many props, adding more for customization becomes unwieldy. Instead, we can use the children prop. Rather than passing in the emoji and text as separate props, we can pass the content directly between the opening and closing tags of the Button component.

<Button>
  <span>👈</span> Previous
</Button>
<Button>
  Next <span>👉</span>
</Button>

This approach allows us to easily change the position of the emoji or add more elements as needed. The Button component can now receive any content as children.
' <span>👈</span> Previous' is passed as child props to Button component. Similarly  'Next <span>👉</span>' wen placing between Button component

Using the Children Prop in the Button Component
To access the content between the opening and closing tags, the Button component uses the children prop. This is a predefined keyword in React, and its value is whatever is placed between the tags.

function Button({ children, bgColor, textColor, onClick }) {
  return (
    <button style={{ backgroundColor: bgColor, color: textColor }} onClick={onClick}>
      {children}
    </button>
  );
}

the 'children' is the value passed to Button function which was placed in 'Step' function between the Button tag (<Button><span>👈</span> Previous
</Button>)

The children prop is a very important tool in React. It allows us to make our components truly reusable, as we can pass any content into the component without it needing to know what that content is.

The Button component simply takes the children and renders them inside the button. We can think of the children prop as a hole that can be filled with any content we choose

example


export default function App() {
  return (
    <div>
      <Steps />
      {/* <Steps /> */}
    </div>
  );
}

function Button({ textColor, bgColor, onClick, children }) {
  return (
    <button
      style={{ backgroundColor: bgColor, color: textColor }}
      onClick={onClick}
    >
      {children}
    </button>
  );
}


function Steps() {
  let [step, setStep] = useState(1);
  let [isOpen, setOpen] = useState(true);
  //let [test, setTest] = useState({ name: "Bini" });
  function handlePrevious() {
    if (step > 1) setStep((st) => st - 1);
  }
  function handleNext() {
    if (step < 3) setStep((st) => st + 1);
    // setTest({ name: "Babu" });
  }
  function close() {
    setOpen((isOpenVal) => !isOpenVal);
  }
  return (
    <div>
      <button className="close" onClick={close}>
        &times;
      </button>
      {isOpen && (
        <div className="steps">
          <div className="numbers">
            <div className={`${step >= 1 ? "active" : ""}`}>1</div>
            <div className={`${step >= 2 ? "active" : ""}`}>2</div>
            <div className={`${step >= 3 ? "active" : ""}`}>3</div>
          </div>
          <p className="message">
            Step {step} : {messages[step - 1]}
          </p>
          <div className="buttons">
                        <Button bgColor="#7950f2" textColor="#fff" onClick={handlePrevious}>
              <span>👈</span>Previous
            </Button>
            <Button bgColor="#7950f2" textColor="#fff" onClick={handleNext}>
              Next<span>👉</span>
            </Button>
 
          </div>
        </div>
      )}
    </div>
  );
}







Split components

components if bigger in size then need to split the components into smaller components. Similarly if there are more props in one component then also we need to split the components.
These 2 problems make it too hard to reuse (big components hard to reuse). Complex code hard to understand and use.
Many Small components will result in confusing the codebase. Too abstracted when using small components.

4 criteria for splitting a Ui into components

1. Components splitted based on the logical separation of content or layout of a web page.
2. Make some of the components reusable.
3. Each component has a defined responsibility.
4. Personal coding style.

1. When to create a new component

Start with a relatively big component (not too big) , then split it into smaller components as it becomes necessary.


1. Components splitted based on the logical separation of content or layout of a web page.

Does the component contain pieces of content or layout that dont belong together. (the its a good idea to create a new component)

2. Make some of the components reusable.

Is it possible to reuse part of the component then go with reusability.

3. Each component has a defined responsibility.

Is the component doing too many different things. Does the component rely on too many props.


General guidelines

Creating a new component creates a new abstraction. Abstractions have a cost, because more abstractions require more mental energy to switch back and forth between components. So try not to create new components too early.
Name a component according to what it does or what it displays. Never declare  a new component inside another component.
Smaller components are more re-usable as larger components are less re-usable.




Component Categories

Most of your components will naturally fall into one of three categories

Stateless/Presentational components - No state for these components. Can receive props and simply present received data or other content. Usually small and reusable.

Stateful components - Have state. But can be reusable.

Structural components - pages , layouts or screens of the application. Result of composition. Can be huge and non-reusable (but dont have to).


Prop Drilling

Pass props through several nested child components inorder to get some data into some deeply nested components.

export default function App() {
  const [movies, setMovies] = useState(tempMovieData);
  const [watched, setWatched] = useState(tempWatchedData);
  return (
    <>
      <Navbar movies={movies} />
      <Main watched={watched} movies={movies} average={average} />
    </>
  );
}


'movies' state has to be passed as props to 'Main' component then to ListBox component as props

import { useState } from "react";
export default function Main({ watched, movies, average }) {
  return (
    <main className="main">
      <div className="box">
        <ListBox movies={movies} />
      </div>

      <div className="box">
        <WatchedBox watched={watched} average={average} />
      </div>
    </main>
  );
}


then pass 'movies' to MoviesList component


function ListBox({ movies }) {
  const [isOpen1, setIsOpen1] = useState(true);
  return (
    <>
      <button
        className="btn-toggle"
        onClick={() => setIsOpen1((open) => !open)}
      >
        {isOpen1 ? "–" : "+"}
      </button>
      ;{isOpen1 && <MovieList movies={movies} />}
    </>
  );
}


this passing of props into nested component is called Props drilling. This resulted into different props which is unnecessary.


Component composition

When a component uses another component in its jsx. Like below example we use 'Success' component inside 'Modal' component.

eg:

function Modal(){
return (
<div className="modal">
<Success />
</div>
);
}

function Success(){
return
(
<p>Well done</p>
);
}

But using component in another component' jsx leads to problem in reusability. Because 'Success' component inside 'Modal' component. Hence we cannot reuse 'Modal' component. So, we cannot display error message in Modal component. To solve this problem we use component composition.

Rewriting 'Modal' component

function Modal({children}){
return (
<div className="modal">
{children}
</div>
);
}

function Success(){
return
(
<p>Well done</p>
);
}


function Error(){
return
(
<p>Error</p>
);
}

We can get the success and error message differently by placing like this

<Modal><Success /> </Modal>

Similarly for Error component

<Modal><Error /> </Modal>

'Success' is passed into Modal we can reuse 'Modal'.

Component composition is combining different components using the children prop (or explicitly defined props)

Component composition used in to different cases
1. Create highly reusable and flexible components.
2. To fix prop drilling




Fix Prop drilling with composition


Here 'movies' state passed as props to Navbar component and then pass 'movies' as props into NumResults component. Which is props drilling.

export default function App() {
  const [movies, setMovies] = useState(tempMovieData);
  const [watched, setWatched] = useState(tempWatchedData);
  return (
    <>
      <Navbar movies={movies} />
      <Main watched={watched} movies={movies} average={average} />
    </>
  );
}

export default function Navbar({ movies }) {
  return (
    <nav className="nav-bar">
      <Logo />
      <Search />
      <NumResults movies={movies} />
    </nav>
  );
}


To solve the Prop drilling we use children Props which is component composition ('movies' passed directly from App to 'NumResults' and need not have to pass 'movies' props as nested anymore, hence resolve Prop drill) . We can remove 'movies={movies}' from Navbar in App component. These 3 components are composition in Navbar in App component
(
<NumResults movies={movies} />)
as  following


export default function App() {
  const [movies, setMovies] = useState(tempMovieData);
  const [watched, setWatched] = useState(tempWatchedData);
  return (
    <>
      <Navbar>
        <NumResults movies={movies} />
      </Navbar>
      <Main watched={watched} movies={movies} average={average} />
    </>
  );
}

export default function Navbar({ children }) {
  return (
    <nav className="nav-bar">
      <Logo />
      <Search />
      {children}
    </nav>
  );
}


Following Props drill exists

export default function App() {
  const [movies, setMovies] = useState(tempMovieData);
  const [watched, setWatched] = useState(tempWatchedData);
  return (
    <>
      <Navbar movies={movies} />
      <Main watched={watched} movies={movies} average={average} />
    </>
  );
}


'movies' state has to be passed as props to 'Main' component then to ListBox component as props

import { useState } from "react";
export default function Main({ watched, movies, average }) {
  return (
    <main className="main">
      <div className="box">
        <ListBox movies={movies} />
      </div>

      <div className="box">
        <WatchedBox watched={watched} average={average} />
      </div>
    </main>
  );
}


then pass 'movies' to MoviesList component


function ListBox({ movies }) {
  const [isOpen1, setIsOpen1] = useState(true);
  return (
    <>
      <button
        className="btn-toggle"
        onClick={() => setIsOpen1((open) => !open)}
      >
        {isOpen1 ? "–" : "+"}
      </button>
      ;{isOpen1 && <MovieList movies={movies} />}
    </>
  );
}


Above Props drill solution as follows by component composition.
Call MovieList in App component and the above parent components for the MovieList component

export default function App() {
  const [movies, setMovies] = useState(tempMovieData);
  const [watched, setWatched] = useState(tempWatchedData);
  return (
    <>
      <Navbar>
        <NumResults movies={movies} />
      </Navbar>
      <Main watched={watched} average={average}>
        <ListBox>
          <MovieList movies={movies}></MovieList>
        </ListBox>
      </Main>
    </>
  );
}

Pass as children to Main

export default function Main({ watched, children, average }) {
  return (
    <main className="main">
      <div className="box">{children}</div>

      <div className="box">
        <WatchedBox watched={watched} average={average} />
      </div>
    </main>
  );
}

Similarly pass as children to ListBox

function ListBox({ children }) {
  const [isOpen1, setIsOpen1] = useState(true);
  return (
    <>
      <button
        className="btn-toggle"
        onClick={() => setIsOpen1((open) => !open)}
      >
        {isOpen1 ? "–" : "+"}
      </button>
      ;{isOpen1 && children}
    </>
  );
}
function MovieList({ movies }) {
  return (
    <ul className="list">
      {movies?.map((movie) => (
        <Movie movie={movie} key={movie.imdbID} />
      ))}
    </ul>
  );
}





Composition to make for reusable box component

Composition to make for reusable box component for 'button' and 'isOpen2' state common.

In the below component 'WatchedBox' we have


function WatchedBox({ watched, average }) {
  const [isOpen2, setIsOpen2] = useState(true);

  return (
    <>
      <button
        className="btn-toggle"
        onClick={() => setIsOpen2((open) => !open)}
      >
        {isOpen2 ? "–" : "+"}
      </button>
      {isOpen2 && (
        <>
          <WatchBoxSummary watched={watched} average={average} />

          <ul className="list">
            {watched.map((movie) => (
              <WatchedMoviesList movie={movie} key={movie.imdbID} />
            ))}
          </ul>
        </>
      )}
    </>
  );
}


Similarly Composition to make for reusable box component for ListBox we use 'isOpen1'

function Box({ children }) {
  const [isOpen, setIsOpen] = useState(true);
  return (
    <div className="box">
      <button className="btn-toggle" onClick={() => setIsOpen((open) => !open)}>
        {isOpen ? "–" : "+"}
      </button>
      {isOpen && children}
    </div>
  );
}




function WatchedSummary({ watched, average }) {
  const avgImdbRating = average(watched.map((movie) => movie.imdbRating));
  const avgUserRating = average(watched.map((movie) => movie.userRating));
  const avgRuntime = average(watched.map((movie) => movie.runtime));
  return (
    <div className="summary">
      <h2>Movies you watched</h2>
      <div>
        <p>
          <span>#️⃣</span>
          <span>{watched.length} movies</span>
        </p>
        <p>
          <span>⭐️</span>
          <span>{avgImdbRating}</span>
        </p>
        <p>
          <span>🌟</span>
          <span>{avgUserRating}</span>
        </p>
        <p>
          <span>⏳</span>
          <span>{avgRuntime} min</span>
        </p>
      </div>
    </div>
  );
}

function WatchedMoviesList({ watched }) {
  return (
    <ul className="list">
      {watched.map((movie) => (
        <WatchedMovie movie={movie} key={movie.imdbID} />
      ))}
    </ul>
  );
}

function MovieList({ movies }) {
  return (
    <ul className="list list-movies">
      {movies?.map((movie) => (
        <Movie movie={movie} key={movie.imdbID} />
      ))}
    </ul>
  );
}


export default function App() {
  const [movies, setMovies] = useState(tempMovieData);
  const [watched, setWatched] = useState(tempWatchedData);
 

  return (
    <>
      <Navbar>
        <NumResults movies={movies} />
      </Navbar>
      <Main watched={watched} average={average}>
        <Box>
          <MovieList movies={movies}></MovieList>
        </Box>
        <Box>
          <WatchedSummary watched={watched} average={average} />
          <WatchedMoviesList watched={watched} />
        </Box>
      </Main>
    </>
  );
}



Passing Elements as Props (Alternative to children)

passing as explicit prop (  <Box element={<MovieList movies={movies}></MovieList>} /> ) in App component like below and multiple components in Box component can be provided as ('element' here) inside fragment.


export default function App() {
  const [movies, setMovies] = useState(tempMovieData);
  const [watched, setWatched] = useState(tempWatchedData);
 

  return (
    <>
      <Navbar>
        <NumResults movies={movies} />
      </Navbar>
      <Main watched={watched} average={average}>
        <Box element={<MovieList movies={movies}></MovieList>} />
        <Box
          element={
            <>
              <WatchedSummary watched={watched} average={average} />
              <WatchedMoviesList watched={watched} />
            </>
          }
        />
      </Main>
    </>
  );
}

And passing element as props in Box

function Box({ element }) {
  const [isOpen, setIsOpen] = useState(true);
  return (
    <div className="box">
      <button className="btn-toggle" onClick={() => setIsOpen((open) => !open)}>
        {isOpen ? "–" : "+"}
      </button>
      {isOpen && element}
    </div>
  );
}












Component Lifecycle instance

Actual physical instance of component that can go through lifecycle.
Component lifecycle means lifecycle of a component encompasses the different phases that specific component instance can go through over time.
First phase in component's lifecycle is  component instance is mounted/initial render (component rendered for the first time). This is where fresh state and props are created for component instance.

Second phase (optional) - After mounted of component it can be re-rendered multiple times (component will also re-render if whenever state changes,  Props that it receives changes, when its parent component re-renders, context changes)

Third Phase - when component unmounted (component dies). This happens when component instance is destroyed and removed. State and Props are destroyed.

We can define code to run at these  specific points in time which can be done by using useEffect.

Search in Google for 'omdb api'


In calling the api with the following code will get re-rendered multiple times since setMovies is a setter for the state 'movies'. State will re-render App component hence the api is called infinity times. Hence we should not setState in re-render logic. To resolve this problem we can call the setState in useEffect hook.

 fetch(`http://www.omdbapi.com/?i=tt3896198\&apikey=${KEY}\&s=interstellar`)
    .then((res) => res.json())
    .then((data) => setMovies(data));



full example App.js

export default function App() {
  const [movies, setMovies] = useState([]);
  const [watched, setWatched] = useState([]);
  fetch(`http://www.omdbapi.com/?i=tt3896198\&apikey=${KEY}\&s=interstellar`)
    .then((res) => res.json())
    .then((data) => setMovies(data));
  return (
    <>
      <Navbar>
        <NumResults movies={movies} />
      </Navbar>
      <Main watched={watched} average={average}>
        <ListBox>
          <MovieList movies={movies}></MovieList>
        </ListBox>
      </Main>
    </>
  );
}


useEffect can safely write api end points like data fetching. useEffect code will be executed only after the initial render thats when App renders. In useEffect we can pass a function as first argument and second argument as dependency array.
useEffect helps to do data fetching. we use useEffect to register a function (here for an api end point example this api end point http://www.omdbapi.com/?i=tt3896198&apikey=${KEY}&s=interstellar ).
useEffect function that registered by useEffect (here the api end point) should not render when the component renders (here App component), but render the api end point that renders when the application is already loaded in the browser. The dependency array (here its empty) will be used when the component is mounted.

example:-

useEffect(function () {
    fetch(`http://www.omdbapi.com/?i=tt3896198\&apikey=${KEY}\&s=interstellar`)
      .then((res) => res.json())
      .then((data) => setMovies(data.Search));
  }, []);


full example of App.js

export default function App() {
  const [movies, setMovies] = useState([]);
  const [watched, setWatched] = useState([]);
  useEffect(function () {
    fetch(`http://www.omdbapi.com/?i=tt3896198\&apikey=${KEY}\&s=interstellar`)
      .then((res) => res.json())
      .then((data) => setMovies(data.Search));
  }, []);

  return (
    <>
      <Navbar>
        <NumResults movies={movies} />
      </Navbar>
      <Main watched={watched} average={average}>
        <Box>
          <MovieList movies={movies}></MovieList>
        </Box>
        <Box>
          <WatchedSummary watched={watched} average={average} />
          <WatchedMoviesList watched={watched} />
        </Box>
      </Main>
    </>
  );
}



Side Effect

A side effect is basically any interaction between a React component and the world outside the component. We can also think a side effect as code that actually does something . example : data fetching, setting up subscriptions, setting up timers, manually accessing the DOM.
We need side effects each time when we build apps. Side effect should not be in render logic.
Instead side effects can be create in 2 places of the component.
1. Inside event handlers ( event handlers triggered by events onClick, onSubmit)
2. useEffect ( side effects called in useEffect allows to write code that will run at different moments mount, re-render or unmount).


Event Handlers

For example: fetching a movie data from api end point is side effect. Movie fetching the data takes place only if an event takes place. We use
Event Handlers to react to a certain event that happens in the user interface. Event handlers are the preferred way to create side effects.
eg:
function handleClick(){
     fetch(`http://www.omdbapi.com/?i=tt3896198\&apikey=${KEY}\&s=interstellar`)
      .then((res) => res.json())
      .then((data) => setMovies(data.Search));

}

useEffects

For example: fetching a movie data from api end point is executed after the component mounts (initial render) and after subsequent re-renders (according to dependency array).

 useEffect(function () {
    fetch(`http://www.omdbapi.com/?i=tt3896198\&apikey=${KEY}\&s=interstellar`)
      .then((res) => res.json())
      .then((data) => setMovies(data.Search));
return () => console.log("Cleanup);
  }, []);

Before the component re-renders or unmounts the cleanup function code is executed in useEffect (i.e here return () => console.log("Cleanup); )

useEffect is used to keep a component synchronized with some external system (i.e here in this example with the API movie data).


Async function

To handle promise its convenient way to use async. But useEffect doesn't return promise, but async function returns promise. So in the below example we have to give async in useEffect by enclosing async function (fetchMovies) in another function.


  useEffect(function () {
    async function fetchMovies() {
      const res = await fetch(
        `http://www.omdbapi.com/?i=tt3896198\&apikey=${KEY}\&s=interstellar`
      );
      const data = await res.json();
      setMovies(data.Search);
    }
    fetchMovies();  // calling the async function
  }, []);




Handling Errors

example of App.js

const KEY = "77bc98be";

export default function App() {
  const [movies, setMovies] = useState([]);
  const [watched, setWatched] = useState([]);
  const [isLoading, setIsLoading] = useState(false);
  const [error, setError] = useState("");

  useEffect(function () {
    async function fetchMovies() {
      try {
        setIsLoading(true); //setting up loading message
        const res = await fetch(
          `http://www.omdbapi.com/?i=tt3896198\&apikey=${KEY}\&s=interstellar`
        );
        if (!res.ok) throw new Error("Something went wrong with fetching data"); //throws error and goes to catch block
        const data = await res.json();
        if (data.Response === "False") throw new Error("Movie not found"); // when the api end point doesnt sent response
        setMovies(data.Search);
      } catch (err) {
        setError(err.message);
      } finally {
        setIsLoading(false); //unsetting up loading message
      }
    }
    fetchMovies();
  }, []);

  return (
    <>
      <Navbar>
        <NumResults movies={movies} />
      </Navbar>
      <Main watched={watched} average={average}>
        <Box>
          {isLoading && <Loader />}
          {!isLoading && !error && <MovieList movies={movies}></MovieList>}
          {error && <ErrorMessage message={error} />}
        </Box>
        <Box>
          <WatchedSummary watched={watched} average={average} />
          <WatchedMoviesList watched={watched} />
        </Box>
      </Main>
    </>
  );
}
function Loader() {
  return <p className="loader">Loading...</p>;
}

function ErrorMessage({ message }) {
  return <p className="error">⛔ {message}</p>;
}




Key


A key is a special attribute used when rendering lists of elements in React.
It helps React identify which items have changed, been added, or removed, allowing for efficient updating of the UI without re-rendering the whole list.




useEffect Dependency Array

By default, effects run after every render. We can prevent that by passing a dependency array. Without the dependency array, react doesn't know when to run the useEffect. each time one of the dependencies changes, the useEffect will be executed again. every state variable and prop used inside the useEffect must be included in the dependency array.

example

const title = props.movie.Title;
const [userRating, setUserRating] = useState('');

useEffect(
function (){
if(!title) return;
document.title = `${title} ${userRating \&\& `(Rated ${userRating}` }`;

return() => (document.title = 'usePopcorn);
}, [title, userRating]
);

Here in the dependency array we included the props (i.e title) and state (i.e userRating) , dependency array in the above like this (i.e [title, userRating] )

useEffect is like an event listener that is listening for one dependency to change. Whenever a dependency changes, it will execute the effect again.
In the above example 'title' and 'userRating' dependencies changes then React will execute the useEffect again. Which will update the 'title' in website (i.e in user interface).
useEffects react to updates to state and props used inside the effect (the depenedencies). So useEffects are reactive (like state updates re-rendering the UI)
Component state/props are synchronized with External system (side effect).
(In the above example title)
useEffect is a synchronization mechanism to synchronize effect with the state of the application. When dependency (state or props) changes effect is executed again. This will re-render the application (effects and component lifecycle are deeply connected).
We can use the dependency array to run effects when the component renders or re-renders.

Example:

useEffect(fn, [x,y,z]);

Effect synchronizes with x, y, z. Lifecycle runs on mount (initial render) and re-renders triggered by updating x, y and z. the effect will be executed each time the component instance is re-rendered for the update in x, y and z. When other piece of state or props is executed (here other than x, y and z) then effect will not be executed.

useEffect(fn, []); 

When the dependency array like above is empty which means that the effect synchronizes with no state/props and lifecycle of component is run only on mount (initial render). So effect will be executed after the initial render of the component, since dependency array is empty.

useEffect(fn)

useEffect with no dependency array will be run for every render (which means the effect synchronizes with everything). In this case every state and props will be dependency in this case.

(Note: fn is function , [] is dependency array)






What can we include in the dependency array of useEffect?

You should include all values that are used inside the effect and that come from the component scope (outside the effect). These can be:

✅ 1. State variables
useEffect(() => {
  console.log(count);
}, [count]);

✅ 2. Props
useEffect(() => {
  console.log(userId);
}, [userId]);

✅ 3. Functions (if created inside the component)
const fetchData = () => {};
useEffect(() => {
  fetchData();
}, [fetchData]);


(Usually paired with useCallback to avoid recreation)

✅ 4. Derived values & memoized values
const doubled = useMemo(() => count * 2, [count]);

useEffect(() => {
  console.log(doubled);
}, [doubled]);

✅ 5. Context values
const theme = useContext(ThemeContext);

useEffect(() => {
  console.log(theme);
}, [theme]);

❌ What should NOT be included
Should NOT Include	Why
setState functions	They are stable, React guarantees identity
Primitive constants	Don’t change
Static functions declared outside component	never changes reference

Example:

useEffect(() => {
  setCount(1);
}, [setCount]); // ❌ not needed

⚠️ Special Case: Objects, Arrays, Functions

Objects and arrays are new references on every render:

const obj = { a: 1 };
useEffect(() => {
}, [obj]); // runs every render ❗


➡️ Use useMemo or useCallback to prevent extra runs.




When are effects executed


Mount (initial render) (say component instance '<MovieDetails />')  -> result of rendering of committed to the DOM -> DOM changes are painted to the DOM in browser -> Effect comes into play after the browser has painted on the screen (not immediately after render of component because effect will have long running process to be executed and if effect works before component render is painted into the browser it will block and user will see the old version of the browser for long)
If the effect sets the state then additional render will be required to display the Ui correctly. So, don't use useEffect too many times.
For example: if title was set initially  to value say 'Interstellar' then changed the title state to 'Interstellar Wars' since the 'title' changes and 'title' its there in the dependency array the component will be re-rendered , will commit the result of render into the DOM and painted into the browser. Since 'title' is there in useEffect dependency array the useEffect will be executed for change in 'title' until component is unmounted (here <MovieDetails /> is unmounted)


useLayoutEffect executes before the browser paints into the browser thats the difference between useLayoutEffect and useEffect. So, most people discourage to use useLayoutEffect.


This means useLayoutEffect is useful when you need to:

Measure DOM elements (layout, width, height, position)

Perform synchronous updates that must happen before the UI is visible

Avoid flickering when applying style calculations




We crated state (  const [query, setQuery] = useState("");) in App.js then in the useEffect fetch ap we give url along with the url we provide 'query' state. In addition we give 'query' state in dependency array of useEffect. If 'query' state in dependency array changes then the useEffect will be executed again.

  useEffect(
    function () {
      async function fetchMovies() {
        try {
          setIsLoading(true); //setting up loading message
          const res = await fetch(
            `http://www.omdbapi.com/?i=tt3896198&apikey=${KEY}&s=${query}`
          );
          if (!res.ok)
            throw new Error("Something went wrong with fetching data"); //throws error and goes to catch block
          const data = await res.json();
          if (data.Response === "False") throw new Error("Movie not found"); // when the api end point doesnt sent response
          setMovies(data.Search);
        } catch (err) {
          setError(err.message);
        } finally {
          setIsLoading(false);
          setError(""); //unsetting up loading message
        }
      }
    if (query.length < 3) { //if in search query has length less than 3 then setMovies and error null
        setMovies([]);
        setError("");
        return;
      }
      fetchMovies();
    },
    [query]
  );



When we search in the navbar we get the corresponding movies listed since we provide 'query' state with value we enter in the search bar.

 <Search query={query} setQuery={setQuery} />



example of App.js

export default function App() {
  const [movies, setMovies] = useState([]);
  const [watched, setWatched] = useState([]);
  const [isLoading, setIsLoading] = useState(false);
  const [error, setError] = useState("");
  const [query, setQuery] = useState("");
  
  const tempQuery = "interstellar";
  useEffect(
    function () {
      async function fetchMovies() {
        try {
          setIsLoading(true); //setting up loading message
          const res = await fetch(
            `http://www.omdbapi.com/?i=tt3896198&apikey=${KEY}&s=${query}`
          );
          if (!res.ok)
            throw new Error("Something went wrong with fetching data"); //throws error and goes to catch block
          const data = await res.json();
          if (data.Response === "False") throw new Error("Movie not found"); // when the api end point doesnt sent response
          setMovies(data.Search);
        } catch (err) {
          setError(err.message);
        } finally {
          setIsLoading(false);
          setError(""); //unsetting up loading message
        }
      }
      if (query.length < 3) { //if in search query has length less than 3 then setMovies and error null
        setMovies([]);
        setError("");
        return;
      }
      fetchMovies();
    },
    [query]
  );

  return (
    <>
      <Navbar>
        <Search query={query} setQuery={setQuery} />
        <NumResults movies={movies} />
      </Navbar>
      <Main watched={watched} average={average}>
        <Box>
          {isLoading && <Loader />}
          {!isLoading && !error && <MovieList movies={movies}></MovieList>}
          {error && <ErrorMessage message={error} />}
        </Box>
        <Box>
          <WatchedSummary watched={watched} average={average} />
          <WatchedMoviesList watched={watched} />
        </Box>
      </Main>
    </>
  );
}





useEffect cleanup function


After the last effect run, the page title in the browser tab was set to Interstellar Wars. However, once we unmounted the movie details component, we would want the title to revert to the original text, which was simply usePopcorn, the name of the application.
We can achieve this by returning a so-called cleanup function from the effect. In this case, it is simply a function that sets the title back to usePopcorn.
cleanup function is the function that we can return from an effect. But cleanup function is optional. cleanup function runs on 2 different occasions
Before the effect is executed again, to clean up the results of the previous side effect.
Right after the component instance has unmounted, allowing us to reset the side effect if necessary. When the component unmounts then cleanup function is executed.
Cleanup function is necessary whenever the side effect keeps happening after the component has been re-rendered or unmounted.
 For example, if you perform an HTTP request in your effect and the component re-renders while the first request is still running, a second request would be fired off. This can create a bug called a race condition. Therefore, it is a good idea to cancel the request in a cleanup function whenever the component re-renders or unmounts. There are many other examples:
When you subscribe to an API service, you should cancel the subscription.
When you start a timer, you should stop the timer in the cleanup function.
If you add an event listener, you should remove it in the cleanup function.
Each useEffect should do only one thing. If we want to use multiple useEffect then use different useEffect. Which makes the cleanup function to cleanup.



useEffect(
    function () {
      if (!title) return;
      document.title = `Movie ${title}`;

      return function () {
        document.title = "usePopcorn";
      };
    },
    [title]
  );




The below code is cleanup 

 return function () {
        document.title = "usePopcorn";
      };


Closure means a function will always remember all the variables that represent the place where it was created.

cleanup function is used in this example where we search say inception when we enter i, then n , then c and so on each time the useEffect fetch api gets triggered to overcome this we call 'AbortController' in useEffect like below

  const controller = new AbortController();

 const res = await fetch(
            `http://www.omdbapi.com/?i=tt3896198&apikey=${KEY}&s=${query}`,
            { signal: controller.signal }
          );

 return function () {
        controller.abort();
      };


Full example:-

 useEffect(
    function () {
      const controller = new AbortController();
      async function fetchMovies() {
        try {
          setIsLoading(true); //setting up loading message
          const res = await fetch(
            `http://www.omdbapi.com/?i=tt3896198&apikey=${KEY}&s=${query}`,
            { signal: controller.signal }
          );
          if (!res.ok)
            throw new Error("Something went wrong with fetching data"); //throws error and goes to catch block
          const data = await res.json();
          if (data.Response === "False") throw new Error("Movie not found"); // when the api end point doesnt sent response
          setMovies(data.Search);
          setError("");
        } catch (err) {
          if (err.name !== "AbortError") {
            setError(err.message);
          }
        } finally {
          setIsLoading(false);
          setError(""); //unsetting up loading message
        }
      }
      if (query.length < 3) {
        setMovies([]);
        setError("");
        return;
      }
      fetchMovies();

      return function () {
        controller.abort();
      };
    },
    [query]
  );










React Hooks

React hooks are special built-in functions that allow us to hook into React internal mechanism. React hooks are certain api's that expose some internal React functionality like creating and accessing state from the fibre tree or registering side effects in Fiber tree. Fiber tree is internal to React which is not accessible and can be accessible only through  useState, useEffect. React hooks used to DOM selections and manipulate them. React starts with the word 'use' which helps distinguish react hooks from other functions like useState and useEffect.
We can create custom Hooks with starting the 'use' word.
Give function component the ability to own state and run side effects at different lifecycle points.

Rules of React Hooks

Don't call hooks inside conditionals, loops, nested functions or after an early return. (react hooks called at the top level)
React hooks can be called inside a function component or a custom hook.


When application is rendered React creates a React element tree which is also called the virtual DOM. On the initial render React creates a Fiber tree out of virtual DOM where each element is a fiber. Fiber consists of received Props, a list of work and a link to list of all React hooks used
in the component instance.


React Hooks are functions that enable developers to "hook into" React state and lifecycle features directly from functional components, eliminating the need for class components for managing state and side effects. Introduced in React 16.8, they promote a more functional programming style and improve code readability and reusability.
Key concepts of React Hooks:
State Management: Hooks like useState and useReducer allow functional components to declare and manage state variables.
useState: Provides a way to add state to functional components. It returns a stateful value and a function to update it.
useReducer: An alternative to useState for more complex state logic, often used when state transitions depend on the previous state or involve multiple sub-values.
Side Effects: The useEffect hook handles side effects in functional components, such as data fetching, subscriptions, or manually changing the DOM. It runs after every render by default, but its behavior can be controlled by specifying dependencies.
Context: useContext allows components to subscribe to React Context without nesting multiple Context.Consumer components, making it easier to share data across the component tree.
Performance Optimization: Hooks like useMemo and useCallback help optimize performance by memoizing values and functions, preventing unnecessary re-renders.
Custom Hooks: Developers can create their own custom hooks to extract and reuse stateful logic across multiple components, promoting code organization and reusability. Custom hooks are simply JavaScript functions whose names start with "use" and that call other built-in or custom hooks. 



useState as callback

const [avgRating, setAvgRating] = useState(0);

setAvgRating(Number(imdbRating));
setAvgRating((avgRate) => (avgRate + userRating) / 2);




Localstorage in useEffect


 const [watched, setWatched] = useState(function () {
    const storedValue = localStorage.getItem("watched");
    return storedValue ? JSON.parse(storedValue) : [];
  });

 useEffect(
    function () {
      localStorage.setItem("watched", JSON.stringify(watched));
    },
    [watched]
  );






useRef

useRef gives an object with a mutable .current property that is persisted across renders

Eg:

const myRef = useRef(23);
myRef.current = 1000;

here myRef was set to 23 then set to 1000. The current value will be persistent about multiple renders by using useRef.
Two big use cases of useRef
1. Creating a variable that stays the same between renders (eg: previous state, setTimeout id, etc)
2. Select and store DOM elements.

Refs are data that isn't rendered , usually only appear in event handlers or effects not in JSX.
Dont read or write .current in render logic 
We write useRef in useEffect hook

State v/s Refs

State - persists across renders, updating causes re-renders, immutable, updates are synchronous
Refs - persists across renders, doesn't updates on re-render, mutable, updates aren't synchronous


example of useRef

function Search({ query, setQuery }) {
  const inputEl = useRef(null);

  useEffect(function () {
    inputEl.current.focus();
  }, []);

  return (
    <input
      className="search"
      type="text"
      placeholder="Search movies..."
      value={query}
      onChange={(e) => setQuery(e.target.value)}
      ref={inputEl}
    />
  );
}

useEffect in the above code will get inputEl which is the input element only after Search component's DOM is rendered.


Example of Refs to persist data between renders


//MovieDetails 


 const countRef = useRef(0);

 useEffect(
    function () {
      if (userRating) countRef.current = countRef.current + 1;
    },
    [userRating]
  );





What does useRef return?

useRef(initialValue) returns a mutable object with a single property called .current.

Structure:
{
  current: initialValue
}


So the value you store inside a ref is accessed and updated like:

ref.current

📦 Example
import { useRef } from "react";

function Example() {
  const countRef = useRef(0);

  function increment() {
    countRef.current = countRef.current + 1;
    console.log(countRef.current);
  }

  return <button onClick={increment}>Increase</button>;
}

Output:

countRef.current will update from 0 → 1 → 2 → ...

But the component will NOT re-render when the ref changes




Custom Hook

When I want to reuse a code the question comes whether UI or Logic to reuse. If UI to reuse then COMPONENT to reuse, But if LOGIC to reuse then a question arise whether 'does logic contain any hooks' If Yes Then CUSTOM HOOK 'does logic contain any hooks' If No then REGULAR FUNCTION.
Custom Hook should have one purpose to make it reusable and portable. Rules of hooks apply to custom hooks too. 
Custom hooks in React are used when you want to reuse logic across multiple components without duplicating code. They allow you to extract stateful or side-effect logic into a separate function.

Example of custom hook:-

import { useState, useEffect } from "react";

export function useLocalStorageState(initialState, key) {
  const [value, setValue] = useState(function () {
    const storeItem = localStorage.getItem(key);
    return storeItem ? JSON.parse(storeItem) : initialState;
  });
  useEffect(
    function () {
      localStorage.setItem(key, JSON.stringify(value));
    },
    [value, key]
  );
  return [value, setValue];
}


Example of custom hook:-

import { useState, useEffect } from "react";
const KEY = "77bc98be";
export function useMovies(query, callback) {
  const [movies, setMovies] = useState([]);
  const [isLoading, setIsLoading] = useState(false);
  const [error, setError] = useState("");
  useEffect(
    function () {
      const controller = new AbortController();
      async function fetchMovies() {
        try {
          setIsLoading(true); //setting up loading message
          const res = await fetch(
            `http://www.omdbapi.com/?i=tt3896198&apikey=${KEY}&s=${query}`,
            { signal: controller.signal }
          );
          if (!res.ok)
            throw new Error("Something went wrong with fetching data"); //throws error and goes to catch block
          const data = await res.json();
          if (data.Response === "False") throw new Error("Movie not found"); // when the api end point doesnt sent response
          setMovies(data.Search);
          setError("");
        } catch (err) {
          if (err.name !== "AbortError") {
            setError(err.message);
          }
        } finally {
          setIsLoading(false);
          setError(""); //unsetting up loading message
        }
      }
      if (query.length < 3) {
        setMovies([]);
        setError("");
        return;
      }
      fetchMovies();

      return function () {
        controller.abort();
      };
    },
    [query]
  );
  return { movies, isLoading, error };
}





useReducer Hook


useReducer works with reducer function ( a pure function takes in previous state, action as an argument and return the next state) and the initial state.

const initialState = { count: 0, step: 1 };

 const [count, dispatch] = useReducer(reducer, initialState);

count is current state returned by 'useReducer' hook.
here 'reducer' is the function which takes previous state as first argument,  action as an second argument, the reducer function is called by dispatch function. dispatch function can be used to update the state.

function reducer(state, action) {
  console.log(state, action);

  switch (action.type) {
    case "dec":
      return { ...state, count: state.count - state.step };
    case "inc":
      return { ...state, count: state.count + state.step };
    case "setCount":
      return { ...state, count: action.payload };
    case "setStep":
      return { ...state, step: action.payload };
    case "reset":
      return initialState;
    default:
      throw new Error("Unknown action");
  }
}

'reducer' function is used to takes previous state as first argument (here state),  action as an second argument and then return next state.



const dec = function () {
    dispatch({ type: "dec" });
  };

here '{ type: "dec" }' denotes action when we work with reducer functions.

JSX of DateCounter as follows


  return (
    <div className="counter">
      <div>
        <input
          type="range"
          min="0"
          max="10"
          value={step}
          onChange={defineStep}
        />
        <span>{step}</span>
      </div>

      <div>
        <button onClick={dec}>-</button>
        <input value={count} onChange={defineCount} />
        <button onClick={inc}>+</button>
      </div>

      <p>{date.toDateString()}</p>

      <div>
        <button onClick={reset}>Reset</button>
      </div>
    </div>
  );


Destructure state

  const [state, dispatch] = useReducer(reducer, initialState);
  const { count, step } = state;


 const dec = function () {
    dispatch({ type: "dec" });
  };

  const inc = function () {
    dispatch({ type: "inc" });
  };

  const defineCount = function (e) {
    dispatch({ type: "setCount", payload: Number(e.target.value) });
  };

  const defineStep = function (e) {
    dispatch({ type: "setStep", payload: Number(e.target.value) });
  };

  const reset = function () {
    dispatch({ type: "reset" });
  };




React Routes


creating using vite , command to create vite app is as follows

npm create vite@4

Enter the project name, Select React, Select Javascript

Then do the following command
 npm install

 and for running this command        'npm run dev'

to install eslint in vite command as follows:- 

npm install eslint vite-plugin-eslint eslint-config-react-app --save-dev



create a file called .eslintrc.json and write below in this file


{
  "extends": "react-app"
}


In 'vite.config' file import eslint and add it in plugins array

import eslint from 'vite-plugin-eslint'

export default defineConfig({
  plugins: [react(), eslint()],
});


Routing - with routing we match different URL's to different UI views (React components). When specific URL gets visited corresponding React component gets rendered.
For example: 'www.example.com/' will load the home page. But  'www.example.com/login' will load the login page. If login successful then will redirect to the app page with this url ''www.example.com/app'. Each of these3 url's will render 3 React components. This enables users to navigate between different application screens using the browser URL. Keeps the UI sync with current browser URL.
React Router is a third party package.

Single Page application (SPA) - Application thats executed entirely on client (browsers).  SPA relies on Routes different URl's correspond to different views (components).
SPA running in client - Whenever user clicks in special link provided by the router, url in the browser changes this is done by React Router. Changing the URL will update DOM as a result. In React, JavaScript used to update the page (DOM).

 In SPA, when React Router routes to a page the page is updated by JavaScript which means there will not be a complete page reload. 
When there is an external data to be loaded on the page say from web API. SPA runs entirely on client, it can always communicate with a server in order to fetch data that it needs. But in this case also the entire page will not be loaded since its a SPA.


Create a folder 'pages' inside src and inside 'pages' folder create 3 files Product.jsx, Pricing.jsx, Homepage.jsx, PageNotFound.jsx

Then install React Router package 

npm install react-router-dom@6



In App.jsx we 'BrowserRouter' to enclose the routes and then 'Routes' and then 'Route'
In 'Route' we give url as 'path' and element to be loaded when hitting url as 'product' , the element is 'Product' the component loaded is 'Product.jsx' (which is Product.jsx).
'<Route path="*" element={<PageNotFound />} />' denotes for all other path excluding 'product', 'pricing', '/' is redirected to 'PageNotFound' component by using '*' in 'path'.


App.jsx


import { BrowserRouter, Routes, Route } from "react-router-dom";
import Product from "./pages/Product";
import Homepage from "./pages/Homepage";
import Pricing from "./pages/Pricing";
import PageNotFound from "./pages/PageNotFound";
export default function App() {
  return (
    <div>
      <h1>Hello Router!!</h1>
      <BrowserRouter>
        <Routes>
          <Route path="/" element={<Homepage />} />
          <Route path="product" element={<Product />} />
          <Route path="pricing" element={<Pricing />} />
          <Route path="*" element={<PageNotFound />} />
        </Routes>
      </BrowserRouter>
    </div>
  );
}



Linking between Routes

When we use anchor tag to redirect to component where we give path leads to hard reload which isn't as expected for SPA. 'Link element provided by React Router package.

'<Link to="/pricing">Pricing</Link>' here redirected to '/pricing' url when clicking on the 'Pricing' link. Thus 'Link' instead of anchor tag makes the application SPA.


Homepage.jsx


import { Link } from "react-router-dom";

export default function Homepage() {
  return (
    <div>
      <h2>WorldWise</h2>
      <Link to="/pricing">Pricing</Link>
      <Link to="/product">Product</Link>
    </div>
  );
}


Now moving the links to another new component 'PageNav' (where 'PageNav' component created in a new folder 'components' in 'src' folder)


components/PageNav.jsx

import { Link } from "react-router-dom";

export default function PageNav() {
  return (
    <div>
      <ul>
        <li>
          <Link to="/">Home</Link>
        </li>
        <li>
          <Link to="/pricing">Pricing</Link>
        </li>
        <li>
          <Link to="/product">Product</Link>
        </li>
      </ul>
    </div>
  );
}




Homepage.jsx

import PageNav from "../components/PageNav";
export default function Homepage() {
  return (
    <div>
      <PageNav />
      <h2>WorldWise</h2>
    </div>
  );
}



To display the currently visited link we can use instead of 'Link' with 'NavLink'

components/PageNav.jsx

import { NavLink } from "react-router-dom";

export default function PageNav() {
  return (
    <div>
      <ul>
        <li>
          <NavLink to="/">Home</NavLink>
        </li>
        <li>
          <NavLink to="/pricing">Pricing</NavLink>
        </li>
        <li>
          <NavLink to="/product">Product</NavLink>
        </li>
      </ul>
    </div>
  );
}




Add CSS module for 'PageNav.jsx' in 'components' folder , CSS module name PageNav.module.css


components/PageNav.jsx


import { NavLink } from "react-router-dom";
import styles from "./PageNav.module.css";
export default function PageNav() {
  return (
    <div className={styles.nav}>
      <ul>
        <li>
          <NavLink to="/">Home</NavLink>
        </li>
        <li>
          <NavLink to="/pricing">Pricing</NavLink>
        </li>
        <li>
          <NavLink to="/product">Product</NavLink>
        </li>
      </ul>
    </div>
  );
}



components/PageNav.module.css


.nav {
}

.nav ul {
  display: flex;
  justify-content: space-between;
  list-style: none;
}
:global(.test) {
  background-color: aquamarine;
}



'test' will be globally used by class as shown in Homepage.jsx below.


Create 'MapLayout.jsx' in 'pages' folder.

pages/MapLayout.jsx


import AppNav from "../components/AppNav";

export default function AppLayoutPage() {
  return (
    <div>
      <AppNav />
    </div>
  );
}

create 'AppNav.jsx' and 'AppNav.module.css' in 'components' folder
 

/components/AppNav.jsx


import styles from "./AppNav.module.css";

export default function AppNav() {
  return <nav className={styles.nav}>Nav</nav>;
}



components/AppNav.module.css

.nav {
  background-color: rebeccapurple;
}


pages/App.js

import { BrowserRouter, Routes, Route } from "react-router-dom";
import Product from "./pages/Product";
import Homepage from "./pages/Homepage";
import Pricing from "./pages/Pricing";
import PageNotFound from "./pages/PageNotFound";
import AppLayout from "./pages/MapLayout";
export default function App() {
  return (
    <div>
      <h1>Hello Router!!</h1>
      <BrowserRouter>
        <Routes>
          <Route path="/" element={<Homepage />} />
          <Route path="product" element={<Product />} />
          <Route path="pricing" element={<Pricing />} />
          <Route path="app" element={<AppLayout />} />
          <Route path="*" element={<PageNotFound />} />
        </Routes>
      </BrowserRouter>
    </div>
  );
}


Homepage.jsx

import { Link } from "react-router-dom";
import PageNav from "../components/PageNav";
import AppNav from "../components/AppNav";
export default function Homepage() {
  return (
    <div>
      <PageNav />
      <AppNav />
      <h2 className="test">WorldWise</h2>
      <Link to="/app">Go to App</Link>
    </div>
  );
}




Changed Homepage.jsx to follows

import { Link } from "react-router-dom";
import PageNav from "../components/PageNav";
import styles from "./Homepage.module.css";

export default function Homepage() {
  return (
    <main className={styles.homepage}>
      <PageNav />
      <section>
        <h1>
          You travel the world.
          <br />
          WorldWise keeps track of your adventures.
        </h1>
        <h2>
          A world map that tracks your footsteps into every city you can think
          of. Never forget your wonderful experiences, and show your friends how
          you have wandered the world.
        </h2>
        <Link to="/app" className="cta">
          Start Tracking
        </Link>
      </section>
    </main>
  );
}



components/PageNav.jsx


import { NavLink } from "react-router-dom";
import styles from "./PageNav.module.css";
import Logo from "./Logo";
export default function PageNav() {
  return (
    <div className={styles.nav}>
      <ul>
        <Logo />
        <li>
          <NavLink to="/pricing">Pricing</NavLink>
        </li>
        <li>
          <NavLink to="/product">Product</NavLink>
        </li>
        <li>
          <NavLink to="/login" className={styles.ctaLink}>
            Login
          </NavLink>
        </li>
      </ul>
    </div>
  );
}




components/Logo.jsx



import styles from "./Logo.module.css";

function Logo() {
   return (
    <Link to="/">
      <img src="/logo.png" alt="WorldWise logo" className={styles.logo} />
    </Link>
  );
}

export default Logo;




pages/Product.jsx



import styles from "./Product.module.css";

export default function Product() {
  return (
    <main className={styles.product}>
      <section>
        <img
          src="img-1.jpg"
          alt="person with dog overlooking mountain with sunset"
        />
        <div>
          <h2>About WorldWide.</h2>
          <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Illo est
            dicta illum vero culpa cum quaerat architecto sapiente eius non
            soluta, molestiae nihil laborum, placeat debitis, laboriosam at fuga
            perspiciatis?
          </p>
          <p>
            Lorem, ipsum dolor sit amet consectetur adipisicing elit. Corporis
            doloribus libero sunt expedita ratione iusto, magni, id sapiente
            sequi officiis et.
          </p>
        </div>
      </section>
    </main>
  );
}




pages/Pricing.js


// Uses the same styles as Product
import styles from "./Product.module.css";

export default function Product() {
  return (
    <main className={styles.product}>
      <section>
        <div>
          <h2>
            Simple pricing.
            <br />
            Just $9/month.
          </h2>
          <p>
            Lorem ipsum dolor, sit amet consectetur adipisicing elit. Vitae vel
            labore mollitia iusto. Recusandae quos provident, laboriosam fugit
            voluptatem iste.
          </p>
        </div>
        <img src="img-2.jpg" alt="overview of a large city with skyscrapers" />
      </section>
    </main>
  );
}



App.jsx

import { BrowserRouter, Routes, Route } from "react-router-dom";
import Product from "./pages/Product";
import Homepage from "./pages/Homepage";
import Pricing from "./pages/Pricing";
import PageNotFound from "./pages/PageNotFound";
import AppLayout from "./pages/MapLayout";
import Login from "./pages/Login";
export default function App() {
  return (
    <div>
      <BrowserRouter>
        <Routes>
          <Route path="/" element={<Homepage />} />
          <Route path="product" element={<Product />} />
          <Route path="pricing" element={<Pricing />} />
          <Route path="app" element={<AppLayout />} />
          <Route path="login" element={<Login />} />
          <Route path="*" element={<PageNotFound />} />
        </Routes>
      </BrowserRouter>
    </div>
  );
}








Nested Routes

<Route path="app" element={<AppLayout />}>
            <Route path="cities" element={<p>List of cities</p>}/>
            <Route path="countries" element={<p>Countries</p>} />
            <Route path="form" element={<p>Form</p>} />
</Route>

'cities', 'countries', 'form' are 3 nested routes in parent route 'app'




App.jsx

import { BrowserRouter, Routes, Route } from "react-router-dom";
import Product from "./pages/Product";
import Homepage from "./pages/Homepage";
import Pricing from "./pages/Pricing";
import PageNotFound from "./pages/PageNotFound";
import AppLayout from "./pages/MapLayout";
import Login from "./pages/Login";
export default function App() {
  return (
    <div>
      <BrowserRouter>
        <Routes>
          <Route path="/" element={<Homepage />} />
          <Route path="product" element={<Product />} />
          <Route path="pricing" element={<Pricing />} />
          <Route path="app" element={<AppLayout />}>
            <Route path="cities" element={<p>List of cities</p>} />
            <Route path="countries" element={<p>Countries</p>} />
            <Route path="form" element={<p>Form</p>} />
          </Route>
          <Route path="login" element={<Login />} />
          <Route path="*" element={<PageNotFound />} />
        </Routes>
      </BrowserRouter>
    </div>
  );
}




Place one component to another component

For example in the above code 'cities', 'countires', 'form' nested routes in app routes to be displayed in 'Sidebar' component. Hence we use the tag '<Outlet /> ' in 'Sidebar' component. (like below)


components/Sidebar.jsx

import AppNav from "./AppNav";
import Logo from "./Logo";
import styles from "./Sidebar.module.css";
import Footer from "./Footer";
import { Outlet } from "react-router-dom";
export default function Sidebar() {
  return (
    <div className={styles.sidebar}>
      <Logo />
      <AppNav />
      <Outlet />

      <Footer />
    </div>
  );
}


when browser url is searched for 'http://localhost:5173/app/cities' then 'app' in the url will go to  'AppLayout' in App.jsx file then the url for 'cities' entered after 'app' then it will print the element we used in 'cities' route in App.jsx which is '<p>List of cities</p>'. So, 'List of cities' is printed.

Index route is the route that will be loaded if any default route in nested route isn't matched. like 'http://localhost:5173/app' without nested url in the url link


example like this ' <Route index element={<p>List of cities</p>} />', shown below:-

 <Route path="app" element={<AppLayout />}>
            <Route index element={<p>List of cities</p>} />
            <Route path="cities" element={<p>List of cities</p>} />
            <Route path="countries" element={<p>Countries</p>} />
            <Route path="form" element={<p>Form</p>} />
          </Route>



Full example of App.js


import { BrowserRouter, Routes, Route } from "react-router-dom";
import Product from "./pages/Product";
import Homepage from "./pages/Homepage";
import Pricing from "./pages/Pricing";
import PageNotFound from "./pages/PageNotFound";
import AppLayout from "./pages/MapLayout";
import Login from "./pages/Login";
export default function App() {
  return (
    <div>
      <BrowserRouter>
        <Routes>
          <Route index element={<Homepage />} />
          <Route path="product" element={<Product />} />
          <Route path="pricing" element={<Pricing />} />
          <Route path="app" element={<AppLayout />}>
            <Route index element={<p>List of cities</p>} />
            <Route path="cities" element={<p>List of cities</p>} />
            <Route path="countries" element={<p>Countries</p>} />
            <Route path="form" element={<p>Form</p>} />
          </Route>
          <Route path="login" element={<Login />} />
          <Route path="*" element={<PageNotFound />} />
        </Routes>
      </BrowserRouter>
    </div>
  );
}




To add 'cities' and 'countries' links in side bar in AppNav.jsx we add the following line of code


AppNav.jsx


import { NavLink } from "react-router-dom";
import styles from "./AppNav.module.css";

export default function AppNav() {
  return (
    <nav className={styles.nav}>
      <ul>
        <li>
          <NavLink to="cities">Cities</NavLink>
        </li>
        <li>
          <NavLink to="countries">Countries</NavLink>
        </li>
      </ul>
    </nav>
  );
}




Pass CityList component in App.jsx


App.jsx


import { BrowserRouter, Routes, Route } from "react-router-dom";
import Product from "./pages/Product";
import Homepage from "./pages/Homepage";
import Pricing from "./pages/Pricing";
import PageNotFound from "./pages/PageNotFound";
import AppLayout from "./pages/MapLayout";
import CityList from "./components/CityList";
import Login from "./pages/Login";
export default function App() {
  return (
    <div>
      <BrowserRouter>
        <Routes>
          <Route index element={<Homepage />} />
          <Route path="product" element={<Product />} />
          <Route path="pricing" element={<Pricing />} />
          <Route path="app" element={<AppLayout />}>
            <Route index element={<CityList />} />
            <Route path="cities" element={<CityList />} />
            <Route path="countries" element={<p>Countries</p>} />
            <Route path="form" element={<p>Form</p>} />
          </Route>
          <Route path="login" element={<Login />} />
          <Route path="*" element={<PageNotFound />} />
        </Routes>
      </BrowserRouter>
    </div>
  );
}





CityList.jsx


import styles from "./CityList.module.css";

export default function CityList() {
  return <ul className={styles.cityList}>List of customers</ul>;
}




Then to create a fake api call we need to install json-server, so type the following command


npm install json-server@latest --save-dev


Add data/cities.json in root


data/cities.json



{
  "cities": [
    {
      "cityName": "Lisbon",
      "country": "Portugal",
      "emoji": "🇵🇹",
      "date": "2027-10-31T15:59:59.138Z",
      "notes": "My favorite city so far!",
      "position": {
        "lat": 38.727881642324164,
        "lng": -9.140900099907554
      },
      "id": 73930385
    },
    {
      "cityName": "Madrid",
      "country": "Spain",
      "emoji": "🇪🇸",
      "date": "2027-07-15T08:22:53.976Z",
      "notes": "",
      "position": {
        "lat": 40.46635901755316,
        "lng": -3.7133789062500004
      },
      "id": 17806751
    },
    {
      "cityName": "Berlin",
      "country": "Germany",
      "emoji": "🇩🇪",
      "date": "2027-02-12T09:24:11.863Z",
      "notes": "Amazing 😃",
      "position": {
        "lat": 52.53586782505711,
        "lng": 13.376933665713324
      },
      "id": 98443197
    }
  ]
}




Then in 'package.json' in the 'scripts' we need to add the "server" value with the following 

"scripts" : {
"server": "json-server --watch data/cities.json --port 8000 -delay 500"
}

Then take a new terminal and run the following command

npm run server







URL for state management


URL is an excellent place to store UI state and an alternative to useState in some situations. Eg: - open/closed panels, currently selected list item, list sorting order, applied list filter.

URL for state management is an easy way to store state in global place accessible to all components in the app. Good way to pass data from one page to next page without storing it in a variable in the app.  Also makes it possible to bookmark and share the page with the exact UI i had the time. example : - Filtering from shopping site by color and price, if the filtered data is there in the URL then we can share that page and the person we shared will see the exact same filters used by the sharing person.

Example

www.example.com/app/cities/lisbon?lat=38.728&lng=-9.141

where 'app/cities' are the path, params here is 'lisbon' and query string is 'lat=38.728&lng=-9.141'.
'params' stands for parameters are very useful to pass data to next page, while the query string is useful to store some global state that should be accessible everywhere


Dynamic route with URL parameters


Params in uRL done in 3 steps
 Create a new Route , link to that route and read the state from the url.
like below

Create a new Route:-

 <Route path="cities/:id" element={<City />} />

this matches with http://localhost:5173/app/cities/123


 Create a new Route:-


App.jsx


import { useEffect, useState } from "react";
import { BrowserRouter, Routes, Route } from "react-router-dom";
import Product from "./pages/Product";
import Homepage from "./pages/Homepage";
import Pricing from "./pages/Pricing";
import PageNotFound from "./pages/PageNotFound";
import AppLayout from "./pages/MapLayout";
import CityList from "./components/CityList";
import Login from "./pages/Login";
import CountriesList from "./components/CountriesList";
import City from "./components/City";
export default function App() {
  const [cities, setCities] = useState([]);
  const [isLoading, setIsLoading] = useState(false);

  const BASE_URL = "http://localhost:9000";

  useEffect(function () {
    async function fetchCities() {
      setIsLoading(true);
      try {
        const res = await fetch(`${BASE_URL}/cities`);
        const data = await res.json();
        setCities(data);
      } catch (err) {
        console.log(err);
      } finally {
        setIsLoading(false);
      }
    }
    fetchCities();
  }, []);

  return (
    <div>
      <BrowserRouter>
        <Routes>
          <Route index element={<Homepage />} />
          <Route path="product" element={<Product />} />
          <Route path="pricing" element={<Pricing />} />
          <Route path="app" element={<AppLayout />}>
            <Route
              index
              element={<CityList cities={cities} isLoading={isLoading} />}
            />
            <Route
              path="cities"
              element={<CityList cities={cities} isLoading={isLoading} />}
            />
            <Route path="cities/:id" element={<City />} />
            <Route
              path="countries"
              element={<CountriesList cities={cities} isLoading={isLoading} />}
            />
            <Route path="form" element={<p>Form</p>} />
          </Route>
          <Route path="login" element={<Login />} />
          <Route path="*" element={<PageNotFound />} />
        </Routes>
      </BrowserRouter>
    </div>
  );
}



CityList.jsx



/* eslint-disable react/prop-types */
import styles from "./CityList.module.css";
import Spinner from "./Spinner";
import CityItem from "./CityItem";
import Message from "./Message";
export default function CityList({ cities, isLoading }) {
  if (isLoading) return <Spinner />;

  if (!cities.length)
    return (
      <Message message="Add your first city by clicking on a city on the map" />
    );
  return (
    <ul className={styles.cityList}>
      {cities.map((city) => {
        return <CityItem key={city.id} city={city} />;
      })}
    </ul>
  );
}



link to that route shown below  

CityItem.jsx

/* eslint-disable react/prop-types */
import { Link } from "react-router-dom";
import styles from "./CityItem.module.css";
const formatDate = (date) =>
  new Intl.DateTimeFormat("en", {
    day: "numeric",
    month: "long",
    year: "numeric",
  }).format(new Date(date));
export default function CityItem({ city }) {
  const { cityName, emoji, date, id } = city;

  return (
    <li>
      <Link className={styles.cityItem} to={`${id}`}>
        <span className={styles.emoji}>{emoji}</span>
        <h3 className={styles.name}>{cityName}</h3>
        <time className={styles.date}>{formatDate(date)}</time>
        <button className={styles.deleteBtn}>&times;</button>
      </Link>
    </li>
  );
}



City.jsx

function City() {
    return (
    <h1>City</h1>
    
  );
}

export default City;



To get the 'id' from the url we use 'useParams()'

City.jsx


/* eslint-disable react/prop-types */

import { useParams } from "react-router-dom";

function City() {
  const { id } = useParams();
  return (
    <h1>city - {id}</h1>
  );
}

export default City;





Query string

Here in the below example we are passing lat and lng to the url in the 'Link' as a query string


 <Link
        className={styles.cityItem}
        to={`${id}?lat=${position.lat}&lng=${position.lng}`}
      >
        <span className={styles.emoji}>{emoji}</span>
        <h3 className={styles.name}>{cityName}</h3>
        <time className={styles.date}>{formatDate(date)}</time>
        <button className={styles.deleteBtn}>&times;</button>
      </Link>


Then when clicking on particular city in the city tab and sidebar then we will get the following in the url

http://localhost:5173/app/cities/73930385?lat=38.727881642324164&lng=-9.140900099907554



Full code of CItyItem.jsx


/* eslint-disable react/prop-types */
import { Link } from "react-router-dom";
import styles from "./CityItem.module.css";
const formatDate = (date) =>
  new Intl.DateTimeFormat("en", {
    day: "numeric",
    month: "long",
    year: "numeric",
  }).format(new Date(date));
export default function CityItem({ city }) {
  const { cityName, emoji, date, id, position } = city;

  return (
    <li>
      <Link
        className={styles.cityItem}
        to={`${id}?lat=${position.lat}&lng=${position.lng}`}
      >
        <span className={styles.emoji}>{emoji}</span>
        <h3 className={styles.name}>{cityName}</h3>
        <time className={styles.date}>{formatDate(date)}</time>
        <button className={styles.deleteBtn}>&times;</button>
      </Link>
    </li>
  );
}



To read 'lat' and 'lng' from the url in Map.jsx we use 'useSearchParams()' hook. useSearchParams()' returns an array (i.e searchParams) and a function to search the params (i.e setSearchParams)

const [searchParams, setSearchParams] = useSearchParams();

 Then get the value from the variable 'lat' and 'lng' using 'get' from the array 'searchParams' as shown below

 const lat = searchParams.get("lat");
 const lng = searchParams.get("lng");


'setSearchParams' used to set the value of the query parameters. When button clicked in the below code we set varaibles 'lat' as 23 an 'lng' as 50. Thus, it change in the url as well as HTML page (since given in Map JSX).


Map.jsx

import { useSearchParams } from "react-router-dom";
import styles from "./Map.module.css";

export default function Map() {
  const [searchParams, setSearchParams] = useSearchParams();
  const lat = searchParams.get("lat");
  const lng = searchParams.get("lng");
  return (
    <div className={styles.mapContainer}>
      <h1>
        Position: {lat} {lng}
      </h1>
<button
        onClick={() => {
          setSearchParams({ lat: 23, lng: 50 });
        }}
      >
        Change position
      </button>
    </div>
  );
}




Programmatic Navigation

To move from one url to another url without user click.
'useNavigate' will return a function and when clicking on map in the right the sidebar should navigate to 'Form' component for that we do the following

  const navigate = useNavigate();

'navigate' is a function which given on button click will navigate to the url mentioned in 'navigate' function. In the below code redirected to 'form' url in sidebar component.


 <div className={styles.mapContainer} onClick={()=>{
      navigate("form")
    }}>
      <h1>
        Position: {lat} {lng}
      </h1>
      <button
        onClick={() => {
          setSearchParams({ lat: 23, lng: 50 });
        }}
      >
        Change position
      </button>
    </div>




Full example Map.jsx


import { useNavigate, useSearchParams } from "react-router-dom";
import styles from "./Map.module.css";

export default function Map() {
  const navigate = useNavigate();
  const [searchParams, setSearchParams] = useSearchParams();
  const lat = searchParams.get("lat");
  const lng = searchParams.get("lng");
  return (
    <div
      className={styles.mapContainer}
      onClick={() => {
        navigate("form");
      }}
    >
      <h1>
        Position: {lat} {lng}
      </h1>
      <button
        onClick={() => {
          setSearchParams({ lat: 23, lng: 50 });
        }}
      >
        Change position
      </button>
    </div>
  );
}





Reusable 'Button' component in 'Form' component. ' navigate(-1)' will move one back since given -1.


function Form() {
  const navigate = useNavigate();
return (
<div className={styles.buttons}>
        <Button type="primary">Add</Button>
        <Button type="back" onClick={(e) => {
            e.preventDefault();
            navigate(-1);
          }}>Back</Button>
</div>

);
Button.jsx

/* eslint-disable react/prop-types */
import styles from "./Button.module.css";
export default function Button({ children, onClick, type }) {
  return (
    <button className={`${styles.btn} ${styles[type]}`} onClick={onClick}>
      {children}
    </button>
  );
}


Button.module.css

.btn {
  color: inherit;
  text-transform: uppercase;
  padding: 0.8rem 1.6rem;
  font-family: inherit;
  font-size: 1.5rem;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.primary {
  font-weight: 700;
  background-color: var(--color-brand--2);
  color: var(--color-dark--1);
}

.back {
  font-weight: 600;
  background: none;
  border: 1px solid currentColor;
}

.position {
  font-weight: 700;
  position: absolute;
  z-index: 1000;
  font-size: 1.4rem;
  bottom: 4rem;
  left: 50%;
  transform: translateX(-50%);
  background-color: var(--color-brand--2);
  color: var(--color-dark--1);
  box-shadow: 0 0.4rem 1.2rem rgba(36, 42, 46, 0.16);
}






<Navigate />

Here 'Navigate is a redirect. 
In App.jsx instead of this below code

<Route index element={<CityList cities={cities} isLoading={isLoading} />}
/>

we change to Navigate as follows, Here 'Navigate is a redirect. here in the below code navigates to 'cities'. 'replace will replace the current history stack

 <Route index element={<Navigate replace to="cities" />} />












Context API

Context API is the solution to PROP drilling

Passing state into multiple deeply nested child components which is called Prop Drilling.
Solution to the Prop drilling is directly passing the props to nested child components, which can be done by Context API.
 Context API allows components everywhere in the tree to reach the state context shares.
Context api is the system to pass data throughout the app without manually passing props down the tree. Allows to broadcast global state to the entire app.
First part of the Context API is 'provider', second part is the value and third part is consumers.
Provider : gives all child components access to value and this provider can sit everywhere in the component tree. But its better to place 'Provider' in the top.
Value : Data that we want to make available (usually state and functions). Data we want to broadcast through the 'Provider', so we pass the value to 'Provider'.
Consumers : All components that read the provided context 'value'. Consumers are the components that subscribe to the context. We can create as many 'consumers' as we want.

But when context 'value' changes ( 'value' is updated) all the consumer components will be re-rendered ('value' read components).
When the value used in the child components are updated, then the provider will immediately notify the 'consumers' about the 'value' change and then will re-render those components.

1. Create a new Context

createContext()

'createContext()' will not pass any value, since giving value to this will not update the value since default value is set. So we pass either empty / null inside as an argument createContext(). 'createContext()' will pass a context (as follows).

const PostContext = createContext();

Here 'PostContext' is a component, hence 'PostContext' starts with uppercase.


2. Pass value to context

Place the '<PostContext.Provider>' tag between the component where you have to pass data here its 'App.js'.
And then pass value to this provider and then value to child components.
Like below

<PostContext.Provider
      value={{
        posts: searchedPosts,
        onAddPost: handleAddPost,
        onClearPosts: handleClearPosts,
        searchQuery: searchQuery,
        setSearchQuery: setSearchQuery,
      }}
    >

the above can replaced also like below since 'searchQuery' and 'setSearchQuery' key and parameter passed is same.

<PostContext.Provider
      value={{
        posts: searchedPosts,
        onAddPost: handleAddPost,
        onClearPosts: handleClearPosts,
        searchQuery,
        setSearchQuery,
      }}
    >



App.js



const PostContext = createContext();
function App() {
  const [posts, setPosts] = useState(() =>
    Array.from({ length: 30 }, () => createRandomPost())
  );
  const [searchQuery, setSearchQuery] = useState("");
  const [isFakeDark, setIsFakeDark] = useState(false);

  // Derived state. These are the posts that will actually be displayed
  const searchedPosts =
    searchQuery.length > 0
      ? posts.filter((post) =>
          `${post.title} ${post.body}`
            .toLowerCase()
            .includes(searchQuery.toLowerCase())
        )
      : posts;

  function handleAddPost(post) {
    setPosts((posts) => [post, ...posts]);
  }

  function handleClearPosts() {
    setPosts([]);
  }

  // Whenever `isFakeDark` changes, we toggle the `fake-dark-mode` class on the HTML element (see in "Elements" dev tool).
  useEffect(
    function () {
      document.documentElement.classList.toggle("fake-dark-mode");
    },
    [isFakeDark]
  );

  return (
    <PostContext.Provider
      value={{
        posts: searchedPosts,
        onAddPost: handleAddPost,
        onClearPosts: handleClearPosts,
        searchQuery: searchQuery,
        setSearchQuery: setSearchQuery,
      }}
    >
      <section>
        <button
          onClick={() => setIsFakeDark((isFakeDark) => !isFakeDark)}
          className="btn-fake-dark-mode"
        >
          {isFakeDark ? "☀️" : "🌙"}
        </button>

        <Header
          posts={searchedPosts}
          onClearPosts={handleClearPosts}
          searchQuery={searchQuery}
          setSearchQuery={setSearchQuery}
        />
        <Main posts={searchedPosts} onAddPost={handleAddPost} />
        <Archive onAddPost={handleAddPost} />
        <Footer />
      </section>
    </PostContext.Provider>
  );
}



3. Consuming the Context



Header.js to be replaced the old one is as follows

Header.js


function Header({ posts, onClearPosts, searchQuery, setSearchQuery }) {
  return (
    <header>
      <h1>
        <span>⚛️</span>The Atomic Blog
      </h1>
      <div>
        <Results posts={posts} />
        <SearchPosts
          searchQuery={searchQuery}
          setSearchQuery={setSearchQuery}
        />
        <button onClick={onClearPosts}>Clear posts</button>
      </div>
    </header>
  );
}



In App.jsx the following code portion as below


<Header
          posts={searchedPosts}
          onClearPosts={handleClearPosts}
          searchQuery={searchQuery}
          setSearchQuery={setSearchQuery}
        />

to be replaced like this

<Header />


To read the value in "Header' component we use 'useContext(PostContext);'
In "Header' component we need only 'onClearPosts'. So destructuring and reading the context value. In 'Header' component does not need 'searchQuery', 'setSearchQuery' and 'posts' (since we need not in parent component (i.e Header) , only required in child components (i.e 'Results', 'SearchPosts'). Consuming the context shown below. 

const { onClearPosts } = useContext(PostContext);


Header.js

function Header() {
  const { onClearPosts } = useContext(PostContext);
  return (
    <header>
      <h1>
        <span>⚛️</span>The Atomic Blog
      </h1>
      <div>
        <Results />
        <SearchPosts />
        <button onClick={onClearPosts}>Clear posts</button>
      </div>
    </header>
  );
}



SearchPosts.js

function SearchPosts() {
  const { searchQuery, setSearchQuery } = useContext(PostContext);
  return (
    <input
      value={searchQuery}
      onChange={(e) => setSearchQuery(e.target.value)}
      placeholder="Search posts..."
    />
  );
}


Results.js

function Results() {
  const { posts } = useContext(PostContext);
  return <p>🚀 {posts.length} atomic posts found</p>;
}




What is Context API?

React’s Context API is used for state sharing between components without prop drilling.

Instead of passing props through every level (Parent → Child → Grandchild → etc.),
you can share data directly using a context provider.

🧩 Real-Life Analogy

Think of Context as a “global message board.”
The Provider puts data on the board,
and Consumers (children) can read or update it directly.

🧱 Basic Structure
1️⃣ Create the Context
import React, { createContext, useState } from "react";

// Step 1: Create context
export const MessageContext = createContext();

// Step 2: Create provider component
export function MessageProvider({ children }) {
  const [message, setMessage] = useState("Hello from Parent (Context)!");

  return (
    <MessageContext.Provider value={{ message, setMessage }}>
      {children}
    </MessageContext.Provider>
  );
}

2️⃣ Use the Provider in Parent (App.js)
import React from "react";
import { MessageProvider } from "./MessageContext";
import Child from "./Child";

function App() {
  return (
    <MessageProvider>
      <h1>🏦 Using Context API</h1>
      <Child />
    </MessageProvider>
  );
}

export default App;

3️⃣ Access and Update Context in Child (Child.js)
import React, { useContext } from "react";
import { MessageContext } from "./MessageContext";

function Child() {
  const { message, setMessage } = useContext(MessageContext);

  return (
    <div>
      <h2>Child Component</h2>
      <p>Parent message: {message}</p>
      <button onClick={() => setMessage("Message updated by Child!")}>
        Update Parent Message
      </button>
    </div>
  );
}

export default Child;

🧠 How It Works

MessageProvider holds the shared state (message and setMessage).

The child uses useContext(MessageContext) to access and modify that state.

When the child updates it (setMessage), the parent and all other components using the same context automatically re-render with the new data.




Custom Provider


Duplicate App.js into App-v1.js and add another file 'PostProvider.js'

Splitting the above App.js into another file where we will add a custom Provider with the file 'PostProvider.js'. So, 'PostProvider.js' shown below is a custom context provider component.


PostProvider.js



import { createContext, useState } from "react";
import { faker } from "@faker-js/faker";
const PostContext = createContext();
function createRandomPost() {
  return {
    title: `${faker.hacker.adjective()} ${faker.hacker.noun()}`,
    body: faker.hacker.phrase(),
  };
}
function PostProvider({ children }) {
  const [posts, setPosts] = useState(() =>
    Array.from({ length: 30 }, () => createRandomPost())
  );
  const [searchQuery, setSearchQuery] = useState("");

  // Derived state. These are the posts that will actually be displayed
  const searchedPosts =
    searchQuery.length > 0
      ? posts.filter((post) =>
          `${post.title} ${post.body}`
            .toLowerCase()
            .includes(searchQuery.toLowerCase())
        )
      : posts;

  function handleAddPost(post) {
    setPosts((posts) => [post, ...posts]);
  }

  function handleClearPosts() {
    setPosts([]);
  }
  return (
    <PostContext.Provider
      value={{
        posts: searchedPosts,
        onAddPost: handleAddPost,
        onClearPosts: handleClearPosts,
        searchQuery: searchQuery,
        setSearchQuery: setSearchQuery,
      }}
    >
      {children}
    </PostContext.Provider>
  );
}

export { PostProvider, PostContext };




App.js

function App() {
  const [isFakeDark, setIsFakeDark] = useState(false);
  // Whenever `isFakeDark` changes, we toggle the `fake-dark-mode` class on the HTML element (see in "Elements" dev tool).
  useEffect(
    function () {
      document.documentElement.classList.toggle("fake-dark-mode");
    },
    [isFakeDark]
  );

  return (
    <section>
      <button
        onClick={() => setIsFakeDark((isFakeDark) => !isFakeDark)}
        className="btn-fake-dark-mode"
      >
        {isFakeDark ? "☀️" : "🌙"}
      </button>
      <PostProvider>
        <Header />
        <Main />
        <Archive />
        <Footer />
      </PostProvider>
    </section>
  );
}



'PostProvider' tag in App.js are wrapped around 'Header', 'Main', 'Archive', 'Footer', hence 'Header', 'Main', 'Archive', 'Footer' will be child for 'PostProvider' tag. In 'PostProvider.js' file we have children which will include all of the child components (here 'Header', 'Main', 'Archive', 'Footer' )


Header.js

function Header() {
  const { onClearPosts } = useContext(PostContext);
  return (
    <header>
      <h1>
        <span>⚛️</span>The Atomic Blog
      </h1>
      <div>
        <Results />
        <SearchPosts />
        <button onClick={onClearPosts}>Clear posts</button>
      </div>
    </header>
  );
}


In the above code 'Header.js' we see the following const { onClearPosts } = useContext(PostContext);' where 'useContext(PostContext)' is repeatedly used in each child components like 'Header', 'Main', 'Archive', 'Footer'. To avoid we can create custom hook for 'useContext(PostContext)'.

Add the following code in PostProvider.js


function usePosts() {
  const context = useContext(PostContext);
  return context;
}


Full code PostProvider.js


import { createContext, useContext, useState } from "react";
import { faker } from "@faker-js/faker";
const PostContext = createContext();
function createRandomPost() {
  return {
    title: `${faker.hacker.adjective()} ${faker.hacker.noun()}`,
    body: faker.hacker.phrase(),
  };
}
function PostProvider({ children }) {
  const [posts, setPosts] = useState(() =>
    Array.from({ length: 30 }, () => createRandomPost())
  );
  const [searchQuery, setSearchQuery] = useState("");

  // Derived state. These are the posts that will actually be displayed
  const searchedPosts =
    searchQuery.length > 0
      ? posts.filter((post) =>
          `${post.title} ${post.body}`
            .toLowerCase()
            .includes(searchQuery.toLowerCase())
        )
      : posts;

  function handleAddPost(post) {
    setPosts((posts) => [post, ...posts]);
  }

  function handleClearPosts() {
    setPosts([]);
  }
  return (
    <PostContext.Provider
      value={{
        posts: searchedPosts,
        onAddPost: handleAddPost,
        onClearPosts: handleClearPosts,
        searchQuery: searchQuery,
        setSearchQuery: setSearchQuery,
      }}
    >
      {children}
    </PostContext.Provider>
  );
}

function usePosts() {
  const context = useContext(PostContext);
  if (context === undefined)
    throw new Error("PostCOntext was used outside of the PostProvider");
  return context;
}

export { PostProvider, usePosts };



Then call 'usePosts() function in child components like below


function Header() {
  const { onClearPosts } = usePosts();
  return (
    <header>
      <h1>
        <span>⚛️</span>The Atomic Blog
      </h1>
      <div>
        <Results />
        <SearchPosts />
        <button onClick={onClearPosts}>Clear posts</button>
      </div>
    </header>
  );
}







Advanced State Management

Types of State - state classification can be done based on state accessibility and state domain.
 
1. State accessibility 

In terms of state accessibility we have 2 types of state local state and global state. 
Local state are needed only by one or few components. Local state are only accessible in component and child component.  
Global state are needed by many components in different position of the component tree. Global state are accessible to every component in the application. 

Hint:- To determine whether to use global or local state, if the component was rendered twice should a state update in one of them reflect in the other one ? 
If the answer is No then use Local state, if answer is yes then use global state.

2. State domain

In terms of state domain we have 2 types of states remote state and UI state.
Remote state used where all application data loaded from a remote server (API). Remote state is usually asynchronous since needs re-fetching and updating.
UI state uses everything else like theme, list filters, form data etc. UI state are synchronous and stored in the application. Ui state doesn't interact with server.



Where to place state

Local state placed in local component, using useState, useReducer or useRef
To place state in multiple related components we use Parent component by lifting the state up, using useState, useReducer or useRef.
For state in multiple related components we place the state in context, tools used Context API + useState or useReducer and the Global state is used (preferably UI state). To update state we use useState or useReducer. Context API not suitable for handling Remote state.
Global state (remote or UI) can be placed in 3rd party library like Redux, React Query, SWR, Zustand. 
URL is a best place to place Global state and tool used in React Router. Global state used when passing between pages using React Router.
Browser for placing states using tools like localstorage, session storage etc and this stores data in user's browser.



Local state (UI state) - useState, useReducer, useRef

Local state (Remote state) - Mostly used in large application. fetch + useEffect + useState/useReducer

Global state (Remote state) - for larger applications - Context API + useState/useReducer
Reducux , Zustard, Recoil
React Query, SWR, RK Query

Global state (UI state) - Context API + useState/useReducer
Reducux , Zustard, Recoil
React Router








In World wise app create a folder in 'src' as 'contexts' and in 'contexts' create a file 'CitiesContext.jsx'




CitiesContext.jsx



/* eslint-disable react/prop-types */
import { createContext, useState, useEffect } from "react";
const BASE_URL = "http://localhost:9000";

const CitiesContext = createContext();

function CitiesProvider({ children }) {
  const [cities, setCities] = useState([]);
  const [isLoading, setIsLoading] = useState(false);

  useEffect(function () {
    async function fetchCities() {
      setIsLoading(true);
      try {
        const res = await fetch(`${BASE_URL}/cities`);
        const data = await res.json();
        setCities(data);
      } catch (err) {
        console.log(err);
      } finally {
        setIsLoading(false);
      }
    }
    fetchCities();
  }, []);
  return (
    <CitiesContext.Provider value={{ cities, isLoading }}>
      {children}
    </CitiesContext.Provider>
  );
}
function useCities() {
  const context = useContext(CitiesContext);
  if (context === undefined)
    throw new Error("CitiesContext used outside CitiesProvider");
  return context;
}
export { CitiesProvider, useCities };




App.jsx

export default function App() {
  return (
    <CitiesProvider>
      <BrowserRouter>
        <Routes>
          <Route index element={<Homepage />} />
          <Route path="product" element={<Product />} />
          <Route path="pricing" element={<Pricing />} />
          <Route path="app" element={<AppLayout />}>
            <Route index element={<Navigate replace to="cities" />} />
            <Route path="cities" element={<CityList />} />
            <Route path="cities/:id" element={<City />} />
            <Route path="countries" element={<CountriesList />} />
            <Route path="form" element={<Form />} />
          </Route>
          <Route path="login" element={<Login />} />
          <Route path="*" element={<PageNotFound />} />
        </Routes>
      </BrowserRouter>
    </CitiesProvider>
  );
}



CityList.jsx

export default function CityList() {
  const { cities, isLoading } = useCities();
  if (isLoading) return <Spinner />;

  if (!cities.length)
    return (
      <Message message="Add your first city by clicking on a city on the map" />
    );
  return (
    <ul className={styles.cityList}>
      {cities.map((city) => {
        return <CityItem key={city.id} city={city} />;
      })}
    </ul>
  );
}



CountriesList.jsx

export default function CountriesList() {
  const { cities, isLoading } = useCities();
  if (isLoading) return <Spinner />;

  if (cities.length === 0)
    return (
      <Message message="Add your first city by clicking on a city on the map" />
    );
  const countries = cities.reduce((arr, city) => {
    if (!arr.map((el) => el.country).includes(city.country))
      return [...arr, { country: city.country, emoji: city.emoji }];
    else return arr;
  }, []);

  return (
    <ul className={styles.countryList}>
      {countries.map((country) => {
        return <CountryItem country={country} key={country.country} />;
      })}
    </ul>
  );
}



Add 'getCity(id)' in 'CitiesContext.jsx'

async function getCity(id) {
    setIsLoading(true);
    try {
      const res = await fetch(`${BASE_URL}/cities/${id}`);
      const data = await res.json();
      setCurrentCity(data);
    } catch (err) {
      console.log(err);
    } finally {
      setIsLoading(false);
    }
  }


CitiesContext.jsx


/* eslint-disable react/prop-types */
import { createContext, useState, useEffect, useContext } from "react";
const BASE_URL = "http://localhost:9000";

const CitiesContext = createContext();

function CitiesProvider({ children }) {
  const [cities, setCities] = useState([]);
  const [isLoading, setIsLoading] = useState(false);
  const [currentCity, setCurrentCity] = useState({});
  useEffect(function () {
    async function fetchCities() {
      setIsLoading(true);
      try {
        const res = await fetch(`${BASE_URL}/cities`);
        const data = await res.json();
        setCities(data);
      } catch (err) {
        console.log(err);
      } finally {
        setIsLoading(false);
      }
    }
    fetchCities();
  }, []);
  async function getCity(id) {
    setIsLoading(true);
    try {
      const res = await fetch(`${BASE_URL}/cities/${id}`);
      const data = await res.json();
      setCurrentCity(data);
    } catch (err) {
      console.log(err);
    } finally {
      setIsLoading(false);
    }
  }
  return (
   <CitiesContext.Provider value={{ cities, isLoading, currentCity, getCity }}>
      {children}
    </CitiesContext.Provider>
  );
}
function useCities() {
  const context = useContext(CitiesContext);
  if (context === undefined)
    throw new Error("CitiesContext used outside CitiesProvider");
  return context;
}
export { CitiesProvider, useCities };




City.jsx


/* eslint-disable react/prop-types */

import { useEffect } from "react";
import { useParams } from "react-router-dom";
import { useCities } from "../contexts/CitiesContext";
import styles from "./City.module.css";
import Spinner from "./Spinner";
import BackButton from "./BackButton";

const formatDate = (date) =>
  new Intl.DateTimeFormat("en", {
    day: "numeric",
    month: "long",
    year: "numeric",
    weekday: "long",
  }).format(new Date(date));

function City() {
  const { id } = useParams();
   const { getCity, currentCity, isLoading } = useCities();

  useEffect(() => {
    getCity(id);
  }, [id]);
  const { cityName, emoji, date, notes } = currentCity;
  if (isLoading) return <Spinner />;
  return (
    <div className={styles.city}>
      <div className={styles.row}>
        <h6>City name</h6>
        <h3>
          <span>{emoji}</span> {cityName}
        </h3>
      </div>

      <div className={styles.row}>
        <h6>You went to {cityName} on</h6>
        <p>{formatDate(date || null)}</p>
      </div>

      {notes && (
        <div className={styles.row}>
          <h6>Your notes</h6>
          <p>{notes}</p>
        </div>
      )}

      <div className={styles.row}>
        <h6>Learn more</h6>
        <a
          href={`https://en.wikipedia.org/wiki/${cityName}`}
          target="_blank"
          rel="noreferrer"
        >
          Check out {cityName} on Wikipedia &rarr;
        </a>
      </div>

      <div>
        <BackButton />
      </div>
    </div>
  );
}

export default City;



Install 'leaflet' for creating map

npm i react-leaflet leaflet

Import leaflet package in 'index.css' like below

@import "https://unpkg.com/leaflet@1.7.1/dist/leaflet.css";
@import "https://fonts.googleapis.com/css2?family=Manrope:wght@400;600;700;800&display=swap";


And place the below code in 'Map.jsx'

 <MapContainer center={position} zoom={13} scrollWheelZoom={false}>
    <TileLayer
      attribution='&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
      url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"
    />
    <Marker position={position}>
      <Popup>
        A pretty CSS3 popup. <br /> Easily customizable.
      </Popup>
    </Marker>
  </MapContainer>



'   const [mapPosition, setMapPosition] = useState([40, 0]);' here 40 is latitude and 0 is longitude









Performance Optimization Tools



3 main areas to optimize performance of React apps they are Prevent wasted Renders, improve app speed/ responsiveness, reduce the bundle size.
To prevent wasted Renders we can memorize components with memo or memorize objects and functions with useMemo and useCallback hooks. Passing elements as children or as regular prop into other elements as children or as normal prop in order to prevent them from being re-rendered.
To improve app speed we use useMemo, useCallback and useTransition hook. To reduce the bundle size by using fewer third party packages in code base. Also by code splitting and lazy loading.

When does a component re-render

In React, a component instance only gets re-rendered in 3 different situations:
When component state changes, whenever there is change in context that the component is subscribed to (whenever component re-renders all its child components will automatically be re-rendered as well), parent component re-rendering (when parent re-render then children who receives the prop will re-render).

Note: A render doesn't mean that DOM actually gets updated but it means the component function gets called. But this can be expensive operation.

Wasted render - a render that didn't produce an change in the DOM.


Test.js

export default function Test() {
  const [count, setCount] = useState(0);
  return (
    <div>
      <h1>Slow counter?!?</h1>
      <button onClick={() => setCount((c) => c + 1)}>Increase: {count}</button>
      <SlowComponent />
    </div>
  );
}


Test.js changed to following

function Counter({ children }) {
  const [count, setCount] = useState(0);
  return (
    <div>
      <h1>Slow counter?!?</h1>
      <button onClick={() => setCount((c) => c + 1)}>Increase: {count}</button>
      {children}
    </div>
  );
}


export default function Test() {
  const [count, setCount] = useState(0);
  return (
    <div>
      <h1>Slow counter?!?</h1>
      <Counter>
        <SlowComponent />
      </Counter>
        </div>
  );
}

App.js

function List() {
  const { posts } = usePosts();
  return (
    <>
      <ul>
        {posts.map((post, i) => (
          <li key={i}>
            <h3>{post.title}</h3>
            <p>{post.body}</p>
          </li>
        ))}
      </ul>
      <Test />
    </>
  );
}

List component not re-rendered hance the component is not slow, since 'SlowComponent' is not re-rendered as it is passed as children prop. We display 'SlowComponent' as children. 'SlowComponent' was rendered before Counter component is re-rendered (  <Counter><SlowComponent /></Counter> ). So when 'Counter' component re-rendered 'SlowComponent' is no longer effected by re-render (since 'SlowComponent' passed as prop already before re-render of 'Counter' component because 'SlowComponent' was created before re-render of 'Counter' component so 'SlowComponent' will not be effected by state update and it already exists)




Memo

Memoization : Optimization technique that executes a pure function once, and saves the result in memory. If we try to execute the function again with the same arguments as before, the previously saved result will be returned without executing the function again.

We can use Memoization to optimize the applications. Memo function to Memoize components we can useMemo, usecallback hooks to memoize objects and functions this will prevent wasted renders and improve overall application speed.

Memo function
Used to create a component that will not re-render when its parent re-renders as long as the passed props stay the same between renders. Memo used to create a memoized component. Memoizing a React component means not to re-render it if props stay the same across renders.
In React usual behavior components re-renders (parent component) then child component also re-renders. But with Memoize if parent component re-renders then child component re-renders only if props passed to child component from parent component change otherwise same props passed but calling the child component will not re-render.
A memoized component will still re-render when its own state changes or when a context thats subscribed to changes because props changes this is because the Ui has new data to be shown since the props from parent component changes so change in child component UI should be reflected.
Memoizing is used for heavy components.


Example in Atomic Blog project



App-memo.js


function App() {
  const [posts, setPosts] = useState(() =>
    Array.from({ length: 30 }, () => createRandomPost())
  );
  const [searchQuery, setSearchQuery] = useState("");
  const [isFakeDark, setIsFakeDark] = useState(false);

  // Derived state. These are the posts that will actually be displayed
  const searchedPosts =
    searchQuery.length > 0
      ? posts.filter((post) =>
          `${post.title} ${post.body}`
            .toLowerCase()
            .includes(searchQuery.toLowerCase())
        )
      : posts;

  function handleAddPost(post) {
    setPosts((posts) => [post, ...posts]);
  }

  function handleClearPosts() {
    setPosts([]);
  }

  // Whenever `isFakeDark` changes, we toggle the `fake-dark-mode` class on the HTML element (see in "Elements" dev tool).
  useEffect(
    function () {
      document.documentElement.classList.toggle("fake-dark-mode");
    },
    [isFakeDark]
  );

  return (
    <section>
      <button
        onClick={() => setIsFakeDark((isFakeDark) => !isFakeDark)}
        className="btn-fake-dark-mode"
      >
        {isFakeDark ? "☀️" : "🌙"}
      </button>

      <Header
        posts={searchedPosts}
        onClearPosts={handleClearPosts}
        searchQuery={searchQuery}
        setSearchQuery={setSearchQuery}
      />
      <Main posts={searchedPosts} onAddPost={handleAddPost} />
      <Archive show={false} />
      <Footer />
    </section>
  );
}




function Archive({ show }) {
 
  const [posts] = useState(() =>
    // 💥 WARNING: This might make your computer slow! Try a smaller `length` first
    Array.from({ length: 30000 }, () => createRandomPost())
  );

  const [showArchive, setShowArchive] = useState(show);

  return (
    <aside>
      <h2>Post archive</h2>
      <button onClick={() => setShowArchive((s) => !s)}>
        {showArchive ? "Hide archive posts" : "Show archive posts"}
      </button>

      {showArchive && (
        <ul>
          {posts.map((post, i) => (
            <li key={i}>
              <p>
                <strong>{post.title}:</strong> {post.body}
              </p>
              {/* <button onClick={() => onAddPost(post)}>Add as new post</button> */}
            </li>
          ))}
        </ul>
      )}
    </aside>
  );
}



In Archive function we set posts to 30000 records as shown above will load the data in UI slowly.


const [posts] = useState(() =>
    // 💥 WARNING: This might make your computer slow! Try a smaller `length` first
    Array.from({ length: 30000 }, () => createRandomPost())
  );



So add memo to function Archive as Archive function is heavy as follows:-



const Archive = memo(function Archive({ show }) {
   const [posts] = useState(() =>
    // 💥 WARNING: This might make your computer slow! Try a smaller `length` first
    Array.from({ length: 30000 }, () => createRandomPost())
  );

  const [showArchive, setShowArchive] = useState(show);

  return (
    <aside>
      <h2>Post archive</h2>
      <button onClick={() => setShowArchive((s) => !s)}>
        {showArchive ? "Hide archive posts" : "Show archive posts"}
      </button>

      {showArchive && (
        <ul>
          {posts.map((post, i) => (
            <li key={i}>
              <p>
                <strong>{post.title}:</strong> {post.body}
              </p>
              {/* <button onClick={() => onAddPost(post)}>Add as new post</button> */}
            </li>
          ))}
        </ul>
      )}
    </aside>
  );
});



memorize doesn't effect state it only deals with props (if props stays same then the Archive function will not re-render).

Instead of passing 'show' as props (like  <Archive show={false} />
 ) we are passing an object
Add the following in App function

 const archiveOptions = {
    show: false,
    title: "Post archive in addition to main posts",
  };

and pass it to Archive as below

  <Archive archiveOptions={archiveOptions} />



App function full


function App() {
  const [posts, setPosts] = useState(() =>
    Array.from({ length: 30 }, () => createRandomPost())
  );
  const [searchQuery, setSearchQuery] = useState("");
  const [isFakeDark, setIsFakeDark] = useState(false);

  // Derived state. These are the posts that will actually be displayed
  const searchedPosts =
    searchQuery.length > 0
      ? posts.filter((post) =>
          `${post.title} ${post.body}`
            .toLowerCase()
            .includes(searchQuery.toLowerCase())
        )
      : posts;

  function handleAddPost(post) {
    setPosts((posts) => [post, ...posts]);
  }

  function handleClearPosts() {
    setPosts([]);
  }

  // Whenever `isFakeDark` changes, we toggle the `fake-dark-mode` class on the HTML element (see in "Elements" dev tool).
  useEffect(
    function () {
      document.documentElement.classList.toggle("fake-dark-mode");
    },
    [isFakeDark]
  );

  const archiveOptions = {
    show: false,
    title: "Post archive in addition to main posts",
  };

  return (
    <section>
      <button
        onClick={() => setIsFakeDark((isFakeDark) => !isFakeDark)}
        className="btn-fake-dark-mode"
      >
        {isFakeDark ? "☀️" : "🌙"}
      </button>

      <Header
        posts={searchedPosts}
        onClearPosts={handleClearPosts}
        searchQuery={searchQuery}
        setSearchQuery={setSearchQuery}
      />
      <Main posts={searchedPosts} onAddPost={handleAddPost} />
      <Archive archiveOptions={archiveOptions} />
      <Footer />
    </section>
  );
}



Archive function changed as follows:-


const Archive = memo(function Archive({ archiveOptions }) {
  
  const [posts] = useState(() =>
    // 💥 WARNING: This might make your computer slow! Try a smaller `length` first
    Array.from({ length: 30000 }, () => createRandomPost())
  );

  const [showArchive, setShowArchive] = useState(archiveOptions.show);

  return (
    <aside>
       <h2>{archiveOptions.title}</h2>
      <button onClick={() => setShowArchive((s) => !s)}>
        {showArchive ? "Hide archive posts" : "Show archive posts"}
      </button>

      {showArchive && (
        <ul>
          {posts.map((post, i) => (
            <li key={i}>
              <p>
                <strong>{post.title}:</strong> {post.body}
              </p>
              {/* <button onClick={() => onAddPost(post)}>Add as new post</button> */}
            </li>
          ))}
        </ul>
      )}
    </aside>
  );
});

In React, everything is re-created on every render (including objects and functions defined inside the component, so a new render gets new functions and new objects even though they are exactly same ones as before) 

In javascript 2 objects or functions that look same are actually different. An empty object is different from another empty object


Eventhough Archive function is passed as object the Archive function is re-rendered even if props hasn't changed this is because if objects or functions passed as props, the child component will always see them as new props on each re-render as props are different between re-renders memo will not work

If objects or functions passed as props, the child component will always see them as new props on each re-render.
When we pass object or function as props to child component then the child component will re-render even though memo is used because these props passed to child component are seen as new props even though they exactly look the same but there is a solution we need to memorize objects and functions to make them stable (preserve) between re-renders by using useMemo and useCallback.

Used to memorize values (useMemo) that we want to preserve between renders and functions (useCallback) between renders.

Values passed into useMemo and useCallback will be basically stored in memory and that cached value will be then returned in future re-renders as long as dependencies ('inputs') stay the same. useMemo and useCallback also have dependency array. When one of the dependencies changes the value no longer be returned from the cache but instead will be recreated.
useMemo and useCallback have a dependency array whenever one dependency changes the value will be re-created.




import { useState, useMemo } from "react";

export default function App() {
  const [count, setCount] = useState(0);
  const [text, setText] = useState("");

  // Expensive calculation
  const expensiveValue = useMemo(() => {
    console.log("Calculating...");
    let total = 0;
    for (let i = 0; i < 500000000; i++) {
      total += i;
    }
    return total;
  }, []); // runs only once

  return (
    <div>
      <h2>Expensive Computed Value: {expensiveValue}</h2>

      <button onClick={() => setCount(count + 1)}>
        Increment Count: {count}
      </button>

      <input
        value={text}
        onChange={(e) => setText(e.target.value)}
        placeholder="Type something"
      />
    </div>
  );
}
Why useMemo?
Without useMemo, the heavy loop runs on every keystroke or button click.

With useMemo, it runs only once unless dependencies change.


useMemo Example — Memoizing Expensive Calculations
❌ Without useMemo → recalculates on every render
✅ With useMemo → recalculates only when dependencies change
✅ Full Example – useMemo
import React, { useState, useMemo } from "react";

function expensiveCalc(num) {
  console.log("Running expensive calculation...");
  let total = 0;
  for (let i = 0; i < 2_000_000_0; i++) {
    total += i;
  }
  return total + num;
}

export default function App() {
  const [count, setCount] = useState(0);
  const [value, setValue] = useState(5);

  const memoResult = useMemo(() => {
    return expensiveCalc(value);
  }, [value]); // 🔥 Only re-run when value changes

  return (
    <div>
      <h2>useMemo Example</h2>
      <h3>Result: {memoResult}</h3>

      <button onClick={() => setValue(value + 1)}>Change Value</button>
      <button onClick={() => setCount(count + 1)}>Increase Count</button>
    </div>
  );
}

🔍 What happens in Console?

When value changes →

Running expensive calculation...


When count changes →

(no expensive calculation) — memoized result reused

📌 useMemo is for memoizing RETURN VALUES.







Parent Component:
import { useState, useCallback } from "react";
import Child from "./Child";

export default function App() {
  const [count, setCount] = useState(0);

  const handleClick = useCallback(() => {
    console.log("Button clicked!");
  }, []); // same function instance unless dependencies change

  return (
    <div>
      <h2>Count: {count}</h2>

      <button onClick={() => setCount(count + 1)}>Increment</button>

      <Child onClick={handleClick} />
    </div>
  );
}




Child Component (memoized):



import React from "react";

function Child({ onClick }) {
  console.log("Child rendered!");
  return <button onClick={onClick}>Child Button</button>;
}

export default React.memo(Child);






useCallback Example — Memoizing Functions (to prevent child re-renders)
❌ Without useCallback → new function created on every render
This causes child components to re-render.
✅ With useCallback → function reference stays same
Child re-renders only when required.
🔥 Scenario

Parent passes a function to child.
We want to avoid re-rendering child when count changes.

✅ Full Example – useCallback + React.memo
Child Component
import React from "react";

const Child = React.memo(({ onClick }) => {
  console.log("Child Rendered");
  return <button onClick={onClick}>Click Child</button>;
});

export default Child;

Parent Component
import React, { useState, useCallback } from "react";
import Child from "./Child";

export default function App() {
  const [count, setCount] = useState(0);
  const [age, setAge] = useState(20);

  const handleChildClick = useCallback(() => {
    console.log("Child clicked");
  }, []); // 🔥 function created ONLY once

  return (
    <div>
      <h2>useCallback Example</h2>

      <Child onClick={handleChildClick} />

      <button onClick={() => setCount(count + 1)}>Increase Count</button>
      <button onClick={() => setAge(age + 1)}>Increase Age</button>
    </div>
  );
}

🔍 What happens in Console?

Page loads →

Child Rendered


Change count →

(NO re-render of Child)


Why?
Because handleChildClick is memoized and does NOT change.

If you change age → same behavior (child does NOT render again).







Redux

Redux is a third party library to manage global state in web application. Redux is a complete standalone library ( easy to integrate with React apps using react-redux library). All global state is stored in one globally accessible store, easy to update using actions. 
In Redux as soon as we update store all React components that consume data from store will be re-rendered. 2 versions of Redux they re classic redux and modern Redux toolkit.
Redux was used for al global state but now there are alternatives. Redux are used only when there is a need for global UI state. (Redux to be used only if  there is lot of global states to be updated frequently). 

In case of useReducer, Event Handler has an action which has type and payload (action contains object that tells how the reducer should update state), we then dispatch to so called reducer function. The reducer takes action type and the payload and together with the current state calculates the next state (new state value). As the state updates the component that originated the state transition will re-render. 

But in Redux,  Event Handler has an action which has type and payload (action contains object that tells how the reducer should update state), we then dispatch to store (store is a centralized container where all global state lives, its the single source of truth of global state in the app). Store is also where one or multiple reducers live. Each reducer is a pure function that calculates the next state ( state transition) based on the action and the current state. Usually one reducer per app feature.
Reducer contains a single task of calculating next state based on action dispatched to the store and the current state that is there in the store. there are multiple reducer in the store because we need to create one reducer per application feature or per data domain to keep things separated. Example in shopping app, could have one reducer for shopping cart, one for user data, one for application color theme. Finally any component that consumes the state that has been updated in the store will always get re-rendered by React. In Redux we use functions called action creators to automate the process of writing actions. Instead of manually creating actions we create functions that do this automatically. This keeps all actions in one single place, since developers need not have to remember action type strings.
Reducer function are not 


npx create-react-app@5 redux-intro



src/store.js


const initialStateAccount = {
  balance: 0,
  loan: 0,
  loanPurpose: "",
};

function accountReducer(state = initialStateAccount, action) {
  switch (action.type) {
    case "account/deposit":
      return { ...state, balance: state.balance + action.payload };
    case "account/withdraw":
      return { ...state, balance: state.balance - action.payload };
    case "account/requestLoan":
      if (state.loan > 0) return state;
      return { ...state, loan: action.payload };
    case "account/payLoan":
      return {
        ...state,
        loan: 0,
        loanPurpose: "",
        balance: state.balance - state.loan,
      };
    default:
      return state;
  }
}


Difference between reducer function in useReducer and Redux is that initialState is passed to reducer function in Redux. action will be an object which consists of type and payload. In reducer function we write the switch case labels as state-domain/event-name.


npm install redux





src/store.js


import { createStore } from "redux";

const initialStateAccount = {
  balance: 0,
  loan: 0,
  loanPurpose: "",
};

function accountReducer(state = initialStateAccount, action) {
  switch (action.type) {
    case "account/deposit":
      return { ...state, balance: state.balance + action.payload };
    case "account/withdraw":
      return { ...state, balance: state.balance - action.payload };
    case "account/requestLoan":
      if (state.loan > 0) return state;
      return {
        ...state,
        loan: action.payload.amount,
        loanPurpose: action.payload.purpose,
        balance: state.balance + action.payload.amount,
      };
    case "account/payLoan":
      return {
        ...state,
        loan: 0,
        loanPurpose: "",
        balance: state.balance - state.loan,
      };
    default:
      return state;
  }
}

const store = createStore(accountReducer);
store.dispatch({ type: "account/deposit", payload: 500 });
store.dispatch({ type: "account/withdraw", payload: 200 });
store.dispatch({
  type: "account/requestLoan",
  payload: {
    amount: 1000,
    purpose: "To buy a car",
  },
});






'dispatch' will dispatch the action.


In index.js import the store.js


index.js

import "./store";




store.getState() returns the current state.


action creators are functions that returns actions.
we are creating 1 action creator for each actions. functions deposit(), withdraw(), requestLoan(), payLoan() are use to return actions.


Adding the following in src/store.js

const initialStateCustomer = {
  fullName: "",
  nationalId: "",
  createdAt: "",
};

const rootReducer = combineReducers({
  account: accountReducer,
  customer: customerReducer,
});
const store = createStore(rootReducer);

function customerReducer(state = initialStateCustomer, action) {
  switch (action.type) {
    case "customer/createCustomer":
      return {
        ...state,
        fullName: action.payload.fullName,
        nationalId: action.payload.nationalId,
        createdAt: action.payload.createdAt,
      };
    case "customer/updateName":
      return {
        ...state,
        fullName: action.payload,
      };
    default:
      return state;
  }
}



function createCustomer(fullName, nationalId) {
  return {
    type: "customer/createCustomer",
    payload: { fullName, nationalId, createdAt: new Date().toISOString() },
  };
}


To combine different reducers we have 'combineReducer' 




src/store


import { combineReducers, createStore } from "redux";

const initialStateAccount = {
  balance: 0,
  loan: 0,
  loanPurpose: "",
};

const initialStateCustomer = {
  fullName: "",
  nationalId: "",
  createdAt: "",
};

function accountReducer(state = initialStateAccount, action) {
  switch (action.type) {
    case "account/deposit":
      return { ...state, balance: state.balance + action.payload };
    case "account/withdraw":
      return { ...state, balance: state.balance - action.payload };
    case "account/requestLoan":
      if (state.loan > 0) return state;
      return {
        ...state,
        loan: action.payload.amount,
        loanPurpose: action.payload.purpose,
        balance: state.balance + action.payload.amount,
      };
    case "account/payLoan":
      return {
        ...state,
        loan: 0,
        loanPurpose: "",
        balance: state.balance - state.loan,
      };
    default:
      return state;
  }
}

function customerReducer(state = initialStateCustomer, action) {
  switch (action.type) {
    case "customer/createCustomer":
      return {
        ...state,
        fullName: action.payload.fullName,
        nationalId: action.payload.nationalId,
        createdAt: action.payload.createdAt,
      };
    case "customer/updateName":
      return {
        ...state,
        fullName: action.payload,
      };
    default:
      return state;
  }
}

const rootReducer = combineReducers({
  account: accountReducer,
  customer: customerReducer,
});
const store = createStore(rootReducer);


function deposit(amount) {
  return { type: "account/deposit", payload: amount };
}
function withdraw(amount) {
  return { type: "account/withdraw", payload: amount };
}
function requestLoan(amount, purpose) {
  return {
    type: "account/requestLoan",
    payload: {
      amount: amount,
      purpose: purpose,
    },
  };
}
function payLoan() {
  return { type: "account/payLoan" };
}
store.dispatch(deposit(500));
store.dispatch(withdraw(200));
store.dispatch(requestLoan(1000, "Buy a cheap car"));
store.dispatch(payLoan());
console.log(store.getState());

function createCustomer(fullName, nationalId) {
  return {
    type: "customer/createCustomer",
    payload: { fullName, nationalId, createdAt: new Date().toISOString() },
  };
}

function updatedName(fullName) {
  return { type: "customer/updateName", payload: fullName };
}

store.dispatch(createCustomer("Bini Babu", 123456));
store.dispatch(updatedName("Anna Babu"));
console.log(store.getState());


Slice is a part of total state, entire state lives in the store.(features/accounts/accountSlice.js, features/accounts/customerSlice.js)


features/accounts/accountSlice.js



const initialStateAccount = {
  balance: 0,
  loan: 0,
  loanPurpose: "",
};
export default function accountReducer(state = initialStateAccount, action) {
  switch (action.type) {
    case "account/deposit":
      return { ...state, balance: state.balance + action.payload };
    case "account/withdraw":
      return { ...state, balance: state.balance - action.payload };
    case "account/requestLoan":
      if (state.loan > 0) return state;
      return {
        ...state,
        loan: action.payload.amount,
        loanPurpose: action.payload.purpose,
        balance: state.balance + action.payload.amount,
      };
    case "account/payLoan":
      return {
        ...state,
        loan: 0,
        loanPurpose: "",
        balance: state.balance - state.loan,
      };
    default:
      return state;
  }
}

export function deposit(amount) {
  return { type: "account/deposit", payload: amount };
}
export function withdraw(amount) {
  return { type: "account/withdraw", payload: amount };
}
export function requestLoan(amount, purpose) {
  return {
    type: "account/requestLoan",
    payload: {
      amount: amount,
      purpose: purpose,
    },
  };
}
export function payLoan() {
  return { type: "account/payLoan" };
}




features/accounts/customerSlice.js



const initialStateCustomer = {
  fullName: "",
  nationalId: "",
  createdAt: "",
};

export default function customerReducer(state = initialStateCustomer, action) {
  switch (action.type) {
    case "customer/createCustomer":
      return {
        ...state,
        fullName: action.payload.fullName,
        nationalId: action.payload.nationalId,
        createdAt: action.payload.createdAt,
      };
    case "customer/updateName":
      return {
        ...state,
        fullName: action.payload,
      };
    default:
      return state;
  }
}

export function createCustomer(fullName, nationalId) {
  return {
    type: "customer/createCustomer",
    payload: { fullName, nationalId, createdAt: new Date().toISOString() },
  };
}

export function updatedName(fullName) {
  return { type: "customer/updateName", payload: fullName };
}



src/store.js

import { combineReducers, createStore } from "redux";
import accountReducer from "./features/accounts/accountSlice";
import customerReducer from "./features/customers/customerSlice";
const rootReducer = combineReducers({
  account: accountReducer,
  customer: customerReducer,
});
const store = createStore(rootReducer);

export default store;



By installing the below command 'react-redux' will help React and Redux to communicate with each other.

import the following in index.js

import { Provider } from "react-redux";

and place the App component enclosing in Provider tag like below

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(
  <React.StrictMode>
    <Provider>
      <App />
    </Provider>
  </React.StrictMode>
);




index.js

import React from "react";
import ReactDOM from "react-dom/client";
import "./index.css";
import App from "./App";
import { Provider } from "react-redux";
import store from "./store";

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(
  <React.StrictMode>
    <Provider store={store}>
      <App />
    </Provider>
  </React.StrictMode>
);



npm install react-redux


feature/customer/Customer.js


import { useSelector } from "react-redux";

function Customer() {
  const customer = useSelector((store) => store.customer.fullName);

  return <h2>👋 Welcome, {customer}</h2>;
}

export default Customer;


useSelector take in an argument a callback (this function take single argument in the entire Redux store). useSelector creates a subscription to the store. Whenever the store changes then this component thats subscribed to the store will re-render. we are reading the value from store and as soon as the value updated in the store then 'CreateCustomer' component is re-rendered.



feature/customer/CreateCustomer.js


import { useState } from "react";
import { useDispatch } from "react-redux";
import { createCustomer } from "./customerSlice";

function Customer() {
  const [fullName, setFullName] = useState("");
  const [nationalId, setNationalId] = useState("");
  const dispatch = useDispatch();

  function handleClick() {
    if (!fullName || !nationalId) return;
    dispatch(createCustomer(fullName, nationalId));
  }

  return (
    <div>
      <h2>Create new customer</h2>
      <div className="inputs">
        <div>
          <label>Customer full name</label>
          <input
            value={fullName}
            onChange={(e) => setFullName(e.target.value)}
          />
        </div>
        <div>
          <label>National ID</label>
          <input
            value={nationalId}
            onChange={(e) => setNationalId(e.target.value)}
          />
        </div>
        <button onClick={handleClick}>Create new customer</button>
      </div>
    </div>
  );
}

export default Customer;





In the handleClick function where we want to dispatch now an action that will create a new customer. 'useDispatch' hook will dispatch hook in React.

import { useDispatch } from "react-redux";
import { createCustomer } from "./customerSlice";

const dispatch = useDispatch();

  function handleClick() {
    dispatch(createCustomer(fullName, nationalId));
  }



App.js

import CreateCustomer from "./features/customers/CreateCustomer";
import Customer from "./features/customers/Customer";
import AccountOperations from "./features/accounts/AccountOperations";
import BalanceDisplay from "./features/accounts/BalanceDisplay";
import { useSelector } from "react-redux";

function App() {
  const fullName = useSelector((state) => state.customer.fullName);
  return (
    <div>
      <h1>🏦 The React-Redux Bank ⚛️</h1>
      {fullName === "" ? (
        <CreateCustomer />
      ) : (
        <>
          <Customer />
          <AccountOperations />
          <BalanceDisplay />
        </>
      )}
    </div>
  );
}

export default App;



through 'useSelector' subscription we fetch the updated fullname value from store.




feature/accounts/AccountOperations.js



import { useState } from "react";
import { useDispatch, useSelector } from "react-redux";
import { deposit, payLoan, requestLoan, withdraw } from "./accountSlice";

function AccountOperations() {
  const [depositAmount, setDepositAmount] = useState("");
  const [withdrawalAmount, setWithdrawalAmount] = useState("");
  const [loanAmount, setLoanAmount] = useState("");
  const [loanPurpose, setLoanPurpose] = useState("");
  const [currency, setCurrency] = useState("USD");

  const dispatch = useDispatch();
  const {
    loan: currentLoan,
    loanPurpose: currentLoanPurpose,
    balance,
    isLoading,
  } = useSelector((store) => store.account);

  console.log(balance);

  function handleDeposit() {
    if (!depositAmount) return;

    dispatch(deposit(depositAmount, currency));
    setDepositAmount("");
    setCurrency("USD");
  }

  function handleWithdrawal() {
    if (!withdrawalAmount) return;
    dispatch(withdraw(withdrawalAmount));
    setWithdrawalAmount("");
  }

  function handleRequestLoan() {
    if (!loanAmount || !loanPurpose) return;
    dispatch(requestLoan(loanAmount, loanPurpose));
    setLoanAmount("");
    setLoanPurpose("");
  }

  function handlePayLoan() {
    dispatch(payLoan());
  }

  return (
    <div>
      <h2>Your account operations</h2>
      <div className="inputs">
        <div>
          <label>Deposit</label>
          <input
            type="number"
            value={depositAmount}
            onChange={(e) => setDepositAmount(+e.target.value)}
          />
          <select
            value={currency}
            onChange={(e) => setCurrency(e.target.value)}
          >
            <option value="USD">US Dollar</option>
            <option value="EUR">Euro</option>
            <option value="GBP">British Pound</option>
          </select>

          <button onClick={handleDeposit} disabled={isLoading}>
            {isLoading ? "Converting..." : `Deposit ${depositAmount}`}
          </button>
        </div>

        <div>
          <label>Withdraw</label>
          <input
            type="number"
            value={withdrawalAmount}
            onChange={(e) => setWithdrawalAmount(+e.target.value)}
          />
          <button onClick={handleWithdrawal}>
            Withdraw {withdrawalAmount}
          </button>
        </div>

        <div>
          <label>Request loan</label>
          <input
            type="number"
            value={loanAmount}
            onChange={(e) => setLoanAmount(+e.target.value)}
            placeholder="Loan amount"
          />
          <input
            value={loanPurpose}
            onChange={(e) => setLoanPurpose(e.target.value)}
            placeholder="Loan purpose"
          />
          <button onClick={handleRequestLoan}>Request loan</button>
        </div>

        {currentLoan > 0 && (
          <div>
            <span>
              Pay back ${currentLoan} ({currentLoanPurpose})
            </span>
            <button onClick={handlePayLoan}>Pay loan</button>
          </div>
        )}
      </div>
    </div>
  );
}

export default AccountOperations;






we call dispatch function to dispatch the actions

  const dispatch = useDispatch();

 const {
    loan: currentLoan,
    loanPurpose: currentLoanPurpose,
    balance,
    isLoading,
  } = useSelector((store) => store.account);


function handleDeposit() {
    if (!depositAmount) return;

    dispatch(deposit(depositAmount, currency));
    setDepositAmount("");
    setCurrency("USD");
  }

  function handleWithdrawal() {
    if (!withdrawalAmount) return;
    dispatch(withdraw(withdrawalAmount));
    setWithdrawalAmount("");
  }








Asynchronous API call cannot be made in reducer functions because reducer functions need to be pure functions with no side effects. Asynchronous API call need to be done outside the reducer. Fetch the data inside the middleware (function that sits between the dispatching and store). Middleware allows developers to run some code after dispatching an action but before the action reaches the reducer in the store. Using Middleware we can perform some action before action gets into the reducer. Middleware used to write asynchronous API calls, set timers, console the logs, pausing and cancelling the actions. redux Thunk is the middleware used to fetch data from asynchronous API call.
Action reaches the Middleware Thunk to fetch data by using asynchronous operation. As long as data reaches Middleware then we place it into actions payload and then we dispatch the action into the store where the state immediately gets updated. Thunk assist Redux to wait before dispatching the fetch data into the store.


Making an API Call With Redux Thunks


Basically, whenever the user deposits some money, they can select which currency that money is in, for example, euro. If that currency is different from US dollars, then we need to convert these 500 euros back to US dollars before they actually get deposited into the account, and before that deposit action is dispatched to the store.

We will have that middleware sitting between dispatching the action, as we click on the button, and that action actually reaching the store.

To use this middleware, we need to follow three steps:

First, install the middleware package.
Then, apply that middleware to our store.
Finally, use the middleware in our action creator functions.


npm install redux-thunk


import { thunk } from "redux-thunk";

const store = createStore(rootReducer, applyMiddleware(thunk));

'applyMiddleware' we pass thunk, told store we want to use middleware in the application


src/store.js

import { applyMiddleware, combineReducers, createStore } from "redux";
import accountReducer from "./features/accounts/accountSlice";
import customerReducer from "./features/customers/customerSlice";
import { thunk } from "redux-thunk";
const rootReducer = combineReducers({
  account: accountReducer,
  customer: customerReducer,
});
const store = createStore(rootReducer, applyMiddleware(thunk));

export default store;


features/accounts/accountSlice.js


const initialStateAccount = {
  balance: 0,
  loan: 0,
  loanPurpose: "",
  isLoading: false,
};

export function deposit(amount, currency) {
   if (currency === "USD") return { type: "account/deposit", payload: amount };

 return async function (dispatch, getState) {
dispatch({ type: "account/convertingCurrency" });
    const res = await fetch(
      `https://api.frankfurter.app/latest?amount=${amount}&from=${currency}&to=USD`
    );
    const data = await res.json();
     const converted = data.rates.USD;
       dispatch({ type: "account/deposit", payload: converted });
  };

}

When we dispatch this action creator, if the currency is not USD, the returned value is a function (the thunk). Redux will recognize this and execute the function instead of immediately dispatching an action to the store. The function returned if its not 'USD' will allow Redux to know that the function is the thunk and it will execute the function and not immediately dispatch the action to the store. Since we return a function Redux knows that this is asynchronous action that we want to execute before dispatching anything to the store. To dispatch later this function here that Redux will call internally will get access to dispatch function and the internal state (getState() ). Asynchronous API shown above to convert to different currency to USD dollars and the Middleware function perform asynchronous API calls and the result is returns as action to store (dispatch the result of asynchronous api in the middleware function). middleware sits between dispatch and store.



features/accounts/AccountOperation.js

function handleDeposit() {
    if (!depositAmount) return;

    dispatch(deposit(depositAmount, currency));
    setDepositAmount("");
    setCurrency("USD");
  }
 






Redux Devtools


Install Redux DevTools from google extension

then install npm package

npm i redux-devtools-extension



src/store.js

import { applyMiddleware, combineReducers, createStore } from "redux";
import accountReducer from "./features/accounts/accountSlice";
import customerReducer from "./features/customers/customerSlice";
import { composeWithDevTools } from "redux-devtools-extension";
import { thunk } from "redux-thunk";
const rootReducer = combineReducers({
  account: accountReducer,
  customer: customerReducer,
});
const store = createStore(
  rootReducer,
  composeWithDevTools(applyMiddleware(thunk))
);

export default store;



In store.js we add this imports 'import { composeWithDevTools } from "redux-devtools-extension";' then wrap around the middleware


const store = createStore(
  rootReducer,
  composeWithDevTools(applyMiddleware(thunk))
);



feature/accounts/accountSlice.js


import { createSlice } from "@reduxjs/toolkit";

const initialStateAccount = {
  balance: 0,
  loan: 0,
  loanPurpose: "",
  isLoading: false,
};
export default function accountReducer(state = initialStateAccount, action) {
  switch (action.type) {
    case "account/deposit":
      return {
        ...state,
        balance: state.balance + action.payload,
        isLoading: false,
      };
    case "account/withdraw":
      return { ...state, balance: state.balance - action.payload };
    case "account/requestLoan":
      if (state.loan > 0) return state;
      return {
        ...state,
        loan: action.payload.amount,
        loanPurpose: action.payload.purpose,
        balance: state.balance + action.payload.amount,
      };
    case "account/payLoan":
      return {
        ...state,
        loan: 0,
        loanPurpose: "",
        balance: state.balance - state.loan,
      };
    case "account/convertingCurrency":
      return { ...state, isLoading: true };
    default:
      return state;
  }
}

export function deposit(amount, currency) {
  if (currency === "USD") return { type: "account/deposit", payload: amount };

  return async function (dispatch, getState) {
    dispatch({ type: "account/convertingCurrency" });
    const res = await fetch(
      `https://api.frankfurter.app/latest?amount=${amount}&from=${currency}&to=USD`
    );
    const data = await res.json();
    const converted = data.rates.USD;
    dispatch({ type: "account/deposit", payload: converted });
  };
}
export function withdraw(amount) {
  return { type: "account/withdraw", payload: amount };
}
export function requestLoan(amount, purpose) {
  return {
    type: "account/requestLoan",
    payload: {
      amount: amount,
      purpose: purpose,
    },
  };
}
export function payLoan() {
  return { type: "account/payLoan" };
}



feature/customer/scustomerSlice.js



const initialStateCustomer = {
  fullName: "",
  nationalId: "",
  createdAt: "",
};

export default function customerReducer(state = initialStateCustomer, action) {
  switch (action.type) {
    case "customer/createCustomer":
      return {
        ...state,
        fullName: action.payload.fullName,
        nationalId: action.payload.nationalId,
        createdAt: action.payload.createdAt,
      };
    case "customer/updateName":
      return {
        ...state,
        fullName: action.payload,
      };
    default:
      return state;
  }
}

export function createCustomer(fullName, nationalId) {
  return {
    type: "customer/createCustomer",
    payload: { fullName, nationalId, createdAt: new Date().toISOString() },
  };
}

export function updatedName(fullName) {
  return { type: "customer/updateName", payload: fullName };
}




What is Redux Toolkit (RTK)?

Redux Toolkit is the modern way of writing Redux code.

npm i @reduxjs/toolkit


In src/store.js make the following changes 

import { configureStore } from "@reduxjs/toolkit";


createStore is deprecated. Now, we will use the configureStore method instead

The configureStore function basically wraps around createStore and adds several functionalities automatically

The result of this call will be our store.

configureStore will do the following:-

It combines our reducers automatically.
It adds the Thunk middleware.
It sets up the developer tools automatically.

In the end, the store is created and returned.

import configureStore and call it with an options object.

In the options object, we specify the root reducer using the reducer property. This is an object where we tell Redux Toolkit about our reducers. Example following:-

const store = configureStore({
  reducer: {
    account: accountReducer,
    cusomer: customerReducer,
  },
});

For example, we can specify two reducers:

account: the account reducer
customer: the customer reducer



src/store-redux-toolkit

import accountReducer from "./features/accounts/accountSlice";
import customerReducer from "./features/customers/customerSlice";
import { configureStore } from "@reduxjs/toolkit";
import { thunk } from "redux-thunk";

const store = configureStore({
  reducer: {
    account: accountReducer,
    cusomer: customerReducer,
  },
});
export default store;






Create account slice to redux toolkit


createSlice which we can import 'import { createSlice } from "@reduxjs/toolkit";'

createSlice automatically create action creators from our reducers, it makes writing reducers easier, mutate state inside reducers.

Immer library will convert the logic back to immutable logic.



feature/accounts/accountSlice.js


import { createSlice } from "@reduxjs/toolkit";

const initialState = {
  balance: 0,
  loan: 0,
  loanPurpose: "",
  isLoading: false,
};

const accountSlice = createSlice({
  name: "account",
  initialState,
  reducers: {
    deposit(state, action) {
      state.balance += action.payload;
    },
    withdraw(state, action) {
      state.balance -= action.payload;
    },
    requestLoan(state, action) {
      if (state.loan > 0) return;

      state.loan = action.payload.amount;
      state.loanPurpose = action.payload.purpose;
      state.balance += action.payload.amount;
    },
    payLoan(state, action) {
      state.loan = 0;
      state.loanPurpose = "";
      state.balance -= state.loan;
    },
  },
});

export const { deposit, withdraw, requestLoan, payLoan } = accountSlice.actions;

export default accountSlice.reducer;



createSlice used to have an object as an argument where the 'name' of the slice which is 'account' here, then the 'initialState', then third argument is multiple reducers which include deposit, withdraw etc. In 'deposit' we mutate the 'state.balance'.


Handling Multiple Arguments in Action Creators
By default, action creators generated by createSlice accept only one argument, which becomes the payload. If more than one argument is needed, use the prepare method. The prepare method allows you to accept multiple arguments and return an object that becomes the payload.


 requestLoan: {
      prepare(amount, purpose) {
        return {
          payload: {
            amount,
            purpose,
          },
        };
      },
      reducer(state, action) {
        if (state.loan > 0) return;

        state.loan = action.payload.amount;
        state.loanPurpose = action.payload.purpose;
        state.balance += action.payload.amount;
      },
    },







feature/accounts/accountSlice.js



import { createSlice } from "@reduxjs/toolkit";

const initialState = {
  balance: 0,
  loan: 0,
  loanPurpose: "",
  isLoading: false,
};

const accountSlice = createSlice({
  name: "account",
  initialState,
  reducers: {
    deposit(state, action) {
      state.balance += action.payload;
    },
    withdraw(state, action) {
      state.balance -= action.payload;
    },
    requestLoan: {
      prepare(amount, purpose) {
        return {
          payload: {
            amount,
            purpose,
          },
        };
      },
      reducer(state, action) {
        if (state.loan > 0) return;

        state.loan = action.payload.amount;
        state.loanPurpose = action.payload.purpose;
        state.balance += action.payload.amount;
      },
    },
    payLoan(state, action) {
     state.balance -= state.loan;
      state.loan = 0;
      state.loanPurpose = "";    },
  },
});

export const { deposit, withdraw, requestLoan, payLoan } = accountSlice.actions;

export default accountSlice.reducer;

















the three main ways for child-to-parent communication in React, explained simply with clear examples.

✅ 1. Using Callback Function (Most Common & Recommended)

Parent sends a function as a prop → Child calls it and sends data back.

Parent → Child
function Parent() {
  const handleMessage = (msg) => {
    console.log("Received from child:", msg);
  };

  return <Child sendMessage={handleMessage} />;
}

Child → Parent
function Child({ sendMessage }) {
  return (
    <button onClick={() => sendMessage("Hello Parent!")}>
      Send Message
    </button>
  );
}
✔️ Result:

When child clicks the button → Parent receives "Hello Parent!"

✅ 2. Using lifting state up

Parent holds the actual state; child only updates it.

Parent
function Parent() {
  const [value, setValue] = useState("");

  return (
    <div>
      <Child value={value} setValue={setValue} />
      <p>Parent Value: {value}</p>
    </div>
  );
}

Child
function Child({ value, setValue }) {
  return (
    <input
      value={value}
      onChange={(e) => setValue(e.target.value)}
    />
  );
}


✔️ Child updates parent state directly → Parent reacts instantly.

✅ 3. Using Context API (For deep nested child → parent)

Useful when child is many levels down (grandchild, great-grandchild).

Create Context
const AppContext = createContext();

Parent provides setter
function Parent() {
  const [message, setMessage] = useState("");

  return (
    <AppContext.Provider value={{ message, setMessage }}>
      <Child />
    </AppContext.Provider>
  );
}

Child uses context to update parent
function Child() {
  const { setMessage } = useContext(AppContext);

  return (
    <button onClick={() => setMessage("Updated from Child!")}>
      Update Parent
    </button>
  );
}


✔️ No need to pass props → clean and scalable.







Lazy Loading 



Lazy Loading in React is a performance optimization technique that allows components to load only when they are needed, rather than at the initial page load.
This reduces the bundle size and improves application load time.

React provides React.lazy() and Suspense for lazy loading components.

🚀 How Lazy Loading Works

Instead of importing a component normally:

import MyComponent from "./MyComponent";


You load it lazily:

const MyComponent = React.lazy(() => import("./MyComponent"));

📘 Basic Example of Lazy Loading in React
App.js
import React, { Suspense } from "react";

const About = React.lazy(() => import("./About")); // Lazy loaded component

function App() {
  return (
    <div>
      <h1>Lazy Loading Example</h1>

      <Suspense fallback={<h2>Loading...</h2>}>
        <About />   {/* Render only when needed */}
      </Suspense>
    </div>
  );
}

export default App;

About.js
export default function About() {
  return <h2>This is the About component.</h2>;
}

What happens?

Until About component is fully loaded, React shows "Loading..."

Once loaded, component is rendered.

🧭 Lazy Loading with React Router
import { BrowserRouter, Routes, Route } from "react-router-dom";
import React, { Suspense } from "react";

const Home = React.lazy(() => import("./Home"));
const Contact = React.lazy(() => import("./Contact"));

function App() {
  return (
    <BrowserRouter>
      <Suspense fallback={<div>Loading route...</div>}>
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/contact" element={<Contact />} />
        </Routes>
      </Suspense>
    </BrowserRouter>
  );
}

export default App;

⭐ Benefits of Lazy Loading
Benefit	Description
Faster initial load	Small bundle size reduces first render time
Better performance	Load components only when required
Efficient resource usage	Avoids unnecessary code execution






Authentication vs Authorization




Concept	Meaning	Example
Authentication	Verifies who the user is	Login using email/password, Google login
Authorization	Determines what the user can access	Admin access vs Normal user access
Relationship	Always happens before authorization	Must authenticate before checking role


How Authentication Works in React
Typical Flow

User enters email/password in login form.

React sends credentials to backend API (Node, Spring, Django, etc.).

Backend verifies and returns JWT token + user details.

React stores token in localStorage / cookie / sessionStorage.

Protected pages check token before rendering.

Example Code: Login & Save Token
const handleLogin = async () => {
  const res = await fetch("/api/login", {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ email, password }),
  });

  const data = await res.json();
  localStorage.setItem("token", data.token);   // save token
};

Protected Route (Authentication Guard)
import { Navigate } from "react-router-dom";

export default function PrivateRoute({ children }) {
  const token = localStorage.getItem("token");

  return token ? children : <Navigate to="/login" replace />;
}

Usage
<Route path="/dashboard" element={
  <PrivateRoute>
    <Dashboard />
  </PrivateRoute>
} />




Here is a complete sample React Authentication + Authorization setup using Context API + JWT including:

Login Page

Auth Context

Protected Route

Role-based Authorization

You can copy & run this structure.

🏗 Project Structure
src/
  ├── App.js
  ├── index.js
  ├── api.js
  ├── context/AuthContext.js
  ├── components/PrivateRoute.js
  ├── pages/Login.js
  ├── pages/Dashboard.js
  ├── pages/Admin.js

🧠 AuthContext.js
import { createContext, useContext, useState } from "react";

const AuthContext = createContext();

export const AuthProvider = ({ children }) => {
  const [user, setUser] = useState(JSON.parse(localStorage.getItem("user")) || null);

  const login = async (email, password) => {
    const res = await fetch("/api/login", {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify({ email, password }),
    });

    const data = await res.json();
    localStorage.setItem("token", data.token);
    localStorage.setItem("user", JSON.stringify(data.user));
    setUser(data.user);
  };

  const logout = () => {
    localStorage.removeItem("token");
    localStorage.removeItem("user");
    setUser(null);
  };

  return (
    <AuthContext.Provider value={{ user, login, logout }}>
      {children}
    </AuthContext.Provider>
  );
};

export const useAuth = () => useContext(AuthContext);

🛡 PrivateRoute.js (Authentication Guard)
import { Navigate } from "react-router-dom";

export default function PrivateRoute({ children }) {
  const token = localStorage.getItem("token");
  return token ? children : <Navigate to="/login" replace />;
}

🔑 AdminRoute.js (Authorization Guard)
import { Navigate } from "react-router-dom";
import { useAuth } from "../context/AuthContext";

export default function AdminRoute({ children }) {
  const { user } = useAuth();
  return user?.role === "admin" ? children : <Navigate to="/unauthorized" replace />;
}

🧾 Login.js
import { useState } from "react";
import { useAuth } from "../context/AuthContext";

export default function Login() {
  const { login } = useAuth();
  const [email, setEmail] = useState("");
  const [password, setPassword] = useState("");

  const handleSubmit = async (e) => {
    e.preventDefault();
    await login(email, password);
  };

  return (
    <form onSubmit={handleSubmit}>
      <h2>Login</h2>
      <input type="email" placeholder="Email" onChange={(e) => setEmail(e.target.value)} />
      <input type="password" placeholder="Password" onChange={(e) => setPassword(e.target.value)} />
      <button type="submit">Login</button>
    </form>
  );
}

📄 App.js
import { BrowserRouter, Routes, Route } from "react-router-dom";
import { AuthProvider } from "./context/AuthContext";
import PrivateRoute from "./components/PrivateRoute";
import AdminRoute from "./components/AdminRoute";
import Login from "./pages/Login";
import Dashboard from "./pages/Dashboard";
import Admin from "./pages/Admin";

function App() {
  return (
    <BrowserRouter>
      <AuthProvider>
        <Routes>
          <Route path="/login" element={<Login />} />

          <Route path="/dashboard" element={
            <PrivateRoute>
              <Dashboard />
            </PrivateRoute>
          } />

          <Route path="/admin" element={
            <AdminRoute>
              <Admin />
            </AdminRoute>
          } />

        </Routes>
      </AuthProvider>
    </BrowserRouter>
  );
}

export default App;

🖥 Dashboard.js
import { useAuth } from "../context/AuthContext";

export default function Dashboard() {
  const { user, logout } = useAuth();
  return (
    <div>
      <h2>Welcome {user?.name}</h2>
      <button onClick={logout}>Logout</button>
    </div>
  );
}

👑 Admin.js
export default function Admin() {
  return <h1>Admin Panel - Protected by Role</h1>;
}

🚀 Example API Response (Backend)

(Express Node.js Example)

res.json({
  user: {
    name: "Bini",
    email: "abc@gmail.com",
    role: "admin"
  },
  token: "12345abcdjwt"
});










What is Reconciliation in React?

Reconciliation is the process React uses to update the DOM efficiently.

When your component’s state or props change, React needs to figure out:

“What actually changed in the UI, and how do I update the browser DOM with minimum operations?”

React does not re-render the whole DOM.
Instead, it uses a Virtual DOM and a Diffing Algorithm to detect differences and update only what changed.

So, reconciliation =
📌 Comparing previous Virtual DOM with the new Virtual DOM
📌 Finding the minimal set of DOM operations needed
📌 Updating the real DOM efficiently

✅ How the Diffing Algorithm works in React

React follows a set of highly optimized rules to determine what changed. This is known as the React Fiber Diffing Algorithm (previously known as the Virtual DOM diffing algorithm).

1. Element Type Comparison
Rule 1: If element types are different → React destroys and recreates

Example:

<div/> → <span/>


React will:

Remove old <div>

Create new <span>

Re-render entire subtree inside it

This is a full replace.



2. Props Comparison

If the element type is same, React compares:

Props

Attributes

Event handlers

Example:

<button class="red" />  →  <button class="blue" />


React only updates the class attribute — minimal DOM change.




3. Diffing Children (Very Important)

React performs a comparison of children lists using two main principles:

A. Diffing Without Keys (Slow & Inefficient)

Example:

<ul>
  <li>A</li>
  <li>B</li>
</ul>


updated to:

<ul>
  <li>B</li>
  <li>A</li>
</ul>


Without keys:

React compares A ↔ B (mismatch → replace)

Compares B ↔ A (mismatch → replace)

Two unnecessary manipulations

React assumes items are reordered only if keys are provided




B. Diffing With Keys (Optimized)

Keys help React identify which items moved or changed.

Example:

<li key="A">A</li>
<li key="B">B</li>


Now React knows:

A still exists → just move it

B still exists → just move it

No need to recreate elements.
This gives O(n) efficiency instead of O(n²).




4. Component Comparison
If the component type is same:

React just updates the props and triggers re-render.

<MyComponent a={1}/> → <MyComponent a={2}/>

If component type is different:

React unmounts old one and mounts new one.

<MyComponent/> → <YourComponent/>



Reconciliation

Process React uses to update UI efficiently by comparing Virtual DOM trees and applying minimal DOM changes.

Diffing Algorithm

Rules React uses to detect differences between two Virtual DOMs:

Different element types → replace entire element

Same element type → compare props

Children diffing uses keys to optimize list updates

Same component type → update props, different → remount


Reconciliation in React is the process of updating the DOM by comparing the previous Virtual DOM with the new Virtual DOM. React uses its Diffing Algorithm to identify what changed and updates only that part of the real DOM.
It checks element types, props, and especially children lists. For lists, React uses keys to match elements efficiently, reducing time complexity from O(n²) to O(n).















Why do we use keys in React?

Keys help React identify which items in a list have changed, been added, or removed.

They act as unique identifiers so React can match the previous Virtual DOM elements with the new ones during the reconciliation / diffing process.

How keys help React internally
1. Keys maintain component identity

Every component instance in React has its own state and lifecycle.

Example list of <Input> components:

{items.map(item => <Input key={item.id} />)}


If keys change incorrectly or are missing, React cannot determine which Input corresponds to which one, causing:

State mixing

Inputs losing their content

Incorrect component re-use

Keys ensure:

"This component should stay exactly the same across re-renders."



2. Keys prevent unnecessary re-renders

With proper keys, React re-renders only the items that actually changed.

Without proper keys:

React re-renders all items

React may unmount and remount components unnecessarily

Performance drops

Keys allow O(n) list diffing instead of O(n²).



3. Keys correctly handle list re-ordering

Example:

A B C


Updated to:

C B A


With correct keys:

React just moves DOM nodes (fast)

With index-based or missing keys:

React thinks A → C, B → B, C → A (incorrect mapping)

React replaces elements unnecessarily

DOM nodes are recreated

Local state inside list items gets lost




What happens if we don’t give proper keys?

1. React uses index as default key → BAD for reorder

List reorder example:

Items move visually

But internal state stays attached to the old positions, not the items
This causes:

Wrong item showing selected state

Wrong item staying expanded/collapsed

Inputs swapping values

2. Component identity breaks

React cannot match old vs new elements correctly, leading to:

Lost input values

Lost focus

Lost checkbox states

useEffect re-runs unnecessarily

Local state moved to wrong list item

3. More unmounting & remounting

Without correct keys:

React destroys and recreates components

Worse performance

Side effects re-run unnecessarily

4. Incorrect UI updates

Because React re-maps list items incorrectly, you see:

Flickering UI

Animation glitches

React warnings





We use keys in React to help identify elements across renders. Keys allow React to understand which components have been changed, added, or removed without recreating the entire list. This preserves component identity, prevents unwanted re-renders, and makes list diffing an O(n) operation.

If we don’t provide proper keys, React falls back to index-based diffing, which breaks when the list changes order. This can cause components to lose state, inputs to swap values, and unnecessary unmount/mount cycles. Essentially, incorrect keys lead to incorrect mapping of elements and poor performance.











Controlled vs Uncontrolled Components

1. Controlled Components
✔ Definition

A component where React controls the form input state.

The value displayed in the UI is always driven by component state (useState).

✔ Example
function Form() {
  const [name, setName] = useState("");

  return (
    <input 
      value={name}
      onChange={(e) => setName(e.target.value)}
    />
  );
}

✔ Characteristics

UI value ↔ React state is always in sync

Easy validation

Easy conditional disabling

Easy transformations, formatting

Easier to test

Works well with complex forms

✔ Drawback

More re-renders

More boilerplate for large forms



2. Uncontrolled Components
✔ Definition

A component where the DOM controls the form input state, not React.

You access the value using refs.

✔ Example
function Form() {
  const inputRef = useRef();

  const handleSubmit = () => {
    console.log(inputRef.current.value);  // Access DOM value
  };

  return <input ref={inputRef} />;
}


Characteristics

React does NOT track the value on every keystroke

Minimal re-renders

Simpler for basic forms

✔ Drawback

Harder to do real-time validation

Harder to sync UI with state

Less predictable

Not ideal for complex forms









Form Control Design Patterns in React



React encourages several ways of designing form architectures depending on the complexity.

1. Controlled Components (Most Common Pattern)

All form fields use React state.

Used when:

Validation on each keystroke

Dynamic enabling/disabling

Showing error messages live

Formatting input






2. Uncontrolled Components (DOM-driven)

Use refs to fetch data only on submit.

Used when:

Small forms (e.g., search input)

Integrating with non-React libraries (e.g., jQuery plugins)

File inputs




3. Hybrid Pattern (Controlled + Uncontrolled together)

Some fields are controlled, some are uncontrolled.

Example:

Controlled fields for email/password

Uncontrolled file input

Uncontrolled fields for heavy text areas

Reason:

Balance between performance and control.

example of Hybrid pattern

import React, { useState, useRef } from "react";

function SignupForm() {
  // Controlled fields
  const [name, setName] = useState("");
  const [email, setEmail] = useState("");

  // Uncontrolled fields
  const fileRef = useRef(null);
  const bioRef = useRef(null);

  const handleSubmit = (e) => {
    e.preventDefault();

    const file = fileRef.current.files[0];
    const bio = bioRef.current.value;

    console.log("Name:", name);
    console.log("Email:", email);
    console.log("Profile Pic:", file);
    console.log("Bio:", bio);
  };

  return (
    <form onSubmit={handleSubmit}>

      {/* Controlled input */}
      <input 
        type="text"
        placeholder="Name"
        value={name}
        onChange={(e) => setName(e.target.value)}
      />

      {/* Controlled input */}
      <input 
        type="email"
        placeholder="Email"
        value={email}
        onChange={(e) => setEmail(e.target.value)}
      />

      {/* Uncontrolled file input (React cannot control files) */}
      <input 
        type="file" 
        ref={fileRef} 
      />

      {/* Uncontrolled textarea for performance reasons */}
      <textarea 
        placeholder="Write your bio"
        ref={bioRef}
      />

      <button type="submit">Submit</button>
    </form>
  );
}

export default SignupForm;


Why is this a Hybrid Pattern?
✔ Controlled fields

Name, Email

React state updates on each keystroke

Good for validation, conditional UI, controlled behavior

✔ Uncontrolled fields

File input (React cannot control file contents → must use ref)

Bio textarea: Avoids expensive re-renders for large text




4. Lifting Form State Up Pattern

Managing form fields from a parent component.

Useful when:

Multiple components share form data

Wizard / multi-step forms

Container-presenter architecture


Code Example: Lifting Form State Up

Parent Component (Manages All State)


import React, { useState } from "react";
import PersonalInfo from "./PersonalInfo";
import AddressInfo from "./AddressInfo";

function SignupForm() {
  const [formData, setFormData] = useState({
    name: "",
    email: "",
    city: "",
    pincode: ""
  });

  const updateField = (field, value) => {
    setFormData(prev => ({
      ...prev,
      [field]: value
    }));
  };

  const handleSubmit = () => {
    console.log("Final Form Data:", formData);
  };

  return (
    <div>
      <h2>Signup Form</h2>

      <PersonalInfo formData={formData} updateField={updateField} />
      <AddressInfo formData={formData} updateField={updateField} />

      <button onClick={handleSubmit}>Submit</button>
    </div>
  );
}

export default SignupForm;

Child Component 1 — PersonalInfo.jsx
function PersonalInfo({ formData, updateField }) {
  return (
    <div>
      <h3>Personal Info</h3>

      <input
        type="text"
        placeholder="Name"
        value={formData.name}
        onChange={e => updateField("name", e.target.value)}
      />

      <input
        type="email"
        placeholder="Email"
        value={formData.email}
        onChange={e => updateField("email", e.target.value)}
      />
    </div>
  );
}

export default PersonalInfo;

Child Component 2 — AddressInfo.jsx
function AddressInfo({ formData, updateField }) {
  return (
    <div>
      <h3>Address Info</h3>

      <input
        type="text"
        placeholder="City"
        value={formData.city}
        onChange={e => updateField("city", e.target.value)}
      />

      <input
        type="text"
        placeholder="Pincode"
        value={formData.pincode}
        onChange={e => updateField("pincode", e.target.value)}
      />
    </div>
  );
}

export default AddressInfo;







5.Controlled with Reducer Pattern

For complex forms, use useReducer instead of multiple useStates.

function reducer(state, action) {
  return { ...state, [action.name]: action.value };
}


Used when:

10+ input fields

dynamic fields

complex validation logic



Registration Form Using useReducer

1. Reducer File (formReducer.js)
export const initialState = {
  name: "",
  email: "",
  age: "",
  city: "",
  error: ""
};

export function formReducer(state, action) {
  switch (action.type) {
    case "UPDATE_FIELD":
      return {
        ...state,
        [action.field]: action.value,
        error: "" // reset error on change
      };

    case "SET_ERROR":
      return {
        ...state,
        error: action.message
      };

    case "RESET_FORM":
      return initialState;

    default:
      return state;
  }
}

2. Parent Form Component Using the Reducer
import React, { useReducer } from "react";
import { formReducer, initialState } from "./formReducer";

function RegisterForm() {
  const [state, dispatch] = useReducer(formReducer, initialState);

  const handleSubmit = (e) => {
    e.preventDefault();

    if (!state.name || !state.email) {
      return dispatch({ type: "SET_ERROR", message: "Name and Email required" });
    }

    console.log("Form Submitted: ", state);
    dispatch({ type: "RESET_FORM" });
  };

  return (
    <form onSubmit={handleSubmit}>
      <h2>Register</h2>

      {/* Controlled inputs (via reducer state) */}
      <input
        type="text"
        placeholder="Name"
        value={state.name}
        onChange={(e) =>
          dispatch({ type: "UPDATE_FIELD", field: "name", value: e.target.value })
        }
      />

      <input
        type="email"
        placeholder="Email"
        value={state.email}
        onChange={(e) =>
          dispatch({ type: "UPDATE_FIELD", field: "email", value: e.target.value })
        }
      />

      <input
        type="number"
        placeholder="Age"
        value={state.age}
        onChange={(e) =>
          dispatch({ type: "UPDATE_FIELD", field: "age", value: e.target.value })
        }
      />

      <input
        type="text"
        placeholder="City"
        value={state.city}
        onChange={(e) =>
          dispatch({ type: "UPDATE_FIELD", field: "city", value: e.target.value })
        }
      />

      {state.error && <p style={{ color: "red" }}>{state.error}</p>}

      <button type="submit">Submit</button>
    </form>
  );
}

export default RegisterForm;

🧠 Why This Is Controlled With Reducer?
⭐ Controlled:

All inputs use value={state.field}

Updates go through React → predictable UI

Good for validation, conditional rendering, error messaging

⭐ Reducer:

All form state handled in one place

One centralized logic to update, validate, reset

Ideal for large forms where useState becomes messy











How do useCallback and useMemo actually prevent re-rendering?




React’s default behavior is:

When a component re-renders → all functions and objects inside it are recreated

Passing new references causes child components to re-render

useCallback and useMemo help avoid this.


Every render creates a new function reference:

const handleClick = () => {}


Even if the logic is identical:

handleClick on render #1 !== handleClick on render #2

Identity is different (because they are new function objects in memory)

If this function is passed to a child wrapped in React.memo():

<Child onClick={handleClick} />


React.memo sees prop changed → re-render.


What useCallback does
const handleClick = useCallback(() => {
  doSomething();
}, []);

useCallback ensures:

The same function instance is reused across renders

Unless its dependencies change

So now React.memo sees:

New props? ❌ No

Same function reference? ✔ Yes
→ Skip re-render

📌 Summary

useCallback prevents re-rendering ONLY when:

The callback is passed to a memoized child

The callback's identity would otherwise change every render


How useMemo prevents re-rendering (Indirectly)

useMemo memoizes computed values or objects, not functions.

Without useMemo

Objects and arrays are recreated on every render:

const filters = { status: "active" };  // new object every time


Even if identical in structure:

Render 1: filters = ObjectA

Render 2: filters = ObjectB

ObjectA !== ObjectB (different reference)

Child components receiving this object will re-render:

<Child filters={filters} />

⭐ What useMemo does
const filters = useMemo(() => ({ status: "active" }), []);


This returns:

The same object reference across renders

Until dependencies change

So React.memo sees:

Same object reference? ✔
→ Skip re-render

📌 Summary

useMemo prevents re-rendering only when:

The computed value is passed to memoized children

The object/array identity would trigger a re-render otherwise


✔ useCallback → memoizes functions
✔ useMemo → memoizes values
✔ Neither stops parent re-render
✔ They stop child re-renders by preventing prop identity change




Example Demonstrating How They Prevent Re-renders
function Parent({ count }) {
  const increment = useCallback(() => {
    console.log("increment");
  }, []);

  const config = useMemo(() => ({ theme: "dark" }), []);

  return (
    <>
      <Child1 onIncrement={increment} />
      <Child2 config={config} />
    </>
  );
}

// Memoized children
const Child1 = React.memo(({ onIncrement }) => {
  console.log("Child1 rendered");
});

const Child2 = React.memo(({ config }) => {
  console.log("Child2 rendered");
});

Renders:

If count changes → Parent re-renders

But Child1 and Child2 do not, because:

increment reference is stable

config reference is stable

Thus they skip re-render.


useCallback and useMemo do not stop the parent component from re-rendering. They prevent unnecessary child component re-renders by keeping references stable. A component wrapped in React.memo will skip re-rendering if its props are the same. useCallback keeps the same function reference across renders, while useMemo keeps the same object/value reference. This prevents prop identity from changing, which avoids triggering re-renders in memoized children.




Parent Component
import React, { useState, useCallback } from "react";

function Parent() {
  const [count, setCount] = useState(0);
  const [dark, setDark] = useState(false);

  // ❗ Without useCallback, this function is a NEW reference every render
  const handleIncrement = useCallback(() => {
    setCount((prev) => prev + 1);
  }, []); // stable reference

  const theme = {
    background: dark ? "#333" : "#fff",
    color: dark ? "#fff" : "#000",
  };

  return (
    <div style={theme}>
      <h2>Count: {count}</h2>

      <button onClick={() => setDark((prev) => !prev)}>Toggle Theme</button>

      {/* Child only re-renders when handleIncrement reference changes */}
      <Child onIncrement={handleIncrement} />
    </div>
  );
}

export default Parent;

Child Component (memoized)
import React from "react";

const Child = React.memo(({ onIncrement }) => {
  console.log("Child Rendered");
  return (
    <button onClick={onIncrement}>Increment Count</button>
  );
});

export default Child;





Without useCallback

Every Parent render creates a new function instance of handleIncrement.

Child receives new prop reference → Child re-renders.

Even if dark changes (not related to count), Child re-renders unnecessarily.

With useCallback

React memoizes the function and returns the same reference across renders.

Child re-renders only when dependencies change (none in this case).

Switching theme does NOT re-render Child.



handleIncrement is created during render, but it is not executed during render.

It only gets executed when you call it, which happens when the button in the Child component is clicked.

✅ Will the callback fire when clicking the Child button?
✔ YES — the callback executes when the user clicks:
<button onClick={onIncrement}>Increment Count</button>


That means:

onIncrement is the same function you passed (handleIncrement)

So clicking it calls setCount(prev => prev + 1)

The count updates

Parent re-renders

Child does not re-render (because useCallback keeps the same reference)

🧠 Important part

Even though Parent re-renders when count updates…

👉 Child does not re-render
because handleIncrement is memoized and does NOT change reference.

🧪 Example Explanation in 3 Steps1️⃣ Child button clicked

→ onIncrement() fires
→ which is handleIncrement().

2️⃣ handleIncrement updates state

→ setCount(prev + 1).

3️⃣ Parent re-renders

BUT Child does not re-render because:

props to Child didn’t change (function reference is stable due to useCallback)

Child is wrapped in React.memo





What is React.memo and when not to use it?


React.memo is a higher-order component that memoizes a functional component.

const MyComponent = React.memo(function MyComponent(props) {
  ...
});

What it does:

React.memo prevents unnecessary re-renders by re-rendering the component only if its props change (shallow comparison).


How React.memo works internally

React.memo performs a shallow comparison on props:

Primitives → compares by value

Objects, arrays, functions → compares by reference

If props are the same → skip re-render

If props changed → re-render normally


🎯 When to Use React.memo

Use it when:

✅ 1. Component is expensive to re-render

Examples:

large tables

complex UI widgets

charts

heavy computation inside render

✅ 2. Component receives stable props

Props that don’t change often, such as:

primitive values (string, number, boolean)

memoized functions (via useCallback)

memoized objects/arrays (via useMemo)

✅ 3. Component is re-rendering because the parent re-renders

React.memo avoids unnecessary renders caused by parent updates.



❌ When NOT to Use React.memo
❌ 1. Component is small/lightweight

Memoization overhead > render cost.
React.memo adds:

memory cost

comparison cost

extra work for React

Using it everywhere harms performance.

❌ 2. Props change on every render

If props are objects/functions created inline:

<MyComp data={{ a: 1 }} onClick={() => {}} />


These create new references each render → memo is useless.

Unless you also use:

useCallback

useMemo

❌ 3. List items where key changes

React.memo won’t help if the key or identity changes.

Bad:

items.map((item, index) => <Row key={index} item={item} />)


Index keys cause:

re-mounting

re-rendering

memo becomes ineffective

❌ 4. When the component depends heavily on children, not props

React.memo only checks props.
If children change constantly → component re-renders anyway.

❌ 5. When you have global state from Context API

Context changes re-render all consumers, even with React.memo.

Example:

const value = useContext(MyContext);


Even with memo:

memo cannot stop re-renders from context updates.






Explain React Suspense. How does it work internally?



React Suspense is a mechanism that allows React to pause rendering of part of the UI until some asynchronous resource (lazy-loaded component, data, etc.) is ready — and during that pause, show a fallback UI.

Suspense + Lazy Loading

The most common use is with React.lazy.

const Profile = React.lazy(() => import("./Profile"));

<Suspense fallback={<Spinner />}>
  <Profile />
</Suspense>

What happens here?

React.lazy(() => import()) triggers a dynamic import.


Suspense for Data Fetching (React 18)

Although Suspense originally only worked for lazy loading, with React 18 + Server Components + libraries, it now supports data fetching.

Example (conceptually):

function User() {
  const user = use(fetchUser());  
  return <div>{user.name}</div>;
}

<Suspense fallback={<UserSkeleton />}>
  <User />
</Suspense>


use() causes suspension until data resolves.

While the module is loading, the lazy component throws a Promise.

Suspense boundary catches the Promise and shows the fallback.

Once the Promise resolves (component loaded), Suspense re-renders the child tree.










When should you use Context API, and when should you avoid it?



What is Context API for?

React Context is meant for sharing data globally across many components without prop drilling.

Examples:

Theme (dark/light)

Authentication user object

Current locale/language

Global configuration

Feature flags



If multiple nested components need the same state but don’t modify it heavily, Context is ideal.

Examples:

UI theme

Logged-in user info

App locale / direction (LTR/RTL)

Read-only app configuration

Permissions


Use Context when you pass the same prop through 4–5 component levels only to reach the bottom.


2. Global state that rarely changes

Context is perfect for stable values that don’t update frequently.

Examples:

currentUser

themeMode

initialSettings


❌ When You Should AVOID Context API
1. When the state updates frequently

Context triggers re-rendering of all components that consume it
→ even if only one part of the app needs the update.

❗ This is the biggest reason to avoid Context.

Examples of high-frequency updates:

Typing in an input

Live search results

Animations

Counter updates

Data streams (WebSockets)


Use state management libraries instead:

Zustand

Redux Toolkit

Jotai

Recoil

They avoid the “Context re-render problem.”


2. When you need complex global state logic

Context is not a replacement for a state management library.

Avoid Context for:

Derived state

Middleware

Async flows

Undo/redo

DevTools

Caching

Server-synced state

Use:

Redux Toolkit (complex global logic)

Zustand/Jotai (simple but performant)

React Query (server-state)



When only SOME children need the state

Context has no built-in “selector” mechanism.

So if a context value is an object:

{ user, theme, settings }


ANY change inside it re-renders ALL consumers.

Better patterns:

Split Contexts into smaller ones

Use state libraries with selectors

Use useContextSelector (3rd-party)

4. When passing callbacks or large objects

Functions and objects change references → cause re-renders in Context consumers.

This leads to performance issues unless heavily memoized.










What are the drawbacks of using Redux?



Traditional Redux (before Redux Toolkit) requires multiple steps for simple operations:

Create actions

Create action creators

Create reducers

Combine reducers

Configure store

Dispatch actions manually

For a simple counter, you write many files and lines of code.

This leads to:

Verbose codebase

Slow development

Difficult onboarding for juniors

This is why Redux Toolkit (RTK) was created—to reduce boilerplate.


2️⃣ Unnecessary Re-Renders (Global State Problem)

Redux uses a single global store.

When any slice of state changes:

All connected components (via connect or useSelector) re-render, even if they only use part of the slice

This leads to “render storms”

Why it happens:

Redux uses strict equality (===) to detect changes

If a reducer returns a new object → all components subscribed to that slice re-render

Example:

const state = { user: {}, theme: {} };


If only theme changes:
→ Components using user still re-render unless carefully optimized

This becomes worse when:

Large UI trees

Frequent updates (typing, animations, websockets)


3️⃣ Performance Issues with Large Stores

Because everything is centralized:

A big store leads to longer update chains

Frequent dispatches can slow down the app

Nested components re-render deeply

You often need manual optimizations like:

memo

useCallback

selector memoization (reselect)

splitting reducers into smaller slices

This adds cognitive load.


4️⃣ Complexity for Simple Apps

Redux is overkill for most small-to-medium applications.

If your app only needs:

Local UI state

A few shared states

Lightweight global store

Redux is too heavy.

Simpler tools like:

Zustand

Jotai

Context API

Recoil

are easier and faster.








How does React handle Events under the hood?


How React Handles Events Under the Hood

React does NOT attach event listeners directly to DOM elements the way vanilla JS does.

Synthetic Events

React wraps native browser events inside its own unified event object called SyntheticEvent.

Why synthetic?

Normalizes event behavior across browsers

Provides a consistent API (e.g., onClick, onChange, etc.)

Lightweight wrapper around the real DOM event

Adds React-specific behavior & performance optimizations

Example:

<button onClick={(e) => console.log(e.type)}>Click</button>


e here is not the browser event → It's a React SyntheticEvent.










React Router with data loading


install the following command

npm create vite@4

How to plan and build react application

1. Gather application requirements and features
2. Divide the application into pages
  2.1 Think about the overall and page level UI
  2.2 Break the desired UI into components
  2.3 Deign and buil a static version (no state yet)
3. Divide the application into feature categories
  3.1 Think about state management (what data to store and where to store data) + data flow
4. Decide on what libraries to use

Project requirements from the business

step 1:-

Here in this example users can order one or more pizzas from a menu
Requires no user accounts and no login users just input their names before using the app
The pizza menu can change so it should be loaded from an API
Users can add multiple pizzas to cart before ordering 
Ordering requires just the user name , phone number and address
GPS location should be provided to make delivery easier
Users can mark their order as priority for additional 20% of cart price
Orders made by sending a POST request with order data (user data + selected pizza) to API
Payment made on delivery no payment processing is necessary in the app.
Each order will get a unique ID that should be displayed so the user can later look up their order based on the ID.
Users should be able to mark as priority even after ordering.


Step 2 + step 3:- 

Features + Pages

feature categories:-
1. User
2. Menu
3. Cart
4. Order

Necessary Pages:-
1. Home page (/) - feature categories User linked to this page
2. Pizza Menu (/menu) - feature categories Menu linked to this page
3. Cart (/cart) - feature categories Cart linked to this page
4. Placing a new order (/order/new) - feature categories Order linked to this page
5. Looking up an order (/order/:orderID) - feature categories Order linked to this page


Step 3 + step 4:- 

1. User - one state slice related to User -> Global UI state (no accounts so stay in app)
2. Menu - one state slice related to Menu -> Global remote state (menu is fetched from API)
3. Cart -  one state slice related to Cart -> Global UI state (no need for API just stored in app)
4. Order - one state slice related to Order -> Global remote state (fetched and submitted to API)

Routing - react router
Styling - tailwindcss 
Remote state management -  react router  - fetching data inside react router - not state management as it doesn't persist state
Ui state management - Redux - state is complex.

remote state management we prefer to use React query instead of react router




In src create a folder 'feature' and inside 'feature' we create folders like cart, menu, user, order
In src create a folder 'ui', in the 'ui' folder we create buttons, inputs etc.
In src create a folder 'services' where e write reusable code for interacting with an API.
In src create a folder 'utils' where we write helper functions that are stateless which doesn't create side effects.



npm install react-router-dom@6

data fetching in react router we use 'createBrowserRouter'

import { createBrowserRouter } from 'react-router-dom' in 'App.jsx' folder.


'createBrowserRouter' is a function where we define all routes an do it passing an array of objects where each object is one route.




import Home from './ui/Home';
import Menu from './feature/menu/Menu';

const router = createBrowserRouter([
  {path:'/', element: <Home />},
  {path:'/menu', element: <Menu />}
])






App.jsx

import { useState } from 'react'
import { createBrowserRouter, RouterProvider } from 'react-router-dom'
import Home from './ui/Home';
import Menu from './feature/menu/Menu';
import Cart from './feature/cart/Cart';
import CreateOrder from './feature/order/CreateOrder';
import Order from './feature/order/Order';

const router = createBrowserRouter([
  {path:'/', element: <Home />},
  {path:'/menu', element: <Menu />},
  {path: "/cart", element: <Cart />},
  {path:'/order/new', element: <CreateOrder />},
  {path: '/order/:orderId', element: <Order />}
])

function App() {
  

  return (
   <RouterProvider router={ router} />
  )
}

export default App





here we are declaring the router outside of JSX and using javascript array. This is to data loading or data fetching or data submitting with 'createBrowserRouter'. 
To use powerful APIs like data loaders, data actions or data fetchers create new router using 'createBrowserRouter' and provide 'router' in  'RouterProvider' component.

Built layout so we can connect with Router. this application we are going  to build for both large and small screens. Create a header with name to the company and link to homepage along with the username. Main page must be pizza menu or current cart view that displays how many items in the cart and link to cart (these are accessible from everywhere in the application , here we put in 'AppLayout.jsx'). So cart and header will be part of the layout. The amin portion of the page changes it can be menu, form, cart items listed.

Create file AppLayout.jsx and Header.jsx in 'ui' folder




AppLayout.jsx


import Header from "./Header";

export default function AppLayout(){
    return (
        <div>
           <Header /> 
           <main>
            <h1>Content</h1>
           </main>
        </div>
    )
}




Header.jsx


import { Link } from "react-router-dom";

export default function Header(){

    return (
        <header>
         <Link to='/'>Fast React Pizza Co.</Link>
        </header>
    )
}


nested routes can be provided by 'children' property in 'createBrowserRouter'. '{element: <AppLayout />} given inside 'createBrowserRouter' since its there in every page we dont give the path (since we dont give path to AppLayout we call it as 'layout route') and all other are 'children' routes.


const router = createBrowserRouter([
  {element: <AppLayout /> , children: [
    {path:'/', element: <Home />},
  {path:'/menu', element: <Menu />},
  {path: "/cart", element: <Cart />},
  {path:'/order/new', element: <CreateOrder />},
  {path: '/order/:orderId', element: <Order />}
  ]} 
  
])

when we click the cart link cart content should come and so in other page for the main content.
Render the content of nested route inside another route by providing <Outlet />



AppLayout.jsx

import CartOverview from "../feature/cart/CartOverview";
import Header from "./Header";

export default function AppLayout(){
    return (
        <div>
           <Header /> 
           <main>
            <h1>Content</h1>
            <Outlet />
           </main>
           <CartOverview />
        </div>
    )
}

AppLayout is the parent route of every single other route that we have in the application, hence we put all other routes as children in AppLayout in createBrowserRouter.


react routers data loading feature called loaders. When we create a function that fetches data from an API, we provide loader function to one of our routes and that route will fetch data as soon as application goes to that route and when data has arrived it will be provided to page component itself using custom hook.
Here we want to fetch the menu data we can do this by 3 steps : - first we create a loader, we provide a loader and provide data to the page. Since we want to load the Menu data  we place loader inside the 'Menu' component. Here the 'loader' function where the 'loader' function here fetch the data and return it.

In 'services' folder in 'apiRestaurant.js' file we call 'getMenu' in the 'loader' function to fetch the menu data.



Menu.jsx

import {getMenu} from "../../services/apiRestaurant"

function Menu() {
  return <h1>Menu</h1>;
}

export async function loader() {
  const menu = await getMenu()
  return menu;
}

export default Menu;


In App.jsx we rename loader as menuLoader like below :-

import Menu, {loader as menuLoader} from './feature/menu/Menu';


App.jsx

const router = createBrowserRouter([
  {element: <AppLayout /> , children: [
    {path:'/', element: <Home />},
  {path:'/menu', element: <Menu />, loader: menuLoader},
  {path: "/cart", element: <Cart />},
  {path:'/order/new', element: <CreateOrder />},
  {path: '/order/:orderId', element: <Order />}
  ]} 
  



In App.jsx full code


import { useState } from 'react'
import { createBrowserRouter, RouterProvider } from 'react-router-dom'
import Home from './ui/Home';
import Menu, {loader as menuLoader} from './feature/menu/Menu';
import Cart from './feature/cart/Cart';
import CreateOrder from './feature/order/CreateOrder';
import Order from './feature/order/Order';
import AppLayout from './ui/AppLayout'

const router = createBrowserRouter([
  {element: <AppLayout /> , children: [
    {path:'/', element: <Home />},
  {path:'/menu', element: <Menu />, loader: menuLoader},
  {path: "/cart", element: <Cart />},
  {path:'/order/new', element: <CreateOrder />},
  {path: '/order/:orderId', element: <Order />}
  ]} 
  
])

function App() {
  

  return (
   <RouterProvider router={ router} />
  )
}

export default App



After we want to have data in component using custom hook called 'useLoaderData'.



Menu.jsx

import { useLoaderData } from "react-router-dom";
import {getMenu} from "../../services/apiRestaurant"

function Menu() {
  const menu = useLoaderData();
  console.log(menu)
  return <h1>Menu</h1>;
}

export async function loader() {
  const menu = await getMenu()
  return menu;
}

export default Menu;


React router will start fetching data at same time as it starts rendering current route
We can get loading state from useNavigation hook as shown below



AppLayout.jsx

import CartOverview from "../feature/cart/CartOverview";
import Header from "./Header";
import { Outlet, useNavigation } from "react-router-dom";
import Loader from "./Loader";

export default function AppLayout(){
    const navigation = useNavigation();
    const loading = navigation.state === "loading";
    return (
        <div className="layout">
            {loading && <Loader />}
           <Header /> 
           <main>
            <h1>Content</h1>
            <Outlet />
           </main>
           <CartOverview />
        </div>
    )
}


Error page can be given as 'errorElement' in the parent layout element (here in AppLayout)
useRouteError() is a hook where we get the status and error of invalid route path

Header.jsx

import { Link } from "react-router-dom";
import SearchOrder from "../feature/order/SearchOrder";

export default function Header(){

    return (
        <header>
         <Link to='/'>Fast React Pizza Co.</Link>
         <SearchOrder />
        </header>
    )
}



SearchOrder.jsx


import { useState } from "react"
import { useNavigate } from "react-router-dom";

export default function SearchOrder(){
    const [query, setQuery] = useState("");
     var navigate = useNavigate();
    function handleSubmit(e){
        e.preventDefault();
        if(!query) return;
        navigate(`/order/${query}`);
        setQuery("")
    }
    return <form onSubmit={handleSubmit}>
        <input placeholder="Search Order ID" value={query} onChange={(e)=> setQuery(e.target.value)} />
    </form>
}


to get loader data we use 'useLoaderData()'




Order.jsx


// Test ID: IIDSAT

import { useLoaderData } from "react-router-dom";
import { getOrder } from "../../services/apiRestaurant";
import {
  calcMinutesLeft,
  formatCurrency,
  formatDate,
} from "../../utils/helpers";



function Order() {
  var order = useLoaderData();
  // Everyone can search for all orders, so for privacy reasons we're gonna gonna exclude names or address, these are only for the restaurant staff
  const {
    id,
    status,
    priority,
    priorityPrice,
    orderPrice,
    estimatedDelivery,
    cart,
  } = order;
  const deliveryIn = calcMinutesLeft(estimatedDelivery);

  return (
    <div>
      <div>
        <h2>Status</h2>

        <div>
          {priority && <span>Priority</span>}
          <span>{status} order</span>
        </div>
      </div>

      <div>
        <p>
          {deliveryIn >= 0
            ? `Only ${calcMinutesLeft(estimatedDelivery)} minutes left 😃`
            : "Order should have arrived"}
        </p>
        <p>(Estimated delivery: {formatDate(estimatedDelivery)})</p>
      </div>

      <div>
        <p>Price pizza: {formatCurrency(orderPrice)}</p>
        {priority && <p>Price priority: {formatCurrency(priorityPrice)}</p>}
        <p>To pay on delivery: {formatCurrency(orderPrice + priorityPrice)}</p>
      </div>
    </div>
  );
}

export async function loader({params}) {
  const order = await getOrder(params.orderId);
  return order;
}

export default Order;



Writing data with React router actions


Loaders are used to read data.
Action are used to mutate data or write data

When 'Form' from 'react-router-dom' is submitted then create a request that will intercepted by the action 'action' function (below) as soon as it is connected with React Router. When 'Form' submitted  React Router will call 'action' function  and will pass in request that was submitted, 'request.formData()' provided by the browser


CreateOrder.jsx


import { useState } from "react";
import { Form } from "react-router-dom";
import { createOrder } from "../../services/apiRestaurant";

// https://uibakery.io/regex-library/phone-number
const isValidPhone = (str) =>
  /^\+?\d{1,4}?[-.\s]?\(?\d{1,3}?\)?[-.\s]?\d{1,4}[-.\s]?\d{1,4}[-.\s]?\d{1,9}$/.test(
    str
  );

const fakeCart = [
  {
    pizzaId: 12,
    name: "Mediterranean",
    quantity: 2,
    unitPrice: 16,
    totalPrice: 32,
  },
  {
    pizzaId: 6,
    name: "Vegetale",
    quantity: 1,
    unitPrice: 13,
    totalPrice: 13,
  },
  {
    pizzaId: 11,
    name: "Spinach and Mushroom",
    quantity: 1,
    unitPrice: 15,
    totalPrice: 15,
  },
];

function CreateOrder() {
  // const [withPriority, setWithPriority] = useState(false);
  const navigation = useNavigation();
  const isSubmitting = navigation.state === 'submitting'
  const cart = fakeCart;

  return (
    <div>
      <h2>Ready to order? Let's go!</h2>

      <Form method="POST">
        <div>
          <label>First Name</label>
          <input type="text" name="customer" required />
        </div>

        <div>
          <label>Phone number</label>
          <div>
            <input type="tel" name="phone" required />
          </div>
        </div>

        <div>
          <label>Address</label>
          <div>
            <input type="text" name="address" required />
          </div>
        </div>

        <div>
          <input
            type="checkbox"
            name="priority"
            id="priority"
            // value={withPriority}
            // onChange={(e) => setWithPriority(e.target.checked)}
          />
          <label htmlFor="priority">Want to yo give your order priority?</label>
        </div>

        <div>
          <input type="hidden" name="cart" value={JSON.stringify(cart)} />
           <button disabled={isSubmitting}>{isSubmitting ? 'Submitting...' : 'Order now'}</button>
        </div>
      </Form>
    </div>
  );
}

export async function action({request}){
  const formData = await request.formData();
  const data = Object.fromEntries(formData);
  const order = { ...data, cart: JSON.parse(data.cart), priority: data.priority === 'on'}
const errors={};
  if(!isValidPhone(order.phone)) errors.phone = "Please give us your correct phone number. We might need it to contact you"
  if(Object.keys(errors).length > 0) return errors;
  const newOrder = await createOrder(order)
  return redirect(`/order/${newOrder.id}`);
}

export default CreateOrder;




'Object.fromEntries(formData)' will get the formdata values entered in form. ' <input type="hidden" name="cart" value={JSON.stringify(cart)} />' will also add cart data inside the 'formValues' in 'action' function



App.jsx

import { useState } from 'react'
import { createBrowserRouter, RouterProvider } from 'react-router-dom'
import Home from './ui/Home';
import Menu, {loader as menuLoader} from './feature/menu/Menu';
import Cart from './feature/cart/Cart';
import CreateOrder,  {action as createOrderAction} from './feature/order/CreateOrder';
import Order, {loader as orderLoader} from './feature/order/Order';
import AppLayout from './ui/AppLayout';
import Error from './ui/Error'

const router = createBrowserRouter([
  {element: <AppLayout /> , errorElement: <Error />, children: [
    {path:'/', element: <Home />},
  {path:'/menu', element: <Menu />, loader: menuLoader},
  {path: "/cart", element: <Cart />},
  {path:'/order/new', element: <CreateOrder />, action: createOrderAction},
  {path: '/order/:orderId', element: <Order />, loader: orderLoader, errorElement: <Error />}
  ]} 
  
])

function App() {
  

  return (
   <RouterProvider router={ router} />
  )
}

export default App



When 'Form' on this path '/order/new' is submitted (here CreateOrder) then action thats specified will be called.





Error handling in Form actions

Since ' {path:'/order/new', element: <CreateOrder />, action: createOrderAction}' action is linked to 'CreateOrder' component all te values returned in the 'createOrderAction' function will be available in 'CreateOrder' using 'useActionData'.

CreateOrder.jsx

import { useState } from "react";
import { Form, redirect, useActionData, useNavigate, useNavigation } from "react-router-dom";
import { createOrder } from "../../services/apiRestaurant";

// https://uibakery.io/regex-library/phone-number
const isValidPhone = (str) =>
  /^\+?\d{1,4}?[-.\s]?\(?\d{1,3}?\)?[-.\s]?\d{1,4}[-.\s]?\d{1,4}[-.\s]?\d{1,9}$/.test(
    str
  );

const fakeCart = [
  {
    pizzaId: 12,
    name: "Mediterranean",
    quantity: 2,
    unitPrice: 16,
    totalPrice: 32,
  },
  {
    pizzaId: 6,
    name: "Vegetale",
    quantity: 1,
    unitPrice: 13,
    totalPrice: 13,
  },
  {
    pizzaId: 11,
    name: "Spinach and Mushroom",
    quantity: 1,
    unitPrice: 15,
    totalPrice: 15,
  },
];

function CreateOrder() {
  const navigation = useNavigation();
  const isSubmitting = navigation.state === 'submitting';
  const formErrors = useActionData();
  // const [withPriority, setWithPriority] = useState(false);
  const cart = fakeCart;

  return (
    <div>
      <h2>Ready to order? Let's go!</h2>

      <Form method="POST">
        <div>
          <label>First Name</label>
          <input type="text" name="customer" required />
        </div>

        <div>
          <label>Phone number</label>
          <div>
            <input type="tel" name="phone" required />
          </div>
          {formErrors?.phone && <p>{formErrors.phone}</p>}
        </div>

        <div>
          <label>Address</label>
          <div>
            <input type="text" name="address" required />
          </div>
        </div>

        <div>
          <input
            type="checkbox"
            name="priority"
            id="priority"
            // value={withPriority}
            // onChange={(e) => setWithPriority(e.target.checked)}
          />
          <label htmlFor="priority">Want to yo give your order priority?</label>
        </div>

        <div>
          <input type="hidden" name="cart" value={JSON.stringify(cart)} />
          <button disabled={isSubmitting}>{isSubmitting ? 'Submitting...' : 'Order now'}</button>
        </div>
      </Form>
    </div>
  );
}

export async function action({request}){
  const formData = await request.formData();
  const data = Object.fromEntries(formData)
  const order = { ...data, cart: JSON.parse(data.cart), priority: data.priority === 'on'};
  const errors={};
  if(!isValidPhone(order.phone)) errors.phone = "Please give us your correct phone number. We might need it to contact you"
  if(Object.keys(errors).length > 0) return errors;
  const newOrder = await createOrder(order);
  
  
  return redirect(`/order/${newOrder.id}`);
}

export default CreateOrder;









Tailwind CSS


Tailwind is a utility first cSS framework packed with utility classes like flex, text-center and rotate-90, among many other classes taht can be composed to build any design directly in your markup in HTML or JSX.
Utility first CSS write lots of tiny classes where each class has one single purpose and combine these classes to built entire components and layouts.


For vite project to install tailwind following commands

npm install -D tailwindcss@3 postcss autoprefixer
npx tailwindcss init -p


Your tailwind.config.js must include the content array as follows

content: [
  "./index.html",
  "./src/**/*.{js,ts,jsx,tsx}",
]



In index.css include the following on top

@tailwind base;
@tailwind components;
@tailwind utilities;


Home.jsx


function Home() {
  return (
    <div>
      <h1 className="text-xl text-yellow-500 font-semibold text-stone-700">
        The best pizza.
        <br />
        <span className="text-yellow-500">
 		Straight out of the oven, straight to you.
        </span>
      </h1>
    </div>
  );
}

export default Home;



'npm install -D prettier prettier-plugin-tailwindcss' will automatically sort the order of class name in the order with which tailwind recommends. 'font-semibold' denotes font weight as semibold.

In 'prettier.config.js' place the following

export default {
  "plugins": ["prettier-plugin-tailwindcss"]
}



' text-yellow-500' here text color set to yello with intensity 500. 'text-xl' text set to extra large.


export default function Username(){
    return (
        <div className="text-sm font-semibold">
            Bini Babu
        </div>
    )
}


'text-sm' text to smaller.



Header.jsx

import { Link } from "react-router-dom";
import SearchOrder from "../feature/order/SearchOrder";

export default function Header(){

    return (
        <header className="bg-yellow-200 px-4 py-3 border-b border-stone-600">
         <Link to='/' className="tracking-widest">Fast React Pizza Co.</Link>
         <SearchOrder />
         <Username />
        </header>
    )
}



'bg-yellow-200' bg denote backgroundcolor with yellow at intensity 200. 'tracking-widest' provides letter-spacing. 'tracking-[5px]' gives letter spacing of 5px. 'px-4'  denotes left and right padding 16px. 'py-3' denotes padding top and bottom 12px. 'border-b' denotes border at bottom and 'border-stone-600' denotes border color stone. 'border-b-8' 8 denotes  border width



CartOverview.jsx


import { Link } from "react-router-dom";

function CartOverview() {
  return (
    <div className="bg-stone-700 text-stone-200 uppercase p-4">
      <p className="space-x-4  font-semibold text-stone-300">
        <span>23 pizzas</span>
        <span>$23.45</span>
      </p>
      <Link to='/cart'>Open cart &rarr;</Link>
    </div>
  );
}

export default CartOverview;



'bg-stone-700' set to background color to stone with intensity 700 and text color set to stone color with intensity 200. 'uppercase' transfers the text to uppercase. 'p-4' denotes padding to left, right, bottom, left to 16px. 'space-x-4 ' provides space of 16px horizontally.



Home.jsx


import CreateUser from '../feature/user/CreateUser'
function Home() {
  return (
    <div className='my-10 text-center'>
      <h1 className="text-xl font-semibold mb-4">
        The best pizza.
        <br />
        <span className="text-yellow-500">
 Straight out of the oven, straight to you.
        </span>
       
      </h1>
      <CreateUser />
    </div>
  );
}

export default Home;


mb-4 denotes margin bottom to 16px
mx-0 denotes margin left and margin right to 0px
my-0 denotes margin bottom and margin top to 0px



Responsive design Tailwind css

'sm' denotes minimum width of 640px, 'md' minimum width of 768px, 'lg' minimum width of 1024px, 'xl' minimum width of 1280px, '2xl' minimum width of 1536px

sm:my-16 denotes  minimum width of 640px of margin top and bottom of 64px when the width of screen below 640px then the default css will come into effect here in the bottom my-10


Home.jsx


import CreateUser from '../feature/user/CreateUser'
function Home() {
  return (
    <div className='my-10 text-center sm:my-16'>
      <h1 className="text-xl font-semibold  mb-8">
        The best pizza.
        <br />
        <span className="text-yellow-500">
 Straight out of the oven, straight to you.
        </span>
       
      </h1>
      <CreateUser />
    </div>
  );
}

export default Home;




Header.jsx


import { Link } from "react-router-dom";
import SearchOrder from "../feature/order/SearchOrder";
import Username from "../feature/user/Username";

export default function Header(){

    return (
        <header className="bg-yellow-200 px-4 py-3 border-b border-stone-600 sm:px-6">
         <Link to='/' className="tracking-widest">Fast React Pizza Co.</Link>
         <SearchOrder />
         <Username />
        </header>
    )
}




CartOverview.jsx

import { Link } from "react-router-dom";

function CartOverview() {
  return (
    <div className="bg-stone-700 text-stone-200 uppercase p-4 sm:px-6 md:text-base">
      <p className="space-x-4 font-semibold text-stone-300 sm:space-x-6">
        <span>23 pizzas</span>
        <span>$23.45</span>
      </p>
      <Link to='/cart'>Open cart &rarr;</Link>
    </div>
  );
}

export default CartOverview;



'md:text-base' denotes when width of screen starts from 768px then the text is set base which means default.
'w-72' denotes width to 128px, 'h-10' to 40px



CreateUser.jsx


import { useState } from 'react';

function CreateUser() {
  const [username, setUsername] = useState('');

  function handleSubmit(e) {
    e.preventDefault();
  }

  return (
    <form onSubmit={handleSubmit}>
      <p className='mb-4 text-sm text-stone-600 md:text-base'>👋 Welcome! Please start by telling us your name:</p>

      <input
        type="text"
        placeholder="Your full name"
        value={username}
        onChange={(e) => setUsername(e.target.value)} className='w-72 h-10'
      />

      {username !== '' && (
        <div>
          <button>Start ordering</button>
        </div>
      )}
    </form>
  );
}

export default CreateUser;






Flex tailwind CSS


'flex items-center justify-between' converts to flex using make 'flex' items center using 'items-center' and put space between items using 'justify-between' 


CartOverview.jsx


import { Link } from "react-router-dom";

function CartOverview() {
  return (
    <div className="flex items-center justify-between bg-stone-700 text-stone-200 uppercase p-4 sm:px-6 md:text-base">
      <p className="space-x-4 font-semibold text-stone-300 sm:space-x-6">
        <span>23 pizzas</span>
        <span>$23.45</span>
      </p>
      <Link to='/cart'>Open cart &rarr;</Link>
    </div>
  );
}

export default CartOverview;



Header.jsx




Grid Tailwind CSS


To place footer to bottom of the screen we place 'grid' to home page so the header, main and footer section will be properly aligned.

'grid grid-rows-3 gap-4' placing grid of css with items in page placed in rows using 'grid-rows-3' where header, main and footer placed in 3 rows.

' h-screen grid-rows-[auto_1fr_auto]' here 'h-screen' takes the height of the screen of 100vh and 'grid-rows-[auto_1fr_auto]' here header and footer aligned rows of auto, main portionallocates maximum space of 1fr.

'overflow-scroll' will provide scroll to only main portion since 'overflow-scroll' given in main className.

max-w-3xl provides maximum width of 3xl in size even for smaller screen.



App.Layout.jsx

import CartOverview from "../feature/cart/CartOverview";
import Header from "./Header";
import { Outlet, useNavigation } from "react-router-dom";
import Loader from "./Loader";

export default function AppLayout(){
    const navigation = useNavigation();
    const loading = navigation.state === "loading";
    return (
        <div className="grid h-screen grid-rows-[auto_1fr_auto] gap-4">
            {loading && <Loader />}
           <Header /> 
           <main className="overflow-scroll bg-red-400 max-w-3xl">
            <h1>Content</h1>
            <Outlet />
           </main>
           <CartOverview />
        </div>
    )
}









Project WildOasis requirement 

1. Authentication
Users of the app are hotel emplyees. They need to be logged into the application to perform tasks.
New users can only be signed up insde the applications ( to guarantee that only actual hotel employees can get accounts)
Users should be able to upload an avatar, and change their name and password.

2.Cabins
App needs a table view with all cabins, showing the cabin photo, name, capacity, price and current discount
Users should be able to update or delete a cabin and to create new cabins (including uploading a photo)

3. Bookings
App needs a table view with all bookings showing arrival and departure dates status and paid amount as well as cabin and guest data.
The booking status can be "unconfirmed" (booked but not yet checked in), "checked in" or "checked out". The table should be filterable by this important status.
Other booking data includes : number of guests, number of nights, guest observations, whether they booked breakfast , breakfast price.

4. Check in /out
Users should be able to delete, check in or check out a booking as the guest arrives (no editing necessary for now)
Bookings may not have been paid yet on guest arrival. Therefore on check in users need to accept payment (outside the app) and then confirm the payment has been received (inside the app).
On check in the guest should have the ability to add breakfast for the entire stay if they hadn't already

5. Guests
Guest data should contain : full name , email, national ID, nationality and a country flag for easy identification.

6. Dashboard
The initial app screen should be a dashboard to display important information for thelast 7, 30 or 90 days: 
  A list of guests checking in and out on the current day. Users should be able to perform these tasks from here 
  Statistics on recent bookings, sales, check ins, and occupancy rate
  A chart showing all daily hotel sales, showing both "total" sales and "extras" sales (only breakfast at the moment)
  A chart showing statistics on stay durations as this is an important metric for the hotel.

7. Settings
Users should be able to define a few application wide settings: breakfast price min and max nights/booking, max guests/booking

App need a dark mode


Features + pages

Feature categories
1. Bookings
2. Cabins
3. Guests
4. Dashboard
5. Check in and out
6. App settings
7. Authentication

Necessary pages
1. Dashboard (/dashboard)
2. Bookings  (/bookings)
3. Cabins (/cabins)
4. Booking check in (/checkin/:bookingID)
5. App settings (/settings)
6. User sign up (/users)
7. Login (/login)
8. Account stings (/account)


Client side rendering and server side rendering

1. Client side rendering with plain React

Used to build single page applications.
All HTML is rendered on the client.
Rendering of Client side rendering which means JavaScript needs to be downloaded before apps start running (bad for performance when using low internet).
One perfect use case: apps that are used "internally" as tools inside companies that are entirely hidden behind a login.

2. Server side rendering with framework like Next.js

Used to build Multi page applications.
Soe HTML i rendered in the server.
More performant as less JavaScript needs to be downloaded.







For routing in WildOasis project we use React Router.
For styling in WildOasis project we use styled components.
Remote state management used in WildOasis project is React Query (best way of managing remote state with features like caching, automatic re-fetching, pre-fetching, offline support etc.
UI state management in WildOasis project used here is context API ( there is almost no UI state needed in this app, so simple context with useState will be enough no need for redux).
Form management used in WildOasis is React Hook Form (handling bigger forms can be a lot of work as manual state creation and errorhandling, alibrary can simplify all this)
React hot toast for notifications, recharts for displaying beautiful charts, date-fns for date manipulation.


npm create vite@4

Also do 'npm install'

To install styled components the following command:-

npm install styled-components






Import styled-components in the react components


App.jsx

import styled from "styled-components";
import GlobalStyles from "./styles/GlobalStyles";

const H1 = styled.h1`
font-size: 30px;
font-weight: 600;
`
const Button = styled.button`
  font-size: 1.4rem;
  padding: 1.2rem 1.6rem;
  font-weight: 500;
  border: none;
  background-color: purple;
  color: white;
  margin: 20px;
  cursor: pointer;
`

const Input = styled.input`
  border: 1px solid #ddd;
  border-radius: 5px;
  padding: 0.8rem 1.2rem;
`

const StyledApp = styled.div`
background-color: orangered;
padding: 20px;
`

function App() {
  return (
    <>
     <GlobalStyles />
     <StyledApp>
      <H1>Hello World</H1>
      <Button onClick={()=>alert("Check in")}>Check in</Button>
      <Button onClick={()=>alert("Check out")}>Check out</Button>
      <Input type="number" placeholder="Number of Guests" />
     </StyledApp>
    </>
  )
}

export default App




Install VS code extensions 'vscode-styled-components'



Global styles with styled components


styles/GlobalStyles.js



import { createGlobalStyle } from "styled-components";

const GlobalStyles = createGlobalStyle`
:root {
  /* Indigo */
  --color-brand-50: #eef2ff;
  --color-brand-100: #e0e7ff;
  --color-brand-200: #c7d2fe;
  --color-brand-500: #6366f1;
  --color-brand-600: #4f46e5;
  --color-brand-700: #4338ca;
  --color-brand-800: #3730a3;
  --color-brand-900: #312e81;

  /* Grey */
  --color-grey-0: #fff;
  --color-grey-50: #f9fafb;
  --color-grey-100: #f3f4f6;
  --color-grey-200: #e5e7eb;
  --color-grey-300: #d1d5db;
  --color-grey-400: #9ca3af;
  --color-grey-500: #6b7280;
  --color-grey-600: #4b5563;
  --color-grey-700: #374151;
  --color-grey-800: #1f2937;
  --color-grey-900: #111827;

  --color-blue-100: #e0f2fe;
  --color-blue-700: #0369a1;
  --color-green-100: #dcfce7;
  --color-green-700: #15803d;
  --color-yellow-100: #fef9c3;
  --color-yellow-700: #a16207;
  --color-silver-100: #e5e7eb;
  --color-silver-700: #374151;
  --color-indigo-100: #e0e7ff;
  --color-indigo-700: #4338ca;

  --color-red-100: #fee2e2;
  --color-red-700: #b91c1c;
  --color-red-800: #991b1b;

  --backdrop-color: rgba(255, 255, 255, 0.1);

  --shadow-sm: 0 1px 2px rgba(0, 0, 0, 0.04);
  --shadow-md: 0px 0.6rem 2.4rem rgba(0, 0, 0, 0.06);
  --shadow-lg: 0 2.4rem 3.2rem rgba(0, 0, 0, 0.12);

  --border-radius-tiny: 3px;
  --border-radius-sm: 5px;
  --border-radius-md: 7px;
  --border-radius-lg: 9px;

  /* For dark mode */
  --image-grayscale: 0;
  --image-opacity: 100%;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  padding: 0;
  margin: 0;

  /* Creating animations for dark mode */
  transition: background-color 0.3s, border 0.3s;
}

html {
  font-size: 62.5%;
}

body {
  font-family: "Poppins", sans-serif;
  color: var(--color-grey-700);

  transition: color 0.3s, background-color 0.3s;
  min-height: 100vh;
  line-height: 1.5;
  font-size: 1.6rem;
}

input,
button,
textarea,
select {
  font: inherit;
  color: inherit;
}

button {
  cursor: pointer;
}

*:disabled {
  cursor: not-allowed;
}

select:disabled,
input:disabled {
  background-color: var(--color-grey-200);
  color: var(--color-grey-500);
}

input:focus,
button:focus,
textarea:focus,
select:focus {
  outline: 2px solid var(--color-brand-600);
  outline-offset: -1px;
}

/* Parent selector, finally 😃 */
button:has(svg) {
  line-height: 0;
}

a {
  color: inherit;
  text-decoration: none;
}

ul {
  list-style: none;
}

p,
h1,
h2,
h3,
h4,
h5,
h6 {
  overflow-wrap: break-word;
  hyphens: auto;
}

img {
  max-width: 100%;

  /* For dark mode */
  filter: grayscale(var(--image-grayscale)) opacity(var(--image-opacity));
}
`


export default GlobalStyles;



App.jsx


import styled from "styled-components";
import GlobalStyles from "./styles/GlobalStyles";
import Button from "./ui/Button";
import Input from "./ui/Input";

const H1 = styled.h1`
font-size: 30px;
font-weight: 600;
`

const StyledApp = styled.div`
background-color: orangered;
padding: 20px;
`

function App() {
  return (
    <>
     <GlobalStyles />
     <StyledApp>
      <H1>Hello World</H1>
      <Button onClick={()=>alert("Check in")}>Check in</Button>
      <Button onClick={()=>alert("Check out")}>Check out</Button>
      <Input type="number" placeholder="Number of Guests" />
     </StyledApp>
    </>
  )
}

export default App





Input.jsx



import styled from "styled-components";
const Input = styled.input`
  border: 1px solid var(--color-grey-300);
  background-color: var(--color-grey-0);
  border-radius:  var(--border-radius-sm);
  padding: 0.8rem 1.2rem;
  box-shadow: var(--shadow-sm);
`

export default Input;



Button.jsx


import styled, { css } from "styled-components";

const sizes = {
  small: css`
    font-size: 1.2rem;
    padding: 0.4rem 0.8rem;
    text-transform: uppercase;
    font-weight: 600;
    text-align: center;
  `,
  medium: css`
    font-size: 1.4rem;
    padding: 1.2rem 1.6rem;
    font-weight: 500;
  `,
  large: css`
    font-size: 1.6rem;
    padding: 1.2rem 2.4rem;
    font-weight: 500;
  `,
};

const variations = {
  primary: css`
    color: var(--color-brand-50);
    background-color: var(--color-brand-600);

    &:hover {
      background-color: var(--color-brand-700);
    }
  `,
  secondary: css`
    color: var(--color-grey-600);
    background: var(--color-grey-0);
    border: 1px solid var(--color-grey-200);

    &:hover {
      background-color: var(--color-grey-50);
    }
  `,
  danger: css`
    color: var(--color-red-100);
    background-color: var(--color-red-700);

    &:hover {
      background-color: var(--color-red-800);
    }
  `,
};

const Button = styled.button`
  font-size: 1.4rem;
  padding: 1.2rem 1.6rem;
  font-weight: 500;
  border: var(--border-radius-sm);
  background-color: var(--color-brand-500);
  color: var(--color-brand-50);
  box-shadow: var(--shadow-sm);
  cursor: pointer;

  &:hover {
      background-color: var(--color-brand-700);
    }
`
export default Button;






To add a variable for css we can add the following, where 'css' is a helper function to generate CSS from a template literal with interpolations.

const test = css`
    text-align: center;
`



Full code Heading.jsx


import styled, { css } from "styled-components";

const test = css`
    text-align: center;
`

const Heading = styled.h1`
font-size: 30px;
font-weight: 600;
${test}
`

export default Heading;




Passing prop to 'Heading' component


We can pass 'type' to Heading component from App.jsx like below and 'as' property ensures we refer to 'h2' or 'h3' in the HTML tag. Whatever we pass to 'as' property will be the lement to be rendered in HTML.


<Heading as="h1">Hello World</Heading>
<Heading as="h2">Check in and out</Heading>
<Heading as="h3">Form</Heading>



Full App.jsx



import styled from "styled-components";
import GlobalStyles from "./styles/GlobalStyles";
import Button from "./ui/Button";
import Input from "./ui/Input";
import Heading from './ui/Heading'
const StyledApp = styled.div`
background-color: orangered;
padding: 20px;
`

function App() {
  return (
    <>
     <GlobalStyles />
     <StyledApp>
      <Heading as="h1">Hello World</Heading>
      <Heading as="h2">Check in and out</Heading>
      <Button onClick={()=>alert("Check in")}>Check in</Button>
      <Button onClick={()=>alert("Check out")}>Check out</Button>
      <Heading as="h3">Form</Heading>
      <Input type="number" placeholder="Number of Guests" />
     </StyledApp>
    </>
  )
}

export default App


Heading.jsx


import styled, { css } from "styled-components";



const Heading = styled.h1`
${(props) => props.as === 'h1' && css`
    font-size: 30px;
    font-weight: 600;
`}
line-height: 1.4
`

export default Heading;



Here the following code snippet from above the code 

${(props) => props.as === 'h1' && css`
    font-size: 30px;
    font-weight: 600;
`}

Here we are accepting 'props' from App.jsx in Heading.jsx checking if 'as = h1' then css is set to the  'font-size: 30px; font-weight: 600; '. Similarly for 'type = h2' and 'type = h3'





Full code Heading.jsx



import styled, { css } from "styled-components";



const Heading = styled.h1`
${(props) => props.as === 'h1' && css`
    font-size: 3rem;
    font-weight: 600;
`}
${(props) => props.as === 'h2' && css`
    font-size: 2rem;
    font-weight: 600; 
`}
${(props) => props.as === 'h3' && css`
    font-size: 1rem;
    font-weight: 500;
`}
line-height: 1.4
`

export default Heading;





Reusable styled components

In App.jsx we use 'variant' and 'size' in 'Button' component

<Button variation="primary" size="medium" onClick={()=>alert("Check in")}>Check in</Button>
<Button variation="secondary" size="small" onClick={()=>alert("Check out")}>Check out</Button>



In 'Button.jsx' 


const Button = styled.button`
  border: none;
  border-radius: var(--border-radius-sm);
  box-shadow: var(--shadow-sm);
  ${(props => sizes[props.size])}
  ${(props=> variations[props.variation])}
`


Button.defaultProps = {
  variation :  'primary',
  size: 'medium'
}



'defaultProps' is to set default props. So 'Check in' button will have this default props.




Full App.jsx


import styled from "styled-components";
import GlobalStyles from "./styles/GlobalStyles";
import Button from "./ui/Button";
import Input from "./ui/Input";
import Heading from './ui/Heading'
import Row from "./ui/Row";
const StyledApp = styled.div`
padding: 20px;
`

function App() {
  return (
    <>
     <GlobalStyles />
     <StyledApp>
      <Row type="vertical">
       <Row type="horizontal">
      <Heading as="h1">Hello World</Heading>
      <div>
      <Heading as="h2">Check in and out</Heading>
      <Button onClick={()=>alert("Check in")}>Check in</Button>
      <Button variation="secondary" size="small" onClick={()=>alert("Check out")}>Check out</Button>
      </div>
     
      </Row>
      <Row type="vertical">
       <Heading as="h3">Form</Heading>
      <form>
        <Input type="number" placeholder="Number of Guests" />
      </form>
      </Row>
      </Row>
     </StyledApp>
    </>
  )
}

export default App




Full Button.jsx


import styled, { css } from "styled-components";

const sizes = {
  small: css`
    font-size: 1.2rem;
    padding: 0.4rem 0.8rem;
    text-transform: uppercase;
    font-weight: 600;
    text-align: center;
  `,
  medium: css`
    font-size: 1.4rem;
    padding: 1.2rem 1.6rem;
    font-weight: 500;
  `,
  large: css`
    font-size: 1.6rem;
    padding: 1.2rem 2.4rem;
    font-weight: 500;
  `,
};

const variations = {
  primary: css`
    color: var(--color-brand-50);
    background-color: var(--color-brand-600);

    &:hover {
      background-color: var(--color-brand-700);
    }
  `,
  secondary: css`
    color: var(--color-grey-600);
    background: var(--color-grey-0);
    border: 1px solid var(--color-grey-200);

    &:hover {
      background-color: var(--color-grey-50);
    }
  `,
  danger: css`
    color: var(--color-red-100);
    background-color: var(--color-red-700);

    &:hover {
      background-color: var(--color-red-800);
    }
  `,
};

const Button = styled.button`
  border: none;
  border-radius: var(--border-radius-sm);
  box-shadow: var(--shadow-sm);
  ${(props => sizes[props.size])}
  ${(props=> variations[props.variation])}
`

Button.defaultProps = {
  variation :  'primary',
  size: 'medium'
}
export default Button;




Install react router

npm i react-router-dom@6




App.jsx modified to he following


import styled from "styled-components";
import GlobalStyles from "./styles/GlobalStyles";
import AppLayout from './ui/AppLayout'
import { BrowserRouter, Routes, Route, Navigate } from "react-router-dom";
import Dashboard from './pages/Dashboard'
import Bookings from './pages/Bookings';
import Cabins from './pages/Cabins';
import Users from './pages/Users';
import Settings from './pages/Settings';
import Account from './pages/Account';
import Login from './pages/Login';
import PageNotFound from './pages/PageNotFound';



function App() {
  return (
    <>
    <GlobalStyles />
    <BrowserRouter>
    <Routes>
      <Route element={<AppLayout />}>
      <Route index element={<Navigate replace to="dashboard" />} />
      <Route path="dashboard" element={<Dashboard />} />
      <Route path="bookings" element={<Bookings />} />
      <Route path="cabins" element={<Cabins />} />
      <Route path="users" element={<Users />} />
      <Route path="settings" element={<Settings />} />
      <Route path="account" element={<Account />} />
      </Route>
      <Route path="login" element={<Login />} />
      <Route path="*" element={<PageNotFound />} />
    </Routes>
    </BrowserRouter>
    </>
    
  )
}

export default App


Here 'AppLayout.jsx' is placed inside src/ui folder and components like 'Dashboard', 'Bookings', 'Cabins', 'Users', 'Settings', 'Account' are child routes to the 'AppLayout' route. And give <Outlet /> in AppLayout.jsx



AppLayout.jsx


import { Outlet } from "react-router-dom";

export default function AppLayout(){
    return (
        <div>
            <h1>App Layout</h1>
            <Outlet />
        </div>
    )
}






create 2 files 'Header.jsx' and 'Sidebar.jsx' in 'ui' folder.



AppLayout.jx


import { Outlet } from "react-router-dom";
import Header from "./Header";
import Sidebar from "./Sidebar";
import styled from "styled-components";

const StyledAppLayout = styled.div`
    display: grid;
    grid-template-columns: 26rem 1fr;
    grid-template-rows: auto 1fr;
    height: 100vh;
`

const Main = styled.main`
    background-color: var(--color-grey-50);
    padding: 4rem 4.8rem 6.4rem;
`

export default function AppLayout(){
    return (
        <StyledAppLayout>
            <Header />
            <Sidebar />
            <Main>
             <Outlet />
            </Main>
        </StyledAppLayout>
    )
}




Header.jsx


import styled from "styled-components"

const StyledHeader = styled.header`
    background-color: var(--color-grey-0);
    padding: 1.2rem 4.8rem;
    border-radius: 1px solid var(--color-grey-100);
`


export default function Header(){
    return (
        <StyledHeader>
        header
        </StyledHeader>
    )
}



Sidebar.jsx


import styled from "styled-components"

const StyledSidebar = styled.aside`
    background-color: var(--color-grey-0);
    padding: 3.2rem 2.4rem;
    border-right: 1px solid var(--color-grey-100);
    grid-row: 1 / -1;
    display: flex;
    flex-direction: column;
    gap: 3.2rem;
`

export default function Sidebar(){
    return (
        <StyledSidebar>
        <Logo />
        <MainNav />
        </StyledSidebar>
     
    )
}



Install react icons

npm i react-icons



MainNav.jsx


import { NavLink } from "react-router-dom";
import styled from "styled-components";
import { HiOutlineCalendarDays, HiOutlineCog6Tooth, HiOutlineHome, HiOutlineHomeModern } from "react-icons/hi2"
import { HiOutlineUser } from "react-icons/hi";

const NavList = styled.ul`
  display: flex;
  flex-direction: column;
  gap: 0.8rem;
`;

const StyledNavLink = styled(NavLink)`
  &:link,
  &:visited {
    display: flex;
    align-items: center;
    gap: 1.2rem;

    color: var(--color-grey-600);
    font-size: 1.6rem;
    font-weight: 500;
    padding: 1.2rem 2.4rem;
    transition: all 0.3s;
  }

  /* This works because react-router places the active class on the active NavLink */
  &:hover,
  &:active,
  &.active:link,
  &.active:visited {
    color: var(--color-grey-800);
    background-color: var(--color-grey-50);
    border-radius: var(--border-radius-sm);
  }

  & svg {
    width: 2.4rem;
    height: 2.4rem;
    color: var(--color-grey-400);
    transition: all 0.3s;
  }

  &:hover svg,
  &:active svg,
  &.active:link svg,
  &.active:visited svg {
    color: var(--color-brand-600);
  }
`;


export default function MainNav(){
  return (
    <nav>
    <NavList>
      <li>
        <StyledNavLink to="/dashboard"><HiOutlineHome /><span>Home</span></StyledNavLink>
      </li>
      <li>
        <StyledNavLink to="/bookings"><HiOutlineCalendarDays /><span>Bookings</span> </StyledNavLink>
      </li>
       <li>
        <StyledNavLink to="/cabins"><HiOutlineHomeModern /><span>Cabins</span> </StyledNavLink>
      </li>
      <li>
        <StyledNavLink to="/users"><HiOutlineUser /><span>Users</span> </StyledNavLink>
      </li>
       <li>
        <StyledNavLink to="/settings"><HiOutlineCog6Tooth /><span>Settings</span> </StyledNavLink>
      </li>
    </NavList>
    </nav>
)
}













React Query

React query manages remote state (state saved in server and need to load the application. React query is a data fetching library. All remote state in React query is cached which eans fetched data will be stored inorder to be reused in different points of the application. 
For example if we fetch data about cabin A in component A, react query will fetch data from API, then will store the received data in cache so component A can use it. But if component B want to fetch cabin data then no additional API request will be necessary, that is react query will given the same data to component B from cache. The advantage of React Query is it wastes a bit less data to be downloaded, once data in the cache all other components like component B can receive it instantly (without showing spinner this leads to fast experience for users). React query gives all loading and error states. React query automatically re fetches to keep state synched in certain situations like after certain timeout, after leave browser window and then come back to it (this ensures remote state always remains synched with the application). For example other component updates the cabin data then application running on all other computers will have cabin state synched with the newly updated state. Pre-fetching to fetch data that is necessary later but before actually displayed on the screen (example of pre-fetching is pagination where data in current page as well as next page is made available as it is available in the cache).

npm i @tanstack/react-query@4

React query first step is to place data basically lives, second provide to the application. 
In App.js

import { QueryClient } from "@tanstack/react-query";
import { ReactQueryDevtools } from "@tanstack/react-query-devtools";
const queryClient = new  QueryClient(
{
defaultOptions: {
 queries : {
staleTime: 60 *1000
  }
}
});

export default function App(){
return (
 <QueryClientProvider client={queryClient}>
 <ReactQueryDevtools initialIsOpen= {false} />
  <Header/>
  <Main />
  <Footer />
 </QueryClientProvider>
)
}


'staleTime' is the amount of time that data in the cache will stay fresh so that it will stay valid until re-fetched again. 'staleTime: 60 *1000' here 60 denotes seconds and 1000 milliseconds. Then 'QueryClientProvider' component on as the parent tag in 'App.js' and provide with 'client'.
React query has dev tools which can be installed by the following command :-

npm i @tanstack/react-query-devtools



If you want to use React Query v5, there are only two small things to change in the project:

isLoading is now called isPending

The cacheTime option is now called gcTime



React Query - useQuery

In React Querywe use 'useQuery' custom hook. In 'useQuery' we pass an object (in the object we pass 2 arguments, first argument is 'queryKey' (to uniquely identify the query here, the value in 'queryKey' is a complex array or an array with strings, here in the below example 'cabin' is to uniquely identifies each data (when we use 'useQuery' in another page with same 'queryKey' say 'cabin' then data will be read from the cache ) ) and second argument is the query function 'queryFn' ( query function is responsible for querying, basically fetching data from API ) 

import getCabins from '../../services/apiCabins'; //api not created for fetching data


const { isLoading, data: cabins, error} = useQuery({
  queryKey : ["cabin"],
  queryFn: getCabins
})


CabinTable.jsx



import { useQuery } from "@tanstack/react-query";
import styled from "styled-components";
import getCabins from '../../services/apiCabins'; //api not created for fetching data
import Spinner from '../../ui/Spinner';
import CabinRow from "./CabinRow";


const Table = styled.div`
  border: 1px solid var(--color-grey-200);

  font-size: 1.4rem;
  background-color: var(--color-grey-0);
  border-radius: 7px;
  overflow: hidden;
`;

const TableHeader = styled.header`
  display: grid;
  grid-template-columns: 0.6fr 1.8fr 2.2fr 1fr 1fr 1fr;
  column-gap: 2.4rem;
  align-items: center;

  background-color: var(--color-grey-50);
  border-bottom: 1px solid var(--color-grey-100);
  text-transform: uppercase;
  letter-spacing: 0.4px;
  font-weight: 600;
  color: var(--color-grey-600);
  padding: 1.6rem 2.4rem;
`;

export default function CabinTable(){
const { isLoading, data: cabins, error} = useQuery({
  queryKey : ["cabin"],
  queryFn: getCabins
})

if(isLoading) return <Spinner />

  return(
  <Table role="table">
    <TableHeader role="row">
      <div></div>
      <div>Cabin</div>
      <div>Capacity</div>
      <div>Price</div>
      <div>Discount</div>
    </TableHeader>
    {cabins.map(cabin => <CabinRow cabin={cabin} key={cabin.id} />)}
  </Table>
  )
}






npm i date-fns

this is to install date functions.


CabinRow.jsx


import styled from "styled-components";
import {formatCurrency} from "../../utils/helpers"


const TableRow = styled.div`
  display: grid;
  grid-template-columns: 0.6fr 1.8fr 2.2fr 1fr 1fr 1fr;
  column-gap: 2.4rem;
  align-items: center;
  padding: 1.4rem 2.4rem;

  &:not(:last-child) {
    border-bottom: 1px solid var(--color-grey-100);
  }
`;

const Img = styled.img`
  display: block;
  width: 6.4rem;
  aspect-ratio: 3 / 2;
  object-fit: cover;
  object-position: center;
  transform: scale(1.5) translateX(-7px);
`;

const Cabin = styled.div`
  font-size: 1.6rem;
  font-weight: 600;
  color: var(--color-grey-600);
  font-family: "Sono";
`;

const Price = styled.div`
  font-family: "Sono";
  font-weight: 600;
`;

const Discount = styled.div`
  font-family: "Sono";
  font-weight: 500;
  color: var(--color-green-700);
`;

export default function CabinRow({cabin}){
const {id, name, maxCapacity, regularPrice, discount, image} = cabin;

  return (
    <TableRow role="row">
     <Img src="image" />
     <Cabin>{name}</Cabin>
     <div>
      Fits upto {maxCapacity} guests
     </div>
     <Price>{formatCurrency(regularPrice)}</Price>
     <Discount>{formatCurrency(discount)}</Discount>
     <button>Delete</button>
    </TableRow>
  )
}


If we go to another page where other than API data is fetched and displayed move away from this component which will be then unmounted. So, the 'querKey' which is 'cabin' where cabin data is inactive and again the Api data displayed need not have to fetch new fetch request. So, the same data again without any new fetch request hence even the spinner comes since we have the data from before as the data comes from stored cache. 
When we move away from the browser and come back later that will trigger a re-fetch as soon as data is stale.
When some user of the application changes something and so all the applications running on other browsers will come out of sync, so React Query will prevent from automatically re fetching the data.
When we change data within stale time completes then the React Query doesn't fetches it waits until data is stale. But if 'staleTime' (provided in App.jsx) is exceeded then refecthing of data happens as data was changed.




Mutations using React Query 


Deleting a cabin 

Mutation can be done using 'useMutation', in 'useMutation' we pass an object, the first argument in 'useMutation' is 'mutationFn' ('mutationFn' is the function that React Query will call ), second argument is 'onSuccess' (callback which tell React Query what to do as soon as mutation was successful). 'queryClient' in App.jsx can be accessible by a hook 'useQueryClient'


useMutation is used for actions that modify data, such as:

Creating data (POST)

Updating data (PUT / PATCH)

Deleting data (DELETE)

Submitting forms

Triggering side-effect operations (e.g., sending emails, payments)



queryClient.invalidateQueries({ queryKey: ['todos'] })
An invalidated query:

Is marked as stale

Will refetch the next time it’s used (or immediately if active)

Keeps its cached data until the refetch completes


const { isLoading : isDeleting, mutate } = useMutation({
  mutationFn: (id) => deleteCabin(id), onSuccess: () =>{
    queryClient.invalidateQueries({
      queryKey: ["cabin"],

    })
  },
  onError: err => alert(err.message)
})




CabinRow.jsx


import styled from "styled-components";
import {formatCurrency} from "../../utils/helpers"
import { useMutation, useQueryClient } from "@tanstack/react-query";
import deleteCabin from '../../services/apiCabins'

const TableRow = styled.div`
  display: grid;
  grid-template-columns: 0.6fr 1.8fr 2.2fr 1fr 1fr 1fr;
  column-gap: 2.4rem;
  align-items: center;
  padding: 1.4rem 2.4rem;

  &:not(:last-child) {
    border-bottom: 1px solid var(--color-grey-100);
  }
`;

const Img = styled.img`
  display: block;
  width: 6.4rem;
  aspect-ratio: 3 / 2;
  object-fit: cover;
  object-position: center;
  transform: scale(1.5) translateX(-7px);
`;

const Cabin = styled.div`
  font-size: 1.6rem;
  font-weight: 600;
  color: var(--color-grey-600);
  font-family: "Sono";
`;

const Price = styled.div`
  font-family: "Sono";
  font-weight: 600;
`;

const Discount = styled.div`
  font-family: "Sono";
  font-weight: 500;
  color: var(--color-green-700);
`;

export default function CabinRow({cabin}){
const {id: cabinId, name, maxCapacity, regularPrice, discount, image} = cabin;

const queryClient = useQueryClient();

const { isLoading : isDeleting, mutate } = useMutation({
  mutationFn: (id) => deleteCabin(id), onSuccess: () =>{
    queryClient.invalidateQueries({
      queryKey: ["cabin"],

    })
  },
  onError: err => alert(err.message)
})


  return (
    <TableRow role="row">
     <Img src="image" />
     <Cabin>{name}</Cabin>
     <div>
      Fits upto {maxCapacity} guests
     </div>
     <Price>{formatCurrency(regularPrice)}</Price>
     <Discount>{formatCurrency(discount)}</Discount>
     <button onClick={()=> mutate(cabinId)} disabled={isDeleting}>Delete</button>
    </TableRow>
  )
}



In CabinRow.jsx we add mutate() function in 'Delete' button.


const {id: cabinId, name, maxCapacity, regularPrice, discount, image} = cabin;
 <button onClick={()=> mutate(cabinId)} disabled={isLoading}>Delete</button>


The 'mutate()' will call 'mutationFn' which will indeed call 'deleteCabin(id)'.





Toast Notifications

npm i react-hot-toast

component is called '<Toaster>'


<Toaster position="top-center" gutter={12} />

'gutter' space between the window and toaster. Position at top center.
'containerStyle' specify an object of styles. In 'toastOptions' we have 'success' property with 'duration' to how long success toast will stay in the screen. 



    <Toaster position="top-center" gutter={12} containerStyle={{margin: "8px"}} toastOptions={{success: {
      duration: 3000
    },
    error: {
      duration: 5000
    },
    style:{
      fontSize: '16px',
      maxWidth: '500px',
      padding: '16px 24px',
      backgroundColor: "var(--color-grey-0)",
      color: "var(--color-grey-700)"
    }
    }}/>




App.jsx


import styled from "styled-components";
import GlobalStyles from "./styles/GlobalStyles";
import AppLayout from './ui/AppLayout'
import { BrowserRouter, Routes, Route, Navigate } from "react-router-dom";
import Dashboard from './pages/Dashboard'
import Bookings from './pages/Bookings';
import Cabins from './pages/Cabins';
import Users from './pages/Users';
import Settings from './pages/Settings';
import Account from './pages/Account';
import Login from './pages/Login';
import PageNotFound from './pages/PageNotFound';
import { QueryClient } from "@tanstack/react-query";
import { Toaster } from "react-hot-toast";

const queryClient = new  QueryClient(
{
defaultOptions: {
 queries : {
staleTime: 60 *1000
  }
}
});

function App() {
  return (
    <>
    <QueryClientProvider client={queryClient}>
    <GlobalStyles />
    <BrowserRouter>
    <Routes>
      <Route element={<AppLayout />}>
      <Route index element={<Navigate replace to="dashboard" />} />
      <Route path="dashboard" element={<Dashboard />} />
      <Route path="bookings" element={<Bookings />} />
      <Route path="cabins" element={<Cabins />} />
      <Route path="users" element={<Users />} />
      <Route path="settings" element={<Settings />} />
      <Route path="account" element={<Account />} />
      </Route>
      <Route path="login" element={<Login />} />
      <Route path="*" element={<PageNotFound />} />
    </Routes>
    </BrowserRouter>
    <Toaster position="top-center" gutter={12} containerStyle={{margin: "8px"}} toastOptions={{success: {
      duration: 3000
    },
    error: {
      duration: 5000
    },
    style:{
      fontSize: '16px',
      maxWidth: '500px',
      padding: '16px 24px',
      backgroundColor: "var(--color-grey-0)",
      color: "var(--color-grey-700)"
    }
    }}/>
    </QueryClientProvider>
    </>
    
  )
}

export default App



CabinRow.jsx


import styled from "styled-components";
import {formatCurrency} from "../../utils/helpers"
import { useMutation, useQueryClient } from "@tanstack/react-query";
import deleteCabin from '../../services/apiCabins'
import toast from "react-hot-toast";

const TableRow = styled.div`
  display: grid;
  grid-template-columns: 0.6fr 1.8fr 2.2fr 1fr 1fr 1fr;
  column-gap: 2.4rem;
  align-items: center;
  padding: 1.4rem 2.4rem;

  &:not(:last-child) {
    border-bottom: 1px solid var(--color-grey-100);
  }
`;

const Img = styled.img`
  display: block;
  width: 6.4rem;
  aspect-ratio: 3 / 2;
  object-fit: cover;
  object-position: center;
  transform: scale(1.5) translateX(-7px);
`;

const Cabin = styled.div`
  font-size: 1.6rem;
  font-weight: 600;
  color: var(--color-grey-600);
  font-family: "Sono";
`;

const Price = styled.div`
  font-family: "Sono";
  font-weight: 600;
`;

const Discount = styled.div`
  font-family: "Sono";
  font-weight: 500;
  color: var(--color-green-700);
`;

export default function CabinRow({cabin}){
const {id: cabinId, name, maxCapacity, regularPrice, discount, image} = cabin;

const queryClient = useQueryClient();

const { isLoading : isDeleting, mutate } = useMutation({
  mutationFn: (id) => deleteCabin(id), onSuccess: () =>{
    toast.success("cabins successfully deleted")
    queryClient.invalidateQueries({
      queryKey: ["cabin"],

    })
  },
  onError: err => toast.error(err.message)
})


  return (
    <TableRow role="row">
     <Img src="image" />
     <Cabin>{name}</Cabin>
     <div>
      Fits upto {maxCapacity} guests
     </div>
     <Price>{formatCurrency(regularPrice)}</Price>
     <Discount>{formatCurrency(discount)}</Discount>
     <button onClick={()=> mutate(cabinId)} disabled={isDeleting}>Delete</button>
    </TableRow>
  )
}





CabinTable.jsx


import { useQuery } from "@tanstack/react-query";
import styled from "styled-components";
import getCabins from '../../services/apiCabins'; //api not created for fetching data
import Spinner from '../../ui/Spinner';
import CabinRow from "./CabinRow";


const Table = styled.div`
  border: 1px solid var(--color-grey-200);

  font-size: 1.4rem;
  background-color: var(--color-grey-0);
  border-radius: 7px;
  overflow: hidden;
`;

const TableHeader = styled.header`
  display: grid;
  grid-template-columns: 0.6fr 1.8fr 2.2fr 1fr 1fr 1fr;
  column-gap: 2.4rem;
  align-items: center;

  background-color: var(--color-grey-50);
  border-bottom: 1px solid var(--color-grey-100);
  text-transform: uppercase;
  letter-spacing: 0.4px;
  font-weight: 600;
  color: var(--color-grey-600);
  padding: 1.6rem 2.4rem;
`;

export default function CabinTable(){
const { isLoading, data: cabins, error} = useQuery({
  queryKey : ["cabin"],
  queryFn: getCabins
})

if(isLoading) return <Spinner />

  return(
  <Table role="table">
    <TableHeader role="row">
      <div></div>
      <div>Cabin</div>
      <div>Capacity</div>
      <div>Price</div>
      <div>Discount</div>
    </TableHeader>
    {cabins.map(cabin => <CabinRow cabin={cabin} key={cabin.id} />)}
  </Table>
  )
}



AppLayout.jsx


import { Outlet } from "react-router-dom";
import Header from "./Header";
import Sidebar from "./Sidebar";
import styled from "styled-components";
import { QueryClient, QueryClientProvider } from '@tanstack/react-query';

const queryClient = new  QueryClient(
{
defaultOptions: {
 queries : {
staleTime: 60 *1000
  }
}
});
const StyledAppLayout = styled.div`
    display: grid;
    grid-template-columns: 26rem 1fr;
    grid-template-rows: auto 1fr;
    height: 100vh;
`

const Main = styled.main`
    background-color: var(--color-grey-50);
    padding: 4rem 4.8rem 6.4rem;
`

const Container = styled.div`
  max-width: 120rem;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 3.2rem;
`

export default function AppLayout(){
    return (
        <QueryClientProvider client={queryClient}>
          <StyledAppLayout>
            <Header />
            <Sidebar />
            <Main>
              <Container>
                <Outlet />
              </Container>
            </Main>
        </StyledAppLayout>
         </QueryClientProvider>
    )
}






React Hook Form

React Hook Form handles form submission and form errors.

npm i react-hook-form@7



 const { register, handleSubmit } = useForm();

'register' is to register the inputs into this hook. So into the for using useForm() hook.

And 'register' is called using {...register("name")} where 'name' is the id in the iput tag of html. (as below). This is registering inputs to the form.


 <FormRow>
        <Label htmlFor="name">Cabin name</Label>
        <Input type="text" id="name" {...register("name")} />
   </FormRow>


Then we call 'onSubmit' by passing 'handleSubmit' using  'useForm' and inside 'handleSubmit' we pass the function which is to be called when the form is submitted.


<Form onSubmit={handleSubmit(submitForm)}>


function submitForm(data){

  }


'data' consists of all inputs being registered in the form using 'handleSubmit' in 'useForm' hook.









CreateCabinForm.jsx


import styled from "styled-components";

import Input from "../../ui/Input";
import Form from "../../ui/Form";
import Button from "../../ui/Button";
import FileInput from "../../ui/FileInput";
import Textarea from "../../ui/Textarea";
import { useForm, useMutation } from "react-hook-form";
import createCabin from '../../services/apiCabins';
import { useQueryClient } from "@tanstack/react-query";
import toast from "react-hot-toast";

const FormRow = styled.div`
  display: grid;
  align-items: center;
  grid-template-columns: 24rem 1fr 1.2fr;
  gap: 2.4rem;

  padding: 1.2rem 0;

  &:first-child {
    padding-top: 0;
  }

  &:last-child {
    padding-bottom: 0;
  }

  &:not(:last-child) {
    border-bottom: 1px solid var(--color-grey-100);
  }

  &:has(button) {
    display: flex;
    justify-content: flex-end;
    gap: 1.2rem;
  }
`;

const Label = styled.label`
  font-weight: 500;
`;

const Error = styled.span`
  font-size: 1.4rem;
  color: var(--color-red-700);
`;

function CreateCabinForm() {
const { register, handleSubmit, reset} = useForm();
const queryClient = useQueryClient();

const {mutate, isLoading: isCreating} = useMutation({
 mutationFn: createCabin,
 onSuccess: () =>{
  toast.success("new cabin successfully created");
  queryClient.invalidateQueries({queryKey: ['cabin']});
  reset();
 },
 onError: (err) => toast.error(err.message)
})



  function submitForm(data){
   mutate(data)
  }
  return (
    <Form onSubmit={handleSubmit(submitForm)}>
      <FormRow>
        <Label htmlFor="name">Cabin name</Label>
        <Input type="text" id="name" {...register("name")} />
      </FormRow>

      <FormRow>
        <Label htmlFor="maxCapacity">Maximum capacity</Label>
        <Input type="number" id="maxCapacity" {...register("maxCapacity")} />
      </FormRow>

      <FormRow>
        <Label htmlFor="regularPrice">Regular price</Label>
        <Input type="number" id="regularPrice" {...register("regularPrice")} />
      </FormRow>

      <FormRow>
        <Label htmlFor="discount">Discount</Label>
        <Input type="number" id="discount" defaultValue={0} {...register("discount")}  />
      </FormRow>

      <FormRow>
        <Label htmlFor="description">Description for website</Label>
        <Textarea type="number" id="description" defaultValue="" {...register("description")} />
      </FormRow>

      <FormRow>
        <Label htmlFor="image">Cabin photo</Label>
        <FileInput id="image" accept="image/*" />
      </FormRow>

      <FormRow>
        {/* type is an HTML attribute! */}
        <Button variation="secondary" type="reset">
          Cancel
        </Button>
        <Button disabled={isCreating}>Add cabin</Button>
      </FormRow>
    </Form>
  );
}

export default CreateCabinForm;




In CreateCabinForm.jsx for the name field we add validation to the name field by passing as an argument with 'required' key and the message when the field isn't entered.


{...register("name"), {
          required: "This field is required"
        }}



'handleSubmit' is called each time when we submit the form. And that point each validators are called and hence 'required' (which we give in register) is checked for each fields in the form. If there is errors in any validation in the form then 'handleSubmit' will not call the 'submitForm' function but instead will call the second function we pass in 'handleSubmit' (say function 'onError' here)


onSubmit={handleSubmit(submitForm, onError)}



and the minimum value can be set along with a message when data fails (here minimum value is 1, with a validation message) in register

eg:-

 {...register("maxCapacity"), {
          required: "This field is required",
          min:{
            value: 1,
            message: "Capacity should be at least 1"
          }
        }}




The 'discount' field need to be less than regularPrice, for that we can write custom validation using ('validate' key in register and in 'validate' we pass a callback function and the argument passed in callback function we get the current value and this current value is currently being input in the field . The logic written in 'validate' callback function when return true then the field is validated), 'getValues' in 'useForm' we get the form values ( eg getValues().regularPrice ).


{...register("discount"), {
          required: "This field is required",
          validate: (value) => value <= getValues().regularPrice || "Discount should be less then regular price"
        }}



We get 'formState' from 'useForm' and from 'formState' we gets errors in the form.

const { register, handleSubmit, reset, getValues, formState} = useForm();
const { errors } = formState;


And pass the error message ' {errors?.name?.message && <p style={{color:red}}>{errors.name.message}</p>}'

<FormRow>
        <Label htmlFor="name">Cabin name</Label>
        <Input type="text" id="name" {...register("name"), {
          required: "This field is required"
        }} />
         <Error>{errors.name.message}</Error>
      </FormRow>





CreateCabinForm.jsx


import styled from "styled-components";

import Input from "../../ui/Input";
import Form from "../../ui/Form";
import Button from "../../ui/Button";
import FileInput from "../../ui/FileInput";
import Textarea from "../../ui/Textarea";
import { useForm, useMutation } from "react-hook-form";
import createCabin from '../../services/apiCabins';
import { useQueryClient } from "@tanstack/react-query";
import toast from "react-hot-toast";

const FormRow = styled.div`
  display: grid;
  align-items: center;
  grid-template-columns: 24rem 1fr 1.2fr;
  gap: 2.4rem;

  padding: 1.2rem 0;

  &:first-child {
    padding-top: 0;
  }

  &:last-child {
    padding-bottom: 0;
  }

  &:not(:last-child) {
    border-bottom: 1px solid var(--color-grey-100);
  }

  &:has(button) {
    display: flex;
    justify-content: flex-end;
    gap: 1.2rem;
  }
`;

const Label = styled.label`
  font-weight: 500;
`;

const Error = styled.span`
  font-size: 1.4rem;
  color: var(--color-red-700);
`;

function CreateCabinForm() {
const { register, handleSubmit, reset, getValues, formState} = useForm();
const { errors } = formState;
const queryClient = useQueryClient();

const {mutate, isLoading: isCreating} = useMutation({
 mutationFn: createCabin,
 onSuccess: () =>{
  toast.success("new cabin successfully created");
  queryClient.invalidateQueries({queryKey: ['cabin']});
  reset();
 },
 onError: (err) => toast.error(err.message)
})



  function submitForm(data){
   mutate(data)
  }

function onError(errors){

}

  return (
    <Form onSubmit={handleSubmit(submitForm, onError)}>
      <FormRow>
        <Label htmlFor="name">Cabin name</Label>
        <Input type="text" id="name" {...register("name"), {
          required: "This field is required"
        }} />
        {errors?.name?.message && <Error>{errors.name.message}</Error>}
      </FormRow>

      <FormRow>
        <Label htmlFor="maxCapacity">Maximum capacity</Label>
        <Input type="number" id="maxCapacity" {...register("maxCapacity"), {
          required: "This field is required",
          min:{
            value: 1,
            message: "Capacity should be at least 1"
          }
        }} />
      </FormRow>

      <FormRow>
        <Label htmlFor="regularPrice">Regular price</Label>
        <Input type="number" id="regularPrice" {...register("regularPrice"), {
          required: "This field is required",
          min:{
            value: 1,
            message: "Capacity should be at least 1"
          }
        }} />
      </FormRow>

      <FormRow>
        <Label htmlFor="discount">Discount</Label>
        <Input type="number" id="discount" defaultValue={0} {...register("discount"), {
          required: "This field is required",
          validate: (value) => value <= getValues().regularPrice || "Discount should be less then regular price"
        }}  />
      </FormRow>

      <FormRow>
        <Label htmlFor="description">Description for website</Label>
        <Textarea type="number" id="description" defaultValue="" {...register("description"), {
          required: "This field is required"
        }} />
      </FormRow>

      <FormRow>
        <Label htmlFor="image">Cabin photo</Label>
        <FileInput id="image" accept="image/*" />
      </FormRow>

      <FormRow>
        {/* type is an HTML attribute! */}
        <Button variation="secondary" type="reset">
          Cancel
        </Button>
        <Button disabled={isCreating}>Add cabin</Button>
      </FormRow>
    </Form>
  );
}

export default CreateCabinForm;



Create 'FormRow.jsx' in 'ui' folder. And restructuring 'CreateCabinForm.jsx' like shown below



FormRow.jsx


import styled from "styled-components";

const StyledFormRow = styled.div`
  display: grid;
  align-items: center;
  grid-template-columns: 24rem 1fr 1.2fr;
  gap: 2.4rem;

  padding: 1.2rem 0;

  &:first-child {
    padding-top: 0;
  }

  &:last-child {
    padding-bottom: 0;
  }

  &:not(:last-child) {
    border-bottom: 1px solid var(--color-grey-100);
  }

  &:has(button) {
    display: flex;
    justify-content: flex-end;
    gap: 1.2rem;
  }
`;

const Label = styled.label`
  font-weight: 500;
`;

const Error = styled.span`
  font-size: 1.4rem;
  color: var(--color-red-700);
`;


export default function FormRow({label, error, children}){
    return (
         <StyledFormRow>
        { label && <Label htmlFor={children.props.id}>{label}</Label> }
        {children}
        {error && <Error>{error}</Error>}
      </StyledFormRow>
    )
}



CreateCabinForm.jsx


import styled from "styled-components";

import Input from "../../ui/Input";
import Form from "../../ui/Form";
import Button from "../../ui/Button";
import FileInput from "../../ui/FileInput";
import Textarea from "../../ui/Textarea";
import { useForm, useMutation } from "react-hook-form";
import createCabin from '../../services/apiCabins';
import { useQueryClient } from "@tanstack/react-query";
import toast from "react-hot-toast";
import FormRow from '../../ui/FormRow'

const StyledFormRow = styled.div`
  display: grid;
  align-items: center;
  grid-template-columns: 24rem 1fr 1.2fr;
  gap: 2.4rem;

  padding: 1.2rem 0;

  &:first-child {
    padding-top: 0;
  }

  &:last-child {
    padding-bottom: 0;
  }

  &:not(:last-child) {
    border-bottom: 1px solid var(--color-grey-100);
  }

  &:has(button) {
    display: flex;
    justify-content: flex-end;
    gap: 1.2rem;
  }
`;

const Label = styled.label`
  font-weight: 500;
`;

const Error = styled.span`
  font-size: 1.4rem;
  color: var(--color-red-700);
`;

function CreateCabinForm() {
const { register, handleSubmit, reset, getValues, formState} = useForm();
const { errors } = formState;
const queryClient = useQueryClient();

const {mutate, isLoading: isCreating} = useMutation({
 mutationFn: createCabin,
 onSuccess: () =>{
  toast.success("new cabin successfully created");
  queryClient.invalidateQueries({queryKey: ['cabin']});
  reset();
 },
 onError: (err) => toast.error(err.message)
})



  function submitForm(data){
   mutate(data)
  }

function onError(errors){

}

  return (
    <Form onSubmit={handleSubmit(submitForm, onError)}>
      <FormRow label="Cabin name" error={errors?.name?.message}>
        <Input type="text" id="name" {...register("name"), {
          required: "This field is required"
        }} />
      </FormRow>

      <FormRow label="Maximum capacity" error={errors?.maxCapacity?.message}>
        <Input type="number" id="maxCapacity" {...register("maxCapacity"), {
          required: "This field is required",
          min:{
            value: 1,
            message: "Capacity should be at least 1"
          }
        }} />
      </FormRow>

      <FormRow label="Regular price" error={errors?.regularPrice?.message}>
        <Input type="number" id="regularPrice" {...register("regularPrice"), {
          required: "This field is required",
          min:{
            value: 1,
            message: "Capacity should be at least 1"
          }
        }} />
      </FormRow>

      <FormRow label="Discount" error={errors?.discount?.message}>
        <Input type="number" id="discount" defaultValue={0} {...register("discount"), {
          required: "This field is required",
          validate: (value) => value <= getValues().regularPrice || "Discount should be less then regular price"
        }}  />
      </FormRow>

      <FormRow label="Description for website" error={errors?.description?.message}>
        <Textarea type="number" id="description" defaultValue="" {...register("description"), {
          required: "This field is required"
        }} />
      </FormRow>

      <FormRow label="Cabin photo">
        <Label htmlFor="image">Cabin photo</Label>
        <FileInput id="image" accept="image/*" />
      </FormRow>

      <FormRow>
        {/* type is an HTML attribute! */}
        <Button variation="secondary" type="reset">
          Cancel
        </Button>
        <Button disabled={isCreating}>Add cabin</Button>
      </FormRow>
    </Form>
  );
}

export default CreateCabinForm;






CreateCabinForm.jsx


import styled from "styled-components";

import Input from "../../ui/Input";
import Form from "../../ui/Form";
import Button from "../../ui/Button";
import FileInput from "../../ui/FileInput";
import Textarea from "../../ui/Textarea";
import { useForm, useMutation } from "react-hook-form";
import createCabin from '../../services/apiCabins';
import { useQueryClient } from "@tanstack/react-query";
import toast from "react-hot-toast";

const FormRow = styled.div`
  display: grid;
  align-items: center;
  grid-template-columns: 24rem 1fr 1.2fr;
  gap: 2.4rem;

  padding: 1.2rem 0;

  &:first-child {
    padding-top: 0;
  }

  &:last-child {
    padding-bottom: 0;
  }

  &:not(:last-child) {
    border-bottom: 1px solid var(--color-grey-100);
  }

  &:has(button) {
    display: flex;
    justify-content: flex-end;
    gap: 1.2rem;
  }
`;

const Label = styled.label`
  font-weight: 500;
`;

const Error = styled.span`
  font-size: 1.4rem;
  color: var(--color-red-700);
`;

function CreateCabinForm() {
const { register, handleSubmit, reset} = useForm();
const queryClient = useQueryClient();

const {mutate, isLoading: isCreating} = useMutation({
 mutationFn: createCabin,
 onSuccess: () =>{
  toast.success("new cabin successfully created");
  queryClient.invalidateQueries({queryKey: ['cabin']});
  reset();
 },
 onError: (err) => toast.error(err.message)
})



  function submitForm(data){
   mutate(data)
  }
  return (
    <Form onSubmit={handleSubmit(submitForm)}>
      <FormRow>
        <Label htmlFor="name">Cabin name</Label>
        <Input type="text" id="name" {...register("name")} />
      </FormRow>

      <FormRow>
        <Label htmlFor="maxCapacity">Maximum capacity</Label>
        <Input type="number" id="maxCapacity" {...register("maxCapacity")} />
      </FormRow>

      <FormRow>
        <Label htmlFor="regularPrice">Regular price</Label>
        <Input type="number" id="regularPrice" {...register("regularPrice")} />
      </FormRow>

      <FormRow>
        <Label htmlFor="discount">Discount</Label>
        <Input type="number" id="discount" defaultValue={0} {...register("discount")}  />
      </FormRow>

      <FormRow>
        <Label htmlFor="description">Description for website</Label>
        <Textarea type="number" id="description" defaultValue="" {...register("description")} />
      </FormRow>

      <FormRow>
        <Label htmlFor="image">Cabin photo</Label>
        <FileInput id="image" accept="image/*" />
      </FormRow>

      <FormRow>
        {/* type is an HTML attribute! */}
        <Button variation="secondary" type="reset">
          Cancel
        </Button>
        <Button disabled={isCreating}>Add cabin</Button>
      </FormRow>
    </Form>
  );
}

export default CreateCabinForm;




In CreateCabinForm.jsx for the name field we add validation to the name field by passing as an argument with 'required' key and the message when the field isn't entered.


{...register("name"), {
          required: "This field is required"
        }}



'handleSubmit' is called each time when we submit the form. And that point each validators are called and hence 'required' (which we give in register) is checked for each fields in the form. If there is errors in any validation in the form then 'handleSubmit' will not call the 'submitForm' function but instead will call the second function we pass in 'handleSubmit' (say function 'onError' here)


onSubmit={handleSubmit(submitForm, onError)}



and the minimum value can be set along with a message when data fails (here minimum value is 1, with a validation message) in register

eg:-

 {...register("maxCapacity"), {
          required: "This field is required",
          min:{
            value: 1,
            message: "Capacity should be at least 1"
          }
        }}




The 'discount' field need to be less than regularPrice, for that we can write custom validation using ('validate' key in register and in 'validate' we pass a callback function and the argument passed in callback function we get the current value and this current value is currently being input in the field . The logic written in 'validate' callback function when return true then the field is validated), 'getValues' in 'useForm' we get the form values ( eg getValues().regularPrice ).


{...register("discount"), {
          required: "This field is required",
          validate: (value) => value <= getValues().regularPrice || "Discount should be less then regular price"
        }}



We get 'formState' from 'useForm' and from 'formState' we gets errors in the form.

const { register, handleSubmit, reset, getValues, formState} = useForm();
const { errors } = formState;


And pass the error message ' {errors?.name?.message && <p style={{color:red}}>{errors.name.message}</p>}'

<FormRow>
        <Label htmlFor="name">Cabin name</Label>
        <Input type="text" id="name" {...register("name"), {
          required: "This field is required"
        }} />
         <Error>{errors.name.message}</Error>
      </FormRow>





CreateCabinForm.jsx


import styled from "styled-components";

import Input from "../../ui/Input";
import Form from "../../ui/Form";
import Button from "../../ui/Button";
import FileInput from "../../ui/FileInput";
import Textarea from "../../ui/Textarea";
import { useForm, useMutation } from "react-hook-form";
import createCabin from '../../services/apiCabins';
import { useQueryClient } from "@tanstack/react-query";
import toast from "react-hot-toast";

const FormRow = styled.div`
  display: grid;
  align-items: center;
  grid-template-columns: 24rem 1fr 1.2fr;
  gap: 2.4rem;

  padding: 1.2rem 0;

  &:first-child {
    padding-top: 0;
  }

  &:last-child {
    padding-bottom: 0;
  }

  &:not(:last-child) {
    border-bottom: 1px solid var(--color-grey-100);
  }

  &:has(button) {
    display: flex;
    justify-content: flex-end;
    gap: 1.2rem;
  }
`;

const Label = styled.label`
  font-weight: 500;
`;

const Error = styled.span`
  font-size: 1.4rem;
  color: var(--color-red-700);
`;

function CreateCabinForm() {
const { register, handleSubmit, reset, getValues, formState} = useForm();
const { errors } = formState;
const queryClient = useQueryClient();

const {mutate, isLoading: isCreating} = useMutation({
 mutationFn: createCabin,
 onSuccess: () =>{
  toast.success("new cabin successfully created");
  queryClient.invalidateQueries({queryKey: ['cabin']});
  reset();
 },
 onError: (err) => toast.error(err.message)
})



  function submitForm(data){
   mutate(data)
  }

function onError(errors){

}

  return (
    <Form onSubmit={handleSubmit(submitForm, onError)}>
      <FormRow>
        <Label htmlFor="name">Cabin name</Label>
        <Input type="text" id="name" {...register("name"), {
          required: "This field is required"
        }} />
        {errors?.name?.message && <Error>{errors.name.message}</Error>}
      </FormRow>

      <FormRow>
        <Label htmlFor="maxCapacity">Maximum capacity</Label>
        <Input type="number" id="maxCapacity" {...register("maxCapacity"), {
          required: "This field is required",
          min:{
            value: 1,
            message: "Capacity should be at least 1"
          }
        }} />
      </FormRow>

      <FormRow>
        <Label htmlFor="regularPrice">Regular price</Label>
        <Input type="number" id="regularPrice" {...register("regularPrice"), {
          required: "This field is required",
          min:{
            value: 1,
            message: "Capacity should be at least 1"
          }
        }} />
      </FormRow>

      <FormRow>
        <Label htmlFor="discount">Discount</Label>
        <Input type="number" id="discount" defaultValue={0} {...register("discount"), {
          required: "This field is required",
          validate: (value) => value <= getValues().regularPrice || "Discount should be less then regular price"
        }}  />
      </FormRow>

      <FormRow>
        <Label htmlFor="description">Description for website</Label>
        <Textarea type="number" id="description" defaultValue="" {...register("description"), {
          required: "This field is required"
        }} />
      </FormRow>

      <FormRow>
        <Label htmlFor="image">Cabin photo</Label>
        <FileInput id="image" accept="image/*" />
      </FormRow>

      <FormRow>
        {/* type is an HTML attribute! */}
        <Button variation="secondary" type="reset">
          Cancel
        </Button>
        <Button disabled={isCreating}>Add cabin</Button>
      </FormRow>
    </Form>
  );
}

export default CreateCabinForm;



Create 'FormRow.jsx' in 'ui' folder. And restructuring 'CreateCabinForm.jsx' like shown below



FormRow.jsx


import styled from "styled-components";

const StyledFormRow = styled.div`
  display: grid;
  align-items: center;
  grid-template-columns: 24rem 1fr 1.2fr;
  gap: 2.4rem;

  padding: 1.2rem 0;

  &:first-child {
    padding-top: 0;
  }

  &:last-child {
    padding-bottom: 0;
  }

  &:not(:last-child) {
    border-bottom: 1px solid var(--color-grey-100);
  }

  &:has(button) {
    display: flex;
    justify-content: flex-end;
    gap: 1.2rem;
  }
`;

const Label = styled.label`
  font-weight: 500;
`;

const Error = styled.span`
  font-size: 1.4rem;
  color: var(--color-red-700);
`;


export default function FormRow({label, error, children}){
    return (
         <StyledFormRow>
        { label && <Label htmlFor={children.props.id}>{label}</Label> }
        {children}
        {error && <Error>{error}</Error>}
      </StyledFormRow>
    )
}



CreateCabinForm.jsx


import styled from "styled-components";

import Input from "../../ui/Input";
import Form from "../../ui/Form";
import Button from "../../ui/Button";
import FileInput from "../../ui/FileInput";
import Textarea from "../../ui/Textarea";
import { useForm, useMutation } from "react-hook-form";
import createCabin from '../../services/apiCabins';
import { useQueryClient } from "@tanstack/react-query";
import toast from "react-hot-toast";
import FormRow from '../../ui/FormRow'

const StyledFormRow = styled.div`
  display: grid;
  align-items: center;
  grid-template-columns: 24rem 1fr 1.2fr;
  gap: 2.4rem;

  padding: 1.2rem 0;

  &:first-child {
    padding-top: 0;
  }

  &:last-child {
    padding-bottom: 0;
  }

  &:not(:last-child) {
    border-bottom: 1px solid var(--color-grey-100);
  }

  &:has(button) {
    display: flex;
    justify-content: flex-end;
    gap: 1.2rem;
  }
`;

const Label = styled.label`
  font-weight: 500;
`;

const Error = styled.span`
  font-size: 1.4rem;
  color: var(--color-red-700);
`;

function CreateCabinForm() {
const { register, handleSubmit, reset, getValues, formState} = useForm();
const { errors } = formState;
const queryClient = useQueryClient();

const {mutate, isLoading: isCreating} = useMutation({
 mutationFn: createCabin,
 onSuccess: () =>{
  toast.success("new cabin successfully created");
  queryClient.invalidateQueries({queryKey: ['cabin']});
  reset();
 },
 onError: (err) => toast.error(err.message)
})



  function submitForm(data){
   mutate(data)
  }

function onError(errors){

}

  return (
    <Form onSubmit={handleSubmit(submitForm, onError)}>
      <FormRow label="Cabin name" error={errors?.name?.message}>
        <Input type="text" id="name" {...register("name"), {
          required: "This field is required"
        }} />
      </FormRow>

      <FormRow label="Maximum capacity" error={errors?.maxCapacity?.message}>
        <Input type="number" id="maxCapacity" {...register("maxCapacity"), {
          required: "This field is required",
          min:{
            value: 1,
            message: "Capacity should be at least 1"
          }
        }} />
      </FormRow>

      <FormRow label="Regular price" error={errors?.regularPrice?.message}>
        <Input type="number" id="regularPrice" {...register("regularPrice"), {
          required: "This field is required",
          min:{
            value: 1,
            message: "Capacity should be at least 1"
          }
        }} />
      </FormRow>

      <FormRow label="Discount" error={errors?.discount?.message}>
        <Input type="number" id="discount" defaultValue={0} {...register("discount"), {
          required: "This field is required",
          validate: (value) => value <= getValues().regularPrice || "Discount should be less then regular price"
        }}  />
      </FormRow>

      <FormRow label="Description for website" error={errors?.description?.message}>
        <Textarea type="number" id="description" defaultValue="" {...register("description"), {
          required: "This field is required"
        }} />
      </FormRow>

      <FormRow label="Cabin photo">
        <Label htmlFor="image">Cabin photo</Label>
        <FileInput id="image" accept="image/*" />
      </FormRow>

      <FormRow>
        {/* type is an HTML attribute! */}
        <Button variation="secondary" type="reset">
          Cancel
        </Button>
        <Button disabled={isCreating}>Add cabin</Button>
      </FormRow>
    </Form>
  );
}

export default CreateCabinForm;




Part 2
