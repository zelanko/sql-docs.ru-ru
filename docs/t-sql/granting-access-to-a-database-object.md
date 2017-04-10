---
title: "Предоставление доступа к объекту базы данных | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
helpviewer_keywords: 
  - "предоставление доступа к объекту базы данных"
ms.assetid: a44d9bbf-f58e-4734-b7f4-eb3b492b777b
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Предоставление доступа к объекту базы данных
Будучи администратором, можно выполнять инструкцию SELECT из таблицы **Products** и представления **vw_Names**, а также выполнять процедуру **pr_Names**; однако Mary всего этого не может. Чтобы предоставить Mary необходимые разрешения, воспользуйтесь инструкцией GRANT.  
  
### Описание процедуры  
  
1.  Выполните следующую инструкцию, чтобы предоставить `Mary` разрешение на `EXECUTE` для хранимой процедуры `pr_Names` .  
  
    ```  
    GRANT EXECUTE ON pr_Names TO Mary;  
    GO  
    ```  
  
В данном сценарии Mary имеет доступ только к таблице **Products** посредством хранимой процедуры. Если Mary нужно выполнять инструкцию SELECT к представлению, нужно выполнить инструкцию `GRANT SELECT ON vw_Names TO Mary`. Чтобы удалить доступ к объектам базы данных, воспользуйтесь инструкцией REVOKE.  
  
> [!NOTE]  
> Если таблицей, представлением или хранимой процедурой не владеет та же схема, процесс предоставления прав становится более сложным.  
  
## Об инструкции GRANT  
Нужно иметь разрешение на EXECUTE, чтобы выполнить хранимую процедуру. Нужно иметь разрешения на SELECT, INSERT, UPDATE и DELETE, чтобы получить доступ к данным и изменять их. Инструкция GRANT также используется для других разрешений, например для разрешений на создание таблиц.  
  
## Следующая задача занятия  
[Сводка. Настройка разрешений на объекты базы данных](../t-sql/summary-configuring-permissions-on-database-objects.md)  
  
## См. также:  
[GRANT (Transact-SQL)](../t-sql/statements/grant-transact-sql.md)  
[REVOKE (Transact-SQL)](../t-sql/statements/revoke-transact-sql.md)  
  
  
  
