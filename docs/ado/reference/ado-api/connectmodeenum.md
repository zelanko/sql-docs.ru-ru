---
title: "ConnectModeEnum | Документы Microsoft"
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
- ConnectModeEnum
helpviewer_keywords:
- ConnectModeEnum enumeration [ADO]
ms.assetid: 3792c294-5161-4538-a908-22a5fc50b85f
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bc9a29f1f46ab56a87b318761b4b0809fd76e6fd
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="connectmodeenum"></a>ConnectModeEnum
Задает разрешения, доступные для изменения данных в [подключения](../../../ado/reference/ado-api/connection-object-ado.md), откройте [запись](../../../ado/reference/ado-api/record-object-ado.md), или указания значения для [режим](../../../ado/reference/ado-api/mode-property-ado.md) свойство  **Запись** и [поток](../../../ado/reference/ado-api/stream-object-ado.md) объектов.  
  
|Константа|Значение|Description|  
|--------------|-----------|-----------------|  
|**adModeRead**|1|Указывает разрешения только для чтения.|  
|**adModeReadWrite**|3|Указывает, разрешения на чтение и запись.|  
|**adModeRecursive**|0x400000|Используется в сочетании с другими  *\*ShareDeny\**  значения (**adModeShareDenyNone**, **adModeShareDenyWrite**, или **adModeShareDenyRead**) распространение ограничения управления доступом для всех вложенных записей текущего **записи**. Он не оказывает воздействия, если **записи** не имеет потомков. Ошибка во время выполнения создается в том случае, если она используется с **adModeShareDenyNone** только. Тем не менее, он может использоваться с **adModeShareDenyNone** в сочетании с другими значениями. Например, можно использовать «**adModeRead** или **adModeShareDenyNone** или **adModeRecursive**».|  
|**adModeShareDenyNone**|16|Дает возможность другим пользователям установить соединение с другими разрешениями. Другим пользователям не может быть запрещен доступ ни для чтения, ни для записи.|  
|**adModeShareDenyRead**|4|Запрет другим пользователям открывать соединение с разрешениями на чтение.|  
|**adModeShareDenyWrite**|8|Запрет другим пользователям открывать соединение с разрешениями на запись.|  
|**adModeShareExclusive**|12|Запрет другим пользователям открывать соединение.|  
|**adModeUnknown**|0|По умолчанию. Указывает, что разрешения не были установлены или не может быть определено.|  
|**adModeWrite**|2|Указывает разрешения только для записи.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.ConnectMode.READ|  
|AdoEnums.ConnectMode.READWRITE|  
|(Не существует эквивалента AdoEnums.ConnectMode.RECURSIVE)|  
|AdoEnums.ConnectMode.SHAREDENYNONE|  
|AdoEnums.ConnectMode.SHAREDENYREAD|  
|AdoEnums.ConnectMode.SHAREDENYWRITE|  
|AdoEnums.ConnectMode.SHAREEXCLUSIVE|  
|AdoEnums.ConnectMode.UNKNOWN|  
|AdoEnums.ConnectMode.WRITE|  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Свойство режима (ADO)](../../../ado/reference/ado-api/mode-property-ado.md)|[Метод Open (ADO запись)](../../../ado/reference/ado-api/open-method-ado-record.md)|  
|[Метод Open (поток ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)|[Объект потока (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)|

