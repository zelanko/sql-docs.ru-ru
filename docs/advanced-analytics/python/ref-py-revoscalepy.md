---
title: Пакет Python revoscalepy
description: Общие сведения о модуле Python revoscalepy в службах машинного обучения SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/06/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c6de9072c32155446b3ff40df3f81af9073c1090
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "73706816"
---
# <a name="revoscalepy-python-module-in-sql-server"></a>revoscalepy (модуль Python в SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

**revoscalepy** — это совместимый с Python35 модуль от корпорации Майкрософт, который поддерживает распределенные вычисления, удаленные контексты вычислений и высокопроизводительные алгоритмы обработки и анализа данных. Он основан на пакете **RevoScaleR** для R (распространяемом с Microsoft R Server и службами SQL Server R Services) и предлагает аналогичные функциональные возможности:

+ локальные и удаленные контексты вычислений в системах с одной версией **revoscalepy**;
+ функции преобразования и визуализации данных;
+ функции обработки и анализа данных, масштабируемые с помощью распределенной или параллельной обработки;
+ улучшенная производительность, включая использование библиотек Intel Math.

Источники данных и контексты вычислений, создаваемые в **revoscalepy**, можно также использовать в алгоритмах машинного обучения. Общие сведения об этих алгоритмах см. в статье [microsoftml Python module in SQL Server](ref-py-microsoftml.md) (Модуль Python microsoftml в SQL Server).

## <a name="full-reference-documentation"></a>Полная справочная документация

Библиотека **revoscalepy** распространяется в нескольких продуктах Майкрософт и используется так же, как при получении в SQL Server или другом продукте. Благодаря сходству функций [документация по отдельным функциям revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) опубликована только в одном разделе в [справочнике по Python](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) для Microsoft Machine Learning Server. Если для конкретных продуктов функции будут действовать иначе, выявленные расхождения будут приведены на странице справки по функциям.

## <a name="versions-and-platforms"></a>Версии и платформы

Модуль **revoscalepy** основан на Python 3.5 и доступен только при установке одного из следующих продуктов или скачиваемых файлов Майкрософт:

+ [Службы машинного обучения SQL Server](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 или более поздней версии](https://docs.microsoft.com/machine-learning-server/)
+ [Клиентские библиотеки Python для клиента обработки и анализа данных](setup-python-client-tools-sql.md)

> [!NOTE]
> В SQL Server 2017 полные версии выпусков продуктов доступны только для Windows. В [SQL Server 2019](../../linux/sql-server-linux-setup-machine-learning.md) модуль **revoscalepy** поддерживает Windows и Linux.

## <a name="functions-by-category"></a>Функции по категориям

Чтобы можно было понять, как использовать каждую функцию, в этом разделе приводится описание функций по категориям. Для поиска функций в алфавитном порядке можно воспользоваться [оглавлением](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference).

## <a name="1-data-source-and-compute"></a>1\. Источники данных и вычисления

**revoscalepy** содержит функции для создания источников данных и настройки расположения или *контекста вычисления*, в котором выполняются вычисления. Функции, относящиеся к сценариям SQL Server, приведены в таблице ниже.

В некоторых случаях SQL Server и Python используют разные типы данных. Список сопоставлений между типами данных SQL и Python см. в разделе о [типах данных Python и SQL](python-libraries-and-data-types.md).

| Компонент| Описание|
| ------- | ---------- |
| [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver) |  Создание объекта контекста вычисления SQL Server для отправки вычислений в удаленный экземпляр. Несколько функций **revoscalepy** принимают контекст вычисления в качестве аргумента. Пример переключения контекста см. в статье о [создание модели с помощью пакета revoscalepy](../tutorials/use-python-revoscalepy-to-create-model.md).|
| [RxSqlServerData](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxsqlserverdata) | Создание объекта данных на основе запроса или таблицы SQL Server. |
| [RxOdbcData](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxodbcdata)| Создание источника данных на основе соединения ODBC. |
| [RxXdfData](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxxdfdata) | Создание источника данных на основе локального XDF-файла. XDF-файлы часто используются для разгрузки данных в памяти на диск. XDF-файл может быть полезен при работе с объемом данных, превышающим объем передаваемых данных из базы данных в одном пакете, или же превышающим допустимый объем данных в памяти. Например, если вам приходится часто перемещать большие объемы данных из базы данных на локальную рабочую станцию, то вместо того, чтобы выполнять запросы к базе данных для каждой операции R, вы можете использовать XDF-файл как кэш, чтобы сохранить данные локально, а затем работать с ними в рабочей области R. |

> [!TIP]
> Если вы не знакомы с концепциями источников данных или контекстов вычислений, рекомендуется начать с изучения [распределенных вычислений](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing) в документации по Microsoft Machine Learning Server.

## <a name="2-data-manipulation-etl"></a>2\. Работа с данными (ETL)

| Компонент | Описание |
|----------|-------------|
|[rx_import](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-import) | Импорт данных в XDF-файл или кадр данных.|
|[rx_data_step](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-data-step) | Преобразование данных из набора входных данных в набор выходных данных.|

<a name="bkmk_algorithms"></a>

## <a name="3-training-and-summarization"></a>3\. Обучение и формирование сводных данных

| Компонент| Описание|
| ------- | ---------- |
|[rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees) | Подбор деревьев принятия решений со стохастическим градиентным усилением|
|[rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest) | Подбор лесов принятия решений по классификации и регрессии|
|[rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree) | Подбор деревьев классификации и регрессии |
|[rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod) | создание модели линейной регрессии;|
|[rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit) | создание модели логистической регрессии;|
|[rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary) | Создание однозначных сводок по объектам в revoscalepy.|

Кроме того, для реализации дополнительных подходов следует изучить функции в [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package).

<a name="ml-scoring"></a>

## <a name="4-scoring-functions"></a>4\. Функции оценки

| Компонент| Описание|
| ------- | ---------- |
| [rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict) | Создание прогнозов на основе обученной модели|) | Создает прогнозы на основе обученной модели и может использоваться для оценки в реальном времени. |
|[rx_predict_default](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict-default) | Вычисление прогнозируемых значений и остатков с помощью объектов rx_lin_mod и rx_logit. |
|[rx_predict_rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict-rx-dforest) | Вычисление прогнозируемых или подогнанных значений для набора данных на основе объектов rx_dforest или rx_btrees. |
|[rx_predict_rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict-rx-dtree) | Вычисление прогнозируемых или подогнанных значений для набора данных на основе объекта rx_dtree. |

## <a name="how-to-work-with-revoscalepy"></a>Работа с revoscalepy

Функции в **revoscalepy** вызываются в коде Python, инкапсулированном в хранимые процедуры. Большинство разработчиков создают решения **revoscalepy** локально, а затем переносят готовый код Python в хранимые процедуры, отрабатывая, таким образом, процедуру развертывания.

При локальном выполнении скрипт Python обычно запускается из командной строки или из среды разработки Python с указанием контекста вычисления SQL Server с помощью одной из функций **revoscalepy**. Удаленный контекст вычисления можно использовать для всего кода или для отдельных функций. Например, может потребоваться разгрузить обучение модели на сервер, чтобы работать с актуальными данными и исключить перемещение данных.

Когда вы будете готовы инкапсулировать скрипт Python в хранимую процедуру [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql), рекомендуется переписать код и оформить его в виде функции, которая содержит четко определенные входные и выходные данные. 

Входные и выходные данные должны быть кадрами данных **Pandas**. После этого вы сможете вызывать хранимую процедуру из любого клиента, который поддерживает T-SQL, без труда передавать запросы SQL в качестве входных данных и сохранять результаты в таблицах SQL. Пример см. в статье об [анализе данных с помощью Python для разработчиков SQL](../tutorials/sqldev-in-database-python-for-sql-developers.md).

### <a name="using-revoscalepy-with-microsoftml"></a>Использование revoscalepy с microsoftml

Функции Python для [microsoftml](ref-py-microsoftml.md) интегрированы с контекстами вычислений и источниками данных, предоставленными в revoscalepy. При вызове функций из microsoftml, например при определении и обучении модели, функции revoscalepy можно использовать для выполнения кода Python в локальной среде или в удаленном контексте вычисления SQL Server.

В следующем примере показан синтаксис импорта модулей в коде Python. Затем можно сослаться на нужные вам функции.

```python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

## <a name="see-also"></a>См. также раздел

+ [Учебники по Python](../tutorials/sql-server-python-tutorials.md)
+ [Руководство. Внедрение кода Python в T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Справочник по Python (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference)
