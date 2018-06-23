---
title: Категория заданий доставки журналов агента SQL Server приводит к ошибке обновления | Документы Microsoft
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
- job categories [SQL Server Agent]
ms.assetid: ef05ce53-c6ce-42ec-9df8-46c951626424
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 47d7d5024d234478b8b54e3c05b3c22335758782
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100997"
---
# <a name="sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail"></a>Категория заданий доставки журналов агента SQL Server приводит к ошибке обновления
  Процесс обновления закончится ошибкой, если категория задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с именем «Доставка журналов» существует.  
  
## <a name="component"></a>Компонент  
 Агент[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]   
  
## <a name="description"></a>Описание  
 Существует системная категория заданий «Доставка журналов». Если в обновляемой установке уже содержится созданная пользователем категория задания с именем «Доставка журналов», необходимо переименовать категорию задания перед обновлением; в противном случае процесс обновления завершится неуспешно.  
  
## <a name="see-also"></a>См. также  
 [Доставка журналов перестанет работать после обновления](../../../2014/sql-server/install/log-shipping-will-not-run-after-upgrading.md)   
 [Обновление приведет к изменению учетная запись прокси-сервера для агента пользователя SQL Server для временной UpgradedProxyAccount](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md)   
 [Проблемы обновления агента SQL Server](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  