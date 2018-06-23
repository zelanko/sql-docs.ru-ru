---
title: Набор строк DISCOVER_TRANSACTIONS | Документы Microsoft
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 85789177-c5df-4336-a90c-c20d69277ab4
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 3869d4f8cd3adf96bd006a8669d7d82778b02450
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095576"
---
# <a name="discovertransactions-rowset"></a>Набор строк DISCOVER_TRANSACTIONS
  Возвращает текущий набор ожидающих транзакций в системе.  
  
 **Область применения:** табличные модели, многомерные модели  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `DISCOVER_TRANSACTIONS` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Описание|  
|-----------------|--------------------|-----------------|  
|`TRANSACTION_ID`|`DBTYPE_WSTR`|Уникальный идентификатор транзакции в виде идентификатора GUID.|  
|`TRANSACTION_SESSION_ID`|`DBTYPE_WSTR`|Уникальный идентификатор сеанса в виде идентификатора GUID.|  
|`TRANSACTION_START_TIME`|`DBTYPE_DBTIMESTAMP`|Дата и время запуска транзакции на сервере в формате UTC.|  
|`TRANSACTION_ELAPSED_TIME_MS`|`DBTYPE_I8`|Общее затраченное время в миллисекундах после начала транзакции.|  
|`TRANSACTION_CPU_TIME_MS`|`DBTYPE_I8`|Время ЦП (в миллисекундах), использованное всеми запросами с начала транзакции.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `DISCOVER_TRANSACTIONS` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|**Имя столбца**|**Индикатор типа**|**Состояние ограничения**|  
|---------------------|------------------------|---------------------------|  
|`ID`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`SESSION_ID`|`DBTYPE_WSTR`|Необязательный параметр.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Использование ADOMD.NET для возврата набора строк  
 Если для получения метаданных используется ADOMD.NET и набор строк схемы, то для ссылки на объект набора строк схемы в методе GetSchemaDataSet вы можете использовать идентификатор GUID или строку. Дополнительные сведения см. в статье [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 В следующей таблице указываются значения строки и идентификатора GUID, определяющие этот набор строк.  
  
|Аргумент|Значение|  
|--------------|-----------|  
|GUID|a07ccd28-8148-11d0-87bb-00c04fc33942|  
|String|DISCOVER_TRANSACTIONS|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы XML для аналитики](xml-for-analysis-schema-rowsets.md)  
  
  