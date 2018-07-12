---
title: Разрешения гостя для пользовательских баз данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 540f1c6d-df51-497e-958a-3a0f429d2920
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 51f08e85c6ebd06c7cfcfb1922312accd8203246
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37230754"
---
# <a name="guest-permissions-on-user-databases"></a>Разрешения гостя для пользовательских баз данных
  Это правило определяет, имеет ли пользователь «Гость» разрешение на доступ к базе данных. Это правило применяется только к пользовательским базам данных.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Отмените разрешения гостя для доступа к базе данных, если оно не требуется.  
  
 Пользователь guest не может быть удален, однако пользователь guest может быть отключен путем отмены его разрешения на CONNECT с помощью инструкции REVOKE CONNECT FROM GUEST в базе данных, отличной от master, tempdb или msdb.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Обеспечение безопасности SQL Server](../security/securing-sql-server.md)  
  
## <a name="see-also"></a>См. также  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
