---
title: Удаление первичных ключей | Документация Майкрософт
ms.custom: ''
ms.date: 07/25/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- removing primary keys
- deleting primary keys
- primary keys [SQL Server], deleting
ms.assetid: c472e465-7bdd-4d74-8fc9-e47fca007ccb
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6cd4fecacab3343c5440db44cc2e03f8874b3e86
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67986465"
---
# <a name="delete-primary-keys"></a>Удаление первичных ключей
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Удалить первичный ключ в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] можно с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. При удалении первичного ключа удаляется и соответствующий индекс.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Удаление первичного ключа с помощью следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требуется разрешение ALTER на таблицу.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-delete-a-primary-key-constraint-using-object-explorer"></a>Удаление ограничения первичного ключа с помощью обозревателя объектов  
  
1.  В Обозревателе объектов разверните таблицу, которая содержит первичный ключ, и разверните узел **Ключи**.  
  
2.  Щелкните ключ правой кнопкой мыши и выберите команду **Удалить**.  
  
3.  В диалоговом окне **Удаление объекта** убедитесь в том, что выбран правильный ключ, и нажмите кнопку **ОК**.  
  
#### <a name="to-delete-a-primary-key-constraint-using-table-designer"></a>Удаление ограничения первичного ключа с помощью конструктора таблиц  
  
1.  В обозревателе объектов щелкните таблицу с первичным ключом правой кнопкой мыши и выберите пункт **Конструктор**.  
  
2.  В сетке таблицы щелкните правой кнопкой строку с первичным ключом и выберите пункт **Удалить первичный ключ** , чтобы переключить параметр.  
  
    > [!NOTE]  
    >  Чтобы отменить это действие, закройте таблицу, не сохраняя изменений. Удаление первичного ключа не может быть отменено без потери всех других изменений, сделанных в таблице.  
  
3.  В меню **Файл** выберите пункт **Сохранить**_table name_.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-delete-a-primary-key-constraint"></a>Удаление ограничения первичного ключа  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере сначала определяется имя ограничения первичного ключа, а затем удаляется ограничение.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Return the name of primary key.  
    SELECT name  
    FROM sys.key_constraints  
    WHERE type = 'PK' AND OBJECT_NAME(parent_object_id) = N'TransactionHistoryArchive';  
    GO  
    -- Delete the primary key constraint.  
    ALTER TABLE Production.TransactionHistoryArchive  
    DROP CONSTRAINT PK_TransactionHistoryArchive_TransactionID;   
    GO  
    ```  
  
 Дополнительные сведения см. в разделах [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md) и [sys.key_constraints (Transact-SQL)](../../relational-databases/system-catalog-views/sys-key-constraints-transact-sql.md)  
  
###  <a name="TsqlExample"></a>  
