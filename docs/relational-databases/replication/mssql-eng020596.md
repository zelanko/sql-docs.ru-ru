---
title: "MSSQL_ENG020596 | Документация Майкрософт"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MSSQL_ENG020596 error
ms.assetid: fa33627c-2e99-4be3-9424-52ab83446e07
caps.latest.revision: "14"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6a0260be11a86a4f311d45e8f69e206af0985048
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="mssqleng020596"></a>MSSQL_ENG020596
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|20596|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Только '%s' или члены роли db_owner могут удалить анонимный агент.|  
  
## <a name="explanation"></a>Объяснение  
 У вас нет необходимых разрешений на удаление агента для анонимной подписки. Имя входа, используемое при вызове [sp_dropanonymousagent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropanonymousagent-transact-sql.md), должно принадлежать члену предопределенной роли сервера **sysadmin** на распространителе, или предопределенной роли базы данных **db_owner** в базе данных распространителя, или пользователю, который выполнял первый запуск этого агента.  
  
## <a name="user-action"></a>Действие пользователя  
 Войдите в систему с соответствующими учетными данными и выполните **sp_dropanonymousagent**.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
