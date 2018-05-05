---
title: Границы набора записей | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- EOF property [ADO], boundaries of a Recordset
- Recordset object [ADO], boundaries of a Recordset
- BOF property [ADO], boundaries of a Recordset
ms.assetid: c0dd4a0f-478d-4c5e-b5d5-7535f211d064
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 20373bc374d1f5f5b75522ede5255a376ab6f657
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="boundaries-of-a-recordset"></a>Границы набора записей
**Набор записей** поддерживает **BOF** и **EOF** свойства для разграничения начала и окончания, соответственно, набора данных. Можно представить **BOF** и **EOF** как «фантомных» записи, которые располагаются в начале и конце **записей**. Подсчет **BOF** и **EOF**, выборка **записей** теперь будет выглядеть следующим образом:  
  
|ProductID|ProductName|UnitPrice|  
|---------------|-----------------|---------------|  
|BOF|||  
|7|Боб родственным органических высохла Груши|30.0000|  
|14|Диаграмме|23.2500|  
|28|Квашеная капуста Rssle|45.6000|  
|51|Сушеные яблоки|53.0000|  
|74|Longlife диаграмме|10.0000|  
|EOF|||  
  
 Когда курсор перемещается за последней записью **EOF** задано значение **True**; в противном случае имеет значение **False**. Аналогичным образом, когда курсор перемещается перед первой записью **BOF** равно **True**; в противном случае его значение равно **False**. Эти свойства используются для перечисления записей в наборе данных, как показано в следующем фрагменте кода JScript.  
  
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
  
 Если оба **BOF** и **EOF** , **True**, **записей** объект пуст. Оба свойства будут **False** для вновь открытого непустой **записей** объекта. Можно использовать **BOF** и **EOF** свойства для определения, если **записей** объект является пустым или не так, как показано в следующем фрагменте кода JScript.  
  
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
  
 Эта схема работает для всех типов курсоров и не зависит от базовой поставщиков. При попытке определить, проверяемая из **записей** объекта путем проверки, если его **RecordCount** значение свойства равно нулю (0) или нет, необходимо принимать меры предосторожности, для использования соответствующего курсора и поставщика, поддерживает возврат числа записей в результат.  
  
 При удалении последней оставшиеся записи **записей** объекта положение курсора остается в неопределенном состоянии. **BOF** и **EOF** свойства могут остаться **False** до попытки изменить положение текущей записи, в зависимости от поставщика. Дополнительные сведения см. в разделе [удаление записей с помощью метода Delete](../../../ado/guide/data/deleting-records-using-the-delete-method.md).
