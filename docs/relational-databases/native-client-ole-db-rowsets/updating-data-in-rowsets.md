---
title: Обновление данных в наборах строк | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- rowsets [OLE DB], updating data
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, updating data
- SQL Server Native Client OLE DB provider, data updates
- data updates [SQL Server], OLE DB
ms.assetid: 37769b1c-c480-419a-8c54-5cc420bf73db
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6bad3eb55de87c4aa376abc4617c31a63eeffc0b
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73761686"
---
# <a name="updating-data-in-rowsets"></a>Обновление данных в наборах строк
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB обновляет данные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], когда потребитель обновляет изменяемый набор строк, содержащий эти данные. Набор строк, который можно изменять, создается, если потребитель запрашивает поддержку либо для интерфейса **IRowsetChange**, либо для интерфейса **IRowsetUpdate**.  
  
 Все [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственные клиентские OLE DBные наборы строк, изменяемые поставщиком, используют [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] курсоры для поддержки набора строк. Свойство DBPROP_LOCKMODE набора строк изменяет поведение управления параллелизмом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в курсорах, а также определяет поведение выборки строки из набора строк и создание ошибок целостности данных в наборах строк, которые можно обновлять.  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB поддерживает синхронизацию строк до или после обновления.  
  
> [!NOTE]  
>  Интерфейс IRowChange::SetColumns может установить значения одного или более именованных столбцов объекта-строки.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Обновление данных в курсорах SQL Server](../../relational-databases/native-client-ole-db-rowsets/updating-data-in-sql-server-cursors.md)  
  
-   [Повторная синхронизация строк](../../relational-databases/native-client-ole-db-rowsets/updating-data-in-rowsets-resynchronizing-rows.md)  
  
## <a name="see-also"></a>См. также раздел  
 [Наборы строк](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
