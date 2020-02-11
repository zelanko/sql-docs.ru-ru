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
ms.openlocfilehash: ce8679c0c7b20dfaa641918f0447a2f77bfd474a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925443"
---
# <a name="editing-existing-records"></a>Изменение существующих записей
Чтобы изменить существующие записи, перейдите к строке, которую необходимо изменить, и измените свойство **значения** полей, которые необходимо изменить. Дополнительные сведения о свойстве **value** объекта **field** см. в разделе [анализ данных](../../../ado/guide/data/examining-data.md). В зависимости от типа курсора для отправки изменений обратно в источник данных будет использоваться **Update** или **UpdateBatch** . Дополнительные сведения см. в разделе [обновление и сохранение данных](../../../ado/guide/data/updating-and-persisting-data.md).  
  
 Обычно более эффективно использовать хранимую процедуру с объектом Command для выполнения обновлений, а также выполнять другие операции, так как хранимая процедура не требует создания курсора. Дополнительные сведения о курсорах см. в разделе Основные сведения о курсорах [и блокировках](../../../ado/guide/data/understanding-cursors-and-locks.md).
