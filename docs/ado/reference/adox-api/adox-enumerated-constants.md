---
title: ADOX перечисляемые константы | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- enumerated constants [ADOX]
ms.assetid: 9d91f511-d46f-44ef-97ef-77bf93836186
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a862168ffd8be5d7490a7151813bb6c1272f6d86
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35284783"
---
# <a name="adox-enumerated-constants"></a>ADOX перечисляемые константы
Чтобы упростить отладку, константы перечисления ADOX списка значение для каждой константы. Тем не менее это значение исключительно рекомендации и может меняться от одного выпуска ADOX в другой. Код только должны зависеть от имени, а не фактического значения перечислимых констант.  
  
 Определены следующие константы перечисления.  
  
|Перечисление|Описание|  
|-----------------|-----------------|  
|[ActionEnum](../../../ado/reference/adox-api/actionenum.md)|Указывает тип действия, выполняемые при **SetPermissions** вызывается.|  
|[AllowNullsEnum](../../../ado/reference/adox-api/allownullsenum.md)|Указывает, проиндексировано ли записи со значениями null.|  
|[ColumnAttributesEnum](../../../ado/reference/adox-api/columnattributesenum.md)|Задает характеристики **столбца**.|  
|[DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md)|Указывает тип данных **поле**, **параметр**, или **свойства**.|  
|[InheritTypeEnum](../../../ado/reference/adox-api/inherittypeenum.md)|Указывает, каким образом объекты будут наследовать разрешения, установленные с **SetPermissions**.|  
|[KeyTypeEnum](../../../ado/reference/adox-api/keytypeenum.md)|Указывает тип **ключ**: внешний, первичный или уникальный.|  
|[ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md)|Указывает тип объекта базы данных, для которого требуется задать разрешения или его владельца.|  
|[RightsEnum](../../../ado/reference/adox-api/rightsenum.md)|Указывает на объект права и разрешения для группы или пользователя.|  
|[RuleEnum](../../../ado/reference/adox-api/ruleenum.md)|Указывает правило, когда **ключ** удаляется.|  
|[SortOrderEnum](../../../ado/reference/adox-api/sortorderenum.md)|Задает последовательность сортировки для индексированного столбца.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ADOX](../../../ado/reference/adox-api/adox-api-reference.md)   
 [Расширения ADO для языка описания данных и безопасности (ADOX)](../../../ado/guide/extensions/ado-extensions-for-data-definition-language-and-security-adox.md)
