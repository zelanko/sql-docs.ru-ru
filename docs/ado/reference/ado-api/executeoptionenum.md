---
title: ExecuteOptionEnum | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ExecuteOptionEnum
helpviewer_keywords:
- ExecuteOptionEnum enumeration [ADO]
ms.assetid: 68bfa83a-5df4-4bef-8736-0f88ae8c29ea
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 589519e7c4a075d5fb06b5f2640d48e5d4ed898d
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66695271"
---
# <a name="executeoptionenum"></a>ExecuteOptionEnum
Указывает, как поставщик должен выполнить команду.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adAsyncExecute**|0x10|Указывает, что будет выполняться асинхронно.<br /><br /> Это значение не может объединяться с [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) значение **adCmdTableDirect**.|  
|**adAsyncFetch**|0x20|Указывает, что оставшиеся строки после начальной количество указанных в [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md) асинхронно нужно извлечь свойство.|  
|**adAsyncFetchNonBlocking**|0x40|Указывает, что основной поток не блокируется при извлечении. Если Запрошенная строка не были получены, текущая строка автоматически перемещается в конец файла.<br /><br /> При открытии [записей](../../../ado/reference/ado-api/recordset-object-ado.md) из [Stream](../../../ado/reference/ado-api/stream-object-ado.md) содержащий постоянно хранимых **записей**, **adAsyncFetchNonBlocking** не будет эффекта. Данная операция будет синхронной и блокировки.<br /><br /> **adAsynchFetchNonBlocking** не действует, если [adCmdTableDirect](../../../ado/reference/ado-api/commandtypeenum.md) параметр используется для открытия **записей**.|  
|**adExecuteNoRecords**|0x80|Указывает, что текст команды команду или хранимую процедуру, которая не возвращает строки (например, команды, только вставляет данные). Если извлекаются все строки, они удаляются и не возвращается.<br /><br /> **adExecuteNoRecords** могут передаваться только как необязательный параметр для **команда** или **выполнить соединение** метод.|  
|**adExecuteStream**|0x400|Указывает, что результаты выполнения команды должно возвращаться в виде потока.<br /><br /> **adExecuteStream** могут передаваться только как необязательный параметр для **Command Execute** метод.|  
|**adExecuteRecord**||Указывает, что **CommandText** команду или хранимую процедуру, которая возвращает одну строку, в которой будут возвращены в качестве **записи** объекта.|  
|**adOptionUnspecified**|-1|Указывает, что команда не определен.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO и WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.ExecuteOption.ASYNCEXECUTE|  
|AdoEnums.ExecuteOption.ASYNCFETCH|  
|AdoEnums.ExecuteOption.ASYNCFETCHNONBLOCKING|  
|AdoEnums.ExecuteOption.NORECORDS|  
|AdoEnums.ExecuteOption.UNSPECIFIED|  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Метод Execute (объект Command ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)|[Метод Execute (объект Connection ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md)|  
|[Метод Open (объект Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|[Метод Requery](../../../ado/reference/ado-api/requery-method.md)|
