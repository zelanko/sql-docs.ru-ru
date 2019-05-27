---
title: Обновление приведет к изменению учетная запись прокси-сервера для агента пользователя SQL Server для временного UpgradedProxyAccount | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server Agent]
ms.assetid: cd2d08c3-4e56-4034-8b68-0c78df8b5471
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a82cbcc9ef1ab57279b44cc83509cb1efad855ca
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66091401"
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
  
  
