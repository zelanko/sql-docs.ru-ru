---
title: MSSQLSERVER_1458 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 1458 (Database Engine error)
ms.assetid: adc78c59-a6f2-432b-9a07-fdd1dc2b9026
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 75bd002a0834c5d8bd3b43407f4ba2d156f2ce0d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver1458"></a>MSSQLSERVER_1458
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|1458|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBM_FAILREDO_ON_PRIMARY|  
|Текст сообщения|В основной копии базы данных «%.*ls» обнаружена ошибка %d, состояние %d, серьезность %d. Зеркальное отображение базы данных приостановлено. Попробуйте устранить причины ошибки и возобновите зеркальное отображение.|  
  
## <a name="explanation"></a>Объяснение  
Это сообщение указывает, что в основной базе данных произошла ошибка, вызвавшая временную приостановку зеркального отображения базы данных.  
  
## <a name="user-action"></a>Действие пользователя  
В большинстве случаев ошибка устраняется без вмешательства пользователя. Если проблема будет повторяться, то рекомендуется перезапустить базу данных или экземпляр сервера. Дополнительные сведения см. в журнале ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на всех участниках, где произошла ошибка, предшествующая сообщению.  
  
## <a name="see-also"></a>См. также:  
[Мониторинг зеркального отображения базы данных (SQL Server)](~/database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)  
  
