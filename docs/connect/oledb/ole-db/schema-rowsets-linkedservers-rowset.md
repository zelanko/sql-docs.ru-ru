---
title: Набор строк LINKEDSERVERS (OLE DB) | Документы Microsoft
description: Набор строк LINKEDSERVERS (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- LINKEDSERVERS rowset
- enumerating data sources [OLE DB]
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b00a600f2690981f152c75c92dc467c1d6d13aed
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="schema-rowsets---linkedservers-rowset"></a>Наборы строк схемы — набор строк LINKEDSERVERS
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **LINKEDSERVERS** набор строк перечисляет источники данных организации, которые могут участвовать в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] распределенных запросов.  
  
 Набор строк **LINKEDSERVERS** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Описание|  
|-----------------|--------------------|-----------------|  
|SVR_NAME|DBTYPE_WSTR|Имя связанного сервера.|  
|SVR_PRODUCT|DBTYPE_WSTR|Имя производителя или другое имя, задающее тип хранилища данных, представленного именем связанного сервера.|  
|SVR_PROVIDERNAME|DBTYPE_WSTR|Понятное имя поставщика OLE DB, используемого для получения данных с этого сервера.|  
|SVR_DATASOURCE|DBTYPE_WSTR|Строка OLE DB DBPROP_INIT_DATASOURCE, используемая для получения источника данных от поставщика.|  
|SVR_PROVIDERSTRING|DBTYPE_WSTR|Значение OLE DB DBPROP_INIT_PROVIDERSTRING, используемое для получения источника данных от поставщика.|  
|SVR_LOCATION|DBTYPE_WSTR|Строка OLE DB DBPROP_INIT_LOCATION, используемая для получения источника данных от поставщика.|  
  
 Набор строк сортируется по столбцу SRV_NAME, и единственное ограничение поддерживается для столбца SRV_NAME.  
  
## <a name="see-also"></a>См. также  
 [Поддержка наборов строк схемы &#40;OLE DB&#41;](../../oledb/ole-db/schema-rowset-support-ole-db.md)  
  
  
