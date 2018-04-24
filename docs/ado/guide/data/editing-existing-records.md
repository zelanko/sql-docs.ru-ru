---
title: Изменение существующих записей | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- editing data [ADO], existing records
ms.assetid: 17ce1263-5897-452a-9ea5-c7f96b33df65
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 43faf0a4bd21513bd03f89814cdb03fd55347bc4
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="editing-existing-records"></a>Изменение существующих записей
Для изменения существующих записей, переход к строке, необходимо изменить и изменить **значение** свойства полей, которые требуется изменить. Дополнительные сведения о **поле** объекта **значение** свойство, в разделе [проверки данных](../../../ado/guide/data/examining-data.md). В зависимости от типа курсора, будет использоваться **обновление** или **UpdateBatch** для отправки изменений обратно в источник данных. Дополнительные сведения см. в разделе [обновление и сохранение данных](../../../ado/guide/data/updating-and-persisting-data.md).  
  
 Это обычно лучше использовать хранимую процедуру с помощью объекта команды для выполнения обновлений, а также для выполнения других операций, поскольку хранимая процедура не требует создания курсора. Дополнительные сведения о курсорах см. в разделе [основные сведения о курсорах и блокировок](../../../ado/guide/data/understanding-cursors-and-locks.md).
