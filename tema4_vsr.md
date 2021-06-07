# Вариативная самостоятельная работа

### [4.1. Создание таблицы со сравнительным анализом библиотек для тестирования.](https://www.dropbox.com/s/vlih2tlz1x8kcde/%D0%A2%D0%B5%D0%BC%D0%B0%204%20%D0%B2%D1%81%D1%80%204.1.docx?dl=0)
[Ссылка](https://www.dropbox.com/s/vlih2tlz1x8kcde/%D0%A2%D0%B5%D0%BC%D0%B0%204%20%D0%B2%D1%81%D1%80%204.1.docx?dl=0)
### [4.4. Написать программу для вычисления факториала натурального числа от 0 до n (где, n — целое, натуральное число, помещающееся в переменную целого числа). Для всех других случаев функция должна поднимать исключение TypeError, ValueError. Протестировать работу этой программы с использованием unittest. Учтите ситуации, для которых должны подниматься исключения.](https://replit.com/@PolinaLazebniko/Tema4-VSR-44#main.py)
```python
"""
    Лазебникова Полина 
    ИВТ 2 курс
    группа 1.1

    Вариативная самостоятельная работа 
    4.4. Написать программу для вычисления факториала натурального числа от 0 до n (где, n — целое, натуральное число, помещающееся в переменную целого числа). Для всех других случаев функция должна поднимать исключение TypeError, ValueError. Протестировать работу этой программы с использованием unittest. 
"""

import re
import unittest

def factorial(n):
    if '.' in str(n):
        raise ValueError("Факториала от дробного числа не существует.")
    elif not re.sub('\.|\-', '', str(n)).isdigit():
        raise TypeError("Аргумент не является числом.")
    elif float(n) < 0:
        raise ValueError("Факториала от отрицательного числа не существует.")
    else:
        n = int(n)
        return 1 if not n else n * factorial(n - 1)

print(f'n! = {factorial(input("Введите число n: "))}')

class TestStringMethods(unittest.TestCase):

    def test_int_vals(self):
        self.assertEqual(factorial(3), 6)
        self.assertEqual(factorial(4), 24)
        self.assertEqual(factorial(6), 720)

    def test_fp_vals(self):
        self.assertRaises(
                          ValueError,
                          factorial(78.5),
                          err='Факториала от дробного числа не существует.'
                         )

    def test_invalid_vals(self):
        pass

if __name__ == '__main__':
    unittest.main()
```
