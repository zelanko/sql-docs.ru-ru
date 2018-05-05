---
title: Свойство NumericScale (ADOX) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Column::PutNumericScale
- _Column::GetNumericScale
- _Column::NumericScale
- _Column::put_NumericScale
- _Column::get_NumericScale
helpviewer_keywords:
- NumericScale property [ADOX]
ms.assetid: 573ee5d1-57c7-4a27-be79-a0e12944ad9b
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fdf5ce61c1be2940b289fc188c9d01123aeffd48
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="numericscale-property-adox"></a>Свойство NumericScale (ADOX)
Указывает шкалу числовых значений в столбце.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает и возвращает **байтов** значение, которое Масштаб значений данных в столбце при [тип](../../../ado/reference/adox-api/type-property-column-adox.md) свойство **adNumeric** или **adDecimal**. **NumericScale** игнорируется для всех других типов данных.  
  
## <a name="remarks"></a>Замечания  
 Значение по умолчанию равно нулю (0).  
  
 **NumericScale** доступно только для чтения для [столбца](../../../ado/reference/adox-api/column-object-adox.md) объектов уже добавлен в коллекцию.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Column (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)  
  
## <a name="see-also"></a>См. также  
 [ADOX кода примерах: NumericScale и точности свойства (Visual Basic)](../../../ado/reference/adox-api/adox-code-example-numericscale-and-precision-properties-example-vb.md)   
 [Свойство Type (Column) (ADOX)](../../../ado/reference/adox-api/type-property-column-adox.md)
