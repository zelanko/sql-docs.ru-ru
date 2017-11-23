---
title: "Обновление данных в наборах строк | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- rowsets [OLE DB], updating data
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, updating data
- SQL Server Native Client OLE DB provider, data updates
- data updates [SQL Server], OLE DB
ms.assetid: 37769b1c-c480-419a-8c54-5cc420bf73db
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5da205c0b57c698cbed9c386cf0bcc9710cd4eaa
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="updating-data-in-rowsets"></a>Обновление данных в наборах строк
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Обновления поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данных, если потребитель обновляет изменяемый набор строк, который содержит данные. Изменяемый набор строк создается в том случае, если потребитель запрашивает поддержку либо для **IRowsetChange** или **IRowsetUpdate** интерфейса.  
  
 Все [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использовать изменяемые поставщик наборов строк OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] курсоров для поддержки набора строк. Свойство DBPROP_LOCKMODE набора строк изменяет поведение управления параллелизмом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в курсорах, а также определяет поведение выборки строки из набора строк и создание ошибок целостности данных в наборах строк, которые можно обновлять.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента поддерживает синхронизацию строк до или после обновления.  
  
> [!NOTE]  
>  Интерфейс IRowChange::SetColumns может установить значения одного или более именованных столбцов объекта-строки.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Обновление данных в курсорах SQL Server](../../relational-databases/native-client-ole-db-rowsets/updating-data-in-sql-server-cursors.md)  
  
-   [Повторная синхронизация строк](../../relational-databases/native-client-ole-db-rowsets/updating-data-in-rowsets-resynchronizing-rows.md)  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
