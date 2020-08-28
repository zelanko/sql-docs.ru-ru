---
description: Collections (синтаксис ADO для Visual C++)
title: Коллекции (синтаксис ADO для Visual C++) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: b4bc59facd753bf6d36c3a79d06a4efe29e7c235
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88975385"
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
  
## <a name="errors"></a>Ошибки  
  
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