---
title: Позиция следующей выборки (драйвер OLE DB) | Документация Майкрософт
description: Выборка строк — следующая позиция выборки
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
author: pmasl
ms.author: pelopes
ms.openlocfilehash: d6fd65f54f0c6f6aa219595e1948ce758c50b4db
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87244205"
---
# <a name="fetching-rows---next-fetch-position-ole-db-driver"></a>Выборка строк — позиция следующей выборки (драйвер OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Драйвер OLE DB для SQL Server отслеживает следующую позицию выборки, чтобы последовательность вызовов метода **GetNextRows** (без пропусков, смены направления или промежуточных вызовов методов **FindNextRow**, **Seek** или **RestartPosition**) считывала весь набор строк без пропусков и повторов строк. Позиция следующей выборки меняется с помощью вызова методов **IRowset::GetNextRows**, **IRowset::RestartPosition** или **IRowsetIndex::Seek** либо вызовом **FindNextRow** со значением *pBookmark*, равным NULL. Вызов **FindNextRow** со значением *pBookmark*, отличным от NULL, не влияет на позицию следующей выборки.  
  
## <a name="see-also"></a>См. также:  
 [Выборка строк](../../oledb/ole-db-rowsets/fetching-rows.md)  
  
  
