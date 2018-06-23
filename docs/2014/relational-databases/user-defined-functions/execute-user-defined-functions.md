---
title: Выполнение определяемых пользователем функций | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-udf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- invoking user-defined functions
- user-defined functions [SQL Server], executing
ms.assetid: 0de7744d-9b73-463f-ae80-e31a020004b5
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6961d8306ff4b5a5f5280d25e3657952d0890063
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097029"
---
# <a name="execute-user-defined-functions"></a>Выполнение определяемых пользователем функций
  Определяемую пользователем функцию можно выполнить в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Для выполнения определяемой пользователем функции с помощью:**  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
 В Transact-SQL параметры могут передаваться через *value* или с помощью @*parameter_name*=*value.* . Параметр не является частью транзакции, поэтому если он изменился в транзакции, которая впоследствии подверглась откату, то прежнее значение параметра не восстанавливается. Возвращаемым вызывающему значением всегда является то значение, которое существует на момент выхода из модуля.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 На выполнение инструкции EXECUTE разрешения не требуются. Однако необходимы разрешения на защищаемые объекты, на которые ссылается командная строка в инструкции EXECUTE. Например, если строка содержит инструкцию INSERT, вызывающий инструкцию EXECUTE пользователь должен иметь разрешение INSERT на целевую таблицу. Разрешения проверяются в месте нахождения инструкции EXECUTE, даже если она содержится внутри модуля. Дополнительные сведения см. в разделе [EXECUTE (Transact-SQL)](/sql/t-sql/language-elements/execute-transact-sql).  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-execute-a-user-defined-function"></a>Выполнение определяемой пользователем функции  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Declares a variable and sets it to zero.  
    -- This variable is used to return the results of the function.  
    DECLARE @ret nvarchar(15)= NULL;   
  
    -- Executes the dbo.ufnGetSalesOrderStatusText function.  
    --The function requires a value for one parameter, @Status.   
    EXEC @ret = dbo.ufnGetSalesOrderStatusText @Status= 5;   
    --Returns the result in the message tab.  
    PRINT @ret;  
    ```  
  
 Дополнительные сведения см. в разделе [EXECUTE (Transact-SQL)](/sql/t-sql/language-elements/execute-transact-sql).  
  
  
