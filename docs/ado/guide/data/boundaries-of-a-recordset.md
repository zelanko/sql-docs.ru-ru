---
title: Границы набора записей | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- EOF property [ADO], boundaries of a Recordset
- Recordset object [ADO], boundaries of a Recordset
- BOF property [ADO], boundaries of a Recordset
ms.assetid: c0dd4a0f-478d-4c5e-b5d5-7535f211d064
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4c9e05a45b5f035a500e210c991a33216be318ea
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62472829"
---
# <a name="boundaries-of-a-recordset"></a>Границы набора записей
**Набор записей** поддерживает **BOF** и **EOF** свойства для разграничения начало и конец, соответственно, набора данных. Можно представить себе **BOF** и **EOF** как «фантомную» записи, которые располагаются в начале и конце **записей**. Подсчет **BOF** и **EOF**, в нашем примере **записей** теперь будет выглядеть следующим образом:  
  
|ProductID|ProductName|UnitPrice|  
|---------------|-----------------|---------------|  
|BOF|||  
|7|Uncle Bob органических высохла Груши|30.0000|  
|14|Диаграмме|23.2500|  
|28|Квашеной Rssle|45.6000|  
|51|Сушеные яблоки|53.0000|  
|74|Longlife диаграмме|10.0000|  
|EOF|||  
  
 При перемещении курсора за последней записью **EOF** присваивается **True**; в противном случае имеет значение **False**. Аналогичным образом, когда курсор перемещается перед первой записи, **BOF** присваивается **True**; в противном случае имеет значение **False**. Эти свойства обычно используются для перечисления записей в наборе данных, как показано в следующем фрагменте кода JScript.  
  
```  
while (objRecordset.EOF != true)   
{  
   // Work on the current record.  
   ...  
   // Advance the cursor forward to the next record.  
   objRecordset.MoveNext();  
}  
or  
while (objRecordset.BOF != true)   
{  
   // Work on the current record.  
   ...  
   // Move the cursor to the previous record.  
   objRecordset.MovePrevious();  
}  
```  
  
 Если оба **BOF** и **EOF** являются **True**, **записей** объект пуст. Оба свойства будут **False** для вновь открытого непустое **записей** объекта. Можно использовать **BOF** и **EOF** свойства друг с другом, чтобы определить, если **записей** объект является пустым или не так, как показано в следующем фрагменте кода JScript.  
  
```  
if (objRecordset.EOF == true && objRecordset.BOF == true)  
{  
   WScript.Echo("we got an empty dataset.");  
}  
else  
{  
   WScript.Echo("we got a full dataset.");  
}  
```  
  
 Эта схема работает для всех типов курсора и не зависит от базовые поставщики. При попытке определить, проверяемая из **записей** объекта, проверяя его **RecordCount** значение свойства равно нулю (0) или нет, то необходимо выполнить меры предосторожности, чтобы использовать соответствующий курсор и поставщика, поддерживает возврат числа записей в результат.  
  
 При удалении последней записи оставшиеся **записей** объекта курсора остается в неопределенном состоянии. **BOF** и **EOF** свойства могут оставаться **False** до попытки изменить положение текущей записи, в зависимости от поставщика. Дополнительные сведения см. в разделе [удаление записей с помощью метода Delete](../../../ado/guide/data/deleting-records-using-the-delete-method.md).
