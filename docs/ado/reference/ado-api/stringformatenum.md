---
title: StringFormatEnum | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- StringFormatEnum
helpviewer_keywords:
- StringFormatEnum enumeration [ADO]
ms.assetid: 28f7d1ec-092b-4323-a39d-d3f882c6c81a
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ac774393a914c13171dfa13150ee708b316fbd03
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35282593"
---
# <a name="stringformatenum"></a>StringFormatEnum
Указывает формат при извлечении [записей](../../../ado/reference/ado-api/recordset-object-ado.md) как строка.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adClipString**|2|Разделяет строки по *RowDelimiter*, столбцов и *ColumnDelimiter*и пустых значений с *NullExpr*. Эти три параметра [GetString](../../../ado/reference/ado-api/getstring-method-ado.md) , не является допустимым только с *StringFormat* из **adClipString**.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.StringFormat.CLIPSTRING|  
  
## <a name="applies-to"></a>Объект применения  
 [Метод GetString (ADO)](../../../ado/reference/ado-api/getstring-method-ado.md)
