---
title: Набор строк DISCOVER_LITERALS | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DISCOVER_LITERALS
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_LITERALS rowset
ms.assetid: 1bf0a2e2-a419-4c25-b271-37dfa44de2ea
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e218c03cd6d2f8dbf06501dd18a2c4c3e4977eca
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48063220"
---
# <a name="discoverliterals-rowset"></a>Набор строк DISCOVER_LITERALS
  Возвращает сведения о литералах, включая типы данных и значения, поддерживаемые поставщиком XML для аналитики [!INCLUDE[msCoName](../../../includes/msconame-md.md)].  
  
 При вызове метода [Discover](../../xmla/xml-elements-methods-discover.md) метод с `DISCOVER_LITERALS` значение перечисления в [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md) элемент, `Discover` возвращает метод `DISCOVER_LITERALS` набора строк.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `DISCOVER_LITERALS` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`LiteralName`|`DBTYPE_WSTR`||Имя литерала, описанное в строке.<br /><br /> Например: `DBLITERAL_LIKE_PERCENT`.|  
|`LiteralValue`|`DBTYPE_WSTR`||Фактическое литеральное значение.<br /><br /> Например, если `LiteralName` имеет значение `DBLITERAL_LIKE_PERCENT`, а символ процента (`%`) соответствует нулю или более символам в предложении LIKE, столбец `LiteralValue` будет иметь значение «`%`».|  
|`LiteralInvalidChars`|`DBTYPE_WSTR`||Недопустимые символы в литерале.<br /><br /> Например, если имена таблиц могут содержать другие символы, помимо цифровых, то эта строка будет выглядеть так: «`0123456789`».|  
|`LiteralInvalidStartingChars`|`DBTYPE_WSTR`||Символы, которые являются недопустимыми, если они представляют собой первый символ литерала. Если первым символом литерала может быть любой допустимый символ, это значение `null`.|  
|`LiteralMaxLength`|`DBTYPE_I4`||Максимальное количество символов в литерале. Если неизвестны максимальное и минимальное значения, то значение -1.|  
|`LiteralNameEnumValue`|`DBTYPE_I4`|||  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `DISCOVER_LITERALS` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|`LiteralName`|`DBTYPE_WSTR`|Необязательный параметр.|  
  
## <a name="see-also"></a>См. также  
 [XML для анализа наборов строк схемы](xml-for-analysis-schema-rowsets.md)   
 [Набор строк DISCOVER_KEYWORDS &#40;XML для Аналитики&#41;](discover-keywords-rowset-xmla.md)  
  
  
