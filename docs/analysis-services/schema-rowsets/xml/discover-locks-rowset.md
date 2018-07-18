---
title: Набор строк DISCOVER_LOCKS | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7f0b52b875793df4074e9feb4e0cc1737224a901
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
ms.locfileid: "34031765"
---
# <a name="discoverlocks-rowset"></a>Набор строк DISCOVER_LOCKS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Предоставляет сведения о текущих установленных блокировках на сервере.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DISCOVER_LOCKS** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|**LOCK_CREATION_TIME**|**DBTYPE_DBTIMESTAMP**||Время на сервере в формате UTC в момент запроса блокировки.|  
|**LOCK_GRANT_TIME**|**DBTYPE_DBTIMESTAMP**||Время на сервере в формате UTC в момент предоставления блокировки на ресурс.|  
|**LOCK_ID**|**DBTYPE_GUID**||Уникальный идентификатор блокировки в виде идентификатора GUID.|  
|**LOCK_OBJECT_ID**|**DBTYPE_WSTR**||Уникальный идентификатор блокируемого объекта.|  
|**LOCK_STATUS**|**DBTYPE_I4**||Состояние блокировки.<br /><br /> 0 означает «Ожидание блокировки объекта».<br /><br /> 1 означает «Блокировка предоставлена».|  
|**LOCK_TRANSACTION_ID**|**DBTYPE_GUID**||Уникальный идентификатор транзакции в виде идентификатора GUID.|  
|**LOCK_TYPE**|**DBTYPE_I4**||Битовая маска типов блокировки; дополнительные сведения см. в подразделе «Примечания» этого раздела.|  
|**SPID**|**DBTYPE_I4**||Идентификатор сеанса.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк **DISCOVER_LOCKS** может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|SPID|DBTYPE_I4|Необязательный параметр.|  
|LOCK_TRANSACTION_ID|DBTYPE_GUID|Необязательно.|  
|LOCK_OBJECT_ID|DBTYPE_WSTR|Необязательно.|  
|LOCK_STATUS|DBTYPE_I4|Необязательно.|  
|LOCK_TYPE|DBTYPE_I4|Необязательно.|  
|LOCK_MIN_TOTAL_MS|DBTYPE_I8|Необязательно.|  
  
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
 [XML для аналитики наборы строк схемы](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
