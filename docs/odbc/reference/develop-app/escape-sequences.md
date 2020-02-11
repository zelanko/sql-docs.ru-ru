---
title: Escape-последовательности | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d73282cde4d0598d7e6a35ac6273935626b96969
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68001380"
---
# <a name="escape-sequences"></a>Escape-последовательности
ODBC определяет escape-последовательности, которые содержат стандартную грамматику для литералов даты, времени, timestamp и интервала времени, скалярные вызовы функций, **такие как** escape-символы предиката, внешние соединения и вызовы процедур. Приложения, поддерживающие взаимодействие, должны использовать эти последовательности везде, где это возможно.  
  
 Чтобы определить, поддерживает ли драйвер escape-последовательности для литералов даты, времени, отметке времени или интервала времени, приложение вызывает **SQLGetTypeInfo**. Если источник данных поддерживает тип данных даты, времени, timestamp или DateTime, он также должен поддерживать соответствующую escape-последовательность. Чтобы определить, поддерживаются ли другие escape-последовательности, приложение вызывает **SQLGetInfo**.  
  
 Дополнительные сведения см. в подразделе [escape-последовательности в ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md)ниже.
