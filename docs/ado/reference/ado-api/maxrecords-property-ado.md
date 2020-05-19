---
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
ms.openlocfilehash: b9e4beaaa4b38a26089d1136d1b32090ea12231f
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82754376"
---
# <a name="maxrecords-property-ado"></a>Свойство MaxRecords (ADO)
Указывает максимальное число записей, возвращаемых в [набор записей](../../../ado/reference/ado-api/recordset-object-ado.md) из запроса.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает значение **типа Long** , указывающее максимальное число возвращаемых записей. Значение по умолчанию равно нулю (**0**), что означает отсутствие ограничения.  
  
## <a name="remarks"></a>Примечания  
 Свойство **maxRecords** используется для ограничения количества записей, возвращаемых поставщиком из источника данных. Значение по умолчанию этого свойства равно нулю. Это означает, что поставщик возвращает все запрошенные записи.  
  
 Свойство **maxRecords** доступно для чтения и записи, когда **набор записей** закрывается и только для чтения, когда он открыт.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства MaxRecords (Visual Basic)](../../../ado/reference/ado-api/maxrecords-property-example-vb.md)   
 [Пример свойства MaxRecords (Visual C++)](../../../ado/reference/ado-api/maxrecords-property-example-vc.md)   
