---
title: Using IRow::GetColumns (драйвер OLE DB)
description: Узнайте, как использовать IRow::GetColumns для доступа ко всем столбцам в строке в OLE DB Driver for SQL Server. IRow позволяет осуществлять последовательный однонаправленный доступ к столбцам.
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 60ded2ad36346bcb05d75add252f0357c48398e7
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/25/2020
ms.locfileid: "88859938"
---
# <a name="using-irowgetcolumns"></a>Использование метода IRow::GetColumns
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Реализация интерфейса **IRow** позволяет перемещаться только вперед с последовательным доступом к столбцам. Столбцы этой строки можно получить либо полностью одним вызовом метода **IRow::GetColumns**, либо по частям, несколько раз вызывая метод **IRow::GetColumns** при доступе к нескольким столбцам строки.  
  
 Если метод **IRow::GetColumns** вызывается несколько раз, эти вызовы не должны перекрываться. Например, если первый вызов метода **IRow::GetColumns** возвращает столбцы 1, 2 и 3, то второй вызов **IRow::GetColumns** будет возвращать столбцы 4, 5 и 6. Если последующие вызовы **IRow::GetColumns** пересекаются, то флажку состояния (полю dwstatus в DBCOLUMNACCESS) присваивается значение DBSTATUS_E_UNAVAILABLE.  
  
## <a name="see-also"></a>См. также:  
 [Выборка одной строки с помощью интерфейса IRow](../../oledb/ole-db-rowsets/fetching-a-single-row-with-irow.md)  
  
  
