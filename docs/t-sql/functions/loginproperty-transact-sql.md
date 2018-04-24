---
title: LOGINPROPERTY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- BadPasswordCount_TSQL
- BadPasswordTime_TSQL
- IsLockedIsMustChange
- PasswordLastSetTime
- LOGINPROPERTY_TSQL
- LockoutTime
- BadPasswordCount
- PasswordHash
- HistoryLengthIsExpired
- LockoutTime_TSQL
- PasswordHash_TSQL
- HistoryLengthIsExpired_TSQL
- PasswordLastSetTime_TSQL
- BadPasswordTime
- IsLockedIsMustChange_TSQL
- LOGINPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- default database
- LOGINPROPERTY function
ms.assetid: b34df777-79b0-49a5-88db-b99998479a5d
caps.latest.revision: 42
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 35f9ae16b85c513349d66a7b53fa4d23bf7de768
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="loginproperty-transact-sql"></a>LOGINPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о настройках политики входа в систему.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
LOGINPROPERTY ( 'login_name' , 'property_name' )  
```  
  
## <a name="arguments"></a>Аргументы  
 *login_name*  
 Имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], для которого будет возвращено состояние свойства входа в систему.  
  
 *propertyname*  
 Выражение, содержащее сведения о свойстве, возвращаемые для имени входа. *propertyname* может иметь одно из указанных ниже значений.  
  
|Значение|Description|  
|-----------|-----------------|  
|**BadPasswordCount**|Возвращает число последовательных попыток входа в систему с неверным паролем.|  
|**BadPasswordTime**|Возвращает время последней попытки входа в систему с неверным паролем.|  
|**DaysUntilExpiration**|Возвращает число дней до завершения срока действия пароля.|  
|**DefaultDatabase**|Возвращает базу данных по умолчанию для имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в соответствии со сведениями, сохраненными в метаданных, или базу данных **master**, если база данных не указана. Возвращает значение NULL для пользователей, прошедших проверку не в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (например, для пользователей, прошедших проверку подлинности Windows).|  
|**DefaultLanguage**|Возвращает язык имени входа по умолчанию в соответствии со сведениями, сохраненными в метаданных. Возвращает значение NULL для пользователей, прошедших проверку не в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], например для пользователей, прошедших проверку подлинности Windows.|  
|**HistoryLength**|Возвращает количество паролей, найденных для имени входа с помощью механизма принудительного применения политики паролей. Возвращает 0, если политика паролей не применяется принудительно. При значении 1 перезапускается возобновление принудительного применения политики паролей.|  
|**IsExpired**|Указывает, истек ли срок действия имени входа.|  
|**IsLocked**|Указывает, заблокировано ли имя входа.|  
|**IsMustChange**|Указывает, необходимо ли менять пароль для имени входа при следующем его подключении.|  
|**LockoutTime**|Возвращает дату блокировки имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из-за превышения разрешенного числа неудачных попыток входа в систему.|  
|**PasswordHash**|Возвращает хэш пароля.|  
|**PasswordLastSetTime**|Возвращает дату установки текущего пароля.|  
|**PasswordHashAlgorithm**|Возвращает алгоритм, используемый для хэширования пароля.|  
  
## <a name="returns"></a>Возвращает  
 Тип данных зависит от запрошенного значения.  
  
 Аргументы **IsLocked**, **IsExpired** и **IsMustChange** имеют тип **int**.  
  
-   1, если имя входа находится в указанном состоянии.  
  
-   0, если имя входа не находится в указанном состоянии.  
  
 Аргументы **BadPasswordCount** и **HistoryLength** имеют тип **int**.  
  
 Аргументы **BadPasswordTime**, **LockoutTime**, **PasswordLastSetTime** имеют тип **datetime**.  
  
 Аргумент **PasswordHash** имеет тип **varbinary**.  
  
 NULL, если имя входа не является допустимым именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Аргумент **DaysUntilExpiration** имеет тип **int**.  
  
-   0, если срок действия имени входа истек или истечет в день запроса.  
  
-   -1, если срок действия пароля не ограничен в соответствии с локальной политикой безопасности Windows.  
  
-   NULL, если параметр CHECK_POLICY или CHECK_EXPIRATION имеет значение OFF для имени входа либо если операционная система не поддерживает политику паролей.  
  
 Аргумент **PasswordHashAlgorithm** имеет тип int.  
  
-   0, если это хэш SQL7.0  
  
-   1, если это хэш SHA-1  
  
-   2, если хэширование по SHA-2  
  
-   NULL, если имя входа не является допустимым именем входа SQL Server.  
  
## <a name="remarks"></a>Remarks  
 Эта встроенная функция возвращает сведения о настройках политики паролей для имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В именах свойств регистр не учитывается, поэтому имена **BadPasswordCount** и **badpasswordcount** эквивалентны. Значения свойств **PasswordHash, PasswordHashAlgorithm** и **PasswordLastSetTime** доступны во всех поддерживаемых конфигурациях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], но другие свойства доступны, только если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работает под управлением [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] при включенных параметрах CHECK_POLICY и CHECK_EXPIRATION. Дополнительные сведения см. в разделе [Политика паролей](../../relational-databases/security/password-policy.md).  
  
## <a name="permissions"></a>Разрешения  
 Требует разрешения VIEW на имя входа. При запросе хэша пароля также требует разрешения CONTROL SERVER.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-checking-whether-a-login-must-change-its-password"></a>A. Проверка необходимости изменения пароля для имени входа  
 В приведенном ниже примере выполняется проверка необходимости изменения пароля для имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `John3` при следующем подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
SELECT LOGINPROPERTY('John3', 'IsMustChange');  
GO  
```  
  
### <a name="b-checking-whether-a-login-is-locked-out"></a>Б. Проверка блокировки имени входа  
 В следующем примере выполняется проверка блокировки имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `John3`.  
  
```  
SELECT LOGINPROPERTY('John3', 'IsLocked');  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE LOGIN (Transact-SQL)](../../t-sql/statements/create-login-transact-sql.md)   
 [sys.server_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)  
  
  
