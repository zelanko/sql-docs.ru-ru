---
title: Сортировать свойства | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6c579c824d65d50dfd1b222615f247d97209db37
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47675602"
---
# <a name="sort-property"></a>Свойство Sort
Указывает один или несколько имен полей, на котором [набор записей](../../../ado/reference/ado-api/recordset-object-ado.md) сортируется, а ли каждое поле сортируется в порядке возрастания или убывания.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **строка** значение, указывающее поле имена в **записей** по которому производится сортировка. Каждое имя разделены запятыми и может стоять пробел и ключевое слово **ASC**, который сортирует поля в порядке возрастания или **DESC**, который сортирует поля в порядке убывания. По умолчанию если ключевое слово не указан, поле сортируется в порядке возрастания.  
  
## <a name="remarks"></a>Примечания  
 Для этого свойства требуется [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойству будет присвоено **adUseClient**. Временный индекс создается для каждого поля, указанного в **сортировки** свойства, если индекс еще не существует.  
  
 Операция сортировки эффективен, поскольку данные не одностраничный физически, но просто осуществляется в порядке, заданном индексом.  
  
 Когда значение **сортировки** свойство не является пустой строкой, **сортировки** порядок свойств имеет приоритет над порядке, указанном в **ORDER BY** предложение включен в инструкцию SQL, используемую для открытия **записей**.  
  
 **Записей** не нужно открывать перед доступом к **сортировки** свойство; его можно задать в любое время после **записей** создается экземпляр объекта.  
  
 Установка **сортировки** присваивается пустая строка будет восстановить исходный порядок строк и удалить временные индексы. Существующие индексы, не удаляются.  
  
 Предположим, что **записей** содержит три поля с именем *firstName*, *middleInitial*, и *lastName*. Задайте **сортировки** свойства в строку "`lastName DESC, firstName ASC`«, порядок будет **записей** по фамилии в порядке убывания, а затем по фамилиям в возрастающем порядке. Отчество учитывается.  
  
 Поле не может иметь имя, либо «ASC» или «DESC» так как эти имена конфликтовать с ключевыми словами **ASC** и **DESC**. Можно создать псевдоним для поля с конфликтующим именем, используя **AS** ключевое слово в запросе, который возвращает **записей**.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства Sort (Visual Basic)](../../../ado/reference/ado-api/sort-property-example-vb.md)   
 [Пример свойства Sort (Visual C++)](../../../ado/reference/ado-api/sort-property-example-vc.md)   
 [Optimize (динамическое свойство (ADO)](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)   
 [Свойство SortColumn (служба удаленных рабочих СТОЛОВ)](../../../ado/reference/rds-api/sortcolumn-property-rds.md)   
 [Свойство SortDirection (служба удаленных рабочих столов)](../../../ado/reference/rds-api/sortdirection-property-rds.md)
