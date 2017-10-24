---
title: "Изменение существующих записей | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editing data [ADO], existing records
ms.assetid: 17ce1263-5897-452a-9ea5-c7f96b33df65
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 03e720476c8056737e2735ac96c97a7caf190de4
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="editing-existing-records"></a>Изменение существующих записей
Для изменения существующих записей, переход к строке, необходимо изменить и изменить **значение** свойства полей, которые требуется изменить. Дополнительные сведения о **поле** объекта **значение** свойство, в разделе [проверки данных](../../../ado/guide/data/examining-data.md). В зависимости от типа курсора, будет использоваться **обновление** или **UpdateBatch** для отправки изменений обратно в источник данных. Дополнительные сведения см. в разделе [обновление и сохранение данных](../../../ado/guide/data/updating-and-persisting-data.md).  
  
 Это обычно лучше использовать хранимую процедуру с помощью объекта команды для выполнения обновлений, а также для выполнения других операций, поскольку хранимая процедура не требует создания курсора. Дополнительные сведения о курсорах см. в разделе [основные сведения о курсорах и блокировок](../../../ado/guide/data/understanding-cursors-and-locks.md).

