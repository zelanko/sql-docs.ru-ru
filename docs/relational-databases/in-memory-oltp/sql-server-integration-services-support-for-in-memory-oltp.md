---
title: "Поддержка служб SQL Server Integration Services для выполняющейся в памяти OLTP | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea82a9b9-e9ed-4d6f-b3fd-917f6c687ae3
caps.latest.revision: "12"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6a36fe2c6a662700e3dd04d3beb891ea9d96cc9a
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="sql-server-integration-services-support-for-in-memory-oltp"></a>Поддержка служб SQL Server Integration Services для In-Memory OLTP
  Можно использовать таблицу, оптимизированную для памяти, представление, ссылающееся на подобные таблицы, или скомпилированную хранимую процедуру как источник или назначение для пакета служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (SSIS). Можно использовать [Источник ADO NET](../../integration-services/data-flow/ado-net-source.md), [Источник OLE DB](../../integration-services/data-flow/ole-db-source.md)или [Источник ODBC](../../integration-services/data-flow/odbc-source.md) в потоке данных пакета служб SSIS и настроить компонент источника для получения данных из оптимизированной для памяти таблицы или представления. Или же можно указать инструкцию SQL для выполнения скомпилированной хранимой процедуры. Аналогично можно использовать [Назначение ADO NET](../../integration-services/data-flow/ado-net-destination.md), [Назначение OLE DB](../../integration-services/data-flow/ole-db-destination.md)или [Назначение ODBC](../../integration-services/data-flow/odbc-destination.md) для загрузки данных в таблицу, оптимизированную для памяти, или в представление либо же указать инструкцию SQL для выполнения скомпилированной хранимой процедуры.  
  
 Можно настроить вышеупомянутые исходные и целевые компоненты в пакете служб SSIS для чтения и записи данных в таблицах и представлениях, оптимизированных для памяти, точно таким же образом, как и в случае с другими таблицами и представлениями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Однако при использовании компилированных хранимых процедур необходимо учитывать два важных аспекта, приведенные в следующем разделе.  
  
## <a name="invoking-a-natively-compiled-stored-procedure-from-an-ssis-package"></a>Вызов скомпилированной хранимой процедуры из пакета служб SSIS  
 Для вызова скомпилированной хранимой процедуры из пакета служб SSIS рекомендуется использовать ODBC Source или ODBC Destination с помощью инструкции SQL формата: **\<имя процедуры>** без ключевого слова **EXEC**. При использовании EXEC «ключевое слово» в инструкции SQL появится сообщение об ошибке, поскольку диспетчер соединений ODBC интерпретирует текст команды SQL в виде инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] , а не хранимой процедуры, а использование курсоров не поддерживается для выполнения в компилированных в собственном коде хранимых процедур. Диспетчер соединений обрабатывает инструкцию SQL без ключевого слова EXEC как вызов хранимой процедуры и не использует курсор.  
  
 Можно также использовать ADO.NET и источник OLE DB для вызова скомпилированной хранимой процедуры, но рекомендуется использовать источник данных ODBC. Если настроить источник ADO.NET для выполнения скомпилированных хранимых процедур, то появится сообщение об ошибке, поскольку поставщик данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient), который использует ADO.NET Source по умолчанию, не поддерживает выполнение скомпилированных хранимых процедур. Источник ADO NET можно настроить на использование поставщика данных ODBC, поставщика OLE DB для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Однако обратите внимание, что источник ODBC дает более высокую производительность, чем источник ADO.NET с поставщиком данных ODBC.  
  
## <a name="see-also"></a>См. также:  
 [Поддержка SQL Server для In-Memory OLTP](../../relational-databases/in-memory-oltp/sql-server-support-for-in-memory-oltp.md)  
  
  
