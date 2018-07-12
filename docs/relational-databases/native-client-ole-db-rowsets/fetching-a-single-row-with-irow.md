---
title: Выборка одной строки при помощи интерфейса IRow | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [SQL Server Native Client]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- SQL Server Native Client OLE DB provider, fetching
ms.assetid: 07c803ca-299a-42c5-ba02-360b9631d15f
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: ab4a6e50ce20b1bceddfb639e5780938f3687639
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37412003"
---
# <a name="fetching-a-single-row-with-irow"></a>Выборка одной строки при помощи интерфейса IRow
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **IRow** реализацию в интерфейса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента была упрощена с целью повышения производительности. **IRow** обеспечивает прямой доступ к столбцам одной строки объекта. Если заранее известно, что в результате выполнения команды будет создается ровно одна строка, **IRow** даст возможность получить столбцы этой строки. Если результирующий набор включает несколько строк, **IRow** будет предоставлять только первую строку.  
  
 **IRow** реализация позволяет перемещаться строки. Каждый столбец в строке осуществляется только один раз с одним исключением: столбец может осуществляться один раз для выяснения его размера и повторно для получения данных.  
  
> [!NOTE]  
>  **IRow::Open** поддерживает только DBGUID_STREAM или DBGUID_NULL тип объектов, которые должны быть открыты.  
  
 Для получения объекта строки с помощью **ICommand::Execute** метода, должен быть передан IID_IRow. **IMultipleResults** интерфейс должен использоваться для обработки нескольких результирующих наборов. **IMultipleResults** поддерживает **IRow** и **IRowset**. **IRowset** используется для массовых операций.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Использование метода IRow::GetColumns](../../relational-databases/native-client-ole-db-rowsets/using-irow-getcolumns.md)  
  
-   [Выборка данных большого двоичного объекта при помощи интерфейса IRow](http://msdn.microsoft.com/library/badbd6ac-20aa-4891-a14f-48d38e7f30de)  
  
## <a name="see-also"></a>См. также  
 [Наборы строк](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
