---
title: "Счетчики производительности XTP (выполняющаяся в памяти OLTP) для SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "04/06/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fe3cbaf4-65f4-44c5-acc6-7b735cda0c5d
caps.latest.revision: 17
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 17
---
# Счетчики производительности XTP (выполняющаяся в памяти OLTP) для SQL Server
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет объекты и счетчики, которые могут использоваться системным монитором для отслеживания активности In-Memory OLTP. Объекты и счетчики являются общими для всех экземпляров данной версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на компьютере, начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
 В прошлом имена объектов и счетчиков содержали *XTP*, как в **Курсоры XTP**. Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] имена составляются по следующей схеме:  
  
-   **Курсоры XTP** **SQL Server** *\<версия>*  
  
 Вместо *\<версия>* подставляется значение типа 2016.  
  
##  <a name="SQLServerPOs"></a> Объекты производительности XTP в SQL Server  
 В следующей таблице приводятся описания счетчиков производительности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Объект производительности|Описание|  
|------------------------|-----------------|  
|[Курсоры XTP SQL Server](../../relational-databases/performance-monitor/sql-server-xtp-cursors.md)|Объект производительности XTP Cursors в SQL Server содержит счетчики, относящиеся к внутренним курсорам механизма In-Memory OLTP. Курсоры — это низкоуровневые строительные блоки, используемые механизмом In-Memory OLTP для обработки запросов [!INCLUDE[tsql](../../includes/tsql-md.md)]. Обычно вы не имеете прямого контроля над ними как таковыми.|  
|[Базы данных XTP SQL Server](../../relational-databases/performance-monitor/sql-server-xtp-databases.md)|Объект производительности баз данных XTP в SQL Server содержит счетчики, относящиеся к базе данных для выполняющейся в памяти OLTP.|  
|[SQL Server XTP Garbage Collection](../../relational-databases/performance-monitor/sql-server-xtp-garbage-collection.md)|Объект производительности XTP Garbage Collection в SQL Server содержит счетчики, относящиеся к механизму сборщика мусора XTP в In-Memory OLTP.|  
|[Регулятор ввода-вывода XTP в SQL Server 2016](../../relational-databases/performance-monitor/sql-server-xtp-io-governor.md)|Объект производительности регулятора ввода-вывода XTP в SQL Server содержит счетчики, относящиеся к регулятору скорости ввода-вывода для выполняющейся в памяти OLTP.|
|[SQL Server XTP Phantom Processor](../../relational-databases/performance-monitor/sql-server-xtp-phantom-processor.md)|Объект производительности SQL Server XTP Phantom Processor содержит счетчики, относящиеся к подсистеме обработки фантомов механизма In-Memory OLTP. Этот компонент отвечает за обнаружение фантомных строк в транзакциях, выполняемых на уровне изоляции SERIALIZABLE.|  
|[Хранилище XTP SQL Server](../../relational-databases/performance-monitor/sql-server-xtp-storage.md)|Объект производительности хранилища XTP в SQL Server содержит счетчики, относящиеся к хранилищу In-Memory OLTP в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Журнал XTP-транзакций SQL Server](../../relational-databases/performance-monitor/sql-server-xtp-transaction-log.md)|Объект производительности транзакций XTP SQL Server содержит счетчики, связанные с журналом транзакций In-Memory OLTP в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[XTP-транзакции SQL Server](../../relational-databases/performance-monitor/sql-server-xtp-transactions.md)|Объект производительности транзакций XTP в SQL Server содержит счетчики, относящиеся к транзакциям модуля In-Memory OLTP в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
  