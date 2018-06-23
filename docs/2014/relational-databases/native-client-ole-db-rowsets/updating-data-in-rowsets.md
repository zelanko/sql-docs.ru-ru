---
title: Обновление данных в наборах строк | Документы Microsoft
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a76d76df980297fd0e7b38cc0d7ec65e310c9e46
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188998"
---
# <a name="updating-data-in-rowsets"></a>Обновление данных в наборах строк
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Обновления поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данных, если потребитель обновляет изменяемый набор строк, который содержит данные. Изменяемый набор строк создается в том случае, если потребитель запрашивает поддержку либо для **IRowsetChange** или **IRowsetUpdate** интерфейса.  
  
 Все [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использовать изменяемые поставщик наборов строк OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] курсоров для поддержки набора строк. Свойство DBPROP_LOCKMODE набора строк изменяет поведение управления параллелизмом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в курсорах, а также определяет поведение выборки строки из набора строк и создание ошибок целостности данных в наборах строк, которые можно обновлять.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента поддерживает синхронизацию строк до или после обновления.  
  
> [!NOTE]  
>  Интерфейс IRowChange::SetColumns может установить значения одного или более именованных столбцов объекта-строки.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Обновление данных в курсорах SQL Server](updating-data-in-sql-server-cursors.md)  
  
-   [Повторная синхронизация строк](updating-data-in-rowsets-resynchronizing-rows.md)  
  
## <a name="see-also"></a>См. также  
 [Наборы строк](rowsets.md)  
  
  