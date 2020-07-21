---
title: MSSQLSERVER_3181 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3181 (Database Engine error)
ms.assetid: e6d2e716-5263-477c-ad0e-7bcbfef4c1f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3aca70f5f13ba81ae240abcc1e63fdf60b31e72d
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551769"
---
# <a name="mssqlserver_3181"></a>MSSQLSERVER_3181
    
## <a name="details"></a>Сведения  
  
|attribute|Значение|  
|-|-|  
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
 [Восстановление базы данных в новое место (SQL Server)](../backup-restore/restore-a-database-to-a-new-location-sql-server.md)   
 [Восстановление файлов в новое расположение &#40;SQL Server&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md)   
 [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql)   
 [RESTORE VERIFYONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)  
  
  
