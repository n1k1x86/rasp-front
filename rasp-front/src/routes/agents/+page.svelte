<div class="card">
  <h1>🖥️ Агенты</h1>
  <table>
    <thead>
      <tr>
        <th>ID</th>
        <th>IP</th>
        <th>Статус</th>
        <th>Последняя активность</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>agent-1</td>
        <td>192.168.0.10</td>
        <td>✅ Активен</td>
        <td>1 мин назад</td>
      </tr>
      <tr>
        <td>agent-2</td>
        <td>192.168.0.11</td>
        <td>❌ Неактивен</td>
        <td>5 часов назад</td>
      </tr>
    </tbody>
  </table>
</div>

<style>
  .card {
    background: var(--card-bg);
    padding: 1rem;
    border-radius: 12px;
  }

  table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 1rem;
  }

  th, td {
    padding: 0.75rem;
    border-bottom: 1px solid var(--fg);
  }

  th {
    text-align: left;
  }
</style>
