---
title: PositionEnum | Документы Microsoft
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
- PositionEnum
helpviewer_keywords:
- PositionEnum enumeration
ms.assetid: e69af0a5-3405-4b72-9c6e-6b188ff746fd
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7c44bea1a7294b12992a7f2f76abac932f0921cf
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="positionenum"></a>PositionEnum
Задает текущее положение указателя записи в [записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adPosBOF**|-2|Указывает, что указатель текущей записи на BOF (то есть [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) свойство **True**).|  
|**adPosEOF**|–3|Указывает, что указатель текущей записи в конец файла (то есть [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) свойство **True**).|  
|**adPosUnknown**|-1|Указывает, что **записей** является пустым, неизвестна текущей позиции или поставщик не поддерживает [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) или [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) свойство.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
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
