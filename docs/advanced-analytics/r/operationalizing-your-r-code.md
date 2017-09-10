---
title: "Ввода в эксплуатацию кода R (Machine Services обучения) | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/26/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f15696b1-2479-4e5f-ac5e-4beaf958a043
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d858352ed7dc519dfde9f625ea24cea6a538be5b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="operationalize-r-code-machine-learning-services"></a>Ввода в эксплуатацию кода R (обучения Machine Services)

Разработчикам баз данных необходимо интегрировать несколько технологий и объединить результаты, чтобы их можно было совместно использовать на всем предприятии. Разработчик базы данных работает с разработчикам приложений, разработчиками SQL и специалистами по анализу данных для разработки и развертывания решений.

В этой статье перечислены ключевые моменты для разработчик базы данных, которые следует учитывать при ввод в эксплуатацию кода R с помощью SQL Server.

## <a name="get-started-with-r-code-in-sql-server"></a>Приступая к работе с код R в SQL Server

В большинстве случаев интеграцию машины обучению означало широко запись для поддержки интеграции и производительности. Тем не менее перемещение кода Python и R в рабочей среде гораздо проще в службах обучения Майкрософт машины, поскольку код может выполняться в SQL Server и вызывать с помощью хранимых процедур. Можно продолжать использовать знакомые средства и не требуется устанавливать среду разработки R. 

Дополнительные сведения о базовом синтаксисе см. в разделе:

+ [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)
+ [С помощью кода R в SQL](../../advanced-analytics/tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md).

Пример развертывание кода R в рабочей среде с помощью хранимых процедур см. в разделе:

+ [В базе данных анализа для разработчиков SQL](../../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md).

## <a name="optimize-your-r-code"></a>Оптимизировать код R

Конечно преобразование кода R в SQL будет проще, если заранее выполняются некоторые оптимизации в коде R или Python. К ним относятся Предотвращение типы данных, вызывающие проблемы, как избежать ненужные преобразования данных и переработке кода R как один вызов функции, могут быть параметризованы легко. Дополнительные сведения см. в разделе:

+ [R библиотек и типы данных](r-libraries-and-data-types.md)

+ [Преобразование кода R для использования служб R](converting-r-code-for-use-in-sql-server.md)

+ [Создание R хранимой процедуры с помощью sqlrutils](generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)

## <a name="integrate-r-and-python-with-applications"></a>Интеграция R и Python с приложениями

Поскольку службы обучения машину можно запустить из хранимой процедуры, вы можете выполнять сценарии R или Python из любого приложения, которое может отправлять инструкции T-SQL и обработки результатов.

Например вы Обучение модели по расписанию, используя задачу «Выполнение T-SQL» в службах Integration Services или с помощью другого планировщика заданий, могут выполнять хранимую процедуру.

Оценки является важной задачей, можно легко автоматизировать или работы с внешними приложениями. Обучение модели, с помощью R или Python или хранимая процедура и сохраните модель в двоичном формате в таблицу. Затем модели можно загрузить в переменную как часть вызова хранимой процедуры, используя один из следующих вариантов для оценки из T-SQL:

+ [В реальном времени](../real-time-scoring.md) оценки, оптимизированный для небольших пакетов
+ Однострочный оценки для вызова из приложения
+ [Оценки собственного](../sql-native-scoring.md), для быстрого пакетный прогноз из SQL Server без вызова R

В этом пошаговом руководстве приведены примеры оценки с помощью хранимой процедуры в пакете и режимов одной строки.

+ [Сквозной Пошаговое руководство для обработки и анализа данных для R в SQL Server](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)

Видеть эти шаблоны решений примеры интеграции оценки в приложении:

+ [Прогнозирование розничных продаж](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/RetailForecasting/Introduction.md)
+ [Мошенничества](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/FraudDetection/Introduction.md)
+ [Кластеризация клиента](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/r-services/getting-started/customer-clustering)

## <a name="boost-performance-and-scale"></a>Повышение производительности и масштабируемости

Хотя язык R с открытым кодом имеет ограничения, пакет RevoScaleR API-интерфейсы могут работать с большими наборами данных и использовать преимущества многопоточных, многоядерных несколькими процессами вычислений в базе данных.

Если решение R использует сложные агрегаты или большие наборы данных, можно использовать высокоэффективные в памяти агрегаты и индексы columnstore SQL Server и программный код R обработку статистических вычислений и оценки.

Дополнительные сведения о способах повышения производительности в SQL Server машинного обучения см. в разделе:

+ [Настройка производительности для SQL Server R Services](../../advanced-analytics/r/sql-server-r-services-performance-tuning.md)
+ [Советы по оптимизации производительности и рекомендации](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

## <a name="adapt-r-code-for-other-platforms-or-compute-contexts"></a>Адаптировать код R для других платформ или контекстов вычислений

Один и тот же код R, выполнить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данных может использоваться для других источников данных, таких как Hadoop и в других контекстов вычислений.

Дополнительные сведения о платформах, поддерживаемых в Microsoft R см. в разделе:

+ [Общие сведения о Microsoft R](https://docs.microsoft.com/r-server/)

+ [Просмотр RevoScaleR](https://docs.microsoft.com/r-server/r/tutorial-r-to-revoscaler)

Дополнительные сведения о том, как можно оптимизировать решениях Microsoft R для запуска на большие объемы данных или нескольких платформ см.:

+ [Запись фрагментации алгоритмы](https://docs.microsoft.com/r-server/r/how-to-developer-write-chunking-algorithms)

+ [Вычисления с большими данными в R](https://docs.microsoft.com/r-server/r/tutorial-large-data-tips)

+ [Разработка собственных параллельных алгоритмов](https://docs.microsoft.com/r-server/r-reference/revopemar/pemar)


