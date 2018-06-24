---
title: Использование компонента Database Mail вместо службы SQL Mail | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: b08df7be-d8be-4184-a661-38ec0ac85cd1
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7a47bf717a995f1f00cb87cd6bad9a2e01db53d7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193765"
---
# <a name="use-database-mail-instead-of-sql-mail"></a>Использование компонента Database Mail вместо службы SQL Mail
  Это правило проверяет представление каталога sys.configurations, чтобы определить, включен ли серверный параметр конфигурации SQL Mail XPs (значение ON).  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Служба SQL Mail будет исключена из будущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Чтобы отправить почту, используйте компонент Database Mail.  
  
 Компонент SQL Mail выполняется внутри службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . При сбое службы SQL Mail сервер также выходит из строя. Компонент Database Mail выполняется вне [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , в отдельном процессе. Он является масштабируемым и не требует установки клиентских компонентов Extended MAPI на рабочем сервере.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Database Mail](../database-mail/database-mail.md)  
  
## <a name="see-also"></a>См. также  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  