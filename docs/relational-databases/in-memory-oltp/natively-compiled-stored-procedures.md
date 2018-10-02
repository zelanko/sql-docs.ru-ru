---
title: Хранимые процедуры, скомпилированные в собственном коде | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
helpviewer_keywords:
- natively compiled stored procedures
ms.assetid: d5ed432c-10c5-4e4f-883c-ef4d1fa32366
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 44dd4f25c5811501ec4219acbdd9b24c0b96ab04
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47674402"
---
# <a name="natively-compiled-stored-procedures"></a>скомпилированные в собственном коде хранимые процедуры
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Скомпилированные в собственном коде хранимые процедуры — это хранимые процедуры [!INCLUDE[tsql](../../includes/tsql-md.md)] , скомпилированные в машинный код, который обращается к таблицам с оптимизацией для памяти. Скомпилированные в собственном коде хранимые процедуры позволяют эффективно выполнять запросы и бизнес-логику в хранимой процедуре. Дополнительные сведения о процессе компиляции в собственный код см. в разделе [Native Compilation of Tables and Stored Procedures](../../relational-databases/in-memory-oltp/native-compilation-of-tables-and-stored-procedures.md). Дополнительные сведения о миграции дисковых хранимых процедур в скомпилированные в собственном коде хранимые процедуры см. в разделе [Проблемы миграции, связанные с хранимыми процедурами, которые скомпилированы в собственном коде](../../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md).  
  
> [!NOTE]  
>  Одним из различий между интерпретируемыми (дисковыми) хранимыми процедурами и хранимыми процедурами, скомпилированными в собственном коде, является то, что интерпретируемые хранимые процедуры компилируются при первом выполнении, а хранимые процедуры, скомпилированные в собственном коде, компилируются при их создании. При работе со скомпилированными хранимыми процедурами многие условия ошибки (арифметическое переполнение, преобразование типов и в некоторых случаях деления на нуль) могут быть обнаружены во время создания, что приведет к сбою операции создания компилируемой хранимой процедуры. При работе с интерпретируемыми хранимыми процедурами эти условия ошибки обычно не приводят к появлению ошибок при создании хранимой процедуры, но все выполнения такой процедуры завершатся ошибкой.  
  
 Подразделы в этом разделе:  
  
-   [Создание хранимых процедур, скомпилированных в собственном коде](../../relational-databases/in-memory-oltp/creating-natively-compiled-stored-procedures.md)  
  
-   [Блоки ATOMIC](../../relational-databases/in-memory-oltp/atomic-blocks-in-native-procedures.md)  
  
-   [Поддерживаемые функции для модулей, скомпилированных в собственном коде T-SQL](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md)  
  
-   [Поддерживаемые конструкции DDL для модулей, скомпилированных в собственном коде T-SQL](../../relational-databases/in-memory-oltp/supported-ddl-for-natively-compiled-t-sql-modules.md)  
  
-   [Скомпилированные в собственном коде хранимые процедуры и параметры SET выполнения](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures-and-execution-set-options.md)  
  
-   [Рекомендации по вызову хранимых процедур, скомпилированных в собственном коде](../../relational-databases/in-memory-oltp/best-practices-for-calling-natively-compiled-stored-procedures.md)  
  
-   [Отслеживание производительности скомпилированных в собственном коде хранимых процедур](../../relational-databases/in-memory-oltp/monitoring-performance-of-natively-compiled-stored-procedures.md)  
  
-   [Вызов хранимых процедур, скомпилированных в собственном коде, из приложений для доступа к данным](../../relational-databases/in-memory-oltp/calling-natively-compiled-stored-procedures-from-data-access-applications.md)  
  
## <a name="see-also"></a>См. также:  
 [Таблицы, оптимизированные для памяти](../../relational-databases/in-memory-oltp/memory-optimized-tables.md)  
  
  
