---
title: Поддержка UTF-16 в SQL Server Native Client 11,0 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: f2520424-8ef4-409f-8147-d83da5076e96
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 415cb2fe8a3295770cfc8bd2d5c6e56750adb6d9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63205122"
---
# <a name="utf-16-support-in-sql-server-native-client-110"></a>Поддержка UTF-16 в собственном клиенте SQL Server версии 11.0
  Начиная с [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], при предоставлении буфера фиксированной длины при привязке результата или выходного параметра столбца, а также `wchar` если символ, записанный в буфер перед завершающим символом, является старшим замещающим кодовым точкой суррогатной пары, а `wchar` следующий символ является младшим кодовым точкой [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -заместителем, собственный клиент не будет добавлять старшую кодовую точку в буфер.  
  
## <a name="see-also"></a>См. также  
 [Компоненты собственного клиента SQL Server](sql-server-native-client-features.md)  
  
  
