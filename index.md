# UchetBudget
<?php
require_once 'config/connect.php';
$budget = mysqli_query($connect, "SELECT * FROM `Объект`");
$budget = mysqli_fetch_all($budget);
?>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta https-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="css/style.css">
    <title>Budget</title>
</head>
<body>
<table>
    <tr>
      <th>id</th>
      <th>Наименование объекта</th>
      <th>Выделенный бюджет, руб.</th>
      <th>Общие затраты бюджета, руб.</th>
      <th>Остаток от выделенного бюджета, руб.</th>
      <th>Дата окончания работ, дней.</th>
      <th>Статус постройки/реставрации объекта</th>
      <th>Комментарии и замечания по ходу выполнения (если требуются)</th>
      <th>&#9998;</th>
    </tr>
    <?php
      foreach($budget as $budgets) {
        ?>
          <tr>
            <td><?= $budgets[0] ?></td>
            <td><?= $budgets[1] ?></td>
            <td><?= $budgets[2] ?></td>
            <td><?= $budgets[3] ?></td> 
            <td><?= $budgets[4] ?></td>
            <td><?= $budgets[5] ?></td> 
            <td><?= $budgets[6] ?></td>
            <td><?= $budgets[7] ?></td>
            <td><a href="update.php?id=<?= $budgets[0] ?>">Обновить</a></td>
          </tr>
        <?php
      }
    ?>
  </table>
  <h2>Добавить новый объект</h2>
  <form action="vendor/create.php" method="post">
    <p>Наименование объекта</p>
    <textarea name="name"></textarea>
    <p>Выделенный бюджет, руб.</p>
    <input type ="number" name= "videl">
    <p>Общие затраты бюджета, руб.</p>
    <input type="number" name="zatr">
    <p>Остаток от выделенного бюджета, руб.</p>
    <input type="number" name="ost">
    <p>Дата окончания работ, дней.</p>
    <input type="number" name="dat">
    <p>Статус постройки/реставрации объекта</p>
    <input type="text" name="stat">
    <p>Комментарии и замечания по ходу выполнения (если требуются)</p>
    <textarea name="text" name="comm"></textarea>
    <button type="submit">Добавить</button>
  </form>
</body>
</html>
