---
title: Коллекции (ADO — синтаксис WFC) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- syntax indexes [ADO], ADO/WFC
- collections [ADO], ADO/WFC syntax
- ADO/WFC syntax index [ADO]
ms.assetid: 073f9a0e-c755-42dd-9f71-4647d68e331a
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 943fdce253fe7197d5ac8793502bfe707cbb10ea
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66699014"
---
# <a name="collections-ado---wfc-syntax"></a>Collections (ADO — синтаксис WFC)
**com.ms.wfc.data пакета**  
  
## <a name="parameters"></a>Параметры  
  
### <a name="methods"></a>Методы  
  
```  
public void append(com.ms.wfc.data.Parameter param)  
public void delete(int n)  
public void delete(String s)  
public void refresh()  
public Parameter getItem(int n)  
public Parameter getItem(String s)  
```  
  
### <a name="properties"></a>Свойства  
  
```  
public int getCount()  
```  
  
## <a name="fields"></a>Поля  
  
### <a name="methods"></a>Методы  
  
```  
public void append(String name, int type)  
public void append(String name, int type, int definedSize)  
public void append(String name, int type, int definedSize, int attrib)  
public void delete(int n)  
public void delete(String s)  
public void refresh()  
public com.ms.wfc.data.Field getItem(int n)  
public com.ms.wfc.data.Field getItem(String s)  
```  
  
### <a name="properties"></a>Свойства  
  
```  
public int getCount()  
```  
  
## <a name="errors"></a>ошибки  
  
### <a name="methods"></a>Методы  
  
```  
public void clear()  
public void refresh()  
public com.ms.wfc.data.Error getItem(int n)  
public com.ms.wfc.data.Error getItem(String s)  
```  
  
### <a name="properties"></a>Свойства  
  
```  
public int getCount()  
```  
  
## <a name="see-also"></a>См. также  
 [Коллекция Errors (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [Коллекция Fields (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Коллекция Parameters (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)
