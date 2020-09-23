---
title: Поддержка UTF-16 в драйвере OLE DB для SQL Server | Документация Майкрософт
description: Сведения о поддержке UTF-16 в OLE DB Driver for SQL Server и добавлении старшей кодовой точки суррогатной пары в буфер.
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f00b9f0ac10c812743cac0bf4222fd2136710b42
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/25/2020
ms.locfileid: "88861784"
---
# <a name="utf-16-support-in-ole-db-driver-for-sql-server"></a>Поддержка UTF-16 в драйвере OLE DB для SQL Server
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Начиная с [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], если при привязке результата столбца или выходного параметра указывается буфер фиксированной длины, а символ **wchar**, записываемый в буфер перед завершающим символом, является старшей кодовой точкой суррогатной пары, а следующий символ **wchar** является младшей кодовой точкой суррогатной пары, то драйвер OLE DB для SQL Server не добавит в буфер старшую кодовую точку суррогатной пары.  
  
## <a name="see-also"></a>См. также:  
 [Возможности драйвера OLE DB для SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)   
  
  
