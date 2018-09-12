---
title: Симметричные ключи в пользовательских базах данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3333ab5b-2518-4753-a0a8-57df5e5af74f
caps.latest.revision: 5
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: bc7ad34802993b402d2799767e93c0bccf30203e
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43814710"
---
# <a name="symmetric-keys-on-user-databases"></a>Симметричные ключи в пользовательских базах данных
  Это правило проверяет, используют ли симметричные ключи длиной менее 128 бит алгоритмы шифрования RC2 или RC4.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 При создании симметричных ключей для шифрования данных используйте 128-битный алгоритм AES. Если алгоритм AES не поддерживается в операционной системе, следует применять алгоритм 3DES.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Выбор алгоритма шифрования](../security/encryption/choose-an-encryption-algorithm.md)  
  
## <a name="see-also"></a>См. также  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
