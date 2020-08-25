---
description: Свойство MaxRecords (ADO)
title: Свойство MaxRecords (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::MaxRecords
helpviewer_keywords:
- MaxRecords property [ADO]
ms.assetid: 20c76571-8c9a-482c-a99e-726ab1d93f8b
author: rothja
ms.author: jroth
ms.openlocfilehash: 4431d9a8af8623150717474cd5429a772f86be8c
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88774453"
---
# <a name="maxrecords-property-ado"></a>Свойство MaxRecords (ADO)
Указывает максимальное число записей, возвращаемых в [набор записей](./recordset-object-ado.md) из запроса.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает значение **типа Long** , указывающее максимальное число возвращаемых записей. Значение по умолчанию равно нулю (**0**), что означает отсутствие ограничения.  
  
## <a name="remarks"></a>Remarks  
 Свойство **maxRecords** используется для ограничения количества записей, возвращаемых поставщиком из источника данных. Значение по умолчанию этого свойства равно нулю. Это означает, что поставщик возвращает все запрошенные записи.  
  
 Свойство **maxRecords** доступно для чтения и записи, когда **набор записей** закрывается и только для чтения, когда он открыт.  
  
## <a name="applies-to"></a>Применение  
 [Объект Recordset (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства MaxRecords (Visual Basic)](./maxrecords-property-example-vb.md)   
 [Пример свойства MaxRecords (Visual C++)](./maxrecords-property-example-vc.md)