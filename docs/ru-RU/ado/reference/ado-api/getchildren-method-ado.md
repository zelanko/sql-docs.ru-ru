---
title: Метод GetChildren (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::raw_GetChildren
- _Record::GetChildren
helpviewer_keywords:
- GetChildren method [ADO]
ms.assetid: b3f09bac-4f66-49f6-aa5a-6fbb4fb28338
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 170f17c66ea05a3df7dc6135918d164bd66f993e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="getchildren-method-ado"></a>Метод GetChildren (ADO)
Возвращает [записей](../../../ado/reference/ado-api/recordset-object-ado.md) , строки которого представляют дочерние элементы коллекции [записи](../../../ado/reference/ado-api/record-object-ado.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set recordset = record.GetChildren  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **записей** объекта, для которой каждая строка представляет потомком текущего **записи** объекта. Например, потомки **записи** что представляет каталог будет файлы и подкаталоги, содержащиеся в родительском каталоге.  
  
## <a name="remarks"></a>Замечания  
 Поставщик определяет, какие столбцы существуют в возвращаемом **записей**. Например, поставщик документа всегда возвращает ресурс **записей**.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|[Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|
