---
description: StringFormatEnum
title: Стрингформатенум | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 90c6214caa0adc1c11cdc0660b65795624919e51
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777143"
---
# <a name="stringformatenum"></a>StringFormatEnum
Задает формат при извлечении [набора записей](./recordset-object-ado.md) в виде строки.  
  
|Константа|Значение|Описание:|  
|--------------|-----------|-----------------|  
|**adClipString**|2|Отделяет строки от *RowDelimiter*, Columns по *ColumnDelimiter*и значения NULL значениями *нуллекспр*. Эти три параметра метода [GetString](./getstring-method-ado.md) допустимы только с *StringFormat* **адклипстринг**.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Константа|  
|--------------|  
|Адоенумс. StringFormat. КЛИПСТРИНГ|  
  
## <a name="applies-to"></a>Применение  
 [Метод GetString (ADO)](./getstring-method-ado.md)