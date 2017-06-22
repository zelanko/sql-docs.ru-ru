---
title: "MSSQLSERVER_3313 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 3313 (Database Engine error)
ms.assetid: a244227b-8553-42df-9435-034f906c4c74
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 6e8b07b5a12de6b011ee581e0d869c4ec30427e3
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver3313"></a>MSSQLSERVER_3313
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|3313|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|ERR_LOG_RID1|  
|Текст сообщения|При повторном выполнении запротоколированной операции в базе данных "%.*ls" произошла ошибка при работе с записью, идентификатор которой %S_LSN. Как правило, конкретный сбой регистрируется как ошибка в журнале событий Windows. Восстановите базу данных из полной резервной копии или произведите ее исправление.|  
  
## <a name="explanation"></a>Объяснение  
Это ошибка свертки при восстановлении с повтором. В результате этой ошибки состояние базы данных изменилось на SUSPECT. Первичная файловая группа и, возможно, другие файловые группы могут быть повреждены. Эта база данных не может быть восстановлена во время загрузки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и поэтому недоступна. Для разрешения этой проблемы требуется вмешательство пользователя.  
  
Следует отметить, что если эта ошибка возникает для базы данных **tempdb**, экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] завершает работу.  
  
## <a name="user-action"></a>Действие пользователя  
Эта ошибка может вызываться временным состоянием, существовавшим в системе во время данной попытки запуска экземпляра сервера или восстановления базы данных. Эта ошибка может быть также вызвана неустранимым сбоем, который возникает при каждой попытке запуска базы данных. Для выяснения причины проверьте журнал событий Windows, в котором должна содержаться предшествующая ошибка, которая указывает на конкретный сбой.  
  
Следует отметить, что при возникновении этой ошибки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обычно создает три файла в папке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **LOG**. Файл SQLDump*nnnn*.txt содержит дополнительные данные диагностики, относящиеся к сбоям, включая сведения о транзакции и о странице, на которой возникла проблема. Эти сведения обычно используются группой поддержки продукта для анализа причины сбоя.  
  
Чтобы получить сведения о причине возникновения ошибки 3313, изучите в журнале событий Windows предшествующее сообщение об ошибке, в котором указан конкретный сбой. Соответствующее действие пользователя зависит от того, что указывают сведения в журнале событий Windows: ошибка [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] была вызвана временным состоянием или неустранимым сбоем. Сведения о действиях пользователя по устранению ошибки 3313 приведены в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:  
[ALTER DATABASE (Transact-SQL)](~/t-sql/statements/alter-database-transact-sql-set-options.md)  
[DBCC CHECKDB (Transact-SQL)](~/t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)  
[Выполнение полного восстановления базы данных (простая модель восстановления)](~/relational-databases/backup-restore/complete-database-restores-simple-recovery-model.md)  
[MSSQLSERVER_824](~/relational-databases/errors-events/mssqlserver-824-database-engine-error.md)  
[sys.databases &#40;Transact-SQL&#41;](~/relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
  

