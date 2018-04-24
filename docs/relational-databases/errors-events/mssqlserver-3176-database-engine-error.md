---
title: MSSQLSERVER_3176 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 3176 (Database Engine error)
ms.assetid: 4be24c64-2d52-4cb4-b4d7-36efbe4555b6
caps.latest.revision: 12
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b5777c53222b9cfdbf0de69466e07ef9a9f9d78a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver3176"></a>MSSQLSERVER_3176
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Идентификатор события|3176|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|LDDB_FILE_CLAIM|  
|Текст сообщения|Файл «%ls» запрошен «%ls»(%d) и «%ls»(%d). Переместить один или несколько файлов можно с помощью предложения WITH MOVE.|  
  
## <a name="explanation"></a>Объяснение  
Попытка использовать файл для нескольких целей.  
  
### <a name="possible-causes"></a>Возможные причины  
В другой базе данных уже используется это имя файла.  
  
## <a name="user-action"></a>Действие пользователя  
Восстановите файлы базы данных в другое место. Переместите каждый файл с помощью предложения WITH MOVE инструкции RESTORE. В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] измените расположения файлов в сетке **Восстановить файлы базы данных как** диалогового окна **Параметры восстановления базы данных**.  
  
## <a name="see-also"></a>См. также:  
[Восстановление базы данных в новом расположении (SQL Server)](~/relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)  
[Восстановление файлов в новое место (SQL Server)](~/relational-databases/backup-restore/restore-files-to-a-new-location-sql-server.md)  
[RESTORE (Transact-SQL)](~/t-sql/statements/restore-statements-transact-sql.md)  
  
