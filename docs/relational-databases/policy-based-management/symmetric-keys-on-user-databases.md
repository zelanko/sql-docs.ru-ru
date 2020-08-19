---
description: Симметричные ключи в пользовательских базах данных
title: Симметричные ключи в пользовательских базах данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3333ab5b-2518-4753-a0a8-57df5e5af74f
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: c7882b4f3f425b600e3ef57fa836ffffd6756289
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88380970"
---
# <a name="symmetric-keys-on-user-databases"></a>Симметричные ключи в пользовательских базах данных
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Это правило проверяет, используют ли симметричные ключи длиной менее 128 бит алгоритмы шифрования RC2 или RC4.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 При создании симметричных ключей для шифрования данных используйте 128-битный алгоритм AES. Если алгоритм AES не поддерживается в операционной системе, следует применять алгоритм 3DES.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Выбор алгоритма шифрования](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
