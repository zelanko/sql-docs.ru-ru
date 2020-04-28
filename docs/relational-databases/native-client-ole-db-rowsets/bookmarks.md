---
title: Закладки | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bookmarks [OLE DB]
- SQL Server Native Client OLE DB provider, bookmarks
- rowsets [OLE DB], bookmarks
- OLE DB rowsets, bookmarks
ms.assetid: 7d9076f2-bf9c-452e-b816-70371a0c1644
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4fffab606cd1b1e2a227e3534bfe837987300efe
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305655"
---
# <a name="bookmarks"></a>Закладки
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Закладки позволяют потребителю быстро вернуться к конкретной строке. Потребитель может получать доступ к произвольной строке с помощью закладок. Столбец закладок является столбцом номер 0 в наборе строк. Потребитель присваивает полю dwFlag в структуре привязки значение DBCOLUMNSINFO_ISBOOKMARK, чтобы указать, что столбец используется как закладка. Пользователь также присваивает свойству набора строк DBPROP_BOOKMARKS значение VARIANT_TRUE. Это позволяет столбцу с номером 0 присутствовать в наборе строк.  Затем для получения строк, начиная со строки, заданной отступом от закладки, используется метод **IRowsetLocate::GetRowsAt**.  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
