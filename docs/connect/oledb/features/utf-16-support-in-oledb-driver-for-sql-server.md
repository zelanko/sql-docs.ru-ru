---
title: Поддержка UTF-16 в драйвер OLE DB для SQL Server | Документы Microsoft
description: Поддержка UTF-16 в драйвер OLE DB для SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: f88dea7bbc4fbd2ea6307647e1cbce47b07a0558
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="utf-16-support-in-ole-db-driver-for-sql-server"></a>Поддержка UTF-16 в драйвер OLE DB для SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Начиная с версии [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], если при привязке результата столбца или выходного параметра указывается буфер фиксированной длины и **wchar** символ, записываемый в буфер перед завершающим символом, является старшим символом-заместителем кодовую точку суррогатная пара и если следующего **wchar** символ является младшим символом-заместителем кодовая точка, драйвер OLE DB для SQL Server не добавит в буфер старший символ-заместитель кодовую точку.  
  
## <a name="see-also"></a>См. также  
 [Возможности драйвера OLE DB для SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)   
  
  
