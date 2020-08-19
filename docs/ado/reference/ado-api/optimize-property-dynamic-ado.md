---
description: Свойство Optimize (динамическое) (ADO)
title: Свойство optimize — Dynamic (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Optimize property [ADO]
ms.assetid: a491c4ce-2b04-4c84-be83-3846bde8d16b
author: rothja
ms.author: jroth
ms.openlocfilehash: 9ce2367d550cc8e420c4a1a9bf9fd10fff9e94e7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442916"
---
# <a name="optimize-property-dynamic-ado"></a>Свойство Optimize (динамическое) (ADO)
Указывает, должен ли быть создан индекс для [поля](../../../ado/reference/ado-api/field-object.md).  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает **логическое** значение, указывающее, должен ли быть создан индекс.  
  
## <a name="remarks"></a>Remarks  
 Индекс может повысить производительность операций, которые находят или сортируют значения в [наборе записей](../../../ado/reference/ado-api/recordset-object-ado.md). Индекс является внутренним по отношению к ADO; Вы не можете явно получить доступ к нему или использовать его в своем приложении.  
  
 Чтобы создать индекс для поля, задайте для свойства **optimize** значение **true**. Чтобы удалить индекс, присвойте этому свойству значение **false**.  
  
 **Optimize** — это динамическое свойство, добавленное к коллекции [свойств](../../../ado/reference/ado-api/properties-collection-ado.md) объекта [field](../../../ado/reference/ado-api/field-object.md) , если свойство [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) имеет значение **адусеклиент**.  
  
## <a name="usage"></a>Использование  
  
```  
Dim rs As New Recordset  
Dim fld As Field  
rs.CursorLocation = adUseClient      'Enable index creation  
rs.Fields.Append "Field1", adChar, 35, adFldIsNullable  
rs.Open  
Set fld = rs.Fields(0)  
fld.Properties("Optimize") = True    'Create an index  
fld.Properties("Optimize") = False   'Delete an index  
```  
  
## <a name="applies-to"></a>Применение  
 [Объект Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример свойства optimize (Visual Basic)](../../../ado/reference/ado-api/optimize-property-example-vb.md)   
 [Пример свойства optimize (Visual c++)](../../../ado/reference/ado-api/optimize-property-example-vc.md)   
 [Свойство Filter](../../../ado/reference/ado-api/filter-property.md)   
 [Метод Find (ADO)](../../../ado/reference/ado-api/find-method-ado.md)   
 [Свойство Sort](../../../ado/reference/ado-api/sort-property.md)
