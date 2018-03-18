---
title: "DENY, запрет разрешений на сервере (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 06/09/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- permissions [SQL Server], servers
- denying permissions [SQL Server], servers
- servers [SQL Server], permissions
- DENY statement, servers
ms.assetid: 68d6b2a9-c36f-465a-9cd2-01d43a667e99
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c5cabf58a9136324602af30f9b8fa6b85e3ee346
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="deny-server-permissions-transact-sql"></a>DENY, запрет разрешений на сервере (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Отзывает разрешения на сервере.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DENY permission [ ,...n ]   
    TO <grantee_principal> [ ,...n ]  
    [ CASCADE ]  
    [ AS <grantor_principal> ]   
  
<grantee_principal> ::= SQL_Server_login   
    | SQL_Server_login_mapped_to_Windows_login  
    | SQL_Server_login_mapped_to_Windows_group  
    | SQL_Server_login_mapped_to_certificate  
    | SQL_Server_login_mapped_to_asymmetric_key  
    | server_role  
  
<grantor_principal> ::= SQL_Server_login   
    | SQL_Server_login_mapped_to_Windows_login  
    | SQL_Server_login_mapped_to_Windows_group  
    | SQL_Server_login_mapped_to_certificate  
    | SQL_Server_login_mapped_to_asymmetric_key  
    | server_role  
```  
  
## <a name="arguments"></a>Аргументы  
 *permission*  
 Указывает разрешение, которое может быть запрещено на сервере. Список разрешений см. в подразделе "Примечания" далее в этом разделе.  
  
 CASCADE  
 Указывает, что запрещаемое разрешение также запрещается для других участников, которым оно было предоставлено данным участником.  
  
 TO \<server_principal>  
 Указывает участника, для которого запрещается разрешение.  
  
 AS \<grantor_principal>  
 Указывает участника, от которого участник, выполняющий данный запрос, получает право на запрещение разрешения.  
  
 *SQL_Server_login*  
 Указывает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *SQL_Server_login_mapped_to_Windows_login*  
 Указывает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], сопоставленное с именем входа Windows.  
  
 *SQL_Server_login_mapped_to_Windows_group*  
 Указывает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], сопоставленное с группой Windows.  
  
 *SQL_Server_login_mapped_to_certificate*  
 Указывает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], сопоставленное с сертификатом.  
  
 *SQL_Server_login_mapped_to_asymmetric_key*  
 Указывает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], сопоставленное с асимметричным ключом.  
  
 *server_role*  
 Указывает роль сервера.  
  
## <a name="remarks"></a>Remarks  
 Разрешения в области сервера могут запрещаться только в том случае, если текущей базой данных является master.  
  
 Сведения о разрешениях для сервера можно просмотреть в представлении каталога [sys.server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md), а сведения о субъектах на уровне сервера — в представлении каталога [sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md). Сведения о членстве ролей сервера можно просмотреть в представлении каталога [sys.server_role_members](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md).  
  
 Сервер является наивысшим уровнем в иерархии разрешений. Наиболее часто указываемые и ограниченные разрешения, которые могут быть запрещены на сервере, перечислены в следующей таблице.  
  
|Разрешение сервера|Подразумевается в разрешении сервера|  
|-----------------------|----------------------------------|  
|ADMINISTER BULK OPERATIONS|CONTROL SERVER|  
|ALTER ANY AVAILABILITY GROUP<br /><br /> **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|CONTROL SERVER|  
|ALTER ANY CONNECTION|CONTROL SERVER|  
|ALTER ANY CREDENTIAL|CONTROL SERVER|  
|ALTER ANY DATABASE|CONTROL SERVER|  
|ALTER ANY ENDPOINT|CONTROL SERVER|  
|ALTER ANY EVENT NOTIFICATION|CONTROL SERVER|  
|ALTER ANY EVENT SESSION|CONTROL SERVER|  
|ALTER ANY LINKED SERVER|CONTROL SERVER|  
|ALTER ANY LOGIN|CONTROL SERVER|  
|ALTER ANY SERVER AUDIT|CONTROL SERVER|  
|ALTER ANY SERVER ROLE<br /><br /> **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|CONTROL SERVER|  
|ALTER RESOURCES|CONTROL SERVER|  
|ALTER SERVER STATE|CONTROL SERVER|  
|ALTER SETTINGS|CONTROL SERVER|  
|ALTER TRACE|CONTROL SERVER|  
|AUTHENTICATE SERVER|CONTROL SERVER|  
|CONNECT ANY DATABASE<br /><br /> **Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|CONTROL SERVER|  
|CONNECT SQL|CONTROL SERVER|  
|CONTROL SERVER|CONTROL SERVER|  
|CREATE ANY DATABASE|ALTER ANY DATABASE|  
|Создание группы доступности<br /><br /> **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|ALTER ANY AVAILABILITY GROUP|  
|CREATE DDL EVENT NOTIFICATION|ALTER ANY EVENT NOTIFICATION|  
|CREATE ENDPOINT|ALTER ANY ENDPOINT|  
|CREATE SERVER ROLE<br /><br /> **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|ALTER ANY SERVER ROLE|  
|CREATE TRACE EVENT NOTIFICATION|ALTER ANY EVENT NOTIFICATION|  
|EXTERNAL ACCESS ASSEMBLY|CONTROL SERVER|  
|IMPERSONATE ANY LOGIN<br /><br /> **Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|CONTROL SERVER|  
|SELECT ALL USER SECURABLES<br /><br /> **Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|CONTROL SERVER|  
|SHUTDOWN|CONTROL SERVER|  
|UNSAFE ASSEMBLY|CONTROL SERVER|  
|VIEW ANY DATABASE|VIEW ANY DEFINITION|  
|VIEW ANY DEFINITION|CONTROL SERVER|  
|VIEW SERVER STATE|ALTER SERVER STATE|  
  
## <a name="remarks"></a>Remarks  
 Следующие три разрешения сервера добавлены в [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
 Разрешение **CONNECT ANY DATABASE**  
 Предоставьте разрешение **CONNECT ANY DATABASE** имени входа, которому нужно подключиться ко всем существующим базам данных и ко всем новым базам, которые могут быть созданы в будущем. Не предоставляет каких-либо разрешений в базах данных за пределами соединения. Объедините с **SELECT ALL USER SECURABLES** и **VIEW SERVER STATE**, чтобы процесс аудита имел доступ к состояниям всех данных или всех баз данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Разрешение **IMPERSONATE ANY LOGIN**  
 После предоставления разрешает процессу среднего уровня олицетворять учетную запись клиентов, подключающихся к ней, так как она подключается к базам данных. При запрещении имени входа с высоким уровнем прав может быть запрещено олицетворение других имен входа. Например, имени входа с разрешением **CONTROL SERVER** можно запретить олицетворение других имен входа.  
  
 Разрешение **SELECT ALL USER SECURABLES**  
 После предоставления имя входа, например аудитор, сможет просматривать данные во всех базах данных, к которым может подключаться пользователь. При запрещении предотвращает доступ к объектам, если они не будут находиться в схеме **sys**.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо иметь разрешение CONTROL SERVER или быть владельцем защищаемого объекта. При использовании предложения AS указанный участник должен быть владельцем защищаемого объекта, разрешения на который у него запрещены.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-denying-connect-sql-permission-to-a-sql-server-login-and-principals-to-which-the-login-has-regranted-it"></a>A. Запрет разрешения CONNECT SQL для пользователя SQL Server с указанным именем входа и участников, которым этот пользователь его предоставил  
 В следующем примере разрешение `CONNECT SQL` запрещается для пользователя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с именем входа `Annika` и для участников, которым он предоставил это разрешение.  
  
```  
USE master;  
DENY CONNECT SQL TO Annika CASCADE;  
GO  
```  
  
### <a name="b-denying-create-endpoint-permission-to-a-sql-server-login-using-the-as-option"></a>Б. Запрет разрешения CREATE ENDPOINT для пользователя SQL Server с помощью параметра AS  
 В следующем примере разрешение `CREATE ENDPOINT` запрещается для пользователя `ArifS`. Пример использует параметр `AS` для указания пользователя `MandarP` в качестве участника, от которого текущий участник получает права для выполнения.  
  
```  
USE master;  
DENY CREATE ENDPOINT TO ArifS AS MandarP;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [GRANT (Transact-SQL)](../../t-sql/statements/grant-transact-sql.md)   
 [DENY (Transact-SQL)](../../t-sql/statements/deny-transact-sql.md)   
 [DENY, запрет разрешений на сервере (Transact-SQL)](../../t-sql/statements/deny-server-permissions-transact-sql.md)   
 [REVOKE, отмена разрешений на сервере (Transact-SQL)](../../t-sql/statements/revoke-server-permissions-transact-sql.md)   
 [Иерархия разрешений (ядро СУБД)](../../relational-databases/security/permissions-hierarchy-database-engine.md)   
 [sys.fn_builtin_permissions (Transact-SQL)](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [sys.fn_my_permissions (Transact-SQL)](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)   
 [HAS_PERMS_BY_NAME (Transact-SQL)](../../t-sql/functions/has-perms-by-name-transact-sql.md)  
  
  
