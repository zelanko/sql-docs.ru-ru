---
title: Машинного обучения учебники по службам SQL Server | Документация Майкрософт
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/22/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 08528f3459022bdcb97b97e22d6f6c474c31a715
ms.sourcegitcommit: eddf8cede905d2adb3468d00220a347acd31ae8d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/24/2018
ms.locfileid: "49960748"
---
# <a name="tutorials-for-sql-server-machine-learning-services"></a>Учебники для служб машинного обучения SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье предоставляет полный список руководств, видеороликов и примеров приложений, использующих функции машинного обучения в SQL Server 2016 или SQL Server 2017. Начните здесь узнать, как для запуска R или Python с T-SQL, как для использования удаленных и локальных вычислительных контекстов и как ввести в эксплуатацию кода R и Python для рабочей среды SQL.

+ [Учебники по Python](../tutorials/sql-server-python-tutorials.md)

+ [Учебники по R](../tutorials/sql-server-r-tutorials.md)

## <a name ="bkmk_samples"></a>Примеры R и Python

Эти примеры и образцы, предоставляемые группой разработки SQL Server и R Server особенно пристально, внедренной аналитики можно использовать в реальных приложениях.

| Ссылка | Описание | Область применения |
|------|-------------|------------|
| [Выполнение клиента кластеризации с помощью R и SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/customerclustering/) | Используйте неконтролируемого обучения для сегментирования потребителей на основе данных о продажах. В этом примере используется алгоритм масштабируемой rxKmeans из Microsoft R для построения модели кластеризации. | SQL Server 2016 или SQL Server 2017 |
| [Выполнение клиента кластеризации с помощью Python и SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/) | Узнайте, как использовать алгоритм методом k-средних для выполнения без учителя кластеризации клиентов. В этом примере используется Python языка в базе данных.| SQL Server 2017 |
| [Создание прогнозной модели с помощью R и SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction) | Узнайте, как ski использование машинного обучения для прогнозирования будущих проката, что позволяет бизнес-плана и сотрудников для удовлетворения будущего спроса. В этом примере используются алгоритмы Майкрософт для создания модели логистической регрессии и модели дерева принятия решений. | SQL Server 2016 или SQL Server 2017 |
| [Создание прогнозной модели с помощью Python и SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/) | Построено ski аренды анализа с помощью Python, которые помогут в планировании для будущего спроса. В этом примере использует новую библиотеку Python, **revoscalepy**, для создания модели линейной регрессии. | SQL Server 2017 |
| [Как использовать Tableau со службами машинного обучения SQL Server](https://blogs.msdn.microsoft.com/mlserver/2017/12/14/how-to-use-tableau-with-sql-server-machine-learning-services-with-r-and-python/) | Анализ социальных и создание диаграмм Tableau, с помощью SQL Server и R. | SQL Server 2016 или SQL Server 2017 |

## <a name="bkmk_solutions"></a>Шаблоны решений

Команды обработки и анализа данных Microsoft предоставила шаблоны настраиваемых решений, которые могут быть использованы для быстрого решения для распространенных сценариев. Каждое решение предназначена для решения конкретной задачи или отрасли проблемы. Большую часть решений предназначены для работы в SQL Server или в облачной среде, такие как машинное обучение Azure. Другие решения можно запустить на платформе Linux или в кластерах Hadoop или Spark, с помощью Microsoft R Server или сервер машинного обучения.

Предоставляется весь код, а также инструкции о том, как обучать и развертывать модели для оценки с помощью хранимых процедур SQL Server.

+ [обнаружение мошенничества;](https://gallery.cortanaanalytics.com/Tutorial/Online-Fraud-Detection-Template-with-SQL-Server-R-Services-1)
+ [прогнозирование ухода клиентов;](https://gallery.cortanaanalytics.com/Tutorial/Customer-Churn-Prediction-Template-with-SQL-Server-R-Services-1)
+ [профилактическое обслуживание.](https://gallery.cortanaanalytics.com/Tutorial/Predictive-Maintenance-Template-with-SQL-Server-R-Services-1)
+ [Спрогнозировать продолжительность госпитализации в больнице](https://gallery.cortanaintelligence.com/Solution/Predicting-Length-of-Stay-in-Hospitals-1)

Дополнительные сведения см. на странице [Шаблоны машинного обучения для служб SQL Server 2016 R Services](https://blogs.technet.microsoft.com/machinelearning/2016/03/23/machine-learning-templates-with-sql-server-2016-r-services/).

## <a name="recommended-reading"></a>Рекомендуемая литература

+ [Почему мы создавали его?](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/01/10/sql-server-r-services-why-did-we-build-it/)

    Хотите узнать всю правду о службах R? В этой статье от разработки и Участникам рабочей группы, с описанием источника и целей служб R SQL Server.

+ [Учебники и образцы данных для Microsoft R](https://docs.microsoft.com/machine-learning-server/r/tutorial-introduction)

    Дополнительные сведения о Microsoft R, а также пакета RevoScaleR обеспечивает этот набор кратких учебниках. Узнайте, как один раз написать код R и развертывание в любом месте, с помощью источников данных RevoScaleR и контексты удаленных вычислений.

+ [Начало работы с MicrosoftML](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-the-microsoftml-package)

  Узнайте, как использовать новые алгоритмы в пакет MicrosoftML для расширенного моделирования и преобразования масштабируемых данных, оптимизированный для несколько контекстов вычислений.
