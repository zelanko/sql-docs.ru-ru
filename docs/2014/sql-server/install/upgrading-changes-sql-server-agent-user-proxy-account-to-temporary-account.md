---
title: Обновление приведет к изменению учетная запись прокси-сервера для агента пользователя SQL Server для временной UpgradedProxyAccount | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- log shipping [SQL Server Agent]
ms.assetid: cd2d08c3-4e56-4034-8b68-0c78df8b5471
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9bae867b97a9fc63b97506fd8900e68b670b8013
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087761"
---
# <a name="upgrading-will-change-the-sql-server-agent-user-proxy-account-to-the-temporary-upgradedproxyaccount"></a>При обновлении пользовательская учетная запись-посредник агента SQL Server изменится на временную учетную запись-посредник UpgradedProxyAccount
  Планы обслуживания базы данных с доставкой журналов не будут включены после обновления.  
  
## <a name="component"></a>Компонент  
 Агент[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]   
  
## <a name="description"></a>Описание  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет новый набор функций доставки журналов, которые несовместимы напрямую с планами обслуживания баз данных.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Пользователи [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], которые используют планы обслуживания баз данных, содержащие функции доставки журналов, должны настроить доставку журналов с использованием этих новых функций. Дополнительные сведения можно получить, осуществив поиск слов «доставка журналов» в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Категория заданий доставки журналов агента SQL Server приводит к ошибке обновления](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md)   
 [Доставка журналов перестанет работать после обновления](../../../2014/sql-server/install/log-shipping-will-not-run-after-upgrading.md)  
  
  