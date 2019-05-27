---
title: Переименовать имена входа, совпадающие имена предопределенных ролей сервера | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- user-defined login names [SQL Server]
- fixed server roles [SQL Server]
- renamed logins [SQL Server]
- logins [SQL Server], names
ms.assetid: 10a1d77c-3153-474f-a6a0-969556794467
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d983f514f7cc0185021de40f153d78fd6e4dd112
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66092880"
---
# <a name="rename-logins-matching-fixed-server-role-names"></a>Переименование имен входа, которые совпадают с именами предопределенной роли сервера
  Помощник по обновлению обнаружил одно или несколько определяемых пользователем имен входа, совпадающих с именами предопределенных ролей сервера. Имена предопределенных ролей сервера зарезервированы. Прежде чем производить обновление, измените имя входа.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 Следующие имена предопределенных ролей сервера зарезервированы и не могут быть использованы как пользовательские имена входа.  
  
-   **sysadmin**  
  
-   **serveradmin**  
  
-   **setupadmin**  
  
-   **securityadmin**  
  
-   **processadmin**  
  
-   **dbcreator**  
  
-   **diskadmin**  
  
-   **bulkadmin**  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Прежде чем производить обновление, выполните следующие шаги.  
  
1.  Зарегистрируйте идентификаторы безопасности (SID) имен входа, выполнив следующую инструкцию.  
  
    ```  
    SELECT name, sid   
    FROM master.dbo.syslogins   
    WHERE name IN('sysadmin', 'serveradmin','setupadmin', 'securityadmin','processadmin', 'dbcreator','diskadmin','bulkadmin')  
    ```  
  
2.  Удалите имена входа.  
  
3.  Используйте **sp_addlogin** системной процедуры для создания новых имен входа. Укажите SID, возвращенное на шаге 1 в **@sid** параметра для каждого соответствующего имени входа.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
