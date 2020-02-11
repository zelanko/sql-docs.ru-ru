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
ms.openlocfilehash: 16fdefcb06d2b1b90dfc3da39aaf6b1c9659debc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67965744"
---
# <a name="numericscale-property-adox"></a>Свойство NumericScale (ADOX)
Указывает Масштаб числового значения в столбце.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает и возвращает значение типа **Byte** , которое является масштабом значений данных в столбце, если свойство [Type](../../../ado/reference/adox-api/type-property-column-adox.md) имеет значение **аднумерик** или **аддеЦимал**. **NumericScale** игнорируется для всех других типов данных.  
  
## <a name="remarks"></a>Remarks  
 Значение по умолчанию равно нулю (0).  
  
 **NumericScale** доступен только для чтения для объектов [Column](../../../ado/reference/adox-api/column-object-adox.md) , уже добавленных в коллекцию.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Column (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример кода ADOX: пример свойства NumericScale и Precision (Visual Basic)](../../../ado/reference/adox-api/adox-code-example-numericscale-and-precision-properties-example-vb.md)   
 [Свойство Type (Column) (ADOX)](../../../ado/reference/adox-api/type-property-column-adox.md)
