---
title: Длина типа данных интервала (англ.) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], interval data types
- length of data types [ODBC]
- interval data type [ODBC], length
ms.assetid: e9eb38d8-f9db-4401-8c62-aa394054cbbf
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 68bb4daa47cb58d5a0ff7b680a2d2154fb14b345
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284324"
---
# <a name="interval-data-type-length"></a>Длина интервального типа данных
Для определения длины типа интервальных данных в символах используются следующие правила. Длина выражается в количестве символов. Количество байтов зависит от набора символов. Длина включает в себя следующие значения, добавленные вместе:  
  
-   Два символа для каждого поля в интервале, который не является ведущим полем.  
  
-   Для ведущей области, количество символов, что является выразить или неявной точностью ведущих. Если ведущая точность не указана, значение по умолчанию составляет 2.  
  
-   Один символ для сепаратора между полями.  
  
-   Один плюс экспресс или подразумеваемой точности секунд. Если точность секунд не указана, значение по умолчанию составляет 6.  
  
 Конкретные значения длины столбца для каждого типа данных интервала содержатся в [размере столбца.](../../../odbc/reference/appendixes/column-size.md)
