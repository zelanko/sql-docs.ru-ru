---
title: "Свойство (ячеек ADO MD) элемента | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Item
- Cellset::Item
helpviewer_keywords:
- Item property [ADO MD]
ms.assetid: 0e93d79b-b12e-4e98-889e-c2dfcca20fd0
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0fb324383dc9321129fdb84475369d899d61adcb
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="item-property-ado-md-cellset"></a>Свойство Item (ячеек ADO MD)
Возвращает ячейку из [ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) координат.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set  
Cell = Cellset.Item ( Positions)  
```  
  
## <a name="parameters"></a>Параметры  
 *Позиции*  
 Объект **VariantArray** из значения, которые однозначно определяют ячейки. *Позиций* может принимать одно из следующих действий:  
  
-   Массив чисел позиции  
  
-   Массив имен элементов  
  
-   Порядковый номер  
  
## <a name="remarks"></a>Замечания  
 Используйте **элемент** возвращаемое свойство [ячейки](../../../ado/reference/ado-md-api/cell-object-ado-md.md) объекта в [ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) объекта. Если **элемент** свойства не удается найти ячейки, соответствующие *позиций* аргументов, возникает ошибка.  
  
 **Элемент** свойство является свойством по умолчанию для **ячеек** объекта. Следующие синтаксические формы являются взаимозаменяемыми:  
  
```  
  
Cellset.Item ( Positions )Cellset ( Positions )  
```  
  
## <a name="remarks"></a>Замечания  
 *Позиций* аргумент указывает, какая ячейка для возврата. Можно указать ячейки по порядковому номеру или по позиции по каждой оси. При указании ячейки по позиции по каждой оси, можно задать числовое значение позиции или имена членов для каждого положения.  
  
 Порядковый номер является число, которое однозначно определяет одну ячейку в пределах **ячеек**. По существу, ячейки нумеруются в **ячеек** как если бы **ячеек** были *p*-мерный массив, где *p* — число осей. Адресация ячеек осуществляется по строкам. Ниже приведена формула для вычисления порядкового номера ячейки:  
  
 Если имена элементов передаются как строки к **элемент**, члены должны быть перечислены в порядке возрастания их идентификаторы числовой оси. В каждой оси, члены должны быть перечислены в порядке возрастания их вложенности измерения — то есть член самым внешним измерением идет первой, следуют элементы внутреннего измерений. Каждого измерения должны быть представлены отдельной строкой, и список элементов строк должны быть разделены запятыми.  
  
> [!NOTE]
>  Получение ячейки с именем члена, не может поддерживаться поставщиком данных. См. в документации к поставщику для получения дополнительной информации.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект набора ячеек (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>См. также:  
 [Объект ячейки (ADO MD)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)   
 [Объект набора ячеек (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)

