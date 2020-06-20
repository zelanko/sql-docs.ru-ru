---
title: Счетчики производительности XTP (выполняющаяся в памяти OLTP) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: fe3cbaf4-65f4-44c5-acc6-7b735cda0c5d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4363a526ada3694e92d18cac0d7abe8a26f6a92f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85016936"
---
# <a name="xtp-in-memory-oltp-performance-counters"></a>Счетчики производительности XTP (In-Memory OLTP)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет объекты и счетчики, которые могут использоваться системным монитором для отслеживания активности In-Memory OLTP.  
  
##  <a name="xtp-in-memory-oltp-performance-objects"></a><a name="SQLServerPOs"></a>Объекты производительности XTP (выполняющаяся в памяти OLTP)  
 В следующей таблице описаны объекты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Объект производительности|Описание|  
|------------------------|-----------------|  
|[Курсоры XTP](../cursors.md)|Объект производительности XTP Cursors содержит счетчики, относящиеся к внутренним курсорам механизма XTP. Курсоры — низкоуровневые строительные блоки, используемые механизмом XTP для обработки запросов [!INCLUDE[tsql](../../includes/tsql-md.md)] . Обычно вы не имеете прямого контроля над ними как таковыми.|  
|[Сборка мусора XTP](sql-server-xtp-garbage-collection.md)|Объект производительности XTP Garbage Collection содержит счетчики, относящиеся к механизму сборщика мусора XTP.|  
|[XTP Phantom Processor](sql-server-xtp-phantom-processor.md)|Объект производительности XTP Phantom Processor содержит счетчики, относящиеся к подсистеме обработки фантомов механизма XTP. Этот компонент отвечает за обнаружение фантомных строк в транзакциях, выполняемых на уровне изоляции SERIALIZABLE.|  
|[Хранилище XTP](sql-server-xtp-storage.md)|Объект производительности XTP Storage содержит счетчики, относящиеся к хранилищу XTP в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Журнал транзакций XTP](sql-server-xtp-transaction-log.md)|Объект производительности XTP Transaction Log содержит счетчики, относящиеся к ведению журнала XTP в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Транзакции XTP](sql-server-xtp-transactions.md)|Объект производительности XTP Transactions содержит счетчики, относящиеся к транзакциям механизма XTP в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
  
