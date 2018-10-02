---
title: MSSQLSERVER_3156 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3156 (Database Engine error)
ms.assetid: 345d8ed4-177e-4ec3-bab3-25d30000e323
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b10bd409a52708e69ef9ae3ad8cf629d73b446dd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47670682"
---
# <a name="mssqlserver3156"></a>MSSQLSERVER_3156
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  
## <a name="see-also"></a>См. также:  
[Восстановление базы данных в новом расположении (SQL Server)](~/relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)  
[Восстановление файлов в новое место (SQL Server)](~/relational-databases/backup-restore/restore-files-to-a-new-location-sql-server.md)  
[RESTORE (Transact-SQL)](~/t-sql/statements/restore-statements-transact-sql.md)  
  
