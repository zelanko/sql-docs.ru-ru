---
title: Sort, свойство | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 3dc6f7799e28fff65a1b6e60329ba9fb94d84824
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759840"
---
# <a name="sort-property"></a>Свойство Sort
Указывает одно или несколько имен полей, в которых сортируется [набор записей](../../../ado/reference/ado-api/recordset-object-ado.md) , а также сведения о том, сортируются ли каждое поле в порядке возрастания или убывания.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает **строковое** значение, указывающее имена полей в **наборе записей** , по которому выполняется сортировка. Каждое имя разделяются запятыми, и при необходимости следует указать пустое значение и ключевое слово **ASC**, которое сортирует поле в возрастающем порядке или **DESC**, что сортирует поле в убывающем порядке. По умолчанию, если ключевое слово не указано, поле сортируется в возрастающем порядке.  
  
## <a name="remarks"></a>Примечания  
 Для этого свойства необходимо, чтобы свойство [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) было установлено в значение **адусеклиент**. Для каждого поля, указанного в свойстве **Sort** , будет создан временный индекс, если индекс еще не существует.  
  
 Операция сортировки эффективна, поскольку данные физически не переупорядочиваются, но доступ к ним осуществляется в порядке, указанном индексом.  
  
 Если значение свойства **Sort** отличается от пустой строки, порядок свойств **сортировки** имеет приоритет над порядком, заданным в предложении **ORDER BY** , включенном в инструкцию SQL, используемую для открытия **набора записей**.  
  
 Перед доступом к свойству **Sort** не нужно открывать **набор записей** . его можно задать в любое время после создания экземпляра объекта **набора записей** .  
  
 Если задать для свойства **Sort** пустую строку, строки будут сброшены в исходный порядок и удалены временные индексы. Существующие индексы не будут удалены.  
  
 Предположим, что **набор записей** содержит три поля с именами *FirstName*, *middleInitial*и *LastName*. Задайте для свойства **Sort** строку " `lastName DESC, firstName ASC` ", которая будет упорядочивать **набор записей** по фамилии в убывающем порядке, а затем по имени по возрастанию. Инициал отчества игнорируется.  
  
 Ни одно поле не может называться "ASC" или "DESC", так как эти имена конфликтуют с ключевыми словами **ASC** и **DESC**. Можно создать псевдоним для поля с конфликтующим именем с помощью ключевого слова **as** в запросе, возвращающем **набор записей**.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства Sort (Visual Basic)](../../../ado/reference/ado-api/sort-property-example-vb.md)   
 [Пример свойства Sort (Visual c++)](../../../ado/reference/ado-api/sort-property-example-vc.md)   
 [Свойство optimize — Dynamic (ADO)](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)   
 [Свойство SortColumn (RDS)](../../../ado/reference/rds-api/sortcolumn-property-rds.md)   
 [Свойство SortDirection (служба удаленных рабочих столов)](../../../ado/reference/rds-api/sortdirection-property-rds.md)
