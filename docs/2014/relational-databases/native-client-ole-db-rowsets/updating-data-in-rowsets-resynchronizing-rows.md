---
title: Повторная синхронизация строк | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- synchronization [OLE DB]
- IRowsetResynch interface
- resynchronizing rows
- data updates [SQL Server], OLE DB
ms.assetid: d2d30505-a878-4aa9-b821-53d8118a45a5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7b041dc07afb30fff0c03d96fec9cd8a5d62f965
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63229013"
---
# <a name="resynchronizing-rows"></a>Повторная синхронизация строк
  Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента поддерживает **интерфейс irowsetresynch** только для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] наборов строк, поддерживаемых курсорами. Интерфейс **IRowsetResynch** не предоставляется по требованию. Пользователь должен запросить этот интерфейс перед открытием набора строк.  
  
## <a name="see-also"></a>См. также  
 [Обновление данных в наборах строк](updating-data-in-rowsets.md)  
  
  
