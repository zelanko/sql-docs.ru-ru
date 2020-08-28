---
description: Служба курсора Майкрософт для OLE DB
title: Служба курсора Майкрософт для OLE DB | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursor service for ole db [ADO]
- cursors [ADO], cursor service for OLE DB
ms.assetid: 1ac3bd9b-2d45-4cc8-88ec-bd8a218cfb49
author: rothja
ms.author: jroth
ms.openlocfilehash: ce59aa28e8db4716b0e27c848ce774b489ff5891
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88979375"
---
# <a name="the-microsoft-cursor-service-for-ole-db"></a>Служба курсора Майкрософт для OLE DB
При выборе курсора на стороне клиента или задании для свойства **CursorLocation** значения **адусеклиент**вы вызываете службу курсора Майкрософт для OLE DB. Вы также можете увидеть ссылки на обработчик курсоров клиента, который, по сути, аналогичен в контексте ADO. Эта служба дополняет функции поддержки курсоров поставщиками данных. В результате вы можете воспринимать относительно единую функциональность всех поставщиков данных.  
  
 Служба курсора для OLE DB делает динамические свойства доступными и расширяет поведение определенных методов. Например, динамическое свойство **optimize** позволяет создавать временные индексы для упрощения определенных операций, таких как метод **Find** .  
  
 Служба курсоров включает поддержку пакетного обновления во всех случаях. Он также имитирует более производительные типы курсоров, такие как динамические курсоры, когда поставщик данных может предоставлять только менее производительные курсоры, например статические курсоры.  
  
## <a name="see-also"></a>См. также  
 [Служба курсора Майкрософт для OLE DB (компонент службы ADO)](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)
