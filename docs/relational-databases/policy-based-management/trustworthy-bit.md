---
title: Бит доверия | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3198188a-2b59-4865-9560-10f760934b8e
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: f6a30012675c45688e49e8d32524b060de869908
ms.sourcegitcommit: ef6e3ec273b0521e7c79d5c2a4cb4dcba1744e67
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/10/2018
ms.locfileid: "51512599"
---
# <a name="trustworthy-bit"></a>Бит доверия
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Это правило определяет, назначена ли роль базы данных dbo предопределенной роли сервера sysadmin и установлен ли бит доверия базы данных (значение ON).  
  
 Если эти условия выполняются, привилегированный пользователь базы данных может повысить право доступа до роли sysadmin. Члены этой роли могут создавать и выполнять небезопасные сборки, которые представляют угрозу для системы.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Сбросьте бит доверия или отмените разрешения sysadmin из роли базы данных dbo.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
