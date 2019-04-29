---
title: MSSQLSERVER_3314 | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3314 (Database Engine error)
ms.assetid: f3a5ca6a-b502-4cab-b3b1-4bc753763fa9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b8d82911f013c9284a55bd55f00654a98633df0a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62914171"
---
# <a name="mssqlserver3314"></a>MSSQLSERVER_3314
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|3314|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|ERR_LOG_RID2|  
|Текст сообщения|При выполнении отката записанной в журнал операции в базе данных «%.*ls» произошла ошибка при работе с записью, идентификатор которой %S_LSN. Как правило, конкретный сбой регистрируется как ошибка в журнале событий Windows. Восстановите базу данных из полной резервной копии или исправьте ее.|  
  
## <a name="explanation"></a>Объяснение  
 Это ошибка свертки при восстановлении откатом. В результате этой ошибки состояние базы данных изменилось на SUSPECT. Первичная файловая группа и, возможно, другие файловые группы могут быть повреждены. Эта база данных не может быть восстановлена во время загрузки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и поэтому недоступна. Для разрешения этой проблемы требуется вмешательство пользователя.  
  
 Следует отметить, что если эта ошибка возникает для базы данных **tempdb**, экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] завершает работу.  
  
## <a name="user-action"></a>Действие пользователя  
 Эта ошибка может вызываться временным состоянием, существовавшим в системе во время данной попытки запуска экземпляра сервера или восстановления базы данных. Эта ошибка может быть также вызвана неустранимым сбоем, который возникает при каждой попытке запуска базы данных. Для выяснения причины проверьте журнал событий Windows, в котором должна содержаться предшествующая ошибка, которая указывает на конкретный сбой.  
  
 Для получения сведений о причине возникновения ошибки 3314 проверьте журнал событий Windows на наличие предыдущего сообщения об ошибке, в котором указан конкретный сбой. Соответствующее действие пользователя зависит от того, что указывают сведения в журнале событий Windows: ошибка [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] была вызвана временным состоянием или неустранимым сбоем. Сведения о действиях пользователя по устранению ошибки 3314 приведены в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также  
 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)   
 [DBCC CHECKDB (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)   
 [Выполнение полного восстановления базы данных (простая модель восстановления)](../backup-restore/complete-database-restores-simple-recovery-model.md)   
 [MSSQLSERVER_824](mssqlserver-824-database-engine-error.md)   
 [sys.databases (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
