---
title: Пакетном режиме | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data updates [ADO], batch mode
- batch mode [ADO]
- updating data [ADO], batch mode
ms.assetid: 0cb548e0-fcb4-4c49-98c8-be287911f826
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c25cd688b5d74e4514e1af645f7917059ce4d445
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62472838"
---
# <a name="batch-mode"></a>Пакетный режим
Пакетный режим действует при **LockType** свойству **adLockBatchOptimistic** и пакетное обновление поддерживается поставщиком. Некоторые параметры типа блокировки недоступны в зависимости от положения курсора. Например, тип пессимистической блокировки вариант недоступен, если **CursorLocation** присваивается **adUseClient**. И наоборот поставщик не поддерживает оптимистической блокировки пакетной службы, когда курсор находится на сервере. Следует использовать пакетного обновления с набором ключей или только для статического курсора.  
  
 **UpdateBatch** метод используется для отправки **записей** изменения, находящиеся в буфере копирования на сервер для обновления источника данных. В следующем разделе, будет открыта **записей** в пакетном режиме, внести изменения в буфер копирования и отправьте изменения в источник данных, используя вызов **UpdateBatch**.  
  
 В этом разделе рассматриваются следующие вопросы.  
  
-   [Отправка обновлений: Метод UpdateBatch](../../../ado/guide/data/sending-the-updates-updatebatch-method.md)  
  
-   [Фильтрация обновленных записей](../../../ado/guide/data/filtering-for-updated-records.md)  
  
-   [Работа с ошибками обновлений](../../../ado/guide/data/dealing-with-failed-updates.md)  
  
-   [Обнаружение и разрешение конфликтов](../../../ado/guide/data/detecting-and-resolving-conflicts.md)  
  
-   [Отключение и повторное подключение набора записей](../../../ado/guide/data/disconnecting-and-reconnecting-the-recordset.md)  
  
-   [Обновление результатов объединения JOIN: Уникальной таблицы](../../../ado/guide/data/updating-joined-results-unique-table.md)
