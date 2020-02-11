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
ms.openlocfilehash: ee6b6a701d4ff81863973c4c8e098bd9ed49c967
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68124683"
---
# <a name="sp_enum_login_for_proxy-transact-sql"></a>sp_enum_login_for_proxy (Transact-SQL)

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
`[ @name = ] 'name'`Имя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] участника, имя входа, роль сервера или роль базы данных **msdb** , для которой перечисляются учетные записи-посредники. Имя имеет тип **nvarchar (256)** и значение по умолчанию NULL.  
  
`[ @proxy_id = ] id`Идентификационный номер прокси-сервера, для которого необходимо получить список сведений. *Proxy_id* имеет **тип int**и значение по умолчанию NULL. Можно указать либо *идентификатор* , либо *proxy_name* .  
  
`[ @proxy_name = ] 'proxy_name'`Имя учетной записи-посредника для получения списка сведений. Аргумент *proxy_name* имеет тип **sysname**и значение по умолчанию NULL. Можно указать либо *идентификатор* , либо *proxy_name* .  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|Идентификационный номер учетной записи-посредника.|  
|**proxy_name**|**имеет sysname**|Имя учетной записи-посредника.|  
|**name**|**имеет sysname**|Имя субъекта безопасности для связи.|  
|**Метки**|**int**|Тип субъекта безопасности.<br /><br /> **** =  0[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имя входа<br /><br /> **1** = предопределенная системная роль<br /><br /> **2** = роль базы данных в **msdb**|  
| &nbsp; | &nbsp; | &nbsp; |
  
## <a name="remarks"></a>Remarks  
 Если параметры не указаны, **sp_enum_login_for_proxy** выводит сведения обо всех именах входа в экземпляре для каждого прокси-сервера.  
  
 При указании идентификатора прокси-сервера или имени прокси-сервера **sp_enum_login_for_proxy** список имен входа, имеющих доступ к учетной записи-посреднику. Если указано имя входа, **sp_enum_login_for_proxy** выводит список учетных записей-посредников, к которым у имени входа есть доступ.  
  
 Если заданы и сведения об учетной записи-посредника, и имя входа, результирующий набор возвращает строку, если указанное имя входа имеет доступ к указанной учетной записи-посредника.  
  
 Эта хранимая процедура находится в **базе данных msdb**.  
  
## <a name="permissions"></a>Разрешения  
 Разрешения на выполнение этой процедуры по умолчанию имеют члены предопределенной роли сервера **sysadmin** .  
  
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
  
## <a name="see-also"></a>См. также:  
 [sp_help_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-proxy-transact-sql.md)   
 [sp_grant_login_to_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grant-login-to-proxy-transact-sql.md)   
 [sp_revoke_login_from_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-login-from-proxy-transact-sql.md)  
  
  
