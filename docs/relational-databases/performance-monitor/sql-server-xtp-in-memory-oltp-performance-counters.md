---
title: "Счетчики производительности XTP (выполняющаяся в памяти OLTP) для SQL Server | Документация Майкрософт"
ms.custom: 
ms.date: 04/06/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe3cbaf4-65f4-44c5-acc6-7b735cda0c5d
caps.latest.revision: 17
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c4fb8ea7bd2ca4a09f0758c175b9eb2781f2ed5b
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="sql-server-xtp-in-memory-oltp-performance-counters"></a>Счетчики производительности XTP (выполняющаяся в памяти OLTP) для SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет объекты и счетчики, которые могут использоваться системным монитором для отслеживания активности In-Memory OLTP. Объекты и счетчики являются общими для всех экземпляров данной версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на компьютере, начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
 В прошлом имена объектов и счетчиков содержали *XTP*, как в **Курсоры XTP**. Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]имена составляются по следующей схеме:  
  
-   **SQL Server** *\<версия>* **XTP Cursors**  
  
 Где *\<версия>* имеет значение вида "2016".  
  
##  <a name="SQLServerPOs"></a> Объекты производительности XTP в SQL Server  
 В следующей таблице приводятся описания счетчиков производительности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Объект производительности|Описание|  
|------------------------|-----------------|  
|[Курсоры XTP SQL Server](../../relational-databases/performance-monitor/sql-server-xtp-cursors.md)|Объект производительности XTP Cursors в SQL Server содержит счетчики, относящиеся к внутренним курсорам механизма In-Memory OLTP. Курсоры — это низкоуровневые строительные блоки, используемые механизмом In-Memory OLTP для обработки запросов [!INCLUDE[tsql](../../includes/tsql-md.md)] . Обычно вы не имеете прямого контроля над ними как таковыми.|  
|[Базы данных XTP SQL Server](../../relational-databases/performance-monitor/sql-server-xtp-databases.md)|Объект производительности баз данных XTP в SQL Server содержит счетчики, относящиеся к базе данных для выполняющейся в памяти OLTP.|  
|[SQL Server XTP Garbage Collection](../../relational-databases/performance-monitor/sql-server-xtp-garbage-collection.md)|Объект производительности XTP Garbage Collection в SQL Server содержит счетчики, относящиеся к механизму сборщика мусора XTP в In-Memory OLTP.|  
|[Регулятор ввода-вывода XTP в SQL Server 2016](../../relational-databases/performance-monitor/sql-server-xtp-io-governor.md)|Объект производительности регулятора ввода-вывода XTP в SQL Server содержит счетчики, относящиеся к регулятору скорости ввода-вывода для выполняющейся в памяти OLTP.|
|[SQL Server XTP Phantom Processor](../../relational-databases/performance-monitor/sql-server-xtp-phantom-processor.md)|Объект производительности SQL Server XTP Phantom Processor содержит счетчики, относящиеся к подсистеме обработки фантомов механизма In-Memory OLTP. Этот компонент отвечает за обнаружение фантомных строк в транзакциях, выполняемых на уровне изоляции SERIALIZABLE.|  
|[Хранилище XTP SQL Server](../../relational-databases/performance-monitor/sql-server-xtp-storage.md)|Объект производительности хранилища XTP в SQL Server содержит счетчики, относящиеся к хранилищу In-Memory OLTP в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Журнал XTP-транзакций SQL Server](../../relational-databases/performance-monitor/sql-server-xtp-transaction-log.md)|Объект производительности транзакций XTP SQL Server содержит счетчики, связанные с журналом транзакций In-Memory OLTP в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[XTP-транзакции SQL Server](../../relational-databases/performance-monitor/sql-server-xtp-transactions.md)|Объект производительности транзакций XTP в SQL Server содержит счетчики, относящиеся к транзакциям модуля In-Memory OLTP в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
  

