---
description: Интерфейс IDBProperties (поставщик собственного клиента OLE DB)
title: Интерфейс IDBProperties (поставщик собственного клиента OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 2e5a4fd8-5164-495a-9986-3477aef8d8a5
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d8b1e72d69d047f2fee77db933f9acb447724035
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2020
ms.locfileid: "91866747"
---
# <a name="idbproperties-native-client-ole-db-provider"></a>Интерфейс IDBProperties (поставщик собственного клиента OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Стандартная спецификация OLE DB допускает задание поставщиками VT_EMPTY для **DBPROPINFO::vValues**. Однако собственный клиент OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] всегда возвращает VT_EMPTY при вызове **IDBProperties::GetPropertyInfo** с **DBPROPSET_ROWSETALL** для извлечения свойств набора строк.  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы (OLE DB)](./sql-server-native-client-ole-db-interfaces.md)  
  
