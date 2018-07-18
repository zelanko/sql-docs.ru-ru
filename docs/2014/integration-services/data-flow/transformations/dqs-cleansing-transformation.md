---
title: Преобразование "Очистка DQS" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data correction
- correct data
ms.assetid: d2ec1b1a-c745-4741-b57c-6fdb524a154c
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 696dce12d347fe8da679c5d029b9f9d78bafc19c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37283720"
---
# <a name="dqs-cleansing-transformation"></a>Преобразование «Очистка DQS»
  Преобразование «Очистка DQS» используется службы Data Quality Services (DQS) для исправления данных из подключенного источника данных путем применения утвержденных правил, созданных для подключенного или аналогичного источника данных. Дополнительные сведения о правилах исправления данных см. в разделе [DQS Knowledge Bases and Domains](../../../data-quality-services/dqs-knowledge-bases-and-domains.md). Дополнительные сведения о службах DQS см. в разделе [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md).  
  
 Чтобы определить, требуется ли исправление данных, преобразование «Очистка DQS» обрабатывает данные из входного столбца, когда выполняются следующие условия.  
  
-   Столбец выбран для корректировки данных.  
  
-   Данные столбца относятся к типу, пригодному для корректировки данных.  
  
-   Столбец сопоставлен с доменом, имеющим совместимый тип данных.  
  
 Преобразование также включает вывод ошибок, настроенный пользователем для обработки ошибок на уровне строк. Чтобы настроить вывод ошибок, запустите **Редактор преобразования «Очистка DQS»**.  
  
 В поток данных можно включить [Fuzzy Grouping Transformation](fuzzy-grouping-transformation.md) для определения строк данных, которые, вероятнее всего, будут повторяться.  
  
## <a name="data-quality-projects-and-values"></a>Проекты и значения служб DQS  
 При обработке данных с помощью преобразования «Очистка DQS» на сервере DQS создается проект очистки. Для управления проектом используется клиент DQS. Кроме того, можно использовать клиент DQS для импорта значений проекта в домен базы знаний служб DQS. Можно импортировать значения только в домен (или связанный домен), использование которого было настроено в преобразовании «Очистка DQS».  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Открытие проектов служб Integration Services в клиенте DQS](../../../data-quality-services/open-integration-services-projects-in-data-quality-client.md)  
  
-   [Импорт значений проекта очистки в домен](../../../data-quality-services/import-cleansing-project-values-into-a-domain.md)  
  
-   [Применение правил качества данных к источнику данных](apply-data-quality-rules-to-data-source.md)  
  
## <a name="related-content"></a>См. также  
  
-   [Управление &#40;открытие, разблокировка, переименование и удаление&#41; проекта качества данных](../../../data-quality-services/manage-open-unlock-rename-and-delete-a-data-quality-project.md)  
  
-   Статья [Очистка сложных данных с использованием составных доменов](http://social.technet.microsoft.com/wiki/contents/articles/13324.using-dqs-cleansing-complex-data-using-composite-domains.aspx)на сайте social.technet.microsoft.com.  
  
  
