---
title: Стойкость пароля для входа (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: b0862c3a-926b-490c-a37f-382e50146a3e
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 58daac31e06f6a1b8120e2848452d9660c7bbe3c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774143"
---
# <a name="sql-server-login-password-strength"></a>Стойкость пароля имени входа SQL Server
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Это правило проверяет, установлен ли флажок «Требовать использование политики паролей» для каждого имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Если включена проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , а версия операционной системы младше [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)], злоумышленник может многократно использовать известный ему пароль имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Рекомендуется обновить операционную систему до [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)].  
  
 Если в определенной среде не требуется проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , следует использовать проверку подлинности Windows.  
  
 Следует установить флажок «Требовать использование политики паролей» для всех имен входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Для настройки политики паролей для имени входа [используется инструкция](../../t-sql/statements/alter-login-transact-sql.md) ALTER LOGIN [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Политика паролей](../../relational-databases/security/password-policy.md)  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
