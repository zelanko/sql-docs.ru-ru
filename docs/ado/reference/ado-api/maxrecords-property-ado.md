---
title: Свойство MaxRecords (ADO) | Документы Microsoft
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
- Recordset15::MaxRecords
helpviewer_keywords:
- MaxRecords property [ADO]
ms.assetid: 20c76571-8c9a-482c-a99e-726ab1d93f8b
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1eb073548d3f2b7b9422b416cdcc5c20a7984a56
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="maxrecords-property-ado"></a>Свойство MaxRecords (ADO)
Указывает максимальное число записей, чтобы вернуться к [записей](../../../ado/reference/ado-api/recordset-object-ado.md) из запроса.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **длинные** значение, указывающее максимальное количество возвращаемых записей. По умолчанию равно нулю (**0**), что означает отсутствие ограничений.  
  
## <a name="remarks"></a>Замечания  
 Используйте **MaxRecords** свойство, чтобы ограничить количество записей, поставщик возвращает из источника данных. Значение по умолчанию этого свойства равно нулю, это означает, что поставщик возвращает все запрошенные записей.  
  
 **MaxRecords** свойство доступно для чтения/записи при **записей** будет закрыто, только для чтения при открытом.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства MaxRecords (Visual Basic)](../../../ado/reference/ado-api/maxrecords-property-example-vb.md)   
 [Пример свойства MaxRecords (Visual C++)](../../../ado/reference/ado-api/maxrecords-property-example-vc.md)   
