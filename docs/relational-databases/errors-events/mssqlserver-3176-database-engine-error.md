---
title: MSSQLSERVER_3176 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3176 (Database Engine error)
ms.assetid: 4be24c64-2d52-4cb4-b4d7-36efbe4555b6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 66e63c40acd3cd5cdbaafb19108c6915ccb2fd82
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47649352"
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
  
