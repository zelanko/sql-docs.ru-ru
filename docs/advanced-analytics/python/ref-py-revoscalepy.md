---
title: пакет Python revoscalepy - службы машинного обучения SQL Server
description: Общие сведения о модуле revoscalepy в службах SQL Server 2017 машинного обучения с помощью Python.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/12/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: e0cded793f6017398641ffa055deec62010b2b3d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62642460"
---
# <a name="revoscalepy-python-module-in-sql-server"></a>revoscalepy (модуль Python в SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**revoscalepy** — это модуль совместимые Python35 от Майкрософт, которая поддерживает распределенные вычисления, удаленные контексты вычисления и алгоритмы обработки и анализа данных с высокой производительностью. Он основан на **RevoScaleR** пакета для R (в состав Microsoft R Server и SQL Server R Services), предлагая аналогичные функциональные возможности:

+ Локальная и удаленная вычислительных контекстов в системах, где та же версия **revoscalepy**
+ Функции преобразования и визуализации данных
+ Функции обработки и анализа данных, масштабируемые через распределенные или параллельной обработкой
+ Повышения производительности, включая использование библиотеки Intel math

Источники данных и контекстов вычисления, создаваемые в **revoscalepy** также может использоваться в алгоритмах машинного обучения. Введение в эти алгоритмы, см. в разделе [microsoftml модуль Python в SQL Server](ref-py-microsoftml.md).

## <a name="full-reference-documentation"></a>Полная справочная документация

**Revoscalepy** library распространяется в нескольких продуктов корпорации Microsoft, но использование совпадает ли вы получаете библиотеки в SQL Server или другой продукт. Так как функции являются одинаковыми, [документации для отдельных revoscalepy функций](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) публикуется только в одном месте в разделе [Справочник по Python](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) для сервера машинного обучения Майкрософт. Следует любого конкретного продукта существует поведения, несоответствия будут указаны в странице справки по функции.

## <a name="versions-and-platforms"></a>Версии и платформы

**Revoscalepy** модуль исходя из Python 3.5 и доступны только в том случае, если устанавливается одно из следующих продуктов корпорации Майкрософт или файлы для загрузки:

+ [SQL Server 2017 службы машинного обучения](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 или более поздней версии](https://docs.microsoft.com/machine-learning-server/)
+ [Клиентские библиотеки Python для клиента обработки и анализа данных](setup-python-client-tools-sql.md)

> [!NOTE]
> Версии выпуска полной версии продукта: только для Windows, для начиная с SQL Server 2017. Поддержка Linux **revoscalepy** возможности [предварительной версии SQL Server 2019](../../linux/sql-server-linux-setup-machine-learning.md).

## <a name="functions-by-category"></a>Функции по категориям

В этом разделе перечислены функции по категориям дать вам представление о том, как используется каждый из них. Можно также использовать [оглавление](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) следует выполнять поиск функций в алфавитном порядке.

## <a name="1-data-source-and-compute"></a>Источник данных 1 и вычислительные ресурсы

**revoscalepy** включает функции для создания источников данных и задание расположения, или *контекста вычислений*, из которых вычисления выполняются. В следующей таблице перечислены функции, относящиеся к сценариев SQL Server.

SQL Server и Python используют разные типы данных в некоторых случаях. Список сопоставлений типов данных SQL и Python, см. в разделе [типы данных Python-to-SQL](python-libraries-and-data-types.md).

| Компонент| Описание|
| ------- | ---------- |
| [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver) |  Создайте объект контекста вычислений SQL Server для принудительной отправки вычислений на удаленном экземпляре. Несколько **revoscalepy** функции принимают контекст вычислений в качестве аргумента. Пример переключения контекста, см. в разделе [создать модель с помощью revoscalepy](../tutorials/use-python-revoscalepy-to-create-model.md).|
| [RxSqlServerData](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxsqlserverdata) | Создайте объект данных, на основе запроса SQL Server или таблицы. |
| [RxOdbcData](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxodbcdata)| Создайте источник данных, на основе соединения ODBC. |
| [RxXdfData](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxxdfdata) | Создайте источник данных, основанный на локальный файл XDF. Файлы XDF часто используются для передачи данных в памяти на диск. Файл XDF можно использовать при работе с больше данных, чем может быть перемещена из базы данных в одном пакете, или больше данных, чем может поместиться в памяти. Например если вам приходится часто перемещать большие объемы данных из базы данных на локальную рабочую станцию, вместо того чтобы запрос базы данных несколько раз для каждой операции R, вы можно использовать xdf-файл как своего рода кэша чтобы сохранить данные локально и затем работать с ними в рабочем пространстве R. |

> [!TIP]
> Если вы не знакомы с идея источников данных или контекстов вычислений, мы рекомендуем начать с [распределенные вычисления](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing) в документации по Microsoft Machine Learning Server.

## <a name="2-data-manipulation-etl"></a>2-управление данными (ETL)

| Компонент | Описание |
|----------|-------------|
|[rx_import](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-import) | Импорт данных в xdf-файл или данные кадра.|
|[rx_data_step](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-data-step) | Преобразуйте данные из входного набора данных в выходной набор данных.|

<a name="bkmk_algorithms"></a>

## <a name="3-training-and-summarization"></a>3-обучение и формирование сводных данных

| Компонент| Описание|
| ------- | ---------- |
|[rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees) | Вписать стохастического градиента повышенных деревьев принятия решений|
|[rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest) | Вписать классификации и регрессии леса принятия решений|
|[rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree) | Вписать деревьев классификации и регрессии |
|[rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod) | создание модели линейной регрессии;|
|[rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit) | создание модели логистической регрессии;|
|[rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary) | Создания сводки одномерное объектов в revoscalepy.|

Следует также просмотреть функций в [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) для дополнительных подходах к.

<a name="ml-scoring"></a>

## <a name="4-scoring-functions"></a>Функции с оценкой 4

| Компонент| Описание|
| ------- | ---------- |
| [rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict) | Создание прогнозов из обученной модели|) | Создает прогнозы на основе обученной модели и может использоваться для оценки в реальном времени. |
|[rx_predict_default](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict-default) | Вычисляет прогнозируемые значения и использование объектов rx_lin_mod и rx_logit остатки. |
|[rx_predict_rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict-rx-dforest) | Вычисляет прогнозируемые или соединяются гладкой значения для набора данных из объекта rx_dforest или rx_btrees. |
|[rx_predict_rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict-rx-dtree) | Вычисляет прогнозируемые или соединяются гладкой значения для набора данных из объекта rx_dtree. |

## <a name="how-to-work-with-revoscalepy"></a>Как работать с помощью revoscalepy

Функции в **revoscalepy** можно вызывать в коде Python, инкапсулируются в хранимых процедурах. Большинство разработчиков создавать **revoscalepy** решения локально, и затем перенести готовый код Python с хранимыми процедурами в качестве упражнения развертывания.

При локальном запуске вы обычно выполнение скрипта Python из командной строки или из среды разработки Python и укажите контекст вычислений SQL Server с помощью одного из **revoscalepy** функции. Контекст удаленных вычислений можно использовать для весь код, или для отдельных функций. Например можно разгрузить Обучение модели на сервер, чтобы использовать последние данные и избежать перемещения данных.

Когда будете готовы для инкапсуляции скрипт Python внутри хранимой процедуры, [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql), рекомендуется переписать код как одну функцию, которая четко определенные входные и выходные данные. 

Входные и выходные данные должны быть **pandas** кадров данных. Если это сделано, можно вызвать хранимую процедуру из любого клиента, поддерживающего T-SQL, легко передать SQL-запросов в качестве входных данных и сохранить результаты в таблицы SQL. Например, см. в разделе [дополнительные аналитические функции Python в базе данных для разработчиков SQL](../tutorials/sqldev-in-database-python-for-sql-developers.md).

### <a name="using-revoscalepy-with-microsoftml"></a>С помощью revoscalepy с microsoftml

Функции Python для [microsoftml](ref-py-microsoftml.md) интегрированы с вычислительных контекстов и источниками данных, предоставляемых в revoscalepy. При вызове функций из microsoftml, например при определении и обучения модели, использовать revoscalepy функции для выполнения Python коде либо локально или в SQl Server удаленного контекста вычислений.

В следующем примере показан синтаксис для импорта модулей в коде Python. Затем можно ссылаться на отдельные функции, которые вам нужны.

```python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

## <a name="see-also"></a>См. также

+ [Учебники по Python](../tutorials/sql-server-python-tutorials.md)
+ [Учебник. Внедрение кода Python в T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Справочник по Python (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference)
