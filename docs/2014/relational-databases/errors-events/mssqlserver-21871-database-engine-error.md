---
title: MSSQLSERVER_21871 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 21871 (Database Engine error)
ms.assetid: d3215378-9282-444f-a18b-00b96fd0133d
caps.latest.revision: 7
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 910fc06aac87eb846c0db76956eb45377fa3ecdb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100011"
---
# <a name="mssqlserver21871"></a>MSSQLSERVER_21871
    
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
 `sp_validate_replica_hosts_as_publishers` Проверка MSredirected_publishers таблицы в базе данных распространителя запись идентифицированного издателя и базы данных издателя.  `sp_validate_replica_hosts_as_publishers` возвращает ошибку 21871, если запись не будет найдена.  
  
## <a name="user-action"></a>Действие пользователя  
 `sp_validate_replica_hosts_as_publishers` относится только к перенаправляемым издателям. Если база данных издателя является членом группы доступности, воспользуйтесь хранимой процедурой `sp_redirect_publisher`, чтобы связать издателя и базу данных издателя с именем прослушивателя группы доступности соответствующей группы доступности.  
  
  