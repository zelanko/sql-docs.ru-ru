---
title: Свойство Precision (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Column::put_Precision
- _Column::PutPrecision
- _Column::GetPrecision
- _Column::get_Precision
- _Column::Precision
helpviewer_keywords:
- Precision property [ADOX]
ms.assetid: 0e0ecbbf-d7de-49d4-a128-5a519ecd54ba
author: rothja
ms.author: jroth
ms.openlocfilehash: 67512b74e4c2b869cb7b1f9397462ce5566557a8
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763725"
---
# <a name="precision-property-adox"></a>Свойство Precision (ADOX)
Указывает максимальную точность значений данных в [столбце](../../../ado/reference/adox-api/column-object-adox.md).  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает и возвращает значение типа **Long** , которое является максимальной точностью значений данных в столбце, если свойство [Type](../../../ado/reference/adox-api/type-property-column-adox.md) имеет числовой тип. **Точность** не учитывается для всех остальных типов данных.  
  
## <a name="remarks"></a>Remarks  
 Значение по умолчанию равно нулю (**0**).  
  
 Это свойство доступно только для чтения для объектов [столбцов](../../../ado/reference/adox-api/column-object-adox.md) , уже добавленных в коллекцию.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Column (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Пример кода ADOX: пример свойства NumericScale и Precision (Visual Basic)](../../../ado/reference/adox-api/adox-code-example-numericscale-and-precision-properties-example-vb.md)   
 [Свойство Type (Column) (ADOX)](../../../ado/reference/adox-api/type-property-column-adox.md)   
 [Объект Column (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)
