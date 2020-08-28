---
description: Изменение существующих записей
title: Изменение существующих записей | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- editing data [ADO], existing records
ms.assetid: 17ce1263-5897-452a-9ea5-c7f96b33df65
author: rothja
ms.author: jroth
ms.openlocfilehash: 35c2376031e96a19c4a761a9826e47be2306518e
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88991335"
---
# <a name="editing-existing-records"></a>Изменение существующих записей
Чтобы изменить существующие записи, перейдите к строке, которую необходимо изменить, и измените свойство **значения** полей, которые необходимо изменить. Дополнительные сведения о свойстве **value** объекта **field** см. в разделе [анализ данных](./examining-data.md). В зависимости от типа курсора для отправки изменений обратно в источник данных будет использоваться **Update** или **UpdateBatch** . Дополнительные сведения см. в разделе [обновление и сохранение данных](./updating-and-persisting-data.md).  
  
 Обычно более эффективно использовать хранимую процедуру с объектом Command для выполнения обновлений, а также выполнять другие операции, так как хранимая процедура не требует создания курсора. Дополнительные сведения о курсорах см. в разделе Основные сведения о курсорах [и блокировках](./understanding-cursors-and-locks.md).