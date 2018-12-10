---
title: Масштабируемость | Документация Майкрософт
ms.custom: ''
ms.date: 08/27/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: a4891c57-56bb-49f4-9bb5-f11b745279e5
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4f672c1b3d7ff8d4480e6fb1647058c50715b657
ms.sourcegitcommit: 1f10e9df1c523571a8ccaf3e3cb36a26ea59a232
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2018
ms.locfileid: "51858569"
---
# <a name="scalability"></a>Масштабируемость
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] содержит улучшения масштабируемости для хранения на дисках таблиц, оптимизированных для памяти. 

## <a name="multiple-threads-to-persist-memory-optimized-tables"></a>Несколько потоков для сохранения таблиц, оптимизированных для памяти.  
  
В [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] использовался один поток автономных контрольных точек, который проверял журнал транзакций на наличие изменений в таблицах, оптимизированных для памяти, и сохранял их в файлы контрольных точек (например, файлы данных и разностные файлы). В компьютерах с большим числом ядер один поток контрольных точек может отставать от времени.  
  
Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] за сохранение изменений в таблицах, оптимизированных для памяти, отвечают несколько параллельных потоков.  
  
## <a name="multi-threaded-recovery"></a>Многопоточное восстановление.
В предыдущем выпуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]журнал, применяемый при операции восстановления, использовал один поток. Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] для применения журнала используется несколько потоков.  
  
## <a name="merge-operation"></a>Операция MERGE  
Теперь операция MERGE является многопоточной.  
   
> [!NOTE]
> Слияние вручную было отключено ввиду того, что многопоточные операции слияния должны справиться с нагрузкой. 

## <a name="dynamic-management-views"></a>Динамические административные представления  
Динамические административные представления [sys.dm_db_xtp_checkpoint_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-stats-transact-sql.md) и [sys.dm_db_xtp_checkpoint_files &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql.md) существенно изменились.  

## <a name="storage-management"></a>Управление хранением
Подсистема, выполняющаяся в памяти OLTP, продолжает использовать оптимизированную для памяти файловую группу в зависимости от FILESTREAM, но отдельные файлы в файловой группе не связаны с FILESTREAM. Эти файлы полностью управляются (создание, удаление и сборка мусора) подсистемой, выполняющейся в памяти OLTP. 

> [!NOTE]
> Представление [DBCC SHRINKFILE (Transact-SQL)](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md) не поддерживается.  
  
## <a name="see-also"></a>См. также:   
[Создание и управление хранилищем для оптимизированных для памяти объектов](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)     
[Database Files and Filegroups](../../relational-databases/databases/database-files-and-filegroups.md)    
[Параметры инструкции ALTER DATABASE для файлов и файловых групп (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md)    
