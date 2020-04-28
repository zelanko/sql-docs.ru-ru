---
title: Метод дочернего элемента (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::raw_GetChildren
- _Record::GetChildren
helpviewer_keywords:
- GetChildren method [ADO]
ms.assetid: b3f09bac-4f66-49f6-aa5a-6fbb4fb28338
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 84f1a2f7a80e17571f1b8ad3e63db640fb58dc19
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67932508"
---
# <a name="getchildren-method-ado"></a>Метод GetChildren (ADO)
Возвращает [набор записей](../../../ado/reference/ado-api/recordset-object-ado.md) , строки которого представляют дочерние элементы [записи](../../../ado/reference/ado-api/record-object-ado.md)коллекции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set recordset = record.GetChildren  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **Recordset** , для которого каждая строка представляет дочерний объект текущего объекта **Record** . Например, дочерние элементы **записи** , представляющей каталог, представляют собой файлы и подкаталоги, содержащиеся в родительском каталоге.  
  
## <a name="remarks"></a>Remarks  
 Поставщик определяет, какие столбцы существуют в возвращенном **наборе записей**. Например, поставщик источника документов всегда возвращает **набор записей**ресурсов.  
  
## <a name="applies-to"></a>Применяется к  
  
|||  
|-|-|  
|[Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|[Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|
