---
title: Категория заданий доставки журналов агент SQL Server приводит к сбою обновления | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server Agent]
- job categories [SQL Server Agent]
ms.assetid: ef05ce53-c6ce-42ec-9df8-46c951626424
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7145d846657613b50706ebe75c9832f40f49383e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66092042"
---
# <a name="sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail"></a>Категория заданий доставки журналов агента SQL Server приводит к ошибке обновления
  Процесс обновления закончится ошибкой, если категория задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с именем «Доставка журналов» существует.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Субагент  
  
## <a name="description"></a>Description  
 Существует системная категория заданий «Доставка журналов». Если в обновляемой установке уже содержится созданная пользователем категория задания с именем «Доставка журналов», необходимо переименовать категорию задания перед обновлением; в противном случае процесс обновления завершится неуспешно.  
  
## <a name="see-also"></a>См. также:  
 [Доставка журналов не будет выполняться после обновления](../../../2014/sql-server/install/log-shipping-will-not-run-after-upgrading.md)   
 [При обновлении агент SQL Server учетная запись-посредник пользователя изменится на временную UpgradedProxyAccount](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md)   
 [Проблемы обновления агента SQL Server](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
