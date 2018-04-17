---
title: Escape-последовательности | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- escape sequences [ODBC], determining if supported
- interoperability of SQL statements [ODBC], escape sequences
ms.assetid: 5913abfa-d280-43e4-a2f1-05a924388bf9
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f3779fc33ef11cd89339aacf0e87cc3805c8864e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="escape-sequences"></a>Escape-последовательность
ODBC определяет управляющие последовательности, содержащий стандартные грамматики для даты, времени, отметки времени и интервала литералами даты и времени, вызовы скалярных функций, **как** предиката escape-символы, внешние соединения и вызовов процедур. Совместимые приложения должны использовать эти последовательности, когда это возможно.  
  
 Чтобы определить, поддерживает ли драйвер escape-последовательности для даты, времени, отметка времени или интервала литералами даты и времени, приложение вызывает **SQLGetTypeInfo**. Источник данных поддерживает даты, времени, отметка времени или тип интервала datetime, должно также поддерживать соответствующие escape-последовательность. Чтобы определить, поддерживаются ли другие escape-последовательности, приложение вызывает **SQLGetInfo**.  
  
 Дополнительные сведения см. в разделе [Escape-последовательностей в ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md)далее в этом разделе.
