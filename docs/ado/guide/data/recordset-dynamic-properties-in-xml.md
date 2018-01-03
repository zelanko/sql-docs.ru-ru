---
title: "Динамический набор записей свойств в XML | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Recordset dynamic properties in XML [ADO]
ms.assetid: 52f8e379-812a-4db8-9210-94458926301c
caps.latest.revision: "3"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7b05609621af12607d11448028fc48a940f531ee
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-dynamic-properties-in-xml"></a>Динамический набор записей свойств в XML
Следующие свойства от поставщика набор записей (из обработчик курсора клиента), в настоящее время сохраняются в формате XML:  
  
-   Повторная синхронизация обновлений  
  
-   Уникальной таблицы  
  
-   Уникальной схемы  
  
-   Уникальный каталог  
  
-   Команда синхронизации  
  
-   IRowsetChange  
  
-   IRowsetUpdate  
  
-   CommandTimeout  
  
-   BatchSize  
  
-   UpdateCriteria  
  
-   Изменить имя  
  
-   AutoRecalc  
  
 Эти свойства сохраняются в разделе Схема как атрибуты определения элемента сохранение набора записей. Эти атрибуты определены в пространстве имен схемы набора строк и должен иметь префикс «rs:».  
  
## <a name="see-also"></a>См. также:  
 [Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
