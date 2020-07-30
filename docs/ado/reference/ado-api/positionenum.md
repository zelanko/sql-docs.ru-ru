---
title: Поситионенум | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- PositionEnum
helpviewer_keywords:
- PositionEnum enumeration
ms.assetid: e69af0a5-3405-4b72-9c6e-6b188ff746fd
author: rothja
ms.author: jroth
ms.openlocfilehash: 6a61dae9888628302da3326a1465f4182c49e39c
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87243225"
---
# <a name="positionenum"></a>PositionEnum
Задает текущую позиции указателя записи в [наборе записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adPosBOF**|–2|Указывает, что указатель текущей записи находится на BOF (то есть свойство [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) имеет **значение true**).|  
|**adPosEOF**|–3|Указывает, что указатель текущей записи находится в EOF (то есть свойство [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) имеет **значение true**).|  
|**adPosUnknown**|-1|Указывает, что **набор записей** пуст, Текущая заданная позицией неизвестна или поставщик не поддерживает свойство [примеры absolutepage](../../../ado/reference/ado-api/absolutepage-property-ado.md) или [примеры AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) .|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Константа|  
|--------------|  
|Адоенумс. позиционирование. BOF|  
|Адоенумс. расположение. EOF|  
|Адоенумс. позиционирование. неизвестно|  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Свойство AbsolutePage (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)  
    :::column-end:::
    :::column:::
        [Свойство AbsolutePosition (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)  
    :::column-end:::
:::row-end:::
