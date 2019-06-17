---
title: MSSQLSERVER_3156 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3156 (Database Engine error)
ms.assetid: 345d8ed4-177e-4ec3-bab3-25d30000e323
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2b1c972481b7c4cf614cf0a91b29247c643696d2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62868930"
---
# <a name="mssqlserver3156"></a>MSSQLSERVER_3156
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Идентификатор события|3156|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|LDDB_CANT_WRITE|  
|Текст сообщения|Невозможно восстановить файл «%ls» до «%ls». Укажите допустимое расположение для файла с помощью предложения WITH MOVE.|  
  
## <a name="explanation"></a>Объяснение  
 Это общее сообщение идентифицирует логические или физические имена файлов, которые не удалось восстановить из-за ошибок в заданном расположении.  
  
### <a name="possible-causes"></a>Возможные причины  
 Ниже приведены возможные причины.  
  
-   Возможно, необходим доступ к указанному каталогу Windows.  
  
-   Возможно, введен или указан несуществующий путь.  
  
-   Указано имя файла, который недоступен для перезаписи.  
  
## <a name="user-action"></a>Действие пользователя  
 Найдите в журналах ошибок другие сообщения, содержащие дополнительные сведения.  
  
 Устраните неполадку, связанную с указанным расположением. Для этого, например, предоставьте необходимые права доступа или измените расположение файла с помощью параметра WITH MOVE предложения RESTORE.  
  
## <a name="see-also"></a>См. также  
 [Восстановление базы данных в новое место (SQL Server)](../backup-restore/restore-a-database-to-a-new-location-sql-server.md)   
 [Восстановление файлов в новое расположение &#40;SQL Server&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md)   
 [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
