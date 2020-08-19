---
description: Использование компонента Database Mail вместо службы SQL Mail
title: Использование компонента Database Mail вместо службы SQL Mail | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: b08df7be-d8be-4184-a661-38ec0ac85cd1
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 342e330cc283d3a639e4145920c678084db846b9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88448237"
---
# <a name="use-database-mail-instead-of-sql-mail"></a>Использование компонента Database Mail вместо службы SQL Mail
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Это правило проверяет представление каталога sys.configurations, чтобы определить, включен ли серверный параметр конфигурации SQL Mail XPs (значение ON).  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Служба SQL Mail будет исключена из будущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Чтобы отправить почту, используйте компонент Database Mail.  
  
 Компонент SQL Mail выполняется внутри службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . При сбое службы SQL Mail сервер также выходит из строя. Компонент Database Mail выполняется вне [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , в отдельном процессе. Он является масштабируемым и не требует установки клиентских компонентов Extended MAPI на рабочем сервере.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
