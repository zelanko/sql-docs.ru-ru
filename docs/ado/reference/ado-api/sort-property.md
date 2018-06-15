---
title: Сортировать свойства | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::get_Sort
- Recordset15::put_Sort
- Recordset15::PutSort
- Recordset15::GetSort
- Recordset15::Sort
helpviewer_keywords:
- DESC [ADO]
- ASC [ADO]
- Sort property [ADO]
ms.assetid: 3683ffa0-6f93-4906-9533-ef6942f24f39
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a42a5160c1e9e86f25c4547aef0e0ead5babe250
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35281913"
---
# <a name="sort-property"></a>Свойство сортировки
Указывает один или несколько имен полей, на котором [записей](../../../ado/reference/ado-api/recordset-object-ado.md) отсортирован, ли каждое поле сортируется в порядке возрастания или убывания.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **строка** значение, указывающее поле имена в **записей** по которому выполняется сортировка. Имя каждого разделены точкой с запятой, а также обязательно следует пробел и ключевое слово **ASC**, которой сортирует по возрастанию, поле или **DESC**, который сортирует поля в порядке убывания. По умолчанию если нет ключевого слова не указан, поле сортируется по возрастанию.  
  
## <a name="remarks"></a>Примечания  
 Для этого свойства требуется [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойству будет присвоено **adUseClient**. Временный индекс создается для каждого поля, указанного в **сортировки** свойства, если индекс еще не существует.  
  
 Операция сортировки эффективна, так как данные не переупорядочить физически, а просто осуществляется в порядке, заданном индексом.  
  
 Если значение **сортировки** свойства не является пустой строкой, **сортировки** порядок свойств имеет приоритет над порядке, указанном в **ORDER BY** предложения включено в инструкцию SQL, используемую для открытия **записей**.  
  
 **Записей** не нужно открывать перед обращением к **сортировки** свойства; это можно сделать в любое время после **записей** экземпляра объекта.  
  
 Установка **сортировки** свойства равным пустой строке приведет к сбросу исходный порядок строк и удалить временные индексы. Существующие индексы, не удаляются.  
  
 Предположим, что **записей** содержит три поля с именем *firstName*, *middleInitial*, и *lastName*. Задать **сортировки** свойства в строку «`lastName DESC, firstName ASC`», будет порядок **набора записей** по фамилиям в убывающем порядке, а затем по имени в порядке возрастания. Отчество учитывается.  
  
 Поле не может называться «ASC» или «DESC», так как эти имена конфликтуют с ключевыми словами **ASC** и **DESC**. Можно создать псевдоним для поля с конфликтующим именем, используя **AS** ключевое слово в запросе, который возвращает **записей**.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства сортировки (Visual Basic)](../../../ado/reference/ado-api/sort-property-example-vb.md)   
 [Пример свойства сортировки (VC ++)](../../../ado/reference/ado-api/sort-property-example-vc.md)   
 [Оптимизировать динамические свойства (ADO)](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)   
 [Свойство SortColumn (RDS)](../../../ado/reference/rds-api/sortcolumn-property-rds.md)   
 [Свойство SortDirection (служба удаленных рабочих столов)](../../../ado/reference/rds-api/sortdirection-property-rds.md)
