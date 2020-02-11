---
title: Удалите ссылки на устаревшие системные хранимые процедуры | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- undocumented system stored procedures [SQL Server]
- system stored procedures [SQL Server]
ms.assetid: 487d24fc-41d5-495e-843c-0ac974ec472f
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2e841956adf08f9ac14a3f1360839e9132bf9cd6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66093104"
---
# <a name="remove-references-to-deprecated-system-stored-procedures"></a>Удаление ссылок на устаревшие системные хранимые процедуры
  Советник по переходу обнаружил инструкции, которые ссылаются на недокументированные системные хранимые процедуры и расширенные хранимые процедуры, более не доступные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Выполнение инструкций, ссылающихся на эти объекты, приведет к ошибке. Не пользуйтесь недокументированными системными объектами и API-интерфейсами, поскольку их функциональные возможности могут быть изменены или удалены в следующей версии без уведомления.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
  
### <a name="documented-system-stored-procedures"></a>Документированные системные хранимые процедуры  
 Были удалены следующие системные хранимые процедуры.  
  
-   sp_addalias  
  
-   sp_addgroup  
  
-   sp_changegroup  
  
-   sp_dropgroup  
  
-   sp_helpgroup  
  
### <a name="undocumented-system-stored-procedures"></a>Недокументированные системные хранимые процедуры  
 Следующие недокументированные системные хранимые процедуры и расширенные хранимые процедуры были удалены.  
  
-   sp_articlesynctranprocs  
  
-   sp_diskdefault  
  
-   sp_EventLog  
  
-   sp_GetMBCSCharLen  
  
-   sp_helplog  
  
-   sp_helpsql  
  
-   sp_IsMBCSLeadByte  
  
-   sp_lock2  
  
-   sp_MSget_current_activity  
  
-   sp_MSset_current_activity  
  
-   sp_MSobjessearch  
  
-   xp_enum_ActiveScriptEngines  
  
-   xp_eventlog  
  
-   xp_GetAdminGroupName  
  
-   xp_GetFileDetails  
  
-   xp_GetLocalSystemAccountName  
  
-   xp_IsNTAdmin  
  
-   xp_MSLocalSystem  
  
-   xp_MSnt2000  
  
-   xp_MSplatform  
  
-   xp_SetSecurity  
  
-   xp_varbintohexstr  
  
## <a name="corrective-action"></a>Действие по исправлению  
  
### <a name="documented-system-stored-procedures"></a>Документированные системные хранимые процедуры  
 Измените приложения в соответствии со следующей таблицей.  
  
|Вместо|выполните следующее:|  
|----------------|-------------|  
|sp_addalias|Псевдонимы заменены сочетанием учетных записей пользователей и ролями базы данных. Дополнительные сведения см. в разделах «CREATE USER (Transact-SQL)» и «CREATE ROLE (Transact-SQL)» электронной документации по SQL Server. В обновленных базах данных псевдонимы необходимо удалить с помощью процедуры sp_dropalias.|  
|sp_addgroupsp_changegroup<br /><br /> sp_dropgroup<br /><br /> sp_helpgroup|Используйте роли. Дополнительные сведения см. в разделах «Роли уровня сервера» и «Роли уровня базы данных» в электронной документации по SQL Server.|  
  
### <a name="undocmented-system-stored-procedures"></a>Недокументированные системные хранимые процедуры  
 Чтобы заменить недокументированные системные хранимые процедуры, можно создать хранимые процедуры CLR с равнозначной функциональностью. Дополнительные сведения см. в разделе «Хранимые процедуры CLR» электронной документации по SQL Server.  
  
## <a name="see-also"></a>См. также:  
 [Проблемы обновления ядро СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Советник по переходу SQL Server 2014 &#91;New&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
