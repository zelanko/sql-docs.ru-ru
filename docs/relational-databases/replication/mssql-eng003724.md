---
title: MSSQL_ENG003724 | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG003724 error
ms.assetid: 10cb119d-92df-4124-b85d-cd2f2666c99c
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 2851a66bb4e9bdefec848d1671bdc88759c35142
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "76286321"
---
# <a name="mssql_eng003724"></a>MSSQL_ENG003724
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|3724|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Невозможно %S_MSG %S_MSG "%.*ls", так как она используется для репликации.|  
  
## <a name="explanation"></a>Объяснение  
 При репликации объектов в базе данных они помечаются как реплицированные в системной таблице **sysarticles** (для моментального снимка и публикаций транзакций) или **sysmergearticles** (для публикаций слиянием). При попытке удалить реплицированный объект возникает данная ошибка.  
  
## <a name="user-action"></a>Действие пользователя  
 Убедитесь в том, что объект базы данных не подвергался репликации, прежде чем предпримете попытку удалить его. Пример:  
  
-   Если данная ошибка появляется в базе данных публикации, удалите статью из публикации, прежде чем удалить объект. Дополнительные сведения см. в статье [Добавление и удаление статей в существующих публикациях](../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
-   Если данная ошибка появляется в базе данных подписки, удалите подписку, прежде чем удалить объект. Дополнительные сведения см. в статье [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md). Для подписок на публикации транзакций имеется возможность удаления подписки на отдельную статью вместо удаления всей публикации. Дополнительные сведения см. в разделе [sp_dropsubscription (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md).  
  
 При возникновении ошибки в нереплицированной базе данных запустите [sp_removedbreplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md), чтобы снять все отметки о репликации для объектов базы данных.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
