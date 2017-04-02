---
title: "Удаление первичных ключей | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-tables"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "удаление первичных ключей"
  - "удаление первичных ключей"
  - "первичные ключи [SQL Server], удаление"
ms.assetid: c472e465-7bdd-4d74-8fc9-e47fca007ccb
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# Удаление первичных ключей
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Удалить первичный ключ в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] можно с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. При удалении первичного ключа удаляется и соответствующий индекс.  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Безопасность](#Security)  
  
-   **Удаление первичного ключа с помощью следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Требуется разрешение ALTER на таблицу.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### Удаление ограничения первичного ключа с помощью обозревателя объектов  
  
1.  В Обозревателе объектов разверните таблицу, которая содержит первичный ключ, и разверните узел **Ключи**.  
  
2.  Щелкните ключ правой кнопкой мыши и выберите команду **Удалить**.  
  
3.  В диалоговом окне **Удаление объекта** убедитесь в том, что выбран правильный ключ, и нажмите кнопку **ОК**.  
  
#### Удаление ограничения первичного ключа с помощью конструктора таблиц  
  
1.  В обозревателе объектов щелкните таблицу с первичным ключом правой кнопкой мыши и выберите пункт **Конструктор**.  
  
2.  В сетке таблицы щелкните правой кнопкой строку с первичным ключом и выберите пункт **Удалить первичный ключ**, чтобы переключить параметр.  
  
    > [!NOTE]  
    >  Чтобы отменить это действие, закройте таблицу, не сохраняя изменений. Удаление первичного ключа не может быть отменено без потери всех других изменений, сделанных в таблице.  
  
3.  В меню **Файл** выберите пункт **Сохранить***table name*.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### Удаление ограничения первичного ключа  
  
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