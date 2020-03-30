---
title: IDBProperties (OLE DB) | Документация Майкрософт
description: Интерфейс IDBProperties (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
ms.openlocfilehash: d8515ef92ce1284379327e63a4bd1730577bd8df
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67994473"
---
# <a name="idbproperties-ole-db"></a>IDBProperties (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Стандартная спецификация OLE DB допускает задание поставщиками VT_EMPTY для **DBPROPINFO::vValues**. Однако драйвер OLE DB для SQL Server всегда возвращает VT_EMPTY при вызове **IDBProperties::GetPropertyInfo** с **DBPROPSET_ROWSETALL** для извлечения свойств набора строк.  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы (OLE DB)](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md) 
  
  
