---
description: Свойство Precision (ADOX)
title: Свойство Precision (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 4f0126da4e68ee84d9a8f155ee1dc50a89ab4646
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88983715"
---
# <a name="precision-property-adox"></a>Свойство Precision (ADOX)
Указывает максимальную точность значений данных в [столбце](./column-object-adox.md).  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает и возвращает значение типа **Long** , которое является максимальной точностью значений данных в столбце, если свойство [Type](./type-property-column-adox.md) имеет числовой тип. **Точность** не учитывается для всех остальных типов данных.  
  
## <a name="remarks"></a>Remarks  
 Значение по умолчанию равно нулю (**0**).  
  
 Это свойство доступно только для чтения для объектов [столбцов](./column-object-adox.md) , уже добавленных в коллекцию.  
  
## <a name="applies-to"></a>Применение  
 [Объект Column (ADOX)](./column-object-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Пример кода ADOX: пример свойства NumericScale и Precision (Visual Basic)](./adox-code-example-numericscale-and-precision-properties-example-vb.md)   
 [Свойство Type (Column) (ADOX)](./type-property-column-adox.md)   
 [Объект Column (ADOX)](./column-object-adox.md)