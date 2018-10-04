---
title: Истечение срока действия пароля для входа (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 7e3bf9da-a436-433d-847a-47c30428cad3
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 04f4c766797c2563b595d4c6aa371e0b437d1197
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48145744"
---
# <a name="sql-server-login-password-expiration"></a>Истечение срока действия пароля имени входа SQL Server
  Это правило проверяет, установлен ли флажок «Истечение срока действия паролей» для каждого имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Если включена проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , а версия операционной системы младше [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)], злоумышленник может многократно использовать известный ему пароль имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Рекомендуется обновить операционную систему до [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)].  
  
 Если в определенной среде не требуется проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , следует использовать проверку подлинности Windows. Дополнительные сведения см. в разделе [Выбор режима проверки подлинности](../security/choose-an-authentication-mode.md).  
  
 Следует установить флажок «Истечение срока действия паролей» для всех имен входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Для настройки политики паролей для имени входа [используется инструкция](/sql/t-sql/statements/alter-login-transact-sql) ALTER LOGIN [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Политика паролей](../security/password-policy.md)  
  
## <a name="see-also"></a>См. также  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
