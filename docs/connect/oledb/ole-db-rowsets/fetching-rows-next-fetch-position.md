---
title: Следующая позиция выборки | Документация Майкрософт
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
manager: jroth
ms.openlocfilehash: a619923c2fb144fa0572c8706edbdc6b908ad621
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66803186"
---
# <a name="fetching-rows---next-fetch-position"></a>Выборка строк — следующая позиция выборки
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Драйвер OLE DB для SQL Server отслеживает следующую позицию выборки, чтобы последовательность вызовов метода **GetNextRows** (без пропусков, смены направления или промежуточных вызовов методов **FindNextRow**, **Seek** или **RestartPosition**) считывала весь набор строк без пропусков и повторов строк. Позиция следующей выборки меняется с помощью вызова методов **IRowset::GetNextRows**, **IRowset::RestartPosition** или **IRowsetIndex::Seek** либо вызовом **FindNextRow** со значением *pBookmark*, равным NULL. Вызов **FindNextRow** со значением *pBookmark*, отличным от NULL, не влияет на позицию следующей выборки.  
  
## <a name="see-also"></a>См. также:  
 [Выборка строк](../../oledb/ole-db-rowsets/fetching-rows.md)  
  
  
