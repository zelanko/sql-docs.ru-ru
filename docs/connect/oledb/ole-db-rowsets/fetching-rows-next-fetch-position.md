---
title: Следующая позиция выборки | Документы Microsoft
description: Извлечение строк - положения следующей выборки
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-rowsets
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
ms.openlocfilehash: b3e7bb16d9f2c04525a0646b9f4647fdd1e811e0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="fetching-rows---next-fetch-position"></a>Извлечение строк - положения следующей выборки
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер OLE DB для SQL Server поддерживает отслеживания из положения следующей выборки таким образом, последовательность вызовов **GetNextRows** метода (без пропускает, изменения направления или промежуточных вызовов **FindNextRow** **Seek**, или **свойство RestartPosition** методы) считывает набор строк целиком, не пропускается или повтора любую строку. Позиция следующей выборки меняется с помощью вызова **IRowset::GetNextRows**, **IRowset::RestartPosition**, или **IRowsetIndex::Seek**, или путем вызова **FindNextRow** со значением null *pBookmark* значение. Вызов **FindNextRow** с аргумента *pBookmark* значение не влияет на позицию следующей выборки.  
  
## <a name="see-also"></a>См. также  
 [Выборка строк](../../oledb/ole-db-rowsets/fetching-rows.md)  
  
  
