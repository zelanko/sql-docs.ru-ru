---
title: ALTER SERVER AUDIT SPECIFICATION (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 05/01/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ALTER SERVER AUDIT SPECIFICATION
- ALTER_SERVER_AUDIT_SPECIFICATION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- server audit [SQL Server]
- audits [SQL Server], specification
- ALTER SERVER AUDIT SPECIFICATION statement
ms.assetid: 9cac288b-940e-4c16-88d6-de06aeed2b47
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 8e28f6f8e97a30118cf27e249c21ffd91714318a
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2020
ms.locfileid: "81631880"
---
# <a name="alter-server-audit-specification-transact-sql"></a>ALTER SERVER AUDIT SPECIFICATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Изменяет объект спецификации аудита сервера с помощью функции аудита [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в статье [Подсистема аудита SQL Server (ядро СУБД)](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
ALTER SERVER AUDIT SPECIFICATION audit_specification_name  
{  
    [ FOR SERVER AUDIT audit_name ]  
    [ { { ADD | DROP } ( audit_action_group_name )  
      } [, ...n] ]  
    [ WITH ( STATE = { ON | OFF } ) ]  
}  
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *audit_specification_name*  
 Имя спецификации аудита.  
  
 *audit_name*  
 Имя аудита, к которому применяется эта спецификация.  
  
 *audit_action_group_name*  
 Имя группы действий уровня сервера, доступных для аудита. Список групп действий аудита см. в разделе [Действия и группы действий подсистемы аудита SQL Server](../../relational-databases/security/auditing/sql-server-audit-action-groups-and-actions.md).  
  
 WITH **(** STATE **=** { ON | OFF } **)**  
 Включает или отключает сбор записей для этой спецификации аудита.  
  
## <a name="remarks"></a>Remarks  
 Чтобы внести изменения в спецификацию аудита, необходимо установить состояние аудита в режим OFF. Если инструкция ALTER SERVER AUDIT SPECIFICATION выполняется при включенной спецификации аудита с любым параметром (кроме STATE=OFF), будет получено сообщение об ошибке.  
  
## <a name="permissions"></a>Разрешения  
 Пользователи с разрешением ALTER ANY SERVER AUDIT могут изменить спецификации аудита сервера и привязать их к любому аудиту.  
  
 После ее создания спецификацию аудита сервера могут просматривать пользователи учетной записи sysadmin, участники с разрешениями CONTROL SERVER или ALTER ANY SERVER AUDIT и участники, имеющие явный доступ к аудиту.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается спецификация аудита сервера с именем `HIPAA_Audit_Specification`. Удаляется группа действий аудита неудачных попыток входа, и добавляется группа действий аудита доступа к объектам базы данных для аудита [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с именем `HIPAA_Audit`.  
  
```  
ALTER SERVER AUDIT SPECIFICATION HIPAA_Audit_Specification  
FOR SERVER AUDIT HIPAA_Audit  
    DROP (FAILED_LOGIN_GROUP),  
    ADD (DATABASE_OBJECT_ACCESS_GROUP)  
    WITH (STATE=ON);  
GO  
```  
  
 Полный пример создания аудита см. в разделе [Аудит SQL Server (ядро СУБД)](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  

## <a name="see-also"></a>См. также:  
 [CREATE SERVER AUDIT (Transact-SQL)](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [ALTER SERVER AUDIT (Transact-SQL)](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER AUDIT (Transact-SQL)](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [CREATE SERVER AUDIT SPECIFICATION (Transact-SQL)](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION (Transact-SQL)](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [CREATE DATABASE AUDIT SPECIFICATION (Transact-SQL)](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [ALTER DATABASE AUDIT SPECIFICATION (Transact-SQL)](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [DROP DATABASE AUDIT SPECIFICATION (Transact-SQL)](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [ALTER AUTHORIZATION (Transact-SQL)](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sys.fn_get_audit_file (Transact-SQL)](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [sys.server_audits (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [sys.server_file_audits (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [sys.server_audit_specifications (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [sys.server_audit_specification_details (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [sys.database_audit_specifications (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [sys.database_audit_specification_details (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [sys.dm_server_audit_status (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [sys.dm_audit_actions (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [Создание аудита сервера и спецификации аудита сервера](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
