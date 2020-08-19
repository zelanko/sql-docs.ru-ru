---
description: xp_logininfo (Transact-SQL)
title: xp_logininfo (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_logininfo_TSQL
- xp_logininfo
dev_langs:
- TSQL
helpviewer_keywords:
- xp_logininfo
ms.assetid: ee7162b5-e11f-4a0e-a09c-1878814dbbbd
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 44b76081c7ec5fdd3496b670b1884347d1a84d1f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88419218"
---
# <a name="xp_logininfo-transact-sql"></a>xp_logininfo (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Возвращают сведения о пользователях и группах Windows.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
xp_logininfo [ [ @acctname = ] 'account_name' ]   
     [ , [ @option = ] 'all' | 'members' ]   
     [ , [ @privilege = ] variable_name OUTPUT]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @acctname = ] 'account_name'` Имя пользователя или группы Windows, которым предоставлен доступ к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Аргумент *account_name* имеет тип **sysname**и значение по умолчанию NULL. Если *account_name* не указан, то выводятся все группы Windows и пользователи Windows, которым было явно предоставлено разрешение на вход. *account_name* должны быть полными. Например, 'ADVWKS4\macraes' или 'BUILTIN\Administrators'.  
  
 **"все"**  |  **"Members"**  
 Указывает, следует ли доставлять данные обо всех путях разрешений для данной учетной записи или только сведения о членах группы Windows. ** \@ параметр имеет тип** **varchar (10)** и значение по умолчанию NULL. Если не указано значение **ALL** , то отображается только первый путь разрешения.  
  
`[ @privilege = ] variable_name` Выходной параметр, возвращающий уровень привилегий указанной учетной записи Windows. *variable_name* имеет тип **varchar (10)** и значение по умолчанию "не требуется". Возвращенный уровень привилегий — **User**, **Admin**или **null**.  
  
 OUTPUT  
 Если указан, помещает *variable_name* в выходной параметр.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**имя учетной записи**|**sysname**|Полностью уточненное имя учетной записи Windows.|  
|**type**|**char (8)**|Тип учетной записи Windows. Допустимые значения: **User** или **Group**.|  
|**правом**|**char(9)**|Права доступа к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Допустимые значения: **Admin**, **User**или **null**.|  
|**mapped login name**|**sysname**|Для учетных записей пользователей, имеющих привилегии пользователя, **сопоставленное имя входа** показывает сопоставленное имя входа, которое [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пытается использовать при входе с помощью этой учетной записи, используя сопоставленные правила с именем домена, добавленным перед ним.|  
|**путь разрешения**|**sysname**|Членство в группе, разрешающее доступ к учетной записи.|  
  
## <a name="remarks"></a>Remarks  
 Если указано *account_name* , **xp_logininfo** сообщает наивысший уровень прав доступа для указанного пользователя или группы Windows. Если пользователь Windows имеет права системного администратора и пользователя домена, он будет выступать в качестве системного администратора. Если пользователь является членом нескольких групп Windows одного уровня прав доступа, группа, которая первой предоставила доступ к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], будет отражена.  
  
 Если *account_name* является допустимым пользователем или группой Windows, не связанными с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] именем входа, возвращается пустой результирующий набор. Если *account_name* не может быть идентифицирован как допустимый пользователь или группа Windows, возвращается сообщение об ошибке.  
  
 Если указаны *account_name* и **ALL** , возвращаются все пути разрешений для пользователя или группы Windows. Если *account_name* является членом нескольких групп, то все, которому был предоставлен доступ к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , возвращаются несколько строк. Строки прав **администратора** возвращаются перед строками привилегий **пользователя** , а в строках уровня привилегий возвращаются в том порядке, в котором [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] были созданы соответствующие имена входа.  
  
 Если указаны *account_name* и **Members** , то возвращается список членов группы следующего уровня. Если *account_name* является локальной группой, в список могут входить локальные пользователи, пользователи домена и группы. Если *account_name* является учетной записью домена, список состоит из пользователей домена. Сервер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен подключиться к контроллеру домена для получения сведений о членстве в группе. Если сервер не может подключиться к контроллеру домена, никакие сведения не возвращаются.  
  
 **xp_logininfo** возвращает сведения только из Active Directory глобальных групп, а не универсальных групп.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли сервера **sysadmin** или членство в **предопределенной** роли базы данных **master** с предоставленным разрешением EXECUTE.  
  
## <a name="examples"></a>Примеры  
 В следующем примере отображаются сведения о `BUILTIN\Administrators` группе Windows.  
  
```  
EXEC xp_logininfo 'BUILTIN\Administrators';  
```  
  
## <a name="see-also"></a>См. также:  
 [sp_denylogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [sp_revokelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Общие расширенные хранимые процедуры &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)  
  
  
