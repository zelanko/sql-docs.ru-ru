---
title: Счетчики производительности XTP (In-Memory OLTP) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: fe3cbaf4-65f4-44c5-acc6-7b735cda0c5d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 2362807e8e033fbc55e75a08d9dec80bf3782e03
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48084054"
---
# <a name="xtp-in-memory-oltp-performance-counters"></a>Счетчики производительности XTP (In-Memory OLTP)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет объекты и счетчики, которые могут использоваться системным монитором для отслеживания активности In-Memory OLTP.  
  
##  <a name="SQLServerPOs"></a> Объекты производительности XTP (In-Memory OLTP)  
 В следующей таблице описаны объекты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Объект производительности|Описание|  
|------------------------|-----------------|  
|[Курсоры XTP](../cursors.md)|Объект производительности XTP Cursors содержит счетчики, относящиеся к внутренним курсорам механизма XTP. Курсоры — низкоуровневые строительные блоки, используемые механизмом XTP для обработки запросов [!INCLUDE[tsql](../../includes/tsql-md.md)] . Обычно вы не имеете прямого контроля над ними как таковыми.|  
|[Сборка мусора XTP](sql-server-xtp-garbage-collection.md)|Объект производительности XTP Garbage Collection содержит счетчики, относящиеся к механизму сборщика мусора XTP.|  
|[Обработчик фантомных строк XTP](sql-server-xtp-phantom-processor.md)|Объект производительности XTP Phantom Processor содержит счетчики, относящиеся к подсистеме обработки фантомов механизма XTP. Этот компонент отвечает за обнаружение фантомных строк в транзакциях, выполняемых на уровне изоляции SERIALIZABLE.|  
|[Хранилище XTP](sql-server-xtp-storage.md)|Объект производительности XTP Storage содержит счетчики, относящиеся к хранилищу XTP в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Журнал транзакций XTP](sql-server-xtp-transaction-log.md)|Объект производительности XTP Transaction Log содержит счетчики, относящиеся к ведению журнала XTP в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Транзакции XTP](sql-server-xtp-transactions.md)|Объект производительности XTP Transactions содержит счетчики, относящиеся к транзакциям механизма XTP в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
  
