---
description: Управление безопасностью триггеров
title: Управление безопасностью триггеров | Документация Майкрософт
ms.custom: ''
ms.date: 06/22/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- triggers [SQL Server], security
ms.assetid: e94720a8-a3a2-4364-b0a3-bbe86e3ce4d5
author: rothja
ms.author: jroth
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 73e56eb0ffcc4996ddd6903f2e79c14947b9a450
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88485413"
---
# <a name="manage-trigger-security"></a>Управление безопасностью триггеров

[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Как триггеры DML, так и триггеры DDL по умолчанию выполняются в контексте того пользователя, который вызывает триггер. Это пользователь, который выполняет инструкцию, вызывающую запуск триггера. Например, если пользователь **Mary** выполняет инструкцию DELETE, которая запускает триггер DML **DML_trigMary** , то код внутри **DML_trigMary** выполняется в контексте прав доступа пользователя **Mary**. Этим поведением по умолчанию могут воспользоваться те пользователи, которые хотят внести небезопасный код в экземпляр базы данных или сервера. Например, следующий триггер DDL создан пользователем **JohnDoe**:  

```sql
CREATE TRIGGER DDL_trigJohnDoe
ON DATABASE
FOR ALTER_TABLE
AS
SET NOCOUNT ON;

BEGIN TRY
  EXEC(N'
    USE [master];
    GRANT CONTROL SERVER TO [JohnDoe];
');
END TRY
BEGIN CATCH
  DECLARE @DoNothing INT;
END CATCH;
GO
```

В этом триггере подразумевается, что как только пользователь с разрешением на выполнение инструкции `GRANT CONTROL SERVER`, например член предопределенной роли сервера **sysadmin**, выполнит инструкцию `ALTER TABLE`, пользователь **JohnDoe** получит разрешение `CONTROL SERVER`. Другими словами, хотя **JohnDoe** не может предоставить разрешение `CONTROL SERVER` самому себе, он создал код триггера, который предоставит ему разрешение работать с повышенными правами доступа. Эта уязвимость относится как к триггерам DML, так и к триггерам DDL.  
  
## <a name="trigger-security-best-practices"></a>Способы защиты триггеров  
 Чтобы предотвратить выполнение кода триггера с повышенными правами доступа, примите следующие меры.  
  
::: moniker range=">=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current"

-   Проверьте базу данных и экземпляр сервера на наличие триггеров DDL и DDL. Для этого выполните соответствующие запросы к представлениям каталогов [sys.triggers](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md) и [sys.server_triggers](../../relational-databases/system-catalog-views/sys-server-triggers-transact-sql.md) . Следующий запрос возвращает все триггеры DML и DDL уровня базы данных в текущей базе данных, а также все триггеры DDL уровня сервера на экземпляре сервера.  
  
    ```sql
    SELECT type, name, parent_class_desc FROM sys.triggers
    UNION ALL
    SELECT type, name, parent_class_desc FROM sys.server_triggers;
    ```  

   > [!NOTE]
   > Для [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] доступен только **sys.triggers**, если не используется [!INCLUDE[ssSDSMIfull](../../includes/sssdsmifull-md.md)].

::: moniker-end

::: moniker range="=azuresqldb-current||=sqlallproducts-allversions"

-   Проверьте базу данных на наличие триггеров DDL и DDL. Для этого выполните соответствующие запросы к представлению каталога [sys.triggers](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md). Следующий запрос возвращает все триггеры DML и триггеры DDL уровня базы данных в текущей базе данных:  
  
    ```sql
    SELECT type, name, parent_class_desc FROM sys.triggers;
    ```  
  
::: moniker-end

-   С помощью инструкции [DISABLE TRIGGER](../../t-sql/statements/disable-trigger-transact-sql.md) запретите триггеры, которые могут нарушить целостность базы данных или сервера при выполнении с повышенными правами доступа. Следующая инструкция отключает все триггеры DDL уровня базы данных в текущей базе данных:  
  
    ```sql
    DISABLE TRIGGER ALL ON DATABASE;
    ```  
  
     Эта инструкция отключает все триггеры DDL уровня сервера на экземпляре сервера:  
  
    ```sql
    DISABLE TRIGGER ALL ON ALL SERVER;
    ```  
  
     Эта инструкция отключает все триггеры DML в текущей базе данных:  
  
    ```sql
    DECLARE @schema_name sysname, @trigger_name sysname, @object_name sysname;
    DECLARE @sql nvarchar(max);
    DECLARE trig_cur CURSOR FORWARD_ONLY READ_ONLY FOR
        SELECT SCHEMA_NAME(schema_id) AS schema_name,
            name AS trigger_name,
            OBJECT_NAME(parent_object_id) AS object_name
        FROM sys.objects WHERE type IN ('TR', 'TA');

    OPEN trig_cur;
    FETCH NEXT FROM trig_cur INTO @schema_name, @trigger_name, @object_name;
  
    WHILE @@FETCH_STATUS = 0
    BEGIN
        SELECT @sql = N'DISABLE TRIGGER ' + QUOTENAME(@schema_name) + N'.'
            + QUOTENAME(@trigger_name)
            + N' ON ' + QUOTENAME(@schema_name) + N'.'
            + QUOTENAME(@object_name) + N'; ';
        EXEC (@sql);
        FETCH NEXT FROM trig_cur INTO @schema_name, @trigger_name, @object_name;
    END;
    GO

    -- Verify triggers are disabled. Should return an empty result set.
    SELECT * FROM sys.triggers WHERE is_disabled = 0;
    GO

    CLOSE trig_cur;
    DEALLOCATE trig_cur;
    ```  
  
## <a name="see-also"></a>См. также:  
 [CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md)   
 [Триггеры DML](../../relational-databases/triggers/dml-triggers.md)   
 [Триггеры DDL](../../relational-databases/triggers/ddl-triggers.md)  
 [Триггеры входа](../../relational-databases/triggers/logon-triggers.md)  
  
