---
title: Перечисляемые константы ADOX | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- enumerated constants [ADOX]
ms.assetid: 9d91f511-d46f-44ef-97ef-77bf93836186
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bdbd67d5e4d7d4647b92b32590a5258de038c80f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47729482"
---
# <a name="adox-enumerated-constants"></a>ADOX Enumerated Constants
Для целей отладки, константы ADOX перечисления списка значение для каждой константы. Тем не менее это значение исключительно рекомендации и может отличаться от одного выпуска ADOX на другой. Ваш код должен основываться только на имя, а не фактического значения, перечислимых констант.  
  
 Определены следующие константы перечисления.  
  
|Перечисление|Описание|  
|-----------------|-----------------|  
|[ActionEnum](../../../ado/reference/adox-api/actionenum.md)|Указывает тип действия, выполняемые при **SetPermissions** вызывается.|  
|[AllowNullsEnum](../../../ado/reference/adox-api/allownullsenum.md)|Указывает, проиндексировано ли записи со значениями null.|  
|[ColumnAttributesEnum](../../../ado/reference/adox-api/columnattributesenum.md)|Указывает характеристики **столбец**.|  
|[DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md)|Указывает тип данных **поле**, **параметр**, или **свойство**.|  
|[InheritTypeEnum](../../../ado/reference/adox-api/inherittypeenum.md)|Указывает, как объекты наследуют разрешения, установленные с **SetPermissions**.|  
|[KeyTypeEnum](../../../ado/reference/adox-api/keytypeenum.md)|Указывает тип **ключ**: внешний, первичный или уникальный.|  
|[ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md)|Указывает тип объекта базы данных, для которого требуется задать разрешения или владельцы.|  
|[RightsEnum](../../../ado/reference/adox-api/rightsenum.md)|Указывает на объект права и разрешения для группы или пользователя.|  
|[RuleEnum](../../../ado/reference/adox-api/ruleenum.md)|Указывает правило, когда выполните **ключ** удаляется.|  
|[SortOrderEnum](../../../ado/reference/adox-api/sortorderenum.md)|Указывает последовательность сортировки для индексированного столбца.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ADOX](../../../ado/reference/adox-api/adox-api-reference.md)   
 [Расширения ADO для языка описания данных и безопасности (ADOX)](../../../ado/guide/extensions/ado-extensions-for-data-definition-language-and-security-adox.md)
