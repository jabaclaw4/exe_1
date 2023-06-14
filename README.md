function evaluateExpression(expression) {
  // Реализация функции, выполняющей вычисления для выражения
  // В данном примере просто возвращаем строку с выражением
  return expression;
}

function parseExpression(input) {
  let index = 0;

  function parseUnaryMinus() {
    if (input[index] === "-") {
      index++;
      const expression = parseExpression();
      return "-" + expression;
    }
    return parseNumber();
  }

  function parseNumber() {
    let number = "";
    while (index < input.length && /[0-9.]/.test(input[index])) {
      number += input[index];
      index++;
    }
    return number;
  }

  return parseUnaryMinus();
}

// Пример использования
const inputExpression = "-42";
const result = evaluateExpression(parseExpression(inputExpression));
console.log(result); // Output: -42
