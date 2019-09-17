# Frontend Developer

### 1. Name

Alexey Khegay

---

### 2. Contact Info

Email: [khegay.alexey@mail.ru](mailto:khegay.alexey@mail.ru)
Phone: [+7 (705) 577-88-52](tel:+77055778852)
Telegram: [@nadeocfg](https://t.me/nadeocfg)

---

### 3. Skills

- HTML;
- CSS;
- JS;
- SQL
- SASS, LESS;
- Bootstrap;
- Photoshop, Illustrator, Figma;
- Java (base).

---

### 4. Experience

More than 50 projects, since 2013 year.
Latest:

- [https://z-star.kz/](https://z-star.kz/)
- [http://steam.z-star.kz/](http://steam.z-star.kz/)
- [https://tepliy-dom.webils.kz/](https://tepliy-dom.webils.kz/)
- [http://sauvage.kz/](http://sauvage.kz/)

<details>
 <summary>Code examples</summary>
 <pre>
  // Sidebar fields
  let startBtn = document.getElementById("start"),
    val = document.querySelectorAll("div[class*='value']"),
    reqExpenses = document.querySelectorAll(".expenses-item"),
    timeData = document.querySelectorAll("input[class*='value']");

  // Buttons
  let reqBtn = document.querySelector(".expenses-item-btn"),
    optBtn = document.querySelector(".optionalexpenses-btn"),
    budgetBtn = document.querySelector(".count-budget-btn");

  // data fields
  let optFields = document.querySelectorAll(".optionalexpenses-item"),
    reqFields = document.querySelectorAll(".expenses-item"),
    inc = document.querySelector("#income"),
    savings = document.querySelector("#savings"),
    savingsSum = document.querySelector("#sum"),
    savingsPercent = document.querySelector("#percent");

  let money, time;

  startBtn.addEventListener("click", function () {
    time = prompt("Введите дату в формате YYYY-MM-DD", "1990-07-16");
    money = +prompt("Ваш бюджет на месяц?", "100000");

    while (isNaN(money) || money == "" || money == null) {
      money = +prompt("Ваш бюджет на месяц?", "100000");
    }

    appData.budget = money;
    appData.timeData = time;

    val[0].textContent = money.toFixed();
    timeData[0].value = new Date(Date.parse(time)).getFullYear();
    timeData[1].value = new Date(Date.parse(time)).getMonth() + 1;
    timeData[2].value = new Date(Date.parse(time)).getDate();
  });

  reqBtn.addEventListener("click", function () {
    let sum = 0;

    for (let i = 0; i < reqExpenses.length; i++) {
      let a = reqExpenses[i].value,
        b = reqExpenses[++i].value;

      if (
        typeof a === "string" &&
        typeof a != null &&
        typeof b === "string" &&
        typeof b != null &&
        a != "" &&
        b != "" &&
        a.length < 50
      ) {
        appData.expenses[a] = b;
        sum += +b;
      } else {
        i = i - 1;
      }
    }
    val[3].textContent = sum;
  });

  optBtn.addEventListener("click", function () {
    for (let i = 0; i < optFields.length; i++) {
      let opt = optFields[i].value;
      appData.optionalExpenses[i] = opt;
      val[4].textContent += appData.optionalExpenses[i] + ' ';
    }
  });

  budgetBtn.addEventListener("click", function () {
    if (appData.budget != undefined) {
      appData.moneyPerDay = (appData.budget / 30).toFixed();
      val[1].textContent = appData.moneyPerDay;

      if (appData.moneyPerDay < 100) {
        val[2].textContent = "Минимальный уровень достатка";
      } else if (appData.moneyPerDay > 100 && appData.moneyPerDay < 2000) {
        val[2].textContent = "Средний уровень достатка";
      } else if (appData.moneyPerDay > 2000) {
        val[2].textContent = "Высокий уровень достатка";
      } else {
        val[2].textContent = "Произошла ошибка";
      }
    } else {
      val[1].textContent = "Не нажали кнопку Начать расчет!";
    }
  });

  inc.addEventListener("input", function () {
    let items = inc.value;
    appData.income = items.split(", ");
    val[5].textContent = appData.income;
  });

  savings.addEventListener("click", function () {
    if (appData.savings == true) {
      appData.savings = false;
    } else {
      appData.savings = true;
    }
  });

  savingsSum.addEventListener("input", function () {
    if (appData.savings == true) {
      let sum = +savingsSum.value,
        percent = +savingsPercent.value;

      appData.monthIncome = (sum / 100 / 12) * percent;
      appData.yearIncome = (sum / 100) * percent;

      val[6].textContent = appData.monthIncome.toFixed(1);
      val[7].textContent = appData.yearIncome.toFixed(1);
    }
  });

  savingsPercent.addEventListener("input", function () {
    if (appData.savings == true) {
      let sum = +savingsSum.value,
        percent = +savingsPercent.value;
      appData.monthIncome = (sum / 100 / 12) * percent;
      appData.yearIncome = (sum / 100) * percent;

      val[6].textContent = appData.monthIncome.toFixed(1);
      val[7].textContent = appData.yearIncome.toFixed(1);
    }
  });

  let appData = {
    budget: money,
    expenses: {},
    optionalExpenses: {},
    income: [],
    timeData: time,
    savings: false
  };
 </pre>
</details>

---

### 5. Education

> 2006 - 2010 | Central Asia College of Technology and Economics | Engineer/Programmer

> 2010 - 2013 | Graduate School of Business Almaty Management University | Bachelor's degree of Information Systems and Technologies

---

### 6. English level

Pre-Intermediate (A2)
