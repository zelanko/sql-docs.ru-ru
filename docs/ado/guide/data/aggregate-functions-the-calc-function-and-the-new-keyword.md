---
description: Агрегатные функции, функция CALC и ключевое слово NEW
title: Агрегатные функции, функция CALC и ключевое слово NEW | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data shaping [ADO], functions
- CALC function [ADO]
- NEW keyword [ADO]
- aggregate functions [ADO]
ms.assetid: 0590b466-2a36-49a2-868e-028ef5e49394
author: rothja
ms.author: jroth
ms.openlocfilehash: ad6bf4b041fbae0f30e327bd32dd067c1e9c429a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453756"
---
# <a name="aggregate-functions-the-calc-function-and-the-new-keyword"></a>Агрегатные функции, функция CALC и ключевое слово NEW
Функция формирования данных поддерживает следующие функции. Имя, присвоенное главе, содержащей столбец для обработки, является *псевдонимом главы*.  
  
 Псевдоним главы может быть полным, состоящим из имени каждого столбца главы, в который входит глава *, содержащая имя столбца,* разделенные точками. Например, если родительская глава, Chap1, содержит дочернюю главу Chap2, имеющую столбец Amount, то полное имя будет Chap1. Chap2. AMT.  
  
|Агрегатные функции|Описание|  
|-------------------------|-----------------|  
|SUM (*раздел-Alias*.* имя столбца*)|Вычисляет сумму всех значений в указанном столбце.|  
|AVG (*раздел-Alias*.* имя столбца*)|Вычисляет среднее всех значений в указанном столбце.|  
|MAX (*раздел-Alias*.* имя столбца*)|Вычисляет максимальное значение в указанном столбце.|  
|MIN (*раздел-Alias*.* имя столбца*)|Вычисляет минимальное значение в указанном столбце.|  
|COUNT (*раздел-Alias*[.* column-name*])|Подсчитывает количество строк в указанном псевдониме. Если столбец указан, в счетчик включаются только строки, для которых этот столбец имеет значение, отличное от NULL.|  
|STDEV (*раздел-Alias*.* имя столбца*)|Вычисляет стандартное отклонение в указанном столбце.|  
|ANY (*раздел-Alias*.* имя столбца*)|Значение указанного столбца. ANY имеет прогнозируемое значение, только если значение столбца одинаково для всех строк в главе.<br /><br /> **Примечание** . Если столбец не содержит одинаковое значение для всех строк главы, команда SHAPE произвольно возвращает одно из значений, которое является значением любой функции.|  
  
|Вычисляемое выражение|Описание|  
|---------------------------|-----------------|  
|CALC (*выражение*)|Вычисляет произвольное выражение, но только для строки **набора записей** , содержащего функцию Calc. Любое выражение, использующее эти [функции Visual Basic для приложений (VBA)](../../../ado/guide/data/visual-basic-for-applications-functions.md) , разрешено.|  
  
|СОЗДАТЬ ключевое слово|Описание|  
|-----------------|-----------------|  
|НОВОЕ *поле-Тип* [(*Ширина* &#124; *шкала* &#124; *точность* &#124; *Ошибка* [, *масштаб* &#124; *Ошибка*])]|Добавляет в **набор записей**пустой столбец указанного типа.|  
  
 *Тип поля* , переданный с помощью ключевого слова New, может быть любым из следующих типов данных.  
  
|Типы данных OLE DB|Эквиваленты типов данных ADO|  
|-----------------------|-----------------------------------|  
|DBTYPE_BSTR|adBSTR|  
|DBTYPE_BOOL|adBoolean|  
|DBTYPE_DECIMAL|adDecimal|  
|DBTYPE_UI1|adUnsignedTinyInt|  
|DBTYPE_I1|adTinyInt|  
|DBTYPE_UI2|adUnsignedSmallInt|  
|DBTYPE_UI4|adUnsignedInt|  
|DBTYPE_I8|adBigInt|  
|DBTYPE_UI8|adUnsignedBigInt|  
|DBTYPE_GUID|адгуид|  
|DBTYPE_BYTES|Адбинари, Адварбинари, Адлонгварбинари|  
|DBTYPE_STR|Адчар, Адварчар, Адлонгварчар|  
|DBTYPE_WSTR|Адвчар, Адварвчар, Адлонгварвчар|  
|DBTYPE_NUMERIC|adNumeric|  
|DBTYPE_DBDATE|adDBDate|  
|DBTYPE_DBTIME|adDBTime|  
|DBTYPE_DBTIMESTAMP|adDBTimeStamp|  
|DBTYPE_VARNUMERIC|adVarNumeric|  
|DBTYPE_FILETIME|adFileTime|  
|DBTYPE_ERROR|adError|  
  
 Если новое поле имеет тип Decimal (в OLE DB, DBTYPE_DECIMAL или в ADO, АддеЦимал), необходимо указать значения точности и масштаба.  
  
## <a name="see-also"></a>См. также  
 [Пример формирования данных](../../../ado/guide/data/data-shaping-example.md)   
 [Грамматика формальной фигуры](../../../ado/guide/data/formal-shape-grammar.md)   
 [Общие сведения о командах формирования данных](../../../ado/guide/data/shape-commands-in-general.md)
