---
title: Состояние свойства (ADO MD) | Документы Microsoft
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
- State
- Cellset::State
helpviewer_keywords:
- State property [ADO MD]
ms.assetid: 06d480ca-9eb6-4570-a45d-a73539bddd32
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 975a9354734e0f6e5d0a2502b89b43c886be5fa3
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35284563"
---
# <a name="state-property-ado-md"></a>Свойство State (ADO MD)
Указывает текущее состояние набора ячеек.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **длинные** целое число, указывающее текущее состояние [ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) объекта и доступно только для чтения. Допустимы следующие значения: **adStateClosed** (0) и **adStateOpen** (1).  
  
## <a name="remarks"></a>Примечания  
 Для использования [ObjectStateEnum](../../../ado/reference/ado-api/objectstateenum.md) имена констант, необходимо иметь ADO библиотеки типов, на которые ссылается проект. В разделе [с помощью ADO с ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md) для получения дополнительной информации.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Cellset (многомерные объекты ADO)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Close-метод (ADO MD)](../../../ado/reference/ado-md-api/close-method-ado-md.md)   
 [Метод Open (многомерные объекты ADO)](../../../ado/reference/ado-md-api/open-method-ado-md.md)
