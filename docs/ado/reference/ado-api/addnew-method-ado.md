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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a2f9efa8f5042fab603c794edada5aacab001936
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67921329"
---
# <a name="addnew-method-ado"></a>Метод AddNew (ADO)
Создает новую запись для обновляемый [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.AddNew FieldList, Values  
```  
  
#### <a name="parameters"></a>Параметры  
 *Набор записей*  
 Объект **записей** объекта.  
  
 *FieldList*  
 Необязательный параметр. Одно имя, или массив имен или порядковые номера поля в новой записи.  
  
 *Значения*  
 Необязательный параметр. Одно значение или массив значений для полей новой записи. Если *"списокполей"* является массивом, *значения* также должен быть массивом с тем же число членов; в противном случае возникает ошибка. Порядок имен полей должен соответствовать порядку значений полей в каждом массиве.  
  
## <a name="remarks"></a>Примечания  
 Используйте **AddNew** метод для создания и инициализации новой записи. Используйте [поддерживает](../../../ado/reference/ado-api/supports-method.md) метод с **adAddNew** ( [CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md) значение) для проверки, возможность добавления записи в текущий **записей**объекта.  
  
 После вызова метода **AddNew** метод, новая запись становится текущей записью и остаются актуальными, после вызова метода [обновления](../../../ado/reference/ado-api/update-method.md) метод. Так как новая запись добавляется к **записей**, вызов **MoveNext** следующее обновление переместит позицию после конца **записей**, что проведение **EOF**  Значение true. Если **записей** объект не поддерживает закладки, вы не сможете получить доступ к новой записи, то при перемещении на другую запись. В зависимости от типа курсора, может потребоваться вызвать [Requery](../../../ado/reference/ado-api/requery-method.md) метод, чтобы сделать доступным новой записи.  
  
 При вызове метода **AddNew** во время редактирования текущей записи или при добавлении новой записи ADO вызывает **обновления** метод, чтобы сохранить любые изменения, а затем создает новую запись.  
  
 Поведение **AddNew** метод зависит от режима обновления из **записей** объекта и ли передать *"списокполей"* и *значения*аргументы.  
  
 В *режим немедленного обновления* (в котором поставщик записывает изменения в источнике данных при вызове метода **обновление** метод), вызов **AddNew** метод без Задает аргументы [EditMode](../../../ado/reference/ado-api/editmode-property.md) свойства **adEditAdd** ( [EditModeEnum](../../../ado/reference/ado-api/editmodeenum.md) значение). Поставщик кэширует локально изменения значения полей. Вызов **обновление** метод размещает новую запись в базу данных и сбрасывает **EditMode** свойства **как таковые** ( **EditModeEnum**значение). Если передать *"списокполей"* и *значения* аргументы, ADO, немедленно публикует новую запись в базу данных (не **обновление** вызов необходим); **EditMode**  не изменяет значение свойства (**как таковые**).  
  
 В *пакетный режим обновления* (в котором поставщик кэширует несколько изменений и записывает их в базовом источнике данных только в том случае, когда вы вызываете [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) метод), вызов **AddNew** метода без аргументов **EditMode** свойства **adEditAdd**. Поставщик кэширует локально изменения значения полей. Вызов **обновление** метод добавляет новую запись в текущий **записей**, однако поставщик не учесть изменения в основную базу данных, и Сброс **EditMode** Чтобы **как таковые**, пока не будет вызван **UpdateBatch** метод. Если передать *"списокполей"* и *значения* аргументы, ADO отправляет новой записи в поставщик хранилища в кэш и задает **EditMode** для **adEditAdd** ; необходимо вызвать **UpdateBatch** метод для публикации новой записи в основную базу данных.  
  
## <a name="example"></a>Пример  
 Приведенный ниже показано, как использовать метод AddNew список полей и список значений, которые включены, чтобы узнать, как включить список полей и список значений как массивы.  
  
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
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода AddNew (Visual Basic)](../../../ado/reference/ado-api/addnew-method-example-vb.md)   
 [Пример метода AddNew (VBScript)](../../../ado/reference/ado-api/addnew-method-example-vbscript.md)   
 [Пример метода AddNew (Visual C++)](../../../ado/reference/ado-api/addnew-method-example-vc.md)   
 [Метод CancelUpdate (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [Свойство EditMode](../../../ado/reference/ado-api/editmode-property.md)   
 [Requery-метод](../../../ado/reference/ado-api/requery-method.md)   
 [Поддерживает метод](../../../ado/reference/ado-api/supports-method.md)   
 [Метод обновления](../../../ado/reference/ado-api/update-method.md)   
 [Метод UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)
