---
title: Набор строк LINKEDSERVERS (OLE DB) | Документация Майкрософт
description: Набор строк LINKEDSERVERS (OLE DB)
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- LINKEDSERVERS rowset
- enumerating data sources [OLE DB]
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 99b942b6cbdf230122c082154c6a9e280444d4e7
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86012784"
---
# <a name="schema-rowsets---linkedservers-rowset"></a>Наборы строк схемы — набор строк LINKEDSERVERS
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Набор строк **LINKEDSERVERS** перечисляет источники данных организации, которые могут применяться в распределенных запросах [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Набор строк **LINKEDSERVERS** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Description|  
|-----------------|--------------------|-----------------|  
|SVR_NAME|DBTYPE_WSTR|Имя связанного сервера.|  
|SVR_PRODUCT|DBTYPE_WSTR|Имя производителя или другое имя, задающее тип хранилища данных, представленного именем связанного сервера.|  
|SVR_PROVIDERNAME|DBTYPE_WSTR|Понятное имя поставщика OLE DB, используемого для получения данных с этого сервера.|  
|SVR_DATASOURCE|DBTYPE_WSTR|Строка OLE DB DBPROP_INIT_DATASOURCE, используемая для получения источника данных от поставщика.|  
|SVR_PROVIDERSTRING|DBTYPE_WSTR|Значение OLE DB DBPROP_INIT_PROVIDERSTRING, используемое для получения источника данных от поставщика.|  
|SVR_LOCATION|DBTYPE_WSTR|Строка OLE DB DBPROP_INIT_LOCATION, используемая для получения источника данных от поставщика.|  
  
 Набор строк сортируется по столбцу SRV_NAME, и единственное ограничение поддерживается для столбца SRV_NAME.  
  
## <a name="see-also"></a>См. также:  
 [Поддержка набора строк схемы &#40;OLE DB&#41;](../../oledb/ole-db/schema-rowset-support-ole-db.md)  
  
  
