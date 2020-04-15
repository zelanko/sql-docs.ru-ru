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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298714"
---
# <a name="escape-sequences"></a>Escape-последовательности
ODBC определяет последовательности побега, содержащие стандартную грамматику для даты, времени, метки времени и интервала времени даты буквальных, масштабальных вызовов функции, **LIKE** предикатные символы побега, внешние соединения, и процедурные вызовы. Совместимые приложения должны использовать эти последовательности, когда это возможно.  
  
 Чтобы определить, поддерживает ли драйвер последовательности побега для даты, времени, метки времени или интервала времени, приложение вызывает **S'LGetTypeInfo**. Если источник данных поддерживает дату, время, отметку времени или тип интервала времени даты, он также должен поддерживать соответствующую последовательность побега. Чтобы определить, поддерживаются ли другие последовательности побега, приложение вызывает **s'LGetInfo.**  
  
 Для получения дополнительной [информации, см. Побег Последовательности в ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md), позже в этом разделе.
