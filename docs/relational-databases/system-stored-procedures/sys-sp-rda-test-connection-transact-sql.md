---
title: sys.sp_rda_test_connection (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_test_connection
- sys.sp_rda_test_connection_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_test_connection stored procedure
ms.assetid: e2ba050c-d7e3-4f33-8281-c9b525b4edb4
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 45ba48abca5372cde0e303bce431ef66b6e299df
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="syssprdatestconnection-transact-sql"></a>sys.sp_rda_test_connection (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Проверяет соединение с SQL Server с удаленным сервером Azure и сообщает о проблемах, которые могут препятствовать миграции данных.  
  
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
 @database_name = N'*db_name*"  
 Имя базы данных SQL Server с поддержкой Stretch. Этот параметр является необязательным.  
  
 @server_address = N'*azure_server_fully_qualified_address*'  
 Полный адрес сервера Azure.  
  
-   Если указать значение для **@database_name**, но указанная база данных не включена, то вы должны предоставить значение для **@server_address**.  
  
-   Если указать значение для **@database_name**, а указанной базы данных с включенным Stretch, то не нужно предоставлять значение для **@server_address**. Если указать значение для **@server_address**, хранимая процедура пропускает его и использует уже существующий сервер Azure, связанных с поддержкой растяжения базы данных.  
  
 @azure_username = N'*azure_username*  
 Имя пользователя для удаленного сервера Azure.  
  
 @azure_password = N'*azure_password*"  
 Пароль для удаленного сервера Azure.  
  
 @credential_name = N'*credential_name*"  
 Вместо предоставления имени пользователя и пароля, можно указать имя учетных данных, хранимые в базе данных с поддержкой Stretch.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 В случае возникновения **успех**, sp_rda_test_connection возвращает ошибку 14855 (STRETCH_MAJOR, STRETCH_CONNECTION_TEST_PROC_SUCCEEDED) с уровнем серьезности EX_INFO и успешном выполнении возврата кода.  
  
 В случае возникновения **сбоя**, sp_rda_test_connection возвращает ошибку 14856 (STRETCH_MAJOR, STRETCH_CONNECTION_TEST_PROC_FAILED) с уровнем серьезности EX_USER и код возврата ошибки.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|link_state|int|Одно из следующих значений, которые соответствуют значениям для **link_state_desc**.<br /><br /> -   0<br />-   1<br />-   2<br />-   3<br />-   4|  
|link_state_desc|varchar(32)|Одно из следующих значений, которые соответствуют предыдущих значений для **link_state**.<br /><br /> — ИСПРАВНО<br />     SQL Server и Azure удаленный сервер находится в работоспособном состоянии.<br />-ERROR_AZURE_FIREWALL<br />     Брандмауэр Azure не позволяет связь между SQL Server и удаленным сервером Azure.<br />-ERROR_NO_CONNECTION<br />     SQL Server не может установить соединение с удаленным сервером Azure.<br />-ERROR_AUTH_FAILURE<br />     Сбой проверки подлинности препятствует связь между SQL Server и удаленным сервером Azure.<br />-ОШИБКА<br />     Связь между SQL Server и удаленным сервером Azure препятствует ошибку, которая не имеет проблемы с проверкой подлинности, проблемы с подключением или проблем с брандмауэром.|  
|error_number|int|Номер ошибки. Если ошибки отсутствуют, это поле имеет значение NULL.|  
|error_message|nvarchar(1024)|Сообщение об ошибке. Если ошибки отсутствуют, это поле имеет значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 Требуются права db_owner.  
  
## <a name="examples"></a>Примеры  
  
### <a name="check-the-connection-from-sql-server-to-the-remote-azure-server"></a>Проверьте подключение к удаленному серверу Azure SQL Server  
  
```sql  
EXECUTE sys.sp_rda_test_connection @database_name = N'<Stretch-enabled database>'  
GO  
  
```  
  
 Результаты показывают, что SQL Server не удается подключиться к удаленному серверу Azure.  
  
|link_state|link_state_desc|error_number|error_message|  
|-----------------|-----------------------|-------------------|--------------------|  
|2|ERROR_NO_CONNECTION|*\<номер ошибки, относящиеся к соединению >*|*\<сообщение, относящиеся к соединению >*|  
  
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
|1|ERROR_AZURE_FIREWALL|*\<номер ошибки, связанные с брандмауэра >*|*\<сообщение об ошибке, относящееся к брандмауэра >*|  
  
### <a name="check-authentication-credentials"></a>Проверьте учетные данные для проверки подлинности  
  
```sql  
USE <Stretch-enabled database>  
GO  
EXECUTE sys.sp_rda_test_connection  
GO  
  
```  
  
 Результаты показывают, что сбой проверки подлинности препятствует связь между SQL Server и удаленным сервером Azure.  
  
|link_state|link_state_desc|error_number|error_message|  
|-----------------|-----------------------|-------------------|--------------------|  
|3|ERROR_AUTH_FAILURE|*\<номер ошибки с проверкой подлинности >*|*\<Ошибка, связанная с проверки подлинности сообщения >*|  
  
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
  
 Результаты показывают, что соединение работает нормально, и базы данных Stretch можно включить для указанной базы данных.  
  
|link_state|link_state_desc|error_number|error_message|  
|-----------------|-----------------------|-------------------|--------------------|  
|0|HEALTHY|NULL|NULL|  
  
  
