---
title: IDBProperties (OLE DB) | Документация Майкрософт
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
ms.openlocfilehash: ed9348ebc51ab5cfbedfd5c8255892502fef3564
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85785413"
---
# <a name="idbproperties-ole-db"></a>IDBProperties (OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Стандартная спецификация OLE DB допускает задание поставщиками VT_EMPTY для **DBPROPINFO::vValues**. Однако собственный клиент OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] всегда возвращает VT_EMPTY при вызове **IDBProperties::GetPropertyInfo** с **DBPROPSET_ROWSETALL** для извлечения свойств набора строк.  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы (OLE DB)](https://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)  
  
  
