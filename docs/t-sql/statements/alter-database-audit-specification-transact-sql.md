---
title: "ALTER DATABASE AUDIT SPECIFICATION (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_DATABASE_AUDIT_SPECIFICATION_TSQL
- ALTER DATABASE AUDIT SPECIFICATION
- ALTER_DATABASE_AUDIT_TSQL
- ALTER DATABASE AUDIT
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER DATABASE AUDIT SPECIFICATION statement
ms.assetid: 85f4e7e6-a330-4de0-9048-64f386ccc314
caps.latest.revision: 22
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 06d58a9ecce3175e021e7db484aeadbe41f3b372
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="alter-database-audit-specification-transact-sql"></a>ALTER DATABASE AUDIT SPECIFICATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет объект спецификации аудита базы данных с помощью компонента аудита [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в статье [Подсистема аудита SQL Server (компонент Database Engine)](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ALTER DATABASE AUDIT SPECIFICATION audit_specification_name  
{  
    [ FOR SERVER AUDIT audit_name ]  
    [ { { ADD | DROP } (   
           { <audit_action_specification> | audit_action_group_name }   
                )   
      } [, ...n] ]  
    [ WITH ( STATE = { ON | OFF } ) ]  
}  
[ ; ]  
<audit_action_specification>::=  
{  
      <action_specification>[ ,...n ] ON [ class :: ] securable   
     BY principal [ ,...n ]   
}  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *audit_specification_name*  
 Имя спецификации аудита.  
  
 *audit_name*  
 Имя аудита, к которому применяется эта спецификация.  
  
 *audit_action_specification*  
 Имя одного или нескольких действий уровня базы данных, доступных для аудита. Список групп действий аудита см. в разделе [группы действий подсистемы аудита SQL Server и действия](../../relational-databases/security/auditing/sql-server-audit-action-groups-and-actions.md).  
  
 *audit_action_group_name*  
 Имя одной или нескольких групп действий уровня базы данных, доступных для аудита. Список групп действий аудита см. в разделе [группы действий подсистемы аудита SQL Server и действия](../../relational-databases/security/auditing/sql-server-audit-action-groups-and-actions.md).  
  
 *класс*  
 Имя класса защищаемого объекта (если применимо).  
  
 *защищаемый объект*  
 Таблица, представление или другой защищаемый объект в базе данных, к которой применяется действие аудита или группа действий аудита. Дополнительные сведения см. в статье [Securables](../../relational-databases/security/securables.md).  
  
 *столбец*  
 Имя столбца защищаемого объекта (если применимо).  
  
 *Участник*  
 Имя участника [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], к которому применяется действие аудита или группа действий аудита. Дополнительные сведения см. в разделе [участников &#40; компонент Database Engine &#41;](../../relational-databases/security/authentication-access/principals-database-engine.md).  
  
 С **(** СОСТОЯНИЕ  **=**  {ON | {OFF} **)**  
 Включает или отключает сбор записей для этой спецификации аудита. Изменения состояния спецификации аудита должны выполняться вне пользовательской транзакции и не могут иметь других изменений в той же инструкции, если выполняется переход от состояния ON к OFF.  
  
## <a name="remarks"></a>Замечания  
 Спецификации аудита базы данных являются незащищаемыми объектами, которые находятся в определенной базе данных. Входит в спецификацию аудита необходимо задать параметр OFF, чтобы внести изменения в базе данных спецификации аудита. Если инструкция ALTER SERVER AUDIT SPECIFICATION выполняется при включенном аудите с любым параметром (кроме STATE=OFF), будет получено сообщение об ошибке. Дополнительные сведения см. в статье [tempdb Database](../../relational-databases/databases/tempdb-database.md).  
  
## <a name="permissions"></a>Permissions  
 Пользователи с разрешением ALTER ANY DATABASE AUDIT могут изменить спецификации аудита базы данных и привязать их к любому аудиту.  
  
 После создания спецификации аудита базы данных ее могут просматривать участники CONTROL SERVER или разрешения ALTER ANY DATABASE AUDIT, учетная запись sysadmin или участники, имеющие явный доступ к аудиту с.  
  
## <a name="examples"></a>Примеры  
 В следующем примере изменяется спецификация аудита базы данных, называемая `HIPPA_Audit_DB_Specification`, которая выполняет аудит инструкций `SELECT` пользователя `dbo` для аудита [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], называемого `HIPPA_Audit`.  
  
```  
ALTER DATABASE AUDIT SPECIFICATION HIPPA_Audit_DB_Specification  
FOR SERVER AUDIT HIPPA_Audit  
    ADD (SELECT  
         ON OBJECT::dbo.Table1  
         BY dbo)  
    WITH (STATE = ON);  
GO  
```  
  
 Полный пример о способах создания аудита см. в разделе [аудита SQL Server &#40; компонент Database Engine &#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
## <a name="see-also"></a>См. также:  
 [Создание АУДИТА сервера &#40; Transact-SQL &#41;](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [ALTER SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [Создание СПЕЦИФИКАЦИИ АУДИТА сервера &#40; Transact-SQL &#41;](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [СОЗДАТЬ СПЕЦИФИКАЦИЮ АУДИТА базы данных &#40; Transact-SQL &#41;](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [УДАЛИТЬ СПЕЦИФИКАЦИЮ АУДИТА базы данных &#40; Transact-SQL &#41;](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [ALTER AUTHORIZATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sys.fn_get_audit_file &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [sys.server_audits &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [sys.server_file_audits &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [sys.server_audit_specifications &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [sys.server_audit_specification_details &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [sys.database_audit_specifications &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [sys.database_audit_specification_details &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [sys.dm_server_audit_status &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [sys.dm_audit_actions &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [Создание аудита сервера и спецификации аудита сервера](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  

