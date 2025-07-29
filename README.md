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
