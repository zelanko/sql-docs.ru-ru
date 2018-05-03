---
title: Свойство точности (ADOX) | Документы Microsoft
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
- _Column::put_Precision
- _Column::PutPrecision
- _Column::GetPrecision
- _Column::get_Precision
- _Column::Precision
helpviewer_keywords:
- Precision property [ADOX]
ms.assetid: 0e0ecbbf-d7de-49d4-a128-5a519ecd54ba
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 73ea0021a6cb74fb7e3e98009be3566270d783e9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="precision-property-adox"></a>Свойство точности (ADOX)
Указывает, максимальная точность значений данных в [столбца](../../../ado/reference/adox-api/column-object-adox.md).  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает и возвращает **длинные** значение, максимальная точность значений данных в столбце при [тип](../../../ado/reference/adox-api/type-property-column-adox.md) свойство имеет числовой тип. **Точность** игнорируется для всех других типов данных.  
  
## <a name="remarks"></a>Замечания  
 Значение по умолчанию равно нулю (**0**).  
  
 Это свойство доступно только для чтения для [столбца](../../../ado/reference/adox-api/column-object-adox.md) объектов уже добавлен в коллекцию.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Column (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)  
  
## <a name="see-also"></a>См. также  
 [ADOX кода примерах: NumericScale и точности свойства (Visual Basic)](../../../ado/reference/adox-api/adox-code-example-numericscale-and-precision-properties-example-vb.md)   
 [Свойство Type (столбец) (ADOX)](../../../ado/reference/adox-api/type-property-column-adox.md)   
 [Объект Column (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)
