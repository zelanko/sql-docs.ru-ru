---
title: "Глубокое погружение обработки и анализа данных: с помощью RevoScaleR пакетов с SQL Server | Документы Microsoft"
ms.date: 12/14/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to:
- SQL Server 2016
- SQL Server 2017
dev_langs: R
ms.assetid: c2efb3f2-cad5-4188-b889-15d68b742ef5
caps.latest.revision: "18"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: a8fe18a578391beaae79259440779b0a76336ee2
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="data-science-deep-dive-using-the-revoscaler-packages-with-sql-server"></a>Глубокое погружение обработки и анализа данных: с помощью RevoScaleR пакетов с SQL Server

Этот учебник демонстрирует использование улучшенные пакеты R, предоставляемые в [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] для работы с данными SQL Server и создавать масштабируемые решения R, с помощью сервера в качестве контекста вычислений для анализа больших данных высокой производительности.

Описание способов создания контекста удаленных вычислений, перемещение данных между контекстов локальных и удаленных вычислений и выполнять код R на удаленный экземпляр SQL Server. Вы также узнаете, как анализировать и отображать данные как локально, так и на удаленном сервере и способы создания и развертывания моделей.

> [!NOTE]
> 
> Этот учебник предназначен для работы с данными SQL Server в Windows и использует контекстов вычислений в базе данных. Если вы хотите использовать R в других контекстах, например, Teradata, Linux или Hadoop, см. следующие учебники Microsoft R Server: 
> + [Использование сервера R с sparklyr](https://docs.microsoft.com/machine-learning-server/r/tutorial-sparklyr-revoscaler)
> + [Explore R and ScaleR in 25 functions](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler) (Обзор R и ScaleR в 25 функциях)
> + [Приступая к работе с ScaleR на Hadoop MapReduce](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-hadoop)

## <a name="overview"></a>Обзор

Чтобы преимущества гибкости и обработки пакета RevoScaleR, в этом учебнике вы перемещения данных и переключения контекстов вычислений часто. Чтобы проиллюстрировать это, ниже приведены некоторые задачи в этом учебнике.

+ Данные изначально получаются из CSV- или XDF-файлов. Импортировать данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью функций из пакета RevoScaleR.
+ Выполняются с помощью модели обучения и оценки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] контекста вычислений. 
+ Использовать функции RevoScaleR для создания новых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы, чтобы сохранить результаты оценки.
+ Создание графиков оба на сервере и локальной контекста вычислений.
+ Обучение модели с данными в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных, выполнение R [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра.
+ Извлечение подмножества данных и сохраните его как файл XDF для повторного использования в анализе на локальной рабочей станции.
+ Получить новые данные для оценки, открыв соединение ODBC для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных. Оценка выполняется на локальной рабочей станции.
+ Создание пользовательской функции R и запустите его на сервере контекст вычислений для выполнения моделирования.

### <a name="article-list-and-time-required"></a>Список статей и длительность

Этот учебник занимает около 75 минут, не включая программу установки.

1. [Работа с данными SQL Server с помощью R](../../advanced-analytics/tutorials/deepdive-work-with-sql-server-data-using-r.md)
2. [Создание объектов данных SQL Server с помощью функции RxSqlServerData](../../advanced-analytics/tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)
3. [Запрос и изменение данных SQL Server](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)
4. [Определение и использование контекстов вычисления](../../advanced-analytics/tutorials/deepdive-define-and-use-compute-contexts.md)
5. [Создание и выполнение сценариев R](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)
6. [Визуализация данных SQL Server с помощью R](../../advanced-analytics/tutorials/deepdive-visualize-sql-server-data-using-r.md)
7. [Создание моделей R](../../advanced-analytics/tutorials/deepdive-create-models.md)
8. [Оценка новых данных](../../advanced-analytics/tutorials/deepdive-score-new-data.md)
9. [Преобразование данных с помощью языка R](../../advanced-analytics/tutorials/deepdive-transform-data-using-r.md)
10. [Загрузка данных в памяти с помощью rxImport](../../advanced-analytics/tutorials/deepdive-load-data-into-memory-using-rximport.md)
11. [Создание новых таблиц SQL Server, с помощью rxDataStep](../../advanced-analytics/tutorials/deepdive-create-new-sql-server-table-using-rxdatastep.md)
12. [Выполнение фрагментирующего анализа с помощью rxDataStep](../../advanced-analytics/tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)
13. [Анализ данных в локальном контексте вычисления](../../advanced-analytics/tutorials/deepdive-analyze-data-in-local-compute-context.md)
14. [Перемещение данных из SQL Server с помощью XDF-файлов](../../advanced-analytics/tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)
15. [Создание простого моделирования](../../advanced-analytics/tutorials/deepdive-create-a-simple-simulation.md)

### <a name="target-audience"></a>Целевая аудитория

Этот учебник предназначен для специалистов по анализу данных или для пользователей, которые уже знакома, с помощью R и выполнять задачи обработки и анализа данных, например сводки и создании модели.  Тем не менее весь код предоставляется, поэтому даже если вы не знакомы с R, можно выполнить код и дальнейшей работы, при условии, что у вас есть необходимых серверных и клиентских средах.

Также должен быть знаком с [!INCLUDE[tsql](../../includes/tsql-md.md)] синтаксис и знать, как получить доступ к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных с помощью средств такие:

+ [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 
+ Инструменты для баз данных в Visual Studio 
+ Бесплатный [mssql расширения для Visual Studio Code](https://docs.microsoft.com/sql/linux/sql-server-linux-develop-use-vscode).
  
> [!TIP]
> Сохраняйте рабочее пространство R после прохождения уроков, чтобы можно было легко продолжить работу с того места, на котором вы остановились.

### <a name="prerequisites"></a>предварительные требования

- **SQL Server с поддержкой R**
  
    Установите SQL Server 2016 и включение служб R (в базе данных). Установить SQL Server 2017 г. и включить службы обучения машины или выберите язык R.
  
-  **Разрешения базы данных**
  
    Для выполнения запросов, используемых для обучения модели, требуются права **db_datareader** в базе данных, в которой хранятся данные. Для выполнения R, ваш пользователь должен иметь разрешение EXECUTE ANY EXTERNAL SCRIPT.

-   **Компьютер разработки обработки и анализа данных**
  
    На компьютере, используемом в качестве среды разработки R, необходимо установить пакеты RevoScaleR и связанных поставщиков. Для этого проще всего установить клиент Microsoft R, Microsoft R Server (изолированный) или машины обучения Server (изолированный). 
      
    > [!NOTE] 
    > Другие версии Revolution R Enterprise или Revolution R Open не поддерживаются.
    > 
    > Распространяемом пакете открытого кода r, не может использоваться в этом учебнике, поскольку только функции RevoScaleR используется в контекстах удаленных вычислений.
  
-   **Дополнительные пакеты R**
  
    В этом учебнике, необходимо установить следующие пакеты: **dplyr**, **ggplot2**, **ggthemes**, **reshape2**, и **e1071** . Инструкции приводятся в рамках учебника.
  
    Все пакеты должны устанавливаться в двух местах: на компьютере, можно использовать для разработки решений R и на компьютере SQL Server, где выполняются R-скриптов. Если у вас разрешение на установку пакетов на компьютере сервера, попросите администратора. 
    
    **Не устанавливайте эти пакеты в пользовательской библиотеке.** Пакеты должны устанавливаться в библиотеке пакетов R, которая используется экземпляром SQL Server.

Дополнительные сведения см. в разделе [необходимые условия для пошаговых руководств, обработки и анализа данных](../../advanced-analytics/tutorials/walkthrough-prerequisites-for-data-science-walkthroughs.md).

## <a name="next-step"></a>Следующий шаг

[Работа с данными SQL Server с помощью R](../../advanced-analytics/tutorials/deepdive-work-with-sql-server-data-using-r.md)

