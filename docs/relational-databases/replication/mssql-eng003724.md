---
title: "MSSQL_ENG003724 | Документация Майкрософт"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG003724 error
ms.assetid: 10cb119d-92df-4124-b85d-cd2f2666c99c
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d97300f400557643da18e81201136649d629b681
ms.lasthandoff: 04/11/2017

---
# <a name="mssqleng003724"></a>MSSQL_ENG003724
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|3724|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Невозможно %S_MSG %S_MSG "%.*ls", так как она используется для репликации.|  
  
## <a name="explanation"></a>Объяснение  
 При репликации объектов в базе данных они помечаются как реплицированные в системной таблице **sysarticles** (для моментального снимка и публикаций транзакций) или **sysmergearticles** (для публикаций слиянием). При попытке удалить реплицированный объект возникает данная ошибка.  
  
## <a name="user-action"></a>Действие пользователя  
 Убедитесь в том, что объект базы данных не подвергался репликации, прежде чем предпримете попытку удалить его. Например:  
  
-   Если данная ошибка появляется в базе данных публикации, удалите статью из публикации, прежде чем удалить объект. Дополнительные сведения см. в статье [Добавление и удаление статей в существующих публикациях](../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
-   Если данная ошибка появляется в базе данных подписки, удалите подписку, прежде чем удалить объект. Дополнительные сведения см. в статье [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md). Для подписок на публикации транзакций имеется возможность удаления подписки на отдельную статью вместо удаления всей публикации. Дополнительные сведения см. в разделе [sp_dropsubscription (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md).  
  
 При возникновении ошибки в нереплицированной базе данных запустите [sp_removedbreplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md), чтобы снять все отметки о репликации для объектов базы данных.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
