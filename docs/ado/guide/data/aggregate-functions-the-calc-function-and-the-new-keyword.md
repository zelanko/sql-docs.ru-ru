---
title: "Агрегатные функции, функция CALC и ключевое слово NEW | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data shaping [ADO], functions
- CALC function [ADO]
- NEW keyword [ADO]
- aggregate functions [ADO]
ms.assetid: 0590b466-2a36-49a2-868e-028ef5e49394
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f24280f155fd5ec6bd86b8486b0f8f77338d8eb6
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="aggregate-functions-the-calc-function-and-the-new-keyword"></a>Агрегатные функции, функция CALC и ключевое слово NEW
Формирование данных поддерживает следующие функции. — Имя, присвоенное главе, содержащую столбец, должна быть выполнена *главе псевдоним*.  
  
 Псевдоним главе может быть полным, состоящий из начальных главе, содержащую имя каждого главе столбца *имя столбца* разделенные точками. Например если родительский главе, chap1, содержит главе дочерних, chap2, имеет столбец amount amt, то полное имя будет chap1.chap2.amt.  
  
|Агрегатные функции|Description|  
|-------------------------|-----------------|  
|SUM (*главе псевдоним*.* Имя столбца*)|Вычисляет сумму всех значений в указанном столбце.|  
|AVG (*главе псевдоним*.* Имя столбца*)|Вычисляет среднее всех значений в указанном столбце.|  
|MAX (*главе псевдоним*.* Имя столбца*)|Вычисляет максимальное значение в указанном столбце.|  
|MIN (*главе псевдоним*.* Имя столбца*)|Вычисляет минимальное значение в указанном столбце.|  
|COUNT (*главе псевдоним*[.* Имя столбца*])|Подсчитывает количество строк в заданный псевдоним. Если указан столбец, при подсчете включаются только строки, для которых этот столбец не является нулевым.|  
|STDEV (*главе псевдоним*.* Имя столбца*)|Вычисляет стандартное отклонение в указанном столбце.|  
|ВСЕ (*главе псевдоним*.* Имя столбца*)|Значение указанного столбца. Какой-либо имеет прогнозируемое значение только в том случае, если значение столбца является одинаковым для всех строк в этой главе.<br /><br /> **Примечание** Если столбец содержит то же значение для всех строк в главе, команда ФИГУРЫ произвольно возвращает одно из значений в качестве значения любой функции.|  
  
|Вычисляемое выражение|Description|  
|---------------------------|-----------------|  
|Калькулятор (*выражение*)|Вычисляет произвольного выражения, но только в строке **записей** с функцией CALC. Любое выражение, с их помощью [Visual Basic для приложений (VBA) функции](../../../ado/guide/data/visual-basic-for-applications-functions.md) разрешено.|  
  
|НОВОЕ ключевое слово|Description|  
|-----------------|-----------------|  
|НОВЫЙ *тип поля* [(*ширина* &#124; *шкалы* &#124; *точности* &#124; *ошибка* [, *шкалы* &#124; *ошибка*])]|Добавляет пустой столбец указанного типа, **записей**.|  
  
 *Тип поля* передан с НОВОЕ ключевое слово может быть любой из следующих типов данных.  
  
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
|DBTYPE_BYTES|adLongVarBinary adBinary AdVarBinary,|  
|DBTYPE_STR|adChar adVarChar, adLongVarChar|  
|DBTYPE_WSTR|adWChar adVarWChar, adLongVarWChar|  
|DBTYPE_NUMERIC|adNumeric|  
|DBTYPE_DBDATE|adDBDate|  
|DBTYPE_DBTIME|adDBTime|  
|DBTYPE_DBTIMESTAMP|adDBTimeStamp|  
|DBTYPE_VARNUMERIC|adVarNumeric|  
|DBTYPE_FILETIME|adFileTime|  
|DBTYPE_ERROR|adError|  
  
 Если новое поле имеет тип decimal (OLE DB DBTYPE_DECIMAL, или ADO, adDecimal), необходимо указать точность и масштаб значения.  
  
## <a name="see-also"></a>См. также:  
 [Пример формирования данных](../../../ado/guide/data/data-shaping-example.md)   
 [Грамматика формальных фигуры](../../../ado/guide/data/formal-shape-grammar.md)   
 [Команды фигуры в целом](../../../ado/guide/data/shape-commands-in-general.md)
