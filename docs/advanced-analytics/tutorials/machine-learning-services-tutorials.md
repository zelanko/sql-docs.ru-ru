---
title: SQL Server R и Python руководств - машинного обучения SQL Server
description: Примеры и руководства по R и Python, создание сценариев в службах машинного обучения SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/18/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 69009a5a11e7f7985729656ae9df6c60bcba8037
ms.sourcegitcommit: 33712a0587c1cdc90de6dada88d727f8623efd11
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2018
ms.locfileid: "53596935"
---
# <a name="sql-server-machine-learning-tutorials-in-r-and-python"></a>Руководства машинного обучения SQL Server в R и Python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье предоставляет полный список учебники и образцы кода, демонстрирующие машинного обучения функции [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md) или [SQL Server 2017 службы машинного обучения](../install/sql-machine-learning-services-windows-install.md). 

+ Краткие руководства используйте встроенные данные или данные не для быстрого просмотра с минимальными усилиями.
+ С дополнительные задачи, более крупных наборов данных и больше объяснения эластичными учебники.
+ Примеры и решения, для разработчиков, которые предпочитают начать с кодом, обходе в обратном направлении, основные понятия и уроки для восполнения пробелов базы знаний.

Вы узнаете, как использовать библиотеки R и Python с реляционными данными, находящихся в же контекст работы, как использовать хранимые процедуры SQL Server для запуска и развертывания пользовательского кода и как вызвать Microsoft R и библиотеки Python для данных высокой производительности Обработка и анализ и задач машинного обучения.

В качестве первого шага, просмотрите основные понятия резервного корпорации Майкрософт по интеграции R и Python с SQL Server.

## <a name="concepts"></a>Основные понятия

Аналитика в базе данных ссылается на встроенную поддержку для R и Python в SQL Server при установке службы машинного обучения SQL Server или SQL Server 2016 R Services (R) в качестве надстройки к компоненту database engine. Интеграция R и Python включает базового распределения с открытым исходным кодом, а также библиотеки Microsoft для высокопроизводительного анализа.

С точки stand архитектуры ваш код выполняется как внешний процесс в окне, чтобы сохранить целостность компонента database engine. Тем не менее для доступа к данным и безопасности через роли базы данных SQL Server и разрешений, который означает, что любое приложение с доступом к SQL Server имеют доступ к скрипта R и Python при развернуть его в качестве хранимой процедуры, или сериализации и сохранения обученной модели для SQL База данных сервера.

Основные различия между R и Python поддерживают SQL Server и эквивалентные языковой поддержке в других продуктов корпорации Майкрософт и службы включают в себя:

+ Возможность «пакет» кода в хранимых процедурах или как двоичные модели.
+ Написание кода, вызывающего библиотеки Microsoft R и Python, установить локально вместе с файлы программы SQL Server.
+ Архитектура безопасности базы данных SQL Server применяются к решений R и Python.
+ Используйте инфраструктуру SQL Server, а также Административная поддержка для пользовательских решений.

## <a name="quickstarts"></a>Краткие руководства

Начните здесь узнать, как запустить R или Python из T-SQL и как ввести в эксплуатацию кода R и Python для рабочей среды SQL.

+ [Python. Запустите Python, с помощью T-SQL](run-python-using-t-sql.md)
+ [R: Hello World в R и SQL.](rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [R: Обрабатывать входные и выходные данные](rtsql-working-with-inputs-and-outputs.md)
+ [R: Обработка типов данных и объектов](rtsql-r-and-sql-data-types-and-data-objects.md)
+ [R: Использование функций R](rtsql-using-r-functions-with-sql-server-data.md)
+ [R: Создание модели прогнозирования](rtsql-create-a-predictive-model-r.md)
+ [R: Predict and plot из модели и](rtsql-predict-and-plot-from-model.md)

## <a name="tutorials"></a>Учебники

Построение на ваш первый опыт работы с R и Python и T-SQL, используя более подробно рассмотрим пакеты корпорации Майкрософт и более специализированные операции, например перехода от локального контексты удаленных вычислений.

+ [Учебники по Python](sql-server-python-tutorials.md)
+ [Учебники по R](sql-server-r-tutorials.md)

<a name ="bkmk_samples"></a>

## <a name="samples"></a>Примеры

Эти примеры и образцы, предоставляемые группой разработки SQL Server и R Server особенно пристально, внедренной аналитики можно использовать в реальных приложениях.

| Ссылка | Описание | 
|------|-------------|
| [Выполнение клиента кластеризации с помощью R и SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/customerclustering/) | Используйте неконтролируемого обучения для сегментирования потребителей на основе данных о продажах. В этом примере используется алгоритм масштабируемой rxKmeans из Microsoft R для построения модели кластеризации. |
| [Выполнение клиента кластеризации с помощью Python и SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/) | Узнайте, как использовать алгоритм методом k-средних для выполнения без учителя кластеризации клиентов. В этом примере используется Python языка в базе данных.| SQL Server 2017 |
| [Создание прогнозной модели с помощью R и SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction) | Узнайте, как ski использование машинного обучения для прогнозирования будущих проката, что позволяет бизнес-плана и сотрудников для удовлетворения будущего спроса. В этом примере используются алгоритмы Майкрософт для создания модели логистической регрессии и модели дерева принятия решений. | 
| [Создание прогнозной модели с помощью Python и SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/) | Построено ski аренды анализа с помощью Python, которые помогут в планировании для будущего спроса. В этом примере использует новую библиотеку Python, **revoscalepy**, для создания модели линейной регрессии. | 
| [Как использовать Tableau со службами машинного обучения SQL Server](https://blogs.msdn.microsoft.com/mlserver/2017/12/14/how-to-use-tableau-with-sql-server-machine-learning-services-with-r-and-python/) | Анализ социальных и создание диаграмм Tableau, с помощью SQL Server и R. | 

<a name="bkmk_solutions"></a>

## <a name="solution-templates"></a>Шаблоны решений

Команды обработки и анализа данных Microsoft предоставила шаблоны настраиваемых решений, которые могут быть использованы для быстрого решения для распространенных сценариев. Каждое решение предназначена для решения конкретной задачи или отрасли проблемы. Большую часть решений предназначены для работы в SQL Server или в облачной среде, такие как машинное обучение Azure. Другие решения можно запустить на платформе Linux или в кластерах Hadoop или Spark, с помощью Microsoft R Server или сервер машинного обучения.

Предоставляется весь код, а также инструкции о том, как обучать и развертывать модели для оценки с помощью хранимых процедур SQL Server.

+ [обнаружение мошенничества;](https://gallery.cortanaanalytics.com/Tutorial/Online-Fraud-Detection-Template-with-SQL-Server-R-Services-1)
+ [прогнозирование ухода клиентов;](https://gallery.cortanaanalytics.com/Tutorial/Customer-Churn-Prediction-Template-with-SQL-Server-R-Services-1)
+ [профилактическое обслуживание.](https://gallery.cortanaanalytics.com/Tutorial/Predictive-Maintenance-Template-with-SQL-Server-R-Services-1)
+ [Спрогнозировать продолжительность госпитализации в больнице](https://gallery.cortanaintelligence.com/Solution/Predicting-Length-of-Stay-in-Hospitals-1)

Дополнительные сведения см. на странице [Шаблоны машинного обучения для служб SQL Server 2016 R Services](https://blogs.technet.microsoft.com/machinelearning/2016/03/23/machine-learning-templates-with-sql-server-2016-r-services/).

