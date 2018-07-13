---
title: MSSQLSERVER_3176 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 3176 (Database Engine error)
ms.assetid: 4be24c64-2d52-4cb4-b4d7-36efbe4555b6
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f6ecd8482645db1cf8b070de8d82ed0012dae01f
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37417393"
---
# <a name="mssqlserver3176"></a>MSSQLSERVER_3176
    
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
  
## <a name="see-also"></a>См. также  
 [Восстановление базы данных в новое место (SQL Server)](../backup-restore/restore-a-database-to-a-new-location-sql-server.md)   
 [Восстановление файлов в новое расположение &#40;SQL Server&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md)   
 [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
