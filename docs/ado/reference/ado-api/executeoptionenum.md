---
title: "ExecuteOptionEnum | Документы Microsoft"
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
- ExecuteOptionEnum
helpviewer_keywords:
- ExecuteOptionEnum enumeration [ADO]
ms.assetid: 68bfa83a-5df4-4bef-8736-0f88ae8c29ea
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 74248756628e892ff8a00e0e6e206b5eb7639e05
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="executeoptionenum"></a>ExecuteOptionEnum
Указывает, каким образом поставщик должен выполнить команду.  
  
|Константа|Значение|Description|  
|--------------|-----------|-----------------|  
|**adAsyncExecute**|0x10|Указывает, что будет выполняться асинхронно.<br /><br /> Это значение нельзя использовать вместе с [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) значение **adCmdTableDirect**.|  
|**adAsyncFetch**|0x20|Указывает, что оставшихся строк после указанного начального количества в [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md) свойства должны быть получены асинхронно.|  
|**adAsyncFetchNonBlocking**|0x40|Указывает, что основной поток никогда не блокируется при получении. Если Запрошенная строка не были получены, текущая строка автоматически перемещается в конец файла.<br /><br /> При открытии [записей](../../../ado/reference/ado-api/recordset-object-ado.md) из [поток](../../../ado/reference/ado-api/stream-object-ado.md) содержащий постоянно хранимых **записей**, **adAsyncFetchNonBlocking** не будет эффекта. Данная операция будет выполнена синхронный и блокировки.<br /><br /> **adAsynchFetchNonBlocking** не имеет силу при [adCmdTableDirect](../../../ado/reference/ado-api/commandtypeenum.md) параметр используется для открытия **записей**.|  
|**adExecuteNoRecords**|0x80|Указывает, что текст команды команду или хранимую процедуру, которая не возвращает строки (например, команду, которая вставляет только данных). Если извлекаются все строки, они удаляются и не возвращается.<br /><br /> **adExecuteNoRecords** могут передаваться только как необязательный параметр для **команда** или **выполнить соединение** метод.|  
|**adExecuteStream**|0x400|Указывает, что результаты выполнения команды должно возвращаться в виде потока.<br /><br /> **adExecuteStream** могут передаваться только как необязательный параметр для **выполняться данная команда** метод.|  
|**adExecuteRecord**||Указывает, что **CommandText** команду или хранимую процедуру, которая возвращает одну строку, в которой будут возвращены в качестве **записи** объекта.|  
|**adOptionUnspecified**|-1|Указывает, что команда не указан.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
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
|[Выполнить метод (команда ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)|[Выполнить метод (соединение ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md)|  
|[Метод Open (набора записей ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|[Requery-метод](../../../ado/reference/ado-api/requery-method.md)|
