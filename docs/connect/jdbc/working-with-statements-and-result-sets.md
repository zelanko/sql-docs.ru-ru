---
title: Работа с инструкциями и результирующими наборами | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc917534-f5f8-4844-87c8-597c48b4e06d
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 15eba10e7e0bdace764ed176a4d4b941b0afcd6a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="working-with-statements-and-result-sets"></a>Работа с инструкциями и результирующими наборами
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  При работе с [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] и инструкции и результирующий набор объектов, он предоставляет, существует несколько методов, которые можно использовать для повышения производительности и надежности приложений.  
  
## <a name="use-the-appropriate-statement-object"></a>Использование подходящего объекта инструкции  
 При использовании одного из объектов инструкции драйвера JDBC, таких как [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md), или [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) объекта, Убедитесь, что вы используете объект подходит для задания.  
  
-   Если у вас ВЫХОДНЫЕ параметры, необязательно использовать объект SQLServerCallableStatement. Вместо этого используйте SQLServerStatement либо этого объекта SQLServerPreparedStatement.  
  
-   Если не планируется исполнять инструкции несколько раз или не имеют IN или ВЫХОДНЫЕ параметры, необязательно использовать SQLServerCallableStatement либо этого объекта SQLServerPreparedStatement. Вместо этого используйте объект SQLServerStatement.  
  
## <a name="use-the-appropriate-concurrency-for-resultset-objects"></a>Используйте подходящий параллелизм для объектов ResultSet  
 Обновляемый параллелизм при создании инструкций, выдающих результирующие наборы, требуется, только если планируется непременно обновлять результаты. Маленькие результирующие наборы быстрее всего считывает стандартная однопроходная неизменяемая модель курсора.  
  
## <a name="limit-the-size-of-your-result-sets"></a>Ограничение размера результирующих наборов  
 Рассмотрите возможность использования [setMaxRows](../../connect/jdbc/reference/setmaxrows-method-sqlserverstatement.md) метод (или синтаксис SET ROWCOUNT или SELECT TOP N SQL), чтобы ограничить количество строк, возвращаемых из потенциально больших результирующих наборов. Если приходится работать с большими результирующими наборами, то, возможно, следует использовать адаптивную буферизацию ответов. Для этого нужно установить свойству строки соединения responseBuffering значение «adaptive». Это значение используется по умолчанию. Такая методика позволяет приложению обрабатывать большие результирующие наборы, не прибегая к курсорам на стороне сервера, и свести к минимуму занимаемую приложением память. Дополнительные сведения см. в разделе [с помощью адаптивной буферизации](../../connect/jdbc/using-adaptive-buffering.md).  
  
## <a name="use-the-appropriate-fetch-size"></a>Использование выборки подходящего размера  
 Для серверных курсоров только для чтения целесообразность определяется сравнением затрат на обращение к серверу и затрат памяти драйвером. Для обновляемых серверных курсоров размер выборки также влияет на чувствительность результирующего набора к изменениям и параллелизму на сервере. Обновления строк в текущем буфере выборки не видны до явно [refreshRow](../../connect/jdbc/reference/refreshrow-method-sqlserverresultset.md) будет вызван метод или пока курсор не покинет буфер выборки. У больших буферов выборки будет лучшая производительность (меньше обращений к серверу), но у них меньше чувствительность к изменениям и уменьшению параллелизма на сервере при использовании CONCUR_SS_SCROLL_LOCKS (1009). Для максимальной чувствительности к изменениям размер выборки должен равняться 1. Однако при этом будет совершаться одно обращение к серверу на каждую выбранную строку.  
  
## <a name="use-streams-for-large-in-parameters"></a>Использование потоков для больших параметров IN  
 Используйте потоки объектов BLOB и CLOB, постепенно материализуемые для управления обновляющимися большими значениями столбцов или отправления больших параметров IN. Драйвер JDBC дробит их и отправляет на сервер за несколько обращений, тем самым позволяя задавать и обновлять значения большие, чем помещаются в памяти.  
  
## <a name="see-also"></a>См. также  
 [Повышение производительности и надежности с помощью драйвера JDBC](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  
