---
title: ADCPROP_UPDATERESYNC_ENUM | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADCPROP_UPDATERESYNC_ENUM
helpviewer_keywords:
- ADCPROP_UPDATERESYNC_ENUM [ADO]
ms.assetid: bc9e1a37-e969-47e9-8382-0bbfffa2034f
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 44358b333ce099281197512ec23f58b3a11f575a
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35275263"
---
# <a name="adcpropupdateresyncenum"></a>ADCPROP_UPDATERESYNC_ENUM
Указывает ли [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) метод следуют неявный [Resync](../../../ado/reference/ado-api/resync-method.md) метода операции и если да, область данной операции.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adResyncAll**|15|Вызывает **Resync** с комбинацией других членов ADCPROP_UPDATERESYNC_ENUM.|  
|**adResyncAutoIncrement**|1|По умолчанию. Пытается извлечь нового значения идентификатора для столбцов, которые автоматически увеличивается на единицу или созданные в источнике данных, например Microsoft Jet счетчик полей или столбцов Microsoft SQL Server Identity.|  
|**adResyncConflicts**|2|Вызывает **Resync** для всех строк, в которых произошел сбой операции обновления или удаления из-за конфликтов параллелизма.|  
|**adResyncInserts**|8|Вызывает **Resync** для всех успешно вставленных строк. Тем не менее значения столбцов AutoIncrement не синхронизируются. Вместо этого содержимое вставленных строк выполняется повторная синхронизация на основе существующего значения первичного ключа. Если первичный ключ — это значение AutoIncrement **Resync** не получить содержимое нужные строки. Для автоматического увеличения Автоувеличение значений первичного ключа, вызовите **UpdateBatch** с комбинацией **adResyncAutoIncrement** + **adResyncInserts**.|  
|**adResyncNone**|0|Не вызывает **Resync**.|  
|**adResyncUpdates**|4|Вызывает **Resync** для всех строк, успешно обновлен.|  
  
## <a name="applies-to"></a>Объект применения  
 [Свойство Update Resync (динамическое) (ADO)](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md)
