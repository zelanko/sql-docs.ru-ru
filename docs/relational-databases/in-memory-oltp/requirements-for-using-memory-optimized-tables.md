---
title: Требования для использования таблиц, оптимизированных для памяти | Документация Майкрософт
ms.custom: ''
ms.date: 11/24/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: in-memory-oltp
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47d9a7e8-c597-4b95-a58a-dcf66df8e572
caps.latest.revision: 65
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c227e67b3edb60166910114bf177beef866ce37d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="requirements-for-using-memory-optimized-tables"></a>Требования для использования таблиц, оптимизированных для памяти
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Использование выполняющихся в памяти OLTP в базе данных Azure описано в статье [In-Memory OLTP (оптимизация в памяти)](http://azure.microsoft.com/documentation/articles/sql-database-in-memory/).  
  
 Помимо [требований к оборудованию и программному обеспечению для установки SQL Server](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md), для использования выполняющейся в памяти OLTP необходимо следующее.  
  
-   Любой выпуск [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] с пакетом обновления 1 (SP1) или более поздней версии. Для [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] и [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] RTM (с предварительным пакетом обновления 1, SP1) необходим выпуск Enterprise, Developer или Evaluation.
    
    > [!NOTE]
    > Для выполняющейся в памяти OLTP нужна 64-разрядная версия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] требуется достаточный объем памяти для хранения данных в оптимизированных для памяти таблицах и индексах, а также дополнительная память для поддержания рабочей нагрузки. Дополнительные сведения см. в статье [Оценка требований к объему памяти для таблиц, оптимизированных для памяти](../../relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md) .  

-   Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запускается на виртуальной машине, объем памяти, выделенный такой машине, должен быть достаточным для того, чтобы обеспечить память, необходимую для оптимизированных для памяти таблиц и индексов. В зависимости от ведущего приложения виртуальной машины для выделения необходимой памяти может служить параметр конфигурации "Резервирование памяти", а при использовании динамической памяти — "Минимальный объем ОЗУ". Убедитесь, что эти параметры удовлетворяют потребности баз данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
-   Свободного места на диске требуется вдвое больше, чем для хранимых и оптимизированных для памяти таблиц.  
  
-   Для использования выполняющейся в памяти OLTP необходимо, чтобы процессор поддерживал инструкцию **cmpxchg16b** . Все современные 64-разрядные процессоры поддерживают **cmpxchg16b**.  
  
     Если вы используете ведущее приложение виртуальной машины и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отображает ошибку, вызванную более старым процессором, проверьте, разрешена ли в ведущем приложении виртуальной машины инструкция **cmpxchg16b**. Если нет, можно использовать Hyper-V, где **cmpxchg16b** поддерживается без изменения параметров конфигурации.  
  
-   In-Memory OLTP устанавливается вместе со **службами компонента Database Engine**.  
  
     Для установки средств создания отчетов ([как определить, следует ли перенести таблицу или хранимую процедуру в выполняющуюся в памяти OLTP](../../relational-databases/in-memory-oltp/determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)) и [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (для управления выполняющейся в памяти OLTP с помощью обозревателя объектов [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]) [скачайте SQL Server Management Studio (SSMS)](../../ssms/download-sql-server-management-studio-ssms.md).   
  
## <a name="important-notes-on-using-includehek2includeshek-2-mdmd"></a>Важные примечания относительно использования [!INCLUDE[hek_2](../../includes/hek-2-md.md)]  
  
-   Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], ограничения на размер оптимизированных для памяти таблиц, кроме доступной памяти, отсутствуют. 

-   В [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] общий объем памяти всех устойчивых таблиц в базе данных не должен превышать 250 ГБ. Дополнительные сведения см. в статье [Оценка требований к объему памяти для таблиц, оптимизированных для памяти](../../relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md).  

> [!NOTE]
> Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] с пакетом обновления 1 (SP1), выпуски Standard и Express поддерживают выполняющуюся в памяти OLTP, однако налагают квоты на объем памяти, который можно использовать для оптимизированных для памяти таблиц в отдельной базе данных. В выпуске Standard это ограничение равно 32 ГБ на базу данных; в выпуске Express — 352 МБ на базу данных. 
  
-   Если создается одна база данных с оптимизированными для памяти таблицами или несколько, необходимо включить мгновенную инициализацию файлов (предоставьте стартовой учетной записи служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пользовательское право *SE_MANAGE_VOLUME_NAME*). Без IFI оптимизированные для памяти файлы хранилища (файлы данных и разностные файлы) будут инициализироваться при создании, что может снизить производительность рабочей нагрузки. Дополнительные сведения об IFI см. в разделе [Инициализация файлов базы данных](../../relational-databases/databases/database-instant-file-initialization.md).
  
## <a name="see-also"></a>См. также:  
 [Выполняющаяся в памяти OLTP (оптимизация в памяти)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
 [Мгновенная инициализация файлов базы данных](../../relational-databases/databases/database-instant-file-initialization.md)  
 [Руководство по архитектуре памяти](../../relational-databases/memory-management-architecture-guide.md)
  
