---
title: Ексекутеоптионенум | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: e7465ee994a0e09cf62b80d3317948479354780b
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87242714"
---
# <a name="executeoptionenum"></a>ExecuteOptionEnum
Указывает, как поставщик должен выполнять команду.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adAsyncExecute**|0x10|Указывает, что команда должна выполняться асинхронно.<br /><br /> Это значение не может быть объединено со значением [Коммандтипинум](../../../ado/reference/ado-api/commandtypeenum.md) **адкмдтабледирект**.|  
|**адасинкфетч**|0x20|Указывает, что оставшиеся строки после начального количества, указанные в свойстве [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md) , должны быть получены асинхронно.|  
|**адасинкфетчнонблоккинг**|0x40|Указывает, что главный поток никогда не блокируется при извлечении. Если запрошенная строка не была получена, то текущая строка автоматически переместится в конец файла.<br /><br /> При открытии [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) из [потока](../../../ado/reference/ado-api/stream-object-ado.md) , содержащего сохраняемый **набор записей**, **адасинкфетчнонблоккинг** не будет иметь никакого влияния; операция будет синхронной и заблокированной.<br /><br /> **адасинчфетчнонблоккинг** не действует, если для открытия **набора записей**используется параметр [адкмдтабледирект](../../../ado/reference/ado-api/commandtypeenum.md) .|  
|**адексекутенорекордс**|0x80|Указывает, что текст команды является командой или хранимой процедурой, которая не возвращает строки (например, команда, которая вставляет только данные). Если какие бы то ни было строки получены, они отбрасываются и не возвращаются.<br /><br /> **адексекутенорекордс** можно передать только как необязательный параметр для метода Execute **команды** или **соединения** .|  
|**адексекутестреам**|0x400|Указывает, что результаты выполнения команды должны возвращаться в виде потока.<br /><br /> **адексекутестреам** может быть передан в метод **EXECUTE** только как необязательный параметр.|  
|**adExecuteRecord**||Указывает, что **CommandText** является командой или хранимой процедурой, возвращающей одну строку, которая должна возвращаться в качестве объекта **записи** .|  
|**адоптионунспеЦифиед**|-1|Указывает, что команда не указана.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Константа|  
|--------------|  
|AdoEnums.ExeКутеоптион. АСИНЦЕКСЕКУТЕ|  
|AdoEnums.ExeКутеоптион. АСИНКФЕТЧ|  
|AdoEnums.ExeКутеоптион. АСИНКФЕТЧНОНБЛОККИНГ|  
|AdoEnums.ExeКутеоптион. незаписи|  
|AdoEnums.ExeКутеоптион. Unspecified указано|  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Метод Execute (объект Command ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)  
        [Метод Execute (объект Connection ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md)  
    :::column-end:::
    :::column:::
        [Метод Open (объект Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)  
        [Метод Requery](../../../ado/reference/ado-api/requery-method.md)  
    :::column-end:::
:::row-end:::
