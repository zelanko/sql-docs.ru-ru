---
title: "LOGINPROPERTY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
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
dev_langs: TSQL
helpviewer_keywords:
- default database
- LOGINPROPERTY function
ms.assetid: b34df777-79b0-49a5-88db-b99998479a5d
caps.latest.revision: "42"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c5aa0f30058bdd2e6fc13121e4a849d4496b667d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
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
  
 *PropertyName*  
 Выражение, содержащее сведения о свойстве, возвращаемые для имени входа. *PropertyName* может принимать одно из следующих значений.  
  
|Значение|Description|  
|-----------|-----------------|  
|**BadPasswordCount**|Возвращает число последовательных попыток входа в систему с неверным паролем.|  
|**BadPasswordTime**|Возвращает время последней попытки входа в систему с неверным паролем.|  
|**DaysUntilExpiration**|Возвращает число дней до завершения срока действия пароля.|  
|**DefaultDatabase**|Возвращает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа база данных по умолчанию хранится в метаданных или **master** Если база данных не указан. Возвращает значение NULL для не -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подготовить пользователей (например, прошедшего проверку подлинности Windows).|  
|**DefaultLanguage**|Возвращает язык имени входа по умолчанию в соответствии со сведениями, сохраненными в метаданных. Возвращает значение NULL для не -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подготовленные пользователи, например, Windows, прошедших проверку пользователей.|  
|**HistoryLength**|Возвращает количество паролей, найденных для имени входа с помощью механизма принудительного применения политики паролей. Возвращает 0, если политика паролей не применяется принудительно. При значении 1 перезапускается возобновление принудительного применения политики паролей.|  
|**IsExpired**|Указывает, истек ли срок действия имени входа.|  
|**Блокирована**|Указывает, заблокировано ли имя входа.|  
|**IsMustChange**|Указывает, необходимо ли менять пароль для имени входа при следующем его подключении.|  
|**LockoutTime**|Возвращает дату блокировки имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из-за превышения разрешенного числа неудачных попыток входа в систему.|  
|**PasswordHash**|Возвращает хэш пароля.|  
|**PasswordLastSetTime**|Возвращает дату установки текущего пароля.|  
|**PasswordHashAlgorithm**|Возвращает алгоритм, используемый для хэширования пароля.|  
  
## <a name="returns"></a>Возвращает  
 Тип данных зависит от запрошенного значения.  
  
 **IsLocked**, **IsExpired**, и **IsMustChange** имеют тип **int**.  
  
-   1, если имя входа находится в указанном состоянии.  
  
-   0, если имя входа не находится в указанном состоянии.  
  
 **BadPasswordCount** и **HistoryLength** имеют тип **int**.  
  
 **BadPasswordTime**, **LockoutTime**, **PasswordLastSetTime** имеют тип **datetime**.  
  
 **PasswordHash** относится к типу **varbinary**.  
  
 NULL, если имя входа не является допустимым именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **DaysUntilExpiration** относится к типу **int**.  
  
-   0, если срок действия имени входа истек или истечет в день запроса.  
  
-   -1, если срок действия пароля не ограничен в соответствии с локальной политикой безопасности Windows.  
  
-   NULL, если параметр CHECK_POLICY или CHECK_EXPIRATION имеет значение OFF для имени входа либо если операционная система не поддерживает политику паролей.  
  
 **PasswordHashAlgorithm** имеет тип int.  
  
-   0, если это хэш SQL7.0  
  
-   1, если хэш SHA-1  
  
-   2, если хэширование по SHA-2  
  
-   NULL, если имя входа не является допустимым именем входа SQL Server.  
  
## <a name="remarks"></a>Замечания  
 Эта встроенная функция возвращает сведения о настройках политики паролей для имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Имена свойств не учитывают регистр, поэтому имена свойства, такие как **BadPasswordCount** и **badpasswordcount** эквивалентны. Значения **PasswordHash, PasswordHashAlgorithm**, и **PasswordLastSetTime** свойства доступны во всех поддерживаемых конфигурациях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], но другие свойства являются только доступна при [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работает на [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] и CHECK_POLICY и CHECK_EXPIRATION. Дополнительные сведения см. в разделе [Password Policy](../../relational-databases/security/password-policy.md).  
  
## <a name="permissions"></a>Permissions  
 Требует разрешения VIEW на имя входа. При запросе хэша пароля также требует разрешения CONTROL SERVER.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-checking-whether-a-login-must-change-its-password"></a>A. Проверка необходимости изменения пароля для имени входа  
 В следующем примере проверяется ли [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа `John3` изменения пароля при очередном подключении к экземпляру компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
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
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [sys.server_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)  
  
  
