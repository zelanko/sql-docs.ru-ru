---
title: Использование метода IRow::GetColumns | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [SQL Server Native Client]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- GetColumns method
ms.assetid: 1f5d2e03-e6fe-4ea1-b71d-55d02b5d59ae
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 21046f1ab8c25a9f929f8e6cf95281e74c157ae6
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37430053"
---
# <a name="using-irowgetcolumns"></a>Использование метода IRow::GetColumns
  **IRow** реализация предоставляет однопроходный последовательный доступ к столбцам. Все столбцы в строке с помощью одного вызова можно получить либо **IRow::GetColumns** или вызвать **IRow::GetColumns** несколько раз, каждый раз, что доступ к несколько столбцов в строке.  
  
 Несколько вызовов **IRow::GetColumns** не должны перекрываться. Например, если первый вызов **IRow::GetColumns** получает столбцы 1, 2 и 3, второй вызов к **IRow::GetColumns** следует вызывать для столбцов, 4, 5 и 6. Если последующие вызовы **IRow::GetColumns** перекрываются флаг состояния (полю dwstatus в DBCOLUMNACCESS) присваивается значение DBSTATUS_E_UNAVAILABLE.  
  
## <a name="see-also"></a>См. также  
 [Выборка одной строки с помощью интерфейса IRow](fetching-a-single-row-with-irow.md)  
  
  
