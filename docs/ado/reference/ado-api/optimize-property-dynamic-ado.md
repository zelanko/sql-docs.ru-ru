---
title: Optimize (динамическое свойство (ADO) | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3e8bb3c3787effe8418db735a72425a793b73e35
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67931854"
---
# <a name="optimize-property-dynamic-ado"></a>Свойство Optimize (динамическое) (ADO)
Указывает, должен ли быть создан индекс на [поле](../../../ado/reference/ado-api/field-object.md).  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **логическое** значение, указывающее, должен ли быть создан индекс.  
  
## <a name="remarks"></a>Примечания  
 Индекс может повысить производительность операций, которые поиск или Сортировка значений в [записей](../../../ado/reference/ado-api/recordset-object-ado.md). Индекс является внутренним для ADO; Вы явным образом не может получить доступ к или использовать его в приложении.  
  
 Чтобы создать индекс для поля, задайте **оптимизировать** свойства **True**. Чтобы удалить индекс, значение этого свойства **False**.  
  
 **Оптимизация** динамическое свойство добавляется к [поле](../../../ado/reference/ado-api/field-object.md) объект [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции при [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойству **adUseClient**.  
  
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
  
## <a name="applies-to"></a>Объект применения  
 [Объект Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>См. также  
 [Оптимизация пример свойства (Visual Basic)](../../../ado/reference/ado-api/optimize-property-example-vb.md)   
 [Оптимизация пример свойства (Visual C++)](../../../ado/reference/ado-api/optimize-property-example-vc.md)   
 [Свойство фильтра](../../../ado/reference/ado-api/filter-property.md)   
 [Метод Find (ADO)](../../../ado/reference/ado-api/find-method-ado.md)   
 [Свойство Sort](../../../ado/reference/ado-api/sort-property.md)
