---
title: Метод append (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _DynaCollection::Append
helpviewer_keywords:
- Append method [ADO]
ms.assetid: f8a9bbed-ba9c-4698-945d-317ad22d2e92
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5e03e29d5c9696efb55ef5ce6ec47fcf28fc0467
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47712397"
---
# <a name="append-method-ado"></a>Метод Append (ADO)
Добавляет объект в коллекцию. Если коллекция [поля](../../../ado/reference/ado-api/fields-collection-ado.md), новый [поле](../../../ado/reference/ado-api/field-object.md) объект может быть создан, прежде чем он будет добавлен к коллекции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
collection.Append object  
fields.Append Name, Type, DefinedSize, Attrib, FieldValue  
```  
  
#### <a name="parameters"></a>Параметры  
 *Коллекции*  
 Объект коллекции.  
  
 *Поля*  
 Объект **поля** коллекции.  
  
 *object*  
 Переменной объекта, который представляет объект для добавления.  
  
 *Название*  
 Объект **строка** значение, содержащее имя нового **поле** объекта, и не должен быть тем же именем, как любой другой объект в *поля*.  
  
 *Тип*  
 Объект [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) значение, значение которого по умолчанию равно **adEmpty**, указывающий тип данных нового поля. Следующие типы данных не поддерживаются ADO, а также следует не быть используется при добавлении новых полей в [объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md): **adIDispatch**, **adIUnknown**, **adVariant**.  
  
 *DefinedSize*  
 Необязательный параметр. Объект **Long** значение, представляющее заданный размер, в символах или байтах нового поля. Значение по умолчанию для этого параметра является производным от *тип*. Поля, *DefinedSize* длиной более 255 байт, обрабатываются как столбцы переменной длины. По умолчанию для *DefinedSize* не определен.  
  
 *Attrib*  
 Необязательный параметр. Объект [FieldAttributeEnum](../../../ado/reference/ado-api/fieldattributeenum.md) значение, значение которого по умолчанию равно **adFldDefault**, который задает атрибуты для нового поля. Если это значение не указано, будет содержать поле атрибутов, производных от *тип*.  
  
 *FieldValue*  
 Необязательный параметр. Объект **Variant** , представляющий значение для нового поля. Если не указан, поле добавляется со значением null.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="parameters-collection"></a>Коллекция Parameters  
 Необходимо задать [тип](../../../ado/reference/ado-api/type-property-ado.md) свойство [параметр](../../../ado/reference/ado-api/parameter-object.md) объекта перед его добавлением [параметры](../../../ado/reference/ado-api/parameters-collection-ado.md) коллекции. Если выбран тип данных переменной длины, необходимо также задать [размер](../../../ado/reference/ado-api/size-property-ado-parameter.md) свойства со значением, отличным от нуля.  
  
 Описывающие параметры самостоятельно число обращений к поставщику и соответственно, повышает производительность при использовании хранимой процедуры или параметризованные запросы. Тем не менее необходимо знать свойства параметров связаны с помощью хранимой процедуры или параметризированного запроса, который требуется вызвать.  
  
 Используйте [CreateParameter](../../../ado/reference/ado-api/createparameter-method-ado.md) метод для создания **параметр** объектов с соответствующими параметрами свойств и используйте **Append** метод, чтобы добавить их в [ Параметры](../../../ado/reference/ado-api/parameters-collection-ado.md) коллекции. Это позволяет задать и получить значения параметров не нужно звонить поставщика сведения о параметре. При написании поставщику, который не предоставляет сведения о параметрах, этот метод следует использовать для заполнения вручную **параметры** коллекции, чтобы использовать параметры вообще.  
  
## <a name="fields-collection"></a>Коллекция Fields  
 *FieldValue* параметр допустим только в том случае, при добавлении **поле** объект [записи](../../../ado/reference/ado-api/record-object-ado.md) объекта, не **записей** объекта. С помощью **записи** объекта, можно добавить поля и укажите значения в то же время. С **записей** объекта, необходимо создать поля при **набор записей** закрытым или откройте **записей** и присвоить значения поля.  
  
> [!NOTE]
>  Для новых **поле** объекты, добавленные **поля** коллекцию **записи** объекта, [значение](../../../ado/reference/ado-api/value-property-ado.md) свойство должно иметь значение перед любыми другими **поле** свойства могут быть указаны. Во-первых, конкретное значение для **значение** свойство, которое должна быть назначена и [обновление](../../../ado/reference/ado-api/update-method.md) на **поля** коллекцию с именем. Затем, другие свойства, такие как [тип](../../../ado/reference/ado-api/type-property-ado.md) или [атрибуты](../../../ado/reference/ado-api/attributes-property-ado.md) возможен. **Поле** объекты следующих типов данных (**DataTypeEnum**) не удается добавить **поля** коллекции и вызовет ошибку: **adArray**, **adChapter**, **adEmpty**, **adPropVariant**, и **adUserDefined**. Кроме того, следующие типы данных не поддерживаются ADO: **adIDispatch**, **adIUnknown**, и **adIVariant**. Для этих типов ошибок не происходит при добавлении, но использование может привести к непредсказуемым результатам, включая утечки памяти.  
  
## <a name="recordset"></a>набор записей  
 Если вы не установите [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойство перед вызовом **Append** метод, **CursorLocation** будет присвоено **adUseClient** () [CursorLocationEnum](../../../ado/reference/ado-api/cursorlocationenum.md) значение) автоматически в том случае, когда [откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md) метод [записей](../../../ado/reference/ado-api/recordset-object-ado.md) вызова объекта.  
  
 Ошибка времени выполнения возникает в том случае, если **Append** вызывается метод **поля** коллекции открытого **набор записей**, или на **записей** где [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) свойства. Можно добавить только поля, чтобы **записей** , не открыт и еще не был подключен к источнику данных. Это обычно происходит при **записей** объекта создается с помощью [CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md) метод или присвоенный переменной объекта.  
  
## <a name="record"></a>Записей  
 Ошибка времени выполнения не происходит, если **Append** вызывается метод **поля** коллекции открытого **записи**. Добавляется новое поле **поля** коллекцию **записи** объекта. Если **записи** является производным от **записей**, новое поле будет отсутствовать в **поля** коллекцию **записей** объекта.  
  
 Можно создать и к несуществующему полю **поля** коллекцию путем присвоения значения на объект поля, как, если она уже существует в коллекции. Назначение вызовет автоматическое создание и добавление элемента **поле** объекта и присваивания, будет завершен.  
  
 После добавления **поле** для **поля** коллекцию **записи** , вызовите **обновление** метод **поля**  коллекции, чтобы сохранить изменения.  
  
## <a name="applies-to"></a>Объект применения  
  
- [Коллекция Fields (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)  
- [Коллекция Parameters (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Append и CreateParameter методы (Visual Basic)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vb.md)   
 [Append и CreateParameter методы (Visual C++)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vc.md)   
 [Метод CreateParameter (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)   
 [Метод Delete (коллекция Fields ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Удаление метода (коллекция Parameters ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Удаление метода (объект Recordset ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [Метод Update](../../../ado/reference/ado-api/update-method.md)
