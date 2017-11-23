---
title: "Метод GetChildren (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Record::raw_GetChildren
- _Record::GetChildren
helpviewer_keywords: GetChildren method [ADO]
ms.assetid: b3f09bac-4f66-49f6-aa5a-6fbb4fb28338
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 46f9af9b4cb1b4648acc75389f7d75cccdc46b96
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
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
