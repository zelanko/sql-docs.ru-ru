---
title: "Метод AddNew (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset15::AddNew
- Recordset15::raw_AddNew
helpviewer_keywords: AddNew method [ADO]
ms.assetid: a9f54be9-5763-45d0-a6eb-09981b03bc08
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 51978e39a34b02238d4c0b1658620c9ba8d538a6
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="addnew-method-ado"></a>Метод AddNew (ADO)
Создает новую запись для обновляемых [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.AddNew FieldList, Values  
```  
  
#### <a name="parameters"></a>Параметры  
 *набор записей*  
 Объект **записей** объекта.  
  
 *FieldList*  
 Необязательный параметр. Только одно имя или массива имен или порядковые номера поля в новой записи.  
  
 *Значения*  
 Необязательный параметр. Одно значение или массив значений для поля в новой записи. Если *списка полей* является массивом, *значения* также должен быть массивом с тем же число членов; в противном случае возникает ошибка. Порядок полей имен должен соответствовать порядку значений полей в каждом массиве.  
  
## <a name="remarks"></a>Remarks  
 Используйте **AddNew** метод для создания и инициализации новой записи. Используйте [поддерживает](../../../ado/reference/ado-api/supports-method.md) метод с **adAddNew** ( [CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md) значение) для проверки, сможете ли вы добавить записи в текущий **записей**объекта.  
  
 После вызова метода **AddNew** метод, новая запись становится текущей записью и остаются актуальными после вызова метода [обновление](../../../ado/reference/ado-api/update-method.md) метод. Так как новая запись добавляется к **записей**, вызов **MoveNext** следующее обновление переместит за пределами **записей**, позволяя **конца файла**  Значение true. Если **записей** объект не поддерживает закладки, не смогут получить доступ к новой записи после перемещения в другую запись. В зависимости от типа курсора, может потребоваться вызвать [Requery](../../../ado/reference/ado-api/requery-method.md) метод для предоставления специальных возможностей новой записи.  
  
 При вызове метода **AddNew** при изменении текущей записи или при добавлении новой записи ADO вызывает **обновление** метод, чтобы сохранить любые изменения, а затем создает новую запись.  
  
 Поведение **AddNew** метод зависит от режима обновления для **записей** объекта и ли передать *списка полей* и *значения*аргументы.  
  
 В *режим немедленного обновления* (в котором поставщик записывает изменения в источнике данных при вызове метода **обновление** метод), вызов **AddNew** метод без Задает аргументы [EditMode](../../../ado/reference/ado-api/editmode-property.md) свойства **adEditAdd** ( [EditModeEnum](../../../ado/reference/ado-api/editmodeenum.md) значение). Поставщик кэширует изменения значений поля локально. Вызов **обновление** метод отправляет новую запись в базу данных и сбрасывает **EditMode** свойства **как таковые** ( **EditModeEnum**значение). Если передать *списка полей* и *значения* аргументы, ADO немедленно отправляет новую запись в базу данных (не **обновление** вызов необходим); **EditMode**  не изменяет значение свойства (**как таковые**).  
  
 В *пакетный режим обновления* (в котором поставщик кэширует внесение нескольких изменений и записывает их в базовом источнике данных только при вызове [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) метод), вызов **AddNew** метод без аргументов наборов **EditMode** свойства **adEditAdd**. Поставщик кэширует изменения значений поля локально. Вызов **обновление** метод добавляет новую запись в текущий **записей**, однако поставщик не учесть изменения в исходную базу данных и сброса **EditMode** Чтобы **как таковые**, пока не будет вызван **UpdateBatch** метод. Если передать *списка полей* и *значения* аргументы, ADO отправляет новую запись поставщика для хранения данных в кэш и задает **EditMode** для **adEditAdd** ; необходимо вызвать **UpdateBatch** метод для публикации новой записи в основную базу данных.  
  
## <a name="example"></a>Пример  
 Приведенный ниже показано, как использовать метод AddNew со списком полей и список значений, которые включены, чтобы узнать, как включать список полей и список значений в виде массивов.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Метод AddNew пример (Visual Basic)](../../../ado/reference/ado-api/addnew-method-example-vb.md)   
 [Пример метода AddNew (VBScript)](../../../ado/reference/ado-api/addnew-method-example-vbscript.md)   
 [Пример метода AddNew (VC ++)](../../../ado/reference/ado-api/addnew-method-example-vc.md)   
 [Метод CancelUpdate (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [Свойство EditMode](../../../ado/reference/ado-api/editmode-property.md)   
 [Requery-метод](../../../ado/reference/ado-api/requery-method.md)   
 [Поддерживает метод](../../../ado/reference/ado-api/supports-method.md)   
 [Метод обновления](../../../ado/reference/ado-api/update-method.md)   
 [Метод UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)
