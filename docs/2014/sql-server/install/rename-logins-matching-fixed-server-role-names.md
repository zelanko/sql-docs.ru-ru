---
title: Переименовать имена входа, совпадающие имена предопределенных ролей сервера | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- user-defined login names [SQL Server]
- fixed server roles [SQL Server]
- renamed logins [SQL Server]
- logins [SQL Server], names
ms.assetid: 10a1d77c-3153-474f-a6a0-969556794467
caps.latest.revision: 18
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0064e08000454f485846b45fb0cc3d37c0afd031
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155615"
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
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
