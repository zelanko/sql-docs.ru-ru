---
title: Хранимые процедуры, скомпилированные в собственном коде | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- natively compiled stored procedures
ms.assetid: d5ed432c-10c5-4e4f-883c-ef4d1fa32366
caps.latest.revision: 54
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 377aa0cd89ad794bb9efb3744cbf62723512d12c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37148715"
---
# <a name="natively-compiled-stored-procedures"></a>скомпилированные в собственном коде хранимые процедуры
  Скомпилированные в собственном коде хранимые процедуры — это хранимые процедуры [!INCLUDE[tsql](../../includes/tsql-md.md)] , скомпилированные в машинный код, который обращается к таблицам с оптимизацией для памяти. Скомпилированные в собственном коде хранимые процедуры позволяют эффективно выполнять запросы и бизнес-логику в хранимой процедуре. Дополнительные сведения о процессе компиляции в собственный код см. в разделе [Native Compilation of Tables and Stored Procedures](native-compilation-of-tables-and-stored-procedures.md). Дополнительные сведения о миграции дисковых хранимых процедур в скомпилированные в собственном коде хранимые процедуры см. в разделе [Migration Issues for Natively Compiled Stored Procedures](migration-issues-for-natively-compiled-stored-procedures.md).  
  
> [!NOTE]  
>  Одним из различий между интерпретируемыми (дисковыми) хранимыми процедурами и хранимыми процедурами, скомпилированными в собственном коде, является то, что интерпретируемые хранимые процедуры компилируются при первом выполнении, а хранимые процедуры, скомпилированные в собственном коде, компилируются при их создании. При работе со скомпилированными хранимыми процедурами многие ошибочные ситуации (арифметическое переполнение, преобразование типов и в некоторых случаях деления на нуль) могут быть обнаружены во время создания, что приведет к неуспешному завершению операции создания компилируемой хранимой процедуры. При работе с интерпретируемыми хранимыми процедурами эти ошибочные ситуации обычно не приводят к появлению ошибок при создании хранимой процедуры, но все выполнения такой процедуры завершатся ошибкой.  
  
 Подразделы в этом разделе:  
  
-   [Создание хранимых процедур, скомпилированных в собственном коде](creating-natively-compiled-stored-procedures.md)  
  
-   [Атомарные блоки](atomic-blocks-in-native-procedures.md)  
  
-   [Поддерживаемые конструкции для хранимых процедур, скомпилированных в собственном коде](supported-features-for-natively-compiled-t-sql-modules.md)  
  
-   [Использование блоков try..catch в хранимых процедурах, скомпилированных в собственном коде](../../database-engine/using-try-catch-in-natively-compiled-stored-procedures.md)  
  
-   [Поддерживаемые конструкции для хранимых процедур, скомпилированных в собственном коде](supported-ddl-for-natively-compiled-t-sql-modules.md)  
  
-   [Скомпилированные в собственном коде хранимые процедуры и параметры SET выполнения](natively-compiled-stored-procedures-and-execution-set-options.md)  
  
-   [Рекомендации по вызову хранимых процедур, скомпилированных в собственном коде](best-practices-for-calling-natively-compiled-stored-procedures.md)  
  
-   [Отслеживание производительности скомпилированных в собственном коде хранимых процедур](monitoring-performance-of-natively-compiled-stored-procedures.md)  
  
-   [Вызов хранимых процедур, скомпилированных в собственном коде, из приложений для доступа к данным](calling-natively-compiled-stored-procedures-from-data-access-applications.md)  
  
## <a name="see-also"></a>См. также  
 [Таблицы, оптимизированные для памяти](memory-optimized-tables.md)  
  
  
