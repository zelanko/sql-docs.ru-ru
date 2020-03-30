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
ms.openlocfilehash: 0ae8a83de24341b7f9672296a9bfe713ae882dfe
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67988758"
---
# <a name="utf-16-support-in-ole-db-driver-for-sql-server"></a>Поддержка UTF-16 в драйвере OLE DB для SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Начиная с [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], если при привязке результата столбца или выходного параметра указывается буфер фиксированной длины, а символ **wchar**, записываемый в буфер перед завершающим символом, является старшей кодовой точкой суррогатной пары, а следующий символ **wchar** является младшей кодовой точкой суррогатной пары, то драйвер OLE DB для SQL Server не добавит в буфер старшую кодовую точку суррогатной пары.  
  
## <a name="see-also"></a>См. также:  
 [Возможности драйвера OLE DB для SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)   
  
  
