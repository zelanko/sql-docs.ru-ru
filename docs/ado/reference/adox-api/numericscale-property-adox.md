---
description: Свойство NumericScale (ADOX)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 94b5a154bfed13485787d46c768a371e0cceb65e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439766"
---
# <a name="numericscale-property-adox"></a>Свойство NumericScale (ADOX)
Указывает Масштаб числового значения в столбце.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает и возвращает значение типа **Byte** , которое является масштабом значений данных в столбце, если свойство [Type](../../../ado/reference/adox-api/type-property-column-adox.md) имеет значение **аднумерик** или **аддеЦимал**. **NumericScale** игнорируется для всех других типов данных.  
  
## <a name="remarks"></a>Remarks  
 Значение по умолчанию равно нулю (0).  
  
 **NumericScale** доступен только для чтения для объектов [Column](../../../ado/reference/adox-api/column-object-adox.md) , уже добавленных в коллекцию.  
  
## <a name="applies-to"></a>Применение  
 [Объект Column (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример кода ADOX: пример свойства NumericScale и Precision (Visual Basic)](../../../ado/reference/adox-api/adox-code-example-numericscale-and-precision-properties-example-vb.md)   
 [Свойство Type (Column) (ADOX)](../../../ado/reference/adox-api/type-property-column-adox.md)
