---
title: "Приступая к работе с машинного обучения в SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 08/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 09d6e887a8c64c98a1c3f68c78b07c26da6ffb76
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="getting-started-with-machine-learning-in-sql-server"></a>Приступая к работе с машинного обучения в SQL Server

Корпорация Майкрософт обеспечивает масштабируемую, интегрированный набор решений машинного обучения в локальной среде и облаке:

+ **Встроенная**, так как в SQL Server можно запустить R или Python. Это позволяет легко процессов слияния enterprise ETL и создание отчетов с данными таких компонентов проектирование, создание моделей и оценки задач обработки и анализа.
+ **Масштабируемая**, так как можно разрабатывать и тестирование решения на переносном компьютере и затем развернуть ее на различных платформах для распределенных специалист по анализу данных или параллельную обработку ключа операций, таких как модели обучения и оценки. Поддерживаются следующие платформы SQL Server в Windows, Hadoop и Spark.

В этой статье ссылки на ресурсы для каждого продукта на платформе Microsoft машинного обучения.

## <a name="machine-learning-in-sql-server"></a>Машинного обучения в SQL Server

+ SQL Server 2017

  Начиная с SQL Server 2017 г CTP 2.0 поддержки для добавил Python, а имя было изменено на машине обучения службы (в базе данных) для отражения поддержки для более широкого круга обучению машины. Теперь можно автоматизировать задач машинного обучения с помощью средств SQL для выполнения кода R или Python. Также можно использовать имя компьютера SQL Server как _контекста вычислений_ для заданий, запущенных из удаленной разработки среды.

    + [Общие сведения об архитектуре для Python в SQL Server](python/architecture-overview-sql-server-python.md)
    + [Настройка SQL Server R Services или службы обучения машины](../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)

+ SQL Server 2016

  SQL Server 2016 поддерживает выполнение кода R в SQL Server с помощью хранимых процедур. Это позволяет легко для автоматизации задач машинного обучения с помощью средств SQL. Или возможность выполнения кода R из удаленного ноутбука или среду разработки R, при использовании имени компьютера SQL Server как _контекста вычислений_.

  Такая интеграция обеспечивает защиту данных и позволяет управлять и сбалансировать ресурсы, используемые R.

    + [Приступая к работе wth SQL Server R Services](r/getting-started-with-sql-server-r-services.md)
    + [Настройка SQL Server R Services или службы обучения машины](../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)

## <a name="microsoft-machine-learning-server-microsoft-r-server"></a>Microsoft машинного обучения Microsoft R (сервер)

В SQL Server 2017 г. для поддержки корпоративных клиентов, который хотите выполнить распределенные и масштабируемые машинного самообучения, задания, но которым не требуется интеграцию с компонентом database engine SQL Server, такие как использование обеспечивается возможность установки сервера обучения Майкрософт машины контекстов вычислений SQL.

В SQL Server 2016 используйте параметр для установки Microsoft R Server.
  
  + [Introducing Microsoft R Server](https://msdn.microsoft.com/microsoft-r/rserver) (Знакомство с Microsoft R Server)
  
Также можно установить R Server через конкретную платформу установщики, доступный в сети MSDN:

  + [R Server for Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows) (R Server для Windows)
  + [R Server для Linux](https://msdn.microsoft.com/microsoft-r/rserver-install-linux-server)
  + [R Server для Hadoop](https://msdn.microsoft.com/microsoft-r/rserver-install-hadoop)

> [!IMPORTANT]
> Если вы хотите запустить Python с помощью R Server, убедитесь, что установлена последняя версия **машины обучения Server**, которая доступна только через программу установки SQL Server 2017 г.:
> 
>    + [Настройка Microsoft R Server или машины обучения](../advanced-analytics/r/create-a-standalone-r-server.md)

## <a name="related-products"></a>Связанные продукты

+ [Настройка клиента обработки и анализа данных](../advanced-analytics/r/set-up-a-data-science-client.md)

  Если вы уже установили один из машинного обучения серверных продуктов, в этой статье содержатся сведения о том, как настроить отдельный компьютер для разработки и тестирования решения, включая средства и необходимых библиотек.

+ [Виртуальная машина обработки и анализа данных](../advanced-analytics/r/provision-the-r-server-only-sql-server-2016-enterprise-vm-on-azure.md)

  Начать запись в машинного обучения, получив этот полный решения машинного обучения в Azure Marketplace. Виртуальная машина анализа данных (часто сокращено до «DSVM») включает SQL Server, Microsoft Server обучения компьютера и все средства разработки.
  
  Последнюю версию виртуальной машины обработки и анализа данных (DSVM) выполняется на выпуск предварительной версии 2016 Windows для предоставления чистая настраиваемые внешнего вида Windows 10. Предварительно настроена на драйверы NVIDIA, CUDA Toolkit 8.0 и библиотека cuDNN NVIDIA для рабочих нагрузок GPU.

## <a name="resources-for-learning"></a>Ресурсы для обучения

+ [Учебники машины обучения](../advanced-analytics/tutorials/machine-learning-services-tutorials.md)

  Начните здесь найти справочные материалы по обучению машины с помощью 2017 г. SQL Server и SQL Server 2017 г. список всех ресурсов.

### <a name="r-tutorials"></a>Учебники R

+ [Учебники по SQL Server R](../advanced-analytics/tutorials/sql-server-r-tutorials.md)

   Описание способов выполнения R в SQL Server, создать и использовать контексты удаленных вычислений или выполнения моделирования в R, с помощью SQL Server.
   
   Содержит учебники, «все, поставляемое», чтобы законченное решение R можно запустить из SQL Server Management Studio, не открывая интегрированной среды разработки R!

+ [Изучить R и ScaleR в 25 малых функций](https://docs.microsoft.com/r-server/r/tutorial-r-to-revoscaler)

   Не знакомы с R? Вас интересует сравнение Microsoft R (или RevoScaleR) на стандартный R? R Server см. Эти быстрого запуска.

### <a name="python-tutorials"></a>Учебники Python

+ [Учебники по SQL Server Python](../advanced-analytics/tutorials/sql-server-r-tutorials.md)

  Узнайте, как выполнять Python в SQL Server. Создать модель, Python и использовать его для оценки данных SQL Server.

   Это решение для начала до конца для разработчиков SQL предоставляет весь код, необходимо запустить Python из SQL Server Management Studio.

+ [Публикация и использование кода Python](../advanced-analytics/python/publish-consume-python-code.md)

  В этом пошаговом руководстве поставляется с весь код, необходимые для развертывания веб-службу, с помощью сервера машины обучения модели.

### <a name="product-samples-with-code"></a>Образцы продуктов с кодом

Эти решения от команды разработчиков SQL Server выполняются в R или Python и демонстрирующие типичные сценарии для интеграции машинного обучения с бизнес-приложений.

+ [Создание интеллектуальных приложений с помощью SQL Server и R](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction)

+ [Сборка приложения интеллектуальной с SQL Server и Python](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)

### <a name="data-science-solution-templates"></a>Шаблоны решений для обработки и анализа данных

Шаблоны решений от команды обработки и анализа данных Microsoft представляют полный пример решения, адаптированные для конкретных отраслей и сценариев. Они предназначены для использования в качестве стандартных блоков для реализации быстрого решения или для демонстрации рекомендации. Каждый шаблон включает образцы данных и настраиваемый код.

+ [Шаблоны решений](../advanced-analytics/tutorials/data-science-scenarios-and-solution-templates.md)

## <a name="next-steps"></a>Следующие шаги

[Начало работы со службами SQL Server машины обучения](../advanced-analytics/r/getting-started-with-sql-server-r-services.md)

[Начало работы с Microsoft машинного обучения сервера](../advanced-analytics/r/getting-started-with-microsoft-r-server-standalone.md)

