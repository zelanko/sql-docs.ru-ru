---
description: CommandTypeEnum
title: Коммандтипинум | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CommandTypeEnum
helpviewer_keywords:
- CommandTypeEnum enumeration [ADO]
ms.assetid: 4b1feb9c-a855-40fe-a906-efe688687e9f
author: rothja
ms.author: jroth
ms.openlocfilehash: 861abb0066f4b9f32ff8f9071c1520a1dec73016
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88450826"
---
# <a name="commandtypeenum"></a>CommandTypeEnum
Указывает, как должен интерпретироваться аргумент команды.  
  
 Важно проверить предоставленные пользователем значения *CommandString* , чтобы не дать пользователям приложений возможность внедрять потенциально опасные команды для выполнения ADO.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**адкмдунспеЦифиед**|-1|Не указывает аргумент типа команды.|  
|**adCmdText**|1|Вычисляет [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) как текстовое определение команды или вызова хранимой процедуры.|  
|**адкмдтабле**|2|Вычисляет **CommandText** как имя таблицы, столбцы которой возвращаются внутренним запросом SQL.|  
|**adCmdStoredProc**|4|Вычисляет **CommandText** в качестве имени хранимой процедуры.|  
|**adCmdUnknown**|8|По умолчанию. Указывает, что тип команды в свойстве **CommandText** неизвестен.<br /><br /> Если тип команды неизвестен, то ADO делает несколько попыток интерпретировать **CommandText**.<br /><br /> -   **CommandText** интерпретируется как текстовое определение команды или вызова хранимой процедуры. Это то же поведение, что и **адкмдтекст**.<br />-   **CommandText** — имя хранимой процедуры. Это то же поведение, что и **адкмдсторедпрок**.<br />-   **CommandText** интерпретируется как имя таблицы. Все столбцы возвращаются внутренним сформированным запросом SQL. Это то же поведение, что и **адкмдтабле**.|  
|**adCmdFile**|256|Вычисляет **CommandText** в качестве имени файла сохраненного [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md). Используется с **набором записей.** Только для [открытия или повторного](../../../ado/reference/ado-api/open-method-ado-recordset.md) [запроса](../../../ado/reference/ado-api/requery-method.md) .|  
|**адкмдтабледирект**|512|Вычисляет **CommandText** как имя таблицы, все столбцы которой возвращаются. Используется с **набором Recordset. Open** или **Requery** only. Чтобы использовать метод [Seek](../../../ado/reference/ado-api/seek-method.md) , **набор записей** должен быть открыт с помощью **адкмдтабледирект**.<br /><br /> Это значение не может быть объединено со значением [Ексекутеоптионенум](../../../ado/reference/ado-api/executeoptionenum.md) **адасинцексекуте**.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Константа|  
|--------------|  
|Адоенумс. CommandType. не указано|  
|Адоенумс. CommandType. TEXT|  
|Адоенумс. CommandType. TABLE|  
|Адоенумс. CommandType. СТОРЕДПРОК|  
|Адоенумс. CommandType. UNKNOWN|  
|Адоенумс. CommandType. FILE|  
|Адоенумс. CommandType. TABLEDIRECT|  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Свойство CommandType (ADO)](../../../ado/reference/ado-api/commandtype-property-ado.md)  
        [Метод Execute (объект Command ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)  
    :::column-end:::
    :::column:::
        [Метод Execute (объект Connection ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md)  
        [Метод Open (объект Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)  
    :::column-end:::
    :::column:::
        [Метод Requery](../../../ado/reference/ado-api/requery-method.md)  
    :::column-end:::
:::row-end:::
