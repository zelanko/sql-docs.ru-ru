---
title: Выборка одной строки при помощи интерфейса IRow | Документы Microsoft
description: Выборка одной строки, с помощью интерфейса IRow драйвера OLE DB для SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
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
- OLE DB Driver for SQL Server, fetching
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0f34071fd7033c381cfc63fb1bb1937ec718ef19
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="fetching-a-single-row-with-irow"></a>Выборка одной строки при помощи интерфейса IRow
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **IRow** интерфейса реализации в драйвер OLE DB для SQL Server была упрощена с целью повышения производительности. **IRow** обеспечивает прямой доступ к столбцам одной строки объекта. Если заранее известно, что результат выполнения команды выведет одну единственную строку **IRow** даст возможность получить столбцы этой строки. Если результирующий набор содержит несколько строк, **IRow** будут представлены только в первой строке.  
  
 **IRow** реализация позволяет перемещаться строки. Каждый столбец в строке осуществляется только один раз с одним исключением: столбец может быть доступен один раз для выяснения его размера и еще раз для выборки данных.  
  
> [!NOTE]  
>  **IRow::Open** поддерживает только типа DBGUID_STREAM или DBGUID_NULL объектов должен быть открыт.  
  
 Для получения объекта строки с помощью **ICommand::Execute** метода, должны быть переданы IID_IRow. **IMultipleResults** интерфейс должен использоваться для обработки нескольких результирующих наборов. **IMultipleResults** поддерживает **IRow** и **IRowset**. **IRowset** используется для массовых операций.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Использование метода IRow::GetColumns](../../oledb/ole-db-rowsets/using-irow-getcolumns.md)   
  
## <a name="see-also"></a>См. также  
 [Наборы строк](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
