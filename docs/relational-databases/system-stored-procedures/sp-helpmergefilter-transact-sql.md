---
title: sp_helpmergefilter (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergefilter
- sp_helpmergefilter_TSQL
helpviewer_keywords:
- sp_helpmergefilter
ms.assetid: f133a094-0009-4771-b93b-e86a5c01e40b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 668233ad7ee79617caa60933a9eef33c5a810164
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58534706"
---
# <a name="sphelpmergefilter-transact-sql"></a>Хранимая процедура sp_helpmergefilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о фильтрах слияния. Эта хранимая процедура выполняется на подписчике в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpmergefilter [ @publication= ] 'publication'   
    [ , [ @article= ] 'article']  
    [ , [ @filtername= ] 'filtername']  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'` — Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
`[ @article = ] 'article'` — Имя статьи. *статья* — **sysname**, значение по умолчанию **%**, которое возвращает имена всех статей.  
  
`[ @filtername = ] 'filtername'` — Имя фильтра, для которого возвращаются сведения. *FilterName* — **sysname**, значение по умолчанию **%**, которое возвращает сведения обо всех фильтрах, определенных для статьи или публикации.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**join_filterid**|**int**|Идентификатор фильтра соединения.|  
|**FilterName**|**sysname**|Имя фильтра.|  
|**Имя статьи соединения**|**sysname**|Имя статьи соединения.|  
|**join_filterclause**|**nvarchar(2000)**|Выражение фильтра для уточнения соединения.|  
|**join_unique_key**|**int**|Определяет, производится ли соединение по уникальному ключу.|  
|**владельца базовой таблицы**|**sysname**|Имя владельца базовой таблицы.|  
|**имя базовой таблицы**|**sysname**|Имя базовой таблицы.|  
|**Владелец таблицы соединения**|**sysname**|Имя владельца таблицы, соединяемой с основной таблицей.|  
|**Имя соединяемой таблицы**|**sysname**|Имя таблицы, соединяемой с основной таблицей.|  
|**Имя статьи**|**sysname**|Имя статьи таблицы, соединяемой с основной таблицей.|  
|**filter_type**|**tinyint**|Тип фильтра слияния. Может быть одним из следующих:<br /><br /> **1** = только фильтр соединения<br /><br /> **2** = связь логических записей<br /><br /> **3** = both|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_helpmergefilter** используется в репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера и **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_helpmergefilter**.  
  
## <a name="see-also"></a>См. также  
 [sp_addmergefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md)   
 [sp_changemergefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changemergefilter-transact-sql.md)   
 [sp_dropmergefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
