---
title: Поддержка Integration Services для выполняющейся в памяти OLTP
description: Сведения об использовании хранимых процедур, скомпилированных в собственном виде, в качестве исходных и целевых компонентов в пакете SQL Server Integration Services.
ms.custom: seo-dt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: ea82a9b9-e9ed-4d6f-b3fd-917f6c687ae3
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3f638de7d98cd8e322174172ce918152cbe4623a
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97485196"
---
# <a name="sql-server-integration-services-support-for-in-memory-oltp"></a>Поддержка служб SQL Server Integration Services для In-Memory OLTP
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Можно использовать таблицу, оптимизированную для памяти, представление, ссылающееся на подобные таблицы, или скомпилированную хранимую процедуру как источник или назначение для пакета служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (SSIS). Можно использовать [Источник ADO NET](../../integration-services/data-flow/ado-net-source.md), [Источник OLE DB](../../integration-services/data-flow/ole-db-source.md)или [Источник ODBC](../../integration-services/data-flow/odbc-source.md) в потоке данных пакета служб SSIS и настроить компонент источника для получения данных из оптимизированной для памяти таблицы или представления. Или же можно указать инструкцию SQL для выполнения скомпилированной хранимой процедуры. Аналогично можно использовать [Назначение ADO NET](../../integration-services/data-flow/ado-net-destination.md), [Назначение OLE DB](../../integration-services/data-flow/ole-db-destination.md)или [Назначение ODBC](../../integration-services/data-flow/odbc-destination.md) для загрузки данных в таблицу, оптимизированную для памяти, или в представление либо же указать инструкцию SQL для выполнения скомпилированной хранимой процедуры.  
  
 Можно настроить вышеупомянутые исходные и целевые компоненты в пакете служб SSIS для чтения и записи данных в таблицах и представлениях, оптимизированных для памяти, точно таким же образом, как и в случае с другими таблицами и представлениями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Однако при использовании компилированных хранимых процедур необходимо учитывать два важных аспекта, приведенные в следующем разделе.  
  
## <a name="invoking-a-natively-compiled-stored-procedure-from-an-ssis-package"></a>Вызов скомпилированной хранимой процедуры из пакета служб SSIS  
 Для вызова скомпилированной хранимой процедуры из пакета служб SSIS рекомендуется использовать ODBC Source или ODBC Destination с помощью инструкции SQL формата: **\<procedure name>** без ключевого слова **EXEC**. При использовании EXEC «ключевое слово» в инструкции SQL появится сообщение об ошибке, поскольку диспетчер соединений ODBC интерпретирует текст команды SQL в виде инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] , а не хранимой процедуры, а использование курсоров не поддерживается для выполнения в компилированных в собственном коде хранимых процедур. Диспетчер соединений обрабатывает инструкцию SQL без ключевого слова EXEC как вызов хранимой процедуры и не использует курсор.  
  
 Можно также использовать ADO.NET и источник OLE DB для вызова скомпилированной хранимой процедуры, но рекомендуется использовать источник данных ODBC. Если настроить источник ADO.NET для выполнения скомпилированных хранимых процедур, то появится сообщение об ошибке, поскольку поставщик данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient), который использует ADO.NET Source по умолчанию, не поддерживает выполнение скомпилированных хранимых процедур. Источник ADO NET можно настроить на использование поставщика данных ODBC, поставщика OLE DB для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Однако обратите внимание, что источник ODBC дает более высокую производительность, чем источник ADO.NET с поставщиком данных ODBC.  
  
## <a name="see-also"></a>См. также:  
 [Поддержка SQL Server для In-Memory OLTP](./transact-sql-support-for-in-memory-oltp.md)  
  
