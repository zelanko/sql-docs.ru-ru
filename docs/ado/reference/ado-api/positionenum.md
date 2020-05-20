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
ms.openlocfilehash: 57a440a97dcdf1c0fddcff8017e0c2d04967b92d
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763345"
---
# <a name="positionenum"></a>PositionEnum
Задает текущую позиции указателя записи в [наборе записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adPosBOF**|-2|Указывает, что указатель текущей записи находится на BOF (то есть свойство [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) имеет **значение true**).|  
|**adPosEOF**|–3|Указывает, что указатель текущей записи находится в EOF (то есть свойство [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) имеет **значение true**).|  
|**adPosUnknown**|-1|Указывает, что **набор записей** пуст, Текущая заданная позицией неизвестна или поставщик не поддерживает свойство [примеры absolutepage](../../../ado/reference/ado-api/absolutepage-property-ado.md) или [примеры AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) .|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Константа|  
|--------------|  
|Адоенумс. позиционирование. BOF|  
|Адоенумс. расположение. EOF|  
|Адоенумс. позиционирование. неизвестно|  
  
## <a name="applies-to"></a>Применяется к  
  
|||  
|-|-|  
|[Свойство AbsolutePage (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)|[Свойство AbsolutePosition (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|
