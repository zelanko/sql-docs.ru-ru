---
title: PositionEnum | Документация Майкрософт
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67917606"
---
# <a name="positionenum"></a>PositionEnum
Задает текущую позицию указателя записи в [записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adPosBOF**|-2|Указывает, что указатель текущей записи на BOF (то есть [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) свойство **True**).|  
|**adPosEOF**|–3|Указывает, что указатель текущей записи в конец файла (то есть [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) свойство **True**).|  
|**adPosUnknown**|-1|Указывает, что **записей** является пустым, неизвестен текущей позиции или поставщик не поддерживает [примеры AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) или [примеры AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) свойство.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO и WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.Position.BOF|  
|AdoEnums.Position.EOF|  
|AdoEnums.Position.UNKNOWN|  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Свойство AbsolutePage (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)|[Свойство AbsolutePosition (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|
