---
title: MSSQL_ENG020596 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020596 error
ms.assetid: fa33627c-2e99-4be3-9424-52ab83446e07
caps.latest.revision: 13
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2a05b9dc595bf27d2912c13792702f680b67a6be
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37179671"
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
 У вас нет необходимых разрешений на удаление агента для анонимной подписки. Имя входа, используемое при вызове [sp_dropanonymousagent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropanonymousagent-transact-sql), должно принадлежать члену предопределенной роли сервера **sysadmin** на распространителе, или предопределенной роли базы данных **db_owner** в базе данных распространителя, или пользователю, который выполнял первый запуск этого агента.  
  
## <a name="user-action"></a>Действие пользователя  
 Войдите в систему с соответствующими учетными данными и выполните **sp_dropanonymousagent**.  
  
## <a name="see-also"></a>См. также  
 [Справочник по ошибкам и событиям (репликация)](errors-and-events-reference-replication.md)  
  
  
