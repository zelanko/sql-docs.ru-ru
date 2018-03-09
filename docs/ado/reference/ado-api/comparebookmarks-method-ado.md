---
title: "Метод CompareBookmarks (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- CompareBookmarks
- Recordset20::CompareBookmarks
- Recordset20::raw_CompareBookmarks
helpviewer_keywords:
- CompareBookmarks method [ADO]
ms.assetid: d0b64286-2cc4-4a22-8f1d-9aefeebbcbc6
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 431ffdb1a2be03404b4d0c3636f547b6c8cf8514
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="comparebookmarks-method-ado"></a>Метод CompareBookmarks (ADO)
Сравнивает две закладки и возвращает сведения об их относительных значениях.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
result = recordset.CompareBookmarks(Bookmark1, Bookmark2)  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает [CompareEnum](../../../ado/reference/ado-api/compareenum.md) значение, указывающее позицию строки относительный две записи, представленный закладок.  
  
#### <a name="parameters"></a>Параметры  
 *Bookmark1*  
 Закладка первой строки.  
  
 *Bookmark2*  
 Закладка, второй строки.  
  
## <a name="remarks"></a>Remarks  
 Закладки необходимо применить к тому же [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта, или **записей** объекта и его [клон](../../../ado/reference/ado-api/clone-method-ado.md). Не удается сравнить надежно закладки из различных **записей** объектов, даже если они были созданы из одного источника или команды. И не может сравнить закладок для **записей** объект, базовый поставщик не поддерживает сравнение.  
  
 Закладка уникально идентифицирует строки в **записей** объекта. Используйте [закладки](../../../ado/reference/ado-api/bookmark-property-ado.md) свойство текущей строки, чтобы получить его закладки.  
  
 Так как тип данных закладки является специфичным для каждого поставщика, ADO предоставляет его как **Variant**. Например, закладки SQL Server являются типом DBTYPE_R8 (**двойные**). ADO будет представлять этот тип как **Variant** с подтипом **двойные**.  
  
 При сравнении закладки, ADO, выполняется приведение любого типа. Значения, просто передаются поставщику которых происходит сравнение. Если передаваемый закладки **CompareBookmarks** метод сохраняются в переменных различных типов, оно может создавать следующие ошибки несоответствия типов: «аргументы имеют неправильный тип, выходят за пределы допустимого диапазона или конфликтующих друг с другом.»  
  
 Закладка, которая не является допустимым или неправильно сформирован приведет к ошибке.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода CompareBookmarks (Visual Basic)](../../../ado/reference/ado-api/comparebookmarks-method-example-vb.md)   
 [Пример метода CompareBookmarks (VC ++)](../../../ado/reference/ado-api/comparebookmarks-method-example-vc.md)   
 [Свойство Bookmark (ADO)](../../../ado/reference/ado-api/bookmark-property-ado.md)
