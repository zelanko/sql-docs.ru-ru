---
title: Приостановка трассировки (SQL Server Profiler) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- pausing traces
- temporarily stopping traces
- traces [SQL Server], pausing
- stopping traces
ms.assetid: 432b9b0c-b5e7-47f3-a71b-310fb3bf2445
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d213e6b680bfe0d020a7c95b4e3924ef5679d7e2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48077104"
---
# <a name="pause-a-trace-sql-server-profiler"></a>приостановить трассировки (приложение SQL Server Profiler)
  При приостановке трассировки дальнейший захват событий прекращается до ее возобновления.  
  
 Приостановка трассировки приводит к тому, что сбор данных о событиях прекращается до ее перезапуска. Перезапуск трассировки позволяет возобновить сбор данных. При перезапуске трассировки уже зарегистрированные данные не утрачиваются. После перезапуска трассировки сбор данных возобновляется, начиная с текущей точки. Приостановив трассировку, можно изменить ее имя, события, столбцы и фильтры. Однако изменить места назначения, в которые отправляются данные трассировки, и соединение с сервером нельзя.  
  
### <a name="to-pause-a-trace"></a>Приостановка трассировки  
  
1.  Выберите окно, содержащее выполняющуюся трассировку.  
  
2.  В меню **Файл** выберите пункт **Приостановить трассировку**.  
  
## <a name="see-also"></a>См. также  
 [Приложение SQL Server Profiler](sql-server-profiler.md)  
  
  
