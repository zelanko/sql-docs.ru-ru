---
title: CommandTypeEnum | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5ff7b6ecf919ab83340e49e4395f8c2d1701261d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47742882"
---
# <a name="commandtypeenum"></a>CommandTypeEnum
Указывает, каким образом следует интерпретировать аргумент команды.  
  
 Очень важно проверить предоставленные пользователем *CommandString* значения, чтобы избежать, предоставляя пользователям приложения возможность встраивать потенциально опасных команд для ADO для выполнения.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adCmdUnspecified**|-1|Не указывайте аргумент типа команды.|  
|**adCmdText**|1|Результатом является [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) как текстовое определение команда или хранимая процедура вызывать.|  
|**adCmdTable**|2|Результатом является **CommandText** как на имя таблицы, столбцы которых возвращаются, созданного внутреннего запроса SQL.|  
|**adCmdStoredProc**|4|Результатом является **CommandText** как имя хранимой процедуры.|  
|**adCmdUnknown**|8|По умолчанию. Указывает, что тип команды в **CommandText** свойство неизвестно.<br /><br /> Если тип команды неизвестен, ADO сделает несколько попыток, чтобы интерпретировать **CommandText**.<br /><br /> -   **CommandText** интерпретируется как текстовое определение для вызова команды или хранимых процедур. Это аналогично **adCmdText**.<br />-   **CommandText** имя хранимой процедуры. Это аналогично **adCmdStoredProc**.<br />-   **CommandText** интерпретируется как имя таблицы. Созданная внутри структура SQL-запрос возвращает все столбцы. Это аналогично **adCmdTable**.|  
|**adCmdFile**|256|Результатом является **CommandText** как имя файла постоянно хранимых [записей](../../../ado/reference/ado-api/recordset-object-ado.md). Используется с **набор записей.** [Откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md) или [Requery](../../../ado/reference/ado-api/requery-method.md) только.|  
|**adCmdTableDirect**|512|Результатом является **CommandText** как на имя таблицы, столбцы которого возвращаются все. Используется с **Recordset.Open** или **Requery** только. Чтобы использовать [Seek](../../../ado/reference/ado-api/seek-method.md) метод, **записей** должен открываться с **adCmdTableDirect**.<br /><br /> Это значение не может объединяться с [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) значение **adAsyncExecute**.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO и WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.CommandType.UNSPECIFIED|  
|AdoEnums.CommandType.TEXT|  
|AdoEnums.CommandType.TABLE|  
|AdoEnums.CommandType.STOREDPROC|  
|AdoEnums.CommandType.UNKNOWN|  
|AdoEnums.CommandType.FILE|  
|AdoEnums.CommandType.TABLEDIRECT|  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Свойство CommandType (ADO)](../../../ado/reference/ado-api/commandtype-property-ado.md)|[Метод Execute (объект Command ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)|  
|[Метод Execute (объект Connection ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md)|[Метод Open (объект Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|  
|[Метод Requery](../../../ado/reference/ado-api/requery-method.md)||
