---
title: Предоставление доступа к объекту базы данных | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- granting access to database objects
ms.assetid: a44d9bbf-f58e-4734-b7f4-eb3b492b777b
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 19381b0c5dbe690a60b2c536a8da759205c08c31
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62643451"
---
# <a name="granting-access-to-a-database-object"></a>Предоставление доступа к объекту базы данных
  Будучи администратором, можно выполнять инструкцию SELECT из таблицы **Products** и представления **vw_Names**, а также выполнять процедуру **pr_Names**; однако Mary всего этого не может. Чтобы предоставить Mary необходимые разрешения, воспользуйтесь инструкцией GRANT.  
  
### <a name="procedure-title"></a>Описание процедуры  
  
1.  Выполните следующую инструкцию, чтобы предоставить `Mary` разрешение на `EXECUTE` для хранимой процедуры `pr_Names` .  
  
    ```  
    GRANT EXECUTE ON pr_Names TO Mary;  
    GO  
    ```  
  
 В данном сценарии Mary имеет доступ только к таблице **Products** посредством хранимой процедуры. Если Mary нужно выполнять инструкцию SELECT к представлению, нужно выполнить инструкцию `GRANT SELECT ON vw_Names TO Mary`. Чтобы удалить доступ к объектам базы данных, воспользуйтесь инструкцией REVOKE.  
  
> [!NOTE]  
>  Если таблицей, представлением или хранимой процедурой не владеет та же схема, процесс предоставления прав становится более сложным.  
  
## <a name="about-grant"></a>Об инструкции GRANT  
 Нужно иметь разрешение на EXECUTE, чтобы выполнить хранимую процедуру. Нужно иметь разрешения на SELECT, INSERT, UPDATE и DELETE, чтобы получить доступ к данным и изменять их. Инструкция GRANT также используется для других разрешений, например для разрешений на создание таблиц.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Сводка. Настройка разрешений на объекты базы данных](lesson-2-5-summary-configuring-permissions-on-database-objects.md)  
  
## <a name="see-also"></a>См. также  
 [GRANT (Transact-SQL)](/sql/t-sql/statements/grant-transact-sql)   
 [REVOKE (Transact-SQL)](/sql/t-sql/statements/revoke-transact-sql)  
  
  
