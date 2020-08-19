---
description: MSSQLSERVER_3181
title: MSSQLSERVER_3181 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3181 (Database Engine error)
ms.assetid: e6d2e716-5263-477c-ad0e-7bcbfef4c1f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 13f30437951352cc034b7cdc5b96d3c98b359941
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476116"
---
# <a name="mssqlserver_3181"></a>MSSQLSERVER_3181
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Идентификатор события|3181|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|LDDB_STORAGE_VERIFY|  
|Текст сообщения|Попытка восстановления из этой резервной копии может привести к недостатку места на диске. Подробные сведения будут приведены в следующих сообщениях.|  
  
## <a name="explanation"></a>Объяснение  
Инструкция RESTORE VERIFYONLY проверяет доступное место на диске, где будет восстанавливаться база данных.  
  
### <a name="possible-causes"></a>Возможные причины  
Может быть, недостаточно места на диске для восстановления проверяемой резервной копии.  
  
## <a name="user-action"></a>Действие пользователя  
Восстановить резервную копию в расположении, где достаточно места на диске, либо обеспечить больше места на диске.  
  
## <a name="see-also"></a>См. также:  
[Восстановление базы данных в новом расположении (SQL Server)](~/relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)  
[Восстановление файлов в новое место (SQL Server)](~/relational-databases/backup-restore/restore-files-to-a-new-location-sql-server.md)  
[RESTORE (Transact-SQL)](~/t-sql/statements/restore-statements-transact-sql.md)  
[RESTORE VERIFYONLY (Transact-SQL)](~/t-sql/statements/restore-statements-verifyonly-transact-sql.md)  
  
