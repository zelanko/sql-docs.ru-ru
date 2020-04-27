---
title: Скомпилированные в собственном коде хранимые процедуры и параметры набора выполнения | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c1869cf7-9030-4d18-85d6-0e419a4e9af7
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: eaf7057130cc3d13c0025b92b207efbace339e74
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63131485"
---
# <a name="natively-compiled-stored-procedures-and-execution-set-options"></a>Скомпилированные в собственном коде хранимые процедуры и параметры SET выполнения
  Параметры сеанса фиксированы в блоках ATOMIC. Выполнение хранимой процедуры не зависит от значения параметров SET сеанса. Однако некоторые параметры SET, например SET NOEXEC и SET SHOWPLAN_XML, препятствуют выполнению хранимых процедур (в том числе хранимых процедур, скомпилированных в собственном коде).  
  
 Если хранимая процедура, скомпилированная в собственном коде, выполняется с любым включенным параметром STATISTICS, то статистика собирается для процедуры в целом, а не одной инструкции. Дополнительные сведения см. в статьях [SET STATISTICS IO (Transact-SQL)](/sql/t-sql/statements/set-statistics-io-transact-sql), [SET STATISTICS PROFILE (Transact-SQL)](/sql/t-sql/statements/set-statistics-profile-transact-sql), [SET STATISTICS TIME (Transact-SQL)](/sql/t-sql/statements/set-statistics-time-transact-sql) и [SET STATISTICS XML (Transact-SQL)](/sql/t-sql/statements/set-statistics-xml-transact-sql). Чтобы получить статистику выполнения на уровне инструкций в изначально скомпилированных хранимых процедурах, используйте сеанс расширенных событий в событии sp_statement_completed, которое запускается, когда завершаются все отдельные запросы в выполнении хранимых процедур. Дополнительные сведения о создании сеансов расширенных событий см. в разделе [CREATE EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/create-event-session-transact-sql).  
  
 `SHOWPLAN_XML` поддерживается для хранимых процедурах, скомпилированных в собственном коде. `SHOWPLAN_ALL` и `SHOWPLAN_TEXT` не поддерживаются для хранимых процедур, скомпилированных в собственном коде.  
  
 `SET FMTONLY` не поддерживается для хранимых процедур, скомпилированных в собственном коде. Используйте вместо этой инструкции [sp_describe_first_result_set (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql).  
  
## <a name="see-also"></a>См. также:  
 [Скомпилированные в собственном коде хранимые процедуры](natively-compiled-stored-procedures.md)  
  
  
