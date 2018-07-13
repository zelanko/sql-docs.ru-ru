---
title: MSSQL_ENG004929 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG004929 error
ms.assetid: 1d9b1d88-1fbf-4089-b392-687d3b0220ca
caps.latest.revision: 13
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b3d66948ad92e18fed77002f956cac9af07c04b7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37186101"
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
 Чтобы удалить ограничение, сначала удалите статью, связанную с таблицей. Дополнительные сведения см. в статье [Добавление и удаление статей в существующих публикациях](publish/add-articles-to-and-drop-articles-from-existing-publications.md). При возникновении ошибки в нереплицированной базе данных запустите [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql), чтобы снять все отметки о репликации для объектов базы данных.  
  
## <a name="see-also"></a>См. также  
 [Справочник по ошибкам и событиям (репликация)](errors-and-events-reference-replication.md)  
  
  
