---
title: IColumnsRowset | Документация Майкрософт
description: IColumnsRowset, интерфейс
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
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: da249467e9eeca92009266eec5190f20b488f9e3
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/18/2018
ms.locfileid: "39107846"
---
# <a name="icolumnsrowset"></a>IColumnsRowset
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Драйвер OLE DB для SQL Server добавляет столбец DBCOLUMN_BASETABLEINSTANCE в набор, возвращаемый методом IColumnsRowset::getcolumnrowset. Этот столбец имеет тип данных DBTYPE_I2 и зарезервирован корпорацией Майкрософт для будущего использования. В будущих версиях данные из этого столбца могут быть изменены.  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md) 
  
  
