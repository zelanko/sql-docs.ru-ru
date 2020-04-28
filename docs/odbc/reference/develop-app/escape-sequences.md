---
title: Escape-последовательности | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- escape sequences [ODBC], determining if supported
- interoperability of SQL statements [ODBC], escape sequences
ms.assetid: 5913abfa-d280-43e4-a2f1-05a924388bf9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5d9589230183b198cb7d59cf9739dab75625441e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298714"
---
# <a name="escape-sequences"></a>Escape-последовательности
ODBC определяет escape-последовательности, которые содержат стандартную грамматику для литералов даты, времени, timestamp и интервала времени, скалярные вызовы функций, **такие как** escape-символы предиката, внешние соединения и вызовы процедур. Приложения, поддерживающие взаимодействие, должны использовать эти последовательности везде, где это возможно.  
  
 Чтобы определить, поддерживает ли драйвер escape-последовательности для литералов даты, времени, отметке времени или интервала времени, приложение вызывает **SQLGetTypeInfo**. Если источник данных поддерживает тип данных даты, времени, timestamp или DateTime, он также должен поддерживать соответствующую escape-последовательность. Чтобы определить, поддерживаются ли другие escape-последовательности, приложение вызывает **SQLGetInfo**.  
  
 Дополнительные сведения см. в подразделе [escape-последовательности в ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md)ниже.
