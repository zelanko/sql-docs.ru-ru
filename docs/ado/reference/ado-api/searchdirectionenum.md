---
description: SearchDirectionEnum
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 918261998fec061f8f977a8a2dfc614166f564f6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442166"
---
# <a name="searchdirectionenum"></a>SearchDirectionEnum
Указывает направление поиска записей в [наборе записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adSearchBackward**|-1|Поиск в обратном направлении, остановка в начале **набора записей**. Если совпадение не найдено, указатель записи размещается по адресу [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md).|  
|**adSearchForward**|1|Поиск вперед, остановка в конце **набора записей**. Если совпадение не найдено, указатель записи размещается на [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md).|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Константа|  
|--------------|  
|Адоенумс. Сеарчдиректион. назад|  
|Адоенумс. Сеарчдиректион. FORWARD|  
  
## <a name="applies-to"></a>Применение  
 [Метод Find (ADO)](../../../ado/reference/ado-api/find-method-ado.md)
