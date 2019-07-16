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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68001380"
---
# <a name="escape-sequences"></a>Escape-последовательности
ODBC определяет управляющие последовательности, содержащий стандартные грамматики для даты, времени, метка времени и интервала литералами даты и времени, вызовы скалярных функций, **как** предиката escape-символы, внешние соединения и вызовов процедур. Совместимые приложения должны использовать эти последовательности, когда это возможно.  
  
 Чтобы определить, поддерживает ли драйвер escape-последовательности для даты, времени, метка времени или интервал литералами даты и времени, приложение вызывает **SQLGetTypeInfo**. Если источник данных поддерживает даты, времени, метка времени или тип данных даты и времени интервала, он должен также поддерживать соответствующие escape-последовательность. Чтобы определить, поддерживается ли escape-последовательности, приложение вызывает **SQLGetInfo**.  
  
 Дополнительные сведения см. в разделе [escape-последовательности в ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md)далее в этом разделе.
