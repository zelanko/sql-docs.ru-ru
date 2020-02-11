---
title: Сеарчдиректионенум | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- SearchDirectionEnum
helpviewer_keywords:
- SearchDirectionEnum enumeration [ADO]
ms.assetid: 81272ae3-2165-4f4e-adfe-9ede0368cb17
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f8926e932317096cb3891cc8c480164268751cea
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67917003"
---
# <a name="searchdirectionenum"></a>SearchDirectionEnum
Указывает направление поиска записей в [наборе записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Постоянно|Значение|Description|  
|--------------|-----------|-----------------|  
|**адсеарчбакквард**|-1|Поиск в обратном направлении, остановка в начале **набора записей**. Если совпадение не найдено, указатель записи размещается по адресу [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md).|  
|**адсеарчфорвард**|1|Поиск вперед, остановка в конце **набора записей**. Если совпадение не найдено, указатель записи размещается на [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md).|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Постоянно|  
|--------------|  
|Адоенумс. Сеарчдиректион. назад|  
|Адоенумс. Сеарчдиректион. FORWARD|  
  
## <a name="applies-to"></a>Применяется к  
 [Метод Find (ADO)](../../../ado/reference/ado-api/find-method-ado.md)
