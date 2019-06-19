---
title: Ввод в эксплуатацию кода R с помощью хранимых процедур — службы машинного обучения SQL Server
description: Внедрите код на языке R в хранимую процедуру SQL Server чтобы сделать его доступным для любого клиентского приложения, имеющие доступ к базе данных SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/15/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 2d00e96162b492d28f0c0ec107612023c8e15e48
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62642028"
---
# <a name="operationalize-r-code-using-stored-procedures-in-sql-server-machine-learning-services"></a>Ввод в эксплуатацию кода R с помощью хранимых процедур в службах машинного обучения SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

При использовании функции R и Python в службах машинного обучения SQL Server, то наиболее распространенный подход к перемещению решения в рабочей среде — путем внедрения кода в хранимые процедуры. В этой статье перечислены ключевые моменты для разработчиков SQL, которые следует учитывать при ввод в эксплуатацию кода R с помощью SQL Server.

## <a name="deploy-production-ready-script-using-t-sql-and-stored-procedures"></a>Развернуть готовый к выпуску скрипт с помощью T-SQL и хранимых процедур

В большинстве случаев интеграции решения для обработки и анализа данных подразумевает обширной перекодирования для поддержки производительности и интеграции. Службы машинного обучения SQL Server упрощает эту задачу, поскольку код R и Python, которые могут выполняться в SQL Server и вызывать с помощью хранимых процедур. Дополнительные сведения о механизм внедрения кода в хранимые процедуры см. в разделе:

+ [Краткое руководство. R-сценарий «Hello world» в SQL Server](../../advanced-analytics/tutorials//quickstart-r-run-using-tsql.md)
+ [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)

Более подробный пример развертывание кода R в рабочей среде с помощью хранимых процедур можно найти в [руководства: Анализ данных R для разработчиков SQL](../../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md)

## <a name="guidelines-for-optimizing-r-code-for-sql"></a>Рекомендации по оптимизации кода R для SQl

Преобразование кода R в SQL проще в том случае, если заранее выполняются некоторые оптимизации в коде R или Python. К ним относятся, избегая типы данных, вызывающие проблемы, избегая ненужные преобразования данных и переписать код R как вызов одной функции, который легко параметризировать. Дополнительные сведения см. в разделе:

+ [Библиотеки и типы данных R](r-libraries-and-data-types.md)
+ [Преобразование кода R для использования в службах R](converting-r-code-for-use-in-sql-server.md)
+ [Использование вспомогательных функций sqlrutils](ref-r-sqlrutils.md)

## <a name="integrate-r-and-python-with-applications"></a>Интеграция R и Python с приложениями

Так как R или Python можно запустить из хранимой процедуры, можно выполнять скрипты из любого приложения, которое может отправлять инструкции T-SQL и обработки результатов. Например, может переобучить модель по расписанию с помощью [задачи Выполнение T-SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task) в службах Integration Services или с помощью другой планировщик заданий, могут выполнять хранимую процедуру.

Оценки — важная задача, которую можно легко автоматизировать, или к работе с внешними приложениями. Вы обучения модели, с помощью R или Python или хранимой процедуры, и [сохранить модель в двоичном формате](../tutorials/walkthrough-build-and-save-the-model.md) в таблицу. Затем модели можно загрузить в переменную как часть вызова хранимой процедуры, используя один из следующих вариантов для оценки из T-SQL:

+ [В реальном времени](../real-time-scoring.md) оценки, оптимизированный для небольшими пакетами
+ Однострочный оценки для вызова из приложения
+ [Собственная Оценка](../sql-native-scoring.md), для быстрой пакетной прогноза на основе SQL Server без вызова R

В этом пошаговом руководстве приведены примеры оценки с помощью хранимой процедуры в пакете и режимов одной строки.

+ [Сквозное шифрование Пошаговое руководство по обработке и анализу данных для R в SQL Server](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)

См. в статье эти шаблоны решений примеры того, как интегрировать оценки в приложении:

+ [Прогнозирование в розничной](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/RetailForecasting/Introduction.md)
+ [обнаружение мошенничества;](https://github.com/Microsoft/r-server-fraud-detection)
+ [Кластеризация клиента](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/r-services/getting-started/customer-clustering)

## <a name="boost-performance-and-scale"></a>Повышение производительности и масштабируемости

Несмотря на то, что открытый язык программирования R определенные ограничения в отношении больших наборов данных, [интерфейсы API пакета RevoScaleR](ref-r-revoscaler.md) состав службы машинного обучения SQL Server могут работать с большими наборами данных и использовать преимущества многопоточных , вычислений в базе данных в нескольких ядер и процессов.

Если решение R использует сложные агрегаты или большие наборы данных, можно использовать высокоэффективные в памяти агрегаты и индексы columnstore SQL Server и переложить на код R обработку статистических вычислений и оценки.

Дополнительные сведения о способах повышения производительности в SQL Server машинного обучения см. в разделе:

+ [Настройка производительности для служб R SQL Server](../../advanced-analytics/r/sql-server-r-services-performance-tuning.md)
+ [Советы по оптимизации производительности и рекомендации](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

## <a name="adapt-r-code-for-other-platforms-or-compute-contexts"></a>Контекста вычислений или адаптировать код R для других платформ

Тот же код R, который применяется к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данные могут использоваться для других источников данных, например Spark через HDFS, при использовании [вариант изолированного сервера](../install/sql-machine-learning-standalone-windows-install.md) в программу установки SQL Server или при установке продукта фирменной символикой отличные от SQL, Сервер машинного обучения Майкрософт (прежнее название — **Microsoft R Server**):

+ [Документация по машинному обучению сервера](https://docs.microsoft.com/r-server/)

+ [Изучите R RevoScaleR](https://docs.microsoft.com/r-server/r/tutorial-r-to-revoscaler)

+ [Писать алгоритмы фрагментации](https://docs.microsoft.com/r-server/r/how-to-developer-write-chunking-algorithms)

+ [Вычисления с большими данными в R](https://docs.microsoft.com/r-server/r/tutorial-large-data-tips)

+ [Разработка собственных параллельных алгоритмов](https://docs.microsoft.com/r-server/r-reference/revopemar/pemar)

