---
title: Повторная синхронизация строк | Документы Microsoft
description: Повторная синхронизация строк с помощью драйвера OLE DB для SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- synchronization [OLE DB]
- IRowsetResynch interface
- resynchronizing rows
- data updates [SQL Server], OLE DB
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2eab6f3a92154ca5e8c910d03fc477ad3af9d82b
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2018
---
# <a name="updating-data-in-rowsets---resynchronizing-rows"></a>Обновление данных в наборах строк - повторная синхронизация строк
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер OLE DB для SQL Server поддерживает **IRowsetResynch** на [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] курсора поддерживается только наборы строк. **IRowsetResynch** недоступен по требованию. Пользователь должен запросить этот интерфейс перед открытием набора строк.  
  
## <a name="see-also"></a>См. также:  
 [Обновление данных в наборах строк](../../oledb/ole-db-rowsets/updating-data-in-rowsets.md)  
  
  
