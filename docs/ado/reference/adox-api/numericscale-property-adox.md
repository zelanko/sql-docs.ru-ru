---
title: Свойство NumericScale (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 328170d487d3de11b9370825bc89e6bb5b799cd7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62710292"
---
# <a name="numericscale-property-adox"></a>Свойство NumericScale (ADOX)
Указывает масштаб числовых значений в столбце.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает и возвращает **байтов** значение, равное Масштаб значений данных в столбце при [тип](../../../ado/reference/adox-api/type-property-column-adox.md) свойство **adNumeric** или **adDecimal**. **NumericScale** учитывается для всех других типов данных.  
  
## <a name="remarks"></a>Примечания  
 Значение по умолчанию равно нулю (0).  
  
 **NumericScale** только для чтения для [столбец](../../../ado/reference/adox-api/column-object-adox.md) объектов, уже добавлен в коллекцию.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Column (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Пример кода ADOX: Свойств NumericScale и Precision (Visual Basic)](../../../ado/reference/adox-api/adox-code-example-numericscale-and-precision-properties-example-vb.md)   
 [Свойство Type (Column) (ADOX)](../../../ado/reference/adox-api/type-property-column-adox.md)
