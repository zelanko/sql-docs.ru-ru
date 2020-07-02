---
title: sp_getmergedeletetype (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_getmergedeletetype
- sp_getmergedeletetype_TSQL
helpviewer_keywords:
- sp_getmergedeletetype
ms.assetid: 64450e4d-844d-4176-874e-f3845536f7d2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 00a7499fb3050a5ab13fa3e9b454b4335200f55a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85731665"
---
# <a name="sp_getmergedeletetype-transact-sql"></a>sp_getmergedeletetype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Возвращает тип удаления слияния. Эта хранимая процедура выполняется на издателе в базе данных публикации или на подписчике в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_getmergedeletetype [ @source_object = ] 'source_object', [ @rowguid =] 'rowguid', [ @delete_type=] delete_type OUTPUT  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @source_object = ] 'source_object'`Имя исходного объекта. *source_object* имеет тип **nvarchar (386)** и не имеет значения по умолчанию.  
  
`[ @rowguid = ] 'rowguid'`Идентификатор строки для типа удаления. *rowguid* имеет тип **uniqueidentifier**и не имеет значения по умолчанию.  
  
`[ @delete_type = ] delete_type OUTPUT`— Это код, указывающий тип удаления. *delete_type* имеет **тип int**и не имеет значения по умолчанию. *delete_type* также является выходным параметром и может принимать одно из следующих значений.  
  
|Применение|Описание|  
|-----------|-----------------|  
|**1**|Пользовательское удаление|  
|**5**|Частичное удаление|  
|**6**|Системное удаление|  
  
## <a name="remarks"></a>Примечания  
 **sp_getmergedeletetype** используется в репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_getmergedeletetype**.  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
