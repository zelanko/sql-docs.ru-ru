---
title: Приостановка трассировки (SQL Server Profiler) | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.suite: sql
ms.technology: profiler
ms.tgt_pltfrm: ''
ms.topic: conceptual
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
ms.openlocfilehash: c58d67783fa415936c74c26167517ca7b1933788
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38031552"
---
# <a name="pause-a-trace-sql-server-profiler"></a>приостановить трассировки (приложение SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  При приостановке трассировки дальнейший захват событий прекращается до ее возобновления.  
  
 Приостановка трассировки приводит к тому, что сбор данных о событиях прекращается до ее перезапуска. Перезапуск трассировки позволяет возобновить сбор данных. При перезапуске трассировки уже зарегистрированные данные не утрачиваются. После перезапуска трассировки сбор данных возобновляется, начиная с текущей точки. Приостановив трассировку, можно изменить ее имя, события, столбцы и фильтры. Однако изменить места назначения, в которые отправляются данные трассировки, и соединение с сервером нельзя.  
  
### <a name="to-pause-a-trace"></a>Приостановка трассировки  
  
1.  Выберите окно, содержащее выполняющуюся трассировку.  
  
2.  В меню **Файл** выберите пункт **Приостановить трассировку**.  
  
## <a name="see-also"></a>См. также:  
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
