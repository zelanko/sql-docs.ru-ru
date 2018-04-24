---
title: Параметры конфигурации сервера "access check cache" | Документы Майкрософт
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: configure-windows
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- access check cache option
ms.assetid: 0a992ea8-3ec6-4a4d-97b5-460ae7326247
caps.latest.revision: 9
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1c566507fd7d146e88de860660487056901d525f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="access-check-cache-server-configuration-options"></a>Параметры конфигурации сервера «access check cache»
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  При доступе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]к объектам базы данных проверка доступа кэшируется во внутренней структуре, которую называют **кэшем результатов проверки доступа**. Параметры **access check cache quota** и **access check cache bucket count** управляют количеством записей и числом сегментов хэша, которые используются в **кэше результатов проверки доступа**. В редких случаях можно добиться увеличения производительности, изменив эти параметры.  
  
 Значение по умолчанию 0 указывает на то, что этими параметрами управляет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Майкрософт рекомендует изменять эти параметры только под руководством службы поддержки пользователей Майкрософт.  
  
## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
