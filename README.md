# Mobile Games
Были исследованы данные опользователях мобильной игры. Рассчитаны продуктовые метрики Retention Rate, ARPU, ARPPU, конверсия в покупку. Проведено A/B тестирование для оценки эффективности акционного предложения в игре, а также предложены продуктовые метрики.

## Используемые библиотеки:
pandas, numpy, seaborn, matplotlib, datetime, pingouin, scipy, statsmodels

## В ходе исследования было сделано следующее:
1. Проведен EDA и очистка данных данных.
2. Написана функция для Retenrion Rate и тепловой карте по Retenrion за определенный период.
3. Расчитаны продуктовые метрики ARPU, ARPPU, конверсия в покупку.
4. Проведено A/B-тестирование на пользователях игры:
   - сформированы гипотезы для проведения A/B-теста;
   - построены qqplot и графики распрделений переменных;
   - проведена проверка выборок на нормальность рапсрделения с помощью теста Харке-Бера и критерия Колмогорова и на гомогенность дисперсий с рпомощью теста Левена ;
   - были проанализиваны и выбран стат. тест для оценки A/B теста;
   - проведено A/B тестирование на тестовой и контрольной группе с помощью Bootstrap;
5. Предложены метрики для оценки тематического события в игре

## Результаты:

1. Была написана функция retention, которая принимает на вход 4 аргумента:
 - auth_path - путь к файлу с данными о времени захода пользователей в игру
 - reg_path - путь к файлу с данными о времени регистрации пользователей в игру
 - start_date - начальная дата исследуемого периода
 - final_date - конечная дата исследуемого периода
и выводит тепловую карту со значениями RR за исследуюемый период по когортам. Тепловая карта по RR за период с 2020-09-01 по 2020-09-20.

![image](https://github.com/azizabobojonova/mobile_games/assets/157654767/10a24df6-df2c-42a3-a851-7d230490d74e)

2. Результат A/B тестирования не показал стат.значимого эффекта от проведения акции. Не было выявлено стат.значимых различий между ARPU, ARPPU, конверсия в покупку в тестовой и контрольной группе.
3. Были предложены следующие метрики для оценки эффективности тематического ивента в игре:
- **DAU, WAU** - сколько игроков приняли участие в событии и начали проходить уровни в день/неделю.
- **Конверсия участников** - какой процент участников завершили все уровни и получили награду. Если показатель слишком низкий, стоил задуматься о сложности уровней игры, также и в обратном случае если слишком большая конверсия может стоит усложнить уровни.
- **Average Session Duration** - средняя длительность сессии каждого игрока во время ивента. Сколько в среднем длится сессия игрока. Если уровни легкие это мотивирует игроков проходить несколько уровней за раз и дольше проводить время в игре. Если же уровни слишком сложные и не получается пройти их за первые попытки это демотивирует игроков.
- **ARPU** - стоит оценить увеличился ли средняя выручка от пользователя во время ивента. Если в игре показывается реклама и есть внутренние покупки, нужно оценить какой доход мы получили от ивента.
- **Retention** - оценить retention по дням, сколько процентов игроков остаются каждый день в игре во время ивента. Помогает оценить насколько игрокам было интересно участвовать, насколько были привлекательны призы во время ивента.
  
Дополнительные метрики при усложененной механике:

- **Среднее количество откатов на уровни** - сколько раз в среднем игроки откатывались на несколько уровней назад перед успешным завершением события.
- **Процент отказов** - какой процент игроков не смогли завершить событие из-за частых откатов на уровни. Поможет оценить сколько процентов игроков мы потеряли во время ивента из-за усложненной механики прохождения.
- **Уровни, которые чаще всего не проходят с первого раза** - поможет оследить есть зи взаимосвязь с потерей игроков с ивента.
- **Уровни, которые игроки чаще всего не проходят несколько раз подряд** - Такие уровни демотивируют игроков, в таком случае важно оценить насколько редкие и уникальные предметы предлагаются игроку для прохождения, чтобы не терять игроков с ивента.
- **Среднее количество откатов, после которого игрок перестаёт проходить ивент** - Плможет оценить после скольких неудачных попытках игроки бросают играть. С точки зрения привлекательности для игроков откаты на несколько уровней может демотивировать. Возможно стоит пересмотреть механику прохождения уровней, возможно откат на один уровень, либо счетчики жизней с таймерами, чтобы меньше игроков отказывались от прохождения ивента.
