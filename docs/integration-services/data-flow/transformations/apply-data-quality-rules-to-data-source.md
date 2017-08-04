---
title: "Применение правил качества данных к источнику данных | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a965e8f2-004d-4ccc-8523-a185b35b26e2
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e7db6b5fc01c5d85b75ebdd6c78ba004a94135bf
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="apply-data-quality-rules-to-data-source"></a>Применение правил качества данных к источнику данных
  Можно использовать службы Data Quality Services (DQS) для корректировки данных в потоке данных пакета, подключив преобразование DQS Cleansing к источнику данных. Дополнительные сведения о языке DQS см. в разделе [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md). Дополнительные сведения об этом преобразовании см. в разделе [DQS Cleansing Transformation](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation.md).  
  
 При обработке данных с помощью преобразования DQS Cleansing, создается проект служб DQS на сервере служб DQS. Для управления проектом используется клиент DQS. Дополнительные сведения см. в статье [Открытие, разблокировка, переименование и удаление проекта качества данных](https://msdn.microsoft.com/library/hh510417.aspx).  
  
### <a name="to-correct-data-in-the-data-flow"></a>Исправление данных в потоке данных  
  
1.  Создайте пакет.  
  
2.  Добавьте и настройте преобразование «Очистка DQS». Дополнительные сведения см. в разделе [DQS Cleansing Transformation Editor Dialog Box](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation-editor-dialog-box.md).  
  
3.  Соедините преобразование «Очистка DQS» с источником данных.  
  
  
