---
title: Свойство UpdateRule (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Key::GetUpdateRule
- _Key::get_UpdateRule
- _Key::PutUpdateRule
- _Key::put_UpdateRule
- _Key::UpdateRule
helpviewer_keywords:
- UpdateRule property [ADOX]
ms.assetid: f4e21060-40cb-4790-8611-4086a092dda2
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: ab8bed66cf459bcbf5cdc8f3a645eb25d4c01112
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66705806"
---
# <a name="updaterule-property-adox"></a>Свойство UpdateRule (ADOX)
Указывает выполнить действие, когда первичный [ключ](../../../ado/reference/adox-api/key-object-adox.md) обновляется.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает и возвращает **Long** значение, которое может принимать одно из [RuleEnum](../../../ado/reference/adox-api/ruleenum.md) константы. Значение по умолчанию — **adRINone**.  
  
## <a name="remarks"></a>Примечания  
 Это свойство доступно только для чтения на [ключ](../../../ado/reference/adox-api/key-object-adox.md) объектов, уже добавленный в коллекцию.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Key (ADOX)](../../../ado/reference/adox-api/key-object-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры метода Append коллекции Keys, свойства Type объекта Key, а также примеры свойств RelatedColumn, RelatedTable и UpdateRule (Visual Basic)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)
