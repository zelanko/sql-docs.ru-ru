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
manager: craigg
ms.openlocfilehash: 64262ae52b802398fc2060092a03e7469146f063
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47692892"
---
# <a name="editing-existing-records"></a>Изменение существующих записей
Для изменения существующих записей, перейдите к строке, необходимо отредактировать и изменить **значение** свойства полей, которые вы хотите изменить. Дополнительные сведения о **поле** объекта **значение** свойство, см. в разделе [проверки данных](../../../ado/guide/data/examining-data.md). В зависимости от типа курсора, будет использовать **обновление** или **UpdateBatch** для отправки изменений в источнике данных. Дополнительные сведения см. в разделе [обновление и сохранение данных](../../../ado/guide/data/updating-and-persisting-data.md).  
  
 Это обычно лучше использовать хранимую процедуру с помощью объекта команды для выполнения обновлений, а также для выполнения других операций, поскольку хранимая процедура не требует создания курсора. Дополнительные сведения о курсорах см. в разделе [основные сведения о курсорах и блокировок](../../../ado/guide/data/understanding-cursors-and-locks.md).
