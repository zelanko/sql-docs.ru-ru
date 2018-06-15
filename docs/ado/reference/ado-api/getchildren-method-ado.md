---
title: Метод GetChildren (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
ms.openlocfilehash: a920d0e7b45394f5714cd8f9df83751a322b9401
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35278853"
---
# <a name="getchildren-method-ado"></a>Метод GetChildren (ADO)
Возвращает [записей](../../../ado/reference/ado-api/recordset-object-ado.md) , строки которого представляют дочерние элементы коллекции [записи](../../../ado/reference/ado-api/record-object-ado.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set recordset = record.GetChildren  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **записей** объекта, для которой каждая строка представляет потомком текущего **записи** объекта. Например, потомки **записи** что представляет каталог будет файлы и подкаталоги, содержащиеся в родительском каталоге.  
  
## <a name="remarks"></a>Примечания  
 Поставщик определяет, какие столбцы существуют в возвращаемом **записей**. Например, поставщик документа всегда возвращает ресурс **записей**.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|[Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|
