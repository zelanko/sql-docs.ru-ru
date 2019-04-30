---
title: Разрешения, необходимые для запуска приложения SQL Server Profiler | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], permissions
- traces [SQL Server], replaying
- replaying traces
- SQL Server Profiler, permissions
- security [SQL Server], SQL Server Profiler
ms.assetid: 5c580a87-88ae-4314-8fe1-54ade83f227f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bed2868b74087cd0e4c119ada7e29f0c5db73ce5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63240527"
---
# <a name="permissions-required-to-run-sql-server-profiler"></a>Разрешения, необходимые для запуска приложения SQL Server Profiler
  По умолчанию для запуска приложения [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] требуются такие же разрешения, что и для хранимых процедур языка Transact-SQL, используемых для создания трассировок. Для запуска приложения [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] пользователь должен обладать разрешением ALTER TRACE. Дополнительные сведения см. в разделе [GRANT, предоставление разрешений на сервер (Transact-SQL)](/sql/t-sql/statements/grant-server-permissions-transact-sql).  
  
> [!IMPORTANT]  
>  Пользователи, которые имеют разрешение SHOWPLAN, ALTER TRACE или VIEW SERVER STATE, могут просматривать запросы, захваченные выходом Showplan. Эти запросы могут содержать конфиденциальные сведения, такие как пароли. В связи с этим рекомендуется предоставлять данные разрешения только пользователям, которые имеют право просмотра конфиденциальных данных, например членам предопределенной роли базы данных db_owner или членам предопределенной роли сервера sysadmin. Также рекомендуется сохранять файлы Showplan или файлы трассировки, содержащие события, связанные с инструкцией Showplan, только в каталог, расположенный в файловой системе NTFS, для которого есть возможность ограничить доступ, предоставляя его только пользователям, имеющим право просмотра конфиденциальных данных.  
  
## <a name="permissions-used-to-replay-traces"></a>Разрешения на воспроизведение трассировок  
 Для воспроизведения трассировок пользователю требуется разрешение ALTER TRACE.  
  
 Однако если во время воспроизведения трассировки возникло событие «Audit Login», приложение [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] использует команду EXECUTE AS. [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] использует для олицетворения пользователя, связанного с событием входа в систему.  
  
 Если в воспроизводимой трассировке приложение [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] обнаруживает событие входа в систему, то производятся проверки следующих разрешений.  
  
1.  Пользователь1, имеющий разрешение ALTER TRACE, запускает воспроизведение трассировки.  
  
2.  В воспроизводимой трассировке возникло событие входа в систему для Пользователя2.  
  
3.  [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] олицетворяет Пользователя2 командой EXECUTE AS.  
  
4.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пытается проверить подлинность Пользователя2, и, в зависимости от результатов, происходят следующие действия.  
  
    1.  Если проверить подлинность Пользователя2 невозможно, приложение [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] возвращает ошибку и продолжает воспроизведение трассировки от имени Пользователя1.  
  
    2.  Если проверка подлинности Пользователя2 прошла успешно, воспроизведение трассировки продолжается от имени Пользователя2.  
  
5.  Разрешения для Пользователя2 проверяются в базе данных назначения, и, в зависимости от результата, происходят следующие действия.  
  
    1.  Если у Пользователя2 есть разрешения на целевую базу данных, то олицетворение проходит успешно и трассировка воспроизводится от имени Пользователя2.  
  
    2.  Если у Пользователя2 нет разрешений на целевую базу данных, сервер проверяет существование пользователя Guest в этой базе данных.  
  
6.  В целевой базе данных проверяется существование пользователя Guest, и, в зависимости от результата, происходят следующие действия.  
  
    1.  Если учетная запись «Guest» существует, трассировка воспроизводится от ее имени.  
  
    2.  Если в базе данных назначения отсутствует учетная запись «Guest», возвращается ошибка и трассировка воспроизводится от имени Пользователя1.  
  
 На следующей диаграмме показан процесс проверки разрешений во время воспроизведения трассировок:  
  
 ![Разрешения на воспроизведение трассировки SQL Server Profiler](../../database-engine/media/replaytracedecisiontree.gif "разрешения на воспроизведение трассировки SQL Server Profiler")  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры приложения SQL Server Profiler (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)   
 [Воспроизведение трассировок](replay-traces.md)   
 [Создание трассировки (SQL Server Profiler)](create-a-trace-sql-server-profiler.md)   
 [Воспроизведение таблицы трассировки (SQL Server Profiler)](replay-a-trace-table-sql-server-profiler.md)   
 [Воспроизведение файла трассировки (SQL Server Profiler)](replay-a-trace-file-sql-server-profiler.md)  
  
  
