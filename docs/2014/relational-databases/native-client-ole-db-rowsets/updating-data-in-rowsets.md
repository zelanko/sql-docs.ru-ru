---
title: Обновление данных в наборах строк | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- rowsets [OLE DB], updating data
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, updating data
- SQL Server Native Client OLE DB provider, data updates
- data updates [SQL Server], OLE DB
ms.assetid: 37769b1c-c480-419a-8c54-5cc420bf73db
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 34071ebd4c0f4a365d654eb858ea419383ceeaa6
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37425703"
---
# <a name="updating-data-in-rowsets"></a>Обновление данных в наборах строк
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Обновления поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данных, если потребитель обновляет изменяемый набор строк, который содержит данные. Изменяемый набор строк создается в том случае, если потребитель запрашивает поддержку либо для **IRowsetChange** или **IRowsetUpdate** интерфейс.  
  
 Все [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использовать наборы строк можно изменять, поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] курсоры для поддержки набора строк. Свойство DBPROP_LOCKMODE набора строк изменяет поведение управления параллелизмом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в курсорах, а также определяет поведение выборки строки из набора строк и создание ошибок целостности данных в наборах строк, которые можно обновлять.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента поддерживает синхронизацию строк до или после обновления.  
  
> [!NOTE]  
>  Интерфейс IRowChange::SetColumns может установить значения одного или более именованных столбцов объекта-строки.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Обновление данных в курсорах SQL Server](updating-data-in-sql-server-cursors.md)  
  
-   [Повторная синхронизация строк](updating-data-in-rowsets-resynchronizing-rows.md)  
  
## <a name="see-also"></a>См. также  
 [Наборы строк](rowsets.md)  
  
  
