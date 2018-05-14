---
title: Свойства публикации, страница "Секции данных" | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.newpubwizard.pubproperties.datapartitions.f1
ms.assetid: 5869edb7-d05f-495b-b828-b7fd5e828d20
caps.latest.revision: 20
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7839c1bb3f4bf944ba230472abdca3a81fa58d38
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="publication-properties-data-partitions"></a>Свойства публикации, секции данных
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Страница **Секции данных** диалогового окна **Свойства публикации** позволяет определить секции данных для публикаций слиянием, использующих параметризованную фильтрацию. После определения секций для них можно создать моментальные снимки, предоставляя первоначальные наборы данных для различных подписчиков на основе свойств соединений (имени входа или имени компьютера) подписчиков. Также можно разрешить подписчикам запрашивать доставку и создание моментальных снимков, если для их секции недоступен моментальный снимок в момент их первой синхронизации. Дополнительные сведения см. в статье [Создание моментального снимка для публикации слиянием с параметризованными фильтрами](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
## <a name="options"></a>Параметры  
 **Добавить**  
 Нажмите кнопку **Добавить** для определения секции. В диалоговом окне **Добавление секции данных** задайте значения для **HOST_NAME()** или **SUSER_SNAME()** и определите расписание обновления моментальных снимков.  
  
 **Изменить**  
 Выберите в сетке существующую секцию и нажмите кнопку **Изменить** для редактирования секции.  
  
 **Удаление**  
 Выберите в сетке существующую секцию и нажмите кнопку **Удалить** для удаления секции.  
  
 **Создать выбранные моментальные снимки**  
 Выберите одну или несколько секций в сетке и выберите параметр **Создать выбранные моментальные снимки** для создания моментальных снимков для этих секций.  
  
 **Очистить существующие моментальные снимки**  
 Выберите одну или несколько секций в сетке и выберите параметр **Очистить существующие моментальные снимки** для очистки моментальных снимков для этих секций.  
  
 **Автоматически определять секцию и, при необходимости, создавать моментальный снимок при попытке синхронизации от нового подписчика**  
 Выберите этот параметр, если нужно разрешить подписчикам запрашивать создание и применение моментальных снимков. Подписчикам может понадобиться этот параметр, если в момент их первой синхронизации для их секции отсутствует моментальный снимок.  
  
## <a name="see-also"></a>См. также:  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Просмотр и изменение свойств публикации](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)   
 [Публикация данных и объектов базы данных](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)  
  
  
