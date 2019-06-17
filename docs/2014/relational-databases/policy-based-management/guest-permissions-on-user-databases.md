---
title: Разрешения гостя для пользовательских баз данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 540f1c6d-df51-497e-958a-3a0f429d2920
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 325242c6660aa49c9358399b38c92d72e21aaf46
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62705121"
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
  
  
