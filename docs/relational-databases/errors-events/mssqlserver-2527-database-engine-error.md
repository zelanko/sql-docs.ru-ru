---
title: "MSSQLSERVER_2527 | | Документация Майкрософт"
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
- 2527 (Database Engine error)
ms.assetid: 1cef90ef-9c39-44e6-bc7f-316c8f53c10c
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 14f0f361ec4eefc2d1e232efaf7c899c0151d1f8
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver2527"></a>MSSQLSERVER_2527
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|2527|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC_INDEX_FILEGROUP_IS_OFFLINE|  
|Текст сообщения|Невозможно обработать индекс I_NAME таблицы O_NAME, так как файловая группа F_NAME находится в режиме «вне сети».|  
  
## <a name="explanation"></a>Объяснение  
Это информационное сообщение указывает, что индекс невозможно проверить, поскольку одна из файловых групп, в которой хранятся данные индекса, находится в режиме «вне сети». Состояние файлов в файловой группе определяет доступность всей файловой группы. Чтобы файловая группа была доступна, необходимо, чтобы все файлы в файловой группе находились в режиме в сети. Если других проблем нет, будут проверяться все остальные индексы того же объекта.  
  
## <a name="user-action"></a>Действие пользователя  
Чтобы просмотреть текущее состояние файлов указанной файловой группы, выполните запрос к представлению каталога **sys.database_files** или**sys.master_files**.  
  
Восстановите автономный файл из резервной копии.  
  
## <a name="see-also"></a>См. также:  
[sys.database_files (Transact-SQL)](~/relational-databases/system-catalog-views/sys-database-files-transact-sql.md)  
[sys.master_files &#40;Transact-SQL&#41;](~/relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
[RESTORE (Transact-SQL)](~/t-sql/statements/restore-statements-transact-sql.md)  
  

