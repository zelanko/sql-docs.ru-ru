---
title: "Сохранение плана выполнения в формате XML | Документация Майкрософт"
ms.custom: 
ms.date: 08/21/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: performance
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML query plans [SQL Server]
- opening execution plans
- XML Showplans [SQL Server]
- execution plans [SQL Server], saving
- saving execution plans
ms.assetid: c439e53b-56f3-4442-97c6-dabd48a203d8
caps.latest.revision: "25"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: caa43dba8d4ce0abdd5dc14f113a5fbfcf58d3ec
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="save-an-execution-plan-in-xml-format"></a>Сохранение плана выполнения в формате XML
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)] Используйте среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], чтобы сохранить планы выполнения в XML-файле и открыть их для просмотра.  
  
 Чтобы использовать функциональные возможности плана выполнения в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]или параметры XML Showplan SET, пользователи должны иметь соответствующие разрешения на выполнение запроса [!INCLUDE[tsql](../../includes/tsql-md.md)] , для которого формируется план выполнения, и им нужно предоставить разрешение SHOWPLAN для всех баз данных, на которые ссылается запрос.  
  
### <a name="to-save-a-query-plan-by-using-the-xml-showplan-set-options"></a>Сохранение плана запроса с помощью параметров XML Showplan SET  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] откройте редактор запросов и подключитесь к компоненту [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Включите [SHOWPLAN_XML](../../t-sql/statements/set-showplan-xml-transact-sql.md) с помощью следующей инструкции:  
  
    ```sql  
    SET SHOWPLAN_XML ON;  
    GO  
    ```  
  
     Чтобы включить [STATISTICS XML](../../t-sql/statements/set-statistics-xml-transact-sql.md), воспользуйтесь следующей инструкцией:  
  
    ```sql  
    SET STATISTICS XML ON;  
    GO  
    ```  
  
     > [!NOTE] 
     > Инструкция SHOWPLAN_XML создает сведения о плане выполнения запроса во время компиляции, но не выполняет запрос. Этот план также называется **расчетным** планом выполнения. Инструкция STATISTICS XML создает сведения о плане выполнения запроса для среды выполнения и выполняет запрос. Этот план также называется **фактическим** планом выполнения.  
  
3.  Выполните запрос. Пример  
  
    ```sql  
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
  
4.  На панели **Результаты** щелкните правой кнопкой мыши поле **Microsoft SQL Server XML Showplan** , содержащее план запроса, и выберите пункт **Сохранить результаты как**.  
  
5.  В диалоговом окне **Сохранить** **результаты** \<сетка или текст> найдите поле **Тип файла** и выберите в нем значение **Все файлы (\*.\*)**.  
  
6.  В поле **Имя файла** укажите имя в формате \<имя**>.sqlplan**, после чего нажмите кнопку **Сохранить**.  
  
### <a name="to-save-an-execution-plan-by-using-sql-server-management-studio-options"></a>Сохранение плана выполнения с помощью параметров среды SQL Server Management Studio  
  
1.  Сформируйте либо прогнозируемый, либо фактический план выполнения с помощью среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Дополнительные сведения см. в разделах [Отображение расчетного плана выполнения](../../relational-databases/performance/display-the-estimated-execution-plan.md) или [Отображение фактического плана выполнения](../../relational-databases/performance/display-an-actual-execution-plan.md).  
  
2.  На вкладке **План выполнения** панели результатов щелкните правой кнопкой мыши графический план выполнения и выберите **Сохранить план выполнения как**.  
  
     Как альтернативный вариант можно также выбрать **Сохранить план выполнения как** в меню **Файл** .  
  
3.  В диалоговом окне **Сохранение** убедитесь, что в поле **Тип файла** установлено значение **Файлы плана выполнения (\*.sqlplan)**.  
  
4.  В поле **Имя файла** укажите имя в формате \<имя**>.sqlplan**, после чего нажмите кнопку **Сохранить**.  
  
### <a name="to-open-a-saved-xml-query-plan-in-sql-server-management-studio"></a>Открытие сохраненного плана запроса в формате XML в среде SQL Server Management Studio  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]в меню **Файл** выберите **Открыть**, а затем нажмите **Файл**.  
  
2.  В диалоговом окне **Открытие файла** установите в поле **Файлы типа** значение **Файлы плана выполнения (\*.sqlplan)**, чтобы получить отфильтрованный список сохраненных файлов XML с планами запросов.  
  
3.  Выберите файл плана запроса XML, который нужно просмотреть, и нажмите **Открыть**.  
  
     Также можно дважды щелкнуть файл с расширением **sqlplan**в проводнике Windows. План откроется в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [SET SHOWPLAN_XML (Transact-SQL)](../../t-sql/statements/set-showplan-xml-transact-sql.md)   
 [SET STATISTICS XML (Transact-SQL)](../../t-sql/statements/set-statistics-xml-transact-sql.md)  
  
  
