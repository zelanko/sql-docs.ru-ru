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
ms.openlocfilehash: d493218f31965c04b5a64321c4a1bf87a2518f6f
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763795"
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
  
## <a name="applies-to"></a>Применяется к  
  
|||  
|-|-|  
|[Метод GetObjectOwner (ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)|[Метод GetPermissions (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)|  
|[Метод SetObjectOwner](../../../ado/reference/adox-api/setobjectowner-method.md)|[Метод SetPermissions (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)|
