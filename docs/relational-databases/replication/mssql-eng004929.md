---
title: MSSQL_ENG004929 | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG004929 error
ms.assetid: 1d9b1d88-1fbf-4089-b392-687d3b0220ca
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 0a9300f76bb5447866a4de8d79b1b89492e4a197
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68766700"
---
# <a name="mssqleng004929"></a>MSSQL_ENG004929
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
    
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
  
  
