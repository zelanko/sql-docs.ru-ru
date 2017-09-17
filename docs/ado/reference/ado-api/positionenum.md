---
title: "PositionEnum | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- PositionEnum
helpviewer_keywords:
- PositionEnum enumeration
ms.assetid: e69af0a5-3405-4b72-9c6e-6b188ff746fd
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c3f317b92d138f020a43f26d71cbadd0f0cd412e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="positionenum"></a>PositionEnum
Задает текущее положение указателя записи в [записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Константа|Значение|Description|  
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
