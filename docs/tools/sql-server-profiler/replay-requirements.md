---
title: "Требования к воспроизведению | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: sql-server-profiler
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- event classes [SQL Server], replaying traces
- traces [SQL Server], replaying
- replaying traces
- TSQL_Replay template [SQL Server]
ms.assetid: 0e01dfc7-84b9-47f6-8bf7-b0656df4fa7d
caps.latest.revision: "18"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fe999b92d34b9070a1c461340919c839468c02c9
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="replay-requirements"></a>Требования к воспроизведению
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Для воспроизведения данных трассировки с [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] или программы распределенного воспроизведения, определенный набор классов событий и столбцов должен быть записан в трассировке. Если для настройки трассировки, которая в дальнейшем будет использоваться для воспроизведения, применяется шаблон трассировки **TSQL_Replay** , то по умолчанию эти параметры включены. В этом разделе приводится описание этих параметров и других требований к воспроизведению.  
  
> [!NOTE]  
>  Для воспроизведения ресурсоемких приложений OLTP (с множеством одновременных активных соединений или высокой пропускной способностью) рекомендуется пользоваться программой распределенного воспроизведения. Программа распределенного воспроизведения воспроизводит данные трассировки с нескольких компьютеров и лучше имитирует важную рабочую нагрузку. Дополнительные сведения см. в статье [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md).  
  
## <a name="event-classes-required-for-replay"></a>Классы событий, необходимые для воспроизведения  
 Чтобы воспроизведение можно было выполнить с помощью [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], в трассировке помимо классов событий, отобранных для наблюдения, необходимо фиксировать следующий набор классов событий.  
  
-   **CursorClose**(требуется только при воспроизведении курсоров со стороны сервера);  
  
-   **CursorExecute** (требуется только при воспроизведении курсоров со стороны сервера);  
  
-   **CursorOpen** (требуется только при воспроизведении курсоров со стороны сервера);  
  
-   **CursorPrepare** (требуется только при воспроизведении курсоров со стороны сервера);  
  
-   **CursorUnprepare** (требуется только при воспроизведении курсоров со стороны сервера);  
  
-   **Аудит входа в систему**  
  
-   **Аудит выхода из системы**  
  
-   **ExistingConnection**  
  
-   **RPC Output Parameter**  
  
-   **RPC:Completed**  
  
-   **RPC:Starting**  
  
-   **Exec Prepared SQL** (требуется только при воспроизведении подготовленных инструкций SQL на стороне сервера);  
  
-   **Prepare SQL** (требуется только при воспроизведении подготовленных инструкций SQL на стороне сервера).  
  
-   **SQL:BatchCompleted**  
  
-   **SQL:BatchStarting**  
  
## <a name="data-columns-required-for-replay"></a>Столбцы данных, необходимые для воспроизведения  
 Чтобы обеспечить воспроизведение трассировки, в дополнение к любым захватываемым столбцам данных должны захватываться следующие столбцы:  
  
-   **Класс событий**  
  
-   **EventSequence**  
  
-   **TextData**  
  
-   **Application Name**  
  
-   **LoginName**  
  
-   **DatabaseName**  
  
-   **Идентификатор базы данных**  
  
-   **ClientProcessID**  
  
-   **HostName**  
  
-   **ServerName**  
  
-   **Binary Data**  
  
-   **SPID**  
  
-   **Start Time**  
  
-   **EndTime**  
  
-   **IsSystem**  
  
-   **NTDomainName**  
  
-   **NTUserName**  
  
-   **Ошибка**  
  
> [!NOTE]  
>  В трассировках, захватывающих данные для воспроизведения, следует использовать шаблон **TSQL_Replay** .  
  
## <a name="other-replay-requirements"></a>Другие требования к воспроизведению  
 В Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]при воспроизведении проверяется наличие обязательных событий и столбцов. Это помогает повысить точность воспроизведения и избавляет от необходимости строить предположения при устранении неполадок воспроизведения, если необходимые данные отсутствуют. Если в трассировке отсутствуют необходимые данные, то воспроизведение возвращает ошибку и завершается неуспешно.  
  
 Для воспроизведения трассировки на целевом сервере, на котором запущен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , отличном от исходного сервера, где первоначально выполнялась трассировка, убедитесь, что выполнены следующие действия:  
  
-   На целевом сервере в той же базе данных, что и на исходном сервере, должны быть созданы все имена входа и пользователи, содержащиеся в трассировке.  
  
-   Все имена входа и пользователи на целевом сервере должны обладать теми же разрешениями, что были у них на исходном сервере.  
  
-   Все пароли должны совпадать с паролями пользователя, выполняющего воспроизведение.  
  
-   Желательно, чтобы идентификаторы баз данных на целевом и на исходном серверах совпадали. Впрочем, если они не совпадают, соответствие можно установить по параметру **DatabaseName** , если он есть в трассировке.  
  
-   Для каждого имени входа в трассировке должна быть задана база данных по умолчанию, соответствующая целевой базе данных имени входа. Например, на исходном сервере в базе данных **Fred_Db**трассировка для воспроизведения содержит операцию для имени входа **Fred** . Таким образом, на целевом сервере необходимо задать базу данных по умолчанию для имени входа **Fred**, соответствующую базе данных **Fred_Db** (даже если имена баз данных различаются). Базу данных по умолчанию для имени входа можно задать с помощью хранимой процедуры **sp_defaultdb** .  
  
 В результате воспроизведения событий, связанных с отсутствующими или неверными именами входа, будут возникать ошибки воспроизведения, но сама операция воспроизведения будет продолжена.  
  
 Сведения о разрешениях, необходимых для воспроизведения трассировки, см. в разделе [Permissions Required to Run SQL Server Profiler](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md).  
  
## <a name="see-also"></a>См. также:  
 [Воспроизведение таблицы трассировки &#40; Приложение SQL Server Profiler &#41;](../../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md)   
 [Воспроизведение файла трассировки &#40; Приложение SQL Server Profiler &#41;](../../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md)   
 [Руководство по классам событий SQL Server](../../relational-databases/event-classes/sql-server-event-class-reference.md)   
 [sp_defaultdb (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-defaultdb-transact-sql.md)   
 [Распределенное воспроизведение SQL Server](../../tools/distributed-replay/sql-server-distributed-replay.md)  
  
  
