---
title: Выборка одной строки при помощи интерфейса IRow | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
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
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: eef27a6cbd6ee793cd227c2cf6e6570e1d04b004
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189976"
---
# <a name="fetching-a-single-row-with-irow"></a>Выборка одной строки при помощи интерфейса IRow
  **IRow** реализацию в интерфейса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента была упрощена с целью повышения производительности. **IRow** обеспечивает прямой доступ к столбцам одной строки объекта. Если заранее известно, что результат выполнения команды выведет одну единственную строку **IRow** даст возможность получить столбцы этой строки. Если результирующий набор содержит несколько строк, **IRow** будут представлены только в первой строке.  
  
 **IRow** реализация позволяет перемещаться строки. Каждый столбец в строке осуществляется только один раз с одним исключением: столбец может быть доступен один раз для выяснения его размера и еще раз для выборки данных.  
  
> [!NOTE]  
>  **IRow::Open** поддерживает только типа DBGUID_STREAM или DBGUID_NULL объектов должен быть открыт.  
  
 Для получения объекта строки с помощью **ICommand::Execute** метода, должны быть переданы IID_IRow. **IMultipleResults** интерфейс должен использоваться для обработки нескольких результирующих наборов. **IMultipleResults** поддерживает **IRow** и **IRowset**. **IRowset** используется для массовых операций.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Использование метода IRow::GetColumns](using-irow-getcolumns.md)  
  
-   [Выборка данных большого двоичного объекта при помощи интерфейса IRow](../../database-engine/dev-guide/fetching-blob-data-using-irow.md)  
  
## <a name="see-also"></a>См. также  
 [Наборы строк](rowsets.md)  
  
  