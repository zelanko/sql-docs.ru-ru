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
ms.openlocfilehash: c63c98eda9ef0827919bfe36f3a2b14ef717f648
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68021499"
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
  
  
