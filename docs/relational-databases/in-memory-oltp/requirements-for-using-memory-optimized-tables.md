---
title: "Требования для использования таблиц, оптимизированных для памяти | Документация Майкрософт"
ms.custom: 
ms.date: 11/16/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: in-memory-oltp
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 47d9a7e8-c597-4b95-a58a-dcf66df8e572
caps.latest.revision: "65"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 88939992ca125a6db88d0e0f3cb3dab794916195
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="requirements-for-using-memory-optimized-tables"></a>Требования для использования таблиц, оптимизированных для памяти
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Использование выполняющихся в памяти OLTP в базе данных Azure описано в статье [In-Memory OLTP (оптимизация в памяти)](http://azure.microsoft.com/documentation/articles/sql-database-in-memory/).  
  
 Помимо [требований к оборудованию и программному обеспечению для установки SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)для использования OLTP в памяти необходимо следующее:  
  
-   Любой выпуск SQL Server 2016 с пакетом обновления 1 (SP1) или более поздней версии. Для SQL Server 2014 и SQL Server 2016 RTM (с предварительным пакетом SP1) необходим выпуск Enterprise, Developer или Evaluation.
    - Примечание. Для выполняющейся в памяти OLTP требуется 64-разрядная версия SQL Server.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] требуется достаточный объем памяти для хранения данных в оптимизированных для памяти таблицах и индексах, а также дополнительная память для поддержания рабочей нагрузки. Дополнительные сведения см. в статье [Оценка требований к объему памяти для таблиц, оптимизированных для памяти](../../relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md) .  

-   Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запускается на виртуальной машине, объем памяти, выделенный такой машине, должен быть достаточным для того, чтобы обеспечить память, необходимую для оптимизированных для памяти таблиц и индексов. В зависимости от ведущего приложения виртуальной машины для выделения необходимой памяти может служить параметр конфигурации "Резервирование памяти", а при использовании динамической памяти — "Минимальный объем ОЗУ". Убедитесь, что эти параметры удовлетворяют потребности баз данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
-   Свободного места на диске требуется вдвое больше, чем для хранимых и оптимизированных для памяти таблиц.  
  
-   Для использования выполняющейся в памяти OLTP необходимо, чтобы процессор поддерживал инструкцию **cmpxchg16b** . Все современные 64-разрядные процессоры поддерживают **cmpxchg16b**.  
  
     Если вы используете ведущее приложение виртуальной машины и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отображает ошибку, вызванную более старым процессором, проверьте, разрешена ли в ведущем приложении виртуальной машины инструкция **cmpxchg16b**. Если нет, можно использовать Hyper-V, где **cmpxchg16b** поддерживается без изменения параметров конфигурации.  
  
-   In-Memory OLTP устанавливается вместе со **службами компонента Database Engine**.  
  
     Для установки создания отчетов ([определение, должна ли таблица или хранимая процедура быть перенесена в In-Memory OLTP](../../relational-databases/in-memory-oltp/determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)) и [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (для управления In-Memory OLTP с помощью обозревателя объектов [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ) [загрузите среду SQL Server Management Studio (SSMS)](https://msdn.microsoft.com/library/mt238290.aspx).   
  
## <a name="important-notes-on-using-includehek2includeshek-2-mdmd"></a>Важные примечания относительно использования [!INCLUDE[hek_2](../../includes/hek-2-md.md)]  
  
-   Начиная с SQL Server 2016, ограничения на размер оптимизированных для памяти таблиц (кроме доступной памяти) не действуют. В SQL Server 2014 общий объем памяти всех устойчивых таблиц в базе данных не должен превышать 250 ГБ. Дополнительные сведения см. в статье [Оценка требований к объему памяти для таблиц, оптимизированных для памяти](../../relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md).  
    - Примечание. Начиная с SQL Server 2016 с пакетом обновления 1 (SP1), выпуски Standard и Express поддерживают выполняющуюся в памяти OLTP, однако налагают квоты на объем памяти, который можно использовать для оптимизированных для памяти таблиц в заданной базе данных. В выпуске Standard это ограничение равно 32 ГБ на базу данных; в выпуске Express — 352 МБ на базу данных. 
  
-   Если создается одна или несколько баз данных с таблицами, оптимизированными для памяти, необходимо включить быструю инициализацию файлов (предоставьте стартовой учетной записи служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] право SE_MANAGE_VOLUME_NAME) для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Без быстрой инициализации файлов оптимизированные для памяти файлы хранилища (файлы данных и разностные файлы) будут инициализироваться при создании и могут отрицательно повлиять на производительность рабочей нагрузки. Дополнительные сведения о быстрой инициализации файлов см. в разделе [Инициализация файлов базы данных](http://msdn.microsoft.com/library/ms175935\(SQL.105\).aspx). Сведения о включении быстрой инициализации файлов см. в разделе [Как и зачем необходимо включать быструю инициализацию файлов](http://blogs.msdn.com/b/sql_pfe_blog/archive/2009/12/23/how-and-why-to-enable-instant-file-initialization.aspx).  
  
## <a name="see-also"></a>См. также  
 [Выполняющаяся в памяти OLTP (оптимизация в памяти)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
