---
title: Переименовывать имена входа, совпадающие с именами предопределенных ролей сервера | Документация Майкрософт
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
ms.openlocfilehash: df9d9e51846e286c67a4773823207524755d15dc
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "72278214"
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
  
3.  Для создания новых имен входа используйте системную процедуру **sp_addlogin** . Укажите идентификатор безопасности, возвращенный на шаге 1 в параметре ** \@SID** для каждого соответствующего имени входа.  
  
## <a name="see-also"></a>См. также:  
 [Проблемы обновления ядро СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Советник по переходу SQL Server 2014 &#91;New&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
