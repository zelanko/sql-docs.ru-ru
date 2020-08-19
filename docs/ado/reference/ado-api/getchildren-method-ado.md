---
description: Метод GetChildren (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 906c20d19143f4f1e8fe0b6c1e91585893acfa5d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443586"
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
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
    :::column-end:::
    :::column:::
        [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
    :::column-end:::
:::row-end:::
