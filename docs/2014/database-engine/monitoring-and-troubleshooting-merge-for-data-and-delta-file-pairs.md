---
title: Мониторинг и устранение неполадок слияния для данных и разностных файлов пар | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: a8b0bacc-4d2c-42e4-84bf-1a97e0bd385b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 61a9b1697b705e56c73a0b610ae426deb288901e
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58537716"
---
# <a name="monitoring-and-troubleshooting-merge-for-data-and-delta-file-pairs"></a>Мониторинг и устранение неполадок со слиянием для пар файлов данных и разностных файлов
  In-Memory OLTP использует политику слияния для автоматического объединения пар смежных файлов данных и разностных файлов. Действия слияния отключить нельзя.  
  
 Мониторинг пар файлов данных и разностных файлов может осуществляться следующим образом.  
  
-   Сравните размер хранилища в памяти и общего размера хранилища. Если хранилище несоразмерно велико, то, скорее всего, слияние не активируется. Дополнительные сведения  
  
-   Просмотрите используемое пространство в данных и разностных файлах, с использованием [sys.dm_db_xtp_checkpoint_files &#40;Transact-SQL&#41; ](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql) для просмотра, если слияние не активируется когда это требуется.  
  
## <a name="performing-a-manual-merge"></a>Выполнение слияния вручную  
 Можно использовать [sys.sp_xtp_merge_checkpoint_files &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-merge-checkpoint-files-transact-sql) для выполнения слияния вручную.  
  
 Используйте следующий запрос для получения сведений о файлах данных и разностных файлах.  
  
```sql  
select checkpoint_file_id, file_type_desc, internal_storage_slot, file_size_in_bytes, file_size_used_in_bytes,   
inserted_row_count, deleted_row_count, lower_bound_tsn, upper_bound_tsn   
from sys.dm_db_xtp_checkpoint_files  
where state = 1  
order by file_type_desc, upper_bound_tsn  
```  
  
 Предположим, что обнаружено три файла данных, которые не были объединены. Используя значение `lower_bound_tsn` первого файла данных и значение `upper_bound_tsn` последнего файла данных, можно выполнить следующую команду:  
  
```sql  
exec sys.sp_xtp_merge_checkpoint_files 'H_DB',  12345, 67890  
```  
  
 Предположим, что три пары файлов данных и разностных файлов имеют каждая по 15 836 строк и 5279 удаленных строк. После слияния новый файл данных содержит 31 872 строки и 0 удаленных строк. Размер нового файла данных может быть значительно больше, чем выбранный исходный размер 128 МБ. Это происходит потому, что слияние вручную переопределяет политику слияния и принудительно выполняет слияние запрошенных файлов.  
  
 Блог [состояния перехода из файлов контрольных точек в базах данных с оптимизированными для памяти таблицами](http://blogs.technet.com/b/dataplatforminsider/archive/2014/01/23/state-transition-of-checkpoint-files-in-databases-with-memory-optimized-tables.aspx) описывается Смена состояния пар данных и разностных файлов с момента их появления в сборку мусора.  
  
## <a name="see-also"></a>См. также  
 [Создание и управление хранилищем для оптимизированных для памяти объектов](../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
