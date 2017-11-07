---
title: "Набор строк DISCOVER_TRANSACTIONS | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 85789177-c5df-4336-a90c-c20d69277ab4
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0b287af43de1284c727a64d27d55b3ccf75c5d87
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="discovertransactions-rowset"></a>Набор строк DISCOVER_TRANSACTIONS
  Возвращает текущий набор ожидающих транзакций в системе.  
  
 **Область применения:** табличные модели, многомерные модели  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DISCOVER_TRANSACTIONS** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Description|  
|-----------------|--------------------|-----------------|  
|**TRANSACTION_ID**|**DBTYPE_WSTR**|Уникальный идентификатор транзакции в виде идентификатора GUID.|  
|**TRANSACTION_SESSION_ID**|**DBTYPE_WSTR**|Уникальный идентификатор сеанса в виде идентификатора GUID.|  
|**TRANSACTION_START_TIME**|**DBTYPE_DBTIMESTAMP**|Дата и время запуска транзакции на сервере в формате UTC.|  
|**TRANSACTION_ELAPSED_TIME_MS**|**DBTYPE_I8**|Общее затраченное время в миллисекундах после начала транзакции.|  
|**TRANSACTION_CPU_TIME_MS**|**DBTYPE_I8**|Время ЦП (в миллисекундах), использованное всеми запросами с начала транзакции.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк **DISCOVER_TRANSACTIONS** может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|**Имя столбца**|**Индикатор типа**|**Состояние ограничения**|  
|---------------------|------------------------|---------------------------|  
|**Идентификатор**|**DBTYPE_WSTR**|Необязательно.|  
|**SESSION_ID**|**DBTYPE_WSTR**|Необязательно.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Использование ADOMD.NET для возврата набора строк  
 Если для получения метаданных используется ADOMD.NET и набор строк схемы, то для ссылки на объект набора строк схемы в методе GetSchemaDataSet вы можете использовать идентификатор GUID или строку. Дополнительные сведения см. в статье [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 В следующей таблице указываются значения строки и идентификатора GUID, определяющие этот набор строк.  
  
|Аргумент|Значение|  
|--------------|-----------|  
|GUID|a07ccd28-8148-11d0-87bb-00c04fc33942|  
|Строковые значения|DISCOVER_TRANSACTIONS|  
  
## <a name="see-also"></a>См. также:  
 [XML для аналитики наборы строк схемы](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  

