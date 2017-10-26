---
title: "Бит доверия | Документация Майкрософт"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3198188a-2b59-4865-9560-10f760934b8e
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: fd48f1b47ccd84ba2eea67323483160c7c226624
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="trustworthy-bit"></a>Бит доверия
  Это правило определяет, назначена ли роль базы данных dbo предопределенной роли сервера sysadmin и установлен ли бит доверия базы данных (значение ON).  
  
 Если эти условия выполняются, привилегированный пользователь базы данных может повысить право доступа до роли sysadmin. Члены этой роли могут создавать и выполнять небезопасные сборки, которые представляют угрозу для системы.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Сбросьте бит доверия или отмените разрешения sysadmin из роли базы данных dbo.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  

