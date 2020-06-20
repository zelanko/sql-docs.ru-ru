---
title: Сохранение плана выполнения в формате XML | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- XML query plans [SQL Server]
- opening execution plans
- XML Showplans [SQL Server]
- execution plans [SQL Server], saving
- saving execution plans
ms.assetid: c439e53b-56f3-4442-97c6-dabd48a203d8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 84ed341d186993ed77260e8361156b324c597839
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85047888"
---
# <a name="save-an-execution-plan-in-xml-format"></a>Сохранение плана выполнения в формате XML
  Используйте среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , чтобы сохранить планы выполнения в XML-файле и открыть их для просмотра.  
  
 Чтобы использовать функциональные возможности плана выполнения в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]или параметры XML Showplan SET, пользователи должны иметь соответствующие разрешения на выполнение запроса [!INCLUDE[tsql](../../includes/tsql-md.md)] , для которого формируется план выполнения, и им нужно предоставить разрешение SHOWPLAN для всех баз данных, на которые ссылается запрос.  
  
### <a name="to-save-a-query-plan-by-using-the-xml-showplan-set-options"></a>Сохранение плана запроса с помощью параметров XML Showplan SET  
  
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
  
4.  На панели **Результаты** щелкните правой кнопкой мыши поле **Microsoft SQL Server XML Showplan** , содержащее план запроса, и выберите пункт **Сохранить результаты как**.  
  
5.  В **Save** \<Grid or Text> диалоговом окне Сохранить **результаты** в поле **Тип файла** выберите **все файлы ( \* . \* )**.  
  
6.  В поле **имя файла** введите имя в формате \<name**> . sqlplan * *, а затем нажмите кнопку **сохранить**.  
  
### <a name="to-save-an-execution-plan-by-using-sql-server-management-studio-options"></a>Сохранение плана выполнения с помощью параметров среды SQL Server Management Studio  
  
1.  Сформируйте либо прогнозируемый, либо фактический план выполнения с помощью среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Дополнительные сведения см. в разделах [Отображение предполагаемого плана выполнения](display-the-estimated-execution-plan.md) или [Отображение фактического плана выполнения](display-an-actual-execution-plan.md).  
  
2.  На вкладке **План выполнения** панели результатов щелкните правой кнопкой мыши графический план выполнения и выберите **Сохранить план выполнения как**.  
  
     Как альтернативный вариант можно также выбрать **Сохранить план выполнения как** в меню **Файл** .  
  
3.  В диалоговом окне **Сохранение** убедитесь, что в поле **Тип файла** установлено значение **Файлы плана выполнения (\*.sqlplan)**.  
  
4.  В поле **имя файла** введите имя в формате \<name**> . sqlplan * *, а затем нажмите кнопку **сохранить**.  
  
### <a name="to-open-a-saved-xml-query-plan-in-sql-server-management-studio"></a>Открытие сохраненного плана запроса в формате XML в среде SQL Server Management Studio  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]в меню **Файл** выберите **Открыть**, а затем нажмите **Файл**.  
  
2.  В диалоговом окне **Открытие файла** установите в поле **Файлы типа** значение **Файлы плана выполнения (\*.sqlplan)**, чтобы получить отфильтрованный список сохраненных файлов XML с планами запросов.  
  
3.  Выберите файл плана запроса XML, который нужно просмотреть, и нажмите **Открыть**.  
  
     Также можно дважды щелкнуть файл с расширением **sqlplan**в проводнике Windows. План откроется в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Настройка SHOWPLAN_XML &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-showplan-xml-transact-sql)   
 [SET STATISTICS XML (Transact-SQL)](/sql/t-sql/statements/set-statistics-xml-transact-sql)  
  
  
