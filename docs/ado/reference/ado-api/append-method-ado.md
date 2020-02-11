---
title: Метод Append (ADO) | Документация Майкрософт
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
ms.openlocfilehash: 17fa0ff30e8dcdbf7ea67080f17c3e066bba8605
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67920678"
---
# <a name="append-method-ado"></a>Метод Append (ADO)
Добавляет объект в коллекцию. Если коллекция является [полями](../../../ado/reference/ado-api/fields-collection-ado.md), то перед добавлением в коллекцию можно создать новый объект [поля](../../../ado/reference/ado-api/field-object.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
collection.Append object  
fields.Append Name, Type, DefinedSize, Attrib, FieldValue  
```  
  
#### <a name="parameters"></a>Параметры  
 *набор*  
 Объект коллекции.  
  
 *полям*  
 Коллекция **Fields** .  
  
 *объектами*  
 Объектная переменная, представляющая объект, который необходимо добавить.  
  
 *Название*  
 **Строковое** значение, содержащее имя нового объекта **field** и не должно совпадать с именем любого другого объекта в *полях*.  
  
 *Тип*  
 Значение [дататипинум](../../../ado/reference/ado-api/datatypeenum.md) , значение по умолчанию которого равно **адемпти**, которое указывает тип данных нового поля. Следующие типы данных не поддерживаются ADO и не должны использоваться при добавлении новых полей в [объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md): **адидиспатч**, **адиункновн**, **адвариант**.  
  
 *DefinedSize*  
 Необязательный параметр. Значение **типа Long** , представляющее определенный размер (в символах или байтах) нового поля. Значение по умолчанию для этого параметра является производным от *типа*. Поля с *DefinedSize* размером более 255 байт рассматриваются как столбцы переменной длины. Значение по умолчанию для *DefinedSize* не указано.  
  
 *Атрибуты*  
 Необязательный параметр. Значение [фиелдаттрибутинум](../../../ado/reference/ado-api/fieldattributeenum.md) , для которого значение по умолчанию — **адфлддефаулт**, определяющее атрибуты для нового поля. Если это значение не указано, поле будет содержать атрибуты, производные от *типа*.  
  
 *FieldValue*  
 Необязательный параметр. **Вариант** , представляющий значение для нового поля. Если не указано, то поле добавляется со значением NULL.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="parameters-collection"></a>Коллекция Parameters  
 Необходимо задать свойство [Type](../../../ado/reference/ado-api/type-property-ado.md) объекта [Parameter](../../../ado/reference/ado-api/parameter-object.md) , прежде чем добавлять его в коллекцию [Parameters](../../../ado/reference/ado-api/parameters-collection-ado.md) . Если выбран тип данных переменной длины, необходимо также задать для свойства [size](../../../ado/reference/ado-api/size-property-ado-parameter.md) значение больше нуля.  
  
 Описание параметров самостоятельно сокращает число вызовов к поставщику и, таким образом, повышает производительность при использовании хранимых процедур или параметризованных запросов. Однако необходимо иметь представление о свойствах параметров, связанных с хранимой процедурой или параметризованным запросом, которые необходимо вызвать.  
  
 Используйте метод [CreateParameter](../../../ado/reference/ado-api/createparameter-method-ado.md) для создания объектов **параметров** с соответствующими параметрами свойств и используйте метод **append** , чтобы добавить их в коллекцию [Parameters](../../../ado/reference/ado-api/parameters-collection-ado.md) . Это позволяет задавать и возвращать значения параметров без вызова поставщика для сведений о параметрах. При записи в поставщик, который не предоставляет сведения о параметрах, необходимо использовать этот метод, чтобы вручную заполнить коллекцию **Parameters** , чтобы использовать параметры.  
  
## <a name="fields-collection"></a>Коллекция Fields  
 Параметр *FieldValue* допустим только при добавлении объекта **поля** в объект [Record](../../../ado/reference/ado-api/record-object-ado.md) , а не в объект **набора записей** . С объектом **Record** можно добавлять поля и предоставлять значения одновременно. При использовании объекта **Recordset** необходимо создать поля, пока **набор записей** будет закрыт, а затем открыть **набор записей** и присвоить значения полям.  
  
> [!NOTE]
>  Для новых объектов **field** , которые были добавлены к коллекции **Fields** объекта **Record** , необходимо задать свойство [value](../../../ado/reference/ado-api/value-property-ado.md) , прежде чем можно будет указать другие свойства **поля** . Во-первых, конкретное значение свойства **value** должно быть назначено и [Обновлено](../../../ado/reference/ado-api/update-method.md) в коллекции **Fields** с именем. Затем можно получить доступ к другим свойствам, например к [типу](../../../ado/reference/ado-api/type-property-ado.md) или [атрибутам](../../../ado/reference/ado-api/attributes-property-ado.md) . Объекты **полей** следующих типов данных (**дататипинум**) не могут быть добавлены в коллекцию **Fields** , и это приведет к ошибке: **адаррай**, **адчаптер**, **адемпти**, **адпропвариант**и **адусердефинед**. Кроме того, следующие типы данных не поддерживаются ADO: **адидиспатч**, **адиункновн**и **адивариант**. Для этих типов ошибка не будет возникать при добавлении, но использование может привести к непредсказуемым результатам, включая утечки памяти.  
  
## <a name="recordset"></a>набор записей  
 Если не задать свойство [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) перед вызовом метода **append** , **CursorLocation** будет иметь значение **адусеклиент** ( [курсорлокатионенум](../../../ado/reference/ado-api/cursorlocationenum.md) Value) автоматически при вызове метода [открытия](../../../ado/reference/ado-api/open-method-ado-recordset.md) объекта [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) .  
  
 Если метод **append** вызывается для коллекции **полей** открытого **набора записей**или для набора **записей** , где было задано свойство [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) , возникнет ошибка времени выполнения. Поля можно добавлять только в **набор записей** , который не является открытым и еще не подключен к источнику данных. Обычно это происходит, когда объект **набора записей** создается с помощью метода [CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md) или присваивается объектной переменной.  
  
## <a name="record"></a>Record  
 Ошибка времени выполнения не возникает, если метод **append** вызывается для коллекции **полей** открытой **записи**. Новое поле будет добавлено в коллекцию **полей** объекта **Record** . Если **запись** была получена из **набора записей**, новое поле не будет отображаться в коллекции **полей** объекта **Recordset** .  
  
 Несуществующее поле может быть создано и добавлено к коллекции **Fields** путем присвоения значения объекту поля, как если бы оно уже существовало в коллекции. Назначение активирует автоматическое создание и добавление объекта **поля** , после чего назначение будет завершено.  
  
 После добавления **поля** в коллекцию **Fields** объекта **Record** вызовите метод **Update** коллекции **Fields** , чтобы сохранить изменения.  
  
## <a name="applies-to"></a>Применяется к  
  
- [Коллекция Fields (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)  
- [Коллекция Parameters (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Примеры методов Append и CreateParameter (Visual Basic)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vb.md)   
 [Пример методов Append и CreateParameter (Visual c++)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vc.md)   
 [Метод CreateParameter (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)   
 [Метод Delete (коллекция полей ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Метод Delete (Коллекция параметров ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Метод Delete (набор записей ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [Метод Update](../../../ado/reference/ado-api/update-method.md)
