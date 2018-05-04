---
title: С помощью IRow::GetColumns | Документы Microsoft
description: Использование метода IRow::GetColumns для доступа к всех столбцов в строке
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
- IRow interface
- single row fetching [OLE DB Driver for SQL Server]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- GetColumns method
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: fc82a06567e1058a1ee0f7745db153d8af96d90e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="using-irowgetcolumns"></a>Использование метода IRow::GetColumns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **IRow** реализация позволяет последовательным последовательный доступ к столбцам. Можно получить либо все столбцы в строке с помощью одного вызова **IRow::GetColumns** или вызвать **IRow::GetColumns** несколько раз, каждый раз при доступе к несколько столбцов в строке.  
  
 Несколько вызовов **IRow::GetColumns** не должны перекрываться. Например, если первый вызов **IRow::GetColumns** получает столбцы 1, 2 и 3, второй вызов для **IRow::GetColumns** должен получать столбцы 4, 5 и 6. Если последующие вызовы **IRow::GetColumns** перекрываются, флаг состояния (полю dwstatus в DBCOLUMNACCESS) присваивается значение DBSTATUS_E_UNAVAILABLE.  
  
## <a name="see-also"></a>См. также  
 [Выборка одной строки при помощи интерфейса IRow](../../oledb/ole-db-rowsets/fetching-a-single-row-with-irow.md)  
  
  
