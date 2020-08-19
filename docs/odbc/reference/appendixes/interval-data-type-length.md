---
description: Длина интервального типа данных
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
ms.openlocfilehash: 589a13e0f0b2c6e6e42ade0f0dc32415556a0efc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483286"
---
# <a name="interval-data-type-length"></a>Длина интервального типа данных
Для определения длины типа данных интервала в символах используются следующие правила. Длина выражается в количестве символов. Число байтов зависит от кодировки. Длина включает следующие значения, которые были добавлены вместе:  
  
-   Два символа для каждого поля в интервале, не являющийся ведущим полем.  
  
-   Для ведущего поля — число символов, которое является выпуском Express или неявной начальной точностью. Если начальная точность не указана, по умолчанию используется значение 2.  
  
-   Один символ для разделителя полей.  
  
-   Один плюс в явных или неявных секундах точность. Если точность секунд не указана, по умолчанию используется значение 6.  
  
 Определенные значения длины столбцов для каждого типа данных интервала содержатся в [размере столбца](../../../odbc/reference/appendixes/column-size.md).
