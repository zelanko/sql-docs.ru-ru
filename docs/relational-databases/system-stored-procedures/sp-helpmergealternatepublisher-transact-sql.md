---
title: sp_helpmergealternatepublisher (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_helpmergealternatepublisher_TSQL
- sp_helpmergealternatepublisher
helpviewer_keywords:
- sp_helpmergealternatepublisher
ms.assetid: a96e365f-5967-4580-9d79-5bacf2d12211
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 9a66e9c0343a4441d3a5bf370d96ff7f6bf61370
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sphelpmergealternatepublisher-transact-sql"></a>sp_helpmergealternatepublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает список всех серверов, которые разрешены как альтернативные издатели для публикации слиянием. Эта хранимая процедура выполняется на подписчике в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpmergealternatepublisher [ @publisher = ] 'publisher', [ @publisher_db = ] 'publisher_db', [ @publication = ] 'publication'  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publisher=**] **"***издатель***"**  
 — Это имя альтернативного издателя. *издатель* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@publisher_db=**] **"***publisher_db***"**  
 — Это имя базы данных публикации. *publisher_db* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@publication=**] **"***публикации***"**  
 — Имя публикации. *публикации* — **sysname**, не имеет значения по умолчанию.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**alternate_publisher**|**sysname**|Имя альтернативного издателя.|  
|**alternate_publisher_db**|**sysname**|Имя базы данных публикации.|  
|**alternate_publication**|**sysname**|Имя публикации.|  
|**alternate_distributor**|**sysname**|Имя распространителя.|  
|**Аргумент**|**nvarchar(255)**|Описание альтернативного издателя.|  
|**Включен**|**бит**|Определяет, является ли сервер альтернативным издателем. **1** указывает, что издатель альтернативного издателя. **0** указывает, что он не включен.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_helpmergealternatepublisher** используется в репликации слиянием.  
  
 Во время каждого сеанса слияния система запрашивает у издателя и подписчика список их альтернативных издателей. Процесс слияния добавляет или удаляет записи в список альтернативных издателей, в результате создается список альтернативных издателей, которые присутствуют и в списке издателя и в списке подписчика.  
  
## <a name="permissions"></a>Разрешения  
 Можно выполнять только члены списка доступа публикации для публикации **sp_helpmergealternatepublisher**.  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
