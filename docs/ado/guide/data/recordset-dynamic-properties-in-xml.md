---
title: Динамические свойства набора записей в XML | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: d9d19ded093cd10a7670b31cd2d5c78a475950d2
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760970"
---
# <a name="recordset-dynamic-properties-in-xml"></a>Динамические свойства набора записей в XML
Следующие специфические для поставщика наборов записей свойства (из обработчика курсора клиента) в настоящее время сохраняются в формате XML:  
  
-   Повторная синхронизация обновлений  
  
-   уникальная таблица  
  
-   Уникальная схема  
  
-   Уникальный каталог  
  
-   Команда повторной синхронизации  
  
-   IRowsetChange  
  
-   IRowsetUpdate  
  
-   CommandTimeout  
  
-   BatchSize  
  
-   упдатекритериа  
  
-   Изменить имя формы  
  
-   ауторекалк  
  
 Эти свойства сохраняются в разделе схемы как атрибуты определения элемента для сохраняемого набора записей. Эти атрибуты определены в пространстве имен схемы набора строк и должны иметь префикс "RS:".  
  
## <a name="see-also"></a>См. также  
 [Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
