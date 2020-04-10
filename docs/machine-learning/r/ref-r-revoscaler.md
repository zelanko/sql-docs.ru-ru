---
title: Библиотека функций R RevoScaleR
description: Общие сведения о библиотеке функций RevoScaleR в SQL Server 2016 R Services и Службах машинного обучения SQL Server с R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/06/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 7b24d5499e618a09c4d80e8614b08219e6c6f788
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2020
ms.locfileid: "81117437"
---
# <a name="revoscaler-r-library-in-sql-server"></a>RevoScaleR (библиотека R в SQL Server)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

**RevoScaleR** — это библиотека высокопроизводительных функций обработки и анализа данных от Майкрософт. Функции поддерживают импорт и преобразование данных, формирование сводных данных, визуализацию и анализ.

В отличие от базовых функций R, операции RevoScaleR могут выполняться для очень больших наборов данных параллельно и в распределенных файловых системах. Функции могут работать с наборами данных, не умещающимися в памяти, посредством фрагментации и повторной сборки результатов после завершения операций.

Функции RevoScaleR указываются с префиксом **rx** или **Rx**, чтобы их было легко найти.

RevoScaleR выступает в качестве платформы для распределенной обработки и анализа данных. Например, можно использовать преобразования и контексты вычислений RevoScaleR с передовыми алгоритмами в [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-the-microsoftml-package). Можно также использовать [rxExec](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexec) для параллельного выполнения базовых функций R.

## <a name="full-reference-documentation"></a>Полная справочная документация

Библиотека **RevoScaleR** распространяется в нескольких продуктах Майкрософт и используется так же, как при получении в SQL Server или другом продукте. Благодаря сходству функций [документация по отдельным функциям RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) опубликована только в одном разделе в [справочнике по R](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) для Microsoft Machine Learning Server. Если для конкретных продуктов функции будут действовать иначе, выявленные расхождения будут приведены на странице справки по функциям.

## <a name="versions-and-platforms"></a>Версии и платформы

Библиотека **RevoScaleR** основана на R 3.4.3 и доступна только при установке одного из следующих продуктов или скачиваемых файлов Майкрософт:

+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)
+ [Службы машинного обучения SQL Server](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 или более поздней версии](https://docs.microsoft.com/machine-learning-server/)
+ [Microsoft R Client](set-up-a-data-science-client.md)

> [!NOTE]
> В SQL Server 2017 полные версии выпусков продуктов доступны только для Windows. В [SQL Server 2019](../../linux/sql-server-linux-setup-machine-learning.md) библиотека **RevoScaleR** поддерживает Windows и Linux.

## <a name="functions-by-category"></a>Функции по категориям

Чтобы можно было понять, как использовать каждую функцию, в этом разделе приводится описание функций по категориям. Для поиска функций в алфавитном порядке можно воспользоваться [оглавлением](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference).

## <a name="1-data-source-and-compute"></a>1\. Источники данных и вычисления

**RevoScaleR** содержит функции для создания источников данных и настройки расположения или *контекста вычисления*, в котором выполняются вычисления. Объект источника данных представляет собой контейнер, который указывает строку подключения с необходимым набором данных и определяется как таблица, представление или запрос. Вызовы хранимых процедур не поддерживаются. Функции, относящиеся к сценариям SQL Server, приведены в таблице ниже.

В некоторых случаях SQL Server и R используют разные типы данных. Список сопоставлений между типами данных SQL и R см. в разделе о [типах данных R и SQL](r-libraries-and-data-types.md).

| Компонент| Описание|
| ------- | ---------- |
| [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) |  Создание объекта контекста вычисления SQL Server для отправки вычислений в удаленный экземпляр. Несколько функций **RevoScaleR** принимают контекст вычисления в качестве аргумента. |
|[rxGetComputeContext/rxSetComputeContext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) | Получение или задание активного контекста вычислений. |
| [RxSqlServerData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata) | Создание объекта данных на основе запроса или таблицы SQL Server. |
| [RxOdbcData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxodbcdata) | Создание источника данных на основе соединения ODBC. |
| [RxXdfData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxxdfdata) | Создание источника данных на основе локального XDF-файла. XDF-файлы часто используются для разгрузки данных в памяти на диск. XDF-файл может быть полезен при работе с объемом данных, превышающим объем передаваемых данных из базы данных в одном пакете, или же превышающим допустимый объем данных в памяти. Например, если вам приходится часто перемещать большие объемы данных из базы данных на локальную рабочую станцию, то вместо того, чтобы выполнять запросы к базе данных для каждой операции R, вы можете использовать XDF-файл как кэш, чтобы сохранить данные локально, а затем работать с ними в рабочей области R.|

> [!TIP]
> Если вы не знакомы с концепциями источников данных или контекстов вычислений, рекомендуется начать с изучения [распределенных вычислений](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing) в документации по Microsoft Machine Learning Server.

### <a name="perform-ddl-statements"></a>Выполнение инструкций DDL

Вы можете выполнить инструкции DDL из R, если у вас имеются необходимые разрешения на экземпляр и базу данных. Следующие функции используют вызовы ODBC для выполнения инструкций DDL или получения схемы базы данных.

| Компонент| Описание|
| ------- | ---------- |
| [rxSqlServerTableExists и rxSqlServerDropTable](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable) | Удаление таблицы [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] или проверка существования объекта или таблицы базы данных. |
| [rxExecuteSQLDDL](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexecutesqlddl) | Выполнение команды языка описания данных DDL, которая определяет объекты базы данных или манипулирует ими. Эта функция не может возвращать данные и используется только для получения или изменения метаданных или схемы объекта.|

## <a name="2-data-manipulation-etl"></a>2\. Работа с данными (ETL)

После создания объекта источника данных вы можете использовать его, чтобы загрузить в него данные, преобразовать данные или записать новые данные в указанное расположение. В зависимости от размера данных в источнике вы также можете определить размер пакета как часть источника данных и переместить данные фрагментами.

| Компонент | Описание |
|----------|-------------|
| [Методы rxOpen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxopen-methods) | Проверка доступности источника данных, открытие или закрытие источника данных, чтение данных из источника, запись данных в целевой объект и закрытие источника данных.|
| [rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport) | Перемещение данных из источника данных в хранилище файлов или кадр данных.|
| [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) | Преобразование данных при их перемещении между источниками данных.|

<a name="graphing-functions"></a>

## <a name="3-graphing-functions"></a>3\. Графические функции

| Имя функции | Описание |
|---------------|-------------|
|[rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram)  |Создает гистограмму на основе данных. | 
|[rxLinePlot](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlineplot) |Создает линейный график на основе данных. | 
|[rxLorenz](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlorenz)  |Вычисляет кривую Лоренца, которую можно построить. | 
|[rxRocCurve](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxroc)  |Вычисляет и строит кривые ошибок на основе фактических и прогнозируемых данных. | 

<a name="statistics-functions"></a>

## <a name="4-descriptive-statistics"></a>4\. Описательная статистика

| Имя функции | Описание |
|---------------|-------------|
|[rxQuantile](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxquantile)<sup>*</sup> |Вычисляет приблизительные квантили для XDF-файлов и кадров данных без сортировки. | 
|[rxSummary](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsummary)<sup>*</sup> |Базовая сводная статистика по данным, включая вычисления по группе. Запись вычислений по группе в XDF-файл не поддерживается. | 
|[rxCrossTabs](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcrosstabs)<sup>*</sup> |Перекрестное табулирование данных на основе формул. | 
|[rxCube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcube)<sup>*</sup> |Альтернативное перекрестное табулирование на основе формул, предназначенное для эффективного представления возвращаемых результатов куба. Запись выходных данных в XDF-файл не поддерживается. | 
|[rxMarginals](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxmarginals)  |Маржинальные сводки по перекрестным табулированиям. | 
|[as.xtabs](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/as.xtabs)  |Преобразует результаты перекрестного табулирования в объект xtabs. | 
|[rxChiSquaredTest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxchisquaredtest)  |Выполняет тест по критерию хи-квадрат для объекта xtabs. Используется с небольшими наборами данных и не фрагментирует данные. | 
|[rxFisherTest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxchisquaredtest)  |Выполняет точный тест Фишера для объекта xtabs. Используется с небольшими наборами данных и не фрагментирует данные. | 
|[rxKendallCor](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxchisquaredtest)  |Вычисляет коэффициент ранговой корреляции Кендалла с использованием объекта xtabs. | 
|[rxPairwiseCrossTab](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpairwisecrosstab)  |Применяет функцию к парным сочетаниям строк и столбцов объекта xtabs. | 
|[rxRiskRatio](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxriskratio)  |Вычисляет относительный риск в четырехклеточном объекте xtabs. | 
|[rxOddsRatio](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxriskratio)  |Вычисляет отношение шансов в четырехклеточном объекте xtabs. | 

Символ <sup>*</sup> обозначает наиболее популярные функции в этой категории.

<a name="prediction-functions"></a>

## <a name="5-prediction-functions"></a>5\. Функции прогнозирования

| Имя функции | Описание |
|---------------|-------------|
|[rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod)<sup>*</sup> |Подгоняет линейную модель к данным. | 
|[rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit)<sup>*</sup> |Подгоняет модель логистической регрессии к данным. | 
|[rxGlm](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxglm)<sup>*</sup> |Подгоняет обобщенную линейную модель к данным. | 
|[rxCovCor](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor)<sup>*</sup> |Вычисляет матрицу ковариации, корреляции или суммы квадратов/векторного произведения для набора переменных. | 
|[rxDTree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree)<sup>*</sup> |Подгоняет дерево классификации или регрессии к данным. | 
|[rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees)<sup>*</sup> |Подгоняет лес принятия решений с классификацией или регрессией к данным с помощью алгоритма стохастического градиентного усиления. | 
|[rxDForest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest)<sup>*</sup> |Подгоняет лес принятия решений с классификацией или регрессией к данным. | 
|[rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxPredict)<sup>*</sup> |Вычисляет прогнозы для подогнанных моделей. Результатом должен быть источник данных XDF. | 
|[rxKmeans](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxkmeans)<sup>*</sup> |Выполняет кластеризацию методом К-средних. | 
|[rxNaiveBayes](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxnaivebayes)<sup>*</sup> |Выполняет классификацию с помощью упрощенного алгоритма Байеса. | 
|[rxCov](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor) |Вычисляет матрицу ковариации для набора переменных. | 
|[rxCor](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor)  |Вычисляет матрицу корреляции для набора переменных. | 
|[rxSSCP](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor)  |Вычисляет матрицу суммы квадратов или векторного произведения для набора переменных. | 
|[rxRoc](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxroc)  |Вычисляет операционные характеристики приемника (ROC) с использованием фактических и прогнозируемых значений из системы бинарного классификатора. | 

Символ <sup>*</sup> обозначает наиболее популярные функции в этой категории.


## <a name="how-to-work-with-revoscaler"></a>Работа с RevoScaleR

Функции в **RevoScaleR** вызываются в коде R, инкапсулированном в хранимые процедуры. Большинство разработчиков создают решения **RevoScaleR** локально, а затем переносят готовый код R в хранимые процедуры, отрабатывая, таким образом, процедуру развертывания.

При локальном выполнении скрипт R обычно запускается из командной строки или из среды разработки R с указанием контекста вычисления SQL Server с помощью одной из функций **RevoScaleR**. Удаленный контекст вычисления можно использовать для всего кода или для отдельных функций. Например, может потребоваться разгрузить обучение модели на сервер, чтобы работать с актуальными данными и исключить перемещение данных.

Когда вы будете готовы инкапсулировать скрипт R в хранимую процедуру [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql), рекомендуется переписать код и оформить его в виде функции, которая содержит четко определенные входные и выходные данные. 

## <a name="see-also"></a>См. также раздел

+ [Учебники по R](../tutorials/sql-server-r-tutorials.md)
+ [Использование контекстов вычисления](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [R для разработчиков на SQL: обучение и эксплуатация модели](../tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [Примеры продуктов Майкрософт на сайте GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples)
+ [Справочник по R (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) 
