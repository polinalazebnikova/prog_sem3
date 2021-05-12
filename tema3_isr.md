# Инвариантная самостоятельная работа

### [3.1. Создание аннотированного списка библиотек для работы с текстом в Python.](https://www.dropbox.com/s/ojfh57iez3i1bc1/%D0%9B%D0%B0%D0%B7%D0%B5%D0%B1%D0%BD%D0%B8%D0%BA%D0%BE%D0%B2%D0%B0%20%D0%9F%D0%BE%D0%BB%D0%B8%D0%BD%D0%B0%20%D0%98%D0%92%D0%A2%201.1%20%D0%98%D0%A1%D0%A0%20%D1%82%D0%B5%D0%BC%D0%B0%206%20%D0%B7%D0%B0%D0%B4%D0%B0%D0%BD%D0%B8%D0%B5%203.1.docx?dl=0)
[Ссылка](https://www.dropbox.com/s/ojfh57iez3i1bc1/%D0%9B%D0%B0%D0%B7%D0%B5%D0%B1%D0%BD%D0%B8%D0%BA%D0%BE%D0%B2%D0%B0%20%D0%9F%D0%BE%D0%BB%D0%B8%D0%BD%D0%B0%20%D0%98%D0%92%D0%A2%201.1%20%D0%98%D0%A1%D0%A0%20%D1%82%D0%B5%D0%BC%D0%B0%206%20%D0%B7%D0%B0%D0%B4%D0%B0%D0%BD%D0%B8%D0%B5%203.1.docx?dl=0)
### [3.2. Разработка сценария с реализацией операции поиска подстроки в тексте. ](https://repl.it/@PolinaLazebniko/Tema6-ISR-Zad32)
```python
"""
    Лазебникова Полина 
    ИВТ 2 курс
    группа 1.1

    Инвариантная самостоятельная работа 
    Задание 3.2: Разработка сценария с реализацией операции поиска подстроки в тексте.
"""

def search_all_str(input_str_f, searchable_str_f): 
    """
    Функция для поиска подстроки 

    Входные данные - строка для поиска, строка, по которой идет поиск

    Сначала ищет первое вхождение подстроки, и далее последующие, если вхождений нет,
    то выводит сообщение об этом
    """
    rec = searchable_str_f.find(input_str_f)
    if rec != -1:
        print('Первое вхождение подстроки: ', rec)
    else:
        print('Нет вхождений подстроки')
    while rec != -1:
        rec = searchable_str_f.find(input_str_f, rec + len(input_str_f), len(searchable_str_f))
        if rec != -1:
            print('Вхождение подстроки: ', rec)
        else:
            print('Больше нет вхождений')

def main():
    """
    Функция, которая принимает от пользователя строку для поиска и строку, по которой идет поиск и 
    вызывает функцию search_all_str  
    """
    input_str = input("Введите строку для поиска: ")
    searchable_str = input("Введите строку, по которой идет поиск: ")    
    search_all_str(input_str, searchable_str)

main()
```
### [3.3. Создание скрипта для считывания данных справочных логов из текстового файла и преобразования их в CSV-формат с последующей записью в новый файл.](https://repl.it/@PolinaLazebniko/Tema6-ISR-Zad33)
```python
"""
    Лазебникова Полина 
    ИВТ 2 курс
    группа 1.1

    Инвариантная самостоятельная работа 
    Задание 3.3: Создание скрипта для считывания данных справочных логов из текстового 
    файла и преобразования их в CSV-формат с последующей записью в новый файл.
"""

import json
import csv

def json_f():
    """
    Функция для работы с json
    """
    handle = open('MOCK_DATA.json')
    lines = json.load(handle)
    return lines

def csv_f(lines):
    """
    Функция для работы с csv
    """
    with open('eggs.csv', 'w', newline='') as csvfile:
        csv_writer = csv.writer(
            csvfile, delimiter=';', quotechar='"',
            quoting=csv.QUOTE_MINIMAL)
        csv_writer.writerow(list(lines[0].keys()))
        for line in lines:
            csv_writer.writerow(list(line.values()))

csv_f(json_f())
```
### [3.4. Реализовать программу шифрующую строку, задаваемую пользователем, с помощью алгоритма шифрования ROT13.](https://replit.com/@PolinaLazebniko/Tema6-ISR-Zad34#main.py)
```python
"""
    Лазебникова Полина 
    ИВТ 2 курс
    группа 1.1

    Инвариантная самостоятельная работа 
    Задание 3.4: Реализовать программу шифрующую строку, задаваемую пользователем, с помощью алгоритма шифрования ROT13.
"""

def rot13(str):
    """
    Функция для шифрования
    """
    new_str = ""
    for letter in str:
        lr = ord(letter)
        if (65 <= lr <= 77) or (97 <= lr <= 109) or (1040 <= lr <= 1055) or (1072 <= lr <= 1087):
           new_str += chr(lr + 13)
        elif (78 <= lr <= 90) or (110 <= lr <= 122) or (1056 <= lr <= 1071) or (1088 <= lr <= 1103):
           new_str += chr(lr - 13)
        else:
            new_str += letter
    print(new_str)

def main():
    user_text = input("Введите строку: ")
    rot13(user_text)

main()
```
