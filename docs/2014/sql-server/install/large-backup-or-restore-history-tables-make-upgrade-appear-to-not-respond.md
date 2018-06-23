---
title: Обновление по-видимому, не отвечают сделать больших таблиц журналов резервного копирования или восстановления | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- backup history tables
- history tables
ms.assetid: f88d86ec-324b-4518-b6d7-1af7e7265812
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1b7d3f6c5734f743d83a712cea745c3816bcdbc0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096812"
---
# <a name="large-backup-or-restore-history-tables-make-upgrade-appear-to-not-respond"></a>Резервное копирование или восстановление больших таблиц журналов может привести к кажущемуся отсутствию ответа от процесса обновления
  В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] в некоторые таблицы журнала резервного копирования и восстановления были добавлены новые столбцы. При обновлении этих таблиц требуется изменить их для добавления новых столбцов. Если одна или несколько из этих таблиц содержит большое количество строк, обновление задержится на длительное время на инструкции ALTER TABLE, которая добавляет столбцы в эту таблицу.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 Может показаться, что процесс обновления остановился, если любая из следующих таблиц журнала резервного копирования и восстановления содержит большое количество строк:  
  
-   **backupfile;**  
  
-   **backupmediafamily;**  
  
-   **backupmediaset;**  
  
-   **backupset;**  
  
-   **restorefile;**  
  
-   **restorefilegroup;**  
  
-   **restorehistory.**  
  
 Если любая из этих таблиц содержит 10 000 или более строк, то помощник по обновлению сообщает об ошибке несоответствия. Не сообщается, какая таблица превысила разрешенное число строк. Первая таблица, число строк в которой превышает 10 000, вызывает ошибку.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Если какая-либо таблица содержит более 10 000 строк, то, прежде чем обновить базу данных, рекомендуется уменьшить число строк так, чтобы оно стало меньше 10 000. Чтобы уменьшить число строк во всех таблицах, можно выполнить **sp_delete_backuphistory** хранимой процедуры. Эта процедура удаляет из всех таблиц журнала резервного копирования и восстановления записи, относящиеся к резервным наборам данных, которые старше указанной даты. Дополнительные сведения см. в разделе [sp_delete_backuphistory (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql).  
  
> [!NOTE]  
>  Можно обновить базу данных, таблицы журнала резервного копирования и восстановления которой содержат более 10 000 строк. Однако при изменении больших таблиц может показаться, что процесс обновления остановился. Чем больше таблица, тем больше времени требуется для завершения программы установки.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
