---
title: "MSSQLSERVER_21871 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 21871 (Database Engine error)
ms.assetid: d3215378-9282-444f-a18b-00b96fd0133d
caps.latest.revision: 6
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 1538eba494fcad374dd0454ed519777466317b0f
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver21871"></a>MSSQLSERVER_21871
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|21871|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SQLErrorNum21871|  
|Текст сообщения|Издатель %s базы данных %s не перенаправлен.|  
  
## <a name="explanation"></a>Объяснение  
**sp_validate_replica_hosts_as_publishers** ищет в таблице MSredirected_publishers, хранящейся в базе данных распространителя, записи о найденном издателе и базе данных издателя.  **sp_validate_replica_hosts_as_publishers** возвращает ошибку 21871, если запись не будет найдена.  
  
## <a name="user-action"></a>Действие пользователя  
**sp_validate_replica_hosts_as_publishers** применима только для перенаправляемых издателей. Если база данных издателя является членом группы доступности, воспользуйтесь хранимой процедурой **sp_redirect_publisher**, чтобы связать издателя и базу данных издателя с именем прослушивателя группы доступности из соответствующей группы доступности.  
  

