---
title: Позиция следующей выборки (драйвер OLE DB) | Документация Майкрософт
description: OLE DB Driver for SQL Server отслеживает следующую точку извлечения, чтобы последовательность вызовов метода GetNextRows считала весь набор строк.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0ba713e9da40255d992e7cccf8c8430a205cadf4
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/25/2020
ms.locfileid: "88861581"
---
# <a name="fetching-rows---next-fetch-position-ole-db-driver"></a>Выборка строк — позиция следующей выборки (драйвер OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Драйвер OLE DB для SQL Server отслеживает следующую позицию выборки, чтобы последовательность вызовов метода **GetNextRows** (без пропусков, смены направления или промежуточных вызовов методов **FindNextRow**, **Seek** или **RestartPosition**) считывала весь набор строк без пропусков и повторов строк. Позиция следующей выборки меняется с помощью вызова методов **IRowset::GetNextRows**, **IRowset::RestartPosition** или **IRowsetIndex::Seek** либо вызовом **FindNextRow** со значением *pBookmark*, равным NULL. Вызов **FindNextRow** со значением *pBookmark*, отличным от NULL, не влияет на позицию следующей выборки.  
  
## <a name="see-also"></a>См. также:  
 [Выборка строк](../../oledb/ole-db-rowsets/fetching-rows.md)  
  
  
