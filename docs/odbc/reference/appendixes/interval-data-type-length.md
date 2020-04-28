---
title: Длина типа данных интервала | Документация Майкрософт
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81284324"
---
# <a name="interval-data-type-length"></a>Длина интервального типа данных
Для определения длины типа данных интервала в символах используются следующие правила. Длина выражается в количестве символов. Число байтов зависит от кодировки. Длина включает следующие значения, которые были добавлены вместе:  
  
-   Два символа для каждого поля в интервале, не являющийся ведущим полем.  
  
-   Для ведущего поля — число символов, которое является выпуском Express или неявной начальной точностью. Если начальная точность не указана, по умолчанию используется значение 2.  
  
-   Один символ для разделителя полей.  
  
-   Один плюс в явных или неявных секундах точность. Если точность секунд не указана, по умолчанию используется значение 6.  
  
 Определенные значения длины столбцов для каждого типа данных интервала содержатся в [размере столбца](../../../odbc/reference/appendixes/column-size.md).
