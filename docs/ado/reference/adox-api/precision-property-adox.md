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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 596eaa30b1a46c93db26da976f997b2a0beae8aa
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47657702"
---
# <a name="precision-property-adox"></a>Свойство Precision (ADOX)
Указывает, максимальная точность значений данных в [столбец](../../../ado/reference/adox-api/column-object-adox.md).  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает и возвращает **Long** значение, максимальная точность значений данных в столбце при [тип](../../../ado/reference/adox-api/type-property-column-adox.md) свойство является числовым типом. **Точность** игнорируется для всех других типов данных.  
  
## <a name="remarks"></a>Примечания  
 Значение по умолчанию равно нулю (**0**).  
  
 Это свойство доступно только для чтения для [столбец](../../../ado/reference/adox-api/column-object-adox.md) объектов, уже добавлен в коллекцию.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Column (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Пример кода ADOX: Свойств NumericScale и Precision (Visual Basic)](../../../ado/reference/adox-api/adox-code-example-numericscale-and-precision-properties-example-vb.md)   
 [Свойство Type (Column) (ADOX)](../../../ado/reference/adox-api/type-property-column-adox.md)   
 [Объект Column (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)
