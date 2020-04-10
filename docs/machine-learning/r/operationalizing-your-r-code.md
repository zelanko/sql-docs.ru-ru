---
title: Развертывание кода на языке R в хранимых процедурах
description: Внедрите код R в хранимую процедуру SQL Server, чтобы сделать его доступным для любого клиентского приложения, имеющего доступ к базе данных SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/15/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: ebca30560a437cc8c95b9604cc24fbd7542c9d85
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2020
ms.locfileid: "81117587"
---
# <a name="operationalize-r-code-using-stored-procedures-in-sql-server-machine-learning-services"></a>Использование кода R с хранимыми процедурами в Службах машинного обучения SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

При использовании функций R и Python в Службах машинного обучения SQL Server наиболее распространенный подход к переносу решений в рабочую среду — внедрение кода в хранимые процедуры. В этой статье перечислены ключевые моменты, которые необходимо учитывать разработчику на SQL при вводе кода R в эксплуатацию с помощью SQL Server.

## <a name="deploy-production-ready-script-using-t-sql-and-stored-procedures"></a>Развертывание готового к использованию скрипта с помощью T-SQL и хранимых процедур

Интеграция решений для обработки и анализа данных обычно предполагает значительную переработку кода для обеспечения производительности и интеграции. Службы машинного обучения SQL Server упрощают эту задачу, так как код R и Python можно выполнять в SQL Server и вызывать с помощью хранимых процедур. Дополнительные сведения о механизме внедрения кода в хранимые процедуры см. в следующих статьях:

+ [Создание и выполнение простых скриптов R в SQL Server](../tutorials/quickstart-r-create-script.md)
+ [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)

Более полный пример развертывания кода R в рабочей среде с помощью хранимых процедур можно найти в [руководстве по аналитике данных R для разработчиков SQL](../../machine-learning/tutorials/sqldev-in-database-r-for-sql-developers.md).

## <a name="guidelines-for-optimizing-r-code-for-sql"></a>Рекомендации по оптимизации кода R для SQL

Преобразовывать код R в SQL проще, если предварительно произвести некоторые оптимизации. К ним относятся исключение типов данных, вызывающих проблемы, предотвращение ненужных преобразований данных и переработка кода R в один вызов функции, который можно легко параметризировать. Дополнительные сведения см. в разделе:

+ [Библиотеки и типы данных R](r-libraries-and-data-types.md)
+ [Преобразование кода на языке R для использования в службах R](converting-r-code-for-use-in-sql-server.md)
+ [Использование вспомогательных функций sqlrutils](ref-r-sqlrutils.md)

## <a name="integrate-r-and-python-with-applications"></a>Интеграция кода R и Python с приложениями

Так как код R или Python можно запускать из хранимой процедуры, скрипты можно выполнять из любого приложения, которое может отправить инструкцию T-SQL и обработать результаты. Например, можно переобучать модель по расписанию с помощью задачи [Выполнение скрипта T-SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task) в Integration Services или с помощью другого планировщика заданий, который может выполнять хранимую процедуру.

Оценка — одна из важных задач, которую можно легко автоматизировать или запускать из внешних приложений. Модель предварительно обучается с помощью кода R или Python либо хранимой процедуры, а затем [сохраняется в двоичном формате](../tutorials/walkthrough-build-and-save-the-model.md) в таблице. После этого модель можно загрузить в переменную в процессе вызова хранимой процедуры и использовать один из следующих способов оценки в T-SQL:

+ оценка в реальном времени, оптимизированная для небольших пакетов;
+ оценка одной строки для вызова из приложения;
+ [собственная оценка](../sql-native-scoring.md) для быстрого пакетного прогнозирования из SQL Server без вызова R.

В этом пошаговом руководстве приведены примеры оценки с помощью хранимой процедуры как в пакетном, так и в построчном режиме:

+ [Полное пошаговое руководство по обработке и анализу данных с помощью R в SQL Server](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)

Примеры интеграции оценки в приложение см. в следующих шаблонах решений:

+ [прогнозирование розничной торговли;](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/RetailForecasting/Introduction.md)
+ [обнаружение мошенничества;](https://github.com/Microsoft/r-server-fraud-detection)
+ [кластеризация клиентов.](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/r-services/getting-started/customer-clustering)

## <a name="boost-performance-and-scale"></a>Повышение производительности и масштабируемости

Хотя язык R с открытым кодом имеет ограничения, связанные с большими наборами данных, [интерфейсы API пакета RevoScaleR](ref-r-revoscaler.md), входящие в состав Служб машинного обучения SQL Server, могут работать с большими наборами данных и использовать преимущества многопоточных, многоядерных вычислений в базе данных в нескольких процессах.

Если решение R использует сложные агрегаты или включает в себя большие наборы данных, можно использовать высокоэффективные хранящиеся в памяти агрегаты и индексы columnstore SQL Server и переложить на код R обработку статистических вычислений и оценок.

Дополнительные сведения о повышении производительности в службе машинного обучения SQL Server см. в следующих статьях:

+ [Настройка производительности служб R SQL Server](../../machine-learning/r/sql-server-r-services-performance-tuning.md)
+ [Советы и рекомендации по оптимизации производительности](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

## <a name="adapt-r-code-for-other-platforms-or-compute-contexts"></a>Адаптация кода R для других платформ или контекстов вычисления

Один и тот же код R, который применяется к данным [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], можно использовать повторно для других источников данных, например Spark на базе HDFS, если выбрать [изолированный сервер](../install/sql-machine-learning-standalone-windows-install.md) в программе установки SQL Server или установить сервер Microsoft Machine Learning Server (прежнее название — **Microsoft R Server**):

+ [Документация по Machine Learning Server](https://docs.microsoft.com/r-server/)

+ [Знакомство с R и RevoScaleR](https://docs.microsoft.com/r-server/r/tutorial-r-to-revoscaler)

+ [Создание алгоритмов фрагментации](https://docs.microsoft.com/r-server/r/how-to-developer-write-chunking-algorithms)

+ [Вычисления с большими данными в R](https://docs.microsoft.com/r-server/r/tutorial-large-data-tips)

+ [Разработка собственного параллельного алгоритма](https://docs.microsoft.com/r-server/r-reference/revopemar/pemar)

