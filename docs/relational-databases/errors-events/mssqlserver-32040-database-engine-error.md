---
title: MSSQLSERVER_32040 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 32040 (Database Engine error)
ms.assetid: 709219b1-f8b2-4696-8923-dd2e91492eb8
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6b67f857344e143850f50839398b4b458f6ba779
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver32040"></a>MSSQLSERVER_32040
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|32040|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SQLErrorNum32040|  
|Текст сообщения|Активировано предупреждение «Самая старая неотправленная транзакция». Текущее значение «%d» превосходит пороговое значение «%d».|  
  
## <a name="explanation"></a>Объяснение  
Это событие зеркального отображения базы данных происходит на экземпляре основного сервера и указывает, что возраст самой старой неотправленной транзакции достиг указанного пользователем порогового значения. Обычно причиной этого события становится изменение показателей производительности системы. Либо уменьшилась пропускная способность между двумя системами, либо возросла нагрузка.  
  
Возраст самой старой неотправленной транзакции представляет собой показатель производительности, который позволяет оценить вероятность утери данных в зависимости от длительности (в минутах) неотправленных транзакций. Эта метрика особенно важна для сеансов, выполняемых в высокопроизводительном режиме. Однако она также важна для сеансов режима высокого уровня безопасности, когда зеркальное отображение приостанавливается или откладывается из-за потери соединения между участниками.  
  
## <a name="user-action"></a>Действие пользователя  
Проверьте, не является ли причиной ошибки уровень нагрузки на экземпляр основного или зеркального серверов или сетевое соединение между ними.  
  
## <a name="see-also"></a>См. также:  
[Зеркальное отображение базы данных (SQL Server)](~/database-engine/database-mirroring/database-mirroring-sql-server.md)  
[Использование пороговых значений предупреждений и оповещений в метриках производительности зеркального отображения (SQL Server)](~/database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)  
  
