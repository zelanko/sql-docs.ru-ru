---
title: Коннектмодинум | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 6e78ab5988d88447539da7c492f0b02943693844
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82762615"
---
# <a name="connectmodeenum"></a>ConnectModeEnum
Указывает доступные разрешения для изменения данных в [соединении](../../../ado/reference/ado-api/connection-object-ado.md), открытия [записи](../../../ado/reference/ado-api/record-object-ado.md)или указания значений для свойства [mode](../../../ado/reference/ado-api/mode-property-ado.md) объектов **Record** и [Stream](../../../ado/reference/ado-api/stream-object-ado.md) .  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adModeRead**|1|Указывает разрешения только для чтения.|  
|**adModeReadWrite**|3|Указывает разрешения на чтение и запись.|  
|**adModeRecursive**|0x400000|Используется в сочетании с другими значениями * \* Шаредени \* * (**адмодешаредениноне**, **адмодешаредениврите**или **адмодешаредениреад**) для распространения ограничений общего доступа ко всем подзаписям текущей **записи**. Он не влияет на наличие дочерних элементов в **записи** . Ошибка времени выполнения создается, если она используется только с **адмодешаредениноне** . Однако его можно использовать с **адмодешаредениноне** при сочетании с другими значениями. Например, можно использовать "**адмодереад** или **адмодешаредениноне** или **адмодерекурсиве**".|  
|**адмодешаредениноне**|16|Позволяет другим пользователям открывать подключение с любыми разрешениями. Другим пользователям не может быть запрещен доступ ни для чтения, ни для записи.|  
|**adModeShareDenyRead**|4|Предотвращает открытие пользователями подключения с разрешениями на чтение.|  
|**adModeShareDenyWrite**|8|Предотвращает открытие пользователями подключения с разрешениями на запись.|  
|**adModeShareExclusive**|12|Запрет на открытие подключения другими пользователями.|  
|**adModeUnknown**|0|По умолчанию. Указывает, что разрешения еще не заданы или не могут быть определены.|  
|**adModeWrite**|2|Указывает разрешения только на запись.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Константа|  
|--------------|  
|Адоенумс. Коннектмоде. READ|  
|Адоенумс. Коннектмоде. READWRITE|  
|(Не существует эквивалента Адоенумс. Коннектмоде. recursive)|  
|Адоенумс. Коннектмоде. ШАРЕДЕНИНОНЕ|  
|Адоенумс. Коннектмоде. ШАРЕДЕНИРЕАД|  
|Адоенумс. Коннектмоде. ШАРЕДЕНИВРИТЕ|  
|Адоенумс. Коннектмоде. ШАРИКСКЛУСИВЕ|  
|AdoEnums.ConnectMode.UNKNOWN|  
|Адоенумс. Коннектмоде. WRITE|  
  
## <a name="applies-to"></a>Применяется к  
  
|||  
|-|-|  
|[Свойство Mode (ADO)](../../../ado/reference/ado-api/mode-property-ado.md)|[Метод Open (объект Record ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)|  
|[Метод Open (объект Stream ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)|[Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)|
