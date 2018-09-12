---
title: Бит доверия | Документация Майкрософт
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
ms.assetid: 3198188a-2b59-4865-9560-10f760934b8e
caps.latest.revision: 9
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 916f12d9336c378a738d799b3e26b6d4a3792cc8
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43809340"
---
# <a name="trustworthy-bit"></a>Бит доверия
  Это правило определяет, назначена ли роль базы данных dbo предопределенной роли сервера sysadmin и установлен ли бит доверия базы данных (значение ON).  
  
 Если эти условия выполняются, привилегированный пользователь базы данных может повысить право доступа до роли sysadmin. Члены этой роли могут создавать и выполнять небезопасные сборки, которые представляют угрозу для системы.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Сбросьте бит доверия или отмените разрешения sysadmin из роли базы данных dbo.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)  
  
## <a name="see-also"></a>См. также  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
