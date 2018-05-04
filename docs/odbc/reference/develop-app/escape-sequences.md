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
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- escape sequences [ODBC], determining if supported
- interoperability of SQL statements [ODBC], escape sequences
ms.assetid: 5913abfa-d280-43e4-a2f1-05a924388bf9
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e9bb389cba92f45373e7fc693c9c4477d50a702a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="escape-sequences"></a>Escape-последовательность
ODBC определяет управляющие последовательности, содержащий стандартные грамматики для даты, времени, отметки времени и интервала литералами даты и времени, вызовы скалярных функций, **как** предиката escape-символы, внешние соединения и вызовов процедур. Совместимые приложения должны использовать эти последовательности, когда это возможно.  
  
 Чтобы определить, поддерживает ли драйвер escape-последовательности для даты, времени, отметка времени или интервала литералами даты и времени, приложение вызывает **SQLGetTypeInfo**. Источник данных поддерживает даты, времени, отметка времени или тип интервала datetime, должно также поддерживать соответствующие escape-последовательность. Чтобы определить, поддерживаются ли другие escape-последовательности, приложение вызывает **SQLGetInfo**.  
  
 Дополнительные сведения см. в разделе [Escape-последовательностей в ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md)далее в этом разделе.
