---
title: "xp_logininfo (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- xp_logininfo_TSQL
- xp_logininfo
dev_langs: TSQL
helpviewer_keywords: xp_logininfo
ms.assetid: ee7162b5-e11f-4a0e-a09c-1878814dbbbd
caps.latest.revision: "32"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b77eb07126cc739908713d8172695db9098d20d9
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="xplogininfo-transact-sql"></a>xp_logininfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращают сведения о пользователях и группах Windows.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
xp_logininfo [ [ @acctname = ] 'account_name' ]   
     [ , [ @option = ] 'all' | 'members' ]   
     [ , [ @privilege = ] variable_name OUTPUT]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@acctname =** ] **"***account_name***"**  
 Имя пользователя или группы Windows, которым предоставляется доступ к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *account_name* — **sysname**, значение по умолчанию NULL. Если *account_name* не указан, все группы Windows и пользователях, которым явным образом было предоставлено разрешение на вход в отчет будут включены. *account_name* должно быть полным. Например, 'ADVWKS4\macraes' или 'BUILTIN\Administrators'.  
  
 **«все»** | **«члены»**  
 Указывает, следует ли доставлять данные обо всех путях разрешений для данной учетной записи или только сведения о членах группы Windows. **@option**— **varchar(10)**, значение по умолчанию NULL. Если не **все** указано, отображаются только путь для первого разрешения.  
  
 [  **@privilege =** ] *имя_переменной*  
 Выходной параметр, возвращающий уровень прав доступа для указанной учетной записи Windows. *имя_переменной* — **varchar(10)**, значение по умолчанию «Not wanted». Возвращаемый уровень прав доступа, является **пользователя**, **администратора**, или **null**.  
  
 OUTPUT  
 При указании помещает *имя_переменной* в выходном параметре.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**Имя учетной записи**|**sysname**|Полностью уточненное имя учетной записи Windows.|  
|**type**|**типа char(8)**|Тип учетной записи Windows. Допустимые значения: **пользователя** или **группы**.|  
|**право доступа**|**char(9)**|Права доступа к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Допустимые значения: **администратора**, **пользователя**, или **null**.|  
|**Сопоставленное имя входа**|**sysname**|Для учетных записей пользователей с пользовательскими привилегиями столбец **сопоставлено имя входа** показано сопоставленное имя входа, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пытается использовать при добавлении вход с помощью этой учетной записи с помощью правил сопоставления с именем домена перед ним.|  
|**Путь разрешения**|**sysname**|Членство в группе, разрешающее доступ к учетной записи.|  
  
## <a name="remarks"></a>Замечания  
 Если *account_name* указано, **xp_logininfo** сообщает высокий уровень прав указанного пользователя или группы Windows. Если пользователь Windows имеет права системного администратора и пользователя домена, он будет выступать в качестве системного администратора. Если пользователь является членом нескольких групп Windows одного уровня прав доступа, группа, которая первой предоставила доступ к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], будет отражена.  
  
 Если *account_name* является допустимым пользователя или группы Windows, не связан с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа, возвращается пустой результирующий набор. Если *account_name* не может быть определен как допустимый пользователь или группа Windows, возвращается сообщение об ошибке.  
  
 Если *account_name* и **все** являются задан, возвращаются все пути разрешений для пользователя или группы Windows. Если *account_name* является членом нескольких групп, которые предоставили доступ к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то возвращается несколько строк. **Администратора** возвращаются перед строками прав **пользователя** строки и прав доступа уровня строки возвращаются в порядке, в котором соответствующие [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] были созданы имена входа.  
  
 Если *account_name* и **члены** являются указан, возвращается список членов группы следующего уровня. Если *account_name* является именем локальной группы, список может включать локальных пользователей, пользователей домена и группы. Если *account_name* является учетной записью домена, список состоит из пользователей домена. Сервер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен подключиться к контроллеру домена для получения сведений о членстве в группе. Если сервер не может подключиться к контроллеру домена, никакие сведения не возвращаются.  
  
 **xp_logininfo** возвращает только сведения из глобальных групп Active Directory, не универсальных групп.  
  
## <a name="permissions"></a>Permissions  
 Требуется членство в **sysadmin** предопределенной роли сервера или членство в **открытый** предопределенной роли базы данных в **master** базы данных и разрешения EXECUTE.  
  
## <a name="examples"></a>Примеры  
 В следующем примере отображаются сведения о `BUILTIN\Administrators` группы Windows.  
  
```  
EXEC xp_logininfo 'BUILTIN\Administrators';  
```  
  
## <a name="see-also"></a>См. также:  
 [Хранимая процедура sp_denylogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [Хранимая процедура sp_grantlogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [Хранимая процедура sp_revokelogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Общие расширенные хранимые процедуры &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)  
  
  
