---
title: "Escape-последовательности | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- escape sequences [ODBC], determining if supported
- interoperability of SQL statements [ODBC], escape sequences
ms.assetid: 5913abfa-d280-43e4-a2f1-05a924388bf9
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1c648549b41ff607ad34175475c6a2b75603625f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="escape-sequences"></a>Escape-последовательность
ODBC определяет управляющие последовательности, содержащий стандартные грамматики для даты, времени, отметки времени и интервала литералами даты и времени, вызовы скалярных функций, **как** предиката escape-символы, внешние соединения и вызовов процедур. Совместимые приложения должны использовать эти последовательности, когда это возможно.  
  
 Чтобы определить, поддерживает ли драйвер escape-последовательности для даты, времени, отметка времени или интервала литералами даты и времени, приложение вызывает **SQLGetTypeInfo**. Источник данных поддерживает даты, времени, отметка времени или тип интервала datetime, должно также поддерживать соответствующие escape-последовательность. Чтобы определить, поддерживаются ли другие escape-последовательности, приложение вызывает **SQLGetInfo**.  
  
 Дополнительные сведения см. в разделе [Escape-последовательностей в ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md)далее в этом разделе.
