---
title: Приступая к работе с машинного обучения в SQL Server | Документы Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 94f95b1a2ddaee32896d3a370338e53aded3ab99
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31203676"
---
# <a name="getting-started-with-machine-learning-in-sql-server"></a>Начало работы с машинным обучением в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Корпорация Майкрософт обеспечивает масштабируемую, интегрированный набор решений машинного обучения в локальной среде и облаке:

+ **Встроенная**, так как в SQL Server можно запустить R или Python. Это позволяет легко процессов слияния enterprise ETL и создание отчетов с данными таких компонентов проектирование, создание моделей и оценки задач обработки и анализа.
+ **Масштабируемая**, так как можно разрабатывать и тестирование решения на переносном компьютере и затем развернуть ее на различных платформах для распределенных специалист по анализу данных или параллельную обработку ключа операций, таких как модели обучения и оценки. Поддерживаются следующие платформы SQL Server в Windows, Hadoop и Spark.

В этой статье ссылки на ресурсы для каждого продукта на платформе Microsoft машинного обучения.

## <a name="machine-learning-in-sql-server"></a>Машинного обучения в SQL Server

+ SQL Server 2017

  Начиная с SQL Server 2017 г., теперь можно использовать код Python в SQL Server. В соответствии с более широкой поддержки для решения в нескольких языках (с Продолжение следует) и имя было изменено на [!INCLUDE[rsql-productnamenew-md](../includes/rsql-productnamenew-md.md)]. Теперь можно автоматизировать задач машинного обучения с помощью средств SQL для выполнения кода R или Python. Также можно использовать имя компьютера SQL Server как _контекста вычислений_ для заданий, запущенных из удаленной разработки среды.

    + [Общие сведения об архитектуре для Python в SQL Server](../advanced-analytics/python/architecture-overview-sql-server-python.md)
    + [Установка служб обучения 2017 машины SQL Server](install/sql-machine-learning-services-windows-install.md)

+ SQL Server 2016

  SQL Server 2016 поддерживает выполнение кода R в SQL Server с помощью хранимых процедур. Это позволяет легко для автоматизации задач машинного обучения с помощью средств SQL. Или возможность выполнения кода R из удаленного ноутбука или среду разработки R, при использовании имени компьютера SQL Server как _контекста вычислений_.

  Такая интеграция обеспечивает защиту данных и позволяет управлять и сбалансировать ресурсы, используемые R.

    + [Приступая к работе wth SQL Server R Services](r/getting-started-with-sql-server-r-services.md)
    + [Установка служб SQL Server 2016 R](install/sql-r-services-windows-install.md)

## <a name="microsoft-machine-learning-server-microsoft-r-server"></a>Microsoft машинного обучения Microsoft R (сервер)

Возможность установки [!INCLUDE[rsql-platformnew-md](../includes/rsql-platformnew-md.md)] предоставляется в 2017 г. SQL Server для поддержки корпоративных клиентов, который требуется выполнить распределенные и масштабируемые машинного самообучения, задания, но которым не требуется интеграция с SQL Server database engine, такие как использование вычислений SQL контексты.

В SQL Server 2016, используйте параметр для установки [!INCLUDE[rsql-platform-md](../includes/rsql-platformnew-md.md)].
  
  + [Добро пожаловать машинного обучения сервера](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server)
  
Вы также можете установить [!INCLUDE[rsql-platform-md](../includes/rsql-platform-md.md)] или [!INCLUDE[rsql-platformnew-md](../includes/rsql-platformnew-md.md)] через установщики платформ:

  + [Установка в Windows](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
  + [Установить в Linux](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-linux-install)
  + [Установить в Hadoop](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-hadoop-install)

> [!IMPORTANT]
> Если вы хотите запустить Python с помощью R Server, убедитесь, что установлена последняя версия [!INCLUDE[rsql-platformnew-md](../includes/rsql-platformnew-md.md)], которая доступна только через [!INCLUDE[sscurrent-md](../includes/sscurrent-md.md)] установки:
> 
>    + [Установка SQL Server 2017 г машины обучения Server (автономный)](install/sql-machine-learning-standalone-windows-install.md) или [установки SQL Server 2016 R Server (автономный)](install/sql-r-standalone-windows-install.md).

## <a name="related-products"></a>Связанные продукты

+ [Настройка клиента обработки и анализа данных](../advanced-analytics/r/set-up-a-data-science-client.md)

  Если вы уже установили один из машинного обучения серверных продуктов, в этой статье содержатся сведения о том, как настроить отдельный компьютер для разработки и тестирования решения, включая средства и необходимых библиотек.

+ [Виртуальная машина обработки и анализа данных](../advanced-analytics/r/provision-the-r-server-only-sql-server-2016-enterprise-vm-on-azure.md)

  Начать запись в машинного обучения, получив этот полный решения машинного обучения в Azure Marketplace. Виртуальная машина анализа данных (часто сокращено до «DSVM») включает SQL Server, Microsoft Server обучения компьютера и все средства разработки.
  
  Последнюю версию виртуальной машины обработки и анализа данных (DSVM) выполняется на выпуск предварительной версии 2016 Windows для предоставления чистая настраиваемые внешнего вида Windows 10. Предварительно настроена на драйверы NVIDIA, CUDA Toolkit 8.0 и библиотека cuDNN NVIDIA для рабочих нагрузок GPU.

## <a name="resources-for-learning"></a>Ресурсы для обучения

+ [Учебники машины обучения](../advanced-analytics/tutorials/machine-learning-services-tutorials.md)

  Начните здесь получить список всех ресурсов для изучения обучению машины с помощью SQL Server 2016 и 2017 г. SQL Server.

### <a name="r-tutorials"></a>Учебники R

+ [Учебники по SQL Server R](../advanced-analytics/tutorials/sql-server-r-tutorials.md)

   Описание способов выполнения R в SQL Server, создать и использовать контексты удаленных вычислений или выполнения моделирования в R, с помощью SQL Server.
   
   Содержит учебники, «все, поставляемое», чтобы законченное решение R можно запустить из SQL Server Management Studio, не открывая интегрированной среды разработки R!

+ [Изучить R и ScaleR в 25 малых функций](https://docs.microsoft.com/r-server/r/tutorial-r-to-revoscaler)

   Не знакомы с R? Вас интересует сравнение Microsoft R (или RevoScaleR) на стандартный R? См. Эти быстрого запуска R и компьютере сервера обучения.

### <a name="python-tutorials"></a>Учебники Python

+ [Учебники по SQL Server Python](../advanced-analytics/tutorials/sql-server-r-tutorials.md)

  Узнайте, как запустить Python в [!INCLUDE[ssnoversion](../includes/ssnoversion.md)]. Создать модель, Python и использовать его для оценки данных SQL Server.

   Это решение для начала до конца для разработчиков SQL предоставляет весь код, необходимо запустить Python из SQL Server Management Studio.


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
