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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d5f7ca47177a953313ff983bb25f9178b73b4930
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67917606"
---
# <a name="positionenum"></a>PositionEnum
Задает текущую позиции указателя записи в [наборе записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Постоянно|Значение|Description|  
|--------------|-----------|-----------------|  
|**адпосбоф**|-2|Указывает, что указатель текущей записи находится на BOF (то есть свойство [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) имеет **значение true**).|  
|**адпосеоф**|-3|Указывает, что указатель текущей записи находится в EOF (то есть свойство [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) имеет **значение true**).|  
|**адпосункновн**|-1|Указывает, что **набор записей** пуст, Текущая заданная позицией неизвестна или поставщик не поддерживает свойство [примеры absolutepage](../../../ado/reference/ado-api/absolutepage-property-ado.md) или [примеры AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) .|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Постоянно|  
|--------------|  
|Адоенумс. позиционирование. BOF|  
|Адоенумс. расположение. EOF|  
|Адоенумс. позиционирование. неизвестно|  
  
## <a name="applies-to"></a>Применяется к  
  
|||  
|-|-|  
|[Свойство AbsolutePage (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)|[Свойство AbsolutePosition (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|
