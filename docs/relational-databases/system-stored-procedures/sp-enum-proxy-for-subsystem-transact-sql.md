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
manager: craigg
ms.openlocfilehash: d521a16fa7c18e67e1929cb0e38aecf862d6c18a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66822641"
---
# <a name="spenumproxyforsubsystem-transact-sql"></a>sp_enum_proxy_for_subsystem (Transact-SQL)

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
`[ @proxy_id = ] proxy_id` Идентификационный номер прокси-сервера необходимо вывести сведения. *Proxy_id* — **int**, значение по умолчанию NULL. Либо *идентификатор* или *proxy_name* может быть указан.  
  
`[ @proxy_name = ] 'proxy_name'` Имя прокси-сервера необходимо вывести сведения. *Proxy_name* — **sysname**, значение по умолчанию NULL. Либо *идентификатор* или *proxy_name* может быть указан.  
  
`[ @subsystem_id = ] subsystem_id` Идентификационный номер подсистемы, о которой предоставляются сведения. *Subsystem_id* — **int**, значение по умолчанию NULL. Либо *subsystem_id* или *subsystem_name* может быть указан.  
  
`[ @subsystem_name = ] 'subsystem_name'` Имя подсистемы, о которой предоставляются сведения. *Subsystem_name* — **sysname**, значение по умолчанию NULL. Либо *subsystem_id* или *subsystem_name* может быть указан.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**subsystem_id**|**int**|Идентификационный номер подсистемы.|  
|**subsystem_name**|**sysname**|Имя подсистемы.|  
|**proxy_id**|**int**|Идентификационный номер учетной записи-посредника.|  
|**proxy_name**|**sysname**|Имя учетной записи-посредника.|  
| &nbsp; | &nbsp; | &nbsp; |
  
## <a name="remarks"></a>Примечания  
 Если параметры не указаны, **sp_enum_proxy_for_subsystem** выводит сведения о всех учетных записях-посредниках для всех подсистем экземпляра.  
  
 Если идентификатор или имя прокси-сервера, **sp_enum_proxy_for_subsystem** выдает список подсистем, прокси-сервер имеет доступ к. Если идентификатор или имя подсистемы, **sp_enum_proxy_for_subsystem** перечислены учетные записи-посредники, которые имеют доступ к данной подсистеме.  
  
 Если указываются сведения о конкретной подсистеме и учетной записи-посреднике, то в случае наличия у заданной учетной записи-посредника доступа к заданной подсистеме результирующий набор возвращает строку.  
  
 Эта хранимая процедура находится в **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 Разрешений на выполнение этой процедуры по умолчанию членами **sysadmin** предопределенной роли сервера.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-listing-all-associations"></a>A. Вывод всех ассоциаций  
 При выполнении следующего примера выводится список всех разрешений, установленных между учетными записями-посредниками и подсистемами в данном экземпляре.  
  
```sql
USE msdb ;  
GO  
  
EXEC dbo.sp_enum_proxy_for_subsystem ;  
GO  
```  
  
### <a name="b-determining-if-a-proxy-has-access-to-a-specific-subsystem"></a>Б. Определение наличия доступа к указанной подсистеме у учетной записи-посредника  
 В следующем примере при наличии у учетной записи-посредника `Catalog application proxy` доступа к подсистеме `ActiveScripting` возвращается строка. В противном случае возвращается пустой результирующий набор.  
  
```sql
USE msdb ;  
GO  
  
EXEC dbo.sp_enum_proxy_for_subsystem  
    @subsystem_name = 'ActiveScripting',  
    @proxy_name = 'Catalog application proxy' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_grant_proxy_to_subsystem &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grant-proxy-to-subsystem-transact-sql.md)  
  
  
