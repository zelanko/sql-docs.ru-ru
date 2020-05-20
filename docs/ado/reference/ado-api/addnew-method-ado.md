---
title: Метод AddNew (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::AddNew
- Recordset15::raw_AddNew
helpviewer_keywords:
- AddNew method [ADO]
ms.assetid: a9f54be9-5763-45d0-a6eb-09981b03bc08
author: rothja
ms.author: jroth
ms.openlocfilehash: a6359d1b9f69963120e9446c47aa5473beedd127
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760730"
---
# <a name="addnew-method-ado"></a>Метод AddNew (ADO)
Создает новую запись для обновляемого объекта [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.AddNew FieldList, Values  
```  
  
#### <a name="parameters"></a>Параметры  
 *записей*  
 Объект **Recordset** .  
  
 *FieldList*  
 Необязательный элемент. Одно имя или массив имен или порядковое расположение полей в новой записи.  
  
 *Значения*  
 Необязательный элемент. Одно значение или массив значений для полей в новой записи. Если *списокполей* является массивом, то *значения* также должны быть массивом с одинаковым числом членов. в противном случае возникает ошибка. Порядок имен полей должен совпадать с порядком значений полей в каждом массиве.  
  
## <a name="remarks"></a>Примечания  
 Используйте метод **AddNew** для создания и инициализации новой записи. Чтобы проверить, можно ли добавлять записи в текущий объект **Recordset** , используйте метод [поддерживает](../../../ado/reference/ado-api/supports-method.md) с **ададднев** (значение [курсороптионенум](../../../ado/reference/ado-api/cursoroptionenum.md) ).  
  
 После вызова метода **AddNew** новая запись становится текущей и остается текущей после вызова метода [Update](../../../ado/reference/ado-api/update-method.md) . Так как новая запись добавляется к **набору записей**, вызов **MoveNext** после обновления будет перемещаться за пределы **набора записей**, делая **EOF** истинным. Если объект **Recordset** не поддерживает закладки, вы не сможете получить доступ к новой записи после перехода на другую запись. В зависимости от типа курсора может потребоваться вызвать метод [Requery](../../../ado/reference/ado-api/requery-method.md) , чтобы сделать новую запись доступной.  
  
 При вызове **AddNew** во время редактирования текущей записи или при добавлении новой записи ADO вызывает метод **Update** для сохранения любых изменений, а затем создает новую запись.  
  
 Поведение метода **AddNew** зависит от режима обновления объекта **Recordset** и от того, передаются ли аргументы *списокполей* и *Values* .  
  
 В *режиме немедленного обновления* (в котором поставщик записывает изменения в базовый источник данных после вызова метода **Update** ), вызов метода **AddNew** без аргументов устанавливает свойство [EditMode](../../../ado/reference/ado-api/editmode-property.md) в **адедитадд** (значение [едитмодинум](../../../ado/reference/ado-api/editmodeenum.md) ). Поставщик кэширует все изменения значений полей локально. Вызов метода **Update** отправляет новую запись в базу данных и сбрасывает свойство **EditMode** в **адедитноне** (значение **едитмодинум** ). При передаче аргументов *списокполей* и *Values* ADO немедленно отправляет новую запись в базу данных (вызов **обновления** не требуется); значение свойства **EditMode** не изменяется (**адедитноне**).  
  
 В *режиме пакетного обновления* (в котором поставщик кэширует несколько изменений и записывает их в базовый источник данных только при вызове метода [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) ), вызов метода **AddNew** без аргументов устанавливает свойство **EditMode** в **адедитадд**. Поставщик кэширует все изменения значений полей локально. Вызов метода **Update** добавляет новую запись в текущий **набор записей**, но поставщик не переносит изменения в основную базу данных или сбрасывает **EditMode** до **Адедитноне**, пока не будет вызван метод **UpdateBatch** . При передаче аргументов *списокполей* и *Values* ADO отправляет новую запись в поставщик для хранения в кэше и устанавливает для **EditMode** значение **адедитадд**. необходимо вызвать метод **UpdateBatch** для публикации новой записи в основную базу данных.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать метод AddNew с включенным списком полей и списком значений, чтобы увидеть, как включить список полей и список значений в качестве массивов.  
  
```  
create table aa1 (intf int, charf char(10))  
insert into aa1 values (2, 'aa')  
  
Dim cn As New adodb.Connection  
Dim rs As New adodb.Recordset  
Dim cmd As New adodb.Command  
  
cn.ConnectionString = "Provider=SQLOLEDB;Data Source=alexverb2;uid=sa;pwd=foo$bar00;"  
  
cn.Open  
rs.Open "select * from xxx..aa1", cn, adOpenKeyset, adLockOptimistic  
  
Dim fieldsArray(1) As Variant  
fieldsArray(0) = "intf"  
fieldsArray(1) = "charf"  
Dim values(1) As Variant  
values(0) = 4  
values(1) = "as"  
rs.AddNew fieldsArray, values  
rs.Update  
```  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода AddNew (Visual Basic)](../../../ado/reference/ado-api/addnew-method-example-vb.md)   
 [Пример метода AddNew (VBScript)](../../../ado/reference/ado-api/addnew-method-example-vbscript.md)   
 [Пример метода AddNew (Visual c++)](../../../ado/reference/ado-api/addnew-method-example-vc.md)   
 [Метод CancelUpdate (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [EditMode, свойство](../../../ado/reference/ado-api/editmode-property.md)   
 [Метод Requery](../../../ado/reference/ado-api/requery-method.md)   
 [Поддерживает метод](../../../ado/reference/ado-api/supports-method.md)   
 [Метод Update](../../../ado/reference/ado-api/update-method.md)   
 [Метод UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)
