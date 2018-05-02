---
title: Приостановка трассировки (приложение SQL Server Profiler) | Документы Microsoft
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: sql-server-profiler
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pausing traces
- temporarily stopping traces
- traces [SQL Server], pausing
- stopping traces
ms.assetid: 432b9b0c-b5e7-47f3-a71b-310fb3bf2445
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cbf301c5d846a42e1aed2571b60c0b88f638631b
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="pause-a-trace-sql-server-profiler"></a>приостановить трассировки (приложение SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] При приостановке трассировки дальнейший захват событий прекращается до ее возобновления.  
  
 Приостановка трассировки приводит к тому, что сбор данных о событиях прекращается до ее перезапуска. Перезапуск трассировки позволяет возобновить сбор данных. При перезапуске трассировки уже зарегистрированные данные не утрачиваются. После перезапуска трассировки сбор данных возобновляется, начиная с текущей точки. Приостановив трассировку, можно изменить ее имя, события, столбцы и фильтры. Однако изменить места назначения, в которые отправляются данные трассировки, и соединение с сервером нельзя.  
  
### <a name="to-pause-a-trace"></a>Приостановка трассировки  
  
1.  Выберите окно, содержащее выполняющуюся трассировку.  
  
2.  В меню **Файл** выберите пункт **Приостановить трассировку**.  
  
## <a name="see-also"></a>См. также:  
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
