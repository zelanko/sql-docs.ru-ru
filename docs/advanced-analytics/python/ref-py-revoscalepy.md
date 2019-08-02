---
title: пакет Python для revoscalepy
description: Общие сведения о модуле revoscalepy в SQL Server Службы машинного обучения с помощью Python.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/12/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 76c68d0753c4ba29387b3378c1086ce9bce4f53b
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715774"
---
# <a name="revoscalepy-python-module-in-sql-server"></a>revoscalepy (модуль Python в SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

**revoscalepy** — это совместимый с Python35 модуль от корпорации Майкрософт, который поддерживает распределенные вычисления, удаленные контексты вычислений и высокопроизводительные алгоритмы обработки и анализа данных. Он основан на пакете **RevoScaleR** для R (распространяемый с Microsoft R Server и SQL Server R Services), предлагая аналогичные функции:

+ Локальные и удаленные контексты вычислений в системах с одинаковой версией **revoscalepy**
+ Функции преобразования и визуализации данных
+ Функции обработки и анализа данных, масштабируемые через распределенную или параллельную обработку
+ Улучшенная производительность, включая использование библиотек Intel Math

Источники данных и контексты вычислений, создаваемые в **revoscalepy** , можно также использовать в алгоритмах машинного обучения. Общие сведения об этих алгоритмах см. [в разделе Модуль Microsoftml Python в SQL Server](ref-py-microsoftml.md).

## <a name="full-reference-documentation"></a>Полная справочная документация

Библиотека **revoscalepy** распространяется в нескольких продуктах Майкрософт, но их использование одинаково при получении библиотеки в SQL Server или другом продукте. Поскольку функции одинаковы, [Документация по отдельным функциям revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) публикуется только в одном расположении в справочнике по [Python](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) для Microsoft Machine Learning Server. Если существуют какие-либо поведения конкретного продукта, расхождения будут указаны на странице справки по функциям.

## <a name="versions-and-platforms"></a>Версии и платформы

Модуль **revoscalepy** основан на Python 3,5 и доступен только при установке одного из следующих продуктов или файлов загрузки Майкрософт:

+ [Изучение служб машины SQL Server](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 или более поздней версии](https://docs.microsoft.com/machine-learning-server/)
+ [Клиентские библиотеки Python для клиента обработки и анализа данных](setup-python-client-tools-sql.md)

> [!NOTE]
> Полные версии продуктов выпускаются только для Windows, начиная с SQL Server 2017. Поддержка Linux для **revoscalepy** впервые добавлена в [предварительной версии SQL Server 2019](../../linux/sql-server-linux-setup-machine-learning.md).

## <a name="functions-by-category"></a>Функции по категориям

В этом разделе перечислены функции по категориям, которые позволяют понять, как используется каждая из них. Оглавление можно также использовать [для поиска](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) функций в алфавитном порядке.

## <a name="1-data-source-and-compute"></a>1 — источник данных и вычисление

**revoscalepy** включает функции для создания источников данных и настройки расположения или *контекста вычисления*, для которых выполняются вычисления. Функции, относящиеся к SQL Serverным сценариям, перечислены в таблице ниже.

В некоторых случаях SQL Server и Python используют разные типы данных. Список сопоставлений между типами данных SQL и Python см. в разделе [типы данных Python-to-SQL](python-libraries-and-data-types.md).

| Компонент| Описание|
| ------- | ---------- |
| [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver) |  Создайте объект контекста вычислений SQL Server для принудительной отправки вычислений в удаленный экземпляр. Несколько функций **revoscalepy** принимают контекст вычислений в качестве аргумента. Пример контекстного переключения см. в разделе [Создание модели с помощью revoscalepy](../tutorials/use-python-revoscalepy-to-create-model.md).|
| [RxSqlServerData](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxsqlserverdata) | Создайте объект данных на основе SQL Server запроса или таблицы. |
| [RxOdbcData](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxodbcdata)| Создайте источник данных на основе соединения ODBC. |
| [RxXdfData](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxxdfdata) | Создайте источник данных на основе локального файла Xdf-. Файлы Xdf-часто используются для разгрузки данных в памяти на диск. Файл Xdf-может быть полезен при работе с большим объемом данных, чем может быть передан из базы данных в одном пакете, или больше данных, чем может уместиться в памяти. Например, если вы регулярно перемещаете большие объемы данных из базы данных на локальную рабочую станцию, а не запрашиваете базу данных повторно для каждой операции R, можно использовать файл Xdf-в качестве типа кэша, чтобы сохранить данные локально, а затем работать с ними в рабочей области R. |

> [!TIP]
> Если вы не знакомы с идеями источников данных или контекстов вычислений, рекомендуется начать с использования [распределенных вычислений](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing) в документации по Microsoft Machine Learning Server.

## <a name="2-data-manipulation-etl"></a>2\. обработка данных (ETL)

| Компонент | Описание |
|----------|-------------|
|[rx_import](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-import) | Импорт данных в файл Xdf-или кадр данных.|
|[rx_data_step](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-data-step) | Преобразование данных из набора входных данных в выходной набор данных.|

<a name="bkmk_algorithms"></a>

## <a name="3-training-and-summarization"></a>3\. обучение и формирование сводных данных

| Компонент| Описание|
| ------- | ---------- |
|[rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees) | Подгонка высокометод стохастическогоных деревьев решений с градиентным ускорением|
|[rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest) | Подгонка лесов принятия решений по классификации и регрессии|
|[rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree) | Подгонка деревьев классификации и регрессии |
|[rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod) | создание модели линейной регрессии;|
|[rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit) | создание модели логистической регрессии;|
|[rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary) | Создание сводок унивариате объектов в revoscalepy.|

Кроме того, следует изучить функции в [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) для дополнительных подходов.

<a name="ml-scoring"></a>

## <a name="4-scoring-functions"></a>4 — функции оценки

| Компонент| Описание|
| ------- | ---------- |
| [rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict) | Создание прогнозов на основе обученной модели|) | Формирует прогнозы из обученной модели и может использоваться для оценки в реальном времени. |
|[rx_predict_default](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict-default) | Вычисление прогнозируемых значений и остатков с помощью объектов rx_lin_mod и rx_logit. |
|[rx_predict_rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict-rx-dforest) | Вычислите прогнозируемые или заданные значения для набора данных из объекта rx_dforest или rx_btrees. |
|[rx_predict_rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict-rx-dtree) | Вычислите прогнозируемые или заданные значения для набора данных из объекта rx_dtree. |

## <a name="how-to-work-with-revoscalepy"></a>Работа с revoscalepy

Функции в **revoscalepy** вызываемы в коде Python, инкапсулированном в хранимых процедурах. Большинство разработчиков создают решения **revoscalepy** локально, а затем выполняют перенос завершенного кода Python в хранимые процедуры в качестве упражнения развертывания.

При локальном запуске скрипт Python обычно запускается из командной строки или из среды разработки Python и задается SQL Server контексте вычислений с помощью одной из функций **revoscalepy** . Можно использовать удаленный контекст вычислений для всего кода или для отдельных функций. Например, может потребоваться разгрузка обучения модели на сервер для использования последних данных и предотвращения перемещения данных.

Когда вы будете готовы инкапсулировать скрипт Python внутри хранимой процедуры [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql), мы рекомендуем переписать код как единую функцию с четко определенными входными и выходными данными. 

Входные и выходные данные должны быть **Pandas** кадрами данных. Когда это будет сделано, можно вызвать хранимую процедуру из любого клиента, который поддерживает T-SQL, легко передавать запросы SQL в качестве входных данных и сохранять результаты в таблицах SQL. Пример см. [в статье изучение служб аналитики Python в базе данных для разработчиков SQL](../tutorials/sqldev-in-database-python-for-sql-developers.md).

### <a name="using-revoscalepy-with-microsoftml"></a>Использование revoscalepy с microsoftml

Функции Python для [microsoftml](ref-py-microsoftml.md) интегрированы с контекстами вычислений и источниками данных, предоставляемыми в revoscalepy. При вызове функций из microsoftml, например при определении и обучении модели, используйте функции revoscalepy для выполнения кода Python либо локально, либо в контексте удаленного вычислений SQl Server.

В следующем примере показан синтаксис импорта модулей в коде Python. Затем можно сослаться на нужные вам функции.

```python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

## <a name="see-also"></a>См. также

+ [Учебники по Python](../tutorials/sql-server-python-tutorials.md)
+ [Учебник. Внедрение кода Python в T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Справочник по Python (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference)
