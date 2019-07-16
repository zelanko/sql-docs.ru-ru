---
title: StreamOpenOptionsEnum | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- StreamOpenOptionsEnum
helpviewer_keywords:
- StreamOpenOptionsEnum enumeration [ADO]
ms.assetid: 85b6c57f-47ed-46ba-bd92-07882ae9e9d2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 562e79590a2a5f1f5e9bb609b9a0ad0ea8b2bfd9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67928686"
---
# <a name="streamopenoptionsenum"></a>StreamOpenOptionsEnum
Указывает параметры для открытия [Stream](../../../ado/reference/ado-api/stream-object-ado.md) объекта. Значения могут объединяться с помощью операции или.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adOpenStreamAsync**|1|Открывает **Stream** объекта в асинхронном режиме.|  
|**adOpenStreamFromRecord**|4|Определяет содержимое *источника* параметр будет уже открытого [записи](../../../ado/reference/ado-api/record-object-ado.md) объекта. Поведение по умолчанию — обрабатывать *источника* как URL-адрес, указывающий непосредственно к узлу в виде древовидной структуры. Открытие потока по умолчанию, связанные с этим узлом.|  
|**adOpenStreamUnspecified**|-1|По умолчанию. Указывает, открывающий **Stream** объекта с параметрами по умолчанию.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO и WFC  
 Эти константы не имеют эквивалентов ADO и WFC.  
  
## <a name="applies-to"></a>Объект применения  
 [Метод Open (объект Stream ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)
