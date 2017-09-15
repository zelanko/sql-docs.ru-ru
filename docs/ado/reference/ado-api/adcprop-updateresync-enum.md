---
title: "ADCPROP_UPDATERESYNC_ENUM | Документы Microsoft"
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
- ADCPROP_UPDATERESYNC_ENUM
helpviewer_keywords:
- ADCPROP_UPDATERESYNC_ENUM [ADO]
ms.assetid: bc9e1a37-e969-47e9-8382-0bbfffa2034f
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e5c25ab6802b6a99902c9e52990be80ff14ed6d5
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="adcpropupdateresyncenum"></a>ADCPROP_UPDATERESYNC_ENUM
Указывает ли [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) метод следуют неявный [Resync](../../../ado/reference/ado-api/resync-method.md) метода операции и если да, область данной операции.  
  
|Константа|Значение|Description|  
|--------------|-----------|-----------------|  
|**adResyncAll**|15|Вызывает **Resync** с комбинацией других членов ADCPROP_UPDATERESYNC_ENUM.|  
|**adResyncAutoIncrement**|1|По умолчанию. Пытается извлечь нового значения идентификатора для столбцов, которые автоматически увеличивается на единицу или созданные в источнике данных, например Microsoft Jet счетчик полей или столбцов Microsoft SQL Server Identity.|  
|**adResyncConflicts**|2|Вызывает **Resync** для всех строк, в которых произошел сбой операции обновления или удаления из-за конфликтов параллелизма.|  
|**adResyncInserts**|8|Вызывает **Resync** для всех успешно вставленных строк. Тем не менее значения столбцов AutoIncrement не синхронизируются. Вместо этого содержимое вставленных строк выполняется повторная синхронизация на основе существующего значения первичного ключа. Если первичный ключ — это значение AutoIncrement **Resync** не получить содержимое нужные строки. Для автоматического увеличения Автоувеличение значений первичного ключа, вызовите **UpdateBatch** с комбинацией **adResyncAutoIncrement** + **adResyncInserts**.|  
|**adResyncNone**|0|Не вызывает **Resync**.|  
|**adResyncUpdates**|4|Вызывает **Resync** для всех строк, успешно обновлен.|  
  
## <a name="applies-to"></a>Объект применения  
 [Свойство динамической повторной синхронизации обновления (ADO)](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md)
