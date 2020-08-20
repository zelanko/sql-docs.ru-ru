---
description: sp_helpmergealternatepublisher (Transact-SQL)
title: sp_helpmergealternatepublisher (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergealternatepublisher_TSQL
- sp_helpmergealternatepublisher
helpviewer_keywords:
- sp_helpmergealternatepublisher
ms.assetid: a96e365f-5967-4580-9d79-5bacf2d12211
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9d20e6273aaafd2c589dbd7e04b38e60890d5c21
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88489336"
---
# <a name="sp_helpmergealternatepublisher-transact-sql"></a>sp_helpmergealternatepublisher (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Возвращает список всех серверов, которые разрешены как альтернативные издатели для публикации слиянием. Эта хранимая процедура выполняется на подписчике в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpmergealternatepublisher [ @publisher = ] 'publisher', [ @publisher_db = ] 'publisher_db', [ @publication = ] 'publication'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publisher = ] 'publisher'` Имя альтернативного издателя. параметр *Publisher* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publisher_db = ] 'publisher_db'` Имя базы данных публикации. Аргумент *publisher_db* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publication = ] 'publication'` Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**alternate_publisher**|**sysname**|Имя альтернативного издателя.|  
|**alternate_publisher_db**|**sysname**|Имя базы данных публикации.|  
|**alternate_publication**|**sysname**|Имя публикации.|  
|**alternate_distributor**|**sysname**|Имя распространителя.|  
|**friendly_name**|**nvarchar(255)**|Описание альтернативного издателя.|  
|**доступной**|**bit**|Определяет, является ли сервер альтернативным издателем. значение **1** указывает, что издатель включен в качестве альтернативного издателя. **0** указывает, что он не включен.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Комментарии  
 **sp_helpmergealternatepublisher** используется в репликации слиянием.  
  
 Во время каждого сеанса слияния система запрашивает у издателя и подписчика список их альтернативных издателей. Процесс слияния добавляет или удаляет записи в список альтернативных издателей, в результате создается список альтернативных издателей, которые присутствуют и в списке издателя и в списке подписчика.  
  
## <a name="permissions"></a>Разрешения  
 Только члены списка доступа к публикации могут выполнять **sp_helpmergealternatepublisher**.  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
