# Инвариантная самостоятельная работа

### [4.1. Разработать программу для считывания данных JSON-формата из файла и вывод их в табличном виде на экран. Организовать тестирование работоспособности программы с помощью assert, print.](https://replit.com/@PolinaLazebniko/sem3-Tema4-ISR-41)
```python
"""
    Лазебникова Полина 
    ИВТ 2 курс
    группа 1.3-

    Инвариантная самостоятельная работа 
    4.1. Разработать программу для считывания данных JSON-формата из файла и вывод их в табличном виде на экран. 
    Организовать тестирование работоспособности программы с помощью assert, print.
"""

import json

def json_table(data):

  table = []
  sstr = '| {id:^3} | {first_name:^10} | {last_name:^15} | {email:^30} | {gender:^6} | {ip_address:^16} |'
  t_caption = '| {:^3} | {:^10} | {:^15} | {:^30} | {:^6} | {:^16} |'.format('id','first_name','last_name','email','gender','ip_address')
  roof = '-'*len(t_caption)
  
  table.append(roof)  
  table.append(t_caption)
  table.append(roof)  

  for el in range(len(data)):
      temp = data[el]
      res = sstr.format(**temp)
      table.append(res)
  table.append(roof)
  return(table)

def test_func(func,arg):
  """
  Тест функции json_table
  """
  try:
    assert type(func(arg)) is tuple
  except:
    print('Тест на тип не пройден', type(func(arg)))
  try:
    assert len(func(arg)) == 100
  except:
    print('Количество строк не соответствует -',len(func(arg)))

def main():
  with open('data.json') as f:
    data_dict = json.load(f)

  test_func(json_table,data_dict)
  
  t = json_table(data_dict)
  for el in t:
    print(el)
  
main()
```
### [4.2. Дополнение программы задания 4.1 (считывание данных JSON-формата) тестами с использованием библиотеки doctest.](https://replit.com/@PolinaLazebniko/sem3-Tema4-ISR-42#main.py)
```python

```
### [4.3. Дополнение программы задания 4.1,4.2 (считывание данных JSONформата) тестами с использованием пакета py.test.](https://replit.com/@PolinaLazebniko/sem3-Tema4-ISR-43#main.py)
```python

```
