---
title: Удаление индекса | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- removing indexes
- deleting indexes
- dropping indexes
- indexes [SQL Server], dropping
- index deletions [SQL Server]
ms.assetid: fd38a0ed-26c4-4c76-9ef7-e0a16147329d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4552ba701782e5790f95f54c0c1c66f82573f1e3
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85025617"
---
# <a name="delete-an-index"></a>Удаление индекса
  В этом разделе описано удаление индекса в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Удаление индекса с помощью**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
 Индексы, созданные с помощью ограничений уникальности и первичных ключей, нельзя удалить этим способом. Вместо этого следует удалять сами ограничения. Для удаления ограничения и соответствующего индекса используется инструкция [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) с предложением DROP CONSTRAINT на языке [!INCLUDE[tsql](../../includes/tsql-md.md)]. Дополнительные сведения см. в статье [Delete Primary Keys](../tables/delete-primary-keys.md).  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER для таблицы или представления. По умолчанию это разрешение предоставляется предопределенной роли сервера **sysadmin** и предопределенным ролям базы данных **db_ddladmin** и **db_owner** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-delete-an-index-by-using-object-explorer"></a>Удаление индекса в обозревателе объектов  
  
1.  В обозревателе объектов разверните базу данных, содержащую таблицу, в которой необходимо удалить индекс.  
  
2.  Разверните папку **Таблицы**.  
  
3.  Разверните таблицу, содержащую индекс, который нужно удалить.  
  
4.  Разверните папку **Индексы**.  
  
5.  Щелкните правой кнопкой мыши индекс, который необходимо удалить, и выберите пункт **Удалить**.  
  
6.  В диалоговом окне **Удаление объекта** убедитесь, что в сетке **Объекты для удаления** указан нужный индекс, и нажмите кнопку **ОК**.  
  
#### <a name="to-delete-an-index-using-table-designer"></a>Удаление индекса при помощи конструктора таблиц  
  
1.  В обозревателе объектов разверните базу данных, содержащую таблицу, в которой необходимо удалить индекс.  
  
2.  Разверните папку **Таблицы**.  
  
3.  Правой кнопкой мыши щелкните таблицу, содержащую индекс, который необходимо удалить, и выберите «Конструктор».  
  
4.  В меню **Конструктор таблиц** выберите пункт **Индексы и ключи**.  
  
5.  В диалоговом окне **Индексы и ключи** выберите индекс, который хотите удалить.  
  
6.  Щелкните **Удалить**.  
  
7.  Щелкните **Закрыть**.  
  
8.  В меню **Файл** выберите пункт **Сохранить**_имя_таблицы_.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-delete-an-index"></a>Удаление индекса  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- delete the IX_ProductVendor_BusinessEntityID index  
    -- from the Purchasing.ProductVendor table  
    DROP INDEX IX_ProductVendor_BusinessEntityID   
        ON Purchasing.ProductVendor;  
    GO  
    ```  
  
 Дополнительные сведения см. в статье [DROP INDEX (Transact-SQL)](/sql/t-sql/statements/drop-index-transact-sql).  
  
  
