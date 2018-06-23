---
title: Счетчики производительности XTP (In-Memory OLTP) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe3cbaf4-65f4-44c5-acc6-7b735cda0c5d
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b12c482300ff8908236d1eda9d0e030df4b2e356
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188670"
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
  
  