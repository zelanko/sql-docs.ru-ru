---
title: Изменение данных через представление | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- data modifications [SQL Server], views
- views [SQL Server], modifying data through
- modifying data [SQL Server], views
ms.assetid: 410e2812-4ebe-48b2-b95f-c7784f1c4336
author: stevestein
ms.author: sstein
ms.openlocfilehash: df1eb4a33d1d10e63363e52760dad805b20c0a8f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85014227"
---
# <a name="modify-data-through-a-view"></a>Изменение данных через представление
  Изменить данные столбца базовой таблицы можно в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Изменение данных таблицы с помощью представления с использованием следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   См. раздел "Обновляемые представления" статьи [CREATE VIEW (Transact-SQL)](/sql/t-sql/statements/create-view-transact-sql).  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Необходимы разрешения UPDATE, INSERT или DELETE для целевой таблицы в зависимости от выполняемого действия.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-modify-table-data-through-a-view"></a>Изменение данных таблицы с помощью представления  
  
1.  В **обозревателе объектов**разверните базу данных, содержащую представление, а затем разверните **Представления**.  
  
2.  Щелкните правой кнопкой мыши представление и выберите **Изменить 200 верхних строк**.  
  
3.  Может потребоваться изменение инструкции SELECT на панели **SQL** для получения строк, которые необходимо изменить.  
  
4.  На панели **Результаты** найдите строку для изменения или удаления. Чтобы удалить строку, щелкните правой кнопкой мыши строку и выберите **Удалить**. Чтобы изменить данные в одном или нескольких столбцах, измените данные в столбце.  
  
    > [!IMPORTANT]  
    >  Нельзя удалить строку, если представление ссылается на несколько базовых таблиц. Можно обновлять только те столбцы, которые принадлежат к одной базовой таблице.  
  
5.  Чтобы вставить строку, прокрутите строки вниз до конца и вставьте новые значения.  
  
    > [!IMPORTANT]  
    >  Нельзя вставить строку, если представление ссылается на несколько базовых таблиц.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-update-table-data-through-a-view"></a>Обновление данных таблицы с помощью представления  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере изменяется значение в столбцах `StartDate` и `EndDate` для определенного сотрудника путем создания ссылки на столбцы в представлении `HumanResources.vEmployeeDepartmentHistory`. Это представление возвращает значения из двух таблиц. Эта инструкция была выполнена успешно, потому что изменялись столбцы только одной из базовых таблиц.  
  
    ```  
    USE AdventureWorks2012 ;   
    GO  
    UPDATE HumanResources.vEmployeeDepartmentHistory  
    SET StartDate = '20110203', EndDate = GETDATE()   
    WHERE LastName = N'Smith' AND FirstName = 'Samantha';   
    GO  
    ```  
  
 Дополнительные сведения см. в статье [UPDATE (Transact-SQL)](/sql/t-sql/queries/update-transact-sql).  
  
#### <a name="to-insert-table-data-through-a-view"></a>Вставка данных таблицы с помощью представления  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере выполняется вставка новой строки в базовую таблицу `HumanResouces.Department` путем указания соответствующих столбцов в представлении `HumanResources.vEmployeeDepartmentHistory`. Эта инструкция была выполнена успешно, поскольку были указаны только столбцы из одной базовой таблицы, а другие столбцы в базовой таблице имеют значения по умолчанию.  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    INSERT INTO HumanResources.vEmployeeDepartmentHistory (Department, GroupName)   
    VALUES ('MyDepartment', 'MyGroup');   
    GO  
    ```  
  
 Дополнительные сведения см. в статье [INSERT (Transact-SQL)](/sql/t-sql/statements/insert-transact-sql).  
  
  
