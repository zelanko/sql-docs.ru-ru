---
description: StreamOpenOptionsEnum
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 80918159031787844330c4ddd92032e81a99c8c1
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777193"
---
# <a name="streamopenoptionsenum"></a>StreamOpenOptionsEnum
Задает параметры для открытия объекта [потока](./stream-object-ado.md) . Значения можно сочетать с операцией или.  
  
|Константа|Значение|Описание:|  
|--------------|-----------|-----------------|  
|**adOpenStreamAsync**|1|Открывает объект **потока** в асинхронном режиме.|  
|**adOpenStreamFromRecord**|4|Определяет содержимое *исходного* параметра как уже открытый объект [Record](./record-object-ado.md) . Поведение по умолчанию состоит в том, чтобы рассматривать *источник* как URL-адрес, указывающий непосредственно на узел в древовидной структуре. Открывается поток по умолчанию, связанный с этим узлом.|  
|**adOpenStreamUnspecified**|-1|По умолчанию. Указывает открытие объекта **потока** с параметрами по умолчанию.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Эти константы не имеют эквивалентов ADO/WFC.  
  
## <a name="applies-to"></a>Применение  
 [Метод Open (объект Stream ADO)](./open-method-ado-stream.md)