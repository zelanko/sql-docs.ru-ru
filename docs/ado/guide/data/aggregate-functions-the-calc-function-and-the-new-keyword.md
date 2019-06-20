---
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 0a72cf80f9fee9c887e7805f3a2a5bd542d7f47c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66702425"
---
# <a name="aggregate-functions-the-calc-function-and-the-new-keyword"></a>Агрегатные функции, функция CALC и ключевое слово NEW
Формирование данных поддерживает следующие функции. — Имя, назначенное в главе, которая содержит столбец обрабатываемом *Глава alias*.  
  
 Глава псевдоним может быть полным, состоящий из каждого столбца название главы, ведущих к главе, содержащей *имя столбца,* разделенные точками. Например если родительского главе, chap1, содержит дочерние Глава, chap2, имеющей столбец amount, amt, то полное имя будет chap1.chap2.amt.  
  
|Агрегатные функции|Описание|  
|-------------------------|-----------------|  
|SUM (*Глава alias*. *Имя столбца*)|Вычисляет сумму всех значений в указанном столбце.|  
|AVG (*Глава alias*. *Имя столбца*)|Вычисляет среднее арифметическое всех значений в указанном столбце.|  
|MAX (*Глава alias*. *Имя столбца*)|Вычисляет максимальное значение в указанном столбце.|  
|MIN (*Глава alias*. *Имя столбца*)|Вычисляет минимальное значение в указанном столбце.|  
|COUNT (*Глава alias*[. *Имя столбца*])|Подсчитывает количество строк в указанный псевдоним. Если он указан, при подсчете включаются только строки, для которых этот столбец имеет отличное от Null.|  
|STDEV (*Глава alias*. *Имя столбца*)|Вычисляет стандартное отклонение в указанном столбце.|  
|ЛЮБОЙ (*Глава alias*. *Имя столбца*)|Значение указанного столбца. Какой-либо имеет прогнозируемое значение только в том случае, если значение в столбце одинаков для всех строк в главе.<br /><br /> **Примечание** Если столбец содержит то же значение для всех строк в главе, команда ФИГУРЫ произвольно возвращает одно из значений в качестве значения любой функции.|  
  
|вычисляемое выражение|Описание|  
|---------------------------|-----------------|  
|Калькулятор (*выражение*)|Вычисляет произвольного выражения, но только в строке с **записей** содержащий функция CALC. Любое выражение, основанное на этих [Visual Basic for Applications (VBA) функции](../../../ado/guide/data/visual-basic-for-applications-functions.md) разрешено.|  
  
|НОВОЕ ключевое слово|Описание|  
|-----------------|-----------------|  
|НОВЫЙ *тип поля* [(*ширины* &#124; *масштабирования* &#124; *точности* &#124; *ошибка*[, *масштабирования* &#124; *ошибка*])]|Добавляет пустой столбец для указанного типа **записей**.|  
  
 *Тип поля* передаваемый с помощью ключевого слова NEW может быть любой из следующих типов данных.  
  
|Типы данных OLE DB|Тип данных ADO equivalent(s)|  
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
|DBTYPE_GUID|adGuid|  
|DBTYPE_BYTES|adBinary, AdVarBinary, adLongVarBinary|  
|DBTYPE_STR|adChar, adVarChar, adLongVarChar|  
|DBTYPE_WSTR|adWChar, adVarWChar, adLongVarWChar|  
|DBTYPE_NUMERIC|adNumeric|  
|DBTYPE_DBDATE|adDBDate|  
|DBTYPE_DBTIME|adDBTime|  
|DBTYPE_DBTIMESTAMP|adDBTimeStamp|  
|DBTYPE_VARNUMERIC|adVarNumeric|  
|DBTYPE_FILETIME|adFileTime|  
|DBTYPE_ERROR|adError|  
  
 Если новое поле имеет тип decimal (в OLE DB DBTYPE_DECIMAL, или ADO, adDecimal), необходимо указать точность и масштаб значения.  
  
## <a name="see-also"></a>См. также  
 [Пример формирования данных](../../../ado/guide/data/data-shaping-example.md)   
 [Грамматика формального формирования данных](../../../ado/guide/data/formal-shape-grammar.md)   
 [Общие сведения о командах формирования данных](../../../ado/guide/data/shape-commands-in-general.md)
