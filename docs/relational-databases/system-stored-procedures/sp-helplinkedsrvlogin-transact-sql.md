---
title: sp_helplinkedsrvlogin (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helplinkedsrvlogin_TSQL
- sp_helplinkedsrvlogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helplinkedsrvlogin
ms.assetid: a2b1eba0-bf71-47e7-a4c7-9f55feec82a3
author: stevestein
ms.author: sstein
ms.openlocfilehash: f1728b3e5d4cd3189a8d9a01a8b72ecedaf7cb6d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68122461"
---
# <a name="sp_helplinkedsrvlogin-transact-sql"></a>sp_helplinkedsrvlogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Предоставляет сведения о сопоставлениях имен входа, установленных для определенного связанного сервера, который используется для распределенных запросов и удаленных хранимых процедур.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helplinkedsrvlogin [ [ @rmtsrvname = ] 'rmtsrvname' ]   
     [ , [ @locallogin = ] 'locallogin' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @rmtsrvname = ] 'rmtsrvname'`Имя связанного сервера, к которому применяется сопоставление имен входа. *рмтсрвнаме* имеет тип **sysname**и значение по умолчанию NULL. При значении NULL возвращаются все сопоставления имен входа, определенные для всех связанных серверов, определенных на локальном компьютере, где выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
`[ @locallogin = ] 'locallogin'`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Имя входа на локальном сервере с сопоставлением со связанным сервером *рмтсрвнаме*. *локаллогин* имеет тип **sysname**и значение по умолчанию NULL. Значение NULL указывает, что возвращаются все сопоставления имен входа, определенные в *рмтсрвнаме* . Если значение не равно NULL, сопоставление для *локаллогин* с *рмтсрвнаме* должно уже существовать. *локаллогин* может быть [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] именем входа или пользователем Windows. В таком случае пользователь Windows должен иметь права на доступ к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], полученные напрямую или через членство в группе Windows, имеющей такие права.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успех) или 1 (сбой).  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**Связанный сервер**|**имеет sysname**|Имя связанного сервера.|  
|**Локальное имя входа**|**имеет sysname**|Локальное имя входа, для которого применяется сопоставление.|  
|**Is Self Mapping**|**smallint**|0 = **Локальное имя входа** сопоставлено с **Удаленный вход** при подключении к **связанному серверу**.<br /><br /> 1 = **Локальное имя входа** сопоставлено с тем же именем входа и паролем при подключении к **связанному серверу**.|  
|**Remote Login**|**имеет sysname**|Имя входа в **LinkedServer** , сопоставленное с **Локаллогин** , если **исселфмаппинг** имеет значение 0. Если значение **исселфмаппинг** равно 1, **RemoteLogin** имеет значение null.|  
  
## <a name="remarks"></a>Remarks  
 Перед удалением сопоставлений имен входа используйте **sp_helplinkedsrvlogin** , чтобы определить связанные серверы.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры безопасности &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_droplinkedsrvlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droplinkedsrvlogin-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
