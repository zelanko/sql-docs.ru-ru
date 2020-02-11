---
title: Коллекции (синтаксис ADO для Visual C++) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
dev_langs:
- C++
helpviewer_keywords:
- ADO for Visual C++ syntax [ADO]
- syntax indexes [ADO], ADO for Visual C++ syntax
- collections [ADO], ADO for Visual C++ syntax
ms.assetid: 6a0109a0-f2d9-4f7c-8e1e-42763f9acaea
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f18884c7a1aabe138408cca7eb529f4f21120330
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67919911"
---
# <a name="collections-ado-for-visual-c-syntax"></a>Collections (синтаксис ADO для Visual C++)
## <a name="parameters"></a>Параметры  
  
### <a name="methods"></a>Методы  
  
```  
Append(IDispatch *Object);  
Delete(VARIANT Index);  
Refresh(void);  
```  
  
 Для получения дополнительных сведений см.  
  
-   [Метод Append (ADO)](../../../ado/reference/ado-api/append-method-ado.md)  
  
-   [Метод Delete (коллекция Parameters ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)  
  
-   [Метод Refresh (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)  
  
### <a name="properties"></a>Свойства  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, _ADOParameter **ppvObject);  
```  
  
 Для получения дополнительных сведений см.  
  
-   [Свойство Count (ADO)](../../../ado/reference/ado-api/count-property-ado.md)  
  
-   [Свойство Item (ADO)](../../../ado/reference/ado-api/item-property-ado.md)  
  
## <a name="fields"></a>Поля  
  
### <a name="methods"></a>Методы  
  
```  
Append(BSTR bstrName, DataTypeEnum Type, long DefinedSize, FieldAttributeEnum Attrib);  
Delete(VARIANT Index);  
Refresh(void);  
```  
  
 Для получения дополнительных сведений см.  
  
-   [Метод Append (ADO)](../../../ado/reference/ado-api/append-method-ado.md)  
  
-   [Метод Delete (коллекция Parameters ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)  
  
-   [Метод Refresh (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)  
  
### <a name="properties"></a>Свойства  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, ADOField **ppvObject);  
```  
  
 Для получения дополнительных сведений см.  
  
-   [Свойство Count (ADO)](../../../ado/reference/ado-api/count-property-ado.md)  
  
-   [Свойство Item (ADO)](../../../ado/reference/ado-api/item-property-ado.md)  
  
## <a name="errors"></a>ошибки  
  
### <a name="methods"></a>Методы  
  
```  
Clear(void);  
Refresh(void);  
```  
  
 Для получения дополнительных сведений см.  
  
-   [Метод Clear (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)  
  
-   [Метод Refresh (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)  
  
### <a name="properties"></a>Свойства  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, ADOError **ppvObject);  
```  
  
 Для получения дополнительных сведений см.  
  
-   [Свойство Count (ADO)](../../../ado/reference/ado-api/count-property-ado.md)  
  
-   [Свойство Item (ADO)](../../../ado/reference/ado-api/item-property-ado.md)  
  
## <a name="properties"></a>Свойства  
  
### <a name="methods"></a>Методы  
  
```  
Refresh(void);  
```  
  
 Для получения дополнительных сведений см.  
  
-   [Метод Refresh (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)  
  
### <a name="properties"></a>Свойства  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, ADOProperty **ppvObject);  
```  
  
 Для получения дополнительных сведений см.  
  
-   [Свойство Count (ADO)](../../../ado/reference/ado-api/count-property-ado.md)  
  
-   [Свойство Item (ADO)](../../../ado/reference/ado-api/item-property-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Коллекция Errors (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [Коллекция Fields (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Коллекция Parameters (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
