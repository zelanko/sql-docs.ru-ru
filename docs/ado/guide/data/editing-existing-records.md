---
title: Изменение существующих записей | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- editing data [ADO], existing records
ms.assetid: 17ce1263-5897-452a-9ea5-c7f96b33df65
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6bd1e02bf406906cc8a893ccee66a408b38510f3
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66702066"
---
# <a name="editing-existing-records"></a>Изменение существующих записей
Для изменения существующих записей, перейдите к строке, необходимо отредактировать и изменить **значение** свойства полей, которые вы хотите изменить. Дополнительные сведения о **поле** объекта **значение** свойство, см. в разделе [проверки данных](../../../ado/guide/data/examining-data.md). В зависимости от типа курсора, будет использовать **обновление** или **UpdateBatch** для отправки изменений в источнике данных. Дополнительные сведения см. в разделе [обновление и сохранение данных](../../../ado/guide/data/updating-and-persisting-data.md).  
  
 Это обычно лучше использовать хранимую процедуру с помощью объекта команды для выполнения обновлений, а также для выполнения других операций, поскольку хранимая процедура не требует создания курсора. Дополнительные сведения о курсорах см. в разделе [основные сведения о курсорах и блокировок](../../../ado/guide/data/understanding-cursors-and-locks.md).
