---
title: MSSQLSERVER_32042 | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 32042 (Database Engine error)
ms.assetid: 53a51c7a-dcd4-4c15-b4d2-6aaa9dce76da
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2dc82f65ed2044ac5edc324e78d743dd6b6e9622
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100634"
---
# <a name="mssqlserver32042"></a>MSSQLSERVER_32042
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|32042|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SQLErrorNum32042|  
|Текст сообщения|Было активировано предупреждение «unsent log». Текущее значение «%d» превосходит пороговое значение «%d».|  
  
## <a name="explanation"></a>Объяснение  
 Это событие зеркального отображения базы данных произошло на экземпляре основного сервера и указывает, что объем неотправленного журнала достиг указанного пользователем порогового значения. Обычно причиной этого события становится изменение показателей производительности системы. Либо уменьшилась пропускная способность между двумя системами, либо возросла нагрузка.  
  
 Объем неотправленного журнала — это показатель производительности, позволяющий оценить вероятность потери данных в зависимости от объема (в килобайтах) неотправленного журнала. Эта метрика особенно важна для сеансов, выполняемых в высокопроизводительном режиме. Однако она также важна для сеансов режима высокого уровня безопасности, когда зеркальное отображение приостанавливается или откладывается из-за потери соединения между участниками.  
  
## <a name="user-action"></a>Действие пользователя  
 Проверьте, не является ли причиной ошибки уровень нагрузки на экземпляр основного или зеркального серверов или сетевое соединение между ними.  
  
## <a name="see-also"></a>См. также  
 [Зеркальное отображение базы данных (SQL Server)](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [Использование пороговых значений предупреждений и оповещений в метриках производительности зеркального отображения (SQL Server)](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)  
  
  