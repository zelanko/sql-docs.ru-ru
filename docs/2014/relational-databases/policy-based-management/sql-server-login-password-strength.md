---
title: Стойкость пароля для входа (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: b0862c3a-926b-490c-a37f-382e50146a3e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1b2c130ace15d6bd4afec307824099c649214e0d
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52823438"
---
# <a name="sql-server-login-password-strength"></a>Стойкость пароля имени входа SQL Server
  Это правило проверяет, установлен ли флажок «Требовать использование политики паролей» для каждого имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Если включена проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , а версия операционной системы младше [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)], злоумышленник может многократно использовать известный ему пароль имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Рекомендуется обновить операционную систему до [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)].  
  
 Если в определенной среде не требуется проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , следует использовать проверку подлинности Windows.  
  
 Следует установить флажок «Требовать использование политики паролей» для всех имен входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Для настройки политики паролей для имени входа [используется инструкция](/sql/t-sql/statements/alter-login-transact-sql) ALTER LOGIN [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Политика паролей](../security/password-policy.md)  
  
## <a name="see-also"></a>См. также  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
