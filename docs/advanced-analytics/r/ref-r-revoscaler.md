---
title: Библиотека функций RevoScaleR R - служб машинного обучения SQL Server
description: Общие сведения о функции библиотеки RevoScaleR в SQL Server 2016 R Services и служб SQL Server 2017 машинного обучения с помощью языка R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/04/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: d0691508ff3be52a4af744c1167ca799f8d23050
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962488"
---
# <a name="revoscaler-r-library-in-sql-server"></a>RevoScaleR (библиотека R в SQL Server)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**RevoScaleR** — это библиотека функций обработки и анализа данных высокой производительности от корпорации Майкрософт. Функции поддерживают импорт данных, преобразования данных, формирования сводных данных, визуализации и анализа.

В отличие от базовых функций R RevoScaleR операции могут выполняться для очень больших наборов данных в параллельном режиме, а также в распределенной файловой системе. Функции могут работать над наборами данных, которые не помещаются в памяти с помощью фрагментации и результаты сборки после завершения операции.

Функции RevoScaleR, обозначаются знаком **rx** или **Rx** префикс, чтобы сделать их легко определить.

RevoScaleR служит в качестве платформы для распределенной обработки и анализа. Например, можно использовать контекстам вычислений RevoScaleR и преобразования с алгоритмами состояние картинок в [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-the-microsoftml-package). Можно также использовать [rxExec](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexec) для выполнения базовых функций R в параллельном режиме.

## <a name="full-reference-documentation"></a>Полная справочная документация

**RevoScaleR** library распространяется в нескольких продуктов корпорации Microsoft, но использование совпадает ли вы получаете библиотеки в SQL Server или другой продукт. Так как функции являются одинаковыми, [документации для отдельных функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) публикуется только в одном месте в разделе [ссылку R](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) для сервера машинного обучения Майкрософт. Следует любого конкретного продукта существует поведения, несоответствия будут указаны в странице справки по функции.

## <a name="versions-and-platforms"></a>Версии и платформы

**RevoScaleR** библиотеки на основе R 3.4.3 и доступны только в том случае, если устанавливается одно из следующих продуктов корпорации Майкрософт или файлы для загрузки:

+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)
+ [SQL Server 2017 службы машинного обучения](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 или более поздней версии](https://docs.microsoft.com/machine-learning-server/)
+ [Microsoft R client](set-up-a-data-science-client.md)

> [!NOTE]
> Версии выпуска полной версии продукта: только для Windows, для начиная с SQL Server 2017. Поддержка Linux **RevoScaleR** возможности [предварительной версии SQL Server 2019](../../linux/sql-server-linux-setup-machine-learning.md).

## <a name="functions-by-category"></a>Функции по категориям

В этом разделе перечислены функции по категориям дать вам представление о том, как используется каждый из них. Можно также использовать [оглавление](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) следует выполнять поиск функций в алфавитном порядке.

## <a name="1-data-source-and-compute"></a>Источник данных 1 и вычислительные ресурсы

**RevoScaleR** включает функции для создания источников данных и задание расположения, или *контекста вычислений*, из которых вычисления выполняются. Объект источника данных представляет собой контейнер, который указывает строку подключения с необходимым набором данных и определяется как таблица, представление или запрос. Вызовы хранимых процедур не поддерживаются. В следующей таблице перечислены функции, относящиеся к сценариев SQL Server.

SQL Server и R используют разные типы данных в некоторых случаях. Список сопоставлений типов данных SQL и R, см. в разделе [типов данных R-to-SQL](r-libraries-and-data-types.md).

| Компонент| Описание|
| ------- | ---------- |
| [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) |  Создайте объект контекста вычислений SQL Server для принудительной отправки вычислений на удаленном экземпляре. Несколько **RevoScaleR** функции принимают контекст вычислений в качестве аргумента. |
|[rxGetComputeContext / rxSetComputeContext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) | Возвращает или задает активный контекст вычисления. |
| [RxSqlServerData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata) | Создайте объект данных, на основе запроса SQL Server или таблицы. |
| [RxOdbcData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxodbcdata) | Создайте источник данных, на основе соединения ODBC. |
| [RxXdfData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxxdfdata) | Создайте источник данных, основанный на локальный файл XDF. Файлы XDF часто используются для передачи данных в памяти на диск. Файл XDF можно использовать при работе с больше данных, чем может быть перемещена из базы данных в одном пакете, или больше данных, чем может поместиться в памяти. Например если вам приходится часто перемещать большие объемы данных из базы данных на локальную рабочую станцию, вместо того чтобы запрос базы данных несколько раз для каждой операции R, вы можно использовать xdf-файл как своего рода кэша чтобы сохранить данные локально и затем работать с ними в рабочем пространстве R.|

> [!TIP]
> Если вы не знакомы с идея источников данных или контекстов вычислений, мы рекомендуем начать с [распределенные вычисления](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing) в документации по Microsoft Machine Learning Server.

### <a name="perform-ddl-statements"></a>Выполнение инструкции DDL

Вы можете выполнить инструкции DDL из R, если у вас есть необходимые разрешения на экземпляр и базу данных. Следующие функции использовать вызовы ODBC на выполнение инструкций DDL или извлечь схему базы данных.

| Компонент| Описание|
| ------- | ---------- |
| [rxSqlServerTableExists и rxSqlServerDropTable](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable) | Удалить [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] таблицу или проверить существование таблицы базы данных или объекта. |
| [rxExecuteSQLDDL](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexecutesqlddl) | Выполнения команды языка определения данных (DDL), определяет или управляет объектов базы данных. Эта функция не может возвращать данные и используется только для извлечения или изменения схемы объекта или метаданных.|

## <a name="2-data-manipulation-etl"></a>2-управление данными (ETL)

После создания объекта источника данных, можно использовать объект для загрузки данных в него и преобразования данных запись новых данных в указанное место назначения. В зависимости от размера данных в источнике вы также можете определить размер пакета как часть источника данных и переместить данные фрагментами.

| Компонент | Описание |
|----------|-------------|
| [rxOpen методы](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxopen-methods) | Проверьте, является ли источник данных недоступен, откройте или закрывает источник данных, чтение данных из источника, записывать данные в целевой объект и закрывает источник данных.|
| [функции rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport) | Перемещение данных из источника данных в хранилище файлов или в кадр данных.|
| [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) | Преобразование данных при его перемещении между источниками данных.|

<a name="graphing-functions"></a>

## <a name="3-graphing-functions"></a>Функции построения диаграмм 3

| Имя функции | Описание |
|---------------|-------------|
|[rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram)  |Создает гистограмму на основе данных. | 
|[rxLinePlot](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlineplot) |Создает линейный график, на основе данных. | 
|[rxLorenz](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlorenz)  |Вычисляет кривую Лоренца, который можно отображать. | 
|[rxRocCurve](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxroc)  |Вычисляет и строит кривые ОШИБОК на основе фактических и прогнозируемых данных. | 

<a name="statistics-functions"></a>

## <a name="4-descriptive-statistics"></a>4-Описательная статистика

| Имя функции | Описание |
|---------------|-------------|
|[rxQuantile](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxquantile) <sup>*</sup> |Вычисляет приблизительно квантили для xdf-файлов и кадры данных без сортировки. | 
|[rxSummary](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsummary) <sup>*</sup> |Базовые сводные статистические данные о данных, включая вычисления по группе. Записи от группы вычислений xdf-файл не поддерживается. | 
|[rxCrossTabs](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcrosstabs) <sup>*</sup> |Формула на основе перекрестные таблицы данных. | 
|[rxCube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcube) <sup>*</sup> |Альтернативные формула на основе перекрестной предназначен для эффективного представления, возвращая результаты куба. Записи выходных данных в xdf-файл не поддерживается. | 
|[rxMarginals](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxmarginals)  |Граничная сводки кросс tabulations. | 
|[AS.xtabs](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/as.xtabs)  |Преобразует результаты перекрестного вычисления переходят к xtabs объекта. | 
|[rxChiSquaredTest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxchisquaredtest)  |Выполняет тест хи-квадрат в объекте xtabs. Использовать с небольшими наборами данных, а не по блокам данных. | 
|[rxFisherTest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxchisquaredtest)  |Выполняет точный тест Фишера в объекте xtabs. Использовать с небольшими наборами данных, а не по блокам данных. | 
|[rxKendallCor](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxchisquaredtest)  |Вычисляет коэффициент ранговой ранг коэффициента корреляции Кендалла с помощью объекта xtabs. | 
|[rxPairwiseCrossTab](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpairwisecrosstab)  |Применяет функцию к парный сочетаниям строк и столбцов объекта xtabs. | 
|[rxRiskRatio](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxriskratio)  |Вычисляет относительный риск в объект xtabs двух две. | 
|[rxOddsRatio](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxriskratio)  |Вычисляет отношение шансов в объект xtabs двух две. | 

<sup>*</sup> Обозначает наиболее популярных функций в этой категории.

<a name="prediction-functions"></a>

## <a name="5-prediction-functions"></a>5-прогнозирующих функций

| Имя функции | Описание |
|---------------|-------------|
|[rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod) <sup>*</sup> |Подгоняет линейную модель к данным. | 
|[rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit) <sup>*</sup> |Подгоняет модель логистической регрессии к данным. | 
|[rxGlm](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxglm) <sup>*</sup> |Подгоняет обобщенную линейную модель к данным. | 
|[rxCovCor](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor) <sup>*</sup> |Вычисления ковариации, корреляции или суммы квадратов или векторного произведения матрицы для набора переменных. | 
|[rxDTree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree) <sup>*</sup> |Устанавливает размер дерева классификации или регрессии к данным. | 
|[rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees) <sup>*</sup> |Подходит для классификации или регрессии леса принятия решений к данным с помощью вероятностного градиентного бустинга. | 
|[rxDForest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest) <sup>*</sup> |Подходит для классификации или регрессии леса принятия решений к данным. | 
|[rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxPredict) <sup>*</sup> |Вычисляет прогнозы для подогнанных моделей. Выходные данные должны быть источника данных XDF. | 
|[rxKmeans](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxkmeans) <sup>*</sup> |Выполняет кластеризацию методом к-средних. | 
|[rxNaiveBayes](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxnaivebayes) <sup>*</sup> |Выполняет классификации упрощенного алгоритма Байеса. | 
|[rxCov](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor) |Вычисляет матрицу ковариации для набора переменных. | 
|[rxCor](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor)  |Вычисляет матрицу корреляции для набора переменных. | 
|[rxSSCP](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor)  |Вычисляет отношение суммы квадратов или векторного произведения матрицы для набора переменных. | 
|[rxRoc](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxroc)  |Получатель операционной характеристика (ROC) вычислений с использованием фактических и прогнозируемых значений из бинарного классификатора системы. | 

<sup>*</sup> Обозначает наиболее популярных функций в этой категории.


## <a name="how-to-work-with-revoscaler"></a>Способы работы с RevoScaleR

Функции в **RevoScaleR** можно вызывать в коде R инкапсулируются в хранимых процедурах. Большинство разработчиков создавать **RevoScaleR** решения локально, и затем перенести готовый код R в хранимые процедуры с действий развертывания.

При локальном запуске вы обычно запустить сценарий R из командной строки или из среды разработки R и укажите контекст вычислений SQL Server с помощью одного из **RevoScaleR** функции. Контекст удаленных вычислений можно использовать для весь код, или для отдельных функций. Например можно разгрузить Обучение модели на сервер, чтобы использовать последние данные и избежать перемещения данных.

Когда будете готовы для инкапсуляции скрипт R в хранимой процедуре, [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql), рекомендуется переписать код как одну функцию, которая четко определенные входные и выходные данные. 

## <a name="see-also"></a>См. также

+ [Учебники по R](../tutorials/sql-server-r-tutorials.md)
+ [Узнайте, как использовать контексты вычислений](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [R для разработчиков SQL: Обучение и ввод модели в эксплуатацию](../tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [Образцы продуктов Microsoft на GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples)
+ [Справочник по R (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) 
