---
title: sp_enum_login_for_proxy (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_enum_login_for_proxy_TSQL
- sp_enum_login_for_proxy
dev_langs:
- TSQL
helpviewer_keywords:
- sp_enum_login_for_proxy
ms.assetid: 62a75019-248a-44c8-a5cc-c79f55ea3acf
ms.author: vanto
author: VanMSFT
manager: jroth
ms.openlocfilehash: fd5b172b7029376d6f9641552315fc64e734cc8a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66822637"
---
# <a name="spenumloginforproxy-transact-sql"></a>sp_enum_login_for_proxy (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отображает связи между учетными записями-посредниками и субъектами безопасности.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_enum_login_for_proxy  
    [ @name = ] 'name'  
    [ @proxy_id = ] id,  
    [ @proxy_name = ] 'proxy_name'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @name = ] 'name'` Имя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] участника, имя входа, роли сервера или **msdb** роли базы данных должны быть перечислены посредники. Имя **nvarchar(256)** , значение по умолчанию NULL.  
  
`[ @proxy_id = ] id` Идентификационный номер прокси-сервера необходимо вывести сведения. *Proxy_id* — **int**, значение по умолчанию NULL. Либо *идентификатор* или *proxy_name* может быть указан.  
  
`[ @proxy_name = ] 'proxy_name'` Имя прокси-сервера необходимо вывести сведения. *Proxy_name* — **sysname**, значение по умолчанию NULL. Либо *идентификатор* или *proxy_name* может быть указан.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|Идентификационный номер учетной записи-посредника.|  
|**proxy_name**|**sysname**|Имя учетной записи-посредника.|  
|**name**|**sysname**|Имя субъекта безопасности для связи.|  
|**flags**|**int**|Тип субъекта безопасности.<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа<br /><br /> **1** = Фиксированная системная роль<br /><br /> **2** = роль базы данных в **msdb**|  
| &nbsp; | &nbsp; | &nbsp; |
  
## <a name="remarks"></a>Примечания  
 Если параметры не указаны, **sp_enum_login_for_proxy** выводит сведения обо всех именах входа в экземпляре для каждого прокси-сервера.  
  
 Если идентификатор или имя прокси-сервера, **sp_enum_login_for_proxy** отображает все имена входа, имеющие доступ к прокси-сервер. Если указано имя входа, **sp_enum_login_for_proxy** прокси-серверы, имя входа имеет доступ к списки.  
  
 Если заданы и сведения об учетной записи-посредника, и имя входа, результирующий набор возвращает строку, если указанное имя входа имеет доступ к указанной учетной записи-посредника.  
  
 Эта хранимая процедура находится в **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 Разрешений на выполнение этой процедуры по умолчанию членами **sysadmin** предопределенной роли сервера.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-listing-all-associations"></a>A. Вывод всех ассоциаций  
 Следующий пример отображает список всех разрешений, установленных между именами входа и учетными записями-посредниками в текущем экземпляре.  
  
```sql
USE msdb ;  
GO  
  
EXEC dbo.sp_enum_login_for_proxy ;  
GO  
```  
  
### <a name="b-listing-proxies-for-a-specific-login"></a>Б. Вывод списка учетных записей-посредников для конкретного имени входа  
 Следующий пример отображает список учетных записей-посредников, к которым имя входа `terrid` имеет доступ.  
  
```sql
USE msdb ;  
GO  
  
EXEC dbo.sp_enum_login_for_proxy  
    @name = 'terrid' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_help_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-proxy-transact-sql.md)   
 [sp_grant_login_to_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grant-login-to-proxy-transact-sql.md)   
 [sp_revoke_login_from_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-login-from-proxy-transact-sql.md)  
  
  
