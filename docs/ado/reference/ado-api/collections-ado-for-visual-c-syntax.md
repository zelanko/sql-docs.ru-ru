---
title: "Коллекции (ADO для синтаксиса Visual C++) | Документы Microsoft"
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
dev_langs: C++
helpviewer_keywords:
- ADO for Visual C++ syntax [ADO]
- syntax indexes [ADO], ADO for Visual C++ syntax
- collections [ADO], ADO for Visual C++ syntax
ms.assetid: 6a0109a0-f2d9-4f7c-8e1e-42763f9acaea
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 58d14610c2d7cbebfddd8d9312cc218d4fd91bbe
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="collections-ado-for-visual-c-syntax"></a>Коллекции (ADO для синтаксиса Visual C++)
## <a name="parameters"></a>Параметры  
  
### <a name="methods"></a>Методы  
  
```  
Append(IDispatch *Object);  
Delete(VARIANT Index);  
Refresh(void);  
```  
  
 Дополнительные сведения см. в разделе  
  
-   [Метод Append (ADO)](../../../ado/reference/ado-api/append-method-ado.md)  
  
-   [Метод Delete (коллекция Parameters ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)  
  
-   [Метод Refresh (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)  
  
### <a name="properties"></a>Свойства  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, _ADOParameter **ppvObject);  
```  
  
 Дополнительные сведения см. в разделе  
  
-   [Свойство Count (ADO)](../../../ado/reference/ado-api/count-property-ado.md)  
  
-   [Свойство Item (ADO)](../../../ado/reference/ado-api/item-property-ado.md)  
  
## <a name="fields"></a>Поля  
  
### <a name="methods"></a>Методы  
  
```  
Append(BSTR bstrName, DataTypeEnum Type, long DefinedSize, FieldAttributeEnum Attrib);  
Delete(VARIANT Index);  
Refresh(void);  
```  
  
 Дополнительные сведения см. в разделе  
  
-   [Метод Append (ADO)](../../../ado/reference/ado-api/append-method-ado.md)  
  
-   [Метод Delete (коллекция Parameters ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)  
  
-   [Метод Refresh (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)  
  
### <a name="properties"></a>Свойства  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, ADOField **ppvObject);  
```  
  
 Дополнительные сведения см. в разделе  
  
-   [Свойство Count (ADO)](../../../ado/reference/ado-api/count-property-ado.md)  
  
-   [Свойство Item (ADO)](../../../ado/reference/ado-api/item-property-ado.md)  
  
## <a name="errors"></a>ошибки  
  
### <a name="methods"></a>Методы  
  
```  
Clear(void);  
Refresh(void);  
```  
  
 Дополнительные сведения см. в разделе  
  
-   [Метод Clear (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)  
  
-   [Метод Refresh (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)  
  
### <a name="properties"></a>Свойства  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, ADOError **ppvObject);  
```  
  
 Дополнительные сведения см. в разделе  
  
-   [Свойство Count (ADO)](../../../ado/reference/ado-api/count-property-ado.md)  
  
-   [Свойство Item (ADO)](../../../ado/reference/ado-api/item-property-ado.md)  
  
## <a name="properties"></a>Свойства  
  
### <a name="methods"></a>Методы  
  
```  
Refresh(void);  
```  
  
 Дополнительные сведения см. в разделе  
  
-   [Метод Refresh (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)  
  
### <a name="properties"></a>Свойства  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, ADOProperty **ppvObject);  
```  
  
 Дополнительные сведения см. в разделе  
  
-   [Свойство Count (ADO)](../../../ado/reference/ado-api/count-property-ado.md)  
  
-   [Свойство Item (ADO)](../../../ado/reference/ado-api/item-property-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Коллекция ошибок (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [Коллекция Fields (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Коллекция параметров (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
