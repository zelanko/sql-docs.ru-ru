---
title: "Учебники по службам обучения машины SQL Server | Документы Microsoft"
ms.date: 12/14/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to:
- SQL Server 2016
- SQL Server 2017
dev_langs:
- Python
- R
ms.assetid: 5ccc75f6-6703-47d9-b879-9a740569b45e
caps.latest.revision: "32"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: b8c384e5d8e13ed0961ad82f95af17c0352389be
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/20/2017
---
# <a name="tutorials-for-sql-server-machine-learning-services"></a>Учебники для служб SQL Server машины обучения

В этой статье содержит полный список учебников, демонстрационные материалы и образцов приложений, использующих функции обучения компьютера в SQL Server 2016 или 2017 г. SQL Server. Начните здесь рассматривается выполнение R или Python из T-SQL, использовать контексты вычислений, удаленные и локальные и оптимизировать код R и Python для производственной среды SQL.

## <a name="start-here"></a>Начните здесь

+ [Учебники по Python](../tutorials/sql-server-python-tutorials.md)

+ [Учебники R](../tutorials/sql-server-r-tutorials.md)

Дополнительные сведения о требованиях и настройке см. в разделе [необходимых компонентов](#bkmk_prerequisites).

## <a name="samples-and-solutions"></a>Образцы кода и решения

+ [Примеры](#bkmk_samples) 

    Эти сценарии реальных от команды разработчиков SQL Server показано, как внедрить в приложение машинного обучения. Все примеры содержат код, который можно загрузить, изменять и использовать в производственной среде.

+ [Решения](#bkmk_solutions) 

    Чтобы приступить к работе быстрое выполнение и машинное обучение настраиваются шаблоны из команды обработки и анализа данных Microsoft. Каждое решение соответствующий конкретной проблемы, задачи или отрасли. Большинство решений, которые предназначены для выполнения в SQL Server или в облачной среде, например машинного обучения Azure. Другие решения можно запустить в Linux или в кластерах Spark или Hadoop, с помощью Microsoft R Server или машины обучения.

### <a name ="bkmk_samples"></a>Образцы продуктов SQL Server

Эти образцы и образцы, предоставляемые команды разработчиков SQL Server и R Server выделите способы использования аналитики, внедренный в реальных приложениях.

+ [Выполнение клиента кластеризации с помощью R и SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/customerclustering/)

  Используйте неконтролируемого обучения сегмент клиентам на основе данных продаж. В этом примере используется алгоритм масштабируемой rxKmeans из Microsoft R для построения модели кластеризации. 
  
  Применяется к: SQL Server 2016 или SQL Server 2017 г.

+ [НОВЫЕ ФУНКЦИИ! Выполнение клиента кластеризации с помощью Python и SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/)

    Узнайте, как использовать алгоритм Kmeans для выполнения незащищенных кластеризации клиентов. Этот пример использует Python языка в базе данных.
    
    Применяется к: SQL Server 2017 г.

+ [Создать прогнозную модель с помощью R и SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction)

  Узнайте, как использовать машинного обучения для прогнозирования будущих внаем, что позволяет бизнес-планом и персонал будущих требований бизнеса ski аренды. В этом примере используются алгоритмы Microsoft для построения модели дерева принятия решений и логистической регрессии. 
  
  Применяется к: SQL Server 2016 или SQL Server 2017 г.

+ [Создать прогнозную модель с помощью Python и SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)

   Построено ski аренды анализа с помощью Python, планированию будущих требований. В этом примере используется в новой библиотеке Python **revoscalepy**, чтобы создать модель линейной регрессии.
   
   Применяется к: SQL Server 2017 г.

+ [Как использовать Tableau со службами SQL Server машины обучения](https://blogs.msdn.microsoft.com/mlserver/2017/12/14/how-to-use-tableau-with-sql-server-machine-learning-services-with-r-and-python/)

    Анализ социальных сетей и создание диаграмм Tableau, с помощью SQL Server и R.

### <a name="bkmk_solutions"></a>Шаблоны решений

Команда обработки и анализа данных Майкрософт предоставила шаблоны решений, которые можно использовать для быстрого решения для распространенных сценариев. Весь код предоставляется вместе с инструкциями о том, как обучать и развернуть модель для оценки с помощью хранимых процедур SQL Server.

+ [обнаружение мошенничества;](https://gallery.cortanaanalytics.com/Tutorial/Online-Fraud-Detection-Template-with-SQL-Server-R-Services-1)
+ [прогнозирование ухода клиентов;](https://gallery.cortanaanalytics.com/Tutorial/Customer-Churn-Prediction-Template-with-SQL-Server-R-Services-1)
+ [профилактическое обслуживание.](https://gallery.cortanaanalytics.com/Tutorial/Predictive-Maintenance-Template-with-SQL-Server-R-Services-1)
+ [Время нахождения больницы прогнозирования](https://gallery.cortanaintelligence.com/Solution/Predicting-Length-of-Stay-in-Hospitals-1)

Дополнительные сведения см. на странице [Шаблоны машинного обучения для служб SQL Server 2016 R Services](https://blogs.technet.microsoft.com/machinelearning/2016/03/23/machine-learning-templates-with-sql-server-2016-r-services/).

## <a name="more-resources-and-reading"></a>Дополнительные ресурсы и чтение

+ [Почему мы постройте его?](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/01/10/sql-server-r-services-why-did-we-build-it/)

    Хотите узнать всю правду о службах R? Эта статья разработки и команды PM с описанием источника и цели служб R SQL Server.

+ [Учебники и образцы данных для Microsoft R](https://docs.microsoft.com/machine-learning-server/r/tutorial-introduction)

    Дополнительные сведения о Microsoft R, а также пакета RevoScaleR обеспечивает в этой коллекции кратких учебниках. Узнайте, как написать код R, один раз и развертывания в любом месте, с помощью RevoScaleR источники данных и контекстах удаленных вычислений.

+ [Приступая к работе с MicrosoftML](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-the-microsoftml-package)

  Сведения об использовании новых алгоритмов в пакете MicrosoftML для расширенного моделирования и преобразования данных масштабируемой, оптимизированный для нескольких контекстов вычислений.

## <a name="bkmk_Prerequisites"></a>Предварительные требования

Чтобы запустить эти учебники, необходимо загрузить и установить SQL Server машинного обучения компонентов, как описано здесь:

+ [Настройка служб SQL Server 2017 г машины обучения или служб R SQL Server 2016](../r/set-up-sql-server-r-services-in-database.md)
+ [Настройка служб SQL Server 2017 г Python](../python/setup-python-machine-learning-services.md)

С 2017 г. SQL Server можно установить R и Python либо оба. В противном случае общий процесс установки, архитектуры и требований одинаковы.

После запуска программы установки SQL Server, не забывайте следующие важные действия:

1. Включение возможности выполнения внешнего сценария, запустив `sp_configure 'external scripts enabled', 1`. Следуйте инструкциям, чтобы изменить настройку и перезапустите SQL Server.
2. Убедитесь, что запущена служба панели запуска, и что рабочих учетных записей запуска можно подключиться к экземпляру SQL Server.
3. Просмотрите разрешения, связанные с пользователями, которые необходимо выполнить скрипты R или Python. Независимо от того, используются ли имен входа SQL Server или учетные записи пользователей Windows пользователь должен иметь разрешение на выполнение скриптов R или Python и должен иметь возможность подключения к экземпляру. В зависимости от того, работу с учебником, пользователь может также потребоваться разрешение на запись данных, создания объектов базы данных или сделать массового импорта данных.

Дополнительные сведения см. в этой статье, для некоторых распространенных проблем установки и настройки: [Устранение неполадок службы машины обучения](../machine-learning-troubleshooting-faq.md)

> [!NOTE]
> Не удается запустить эти учебники, с помощью другого средства R или Python открытым исходным кодом. Среды разработки и сервере SQL Server с помощью машинного обучения должен иметь R или Python библиотек, предоставляемых корпорацией Майкрософт, которые поддерживают интеграцию с SQL Server и использование контекстах удаленных вычислений.
