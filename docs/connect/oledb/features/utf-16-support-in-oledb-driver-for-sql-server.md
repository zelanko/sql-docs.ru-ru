---
title: Поддержка UTF-16 в драйвер OLE DB для SQL Server | Документы Microsoft
description: Поддержка UTF-16 в драйвер OLE DB для SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: bcb7393315063102315fdf5062bdfa05ee07282d
ms.sourcegitcommit: 354ed9c8fac7014adb0d752518a91d8c86cdce81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/14/2018
ms.locfileid: "35611629"
---
# <a name="utf-16-support-in-ole-db-driver-for-sql-server"></a>Поддержка UTF-16 в драйвер OLE DB для SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Начиная с версии [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], если при привязке результата столбца или выходного параметра указывается буфер фиксированной длины и **wchar** символ, записываемый в буфер перед завершающим символом, является старшим символом-заместителем кодовую точку суррогатная пара и если следующего **wchar** символ является младшим символом-заместителем кодовая точка, драйвер OLE DB для SQL Server не добавит в буфер старший символ-заместитель кодовую точку.  
  
## <a name="see-also"></a>См. также  
 [Возможности драйвера OLE DB для SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)   
  
  
