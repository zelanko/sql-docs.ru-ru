---
title: Скомпилированные в собственном коде хранимые процедуры и параметры настройки
description: Параметры SET сеанса не влияют на выполнение хранимой процедуры, за исключением того, что определенные параметры SET приводят к тому, что хранимые процедуры не запускаются.
ms.custom: seo-dt-2019
ms.date: 10/26/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c1869cf7-9030-4d18-85d6-0e419a4e9af7
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e86ab52348e4e51a2b060bab50aecf2d3c453fc3
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97485286"
---
# <a name="natively-compiled-stored-procedures-and-execution-set-options"></a>Скомпилированные в собственном коде хранимые процедуры и параметры SET выполнения
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Параметры сеанса фиксируются в атомарных блоках, как описано в разделе [Атомарные блоки](atomic-blocks-in-native-procedures.md). Выполнение хранимой процедуры не зависит от параметров SET сеанса, так как атомарные блоки являются обязательными. Однако некоторые параметры SET, например SET NOEXEC и SET SHOWPLAN_XML, препятствуют выполнению хранимых процедур (в том числе хранимых процедур, скомпилированных в собственном коде).   
  
 Если хранимая процедура, скомпилированная в собственном коде, выполняется с любым включенным параметром STATISTICS, то статистика собирается для процедуры в целом, а не одной инструкции. Дополнительные сведения см. в статьях [SET STATISTICS IO (Transact-SQL)](../../t-sql/statements/set-statistics-io-transact-sql.md), [SET STATISTICS PROFILE (Transact-SQL)](../../t-sql/statements/set-statistics-profile-transact-sql.md), [SET STATISTICS TIME (Transact-SQL)](../../t-sql/statements/set-statistics-time-transact-sql.md) и [SET STATISTICS XML (Transact-SQL)](../../t-sql/statements/set-statistics-xml-transact-sql.md). Чтобы получить статистику выполнения на уровне инструкций в изначально скомпилированных хранимых процедурах, используйте сеанс расширенных событий в событии sp_statement_completed, которое запускается, когда завершаются все отдельные запросы в выполнении хранимых процедур. Дополнительные сведения о создании сеансов расширенных событий см. в разделе [CREATE EVENT SESSION (Transact-SQL)](../../t-sql/statements/create-event-session-transact-sql.md).  
  
 **SHOWPLAN_XML** поддерживается для хранимых процедур, скомпилированных в собственном коде. **SHOWPLAN_ALL** и **SHOWPLAN_TEXT** не поддерживаются для хранимых процедур, скомпилированных в собственном коде.  
  
 **SET FMTONLY** не поддерживается для хранимых процедур, скомпилированных в собственном коде. Используйте вместо этой инструкции [sp_describe_first_result_set (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [Скомпилированные в собственном коде хранимые процедуры](./a-guide-to-query-processing-for-memory-optimized-tables.md)  
  
