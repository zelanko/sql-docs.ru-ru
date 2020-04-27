---
title: Сравнимость для IRowsetFind | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- IRowsetFind comparability [ODBC]
ms.assetid: 7d148b56-9bbe-4e55-b31f-43f115705402
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c9aa8cb118a84bca1d37bdd409055b21d1d11552
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63233022"
---
# <a name="comparability-for-irowsetfind"></a>Сравнимость для IRowsetFind
  Интерфейс IRowsetFind поддерживает следующие сравнения (только для типов даты-времени).  
  
-   LT  
  
-   LE  
  
-   EQ  
  
-   GE  
  
-   GT  
  
-   NE  
  
-   IGNORE  
  
 При попытке любого другого сравнения возвращается ошибка DB_E_BADCOMPAREOP. Это согласуется со спецификацией OLE DB.  
  
## <a name="see-also"></a>См. также  
 [Улучшения функций даты и времени &#40;OLE DB&#41;](date-and-time-improvements-ole-db.md)  
  
  
