---
title: Поддержка UTF-16 в драйвере OLE DB для SQL Server | Документация Майкрософт
description: Поддержка UTF-16 в драйвере OLE DB для SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 71b4298fa3e843e6e9a15dce638f2f068fe5d4b3
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86007245"
---
# <a name="utf-16-support-in-ole-db-driver-for-sql-server"></a>Поддержка UTF-16 в драйвере OLE DB для SQL Server
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Начиная с [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], если при привязке результата столбца или выходного параметра указывается буфер фиксированной длины, а символ **wchar**, записываемый в буфер перед завершающим символом, является старшей кодовой точкой суррогатной пары, а следующий символ **wchar** является младшей кодовой точкой суррогатной пары, то драйвер OLE DB для SQL Server не добавит в буфер старшую кодовую точку суррогатной пары.  
  
## <a name="see-also"></a>См. также:  
 [Возможности драйвера OLE DB для SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)   
  
  
