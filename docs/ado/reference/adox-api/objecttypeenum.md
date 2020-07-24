---
title: Обжекттипинум | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ObjectTypeEnum
helpviewer_keywords:
- ObjectTypeEnum enumeration [ADOX]
ms.assetid: 3fdecfca-aa91-4596-ad98-610f1b7f840b
author: rothja
ms.author: jroth
ms.openlocfilehash: fe7d97909a2d38e548a072245b08110b1d61eb3c
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86943166"
---
# <a name="objecttypeenum"></a>ObjectTypeEnum
Указывает тип объекта базы данных, для которого задаются разрешения или владение.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adPermObjColumn**|2|Объект является столбцом.|  
|**адпермобждатабасе**|3|Объект является базой данных.|  
|**адпермобжпроцедуре**|4|Объект является процедурой.|  
|**adPermObjProviderSpecific**|-1|Объект является типом, определенным поставщиком. Если параметр *ObjectType* имеет значение **адпермобжпровидерспеЦифик** и не указан *обжекттипеид* , возникнет ошибка.|  
|**адпермобжтабле**|1|Объект является таблицей.|  
|**adPermObjView**|5|Объект является представлением.|  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Метод GetObjectOwner (ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)  
        [Метод GetPermissions (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)  
    :::column-end:::
    :::column:::
        [Метод SetObjectOwner](../../../ado/reference/adox-api/setobjectowner-method.md)  
        [Метод SetPermissions (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)  
    :::column-end:::
:::row-end:::
