---
title: Метод CompareBookmarks (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CompareBookmarks
- Recordset20::CompareBookmarks
- Recordset20::raw_CompareBookmarks
helpviewer_keywords:
- CompareBookmarks method [ADO]
ms.assetid: d0b64286-2cc4-4a22-8f1d-9aefeebbcbc6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0d737c2f031fa3ba630eabb7e52dff0e056c3390
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67919590"
---
# <a name="comparebookmarks-method-ado"></a>Метод CompareBookmarks (ADO)
Сравнивает две закладки и возвращает значение, указывающее на их относительные значения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
result = recordset.CompareBookmarks(Bookmark1, Bookmark2)  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение [компаринум](../../../ado/reference/ado-api/compareenum.md) , указывающее относительное расположение строки двух записей, представленных их закладками.  
  
#### <a name="parameters"></a>Параметры  
 *Bookmark1*  
 Закладка первой строки.  
  
 *Bookmark2*  
 Закладка второй строки.  
  
## <a name="remarks"></a>Remarks  
 Закладки должны применяться к одному и тому же объекту [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) , а также к объекту **Recordset** и его [клону](../../../ado/reference/ado-api/clone-method-ado.md). Вы не можете надежно сравнивать закладки из различных объектов **набора записей** , даже если они были созданы из одного и того же источника или команды. Также можно сравнивать закладки для объекта **набора записей** , базовый поставщик которого не поддерживает сравнения.  
  
 Закладка однозначно определяет строку в объекте **набора записей** . Чтобы получить закладку, используйте свойство [Bookmark](../../../ado/reference/ado-api/bookmark-property-ado.md) текущей строки.  
  
 Поскольку тип данных закладки зависит от каждого поставщика, ADO предоставляет его как **вариант**. Например, SQL Server закладки имеют тип DBTYPE_R8 (**Double**). ADO будет предоставлять этот тип как **вариант** с подтипом **Double**.  
  
 При сравнении закладок ADO не пытается приведение типов. Значения просто передаются поставщику, где выполняется сравнение. Если закладки, передаваемые в метод **CompareBookmarks** , хранятся в переменных различных типов, он может создать следующую ошибку несоответствия типов: "аргументы имеют неверный тип, находятся вне допустимого диапазона или конфликтуют друг с другом".  
  
 Недопустимая или неправильно сформированная закладка приведет к ошибке.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример метода CompareBookmarks (Visual Basic)](../../../ado/reference/ado-api/comparebookmarks-method-example-vb.md)   
 [Пример метода CompareBookmarks (Visual c++)](../../../ado/reference/ado-api/comparebookmarks-method-example-vc.md)   
 [Свойство Bookmark (ADO)](../../../ado/reference/ado-api/bookmark-property-ado.md)
