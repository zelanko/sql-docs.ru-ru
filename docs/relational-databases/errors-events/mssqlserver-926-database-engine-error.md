---
title: MSSQLSERVER_926 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 926 (Database Engine error)
ms.assetid: 57e01668-883b-4be4-84a8-a111caaf0486
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 022706502e3fe96dad1dbdc826dfb4076f024b0f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85636442"
---
# <a name="mssqlserver_926"></a>MSSQLSERVER_926
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|926|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DB_SUSPECT|  
|Текст сообщения|Невозможно открыть базу данных «%.*ls». Она была отмечена как подозрительная (SUSPECT) операцией восстановления. Дополнительные сведения см. в журнале ошибок SQL Server.|  
  
## <a name="explanation"></a>Объяснение  
База данных помечается как подозрительная из-за ошибки в процессе восстановления, который должен переводить ее в согласованное транзакционное состояние. Это может происходить во время следующих операций.  
  
-   Запуск экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Присоединение базы данных.  
  
-   Использование процедур RESTORE и RESTORE LOG.  
  
## <a name="user-action"></a>Действие пользователя  
Проверьте журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и выясните причину ошибки. Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перезапускалась после неуспешного завершения восстановления, найдите предыдущие журналы ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и попробуйте отыскать причину ошибки восстановления.  
  
Если восстановление завершилось неуспешно из-за постоянной ошибки ввода-вывода, обрыва страницы или другой вероятной неполадки оборудования, устраните проблему, связанную с оборудованием, и восстановите базу данных из резервной копии. Если резервные копии недоступны, воспользуйтесь параметрами исправления инструкции DBCC CHECKDB.  
  
Если решить проблему невозможно, обратитесь к основному поставщику услуг по технической поддержке. Убедитесь в наличии журнала ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:  
[Резервное копирование и восстановление баз данных SQL Server](~/relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
[RESTORE (Transact-SQL)](~/t-sql/statements/restore-statements-transact-sql.md)  
[sys.sysdatabases (Transact-SQL)](~/relational-databases/system-compatibility-views/sys-sysdatabases-transact-sql.md)  
[Присоединение и отсоединение базы данных (SQL Server)](~/relational-databases/databases/database-detach-and-attach-sql-server.md)  
  
