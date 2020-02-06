---
title: MSSQL_ENG014144 | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014144 error
ms.assetid: fdc744d5-530e-48c4-9420-cca032fd482b
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: c43395fffe934756bb69e0d094a3e6637adcedad
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "76286511"
---
# <a name="mssql_eng014144"></a>MSSQL_ENG014144
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|14144|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Невозможно удалить подписчик '%s'. В базе данных публикации '%s' для него есть подписки.|  
  
## <a name="explanation"></a>Объяснение  
 Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , настроенный в качестве подписчика, не может быть удален из роли подписчика до тех пор, пока есть активные подписки, настроенные для данного экземпляра.  
  
## <a name="user-action"></a>Действие пользователя  
 Удалите все связанные подписки, прежде чем пытаться изменить состояние подписчика для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
1.  Выполните [sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md) в базе данных публикации в издателе, чтобы найти подписки.  
  
2.  Выполните [sp_dropsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md) в базе данных публикации в издателе, чтобы удалить подписки.  

## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
