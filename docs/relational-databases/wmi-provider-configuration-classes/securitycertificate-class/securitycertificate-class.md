---
title: Класс SecurityCertificate
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
apiname:
- SecurityCertificate Class
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SecurityCertificate class
ms.assetid: d772da67-e04e-4499-9f80-7a5e94829b5c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2153724ef3e8a7ea31c2b99c344c6f824318a982
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85888801"
---
# <a name="securitycertificate-class"></a>Класс SecurityCertificate
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Класс [SecurityCertificate Class](../../../relational-databases/wmi-provider-configuration-classes/securitycertificate-class/securitycertificate-class.md) представляет сертификат безопасности. Сертификат — это подписанная цифровой подписью инструкция, которая привязывает значение открытого ключа к экземпляру [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , который содержит соответствующий закрытый ключ. Сертификат выдается центром сертификации.  
  
 Работая с классом [SecurityCertificate](../../../relational-databases/wmi-provider-configuration-classes/securitycertificate-class/securitycertificate-class.md), можно выполнять следующие задачи:  
  
-   просматривать свойства сертификата безопасности;  
  
-   устанавливать сертификат безопасности с заданным SHA-отпечатком для указанного экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)];  
  
-   проверять SHA-отпечаток для указанного экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Иерархия шифрования](../../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
