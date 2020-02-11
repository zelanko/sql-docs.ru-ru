---
title: MSSQLSERVER_3414 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3414 (Database Engine error)
ms.assetid: f25852f9-b91c-4356-b817-78bec9ec8db4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 890179c3f5a6bc7d3d627ce9cf2c51fc5d2e96ba
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62868279"
---
# <a name="mssqlserver_3414"></a>MSSQLSERVER_3414
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|3414|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|REC_GIVEUP|  
|Текст сообщения|Во время восстановления произошла ошибка, препятствующая перезапуску базы данных «%.*ls» (идентификатор базы данных %d). Проведите диагностику ошибок восстановления и исправьте их, или проведите восстановление из проверенной рабочей резервной копии. Если ошибки не устранены или ожидаются в будущем, свяжитесь со службой технической поддержки.|  
  
## <a name="explanation"></a>Объяснение  
 Заданная база данных была восстановлена, но не была запущена, так как при восстановлении возникли ошибки. В результате этой ошибки состояние базы данных изменилось на SUSPECT. Первичная файловая группа и, возможно, другие файловые группы могут быть повреждены. Эта база данных не может быть восстановлена во время загрузки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и поэтому недоступна. Для разрешения этой проблемы требуется вмешательство пользователя.  
  
 Следует отметить, что если эта ошибка возникает для базы данных **tempdb**, экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] завершает работу.  
  
## <a name="user-action"></a>Действие пользователя  
 Эта ошибка может вызываться временным состоянием, существовавшим в системе во время данной попытки запуска экземпляра сервера или восстановления базы данных. Эта ошибка может быть также вызвана неустранимым сбоем, который возникает при каждой попытке запуска базы данных. Для выяснения причины проверьте журнал событий Windows, в котором должна содержаться предшествующая ошибка, которая указывает на конкретный сбой.  
  
 Чтобы получить сведения о причине возникновения ошибки 3414, проверьте журнал событий Windows на наличие предыдущего сообщения об ошибке, в котором указан конкретный сбой. Соответствующее действие пользователя зависит от того, что указывают сведения в журнале событий Windows: ошибка [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] была вызвана временным состоянием или неустранимым сбоем. Сведения о действиях пользователя по устранению ошибки 3414 приведены в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также:  
 [&#41;Transact-SQL ALTER DATABASE &#40;](/sql/t-sql/statements/alter-database-transact-sql)   
 [DBCC CHECKDB &#40;&#41;Transact-SQL](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)   
 [Полное восстановление базы данных &#40;простой модели восстановления&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md)   
 [MSSQLSERVER_824](mssqlserver-824-database-engine-error.md)   
 [sys.databases (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
