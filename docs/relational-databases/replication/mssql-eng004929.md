---
title: "MSSQL_ENG004929 | Документация Майкрософт"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MSSQL_ENG004929 error
ms.assetid: 1d9b1d88-1fbf-4089-b392-687d3b0220ca
caps.latest.revision: "14"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 84c2b4d77277b2d63c652dc5c4f02625921e2f46
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="mssqleng004929"></a>MSSQL_ENG004929
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|4929|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Невозможно изменить %S_MSG "%.*ls", так как выполняется публикация для репликации.|  
  
## <a name="explanation"></a>Объяснение  
 Указанная ошибка обычно возникает при попытке удалить ограничение первичного ключа, действующее в отношении таблицы, опубликованной для репликации транзакций. Репликация транзакций требует первичный ключ для каждой опубликованной таблицы; следовательно, ограничение нельзя удалить.  
  
## <a name="user-action"></a>Действие пользователя  
 Чтобы удалить ограничение, сначала удалите статью, связанную с таблицей. Дополнительные сведения см. в статье [Добавление и удаление статей в существующих публикациях](../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md). При возникновении ошибки в нереплицированной базе данных запустите [sp_removedbreplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md), чтобы снять все отметки о репликации для объектов базы данных.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
