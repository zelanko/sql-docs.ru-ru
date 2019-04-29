---
title: Динамические свойства набора записей в формате XML | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset dynamic properties in XML [ADO]
ms.assetid: 52f8e379-812a-4db8-9210-94458926301c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 50841931d26847ba339d64634d3eff4d7a7efc1b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62910894"
---
# <a name="recordset-dynamic-properties-in-xml"></a>Динамические свойства набора записей в XML
Следующие свойства от поставщика набор записей (из обработчик курсора клиента), в настоящее время сохраняются в формате XML:  
  
-   Повторная синхронизация обновления  
  
-   уникальная таблица  
  
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
  
 Эти свойства сохраняются в раздел схемы как атрибуты определения элемента, сохранение набора записей. Эти атрибуты определяются в пространстве имен схемы набора строк и должен иметь префикс «rs:».  
  
## <a name="see-also"></a>См. также  
 [Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
