---
title: Применение правил качества данных к источнику данных | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a965e8f2-004d-4ccc-8523-a185b35b26e2
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 232ea4b3c3d8c54d0d4fa3938ccab5cb91664b03
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37160855"
---
# <a name="apply-data-quality-rules-to-data-source"></a>Применение правил качества данных к источнику данных
  Можно использовать службы Data Quality Services (DQS) для корректировки данных в потоке данных пакета, подключив преобразование DQS Cleansing к источнику данных. Дополнительные сведения о языке DQS см. в разделе [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md). Дополнительные сведения об этом преобразовании см. в разделе [DQS Cleansing Transformation](dqs-cleansing-transformation.md).  
  
 При обработке данных с помощью преобразования DQS Cleansing, создается проект служб DQS на сервере служб DQS. Для управления проектом используется клиент DQS. Дополнительные сведения см. в статье [Управление проектом служб DQS (открытие, разблокировка, переименование и удаление)](../../../data-quality-services/manage-open-unlock-rename-and-delete-a-data-quality-project.md).  
  
### <a name="to-correct-data-in-the-data-flow"></a>Исправление данных в потоке данных  
  
1.  Создайте пакет.  
  
2.  Добавьте и настройте преобразование «Очистка DQS». Дополнительные сведения см. в разделе [DQS Cleansing Transformation Editor Dialog Box](../../dqs-cleansing-transformation-editor-dialog-box.md).  
  
3.  Соедините преобразование «Очистка DQS» с источником данных.  
  
  
