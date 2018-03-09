---
title: "Пространства имен | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- namespaces in ADO
ms.assetid: efff5569-db52-451d-a039-2e74870534da
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c34bb680f7a066eeb694cf62fba39cabb0d4cbea
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="namespaces"></a>Пространства имен
Формат сохраняемости XML в ADO использует следующие четыре пространства имен.  
  
## <a name="remarks"></a>Remarks  
 Формат сохраняемости XML в ADO использует следующие четыре пространства имен.  
  
|Prefix|Описание|  
|------------|-----------------|  
|s|Ссылается на пространство имен «XML-данных», содержащее элементы и атрибуты, определяющие схему текущего набора записей.|  
|DT|Ссылается на спецификацию определения типа данных.|  
|rs|Ссылается на пространство имен, содержащие элементы и атрибуты, относящиеся к свойствам набора записей ADO и атрибуты.|  
|z|Ссылается на схему текущего набора строк.|  
  
 Клиент не следует добавлять свои собственные теги для этих пространств имен, как определено в спецификации. Например, клиент не должен определять пространство имен, что «urn: schemas-microsoft-com:rowset» и затем записать что-нибудь, например «rs: MyOwnTag.» Дополнительные сведения о пространствах имен см. в разделе [W3C по пространствам имен в XML](http://www.w3.org/TR/REC-xml-names/).  
  
> [!IMPORTANT]
>  Идентификатор для тега схемы должен быть «RowsetSchema» и пространство имен, используемое для ссылки на схему текущего набора строк должен указывать на «#RowsetSchema».  
  
 Обратите внимание, что префикс пространства имен — часть между двоеточием и знаком равенства, выбрано произвольно.  
  
```  
xmlns:rs="urn:schemas-microsoft-com:rowset"  
```  
  
 Пользователь может определять это может быть любое имя, при условии, что это имя используется согласованно во всех XML-документа. ADO всегда записывает «s», ««службы Reporting Services», «ТР» и «z», но эти имена префикс не жестко закодирована в компоненте загрузки.  
  
## <a name="see-also"></a>См. также  
 [Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
