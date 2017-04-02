---
title: "Сохранение плана выполнения в формате XML | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "планы запроса в формате XML [SQL Server]"
  - "открытие планов выполнения"
  - "Showplan XML, инструкции [SQL Server]"
  - "планы выполнения [SQL Server], сохранение"
  - "сохранение планов выполнения"
ms.assetid: c439e53b-56f3-4442-97c6-dabd48a203d8
caps.latest.revision: 25
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 25
---
# Сохранение плана выполнения в формате XML
  Используйте среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , чтобы сохранить планы выполнения в XML-файле и открыть их для просмотра.  
  
 Чтобы использовать функциональные возможности плана выполнения в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]или параметры XML Showplan SET, пользователи должны иметь соответствующие разрешения на выполнение запроса [!INCLUDE[tsql](../../includes/tsql-md.md)] , для которого формируется план выполнения, и им нужно предоставить разрешение SHOWPLAN для всех баз данных, на которые ссылается запрос.  
  
### Сохранение плана запроса с помощью параметров XML Showplan SET  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] откройте редактор запросов и подключитесь к компоненту [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Включите SHOWPLAN_XML с помощью следующей инструкции:  
  
    ```  
    SET SHOWPLAN_XML ON;  
    GO  
    ```  
  
     Для включения STATISTICS XML воспользуйтесь следующей инструкцией:  
  
    ```  
    SET STATISTICS XML ON;  
    GO  
    ```  
  
     Инструкция SHOWPLAN_XML создает сведения о плане выполнения запроса во время компиляции, но не выполняет запрос. Инструкция STATISTICS XML создает сведения о плане выполнения запроса во время выполнения и выполняет запрос.  
  
3.  Выполните запрос. Пример  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SET SHOWPLAN_XML ON;  
    GO  
    -- Execute a query.  
    SELECT BusinessEntityID   
    FROM HumanResources.Employee  
    WHERE NationalIDNumber = '509647174';  
    GO  
    SET SHOWPLAN_XML OFF;  
    ```  
  
4.  На панели **Результаты** щелкните правой кнопкой мыши поле **Microsoft SQL Server XML Showplan**, содержащее план запроса, и выберите пункт **Сохранить результаты как**.  
  
5.  В диалоговом окне **Сохранение** \<сетка или текст> **результатов** в поле **Тип файла** выберите **Все файлы (\*.\*)**.  
  
6.  В поле **Имя файла** укажите имя в формате \<имя**>.sqlplan**, после чего нажмите кнопку **Сохранить**.  
  
### Сохранение плана выполнения с помощью параметров среды SQL Server Management Studio  
  
1.  Сформируйте либо прогнозируемый, либо фактический план выполнения с помощью среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Дополнительные сведения см. в разделах [Отображение предполагаемого плана выполнения](../../relational-databases/performance/display-the-estimated-execution-plan.md) или [Отображение фактического плана выполнения](../../relational-databases/performance/display-an-actual-execution-plan.md).  
  
2.  На вкладке **План выполнения** панели результатов щелкните правой кнопкой мыши графический план выполнения и выберите **Сохранить план выполнения как**.  
  
     Как альтернативный вариант можно также выбрать **Сохранить план выполнения как** в меню **Файл** .  
  
3.  В диалоговом окне **Сохранение** убедитесь, что в поле **Тип файла** установлено значение **Файлы плана выполнения (\*.sqlplan)**.  
  
4.  В поле **Имя файла** укажите имя в формате \<имя**>.sqlplan**, после чего нажмите кнопку **Сохранить**.  
  
### Открытие сохраненного плана запроса в формате XML в среде SQL Server Management Studio  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]в меню **Файл** выберите **Открыть**, а затем нажмите **Файл**.  
  
2.  В диалоговом окне **Открытие файла** установите в поле **Файлы типа** значение **Файлы плана выполнения (\*.sqlplan)**, чтобы получить отфильтрованный список сохраненных файлов XML с планами запросов.  
  
3.  Выберите файл плана запроса XML, который нужно просмотреть, и нажмите **Открыть**.  
  
     Также можно дважды щелкнуть файл с расширением **sqlplan** в проводнике Windows. План откроется в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
## См. также:  
 [SET SHOWPLAN_XML (Transact-SQL)](../../t-sql/statements/set-showplan-xml-transact-sql.md)   
 [SET STATISTICS XML (Transact-SQL)](../../t-sql/statements/set-statistics-xml-transact-sql.md)  
  
  