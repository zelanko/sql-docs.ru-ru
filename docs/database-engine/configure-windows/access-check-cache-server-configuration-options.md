---
title: Параметры конфигурации сервера "access check cache" | Документы Майкрософт
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- access check cache option
ms.assetid: 0a992ea8-3ec6-4a4d-97b5-460ae7326247
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.openlocfilehash: cc290a3fbde8426c1728a03b4ec9ddeaf4d5144f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66782483"
---
# <a name="access-check-cache-server-configuration-options"></a>Параметры конфигурации сервера «access check cache»
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  При доступе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]к объектам базы данных проверка доступа кэшируется во внутренней структуре, которую называют **кэшем результатов проверки доступа**. Параметры **access check cache quota** и **access check cache bucket count** управляют количеством записей и числом сегментов хэша, которые используются в **кэше результатов проверки доступа**. В редких случаях можно добиться увеличения производительности, изменив эти параметры.  
  
 Значение по умолчанию 0 указывает на то, что этими параметрами управляет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Майкрософт рекомендует изменять эти параметры только под руководством службы поддержки пользователей Майкрософт.  
  
## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
