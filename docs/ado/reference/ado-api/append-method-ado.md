---
title: "Append-метод (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: _DynaCollection::Append
helpviewer_keywords: Append method [ADO]
ms.assetid: f8a9bbed-ba9c-4698-945d-317ad22d2e92
caps.latest.revision: "18"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 87c05e88325d3e00061ee57af80be65d9a7508ba
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="append-method-ado"></a>Append-метод (ADO)
Добавляет объект в коллекцию. Если коллекция [поля](../../../ado/reference/ado-api/fields-collection-ado.md), новый [поле](../../../ado/reference/ado-api/field-object.md) объект может быть создан, перед добавлением в коллекцию.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
collection.Append object  
fields.Append Name, Type, DefinedSize, Attrib, FieldValue  
```  
  
#### <a name="parameters"></a>Параметры  
 *коллекции*  
 Объект коллекции.  
  
 *поля*  
 Объект **поля** коллекции.  
  
 *объект*  
 Объектная переменная, представляющая объект для добавления.  
  
 *Название*  
 Объект **строка** значение, содержащее имя нового **поле** объекта, и не должны тем же именем как любой другой объект в *поля*.  
  
 *Тип*  
 Объект [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) значение, значение которого по умолчанию — **adEmpty**, который указывает тип данных нового поля. Следующие типы данных не поддерживаются ADO и следует не будет использоваться, когда добавление новых полей в [объекта набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md): **adIDispatch**, **adIUnknown**, **adVariant**.  
  
 *DefinedSize*  
 Необязательно. Объект **длинные** значение, представляющее заданный размер, в символах или байтах нового поля. Значение по умолчанию для этого параметра является производным от *типа*. Поля, которые имеют *DefinedSize* больше 255 байт рассматриваются как столбцы переменной длины. Значение по умолчанию для *DefinedSize* не указан.  
  
 *Attrib*  
 Необязательно. Объект [FieldAttributeEnum](../../../ado/reference/ado-api/fieldattributeenum.md) значение, значение которого по умолчанию — **adFldDefault**, который задает атрибуты для нового поля. Если это значение не задано, это поле будет содержать атрибутов, производных от *типа*.  
  
 *FieldValue*  
 Необязательно. Объект **Variant** , представляющий значение для нового поля. Если не указан, поле добавляется со значением null.  
  
## <a name="remarks"></a>Замечания  
  
## <a name="parameters-collection"></a>Коллекция Parameters  
 Необходимо задать [тип](../../../ado/reference/ado-api/type-property-ado.md) свойство [параметр](../../../ado/reference/ado-api/parameter-object.md) объекта перед его добавлением [параметры](../../../ado/reference/ado-api/parameters-collection-ado.md) коллекции. Если выбран тип данных переменной длины, необходимо также задать [размер](../../../ado/reference/ado-api/size-property-ado-parameter.md) значение больше нуля.  
  
 Описания параметров самостоятельно минимизирует число вызовов поставщика и соответственно, повышает производительность при использовании хранимой процедуры или параметризованные запросы. Тем не менее необходимо знать свойства параметров, связанных с помощью хранимой процедуры или параметризированного запроса, который требуется вызвать.  
  
 Используйте [CreateParameter](../../../ado/reference/ado-api/createparameter-method-ado.md) метод для создания **параметр** объектов с соответствующими параметрами свойств, а также с помощью **Append** метод, чтобы добавить их в [ Параметры](../../../ado/reference/ado-api/parameters-collection-ado.md) коллекции. Это позволяет задать и возвращать значения параметров без вызова метода поставщика для получения параметров. При создании поставщика, который не предоставляет сведения о параметрах, необходимо использовать этот метод для заполнения вручную **параметры** коллекции для использования во всех параметров.  
  
## <a name="fields-collection"></a>Коллекция Fields  
 *FieldValue* параметр допустим только при добавлении **поле** объект [запись](../../../ado/reference/ado-api/record-object-ado.md) объекта, не к **записей** объекта. С **записи** объекта, можно добавить поля и укажите значения в то же время. С **записей** объекта, необходимо создать поля при **набора записей** закрыта, и затем откройте **записей** и присвоения значений поля.  
  
> [!NOTE]
>  Для новых **поле** объектов, добавленных в **поля** коллекцию **запись** объекта, [значение](../../../ado/reference/ado-api/value-property-ado.md) свойство должно быть задано перед любыми другими **поле** можно задать свойства. Во-первых, конкретное значение для **значение** свойство должна быть назначена и [обновление](../../../ado/reference/ado-api/update-method.md) на **поля** коллекцию с именем. После этого другие свойства, такие как [тип](../../../ado/reference/ado-api/type-property-ado.md) или [атрибуты](../../../ado/reference/ado-api/attributes-property-ado.md) доступны. **Поле** объектов следующих типов данных (**DataTypeEnum**) не может быть добавлен к **поля** коллекции и вызовет ошибку: **adArray**, **adChapter**, **adEmpty**, **adPropVariant**, и **adUserDefined**. Кроме того, следующие типы данных не поддерживаются ADO: **adIDispatch**, **adIUnknown**, и **adIVariant**. Для этих типов ошибок не происходит при добавлении, но использование может привести к непредсказуемым результатам, включая утечки памяти.  
  
## <a name="recordset"></a>набор записей  
 Если вы не установите [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойство перед вызовом **Append** метода **CursorLocation** будет присвоено **adUseClient** () [CursorLocationEnum](../../../ado/reference/ado-api/cursorlocationenum.md) значение) автоматически при [откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md) метод [записей](../../../ado/reference/ado-api/recordset-object-ado.md) вызывается.  
  
 Ошибка во время выполнения возникает, если **Append** метод будет вызван на **поля** коллекции открытого **записей**, или на **набора записей** где [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) свойства. Можно добавлять только поля **записей** , не открыт и еще не был подключен к источнику данных. Это условие обычно выполняется при **записей** объекта создается с [CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md) метода или присвоенный переменной объекта.  
  
## <a name="record"></a>Записей  
 Ошибка во время выполнения не возникает, если **Append** метод будет вызван на **поля** коллекции открытого **записи**. Будет добавлено новое поле к **поля** коллекцию **записи** объекта. Если **запись** является производным от **записей**, новое поле не будет отображаться в **поля** коллекцию **записей** объекта.  
  
 Несуществующий поля могут создаваться и добавляемый **поля** коллекции путем присвоения значения полей объекта, как если бы она уже существует в коллекции. Назначение вызовет автоматическое создание и добавление из **поле** объекта и назначение будет завершено.  
  
 После добавления **поле** для **поля** коллекцию **запись** , вызовите **обновление** метод **поля**  коллекции для сохранения изменений.  
  
## <a name="applies-to"></a>Объект применения  
  
- [Коллекция Fields (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)  
- [Коллекция Parameters (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Добавление и пример CreateParameter методы (Visual Basic)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vb.md)   
 [Добавление и пример методы CreateParameter (VC ++)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vc.md)   
 [Метод CreateParameter (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)   
 [Метод Delete (ADO поля коллекции)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Удаление метода (коллекция параметров ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Удаление метода (набора записей ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [Метод Update](../../../ado/reference/ado-api/update-method.md)
