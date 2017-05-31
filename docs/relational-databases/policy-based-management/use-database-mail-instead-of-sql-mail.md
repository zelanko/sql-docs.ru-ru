---
title: "Использование компонента Database Mail вместо службы SQL Mail | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: b08df7be-d8be-4184-a661-38ec0ac85cd1
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 81e3e1ee2e090e7c87ad910430846be372f9267e
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="use-database-mail-instead-of-sql-mail"></a>Использование компонента Database Mail вместо службы SQL Mail
  Это правило проверяет представление каталога sys.configurations, чтобы определить, включен ли серверный параметр конфигурации SQL Mail XPs (значение ON).  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Служба SQL Mail будет исключена из будущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Чтобы отправить почту, используйте компонент Database Mail.  
  
 Компонент SQL Mail выполняется внутри службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . При сбое службы SQL Mail сервер также выходит из строя. Компонент Database Mail выполняется вне [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , в отдельном процессе. Он является масштабируемым и не требует установки клиентских компонентов Extended MAPI на рабочем сервере.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
