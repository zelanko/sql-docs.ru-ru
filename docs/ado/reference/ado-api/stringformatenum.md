---
title: StringFormatEnum | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- StringFormatEnum
helpviewer_keywords:
- StringFormatEnum enumeration [ADO]
ms.assetid: 28f7d1ec-092b-4323-a39d-d3f882c6c81a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 85bef64902f014e7b5269d6df328128bc8fe8d6e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67937881"
---
# <a name="stringformatenum"></a>StringFormatEnum
Задает формат при извлечении [записей](../../../ado/reference/ado-api/recordset-object-ado.md) как строка.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adClipString**|2|Разделяет строки по *RowDelimiter*, столбцы по *ColumnDelimiter*и значения, null *NullExpr*. Эти три параметра [GetString](../../../ado/reference/ado-api/getstring-method-ado.md) не является допустимым только с *StringFormat* из **adClipString**.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO и WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.StringFormat.CLIPSTRING|  
  
## <a name="applies-to"></a>Объект применения  
 [Метод GetString (ADO)](../../../ado/reference/ado-api/getstring-method-ado.md)
