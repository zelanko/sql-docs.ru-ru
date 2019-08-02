---
title: Эксплуатацию код R с помощью хранимых процедур
description: Внедрите код языка R в SQL Server хранимую процедуру, чтобы сделать ее доступной для любого клиентского приложения, имеющего доступ к базе данных SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/15/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: adcac48bc7d90aae5f05a9b671f05e34cc8cf554
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715684"
---
# <a name="operationalize-r-code-using-stored-procedures-in-sql-server-machine-learning-services"></a>Эксплуатацию код R с помощью хранимых процедур в SQL Server Службы машинного обучения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

При использовании функций R и Python в SQL Server Службы машинного обучения наиболее распространенным подходом к перемещению решений в рабочую среду является внедрение кода в хранимые процедуры. В этой статье перечислены ключевые моменты, которые необходимо учитывать разработчику SQL при эксплуатациюии кода R с помощью SQL Server.

## <a name="deploy-production-ready-script-using-t-sql-and-stored-procedures"></a>Развертывание готового к использованию скрипта с помощью T-SQL и хранимых процедур

Традиционно интеграция решений обработки и анализа данных призвана значительно переписать код для поддержки производительности и интеграции. SQL Server Службы машинного обучения упрощает эту задачу, так как код R и Python можно выполнять в SQL Server и вызывать с помощью хранимых процедур. Дополнительные сведения о механизме внедрения кода в хранимых процедурах см. в следующих статьях:

+ [QuickStart Скрипт R "Hello World" в SQL Server](../../advanced-analytics/tutorials//quickstart-r-run-using-tsql.md)
+ [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)

Более полный пример развертывания кода R в рабочей среде с помощью хранимых процедур можно найти в [учебнике: Аналитика данных R для разработчиков SQL](../../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md)

## <a name="guidelines-for-optimizing-r-code-for-sql"></a>Рекомендации по оптимизации кода R для SQl

Преобразование кода R в SQL упрощается, если некоторые оптимизации выполняются заранее в коде R или Python. Они включают в себя предотвращение типов данных, вызывающих проблемы, предотвращение ненужных преобразований данных и перезапись кода R в виде единого вызова функции, который можно легко задействовать. Дополнительные сведения см. в разделе:

+ [Библиотеки и типы данных R](r-libraries-and-data-types.md)
+ [Преобразование кода R для использования в службах R](converting-r-code-for-use-in-sql-server.md)
+ [Использование вспомогательных функций sqlrutils](ref-r-sqlrutils.md)

## <a name="integrate-r-and-python-with-applications"></a>Интеграция R и Python с приложениями

Поскольку R или Python можно запускать из хранимой процедуры, можно выполнять сценарии из любого приложения, которое может отправить инструкцию T-SQL и обработать результаты. Например, можно переучить модель по расписанию с помощью [задачи «Выполнение T-SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task) » в Integration Services или с помощью другого планировщика заданий, который может выполнять хранимую процедуру.

Оценка — это важная задача, которую можно легко автоматизировать или запустить из внешних приложений. Сначала обучить модель с помощью языка R или Python или хранимой процедуры, а затем [Сохраните модель в двоичном формате](../tutorials/walkthrough-build-and-save-the-model.md) в таблице. Затем модель может быть загружена в переменную как часть вызова хранимой процедуры с использованием одного из следующих параметров для оценки из T-SQL:

+ [Оценка в реальном времени, оптимизированная для небольших пакетов
+ Оценка одной строки для вызова из приложения
+ [Собственная оценка](../sql-native-scoring.md)для быстрого прогнозирования пакетов от SQL Server без вызова R

В этом пошаговом руководстве приведены примеры оценки с помощью хранимой процедуры в режиме пакетной обработки и одной строки:

+ [Сквозное пошаговое руководство по обработке и анализу данных для R в SQL Server](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)

Примеры интеграции оценки в приложение см. в этих шаблонах решений:

+ [Прогнозирование розничной торговли](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/RetailForecasting/Introduction.md)
+ [обнаружение мошенничества;](https://github.com/Microsoft/r-server-fraud-detection)
+ [Кластеризация клиентов](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/r-services/getting-started/customer-clustering)

## <a name="boost-performance-and-scale"></a>Повышение производительности и масштабируемости

Хотя язык R с открытым исходным кодом обладает известными ограничениями на большие наборы данных, [интерфейсы API пакета RevoScaleR](ref-r-revoscaler.md) , включенные в службу SQL Server машинное обучение, могут выполнять операции с большими наборами и преимуществами многопоточных, многоядерных Многопроцессные вычисления в базе данных.

Если решение R использует сложные агрегаты или содержит большие наборы данных, можно использовать высокоэффективные статистические выражения в памяти и индексы columnstore SQL Server, а также разрешить коду R обработку статистических вычислений и оценок.

Дополнительные сведения о том, как повысить производительность в SQL Server Машинное обучение, см. в следующих статьях:

+ [Настройка производительности для SQL Server R Services](../../advanced-analytics/r/sql-server-r-services-performance-tuning.md)
+ [Советы и рекомендации по оптимизации производительности](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

## <a name="adapt-r-code-for-other-platforms-or-compute-contexts"></a>Адаптация кода R для других платформ или контекстов вычислений

Тот же код R, который выполняется с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данными, можно использовать для других источников данных, например Spark через HDFS, при использовании [отдельного сервера](../install/sql-machine-learning-standalone-windows-install.md) в SQL Server установки или при установке продукта, не являющегося фирменным, Microsoft машинное обучение Сервер (прежнее название — **Microsoft R Server**):

+ [Документация по Machine Learning Server](https://docs.microsoft.com/r-server/)

+ [Знакомство с R и RevoScaleR](https://docs.microsoft.com/r-server/r/tutorial-r-to-revoscaler)

+ [Создание алгоритмов фрагментации](https://docs.microsoft.com/r-server/r/how-to-developer-write-chunking-algorithms)

+ [Вычисления с большими данными в R](https://docs.microsoft.com/r-server/r/tutorial-large-data-tips)

+ [Разработка собственного параллельного алгоритма](https://docs.microsoft.com/r-server/r-reference/revopemar/pemar)

