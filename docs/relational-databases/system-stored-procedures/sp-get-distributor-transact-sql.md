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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 545bc84b8b68f89428912aba635c87ce23dcbd22
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85757927"
---
# <a name="sp_get_distributor-transact-sql"></a>Хранимая процедура sp_get_distributor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Определяет, установлен ли на сервере распространитель. Хранимая процедура выполняется на компьютере, где выполняется поиск распространителя, в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_get_distributor   
```  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**Установка**|**int**|**0** = нет; **1** = да|  
|**сервер распространения**|**sysname**|Имя сервера распространителя|  
|**база данных распространителя установлена**|**int**|**0** = нет; **1** = да|  
|**is distribution publisher**|**int**|**0** = нет; **1** = да|  
|**есть Удаленный распространяющий издатель**|**int**|**0** = нет; **1** = да|  
  
## <a name="remarks"></a>Примечания  
 **sp_get_distributor** используется главным образом в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] в репликации моментальных снимков, транзакций и слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Любой пользователь может выполнить **sp_get_distributor**. Результирующий набор, отличный от NULL, возвращается при выполнении этой хранимой процедуры членами предопределенной роли базы данных **db_owner** или **replmonitor** в базе данных распространителя или членами предопределенной роли базы данных **db_owner** по крайней мере в одной опубликованной базе данных. Результирующий набор, отличный от NULL, также возвращается при выполнении этой хранимой процедуры пользователями из списка доступа к публикации (PAL) по крайней мере одной опубликованной базы данных или в списке PAL базы данных распространителя для издателя, не являющегося SQL Server, также может выполняться **sp_get_distributor**.  
  
## <a name="see-also"></a>См. также  
 [Настройка публикации и распространения](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Скрипт сведений о распространителе и издателе](../../relational-databases/replication/administration/distributor-and-publisher-information-script.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
