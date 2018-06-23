---
title: Поддержка UTF-16 в собственном клиенте SQL Server 11.0 | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: f2520424-8ef4-409f-8147-d83da5076e96
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 66198f42676944967a2d655f14a27470922fd318
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191424"
---
# <a name="utf-16-support-in-sql-server-native-client-110"></a>Поддержка UTF-16 в собственном клиенте SQL Server версии 11.0
  Начиная с версии [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], если при привязке результата столбца или выходного параметра указывается буфер фиксированной длины и `wchar` символ, записываемый в буфер перед завершающим символом, является старшим суррогатной пары, а также если Следующий `wchar` символ является младшим символом-заместителем кодом, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client не будет добавлять старшим буфера.  
  
## <a name="see-also"></a>См. также  
 [Компоненты SQL Server Native Client](sql-server-native-client-features.md)  
  
  