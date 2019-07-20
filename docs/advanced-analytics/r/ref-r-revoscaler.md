---
title: Библиотека функций R RevoScaleR
description: Введение в библиотеку функций RevoScaleR в службах SQL Server 2016 R и SQL Server 2017 Службы машинного обучения с R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/04/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 24c751051ff09fa80e738fc4723a00722b6b2e12
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344525"
---
# <a name="revoscaler-r-library-in-sql-server"></a>RevoScaleR (библиотека R в SQL Server)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**RevoScaleR** — это библиотека высокопроизводительных функций обработки и анализа данных от Майкрософт. Функции поддерживают импорт и преобразование данных, формирование сводных данных, визуализацию и анализ.

В отличие от базовых функций R, операции RevoScaleR могут выполняться для очень больших наборов данных, параллельно и в распределенных файловых системах. Функции могут работать над наборами данных, которые не помещаются в памяти, с помощью фрагментации и путем повторной сборки результатов после завершения операций.

Функции RevoScaleR обозначаются префиксом **RX** или **RX** , чтобы облегчить их обнаружение.

RevoScaleR выступает в качестве платформы для распределенной обработки и анализа данных. Например, можно использовать контексты вычислений RevoScaleR и преобразования с помощью встроенных алгоритмов в [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-the-microsoftml-package). Можно также использовать [rxExec](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexec) для параллельного выполнения базовых функций R.

## <a name="full-reference-documentation"></a>Полная справочная документация

Библиотека **RevoScaleR** распространяется в нескольких продуктах Майкрософт, но их использование одинаково при получении библиотеки в SQL Server или другом продукте. Поскольку функции одинаковы, [Документация по отдельным функциям RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) публикуется только в одном расположении в справочнике по [R](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) для Microsoft Machine Learning Server. Если существуют какие-либо поведения конкретного продукта, расхождения будут указаны на странице справки по функциям.

## <a name="versions-and-platforms"></a>Версии и платформы

Библиотека **RevoScaleR** основана на R 3.4.3 и доступна только при установке одного из следующих продуктов или загрузок Майкрософт:

+ [Службы SQL Server 2016 R](../install/sql-r-services-windows-install.md)
+ [SQL Server 2017 Службы машинного обучения](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 или более поздней версии](https://docs.microsoft.com/machine-learning-server/)
+ [Клиент Microsoft R](set-up-a-data-science-client.md)

> [!NOTE]
> Полные версии продуктов выпускаются только для Windows, начиная с SQL Server 2017. Поддержка Linux для **RevoScaleR** впервые добавлена в [предварительной версии SQL Server 2019](../../linux/sql-server-linux-setup-machine-learning.md).

## <a name="functions-by-category"></a>Функции по категориям

В этом разделе перечислены функции по категориям, которые позволяют понять, как используется каждая из них. Оглавление можно также использовать [для поиска](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) функций в алфавитном порядке.

## <a name="1-data-source-and-compute"></a>1 — источник данных и вычисление

**RevoScaleR** включает функции для создания источников данных и настройки расположения или *контекста вычисления*, для которых выполняются вычисления. Объект источника данных представляет собой контейнер, который указывает строку подключения с необходимым набором данных и определяется как таблица, представление или запрос. Вызовы хранимых процедур не поддерживаются. Функции, относящиеся к SQL Serverным сценариям, перечислены в таблице ниже.

В некоторых случаях SQL Server и R используют разные типы данных. Список сопоставлений между типами данных SQL и R см. в разделе [типы данных r to-SQL](r-libraries-and-data-types.md).

| Компонент| Описание|
| ------- | ---------- |
| [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) |  Создайте объект контекста вычислений SQL Server для принудительной отправки вычислений в удаленный экземпляр. Несколько функций **RevoScaleR** принимают контекст вычислений в качестве аргумента. |
|[Рксжеткомпутеконтекст/rxSetComputeContext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) | Возвращает или задает активный контекст вычислений. |
| [RxSqlServerData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata) | Создайте объект данных на основе SQL Server запроса или таблицы. |
| [RxOdbcData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxodbcdata) | Создайте источник данных на основе соединения ODBC. |
| [RxXdfData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxxdfdata) | Создайте источник данных на основе локального файла Xdf-. Файлы Xdf-часто используются для разгрузки данных в памяти на диск. Файл Xdf-может быть полезен при работе с большим объемом данных, чем может быть передан из базы данных в одном пакете, или больше данных, чем может уместиться в памяти. Например, если вы регулярно перемещаете большие объемы данных из базы данных на локальную рабочую станцию, а не запрашиваете базу данных повторно для каждой операции R, можно использовать файл Xdf-в качестве типа кэша, чтобы сохранить данные локально, а затем работать с ними в рабочей области R.|

> [!TIP]
> Если вы не знакомы с идеями источников данных или контекстов вычислений, рекомендуется начать с использования [распределенных вычислений](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing) в документации по Microsoft Machine Learning Server.

### <a name="perform-ddl-statements"></a>Выполнение инструкций DDL

Инструкции DDL можно выполнять из R, если у вас есть необходимые разрешения на экземпляр и базу данных. Следующие функции используют вызовы ODBC для выполнения инструкций DDL или получения схемы базы данных.

| Компонент| Описание|
| ------- | ---------- |
| [rxSqlServerTableExists и rxSqlServerDropTable](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable) | [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] Удалите таблицу или проверьте наличие таблицы или объекта базы данных. |
| [рксексекутесклддл](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexecutesqlddl) | Выполните команду языка описания данных DDL, которая определяет объекты базы данных или манипулирует ими. Эта функция не может возвращать данные и используется только для получения или изменения схемы или метаданных объекта.|

## <a name="2-data-manipulation-etl"></a>2\. обработка данных (ETL)

После создания объекта источника данных можно использовать объект для загрузки в него данных, преобразования данных или записи новых данных в указанное место назначения. В зависимости от размера данных в источнике вы также можете определить размер пакета как часть источника данных и переместить данные фрагментами.

| Компонент | Описание |
|----------|-------------|
| [rxOpen — методы](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxopen-methods) | Проверьте, доступен ли источник данных, откройте или закройте источник данных, считывает данные из источника, записываете данные в целевой объект и закрываете источник данных.|
| [rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport) | Перемещение данных из источника данных в хранилище файлов или в кадр данных.|
| [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) | Преобразуйте данные, перемещая их между источниками данных.|

<a name="graphing-functions"></a>

## <a name="3-graphing-functions"></a>3\. графические функции

| Имя функции | Описание |
|---------------|-------------|
|[rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram)  |Создает гистограмму на основе данных. | 
|[ркслинеплот](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlineplot) |Создает график на основе данных. | 
|[ркслоренз](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlorenz)  |Вычисление кривой Лоренца, которая может быть построена. | 
|[rxRocCurve](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxroc)  |Выполняет вычисление и построение диаграмм ROC кривых от фактических и прогнозируемых данных. | 

<a name="statistics-functions"></a>

## <a name="4-descriptive-statistics"></a>4\. Описательная статистика

| Имя функции | Описание |
|---------------|-------------|
|[ркскуантиле](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxquantile)<sup>*</sup> |Вычисление приблизительных квантилей для файлов Xdf-и кадров данных без сортировки. | 
|[rxSummary](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsummary)<sup>*</sup> |Базовая сводная статистика данных, включая вычисления по группам. Запись с помощью групповых вычислений в файл. Xdf-не поддерживается. | 
|[rxCrossTabs](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcrosstabs) <sup>*</sup> |Перекрестные табличные данные на основе формул. | 
|[rxCube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcube)<sup>*</sup> |Альтернативная перекрестная Табуляция на основе формул, предназначенная для эффективного представления, возвращающего результаты Куба. Запись выходных данных в файл. Xdf-не поддерживается. | 
|[рксмаргиналс](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxmarginals)  |Маржинальная сводка перекрестных табличий. | 
|[AS. кстабс](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/as.xtabs)  |Преобразует результаты перекрестной табуляции в объект кстабс. | 
|[рксчискуаредтест](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxchisquaredtest)  |Выполняет тест хи-квадрат для объекта кстабс. Используется с небольшими наборами данных и не содержит блоков данных. | 
|[рксфишертест](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxchisquaredtest)  |Выполняет точную проверку Фишера для объекта кстабс. Используется с небольшими наборами данных и не содержит блоков данных. | 
|[ркскендаллкор](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxchisquaredtest)  |Выполняет вычисление коэффициента корреляции Кендалл в Тау с помощью объекта кстабс. | 
|[rxPairwiseCrossTab](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpairwisecrosstab)  |Применение функции к парным сочетаниям строк и столбцов объекта кстабс. | 
|[рксрискратио](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxriskratio)  |Вычислите относительные риски для двух объектов кстабс. | 
|[рксоддсратио](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxriskratio)  |Вычисление вероятного соотношения на два объекта кстабс. | 

<sup>*</sup>Обозначает наиболее популярные функции в этой категории.

<a name="prediction-functions"></a>

## <a name="5-prediction-functions"></a>5-прогнозирующие функции

| Имя функции | Описание |
|---------------|-------------|
|[rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod)<sup>*</sup> |Подмещает линейную модель к данным. | 
|[rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit)<sup>*</sup> |Соответствует модели логистической регрессии с данными. | 
|[rxGlm](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxglm)<sup>*</sup> |Подмещает обобщенную линейную модель к данным. | 
|[rxCovCor](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor) <sup>*</sup> |Вычислите ковариацию, корреляцию или сумму квадратов и перекрестных матриц для набора переменных. | 
|[rxDTree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree)<sup>*</sup> |Подходящее дерево классификации или регрессии к данным. | 
|[рксбтрис](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees)<sup>*</sup> |Помещает лес решений с классификацией или регрессией в данные с помощью алгоритма усиления градиента метод стохастического. | 
|[rxDForest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest)<sup>*</sup> |Помещает в лес решения по классификации или регрессии данные. | 
|[rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxPredict)<sup>*</sup> |Вычисляет прогнозы для моделей с заданной. Выходные данные должны быть источниками данных Xdf-. | 
|[ркскмеанс](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxkmeans)<sup>*</sup> |Выполняет кластеризацию с k-средних. | 
|[ркснаивебайес](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxnaivebayes)<sup>*</sup> |Выполняет классификацию упрощенного алгоритма Байеса. | 
|[рксков](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor) |Вычислите матрицу ковариации для набора переменных. | 
|[ркскор](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor)  |Вычислите матрицу корреляции для набора переменных. | 
|[ркссскп](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor)  |Вычисление суммы квадратов и матриц перекрестного произведения для набора переменных. | 
|[рксрок](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxroc)  |Операционная характеристика приемника (ROC) вычисляется с использованием фактических и прогнозируемых значений из двоичной системы-классификатора. | 

<sup>*</sup>Обозначает наиболее популярные функции в этой категории.


## <a name="how-to-work-with-revoscaler"></a>Работа с RevoScaleR

Функции в **RevoScaleR** вызываемы в коде R, инкапсулированном в хранимых процедурах. Большинство разработчиков создают решения **RevoScaleR** локально, а затем выполняют перенос завершенного кода R в хранимые процедуры в качестве упражнения развертывания.

При локальном запуске скрипт R обычно запускается из командной строки или из среды разработки R и указывается SQL Server контексте вычислений с помощью одной из функций **RevoScaleR** . Можно использовать удаленный контекст вычислений для всего кода или для отдельных функций. Например, может потребоваться разгрузка обучения модели на сервер для использования последних данных и предотвращения перемещения данных.

Когда вы будете готовы инкапсулировать R-скрипт в хранимую процедуру [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql), мы рекомендуем переписать код как единую функцию с четко определенными входными и выходными данными. 

## <a name="see-also"></a>См. также

+ [Учебники по R](../tutorials/sql-server-r-tutorials.md)
+ [Сведения об использовании контекстов вычислений](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [R для разработчиков SQL: Обучение и эксплуатацию модели](../tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [Примеры продуктов Майкрософт на сайте GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples)
+ [Справочник по R (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) 
