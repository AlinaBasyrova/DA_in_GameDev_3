# DA_in_GameDev_3

Отчет по лабораторной работе #3 выполнил(а):
- Басырова Алина Радмировна
- РИ220942
  
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Структура отчета

- Данные о работе: название работы, фио, группа, выполненные задания.
- Цель работы.
- Задание 1.
- Задание 2.
- Задание 3.
- Выводы.

## Цель работы
разработать баланс для десяти уровней игры Dragon Picker

Ход работы:

## Задание 1
### Предложите вариант изменения найденных переменных для 10 уровней в игре. Визуализируйте изменение уровня сложности в таблице.
Среди переменных, влияющих на сложность игры были выделены:
- Speed - скорость передвижения дракона
- Time Between Egg Drops - время между повявлением яиц
- Left Right Distance - дистанция между левой и правой границей
- Chance Direction - шанс того, что дракон изменит свое направление

![image](https://github.com/AlinaBasyrova/DA_in_GameDev_3/assets/129521982/cb137e0d-0ae7-4d75-83d5-ec8d9d36a4d8)

Для повышения сложности игры я буду увеличивать скорость, шанс смены направления, дистанцию и уменьшать время между появлением яиц. Таким образом формула итоговой сложности может принять вид:
difficult = speed + distance + chance + 1/egg_time

Стартовые значения и коэффициент изменения
- Speed - 1; 1.5
- Time Between Egg Drops - 5; 0.8
- Left Right Distance - 10; 1.08
- Chance Direction - 0.001; 1.5

![image](https://github.com/AlinaBasyrova/DA_in_GameDev_3/assets/129521982/1db5e9af-13b9-47f1-80c7-231c9e96063e)



## Задание 2
### Создайте 10 сцен на Unity с изменяющимся уровнем сложности.

## Задание 3
### Решение в 80+ баллов должно заполнять google-таблицу данными из Python. В Python данные также должны быть визуализированы.

```py
import gspread
import matplotlib.pyplot as plt
import numpy as np

speed = 1
egg_time = 5
distance = 10
chance = 0.001
lvl_count = 10
difficult = []
gc = gspread.service_account(filename='da-in-gamedev-2-404609-c13383911b0b.json')
sh = gc.open("DA_3")

sh.sheet1.update(('A1'), "№ Уровня")
sh.sheet1.update(('B1'), "Speed")
sh.sheet1.update(('C1'), "Time Between Egg Drops")
sh.sheet1.update(('D1'), "Left Right Distance")
sh.sheet1.update(('E1'), "Chance Direction")
sh.sheet1.update(('F1'), "Difficulty")


for i in range(1, 11):
    difficult.append(round(speed + distance + chance + 1/egg_time, 3))
    sh.sheet1.update(('A' + str(i+1)), i)
    sh.sheet1.update(('B' + str(i+1)), speed)
    sh.sheet1.update(('C' + str(i+1)), egg_time)
    sh.sheet1.update(('D' + str(i+1)), distance)
    sh.sheet1.update(('E' + str(i+1)), chance)
    sh.sheet1.update(('F' + str(i+1)), difficult[i-1])
    speed = round(speed * 1.5, 3)
    egg_time = round(egg_time * 0.8, 3)
    distance = round(distance * 1.08, 3)
    chance = round(chance * 1.5, 3)
    
fig, ax = plt.subplots()
x = np.arange(1, 11)
y = np.array(difficult)
ax.plot(x, y)
ax.grid()
plt.xticks(range(1, 11, 1), range(1, 11, 1))
plt.yticks(range(1, 35, 2), range(1, 35, 2))
plt.xlabel("№ Уровня")
plt.ylabel("Сложность")
plt.show()

print('Done')
```


## Выводы

- В ходе данной лабораторной работы я познакомилась с Unity, Jupyter Notebook, Anaconda и VS Code. Вывела строку "Hello World" с использованием языков Python и C# в таких средах, как Jupyter Notebook и Unity.

| Plugin | README |
| ------ | ------ |
| GitHub | [plugins/github/README.md][PlGh] |
| VS Code | [plugins/vscode/README.md][PlGh] |
| Unity | [plugins/unity/README.md][PlMe] |
| Jupiter Notebook | [plugins/jupiternotebook/README.md][PlGa] |

## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**
