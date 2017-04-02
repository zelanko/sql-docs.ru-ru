---
title: "Ввод в эксплуатацию кода R | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "05/31/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f15696b1-2479-4e5f-ac5e-4beaf958a043
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 11
---
# Ввод в эксплуатацию кода R
  Разработчикам баз данных необходимо интегрировать несколько технологий и объединить результаты, чтобы их можно было совместно использовать на всем предприятии. Разработчик базы данных работает с разработчиками приложений, разработчиками SQL и специалистами по анализу данных для создания решений, методов управления данными, а также проектирования и развертывания решений. [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] предоставляют множество преимуществ для разработчиков, работающих со специалистами по анализу данных.  
  
-   **Взаимодействовать с помощью скриптов R [!INCLUDE[tsql](../../includes/tsql-md.md)].** Приложения и разработчиков баз данных, а также аналитиков, создания отчетов, можно вызвать сценарий R путем вызова из системной хранимой процедуры.  
  
     Дополнительные сведения о базовом синтаксисе см. в разделе [sp_execute_external_script & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) и [с помощью кода R в T-SQL](../../advanced-analytics/r-services/using-r-code-in-transact-sql-sql-server-r-services.md).  
 
    Развернутый пример того, как ввод в эксплуатацию R код с использованием хранимых процедур см. в разделе [аналитики в базе данных для разработчиков SQL](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md).
  
     Интеграция с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , кроме того, означает, что вы можете выполнять сценарии R с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] и внедрять результаты в свое приложение. Например, можно создать отчет [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , который выполняет сценарий R и затем отображает графики и прогнозы в отчете.  
  
-   **Производительность и масштаб.** Несмотря на то, что известно, что язык R с открытым исходным имеют ограничения, пакет RevoScaleR API-интерфейсы, предоставляемые [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] можно работать с большими наборами данных и использовать преимущества многопоточных, многоядерных процессоров, несколькими процессами вычислений в базе данных.  
  
     Если решение R использует сложные агрегаты или включает в себя большие наборы данных, можно использовать высокоэффективные хранящиеся в памяти агрегаты и индексы columnstore SQL и переложить на код R обработку статистических вычислений и оценок.  
  
-   **Стандартные инструменты разработки и управления** Не требуются дополнительные инструменты для администрирования или развертывания. Все задания R можно вызывать с помощью хранимой процедуры.  
  
     Кроме того, один и тот же код R, который применяется к данным [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , можно использовать повторно для других источников данных, например Hadoop.  
  
 В этом разделе описываются основные понятия, знание которых необходимо для успешного преобразования решений R и их развертывания в рабочей среде с помощью [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].  
  
## В этом разделе

[Работа с типами данных R](../../advanced-analytics/r-services/working-with-r-data-types.md)

[Преобразование кода R для использования в службах R](../../advanced-analytics/r-services/converting-r-code-for-use-in-r-services.md)

##  <a name="bkmk_RelatedTasks"></a> Связанные задачи  
  
[Настройка производительности для SQL Server R служб](../../advanced-analytics/r-services/sql-server-r-services-performance-tuning.md)
 
## См. также:  
 [Возможности и задачи служб R SQL Server](../../advanced-analytics/r-services/sql-server-r-services-features-and-tasks.md)   
 [sp_execute_external_script & #40; Transact-SQL и #41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)  
  
  