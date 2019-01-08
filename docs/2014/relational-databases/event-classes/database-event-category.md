---
title: Категория событий Database | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- event classes [SQL Server], Database event category
- Database event category [SQL Server]
- SQL Server event classes, Database event category
ms.assetid: b61af738-f144-4992-b0b2-d44cb7240991
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e0d725f95fc8e9de0865ad895abd860d5f03687b
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52793014"
---
# <a name="database-event-category"></a>Категория событий Database
  В категории событий **База данных** содержатся классы событий для контроля компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Класс событий Data File Auto Grow](data-file-auto-grow-event-class.md)|Указывает на то, что размер файла данных увеличивается автоматически. Это событие не происходит при явном увеличении файла данных с помощью инструкции ALTER DATABASE.|  
|[Класс событий Data File Auto Shrink](data-file-auto-shrink-event-class.md)|Указывает на то, что файл данных был сжат.|  
|[Соединение зеркального отображения базы данных, класс событий](database-mirroring-connection-event-class.md)|Событие, формируемое для уведомления о состоянии транспортного соединения для зеркального отображения базы данных.|  
|[Класс событий Database Mirroring State Change](database-mirroring-state-change-event-class.md)|Указывает, когда изменяется состояние зеркальной базы данных.|  
|[Класс событий Database Suspect Data Page](database-suspect-data-page-event-class.md)|Указывает, что страница добавлена в таблицу **suspect_pages** базы данных **msdb** .|  
|[Класс событий Log File Auto Grow](log-file-auto-grow-event-class.md)|Указывает на то, что размер файла журнала был сжат автоматически. Это событие не происходит при явном увеличении файла журнала с помощью инструкции ALTER DATABASE.|  
|[Класс событий Log File Auto Shrink](log-file-auto-shrink-event-class.md)|Указывает на то, что размер файла журнала был сжат автоматически. Это событие не происходит при явном сжатии файла журнала с помощью инструкции ALTER DATABASE.|  
  
## <a name="see-also"></a>См. также  
 [Расширенные события](../extended-events/extended-events.md)  
  
  
