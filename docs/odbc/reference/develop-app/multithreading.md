---
title: "Многопоточность | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC drivers [ODBC], thread-safe
- thread-safe drivers [ODBC]
- multithreaded applications [ODBC]
ms.assetid: cdfebdf5-12ff-4e28-8055-41f49b77f664
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 86ef8e539354dce2d0cd349d75053b05a7ca59ca
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="multithreading"></a>Многопоточность
Несколько потоков операционных системах драйверы должны быть потокобезопасным. То есть должны быть приложения могут использовать тот же дескриптор более чем в одном потоке. Как это можно сделать, специфические для драйвера и вполне вероятно, что драйверы будет сериализовать любые попытки получить доступ к тем же дескриптором в двух разных потоках.  
  
 Приложения часто используют несколько потоков вместо асинхронной обработки. Приложение создает отдельный поток, вызывает функцию ODBC на нем и затем продолжает обработку в основном потоке. Вместо необходимости постоянного опроса асинхронной функции, как в случае, если используется атрибут инструкции атрибуту SQL_ATTR_ASYNC_ENABLE, приложение может просто разрешить вновь созданный поток завершения.  
  
 Функции, которые принимают дескриптор инструкции, а также выполняются в одном потоке можно отменить, вызвав **SQLCancel** с той же инструкции обработки из другого потока. Несмотря на то, что драйверы не должен сериализовать использование **SQLCancel** таким образом, нет гарантии, что вызов **SQLCancel** действительно отменит функции, работающей на другой поток.
