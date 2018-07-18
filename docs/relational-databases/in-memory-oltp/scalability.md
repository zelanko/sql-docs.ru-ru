---
title: Масштабируемость | Документация Майкрософт
ms.custom: ''
ms.date: 08/27/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: in-memory-oltp
ms.reviewer: ''
ms.suite: sql
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a4891c57-56bb-49f4-9bb5-f11b745279e5
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 1768c9db30f01b6c5cd0350614e2f3c3dc579acb
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
ms.locfileid: "34327345"
---
# <a name="scalability"></a>Масштабируемость
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  SQL Server 2016 содержит улучшения масштабируемости для хранения на дисках таблиц, оптимизированных для памяти.  
  
-   **Несколько потоков для сохранения таблиц, оптимизированных для памяти.**  
  
     В предыдущем выпуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]использовался один поток автономных контрольных точек, который проверял журнал транзакций на наличие изменений в таблицах, оптимизированных для памяти, и сохранял их в файлы контрольных точек (например, файлы данных и разностные файлы). При наличии большего числа ядер один поток контрольных точек может отставать от времени.  
  
     В [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]за сохранение изменений в таблицах, оптимизированных для памяти, отвечают несколько параллельных потоков.  
  
-   **Многопоточное восстановление.**  
  
     В предыдущем выпуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]журнал, применяемый при операции восстановления, использовал один поток. В [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]для применения журнала используется несколько потоков.  
  
-   **Операция MERGE**  
  
     Теперь операция MERGE является многопоточной.  
  
-   **Динамические административные представления**  
  
     Представления [sys.dm_db_xtp_checkpoint_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-stats-transact-sql.md) и [sys.dm_db_xtp_checkpoint_files (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql.md) существенно изменились.  
  
 Слияние вручную было отключено ввиду того, что многопоточные операции слияния должны справиться с нагрузкой.  
  
 Подсистема, выполняющаяся в памяти OLTP, продолжает использовать оптимизированную для памяти файловую группу в зависимости от FILESTREAM, но отдельные файлы в файловой группе не связаны с FILESTREAM. Эти файлы полностью управляются (создание, удаление и сборка мусора) подсистемой, выполняющейся в памяти OLTP. Представление [DBCC SHRINKFILE (Transact-SQL)](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md) не поддерживается.  
  
  
