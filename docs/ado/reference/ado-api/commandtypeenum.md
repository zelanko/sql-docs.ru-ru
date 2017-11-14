---
title: "CommandTypeEnum | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- CommandTypeEnum
helpviewer_keywords:
- CommandTypeEnum enumeration [ADO]
ms.assetid: 4b1feb9c-a855-40fe-a906-efe688687e9f
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bc2cd3acc56c11bdab98d58c1adc76d98eb1579d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="commandtypeenum"></a>CommandTypeEnum
Указывает, как следует интерпретировать аргумент команды.  
  
 Важно проверить предоставленные пользователем *CommandString* значения, чтобы избежать предоставления приложения пользователям возможность внедрить потенциально опасные команды для ADO для выполнения.  
  
|Константа|Значение|Description|  
|--------------|-----------|-----------------|  
|**adCmdUnspecified**|-1|Не указан аргумент типа команды.|  
|**adCmdText**|1|Результатом является [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) как текстовое определение команда или хранимая процедура вызова.|  
|**adCmdTable**|2|Результатом является **CommandText** как имя таблицы, столбцы возвращаются внутри созданного запросом SQL.|  
|**adCmdStoredProc**|4|Результатом является **CommandText** имени хранимой процедуры.|  
|**adCmdUnknown**|8|По умолчанию. Указывает, что тип команды в **CommandText** неизвестное свойство.<br /><br /> Если неизвестны тип команды ADO сделает несколько попыток, чтобы интерпретировать **CommandText**.<br /><br /> -   **CommandText** интерпретируется как текстовое определение вызова команды или хранимой процедуры. Это поведение аналогично **adCmdText**.<br />-   **CommandText** имя хранимой процедуры. Это поведение аналогично **adCmdStoredProc**.<br />-   **CommandText** интерпретируется как имя таблицы. Внутренне созданные SQL-запроса возвращаются все столбцы. Это поведение аналогично **adCmdTable**.|  
|**adCmdFile**|256|Результатом является **CommandText** как имя файла постоянно хранимых [записей](../../../ado/reference/ado-api/recordset-object-ado.md). При использовании **набор записей.** [Откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md) или [Requery](../../../ado/reference/ado-api/requery-method.md) только.|  
|**adCmdTableDirect**|512|Результатом является **CommandText** как имя таблицы, столбцы возвращаются все. При использовании **Recordset.Open** или **Requery** только. Для использования [Seek](../../../ado/reference/ado-api/seek-method.md) метода **записей** должен открываться с **adCmdTableDirect**.<br /><br /> Это значение нельзя использовать вместе с [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) значение **adAsyncExecute**.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
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
|[Свойство CommandType (ADO)](../../../ado/reference/ado-api/commandtype-property-ado.md)|[Выполнить метод (команда ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)|  
|[Выполнить метод (соединение ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md)|[Метод Open (набора записей ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|  
|[Requery-метод](../../../ado/reference/ado-api/requery-method.md)||

