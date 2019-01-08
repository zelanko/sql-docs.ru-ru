---
title: Ввод в эксплуатацию кода R с помощью хранимых процедур — службы машинного обучения SQL Server
description: Внедрите код на языке R в хранимую процедуру SQL Server чтобы сделать его доступным для любого клиентского приложения, имеющие доступ к базе данных SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 3fc96e57fffb3e000a7e1a19887ed27651df9009
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2018
ms.locfileid: "53432187"
---
# <a name="operationalize-r-code-machine-learning-services"></a>Ввод в эксплуатацию кода R (служб машинного обучения)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Разработчикам баз данных необходимо интегрировать несколько технологий и объединить результаты, чтобы их можно было совместно использовать на всем предприятии. Разработчик базы данных работает с разработчикам приложений, SQL разработчиков и специалистов по анализу данных для разработки и развертывания решений.

В этой статье перечислены основные моменты, разработчик базы данных, которые следует учитывать при ввод в эксплуатацию кода R с помощью SQL Server.

## <a name="get-started-with-r-code-in-sql-server"></a>Начало работы с кодом R в SQL Server

В большинстве случаев интеграции решения машинного обучения подразумевает обширной перекодирования для поддержки производительности и интеграции. Тем не менее при перемещении кода R и Python в рабочей среде гораздо проще в службах для машинного обучения SQL Server, так как код может выполняться в SQL Server и вызывать с помощью хранимых процедур. Можно продолжать использовать знакомые средства и не требуется устанавливать среду разработки R. 

Дополнительные сведения о базовом синтаксисе см. в разделе:

+ [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)
+ [Использование кода R в SQL](../../advanced-analytics/tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md).

Пример того, как можно развернуть код R в рабочей среде с помощью хранимых процедур см. в разделе:

+ [В базе данных аналитики для разработчиков SQL](../../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md).

## <a name="optimize-your-r-code"></a>Оптимизировать код R

Само собой преобразование кода R в SQL будет проще, если заранее выполняются некоторые оптимизации в коде R или Python. К ним относятся, избегая типы данных, вызывающие проблемы, избегая ненужные преобразования данных и переписать код R как вызов одной функции, который легко параметризировать. Дополнительные сведения см. в разделе:

+ [Библиотеки и типы данных R](r-libraries-and-data-types.md)

+ [Преобразование кода R для использования в службах R](converting-r-code-for-use-in-sql-server.md)

+ [Использование вспомогательных функций sqlrutils](ref-r-sqlrutils.md)

## <a name="integrate-r-and-python-with-applications"></a>Интеграция R и Python с приложениями

Так как службы машинного обучения можно запустить из хранимой процедуры, можно выполнять скрипты R или Python из любого приложения, которое может отправлять инструкции T-SQL и обрабатывать результаты.

Например можно переобучить модель по расписанию, используя задачу «Выполнение T-SQL» в службах Integration Services или с помощью другой планировщик заданий, могут выполнять хранимую процедуру.

Оценки — важная задача, которую можно легко автоматизировать, или к работе с внешними приложениями. Обучить модель, с помощью R или Python или хранимой процедуры и сохранить модель в двоичном формате в таблицу. Затем модели можно загрузить в переменную как часть вызова хранимой процедуры, используя один из следующих вариантов для оценки из T-SQL:

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

Хотя язык R с открытым кодом имеет ограничения, пакет RevoScaleR API-интерфейсы могут работать с большими наборами данных и использовать преимущества многопоточных, многоядерных многопроцессных вычислений в базе данных.

Если решение R использует сложные агрегаты или большие наборы данных, можно использовать высокоэффективные в памяти агрегаты и индексы columnstore SQL Server и переложить на код R обработку статистических вычислений и оценки.

Дополнительные сведения о способах повышения производительности в SQL Server машинного обучения см. в разделе:

+ [Настройка производительности для служб R SQL Server](../../advanced-analytics/r/sql-server-r-services-performance-tuning.md)
+ [Советы по оптимизации производительности и рекомендации](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

## <a name="adapt-r-code-for-other-platforms-or-compute-contexts"></a>Контекста вычислений или адаптировать код R для других платформ

Тот же код R, который применяется к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данных может использоваться для других источников данных, таких как Hadoop и в других контекстах вычислений.

Дополнительные сведения о платформах, поддерживаемых Microsoft R см. в разделе:

+ [Введение в Microsoft R](https://docs.microsoft.com/r-server/)

+ [Изучите RevoScaleR](https://docs.microsoft.com/r-server/r/tutorial-r-to-revoscaler)

Дополнительные сведения о том, как можно оптимизировать Ваши решения для работы в больших объемов данных или на нескольких платформах с Microsoft R см. в разделе:

+ [Писать алгоритмы фрагментации](https://docs.microsoft.com/r-server/r/how-to-developer-write-chunking-algorithms)

+ [Вычисления с большими данными в R](https://docs.microsoft.com/r-server/r/tutorial-large-data-tips)

+ [Разработка собственных параллельных алгоритмов](https://docs.microsoft.com/r-server/r-reference/revopemar/pemar)

