# Проектная работа #

## Когнитивная система Soar ##

Проект выполнил студент 2 курса.

### Описание когнитивных архитектур ###

Когнитивная архитектура определяет базовую инфраструктуру интеллектуальной системы. 
Следовательно, архитектура включает в себя те аспекты когнитивного агента, которые постоянны во времени и в различных областях применения. Аспекты:
краткосрочная и долгосрочная память, в которых хранится содержимое об убеждениях, целях и знаниях агента;
представление элементов, которые содержатся в этих видах памяти, и их организацию в крупномасштабные ментальные структуры;
функциональные процессы, которые действуют в этих структурах, в том числе механизмы обучения, которые их изменяют.

Исследования когнитивных архитектур важны, потому что они поддерживают главную цель искусственного интеллекта и когнитивной науки: создание и понимание искусственных агентов. Например, все современные робототехнические системы управляются специальным программным обеспечением.

### Soar ###

Soar – одна из таких архитектур. Эта архитектура широко используется исследователями для моделирования различных аспектов поведения человека. Основная цель проекта добиться полного выполнения всех возможностей интеллектуальных агентов. Soar использует правила для определения поведения, такие как условные (if-then). Если не описано точно поведения для конкретной процедуры, то в Soar применяется различные стратегии, например, методы для решения тупика. Когда решение найдено, Soar применяет методику обучения, называемую chunking, позволяющую создать новое правило. Система написана на языке программирования Java. 

Процедурные долгосрочные знания в Soar принимают форму продукционных правил, которые в свою очередь, организованы в терминологии операторов, связанных с пространствами задач. 
Некоторые операторы описывают простые, примитивные действия, которые изменяют внутреннее состояние агента или генерируют примитивные внешние действия, в то время как другие операторы описывают более абстрактные деятельности. 
Soar представляет все долгосрочные знания, эпизодическую и семантическую память. Эпизодическая память хранит историю предыдущих состояний, в то время как семантическая память содержит ранее известные факты. 

Все задачи в Soar сформулированы как попытки достижения поставленных целей. Операторы выполняют основные акты системы, знания используются для динамического определения их выбора и применения. 
Также Soar имеет несколько механизмов обучения для различных видов знаний: разбиение данных на порции и обучение с подкреплением позволяют приобрести процедурные знания, тогда как эпизодическое и семантическое обучение позволяют приобрести соответствующие им виды знаний.

### Архитектура Soar ###

После прочтения и выполнения всех упражнений из Tutorial был подробно разобран механизм работы с системой Soar.

В архитектуре имеются такие важные части системы, как временная, постоянная память, и основные процессы. Постоянная память необходима для хранения правил агента. Временная память - для размещения временных данных (например, результаты вычислений), для хранения некоторых структур, переменных, также для прочтения всей информации с
сенсоров, для просмотра текущего состояния. Важно отметить, что временная память представлена в виде графа. Все переменные и структуры в памяти глобальны. Основные процессы архитектуры — это создание состояний, принятие решений, обучение и планирование.

Действие агента происходит в одном цикле работы системы. Первая этап цикла - это получение данных из внешнего мира (input phase), происходит получение данных агента: информация с сенсоров, местоположение агента и информация о нем. Следующий этап - предложения операторов (propose phase), выбираются подходящие операторы, у которых выполняются все условия. Третий этап — выбор определенного оператора из предложенных (decision phase), выбирается один оператор, если заданы приоритеты, то предпочитается оператор с наивысшем приоритетом. Следующий этап - применение выбранного на предыдущем шаге оператора (apply phase). Заключительный этап - передача информации во внешний мир, с которым взаимодействует агент (output phase), агент выполняет действия в этом мире.

### Запуск системы ###

Нужно скачать последнюю версию Soar: http://soar.eecs.umich.edu/articles/downloads/soar-suite/105-soar-tutorial-9-4-0. 
Для работы с разработанным агентом скачайте все необходимые файлы, размещенные в репозитории. 
После скачивания файлов запустите Eaters, создайте нового агента (выбирайте кнопку New), задайте цвет и имя созданного агента, затем выбирайте Soar агента, подобрав нужный файл с правилами агента ***.soar. После создания одного агента можете основать еще несколько (до 4), после чего запустите агентов. Для отслеживания работы используйте debugger, в котором есть возможность отследить цикл работы агента.

### Описание собственного агента ###

Реализованные правила помогают итерсу избегать других, то есть у них не будет возможности съесть его.
Для этого использовал вспомогательную структуру, помогающую находить противоположное направление к заданному.
Агенту предложены два оператора: переместиться на соседнюю клетку при том, что на расстоянии 2 клеток от исходной есть другой итерс(move-avoid) или нет(move). Для каждого оператора ставятся приоритеты в зависимости от того, что в соседней клетке: высший приоритет имеют клетки с бонусным ресурсом, затем с нормальным. И оператор move-avoid предпочтительнее move, так как нам важно не попасть на клетку, соседнюю с другим итерсом. В итоге выбирается наиболее подходящий оператор для текущей ситуации, после чего итерс двигается в нужном направлении. 

### План работы по реализации проекта ###

**Выполненный план работы:**

* установить дистрибутив Soar системы;

* разобраться во взаимодействии модулей, из которых состоит система;

* понять архитектуру системы и цикл работы агента;

* выполнить упражнения из Tutorial с программной реализацией;

* написать собственного агента move_avoid.soar.
