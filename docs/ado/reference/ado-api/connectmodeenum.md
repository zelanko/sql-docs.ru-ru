---
title: ConnectModeEnum | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ConnectModeEnum
helpviewer_keywords:
- ConnectModeEnum enumeration [ADO]
ms.assetid: 3792c294-5161-4538-a908-22a5fc50b85f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2a5ab00cc6e01b97639ae3f7d353fa2462ef3fd0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47637862"
---
# <a name="connectmodeenum"></a>ConnectModeEnum
Указывает доступные разрешения для изменения данных в [подключения](../../../ado/reference/ado-api/connection-object-ado.md), откройте [записи](../../../ado/reference/ado-api/record-object-ado.md), или заданием значений для [режим](../../../ado/reference/ado-api/mode-property-ado.md) свойство  **Запись** и [Stream](../../../ado/reference/ado-api/stream-object-ado.md) объектов.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adModeRead**|1|Указывает разрешения только для чтения.|  
|**adModeReadWrite**|3|Обозначает разрешения на чтение и запись.|  
|**adModeRecursive**|0x400000|Используется в сочетании с другими *\*ShareDeny\** значения (**adModeShareDenyNone**, **adModeShareDenyWrite**, или **adModeShareDenyRead**) для распространения ограничений по общему доступу для всех вложенных записей текущего **записи**. Он не оказывает воздействия, если **записи** не имеет дочерних объектов. Ошибка во время выполнения создается в том случае, если используется в сочетании с **adModeShareDenyNone** только. Тем не менее, он может использоваться с **adModeShareDenyNone** в сочетании с другими значениями. Например, можно использовать "**adModeRead** или **adModeShareDenyNone** или **adModeRecursive**«.|  
|**adModeShareDenyNone**|16|Дает возможность другим пользователям открыть соединение с какие-либо разрешения. Другим пользователям не может быть запрещен доступ ни для чтения, ни для записи.|  
|**adModeShareDenyRead**|4|Другие пользователи не смогут открывать соединение с разрешениями на чтение.|  
|**adModeShareDenyWrite**|8|Другие пользователи не смогут открывать соединение с разрешениями на запись.|  
|**adModeShareExclusive**|12|Другие пользователи не смогут открывать соединение.|  
|**adModeUnknown**|0|По умолчанию. Указывает, что разрешения еще не были установлены или не может быть определено.|  
|**adModeWrite**|2|Обозначает разрешения только для записи.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO и WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.ConnectMode.READ|  
|AdoEnums.ConnectMode.READWRITE|  
|(Нет-нет эквивалента AdoEnums.ConnectMode.RECURSIVE)|  
|AdoEnums.ConnectMode.SHAREDENYNONE|  
|AdoEnums.ConnectMode.SHAREDENYREAD|  
|AdoEnums.ConnectMode.SHAREDENYWRITE|  
|AdoEnums.ConnectMode.SHAREEXCLUSIVE|  
|AdoEnums.ConnectMode.UNKNOWN|  
|AdoEnums.ConnectMode.WRITE|  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Свойство Mode (ADO)](../../../ado/reference/ado-api/mode-property-ado.md)|[Метод Open (объект Record ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)|  
|[Метод Open (объект Stream ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)|[Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)|
