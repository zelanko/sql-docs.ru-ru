---
title: Стреамопеноптионсенум | Документация Майкрософт
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67928686"
---
# <a name="streamopenoptionsenum"></a>StreamOpenOptionsEnum
Задает параметры для открытия объекта [потока](../../../ado/reference/ado-api/stream-object-ado.md) . Значения можно сочетать с операцией или.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adOpenStreamAsync**|1|Открывает объект **потока** в асинхронном режиме.|  
|**adOpenStreamFromRecord**|4|Определяет содержимое *исходного* параметра как уже открытый объект [Record](../../../ado/reference/ado-api/record-object-ado.md) . Поведение по умолчанию состоит в том, чтобы рассматривать *источник* как URL-адрес, указывающий непосредственно на узел в древовидной структуре. Открывается поток по умолчанию, связанный с этим узлом.|  
|**adOpenStreamUnspecified**|-1|По умолчанию. Указывает открытие объекта **потока** с параметрами по умолчанию.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Эти константы не имеют эквивалентов ADO/WFC.  
  
## <a name="applies-to"></a>Применяется к  
 [Метод Open (объект Stream ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)
