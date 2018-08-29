---
title: IDBProperties (OLE DB) | Документация Майкрософт
description: Интерфейс IDBProperties (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: a5b8c3626cd95d19b6eb79d28d042bed38a4b602
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43017319"
---
# <a name="idbproperties-ole-db"></a>IDBProperties (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Стандартная спецификация OLE DB допускает задание поставщиками VT_EMPTY для **DBPROPINFO::vValues**. Однако драйвер OLE DB для SQL Server всегда возвращает VT_EMPTY при вызове **IDBProperties::GetPropertyInfo** с **DBPROPSET_ROWSETALL** для извлечения свойств набора строк.  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md) 
  
  
