---
title: sys.sp_rda_test_connection (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_test_connection
- sys.sp_rda_test_connection_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_test_connection stored procedure
ms.assetid: e2ba050c-d7e3-4f33-8281-c9b525b4edb4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a63a88e24f62ba9d8a4a70107663ab2d585f4640
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68061793"
---
# <a name="syssprdatestconnection-transact-sql"></a>sys.sp_rda_test_connection (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Проверяет соединение с SQL Server с удаленным сервером Azure и сообщает о проблемах, которые могут помешать миграции данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
EXECUTE sys.sp_rda_test_connection  
   @database_name = N'db_name',   
   @server_address = N'azure_server_fully_qualified_address',  
   @azure_username = N'azure_username',   
   @azure_password = N'azure_password',  
   @credential_name = N'credential_name'  
  
```  
  
## <a name="arguments"></a>Аргументы  
 @database_name = N'*db_name*'  
 Имя базы данных SQL Server с поддержкой Stretch. Этот параметр является необязательным.  
  
 @server_address = N'*azure_server_fully_qualified_address*'  
 Полный адрес сервера Azure.  
  
-   Если указать значение для **@database_name** , но указанная база данных не включена поддержка Stretch, то вы должны предоставить значение для **@server_address** .  
  
-   Если указать значение для **@database_name** и указанной базы данных, совместимых со Stretch, то не нужно предоставлять значение для **@server_address** . Если указать значение для **@server_address** , хранимая процедура пропускает его и использует уже существующий сервер Azure, связанные с поддержкой растяжения базы данных.  
  
 @azure_username = N "*azure_username*  
 Имя пользователя для удаленного сервера Azure.  
  
 @azure_password = N'*azure_password*'  
 Пароль для удаленным сервером Azure.  
  
 @credential_name = N "*credential_name*"  
 Вместо предоставления имени пользователя и пароля, можно указать имя учетных данных, хранящихся в базе данных с поддержкой Stretch.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 В частности **успех**, sp_rda_test_connection возвращает ошибку 14855 (STRETCH_MAJOR, STRETCH_CONNECTION_TEST_PROC_SUCCEEDED) с уровнем серьезности EX_INFO и код возврата успешно.  
  
 В частности **сбоя**, sp_rda_test_connection возвращает ошибку 14856 (STRETCH_MAJOR, STRETCH_CONNECTION_TEST_PROC_FAILED) с уровнем серьезности EX_USER и код возврата ошибки.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|link_state|ssNoversion|Одно из следующих значений, которые соответствуют значениям **link_state_desc**.<br /><br /> -   0<br />-   1<br />-   2<br />-   3<br />-   4|  
|link_state_desc|varchar(32)|Одно из следующих значений, которые соответствуют предыдущему значений в параметре **link_state**.<br /><br /> — РАБОТОСПОСОБНОСТЬ<br />     SQL Server и Azure удаленный сервер находится в работоспособном состоянии.<br />-ERROR_AZURE_FIREWALL<br />     Брандмауэр Azure блокирует связь между SQL Server и удаленным сервером Azure.<br />-ERROR_NO_CONNECTION<br />     SQL Server не удается установить подключение к удаленным сервером Azure.<br />-ERROR_AUTH_FAILURE<br />     Ошибка проверки подлинности блокирует связь между SQL Server и удаленным сервером Azure.<br />-ОШИБКА<br />     Ошибка, которая не имеет проблемы с проверкой подлинности, разрыв подключения или проблемы с брандмауэром блокирует связь между SQL Server и удаленным сервером Azure.|  
|error_number|ssNoversion|Номер ошибки. Если отсутствуют ошибки, это поле имеет значение NULL.|  
|error_message|nvarchar(1024)|Сообщение об ошибке. Если отсутствуют ошибки, это поле имеет значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 Требуются права db_owner.  
  
## <a name="examples"></a>Примеры  
  
### <a name="check-the-connection-from-sql-server-to-the-remote-azure-server"></a>Проверьте подключение к удаленному серверу Azure SQL Server  
  
```sql  
EXECUTE sys.sp_rda_test_connection @database_name = N'<Stretch-enabled database>'  
GO  
  
```  
  
 Результаты показывают, что SQL Server не может соединиться с удаленным сервером Azure.  
  
|link_state|link_state_desc|error_number|error_message|  
|-----------------|-----------------------|-------------------|--------------------|  
|2|ERROR_NO_CONNECTION|*\<номер ошибки, относящиеся к соединению >*|*\<сообщение об ошибке, относящиеся к соединению >*|  
  
### <a name="check-the-azure-firewall"></a>Проверьте брандмауэр Azure  
  
```sql  
USE <Stretch-enabled database>  
GO  
EXECUTE sys.sp_rda_test_connection  
GO  
  
```  
  
 Результаты показывают, что брандмауэр Azure не позволяет связь между SQL Server и удаленным сервером Azure.  
  
|link_state|link_state_desc|error_number|error_message|  
|-----------------|-----------------------|-------------------|--------------------|  
|1|ERROR_AZURE_FIREWALL|*\<номер ошибки, связанные с брандмауэра >*|*\<сообщение об ошибке, связанных с брандмауэром >*|  
  
### <a name="check-authentication-credentials"></a>Проверьте учетные данные проверки подлинности  
  
```sql  
USE <Stretch-enabled database>  
GO  
EXECUTE sys.sp_rda_test_connection  
GO  
  
```  
  
 Результаты показывают, что сбой проверки подлинности блокирует связь между SQL Server и удаленным сервером Azure.  
  
|link_state|link_state_desc|error_number|error_message|  
|-----------------|-----------------------|-------------------|--------------------|  
|3|ERROR_AUTH_FAILURE|*\<номер ошибки, относящихся к проверке подлинности >*|*\<сообщение об ошибке, относящихся к проверке подлинности >*|  
  
### <a name="check-the-status-of-the-remote-azure-server"></a>Проверьте состояние удаленным сервером Azure  
  
```sql  
USE <SQL Server database>  
GO  
EXECUTE sys.sp_rda_test_connection   
    @server_address = N'<server name>.database.windows.net',   
    @azure_username = N'<user name>',   
    @azure_password = N'<password>'  
GO  
  
```  
  
 Результаты показывают, что подключение работоспособно и что вы можете включить Stretch Database для указанной базы данных.  
  
|link_state|link_state_desc|error_number|error_message|  
|-----------------|-----------------------|-------------------|--------------------|  
|0|HEALTHY|NULL|NULL|  
  
  
