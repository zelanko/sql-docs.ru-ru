---
title: "Удаление представлений | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-views
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dropping views
- deleting views
- views [SQL Server], deleting
- removing views
ms.assetid: 6823c7f8-06ca-4bda-8482-7092f03d52a0
caps.latest.revision: "15"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ac6e4763f270e45303f425d58226682184754fec
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="delete-views"></a>Удаление представлений
  Представления можно удалить в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Удаление представления из базы данных с использованием следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   При удалении представления из системного каталога удаляется его определение и другие сведения о нем. Все связанные с представлением разрешения также удаляются.  
  
-   Любое представление таблицы, удаленной с помощью инструкции `DROP TABLE` , нужно удалять явно, с помощью инструкции `DROP VIEW`.  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Требует либо разрешения CONTROL для схемы SCHEMA, либо разрешения CONTROL для объекта OBJECT.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-delete-a-view-from-a-database"></a>Удаление представления из базы данных  
  
1.  В **обозревателе объектов**разверните базу данных, в которой содержится представление, подлежащее удалению, а затем разверните папку **Представления** .  
  
2.  Щелкните правой кнопкой мыши представление, которое требуется удалить, и выберите **Удалить**.  
  
3.  В диалоговом окне **Удаление объекта** нажмите кнопку **ОК**.  
  
    > [!IMPORTANT]  
    >  Щелкните **Показать зависимости** в диалоговом окне **Удаление объекта** , чтобы открыть диалоговое окно *имя_представления***Зависимости** . При этом будут отображены все объекты, зависящие от представления, и все объекты, от которых зависит представление.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-delete-a-view-from-a-database"></a>Удаление представления из базы данных  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В примере указанное представление удаляется только в том случае, если оно существует.  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    IF OBJECT_ID ('HumanResources.EmployeeHireDate', 'V') IS NOT NULL  
    DROP VIEW HumanResources.EmployeeHireDate;  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [DROP VIEW (Transact-SQL)](../../t-sql/statements/drop-view-transact-sql.md).  
  
  
