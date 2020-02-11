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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 04c7b1d1cb5d07a300b82d13a7e80158498bbd5f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67965650"
---
# <a name="objecttypeenum"></a>ObjectTypeEnum
Указывает тип объекта базы данных, для которого задаются разрешения или владение.  
  
|Постоянно|Значение|Description|  
|--------------|-----------|-----------------|  
|**адпермобжколумн**|2|Объект является столбцом.|  
|**адпермобждатабасе**|3|Объект является базой данных.|  
|**адпермобжпроцедуре**|4|Объект является процедурой.|  
|**адпермобжпровидерспеЦифик**|-1|Объект является типом, определенным поставщиком. Если параметр *ObjectType* имеет значение **адпермобжпровидерспеЦифик** и не указан *обжекттипеид* , возникнет ошибка.|  
|**адпермобжтабле**|1|Объект является таблицей.|  
|**адпермобжвиев**|5|Объект является представлением.|  
  
## <a name="applies-to"></a>Применяется к  
  
|||  
|-|-|  
|[Метод GetObjectOwner (ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)|[Метод GetPermissions (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)|  
|[Метод SetObjectOwner](../../../ado/reference/adox-api/setobjectowner-method.md)|[Метод SetPermissions (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)|
