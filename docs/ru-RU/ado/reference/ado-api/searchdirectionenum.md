---
title: SearchDirectionEnum | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- SearchDirectionEnum
helpviewer_keywords:
- SearchDirectionEnum enumeration [ADO]
ms.assetid: 81272ae3-2165-4f4e-adfe-9ede0368cb17
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7f354c2069a1862a1b4d6b69b4db78516a292405
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="searchdirectionenum"></a>SearchDirectionEnum
Указывает направление поиска записей в [записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adSearchBackward**|-1|Выполняет поиск назад, остановка в начале **записей**. Если совпадение не найдено, указатель записи расположена на [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md).|  
|**adSearchForward**|1|Поиск вперед, остановка в конце **записей**. Если совпадение не найдено, указатель записи расположена на [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md).|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.SearchDirection.BACKWARD|  
|AdoEnums.SearchDirection.FORWARD|  
  
## <a name="applies-to"></a>Объект применения  
 [Метод Find (ADO)](../../../ado/reference/ado-api/find-method-ado.md)
