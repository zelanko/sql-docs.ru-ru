---
title: Динамический набор записей свойств в XML | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset dynamic properties in XML [ADO]
ms.assetid: 52f8e379-812a-4db8-9210-94458926301c
caps.latest.revision: 3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 84619cdbe7070cc971d9347b2bfd3b7b5ba5c6a5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
-   CommandTimeOut  
  
-   BatchSize  
  
-   UpdateCriteria  
  
-   Изменить имя  
  
-   AutoRecalc  
  
 Эти свойства сохраняются в разделе Схема как атрибуты определения элемента сохранение набора записей. Эти атрибуты определены в пространстве имен схемы набора строк и должен иметь префикс «rs:».  
  
## <a name="see-also"></a>См. также  
 [Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
