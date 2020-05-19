---
title: Поддержка UTF-16 в SQL Server Native Client 11,0 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: f2520424-8ef4-409f-8147-d83da5076e96
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b28d869a6e33969550751158e321ec24062bf6ac
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82707148"
---
# <a name="utf-16-support-in-sql-server-native-client-110"></a>Поддержка UTF-16 в собственном клиенте SQL Server версии 11.0
  Начиная с [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] , при предоставлении буфера фиксированной длины при привязке результата или выходного параметра столбца, а также если `wchar` символ, записанный в буфер перед завершающим символом, является старшим замещающим кодовым точкой суррогатной пары, а следующий символ является младшим кодовым точкой-заместителем `wchar` , [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственный клиент не будет добавлять старшую кодовую точку в буфер.  
  
## <a name="see-also"></a>См. также  
 [Компоненты собственного клиента SQL Server](sql-server-native-client-features.md)  
  
  
