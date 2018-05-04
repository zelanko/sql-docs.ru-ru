---
title: Следующая позиция выборки | Документы Microsoft
description: Извлечение строк - положения следующей выборки
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
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
ms.openlocfilehash: 9613ea77a5eaac5136c6ca744a7201621fa3b876
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="fetching-rows---next-fetch-position"></a>Извлечение строк - положения следующей выборки
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер OLE DB для SQL Server поддерживает отслеживания из положения следующей выборки таким образом, последовательность вызовов **GetNextRows** метода (без пропускает, изменения направления или промежуточных вызовов **FindNextRow** **Seek**, или **свойство RestartPosition** методы) считывает набор строк целиком, не пропускается или повтора любую строку. Позиция следующей выборки меняется с помощью вызова **IRowset::GetNextRows**, **IRowset::RestartPosition**, или **IRowsetIndex::Seek**, или путем вызова **FindNextRow** со значением null *pBookmark* значение. Вызов **FindNextRow** с аргумента *pBookmark* значение не влияет на позицию следующей выборки.  
  
## <a name="see-also"></a>См. также  
 [Выборка строк](../../oledb/ole-db-rowsets/fetching-rows.md)  
  
  
