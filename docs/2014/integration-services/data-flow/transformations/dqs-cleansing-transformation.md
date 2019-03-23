---
title: Преобразование "Очистка DQS" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data correction
- correct data
ms.assetid: d2ec1b1a-c745-4741-b57c-6fdb524a154c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 0c06abe4d6adb3916028b3501c16b68d2491af47
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58386162"
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
  
## <a name="related-tasks"></a>Связанные задачи  
  
-   [Открытие проектов служб Integration Services в клиенте DQS](../../../data-quality-services/open-integration-services-projects-in-data-quality-client.md)  
  
-   [Импорт значений проекта очистки в домен](../../../data-quality-services/import-cleansing-project-values-into-a-domain.md)  
  
-   [Применение правил качества данных к источнику данных](apply-data-quality-rules-to-data-source.md)  
  
## <a name="related-content"></a>См. также  
  
-   [Управление &#40;открытие, разблокировка, переименование и удаление&#41; проекта качества данных](../../../data-quality-services/manage-open-unlock-rename-and-delete-a-data-quality-project.md)  
  
-   Статья [Очистка сложных данных с использованием составных доменов](https://social.technet.microsoft.com/wiki/contents/articles/13324.using-dqs-cleansing-complex-data-using-composite-domains.aspx)на сайте social.technet.microsoft.com.  
  
  
