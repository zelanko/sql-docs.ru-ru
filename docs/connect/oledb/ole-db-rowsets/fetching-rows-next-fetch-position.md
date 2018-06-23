---
title: Следующая позиция выборки | Документы Microsoft
description: Извлечение строк - положения следующей выборки
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 46e6e3b9898d6c1adbe4df4bdc2b33444b623df9
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/16/2018
ms.locfileid: "35690117"
---
# <a name="fetching-rows---next-fetch-position"></a>Извлечение строк - положения следующей выборки
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Драйвер OLE DB для SQL Server поддерживает отслеживания из положения следующей выборки таким образом, последовательность вызовов **GetNextRows** метода (без пропускает, изменения направления или промежуточных вызовов **FindNextRow** **Seek**, или **свойство RestartPosition** методы) считывает набор строк целиком, не пропускается или повтора любую строку. Позиция следующей выборки меняется с помощью вызова **IRowset::GetNextRows**, **IRowset::RestartPosition**, или **IRowsetIndex::Seek**, или путем вызова **FindNextRow** со значением null *pBookmark* значение. Вызов **FindNextRow** с аргумента *pBookmark* значение не влияет на позицию следующей выборки.  
  
## <a name="see-also"></a>См. также  
 [Выборка строк](../../oledb/ole-db-rowsets/fetching-rows.md)  
  
  
