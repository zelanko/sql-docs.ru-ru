---
title: Набор строк DISCOVER_LOCKS | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- DISCOVER_LOCKS rowset
ms.assetid: dea48167-212c-40b7-a416-434042a1b697
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4458d9dac98fd35d54ff35c0d1d524a92b576ba5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37167605"
---
# <a name="discoverlocks-rowset"></a>Набор строк DISCOVER_LOCKS
  Предоставляет сведения о текущих установленных блокировках на сервере.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `DISCOVER_LOCKS` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`LOCK_CREATION_TIME`|`DBTYPE_DBTIMESTAMP`||Время на сервере в формате UTC в момент запроса блокировки.|  
|`LOCK_GRANT_TIME`|`DBTYPE_DBTIMESTAMP`||Время на сервере в формате UTC в момент предоставления блокировки на ресурс.|  
|`LOCK_ID`|`DBTYPE_GUID`||Уникальный идентификатор блокировки в виде идентификатора GUID.|  
|`LOCK_OBJECT_ID`|`DBTYPE_WSTR`||Уникальный идентификатор блокируемого объекта.|  
|`LOCK_STATUS`|`DBTYPE_I4`||Состояние блокировки.<br /><br /> 0 означает «Ожидание блокировки объекта».<br /><br /> 1 означает «Блокировка предоставлена».|  
|`LOCK_TRANSACTION_ID`|`DBTYPE_GUID`||Уникальный идентификатор транзакции в виде идентификатора GUID.|  
|`LOCK_TYPE`|`DBTYPE_I4`||Битовая маска типов блокировки; дополнительные сведения см. в подразделе «Примечания» этого раздела.|  
|`SPID`|`DBTYPE_I4`||Идентификатор сеанса.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `DISCOVER_LOCKS` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|SPID|DBTYPE_I4|Необязательный параметр.|  
|LOCK_TRANSACTION_ID|DBTYPE_GUID|Необязательный параметр.|  
|LOCK_OBJECT_ID|DBTYPE_WSTR|Необязательный параметр.|  
|LOCK_STATUS|DBTYPE_I4|Необязательный параметр.|  
|LOCK_TYPE|DBTYPE_I4|Необязательный параметр.|  
|LOCK_MIN_TOTAL_MS|DBTYPE_I8|Необязательный параметр.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="lock-types"></a>Типы блокировок  
  
|Имя блокировки|Значение|Описание|  
|---------------|-----------|-----------------|  
|LOCK_NONE|0x0000000|Блокировка отсутствует.|  
|LOCK_SESSION_LOCK|0x0000001|Неактивный сеанс; нарушения в работе под действием других блокировок не возникают.|  
|LOCK_READ|0x0000002|Блокировка чтения во время обработки.|  
|LOCK_WRITE|0x0000004|Блокировка записи во время обработки.|  
|LOCK_COMMIT_READ|0x0000008|Блокировка фиксации, общая.|  
|LOCK_COMMIT_WRITE|0x0000010|Блокировка фиксации, монопольная.|  
|LOCK_COMMIT_ABORTABLE|0x0000020|Аварийное прекращение работы в ходе выполнения фиксации.|  
|LOCK_COMMIT_INPROGRESS|0x0000040|Происходит фиксация.|  
|LOCK_INVALID|0x0000080|Недействительная блокировка.|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы XML для аналитики](xml-for-analysis-schema-rowsets.md)  
  
  
