---
title: sp_get_distributor (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_get_distributor
- sp_get_distributor_TSQL
helpviewer_keywords:
- sp_get_distributor
ms.assetid: f0134448-bc17-4f2f-bd81-619351ce56ac
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ccdc8529bb62e4e1db15f0a5ea85a64c5b679abf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62521019"
---
# <a name="spgetdistributor-transact-sql"></a>Хранимая процедура sp_get_distributor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Определяет, установлен ли на сервере распространитель. Хранимая процедура выполняется на компьютере, где выполняется поиск распространителя, в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_get_distributor   
```  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**установлен**|**int**|**0** = нет; **1** = yes|  
|**сервер распространения**|**sysname**|Имя сервера распространителя|  
|**базы данных распространителя установлена**|**int**|**0** = нет; **1** = yes|  
|**является распространяющий издатель**|**int**|**0** = нет; **1** = yes|  
|**имеется Удаленный распространяющий издатель**|**int**|**0** = нет; **1** = yes|  
  
## <a name="remarks"></a>Примечания  
 **sp_get_distributor** используется преимущественно средой [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] в моментальных снимков, транзакций и репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Любой пользователь может выполнить **sp_get_distributor**. Отличное от NULL результирующий набор возвращается, если эта хранимая процедура выполняется членами **db_owner** или **replmonitor** предопределенных ролей базы данных в базу данных распространителя или членами  **db_owner** предопределенной роли базы данных по крайней мере одной опубликованной базы данных. Набор НЕНУЛЕВОЙ результат также возвращается, если эта хранимая процедура выполняется пользователями в списке доступа к публикации (PAL) из по крайней мере одной опубликованной базы данных, либо в список доступа к публикации базы данных распространителя для издателя, отличном от издателя SQL Server, также можно выполнить **sp _get_distributor**.  
  
## <a name="see-also"></a>См. также  
 [Настройка публикации и распространения](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Distributor and Publisher Information Script](../../relational-databases/replication/administration/distributor-and-publisher-information-script.md)  (Скрипт вывода сведений о распространителе и издателе)  
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
