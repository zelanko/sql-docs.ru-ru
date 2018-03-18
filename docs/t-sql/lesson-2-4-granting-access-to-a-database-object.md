---
title: "Предоставление доступа к объекту базы данных | Документы Майкрософт"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- granting access to database objects
ms.assetid: a44d9bbf-f58e-4734-b7f4-eb3b492b777b
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 5ccbacfe52541c59e12b992220f40806cae46bca
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="lesson-2-4---granting-access-to-a-database-object"></a>Урок 2–4. Предоставление доступа к объекту базы данных
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)] Будучи администратором, можно выполнять инструкцию SELECT из таблицы **Products** и представления **vw_Names**, а также выполнять процедуру **pr_Names**; однако Мэри всего этого не может. Чтобы предоставить Mary необходимые разрешения, воспользуйтесь инструкцией GRANT.  
  
### <a name="procedure-title"></a>Описание процедуры  
  
1.  Выполните следующую инструкцию, чтобы предоставить `Mary` разрешение на `EXECUTE` для хранимой процедуры `pr_Names` .  
  
    ```  
    GRANT EXECUTE ON pr_Names TO Mary;  
    GO  
    ```  
  
В данном сценарии Mary имеет доступ только к таблице **Products** посредством хранимой процедуры. Если Mary нужно выполнять инструкцию SELECT к представлению, нужно выполнить инструкцию `GRANT SELECT ON vw_Names TO Mary`. Чтобы удалить доступ к объектам базы данных, воспользуйтесь инструкцией REVOKE.  
  
> [!NOTE]  
> Если таблицей, представлением или хранимой процедурой не владеет та же схема, процесс предоставления прав становится более сложным.  
  
## <a name="about-grant"></a>Об инструкции GRANT  
Нужно иметь разрешение на EXECUTE, чтобы выполнить хранимую процедуру. Нужно иметь разрешения на SELECT, INSERT, UPDATE и DELETE, чтобы получить доступ к данным и изменять их. Инструкция GRANT также используется для других разрешений, например для разрешений на создание таблиц.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
[Сводка. Настройка разрешений на объекты базы данных](../t-sql/lesson-2-5-summary-configuring-permissions-on-database-objects.md)  
  
## <a name="see-also"></a>См. также:  
[GRANT (Transact-SQL)](../t-sql/statements/grant-transact-sql.md)  
[REVOKE (Transact-SQL)](../t-sql/statements/revoke-transact-sql.md)  
  
  
  
