---
title: Использование метода IRow::GetColumns | Документация Майкрософт
description: Использование метода IRow::GetColumns для доступа к всех столбцов в строке
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [OLE DB Driver for SQL Server]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- GetColumns method
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: f210e06b3c1304251e52ad8fc3f3177fef5e5a10
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66803766"
---
# <a name="using-irowgetcolumns"></a>Использование метода IRow::GetColumns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Реализация интерфейса **IRow** позволяет перемещаться только вперед с последовательным доступом к столбцам. Столбцы этой строки можно получить либо полностью одним вызовом метода **IRow::GetColumns**, либо по частям, несколько раз вызывая метод **IRow::GetColumns** при доступе к нескольким столбцам строки.  
  
 Если метод **IRow::GetColumns** вызывается несколько раз, эти вызовы не должны перекрываться. Например, если первый вызов метода **IRow::GetColumns** возвращает столбцы 1, 2 и 3, то второй вызов **IRow::GetColumns** будет возвращать столбцы 4, 5 и 6. Если последующие вызовы **IRow::GetColumns** пересекаются, то флажку состояния (полю dwstatus в DBCOLUMNACCESS) присваивается значение DBSTATUS_E_UNAVAILABLE.  
  
## <a name="see-also"></a>См. также:  
 [Выборка одной строки с помощью интерфейса IRow](../../oledb/ole-db-rowsets/fetching-a-single-row-with-irow.md)  
  
  
