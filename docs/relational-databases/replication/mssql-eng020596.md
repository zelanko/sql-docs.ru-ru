---
title: MSSQL_ENG020596 | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020596 error
ms.assetid: fa33627c-2e99-4be3-9424-52ab83446e07
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 7303f13493dd559fb6ee840d1d05e075980c21d6
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "76286057"
---
# <a name="mssql_eng020596"></a>MSSQL_ENG020596
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
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
  
  
