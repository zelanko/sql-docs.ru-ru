---
description: Метод CompareBookmarks (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 3c5e863a694aa63e568e388304d964752dbae325
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776073"
---
# <a name="comparebookmarks-method-ado"></a>Метод CompareBookmarks (ADO)
Сравнивает две закладки и возвращает значение, указывающее на их относительные значения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
result = recordset.CompareBookmarks(Bookmark1, Bookmark2)  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение [компаринум](./compareenum.md) , указывающее относительное расположение строки двух записей, представленных их закладками.  
  
#### <a name="parameters"></a>Параметры  
 *Bookmark1*  
 Закладка первой строки.  
  
 *Bookmark2*  
 Закладка второй строки.  
  
## <a name="remarks"></a>Remarks  
 Закладки должны применяться к одному и тому же объекту [Recordset](./recordset-object-ado.md) , а также к объекту **Recordset** и его [клону](./clone-method-ado.md). Вы не можете надежно сравнивать закладки из различных объектов **набора записей** , даже если они были созданы из одного и того же источника или команды. Также можно сравнивать закладки для объекта **набора записей** , базовый поставщик которого не поддерживает сравнения.  
  
 Закладка однозначно определяет строку в объекте **набора записей** . Чтобы получить закладку, используйте свойство [Bookmark](./bookmark-property-ado.md) текущей строки.  
  
 Поскольку тип данных закладки зависит от каждого поставщика, ADO предоставляет его как **вариант**. Например, SQL Server закладки имеют тип DBTYPE_R8 (**Double**). ADO будет предоставлять этот тип как **вариант** с подтипом **Double**.  
  
 При сравнении закладок ADO не пытается приведение типов. Значения просто передаются поставщику, где выполняется сравнение. Если закладки, передаваемые в метод **CompareBookmarks** , хранятся в переменных различных типов, он может создать следующую ошибку несоответствия типов: "аргументы имеют неверный тип, находятся вне допустимого диапазона или конфликтуют друг с другом".  
  
 Недопустимая или неправильно сформированная закладка приведет к ошибке.  
  
## <a name="applies-to"></a>Применение  
 [Объект Recordset (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода CompareBookmarks (Visual Basic)](./comparebookmarks-method-example-vb.md)   
 [Пример метода CompareBookmarks (Visual c++)](./comparebookmarks-method-example-vc.md)   
 [Свойство Bookmark (ADO)](./bookmark-property-ado.md)