---
title: IColumnsRowset | Документы Microsoft
description: IColumnsRowset, интерфейс
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 27428d0691d7bd12dc0a21912b4a70d41e51737d
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35304573"
---
# <a name="icolumnsrowset"></a>IColumnsRowset
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер OLE DB для SQL Server добавляет столбец DBCOLUMN_BASETABLEINSTANCE в набор, возвращаемый методом IColumnsRowset::getcolumnrowset. Этот столбец имеет тип данных DBTYPE_I2 и зарезервирован корпорацией Майкрософт для будущего использования. В будущих версиях данные из этого столбца могут быть изменены.  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md) 
  
  
