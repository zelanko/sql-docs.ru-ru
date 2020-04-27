---
title: Обновление данных в наборах строк | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: f68e4f2be641d6c6aeaf8bbbfcc8cad81ab1a39a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62938685"
---
# <a name="updating-data-in-rowsets"></a>Обновление данных в наборах строк
  Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента обновляет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данные, когда потребитель обновляет изменяемый набор строк, содержащий эти данные. Набор строк, который можно изменять, создается, если потребитель запрашивает поддержку либо для интерфейса **IRowsetChange**, либо для интерфейса **IRowsetUpdate**.  
  
 Все [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственные наборы строк, изменяемые поставщиком OLE DB клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , используют курсоры для поддержки набора строк. Свойство DBPROP_LOCKMODE набора строк изменяет поведение управления параллелизмом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в курсорах, а также определяет поведение выборки строки из набора строк и создание ошибок целостности данных в наборах строк, которые можно обновлять.  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента поддерживает синхронизацию строк до или после обновления.  
  
> [!NOTE]  
>  Интерфейс IRowChange::SetColumns может установить значения одного или более именованных столбцов объекта-строки.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Обновление данных в курсорах SQL Server](updating-data-in-sql-server-cursors.md)  
  
-   [Повторная синхронизация строк](updating-data-in-rowsets-resynchronizing-rows.md)  
  
## <a name="see-also"></a>См. также  
 [Наборы строк](rowsets.md)  
  
  
