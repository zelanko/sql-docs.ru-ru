---
title: Закладки | Документы Microsoft
description: Закладки в драйвер OLE DB для SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bookmarks [OLE DB]
- OLE DB Driver for SQL Server, bookmarks
- rowsets [OLE DB], bookmarks
- OLE DB rowsets, bookmarks
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 3e7c40b7d81be7c94c6e99c777006bfda7355f25
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35305633"
---
# <a name="bookmarks"></a>Закладки
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Закладки позволяют потребителю быстро вернуться к конкретной строке. Потребитель может получать доступ к произвольной строке с помощью закладок. Столбец закладок является столбцом номер 0 в наборе строк. Потребитель присваивает полю dwFlag в структуре привязки значение DBCOLUMNSINFO_ISBOOKMARK, чтобы указать, что столбец используется как закладка. Пользователь также присваивает свойству набора строк DBPROP_BOOKMARKS значение VARIANT_TRUE. Это позволяет столбцу с номером 0 присутствовать в наборе строк.  **IRowsetLocate::GetRowsAt** метод используется для выборки строк, начиная со строки, указанной в качестве смещения относительно закладки.  
  
## <a name="see-also"></a>См. также  
 [Наборы строк](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
