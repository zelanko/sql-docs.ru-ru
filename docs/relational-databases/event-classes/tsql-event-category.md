---
title: Категория событий TSQL | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- SQL Server event classes, TSQL event category
- TSQL event category [SQL Server]
- event classes [SQL Server], TSQL event category
ms.assetid: 215f8747-64b5-4bf3-9845-d476b10cda3a
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3e79d7b85f847ef0410d44b9247bd5bd0b00ba3b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47745912"
---
# <a name="tsql-event-category"></a>Категория событий TSQL
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Категория событий **TSQL** включает общие события TSQL.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Класс событий Exec Prepared SQL](../../relational-databases/event-classes/exec-prepared-sql-event-class.md)|Указывает, что SqlClient, ODBC, OLE DB или DB-Library выполнили подготовленные инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] .|  
|[Класс событий Prepare SQL](../../relational-databases/event-classes/prepare-sql-event-class.md)|Указывает, что SqlClient, ODBC, OLE DB или DB-Library подготовили для использования инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)] .|  
|[Класс событий SQL:BatchCompleted](../../relational-databases/event-classes/sql-batchcompleted-event-class.md)|Указывает, что выполнение пакета языка [!INCLUDE[tsql](../../includes/tsql-md.md)] завершено.|  
|[Класс событий SQL:BatchStarting](../../relational-databases/event-classes/sql-batchstarting-event-class.md)|Указывает, что выполнение пакета языка [!INCLUDE[tsql](../../includes/tsql-md.md)] начато.|  
|[Класс событий SQL:StmtCompleted](../../relational-databases/event-classes/sql-stmtcompleted-event-class.md)|Указывает, что выполнение инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)] завершено.|  
|[Класс событий SQL:StmtRecompile](../../relational-databases/event-classes/sql-stmtrecompile-event-class.md)|Указывает на повторные компиляции уровня инструкций, инициированные всеми типами пакетов: хранимыми процедурами, триггерами, нерегламентированными пакетами и запросами.|  
|[Класс событий SQL:StmtStarting](../../relational-databases/event-classes/sql-stmtstarting-event-class.md)|Указывает, что выполнение инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)] начато.|  
|[Класс событий Unprepare SQL](../../relational-databases/event-classes/unprepare-sql-event-class.md)|Указывает, что SqlClient, ODBC, OLE DB или DB-Library удалили подготовленные инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] .|  
|[Класс событий XQuery Static Type](../../relational-databases/event-classes/xquery-static-type-event-class.md)|Возникает, если сервер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняет выражение XQuery.|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по Transact-SQL (компонент Database Engine)](../../t-sql/transact-sql-reference-database-engine.md)  
  
  
