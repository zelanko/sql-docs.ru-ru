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
ms.openlocfilehash: af8581071400db888fb508b88f8e8ae93bc71f70
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85038997"
---
# <a name="utf-16-support-in-sql-server-native-client-110"></a>Поддержка UTF-16 в собственном клиенте SQL Server версии 11.0
  Начиная с [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] , при предоставлении буфера фиксированной длины при привязке результата или выходного параметра столбца, а также если `wchar` символ, записанный в буфер перед завершающим символом, является старшим замещающим кодовым точкой суррогатной пары, а следующий символ является младшим кодовым точкой-заместителем `wchar` , [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственный клиент не будет добавлять старшую кодовую точку в буфер.  
  
## <a name="see-also"></a>См. также:  
 [Компоненты собственного клиента SQL Server](sql-server-native-client-features.md)  
  
  
