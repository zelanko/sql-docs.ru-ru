---
title: Секлар функция побега последовательность (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], scalar function
- scalar functions [ODBC], escape sequences
- ODBC escape sequences [ODBC], scalar function
ms.assetid: aaf5d516-e090-445f-8839-9e39581c69c7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8347b8e6f0fab6dffc5295fb3b8260a6a56ed123
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305077"
---
# <a name="scalar-function-escape-sequence"></a>Escape-последовательность скалярной функции
ODBC использует последовательности побега для масштабирования функций. Синтаксис этой последовательности побега заключается в следующем:  
  
```  
{fn scalar-function}  
```  
  
## <a name="remarks"></a>Remarks  
 В обозначении BNF синтаксис заключается следующим образом:  
  
 *ODBC-scalar-функция-побег* :::  
  
 *ODBC-esc-инициатор* fn *scalar-функция ODBC-esc-терминатор*  
  
 *scalar-функция* ::» *функция-имя* *(аргумент-список)*  
  
 (Определения для нетерминальных *функций-имя* и *имя функции* *(аргумент-список)* являются производными от списка функций масштабирования в [приложении E: Scalar Функции](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).)  
  
 *ODBC-esc-инициатор* :::  
  
 *ODBC-esc-терминатор* :::  
  
 Чтобы определить, поддерживает ли источник данных процедуры, а драйвер поддерживает синтаксис вызова процедуры ODBC, приложение может вызвать **s'LGetInfo.** Для получения дополнительной информации [см.](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md)
