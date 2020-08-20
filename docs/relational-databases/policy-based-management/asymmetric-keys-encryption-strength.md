---
description: Стойкость шифрования асимметричных ключей
title: Стойкость асимметричных ключей шифрования | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 235ff2ab-1c5a-45c7-a91b-9db69b958b60
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 193f18868c3e5d3afad51a304ab5f19836dfb1d1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88490697"
---
# <a name="asymmetric-keys-encryption-strength"></a>Стойкость шифрования асимметричных ключей
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Это правило проверяет, были ли созданы асимметричные ключи с применением 1024-битного шифрования или более стойкого.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Для создания асимметричных ключей для шифрования данных применяйте 1024-разрядный алгоритм шифрования RSA или более стойкий.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Выбор алгоритма шифрования](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
