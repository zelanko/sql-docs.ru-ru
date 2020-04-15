---
title: Размер дисплея Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- display size of data types [ODBC]
- size of data types [ODBC]
- data types [ODBC], display size
- SQL data types [ODBC], column characteristics
ms.assetid: 9f7f766f-2492-463c-aab7-f2476e222042
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 578bf0cbdf2dd1dbd06dd4a248f4efa5eb839916
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307035"
---
# <a name="display-size"></a>Отображаемый размер
Размер дисплея столбца — это максимальное количество символов, необходимое для отображения данных в форме символа. В следующей таблице определяется размер дисплея для каждого типа данных ODBC S'L.  
  
|Идентификатор типа S'L|Размер дисплея|  
|-------------------------|------------------|  
|Все типы символов|Определенное (для фиксированных типов) или максимальное (для переменных типов) количество символов, необходимых для отображения данных в форме символа.|  
|SQL_DECIMAL SQL_NUMERIC|Точность столбца плюс 2 (знак, *точные* цифры и десятичная точка). Например, размер дисплея столбца, определяемого как NUMERIC (10,3), составляет 12.|  
|SQL_BIT|1 (1 цифра).|  
|SQL_TINYINT|4, если подписан (знак и 3 цифры) или 3, если неподписанные (3 цифры).|  
|SQL_SMALLINT|6, если подписан (знак и 5 цифр) или 5, если неподписаны (5 цифр).|  
|SQL_INTEGER|11, если подписан (знак и 10 цифр) или 10, если не подписаны (10 цифр).|  
|SQL_BIGINT|20 (знак и 19 цифр, если подписаны или 20 цифр, если не подписаны).|  
|SQL_REAL|14 (знак, 7 цифр, десятичная точка, буква *Е,* знак и 2 цифры).|  
|SQL_FLOAT SQL_DOUBLE|24 (знак, 15 цифр, десятичная точка, буква *Е,* знак и 3 цифры).|  
|Все бинарные типы|Определенная или максимальная (для переменных типов) длина столбца раз 2. (Каждый бинарный байт представлен двухзначным гексадецимальным числом.)|  
|SQL_TYPE_DATE|10 (дата в формате *yyyy-mm-dd).*|  
|SQL_TYPE_TIME|8 (время в формате *hh:mm:ss)*<br /><br /> — или —<br /><br /> 9 *с* (время в формате *hh:mm: ss*ss .fff...», где *s* является дробной точностью секунд).|  
|SQL_TYPE_TIMESTAMP|19 (для метки времени в *формате yyyy-mm-dd:mm:ss)*<br /><br /> — или —<br /><br /> 20 *с* (для метки времени в *yyyy-mm-dd hh:mm: ss*.fff...» формат, где *s* является дробной точностью секунд).|  
|Все типы интервальных данных|[См. Длина типа данных Interval.](../../../odbc/reference/appendixes/interval-data-type-length.md)|  
|SQL_GUID|36 (количество персонажей в формате *aaaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeee*|  
  
 Если драйвер не может определить столбец или длину параметра переменных типов, он возвращаетSQL_NO_TOTAL.
