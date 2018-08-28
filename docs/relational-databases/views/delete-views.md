---
title: Удаление представлений | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: table-view-index, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- dropping views
- deleting views
- views [SQL Server], deleting
- removing views
ms.assetid: 6823c7f8-06ca-4bda-8482-7092f03d52a0
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 17859bdbaaf8a08569717c1d1cb64ab6eab6ff93
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43075945"
---
# <a name="delete-views"></a>Удаление представлений
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]
  Представления можно удалить в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Удаление представления из базы данных с использованием следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   При удалении представления из системного каталога удаляется его определение и другие сведения о нем. Все связанные с представлением разрешения также удаляются.  
  
-   Любое представление таблицы, удаленной с помощью инструкции `DROP TABLE` , нужно удалять явно, с помощью инструкции `DROP VIEW`.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требует либо разрешения CONTROL для схемы SCHEMA, либо разрешения CONTROL для объекта OBJECT.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-delete-a-view-from-a-database"></a>Удаление представления из базы данных  
  
1.  В **обозревателе объектов**разверните базу данных, в которой содержится представление, подлежащее удалению, а затем разверните папку **Представления** .  
  
2.  Щелкните правой кнопкой мыши представление, которое требуется удалить, и выберите **Удалить**.  
  
3.  В диалоговом окне **Удаление объекта** нажмите кнопку **ОК**.  
  
    > [!IMPORTANT]  
    >  Выберите команду **Показать зависимости** в диалоговом окне **Удаление объекта** , чтобы открыть диалоговое окно *Зависимости***имя представления**. При этом будут отображены все объекты, зависящие от представления, и все объекты, от которых зависит представление.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-delete-a-view-from-a-database"></a>Удаление представления из базы данных  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
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
  
  
