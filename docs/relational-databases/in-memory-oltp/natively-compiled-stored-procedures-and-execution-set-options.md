---
title: "Скомпилированные в собственном коде хранимые процедуры и параметры набора выполнения | Документация Майкрософт"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1869cf7-9030-4d18-85d6-0e419a4e9af7
caps.latest.revision: 5
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 02a1683278d0f64ac41893a9cdb8e97a634002b5
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="natively-compiled-stored-procedures-and-execution-set-options"></a>Скомпилированные в собственном коде хранимые процедуры и параметры SET выполнения
  Параметры сеанса фиксированы в блоках ATOMIC. Выполнение хранимой процедуры не зависит от значения параметров SET сеанса. Однако некоторые параметры SET, например SET NOEXEC и SET SHOWPLAN_XML, препятствуют выполнению хранимых процедур (в том числе хранимых процедур, скомпилированных в собственном коде).  
  
 Если хранимая процедура, скомпилированная в собственном коде, выполняется с любым включенным параметром STATISTICS, то статистика собирается для процедуры в целом, а не одной инструкции. Дополнительные сведения см. в статьях [SET STATISTICS IO (Transact-SQL)](../../t-sql/statements/set-statistics-io-transact-sql.md), [SET STATISTICS PROFILE (Transact-SQL)](../../t-sql/statements/set-statistics-profile-transact-sql.md), [SET STATISTICS TIME (Transact-SQL)](../../t-sql/statements/set-statistics-time-transact-sql.md) и [SET STATISTICS XML (Transact-SQL)](../../t-sql/statements/set-statistics-xml-transact-sql.md). Чтобы получить статистику выполнения на уровне инструкций в изначально скомпилированных хранимых процедурах, используйте сеанс расширенных событий в событии sp_statement_completed, которое запускается, когда завершаются все отдельные запросы в выполнении хранимых процедур. Дополнительные сведения о создании сеансов расширенных событий см. в разделе [CREATE EVENT SESSION (Transact-SQL)](../../t-sql/statements/create-event-session-transact-sql.md).  
  
 **SHOWPLAN_XML** поддерживается для хранимых процедур, скомпилированных в собственном коде. **SHOWPLAN_ALL** и **SHOWPLAN_TEXT** не поддерживаются для хранимых процедур, скомпилированных в собственном коде.  
  
 **SET FMTONLY** не поддерживается для хранимых процедур, скомпилированных в собственном коде. Используйте вместо этой инструкции [sp_describe_first_result_set (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [Скомпилированные в собственном коде хранимые процедуры](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)  
  
  
