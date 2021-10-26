# Solving Problems Step-by-Step

``` javascript
// - Write a node program that takes in an unlimited number of command line arguments, goes through each and prints out the sum of them. If any argument is not a whole number, skip it. Do support negative numbers though. If any argument is not a number, output an error message. We need at least 2 arguments.

// takes in an unlimited number of command line arguments
// Edge case: We need at least 2 arguments.

// const newArgs = process.argv.slice(2).map(num => Number(num));

const args = process.argv.slice(2);

console.log("New Args", newArgs)

if (args.length < 2) {
  console.log('Please input at least 2 command-line arguements');
  process.exit();
}

console.log('args:', args);

const convertToNum = function (numbers) {
  const outputNums = [];

  for (let num of numbers) {
    outputNums.push(Number(num));
  }
  return outputNums;
};

const allIntegers = function (numbers) {
  const outputNums = [];

  for (let num of numbers) {
    if (Number.isInteger(num)) {
      outputNums.push(num);
    }
  }
  return outputNums;
};

const allNumbers = function (numbers) {

  console.log('numbers', numbers)
  for (let num of numbers) {
    if (isNaN(num)) {
      console.log('Please input only numbers');
      // throw new Error ('Please input only numbers')
      process.exit();
    }
  }
  return numbers;
};

// Single responsibility principle
// a function should have a single goal

const sum = function (numbers = []) {
  console.log('numbers:', numbers);

  // for (let i=0; i < numbers.length; i-- ) {
  // numbers[i]
  // }

  // goes through each arguments

  // accumulator
  let total = 0;

  // prints out the sum of them
  for (let num of numbers) {
    // no index value
    // Edge Case: If any argument is not a number, output an error message.

    // const convertedNum = Number(num);

    // Edge Case: If any argument is not a whole number, skip it.
    // isInteger
    // num % 1 === 0 => whole number

    // total = total + num;
    total += num;

    console.log('Num:', num, 'total:', total, typeof num);
  }
  return total;
};

const result = sum(allIntegers(allNumbers(convertToNum(args))));
// console.assert(sum(args) === 10, "it should be 10 with [1,2,3,4,5]")

console.log('result:', result);
```