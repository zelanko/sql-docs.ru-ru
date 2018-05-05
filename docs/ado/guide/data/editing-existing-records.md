---
title: Изменение существующих записей | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
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
ms.openlocfilehash: 64c3514b47a6fed7435967b48e9c2141eb9b61a3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="editing-existing-records"></a>Изменение существующих записей
Для изменения существующих записей, переход к строке, необходимо изменить и изменить **значение** свойства полей, которые требуется изменить. Дополнительные сведения о **поле** объекта **значение** свойство, в разделе [проверки данных](../../../ado/guide/data/examining-data.md). В зависимости от типа курсора, будет использоваться **обновление** или **UpdateBatch** для отправки изменений обратно в источник данных. Дополнительные сведения см. в разделе [обновление и сохранение данных](../../../ado/guide/data/updating-and-persisting-data.md).  
  
 Это обычно лучше использовать хранимую процедуру с помощью объекта команды для выполнения обновлений, а также для выполнения других операций, поскольку хранимая процедура не требует создания курсора. Дополнительные сведения о курсорах см. в разделе [основные сведения о курсорах и блокировок](../../../ado/guide/data/understanding-cursors-and-locks.md).
