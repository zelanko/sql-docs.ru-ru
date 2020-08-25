---
description: Collections (синтаксис ADO для Visual C++)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: c1e7719277bd7b03dac00d315243a94c9b84ec01
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776213"
---
# <a name="collections-ado-for-visual-c-syntax"></a>Collections (синтаксис ADO для Visual C++)
## <a name="parameters"></a>Параметры  
  
### <a name="methods"></a>Методы  
  
```  
Append(IDispatch *Object);  
Delete(VARIANT Index);  
Refresh(void);  
```  
  
 Дополнительные сведения см. в разделе  
  
-   [Метод Append (ADO)](./append-method-ado.md)  
  
-   [Метод Delete (коллекция Parameters ADO)](./delete-method-ado-parameters-collection.md)  
  
-   [Метод Refresh (ADO)](./refresh-method-ado.md)  
  
### <a name="properties"></a>Свойства  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, _ADOParameter **ppvObject);  
```  
  
 Дополнительные сведения см. в разделе  
  
-   [Свойство Count (ADO)](./count-property-ado.md)  
  
-   [Свойство Item (ADO)](./item-property-ado.md)  
  
## <a name="fields"></a>Поля  
  
### <a name="methods"></a>Методы  
  
```  
Append(BSTR bstrName, DataTypeEnum Type, long DefinedSize, FieldAttributeEnum Attrib);  
Delete(VARIANT Index);  
Refresh(void);  
```  
  
 Дополнительные сведения см. в разделе  
  
-   [Метод Append (ADO)](./append-method-ado.md)  
  
-   [Метод Delete (коллекция Parameters ADO)](./delete-method-ado-parameters-collection.md)  
  
-   [Метод Refresh (ADO)](./refresh-method-ado.md)  
  
### <a name="properties"></a>Свойства  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, ADOField **ppvObject);  
```  
  
 Дополнительные сведения см. в разделе  
  
-   [Свойство Count (ADO)](./count-property-ado.md)  
  
-   [Свойство Item (ADO)](./item-property-ado.md)  
  
## <a name="errors"></a>ошибки  
  
### <a name="methods"></a>Методы  
  
```  
Clear(void);  
Refresh(void);  
```  
  
 Дополнительные сведения см. в разделе  
  
-   [Метод Clear (ADO)](./clear-method-ado.md)  
  
-   [Метод Refresh (ADO)](./refresh-method-ado.md)  
  
### <a name="properties"></a>Свойства  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, ADOError **ppvObject);  
```  
  
 Дополнительные сведения см. в разделе  
  
-   [Свойство Count (ADO)](./count-property-ado.md)  
  
-   [Свойство Item (ADO)](./item-property-ado.md)  
  
## <a name="properties"></a>Свойства  
  
### <a name="methods"></a>Методы  
  
```  
Refresh(void);  
```  
  
 Дополнительные сведения см. в разделе  
  
-   [Метод Refresh (ADO)](./refresh-method-ado.md)  
  
### <a name="properties"></a>Свойства  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, ADOProperty **ppvObject);  
```  
  
 Дополнительные сведения см. в разделе  
  
-   [Свойство Count (ADO)](./count-property-ado.md)  
  
-   [Свойство Item (ADO)](./item-property-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Коллекция Errors (ADO)](./errors-collection-ado.md)   
 [Коллекция Fields (ADO)](./fields-collection-ado.md)   
 [Коллекция Parameters (ADO)](./parameters-collection-ado.md)   
 [Коллекция Properties (ADO)](./properties-collection-ado.md)