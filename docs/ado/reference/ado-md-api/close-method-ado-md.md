---
title: Close-метод (ADO MD) | Документы Microsoft
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
- Close
- Cellset::Close
helpviewer_keywords:
- Close method [ADO MD]
ms.assetid: a3aa594d-f9d4-4654-8625-ec20153ff5d9
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 03cf786407d12e4ff38ae7a58cedcb110af1734d
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="close-method-ado-md"></a>Close-метод (ADO MD)
Закрывает открытые набора ячеек.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Cellset.Close  
```  
  
## <a name="remarks"></a>Замечания  
 С помощью **закрыть** метод закрытия [ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) объекта будет освобождать связанные данные, включая данные в каком-либо связанных с [ячейки](../../../ado/reference/ado-md-api/cell-object-ado-md.md), [оси](../../../ado/reference/ado-md-api/axis-object-ado-md.md), [Позиции](../../../ado/reference/ado-md-api/position-object-ado-md.md), или [член](../../../ado/reference/ado-md-api/member-object-ado-md.md) объектов. Закрытие **ячеек** не удаляет его из памяти, можно изменить его параметры свойств и открыть его позже. Для полного устранения объекта из памяти, присвойте переменной объекта **ничего не**.  
  
 Позже можно вызвать [откройте](../../../ado/reference/ado-md-api/open-method-ado-md.md) метод, чтобы снова открыть **ячеек** с помощью той же или другой исходной строки. Хотя **ячеек** объект был закрыт, получение какие-либо свойства или вызов любых методов, которые ссылаются на базовые данные или метаданные, приведет к ошибке.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Cellset (многомерные объекты ADO)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Объект Axis (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)   
 [Объект ячейки (ADO MD)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)   
 [Объект члена (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)   
 [Метод Open (ADO MD)](../../../ado/reference/ado-md-api/open-method-ado-md.md)   
 [Позиция объекта (ADO MD)](../../../ado/reference/ado-md-api/position-object-ado-md.md)   
 [Свойство State (многомерные объекты ADO)](../../../ado/reference/ado-md-api/state-property-ado-md.md)
