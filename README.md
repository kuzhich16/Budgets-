<!DOCTYPE html>
<html lang="uk">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Фінансовий Трекер ₴</title>

  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Manrope:wght@400;500;600;700&family=Unbounded:wght@400;500;700&display=swap" rel="stylesheet">

  <style>
    :root{
      --bg:#0f1115;
      --card:#1a1d24;
      --card2:#20242d;
      --text:#f5f5f5;
      --muted:#9aa3b2;
      --accent:#f5c842;
      --danger:#ff5c5c;
      --success:#4ade80;
      --warning:#facc15;
      --border:#2d3340;
      --shadow:0 10px 30px rgba(0,0,0,.35);
    }

    *{
      margin:0;
      padding:0;
      box-sizing:border-box;
    }

    body{
      font-family:'Manrope',sans-serif;
      background:linear-gradient(180deg,#0c0e12,#12151c);
      color:var(--text);
      min-height:100vh;
      padding:20px;
    }

    h1,h2,h3,h4{
      font-family:'Unbounded',sans-serif;
    }

    .container{
      max-width:1400px;
      margin:auto;
    }

    .header{
      display:flex;
      justify-content:space-between;
      align-items:center;
      flex-wrap:wrap;
      gap:15px;
      margin-bottom:25px;
    }

    .title{
      font-size:28px;
      color:var(--accent);
    }

    .subtitle{
      color:var(--muted);
      margin-top:8px;
    }

    .tabs{
      display:flex;
      gap:10px;
      flex-wrap:wrap;
      margin-bottom:25px;
    }

    .tab-btn{
      background:var(--card);
      border:1px solid var(--border);
      color:var(--text);
      padding:12px 18px;
      border-radius:14px;
      cursor:pointer;
      transition:.25s;
      font-weight:700;
    }

    .tab-btn:hover{
      transform:translateY(-2px);
      border-color:var(--accent);
    }

    .tab-btn.active{
      background:var(--accent);
      color:#000;
    }

    .tab-content{
      display:none;
      animation:fade .35s ease;
    }

    .tab-content.active{
      display:block;
    }

    @keyframes fade{
      from{
        opacity:0;
        transform:translateY(10px);
      }
      to{
        opacity:1;
        transform:translateY(0);
      }
    }

    .grid{
      display:grid;
      grid-template-columns:repeat(auto-fit,minmax(280px,1fr));
      gap:18px;
      margin-bottom:20px;
    }

    .card{
      background:linear-gradient(180deg,var(--card),var(--card2));
      border:1px solid var(--border);
      border-radius:22px;
      padding:20px;
      box-shadow:var(--shadow);
    }

    .card h3{
      margin-bottom:18px;
      font-size:18px;
      color:var(--accent);
    }

    label{
      display:block;
      margin-bottom:8px;
      color:var(--muted);
      font-size:14px;
    }

    input,select,textarea{
      width:100%;
      background:#11141a;
      border:1px solid var(--border);
      color:var(--text);
      padding:12px;
      border-radius:12px;
      margin-bottom:14px;
      outline:none;
      transition:.2s;
      font-family:'Manrope',sans-serif;
    }

    input:focus,
    select:focus,
    textarea:focus{
      border-color:var(--accent);
    }

    button{
      border:none;
      cursor:pointer;
      transition:.25s;
      font-family:'Manrope',sans-serif;
      font-weight:700;
    }

    .primary-btn{
      background:var(--accent);
      color:#000;
      width:100%;
      padding:13px;
      border-radius:12px;
    }

    .primary-btn:hover{
      transform:translateY(-2px);
    }

    .summary{
      display:grid;
      grid-template-columns:repeat(auto-fit,minmax(220px,1fr));
      gap:16px;
      margin-bottom:20px;
    }

    .summary-box{
      background:var(--card);
      border:1px solid var(--border);
      border-radius:20px;
      padding:20px;
    }

    .summary-box p{
      color:var(--muted);
      margin-bottom:8px;
    }

    .summary-box h2{
      font-size:28px;
    }

    .income{
      color:var(--success);
    }

    .expense{
      color:var(--danger);
    }

    .balance{
      color:var(--accent);
    }

    .list{
      display:flex;
      flex-direction:column;
      gap:12px;
    }

    .item{
      background:#141821;
      border:1px solid var(--border);
      border-radius:16px;
      padding:16px;
      display:flex;
      justify-content:space-between;
      gap:15px;
      align-items:flex-start;
      flex-wrap:wrap;
    }

    .item-title{
      font-weight:700;
      margin-bottom:6px;
    }

    .item-sub{
      color:var(--muted);
      font-size:14px;
    }

    .delete-btn{
      background:rgba(255,92,92,.15);
      color:var(--danger);
      padding:10px 14px;
      border-radius:10px;
    }

    .delete-btn:hover{
      background:rgba(255,92,92,.25);
    }

    .progress-wrap{
      margin-bottom:18px;
    }

    .progress-head{
      display:flex;
      justify-content:space-between;
      margin-bottom:8px;
    }

    .progress{
      width:100%;
      height:16px;
      background:#11151c;
      border-radius:999px;
      overflow:hidden;
    }

    .progress-bar{
      height:100%;
      background:linear-gradient(90deg,var(--accent),#ffd96d);
      border-radius:999px;
      transition:.4s;
    }

    .rule-grid{
      display:grid;
      grid-template-columns:repeat(auto-fit,minmax(220px,1fr));
      gap:16px;
      margin-top:20px;
    }

    .rule-box{
      background:#151922;
      border:1px solid var(--border);
      border-radius:16px;
      padding:18px;
    }

    .rule-box h4{
      margin-bottom:12px;
      color:var(--accent);
    }

    .status{
      margin-top:20px;
      padding:16px;
      border-radius:16px;
      font-weight:700;
    }

    .critical{
      background:rgba(255,92,92,.12);
      border:1px solid rgba(255,92,92,.4);
      color:var(--danger);
    }

    .moderate{
      background:rgba(250,204,21,.12);
      border:1px solid rgba(250,204,21,.4);
      color:var(--warning);
    }

    .good{
      background:rgba(74,222,128,.12);
      border:1px solid rgba(74,222,128,.4);
      color:var(--success);
    }

    .badge{
      display:inline-block;
      padding:8px 12px;
      border-radius:999px;
      background:rgba(245,200,66,.15);
      color:var(--accent);
      margin-top:10px;
      font-size:14px;
      font-weight:700;
    }

    .empty{
      text-align:center;
      color:var(--muted);
      padding:30px;
    }

    @media(max-width:768px){
      body{
        padding:14px;
      }

      .title{
        font-size:22px;
      }

      .summary-box h2{
        font-size:22px;
      }

      .item{
        flex-direction:column;
      }
    }
  </style>
</head>
<body>

<div class="container">

  <div class="header">
    <div>
      <h1 class="title">💰 Особистий Фінансовий Трекер ₴</h1>
      <p class="subtitle">Контроль бюджету, боргів та фінансового плану</p>
    </div>
  </div>

  <div class="tabs">
    <button class="tab-btn active" data-tab="budget">💰 Бюджет</button>
    <button class="tab-btn" data-tab="debts">📋 Борги</button>
    <button class="tab-btn" data-tab="analysis">📊 Аналіз</button>
    <button class="tab-btn" data-tab="plan">🎯 План</button>
  </div>

  <!-- БЮДЖЕТ -->
  <div class="tab-content active" id="budget">

    <div class="grid">
      <div class="card">
        <h3>➕ Додати транзакцію</h3>

        <label>Тип</label>
        <select id="type">
          <option value="income">Дохід</option>
          <option value="expense">Витрата</option>
        </select>

        <label>Категорія</label>
        <input type="text" id="category" placeholder="Наприклад: Їжа">

        <label>Сума ₴</label>
        <input type="number" id="amount" placeholder="0">

        <label>Дата</label>
        <input type="date" id="date">

        <label>Нотатка</label>
        <textarea id="note" rows="3" placeholder="Додаткова інформація"></textarea>

        <button class="primary-btn" onclick="addTransaction()">Зберегти</button>
      </div>

      <div class="card">
        <h3>📅 Фільтр по місяцях</h3>

        <label>Місяць</label>
        <input type="month" id="monthFilter">

        <button class="primary-btn" onclick="renderTransactions()">Застосувати</button>
      </div>
    </div>

    <div class="summary">
      <div class="summary-box">
        <p>Доходи</p>
        <h2 class="income" id="incomeTotal">₴0</h2>
      </div>

      <div class="summary-box">
        <p>Витрати</p>
        <h2 class="expense" id="expenseTotal">₴0</h2>
      </div>

      <div class="summary-box">
        <p>Баланс</p>
        <h2 class="balance" id="balanceTotal">₴0</h2>
      </div>
    </div>

    <div class="card">
      <h3>📜 Транзакції</h3>
      <div class="list" id="transactionList"></div>
    </div>

  </div>

  <!-- БОРГИ -->
  <div class="tab-content" id="debts">

    <div class="grid">
      <div class="card">
        <h3>➕ Додати борг</h3>

        <label>Кому винні</label>
        <input type="text" id="debtName">

        <label>Сума ₴</label>
        <input type="number" id="debtAmount">

        <label>% ставка</label>
        <input type="number" id="debtRate">

        <label>Мінімальний платіж ₴</label>
        <input type="number" id="debtMin">

        <button class="primary-btn" onclick="addDebt()">Зберегти борг</button>
      </div>

      <div class="card">
        <h3>❄️ Метод сніжного кому</h3>

        <div id="snowballAdvice"></div>
      </div>
    </div>

    <div class="summary">
      <div class="summary-box">
        <p>Загальна сума боргів</p>
        <h2 class="expense" id="debtTotal">₴0</h2>
      </div>
    </div>

    <div class="card">
      <h3>📋 Список боргів</h3>
      <div class="list" id="debtList"></div>
    </div>

  </div>

  <!-- АНАЛІЗ -->
  <div class="tab-content" id="analysis">

    <div class="card">
      <h3>📊 Витрати по категоріях</h3>
      <div id="categoryAnalysis"></div>
    </div>

    <div class="card" style="margin-top:20px;">
      <h3>📐 Правило 50 / 30 / 20</h3>
      <div class="rule-grid">
        <div class="rule-box">
          <h4>50% Потреби</h4>
          <p id="needsValue">₴0</p>
        </div>

        <div class="rule-box">
          <h4>30% Бажання</h4>
          <p id="wantsValue">₴0</p>
        </div>

        <div class="rule-box">
          <h4>20% Заощадження</h4>
          <p id="saveValue">₴0</p>
        </div>
      </div>
    </div>

  </div>

  <!-- ПЛАН -->
  <div class="tab-content" id="plan">

    <div class="card">
      <h3>🎯 Розумний фінансовий план</h3>

      <div id="planContent"></div>

      <div id="statusBox"></div>
    </div>

  </div>

</div>

<script>

  // ---------------- STORAGE ----------------

  let transactions = JSON.parse(localStorage.getItem('transactions')) || [];
  let debts = JSON.parse(localStorage.getItem('debts')) || [];

  function saveData(){
    localStorage.setItem('transactions', JSON.stringify(transactions));
    localStorage.setItem('debts', JSON.stringify(debts));
  }

  // ---------------- TABS ----------------

  const tabs = document.querySelectorAll('.tab-btn');
  const contents = document.querySelectorAll('.tab-content');

  tabs.forEach(btn=>{
    btn.addEventListener('click',()=>{

      tabs.forEach(b=>b.classList.remove('active'));
      contents.forEach(c=>c.classList.remove('active'));

      btn.classList.add('active');
      document.getElementById(btn.dataset.tab).classList.add('active');

      renderAll();
    });
  });

  // ---------------- HELPERS ----------------

  function formatUAH(value){
    return `₴${Number(value).toLocaleString('uk-UA')}`;
  }

  function today(){
    return new Date().toISOString().split('T')[0];
  }

  document.getElementById('date').value = today();

  // ---------------- TRANSACTIONS ----------------

  function addTransaction(){

    const type = document.getElementById('type').value;
    const category = document.getElementById('category').value.trim();
    const amount = Number(document.getElementById('amount').value);
    const date = document.getElementById('date').value;
    const note = document.getElementById('note').value.trim();

    if(!category || !amount || !date){
      alert('Заповніть всі поля');
      return;
    }

    transactions.push({
      id:Date.now(),
      type,
      category,
      amount,
      date,
      note
    });

    saveData();

    document.getElementById('category').value='';
    document.getElementById('amount').value='';
    document.getElementById('note').value='';

    renderAll();
  }

  function deleteTransaction(id){
    transactions = transactions.filter(t=>t.id !== id);
    saveData();
    renderAll();
  }

  function getFilteredTransactions(){

    const month = document.getElementById('monthFilter').value;

    if(!month) return transactions;

    return transactions.filter(t=>t.date.startsWith(month));
  }

  function renderTransactions(){

    const list = document.getElementById('transactionList');
    const data = getFilteredTransactions();

    list.innerHTML='';

    if(data.length===0){
      list.innerHTML='<div class="empty">Транзакцій немає</div>';
    }

    data.sort((a,b)=>new Date(b.date)-new Date(a.date));

    data.forEach(t=>{

      const div = document.createElement('div');
      div.className='item';

      div.innerHTML=`
        <div>
          <div class="item-title">
            ${t.type === 'income' ? '💵' : '💸'} ${t.category}
          </div>

          <div class="item-sub">
            ${t.date} ${t.note ? '• '+t.note : ''}
          </div>
        </div>

        <div style="display:flex; gap:10px; align-items:center;">
          <strong style="color:${t.type==='income' ? '#4ade80' : '#ff5c5c'}">
            ${t.type==='income' ? '+' : '-'}${formatUAH(t.amount)}
          </strong>

          <button class="delete-btn" onclick="deleteTransaction(${t.id})">
            Видалити
          </button>
        </div>
      `;

      list.appendChild(div);
    });

    updateSummary();
  }

  function updateSummary(){

    const data = getFilteredTransactions();

    const income = data
      .filter(t=>t.type==='income')
      .reduce((a,b)=>a+b.amount,0);

    const expense = data
      .filter(t=>t.type==='expense')
      .reduce((a,b)=>a+b.amount,0);

    const balance = income-expense;

    document.getElementById('incomeTotal').innerText=formatUAH(income);
    document.getElementById('expenseTotal').innerText=formatUAH(expense);
    document.getElementById('balanceTotal').innerText=formatUAH(balance);
  }

  // ---------------- DEBTS ----------------

  function addDebt(){

    const name = document.getElementById('debtName').value.trim();
    const amount = Number(document.getElementById('debtAmount').value);
    const rate = Number(document.getElementById('debtRate').value);
    const min = Number(document.getElementById('debtMin').value);

    if(!name || !amount){
      alert('Заповніть поля');
      return;
    }

    debts.push({
      id:Date.now(),
      name,
      amount,
      rate,
      min
    });

    saveData();

    document.getElementById('debtName').value='';
    document.getElementById('debtAmount').value='';
    document.getElementById('debtRate').value='';
    document.getElementById('debtMin').value='';

    renderAll();
  }

  function deleteDebt(id){
    debts = debts.filter(d=>d.id!==id);
    saveData();
    renderAll();
  }

  function renderDebts(){

    const list = document.getElementById('debtList');
    const total = debts.reduce((a,b)=>a+b.amount,0);

    document.getElementById('debtTotal').innerText=formatUAH(total);

    list.innerHTML='';

    if(debts.length===0){
      list.innerHTML='<div class="empty">Боргів немає 🎉</div>';
    }

    const sorted = [...debts].sort((a,b)=>a.amount-b.amount);

    sorted.forEach(d=>{

      const div = document.createElement('div');
      div.className='item';

      div.innerHTML=`
        <div>
          <div class="item-title">🏦 ${d.name}</div>
          <div class="item-sub">
            Ставка: ${d.rate || 0}% • Мін. платіж: ${formatUAH(d.min || 0)}
          </div>
        </div>

        <div style="display:flex; gap:10px; align-items:center;">
          <strong class="expense">${formatUAH(d.amount)}</strong>

          <button class="delete-btn" onclick="deleteDebt(${d.id})">
            Видалити
          </button>
        </div>
      `;

      list.appendChild(div);
    });

    const advice = document.getElementById('snowballAdvice');

    if(sorted.length){

      advice.innerHTML=`
        <p>
          Спочатку закривайте:
        </p>

        <div class="badge">
          ${sorted[0].name} — ${formatUAH(sorted[0].amount)}
        </div>

        <p style="margin-top:14px; color:var(--muted);">
          Метод «сніжного кому» рекомендує спочатку погасити найменший борг,
          щоб швидше отримати психологічний прогрес.
        </p>
      `;

    }else{

      advice.innerHTML=`
        <div class="empty">
          Додайте борги для аналізу
        </div>
      `;
    }
  }

  // ---------------- ANALYSIS ----------------

  function renderAnalysis(){

    const expenses = transactions.filter(t=>t.type==='expense');

    const totalExpenses = expenses.reduce((a,b)=>a+b.amount,0);

    const categories = {};

    expenses.forEach(e=>{
      categories[e.category] = (categories[e.category] || 0) + e.amount;
    });

    const box = document.getElementById('categoryAnalysis');
    box.innerHTML='';

    if(totalExpenses===0){
      box.innerHTML='<div class="empty">Немає витрат для аналізу</div>';
    }

    Object.entries(categories).forEach(([cat,val])=>{

      const percent = ((val/totalExpenses)*100).toFixed(1);

      box.innerHTML += `
        <div class="progress-wrap">

          <div class="progress-head">
            <span>${cat}</span>
            <span>${formatUAH(val)} (${percent}%)</span>
          </div>

          <div class="progress">
            <div class="progress-bar" style="width:${percent}%"></div>
          </div>

        </div>
      `;
    });

    const income = transactions
      .filter(t=>t.type==='income')
      .reduce((a,b)=>a+b.amount,0);

    document.getElementById('needsValue').innerText =
      formatUAH(income*0.5);

    document.getElementById('wantsValue').innerText =
      formatUAH(income*0.3);

    document.getElementById('saveValue').innerText =
      formatUAH(income*0.2);
  }

  // ---------------- PLAN ----------------

  function renderPlan(){

    const income = transactions
      .filter(t=>t.type==='income')
      .reduce((a,b)=>a+b.amount,0);

    const expenses = transactions
      .filter(t=>t.type==='expense')
      .reduce((a,b)=>a+b.amount,0);

    const debtTotal = debts
      .reduce((a,b)=>a+b.amount,0);

    const remain = income-expenses;

    let debtPercent = 0;
    let strategy = '';

    if(debtTotal===0){
      strategy = 'Класичне правило 50/30/20';
    }else if(debtTotal > income*6){
      debtPercent = 35;
      strategy = 'Агресивне погашення боргів';
    }else if(debtTotal > income*2){
      debtPercent = 25;
      strategy = 'Помірне погашення боргів';
    }else{
      debtPercent = 15;
      strategy = 'Легке погашення боргів';
    }

    const debtPay = income*(debtPercent/100);

    const save = income*0.2;
    const needs = income*0.5;
    const wants = income*0.3;

    const box = document.getElementById('planContent');

    box.innerHTML=`
      <div class="rule-grid">

        <div class="rule-box">
          <h4>💵 Місячний дохід</h4>
          <p>${formatUAH(income)}</p>
        </div>

        <div class="rule-box">
          <h4>💸 Місячні витрати</h4>
          <p>${formatUAH(expenses)}</p>
        </div>

        <div class="rule-box">
          <h4>🏦 Борги</h4>
          <p>${formatUAH(debtTotal)}</p>
        </div>

      </div>

      <div style="margin-top:24px;">
        <h3 style="margin-bottom:14px;">📌 Рекомендації</h3>

        <div class="list">

          ${
            debtTotal===0
            ?
            `
            <div class="item">
              <div>
                <div class="item-title">Правило 50 / 30 / 20</div>
                <div class="item-sub">
                  Потреби: ${formatUAH(needs)} •
                  Бажання: ${formatUAH(wants)} •
                  Заощадження: ${formatUAH(save)}
                </div>
              </div>
            </div>
            `
            :
            `
            <div class="item">
              <div>
                <div class="item-title">${strategy}</div>
                <div class="item-sub">
                  Рекомендується направляти
                  <strong>${debtPercent}%</strong> доходу на борги:
                  <strong>${formatUAH(debtPay)}</strong>
                </div>
              </div>
            </div>
            `
          }

          <div class="item">
            <div>
              <div class="item-title">💰 Залишок після витрат</div>
              <div class="item-sub">
                ${formatUAH(remain)}
              </div>
            </div>
          </div>

        </div>
      </div>
    `;

    const statusBox = document.getElementById('statusBox');

    let statusClass='good';
    let statusText='Фінансовий стан добрий ✅';

    if(remain < 0){
      statusClass='critical';
      statusText='Критично: витрати перевищують дохід 🚨';
    }else if(remain < income*0.15){
      statusClass='moderate';
      statusText='Помірно: залишок занадто малий ⚠️';
    }

    statusBox.innerHTML=`
      <div class="status ${statusClass}">
        ${statusText}
      </div>
    `;
  }

  // ---------------- RENDER ----------------

  function renderAll(){
    renderTransactions();
    renderDebts();
    renderAnalysis();
    renderPlan();
  }

  renderAll();

</script>

</body>
</html>
