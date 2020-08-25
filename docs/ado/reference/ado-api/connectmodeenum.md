---
description: ConnectModeEnum
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
ms.openlocfilehash: 10bc68683f337f5a0bdf6fc5679c4276925a4234
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88775853"
---
# <a name="connectmodeenum"></a>ConnectModeEnum
Указывает доступные разрешения для изменения данных в [соединении](./connection-object-ado.md), открытия [записи](./record-object-ado.md)или указания значений для свойства [mode](./mode-property-ado.md) объектов **Record** и [Stream](./stream-object-ado.md) .  
  
|Константа|Значение|Описание:|  
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
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Свойство Mode (ADO)](./mode-property-ado.md)  
        [Метод Open (объект Record ADO)](./open-method-ado-record.md)  
    :::column-end:::
    :::column:::
        [Метод Open (объект Stream ADO)](./open-method-ado-stream.md)  
        [Объект Stream (ADO)](./stream-object-ado.md)  
    :::column-end:::
:::row-end:::