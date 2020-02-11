---
title: sp_fulltext_pendingchanges (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_fulltext_pendingchanges_TSQL
- sp_fulltext_pendingchanges
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_pendingchanges
ms.assetid: fee042fe-4781-4a33-a01b-d98fb5629f1b
author: MikeRayMSFT
ms.author: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d4d8cbd7082a3ec8d19ccc6df7212a70b101e6b8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68124217"
---
# <a name="sp_fulltext_pendingchanges-transact-sql"></a>sp_fulltext_pendingchanges (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает необработанные изменения, например ожидающие выполнения операции вставки, обновления и удаления, для указанной таблицы, в которой отслеживаются изменения.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_fulltext_pendingchanges table_id  
```  
  
## <a name="arguments"></a>Аргументы  
 *table_id*  
 Идентификатор таблицы. Если таблица не включена в полнотекстовый индекс или отслеживание изменений не включено для данной таблицы, то возвращается ошибка.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**Key**|*|Значение полнотекстового ключа из указанной таблицы.|  
|**DocId**|**bigint**|Столбец внутреннего идентификатора документа (DocId), который соответствует значению ключа.|  
|**Состояние**|**int**|0 = строка будет удалена из полнотекстового индекса<br /><br /> 1 = строка будет включена в полнотекстовый индекс<br /><br /> 2 = обновленная строка<br /><br /> -1 = строка в переходном состоянии (включена в пакет изменений, но не зафиксирована) или в состоянии ошибки|  
|**DocState**|**tinyint**|Необработанный дамп столбца состояния схемы внутренних идентификаторов документа (DOCID).|  
  
 <sup>* Тип данных для столбца Key совпадает с типом данных полнотекстового ключевого столбца в базовой таблице.</sup>  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="remarks"></a>Remarks  
 Если отсутствуют изменения, которые нужно обработать, то возвращается пустой набор строк.  
  
 Запросы полнотекстового поиска не возвращают строки со значением **состояния** 0. Это происходит потому, что эти строки удалены из базовой таблицы и ожидается их удаление из полнотекстового индекса.  
  
 Для определения количества изменений, ожидающихся в определенной таблице, используется свойство **TableFullTextPendingChanges** функции OBJECTPROPERTYEX.  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры полнотекстового поиска и семантического поиска &#40;языке Transact-SQL&#41;](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)   
 [OBJECTPROPERTYEX (Transact-SQL)](../../t-sql/functions/objectpropertyex-transact-sql.md)  
  
  
