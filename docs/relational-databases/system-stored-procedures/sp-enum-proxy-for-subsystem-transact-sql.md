---
title: sp_enum_proxy_for_subsystem (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_enum_proxy_for_subsystem_TSQL
- sp_enum_proxy_for_subsystem
dev_langs:
- TSQL
helpviewer_keywords:
- sp_enum_proxy_for_subsystems
ms.assetid: 580cc3be-1068-4a96-8d15-78ca3a5bb719
ms.author: vanto
author: VanMSFT
ms.openlocfilehash: 93a55b28325bd9b04af569120ad34baeb689e8f9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68124665"
---
# <a name="sp_enum_proxy_for_subsystem-transact-sql"></a>sp_enum_proxy_for_subsystem (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Выдает список разрешений для учетных записей-посредников агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на доступ к подсистемам.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_enum_proxy_for_subsystem  
    [ @proxy_id = ] proxy_id,  
    [ @proxy_name = ] 'proxy_name',  
    [ @subsystem_id = ] subsystem_id,  
    [ @subsystem_name = ] 'subsystem_name'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @proxy_id = ] proxy_id`Идентификационный номер учетной записи-посредника для получения списка сведений. *Proxy_id* имеет **тип int**и значение по умолчанию NULL. Можно указать либо *идентификатор* , либо *proxy_name* .  
  
`[ @proxy_name = ] 'proxy_name'`Имя учетной записи-посредника для получения списка сведений. Аргумент *proxy_name* имеет тип **sysname**и значение по умолчанию NULL. Можно указать либо *идентификатор* , либо *proxy_name* .  
  
`[ @subsystem_id = ] subsystem_id`Идентификационный номер подсистемы, для которой необходимо вывести сведения. *Subsystem_id* имеет **тип int**и значение по умолчанию NULL. Можно указать либо *subsystem_id* , либо *subsystem_name* .  
  
`[ @subsystem_name = ] 'subsystem_name'`Имя подсистемы, для которой необходимо вывести сведения. Аргумент *subsystem_name* имеет тип **sysname**и значение по умолчанию NULL. Можно указать либо *subsystem_id* , либо *subsystem_name* .  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**subsystem_id**|**int**|Идентификационный номер подсистемы.|  
|**subsystem_name**|**sysname**|Имя подсистемы.|  
|**proxy_id**|**int**|Идентификационный номер учетной записи-посредника.|  
|**proxy_name**|**sysname**|Имя учетной записи-посредника.|  
| &nbsp; | &nbsp; | &nbsp; |
  
## <a name="remarks"></a>Remarks  
 Если параметры не указаны, **sp_enum_proxy_for_subsystem** выводит сведения обо всех учетных записях-посредниках в экземпляре для каждой подсистемы.  
  
 При указании идентификатора прокси-сервера или имени прокси-сервера **sp_enum_proxy_for_subsystem** перечисляет подсистемы, к которым прокси-сервер имеет доступ. Если указано имя подсистемы или подсистемы, **sp_enum_proxy_for_subsystem** выводит список учетных записей-посредников, имеющих доступ к этой подсистеме.  
  
 Если указываются сведения о конкретной подсистеме и учетной записи-посреднике, то в случае наличия у заданной учетной записи-посредника доступа к заданной подсистеме результирующий набор возвращает строку.  
  
 Эта хранимая процедура находится в **базе данных msdb**.  
  
## <a name="permissions"></a>Разрешения  
 Разрешения на выполнение этой процедуры по умолчанию имеют члены предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-listing-all-associations"></a>A. Вывод всех ассоциаций  
 При выполнении следующего примера выводится список всех разрешений, установленных между учетными записями-посредниками и подсистемами в данном экземпляре.  
  
```sql
USE msdb ;  
GO  
  
EXEC dbo.sp_enum_proxy_for_subsystem ;  
GO  
```  
  
### <a name="b-determining-if-a-proxy-has-access-to-a-specific-subsystem"></a>Б) Определение наличия доступа к указанной подсистеме у учетной записи-посредника  
 В следующем примере при наличии у учетной записи-посредника `Catalog application proxy` доступа к подсистеме `ActiveScripting` возвращается строка. В противном случае возвращается пустой результирующий набор.  
  
```sql
USE msdb ;  
GO  
  
EXEC dbo.sp_enum_proxy_for_subsystem  
    @subsystem_name = 'ActiveScripting',  
    @proxy_name = 'Catalog application proxy' ;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sp_grant_proxy_to_subsystem &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grant-proxy-to-subsystem-transact-sql.md)  
  
  
