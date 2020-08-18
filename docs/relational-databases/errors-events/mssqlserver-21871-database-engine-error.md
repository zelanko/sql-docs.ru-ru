---
description: MSSQLSERVER_21871
title: MSSQLSERVER_21871 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 21871 (Database Engine error)
ms.assetid: d3215378-9282-444f-a18b-00b96fd0133d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 52f82fbebc9f164152f6047a90bbb1238e1a2bb7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88332790"
---
# <a name="mssqlserver_21871"></a>MSSQLSERVER_21871
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|21871|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SQLErrorNum21871|  
|Текст сообщения|Издатель %s базы данных %s не перенаправлен.|  
  
## <a name="explanation"></a>Объяснение  
**sp_validate_replica_hosts_as_publishers** ищет в таблице MSredirected_publishers, хранящейся в базе данных распространителя, записи о найденном издателе и базе данных издателя.  **sp_validate_replica_hosts_as_publishers** возвращает ошибку 21871, если запись не будет найдена.  
  
## <a name="user-action"></a>Действие пользователя  
**sp_validate_replica_hosts_as_publishers** применима только для перенаправляемых издателей. Если база данных издателя является членом группы доступности, воспользуйтесь хранимой процедурой **sp_redirect_publisher**, чтобы связать издателя и базу данных издателя с именем прослушивателя группы доступности из соответствующей группы доступности.  
  
