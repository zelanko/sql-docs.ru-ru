---
title: "Углубленное рассмотрение обработки и анализа данных: использование пакетов RevoScaleR | Документация Майкрософт"
ms.custom: 
ms.date: 05/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
dev_langs:
- R
ms.assetid: c2efb3f2-cad5-4188-b889-15d68b742ef5
caps.latest.revision: 18
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 51f4a782ad941d8b9a66ba00cbf2b3540478361c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="data-science-deep-dive-using-the-revoscaler-packages"></a>Углубленное рассмотрение обработки и анализа данных: использование пакетов RevoScaleR

Этот учебник демонстрирует использование улучшенные пакеты R, предоставляемые в [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] для работы с данными SQL Server и создавать масштабируемые решения R, с помощью сервера в качестве контекста вычислений для анализа больших данных высокой производительности.

Вы узнаете, как для создания контекста удаленных вычислений, перемещение данных между контекстами локальных и удаленных вычислений и выполнять код R на удаленный экземпляр SQL Server. Вы также узнаете, как анализировать и отображать данные как локально, так и на удаленном сервере и способы создания и развертывания моделей.

> [!NOTE]
> 
> Этот учебник предназначен для работы с данными SQL Server в Windows и использует контекстов вычислений в базе данных. Если вы хотите использовать R в других контекстах, например, Teradata, Linux или Hadoop, см. следующие учебники Microsoft R Server: 
> + [Использование сервера R с sparklyr](https://msdn.microsoft.com/microsoft-r/microsoft-r-get-started-spark-interop)
> + [Explore R and ScaleR in 25 functions](https://msdn.microsoft.com/microsoft-r/microsoft-r-tutorial-r2revoscaler) (Обзор R и ScaleR в 25 функциях)
> + [Приступая к работе с ScaleR на Hadoop MapReduce](https://msdn.microsoft.com/microsoft-r/scaler-hadoop-getting-started)
> + [Руководство по RevoScaleR Teradata начало работы с](https://msdn.microsoft.com/microsoft-r/scaler-teradata-getting-started)

## <a name="overview"></a>Обзор

Для иллюстрации гибкости и вычислительной мощности пакетов ScaleR в этом учебном курсе вы будете часто переключать контекст вычислений и перемещать данные.

+ Данные изначально получаются из CSV- или XDF-файлов. Вы будете импортировать данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью функций из пакета RevoScaleR.
+ Обучение и оценка модели будет выполняться в контексте вычислений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
    Вы будете создавать новые таблицы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью функций **rx** для сохранения результатов оценки.
+ Графики будут создаваться как на сервере, так и в контексте локальных вычислений.
+ Для обучения модели будут использоваться данные, уже хранящиеся в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Все вычисления будут производиться в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
+ Вы будете извлекать подмножества данных и сохранять их в XDF-файле для повторного использования при анализе на локальной рабочей станции.
+ Новые данные, используемые в процессе анализа, извлекаются из базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью подключения ODBC. Все вычисления производятся на локальной рабочей станции.
+ Наконец, вы проведете моделирование на основе пользовательской функции R, используя контекст серверных вычислений.

### <a name="get-started-now"></a>Начнем прямо сейчас

Этот учебник занимает около 75 минут, не включая программу установки.

1. [Работа с данными SQL Server, с помощью R](../../advanced-analytics/tutorials/deepdive-work-with-sql-server-data-using-r.md)
2. [Создание объектов данных SQL Server с помощью функции RxSqlServerData](../../advanced-analytics/tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)
3. [Запрашивать и изменять данных SQL Server](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)
4. [Определение и использование контекстов вычислений](../../advanced-analytics/tutorials/deepdive-define-and-use-compute-contexts.md)
5. [Создание и выполнение сценариев R](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)
6. [Визуализация данных SQL Server с помощью R](../../advanced-analytics/tutorials/deepdive-visualize-sql-server-data-using-r.md)
7. [Создание моделей R](../../advanced-analytics/tutorials/deepdive-create-models.md)
8. [Оценка новых данных](../../advanced-analytics/tutorials/deepdive-score-new-data.md)
9. [Преобразование данных с помощью R](../../advanced-analytics/tutorials/deepdive-transform-data-using-r.md)
10. [Загрузка данных в памяти с помощью rxImport](../../advanced-analytics/tutorials/deepdive-load-data-into-memory-using-rximport.md)
11. [Создание новой таблицы SQL Server, с помощью rxDataStep](../../advanced-analytics/tutorials/deepdive-create-new-sql-server-table-using-rxdatastep.md)
12. [Выполнять анализ фрагментации, с помощью rxDataStep](../../advanced-analytics/tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)
13. [Анализ данных в локальном контексте;](../../advanced-analytics/tutorials/deepdive-analyze-data-in-local-compute-context.md)
14. [Перемещение данных между SQL Server и XDF-файла](../../advanced-analytics/tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)
15. [Создание простого моделирования](../../advanced-analytics/tutorials/deepdive-create-a-simple-simulation.md)

### <a name="target-audience"></a>Целевая аудитория

Этот учебник предназначен для специалистов по обработке и анализу данных или для тех, кто уже немного знаком с R и задачами обработки и анализа данных, включая исследование, статистический анализ и настройку модели.  Тем не менее весь код предоставляется, поэтому даже если вы не знакомы с R, можно легко выполнить код и дальнейшей работы, при условии, что у вас есть необходимых серверных и клиентских средах.

Также необходимо разбираться в синтаксисе [!INCLUDE[tsql](../../includes/tsql-md.md)] и уметь получать доступ к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или других средств для работы с базами данных, таких как Visual Studio.
  
> [!TIP]
> Сохраняйте рабочее пространство R после прохождения уроков, чтобы можно было легко продолжить работу с того места, на котором вы остановились.

### <a name="prerequisites"></a>Предварительные требования

- **SQL Server с поддержкой R**
  
    Установите SQL Server 2016 и включение служб R (в базе данных). Установить SQL Server 2017 г. и включить службы обучения машины или выберите язык R. Процесс установки описан в [электронной документации по SQL Server 2016](http://msdn.microsoft.com/library/mt696069(SQL.130).aspx).
  
-  **Разрешения базы данных**
  
    Для выполнения запросов, используемых для обучения модели, требуются права **db_datareader** в базе данных, в которой хранятся данные. Для выполнения R, ваш пользователь должен иметь разрешение EXECUTE ANY EXTERNAL SCRIPT.

-   **Компьютер разработки обработки и анализа данных**
  
    В среде разработки R, необходимо также установить пакеты RevoScaleR и связанных поставщиков. Для этого проще всего установить клиент Microsoft R или Microsoft R Server (изолированный). Дополнительные сведения см. в разделе [Настройка клиента обработки и анализа данных](http://msdn.microsoft.co/library/mt696067(SQL.130).aspx).
      
    > [!NOTE] 
    > Другие версии Revolution R Enterprise или Revolution R Open не поддерживаются.
    > 
    > Распространяемом пакете открытого кода r, например R 3.2.2, не будет работать в этом учебнике, поскольку только функции RevoScaleR используется в контекстах удаленных вычислений.
  
-   **Дополнительные пакеты R**
  
    Для этого учебника необходимо установить следующие пакеты: **dplyr**, **ggplot2**, **ggthemes**, **reshape2**и **e1071**. Инструкции приводятся в рамках учебника.
  
    Все пакеты должны устанавливаться в двух местах: на компьютере, можно использовать для разработки решений R и на компьютере SQL Server, где будет выполняться R-скриптов. Если у вас разрешение на установку пакетов на компьютере сервера, попросите администратора. **Не устанавливайте эти пакеты в пользовательской библиотеке.** Важно установить пакеты в библиотеке пакетов R, которая используется экземпляром SQL Server.

Дополнительные сведения см. в разделе [необходимые условия для пошаговых руководств, обработки и анализа данных](../../advanced-analytics/tutorials/walkthrough-prerequisites-for-data-science-walkthroughs.md).



## <a name="next-step"></a>Следующий шаг

[Работа с данными SQL Server, с помощью R](../../advanced-analytics/tutorials/deepdive-work-with-sql-server-data-using-r.md)


