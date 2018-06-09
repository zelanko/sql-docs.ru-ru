---
title: sp_helplinkedsrvlogin (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_helplinkedsrvlogin_TSQL
- sp_helplinkedsrvlogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helplinkedsrvlogin
ms.assetid: a2b1eba0-bf71-47e7-a4c7-9f55feec82a3
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: b9615c833939c18b3653fa4035258b91bb5bdfc8
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "33253267"
---
# <a name="sphelplinkedsrvlogin-transact-sql"></a>sp_helplinkedsrvlogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Предоставляет сведения о сопоставлениях имен входа, установленных для определенного связанного сервера, который используется для распределенных запросов и удаленных хранимых процедур.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helplinkedsrvlogin [ [ @rmtsrvname = ] 'rmtsrvname' ]   
     [ , [ @locallogin = ] 'locallogin' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@rmtsrvname=**] **"***серверу rmtsrvname***"**  
 Имя связанного сервера, к которому применяется сопоставление имен входа. *серверу rmtsrvname* — **sysname**, значение по умолчанию NULL. При значении NULL возвращаются все сопоставления имен входа, определенные для всех связанных серверов, определенных на локальном компьютере, где выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [  **@locallogin=**] **"***locallogin***"**  
 — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Входа на локальном сервере, сопоставленный со связанным сервером *серверу rmtsrvname*. *locallogin* — **sysname**, значение по умолчанию NULL. Значение NULL указывает, что все сопоставления имен входа определены на *серверу rmtsrvname* возвращаются. Если не равно NULL, сопоставление для *locallogin* для *серверу rmtsrvname* должен уже существовать. *locallogin* может быть [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа или пользователя Windows. В таком случае пользователь Windows должен иметь права на доступ к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], полученные напрямую или через членство в группе Windows, имеющей такие права.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**Связанный сервер**|**sysname**|Имя связанного сервера.|  
|**Локальное имя входа**|**sysname**|Локальное имя входа, для которого применяется сопоставление.|  
|**Собственный сопоставление**|**smallint**|0 = **локальное имя входа** сопоставляется **удаленного входа** при подключении к **связанного сервера**.<br /><br /> 1 = **локальное имя входа** сопоставляется имя входа и пароль при подключении к **связанного сервера**.|  
|**Удаленное имя входа**|**sysname**|Имя входа на **LinkedServer** сопоставленный **LocalLogin** при **IsSelfMapping** — 0. Если **IsSelfMapping** -1, **RemoteLogin** имеет значение NULL.|  
  
## <a name="remarks"></a>Примечания  
 Перед удалением сопоставлений имен входа с помощью **sp_helplinkedsrvlogin** для определения связанных серверов, которые участвуют.  
  
## <a name="permissions"></a>Разрешения  
 Разрешения не проверяются.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-displaying-all-login-mappings-for-all-linked-servers"></a>A. Вывод всех сопоставлений имен входа для всех связанных серверов  
 В следующем примере выводятся все сопоставления имен входа для всех связанных серверов, определенные на локальном компьютере, выполняющем [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
EXEC sp_helplinkedsrvlogin;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Linked Server    Local Login   Is Self Mapping Remote Login   
---------------- ------------- --------------- --------------   
Accounts         NULL          1               NULL  
Sales            NULL          1               NULL  
Sales            Mary          0               sa  
Marketing        NULL          1               NULL  
  
(4 row(s) affected)  
```  
  
### <a name="b-displaying-all-login-mappings-for-a-linked-server"></a>Б. Вывод всех сопоставлений имен входа для одного связанного сервера  
 В следующем примере выводятся все локально определенные сопоставления имен входа для связанного сервера `Sales`.  
  
```  
EXEC sp_helplinkedsrvlogin 'Sales';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Linked Server    Local Login   Is Self Mapping Remote Login   
---------------- ------------- --------------- --------------   
Sales            NULL          1               NULL  
Sales            Mary          0               sa  
  
(2 row(s) affected)  
```  
  
### <a name="c-displaying-all-login-mappings-for-a-local-login"></a>В. Вывод всех сопоставлений имен входа для локального имени входа  
 В следующем примере выводятся все локально определенные сопоставления имен входа для имени входа `Mary`.  
  
```  
EXEC sp_helplinkedsrvlogin NULL, 'Mary';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Linked Server    Local Login   Is Self Mapping Remote Login   
---------------- ------------- --------------- --------------   
Sales            NULL          1               NULL  
Sales            Mary          0               sa  
  
(2 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры безопасности (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addlinkedserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_droplinkedsrvlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droplinkedsrvlogin-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
