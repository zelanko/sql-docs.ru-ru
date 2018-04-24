---
title: Пакетного режима | Документы Microsoft
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
- data updates [ADO], batch mode
- batch mode [ADO]
- updating data [ADO], batch mode
ms.assetid: 0cb548e0-fcb4-4c49-98c8-be287911f826
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f9fadf4744517b2de4e756e6e6167d8615419a25
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="batch-mode"></a>Пакетный режим
Пакетный режим действует при **LockType** свойству **adLockBatchOptimistic** и пакета обновления поддерживается поставщиком. Некоторые параметры типа блокировки недоступны в зависимости от положения курсора. Например, тип Пессимистическая блокировка вариант недоступен, если **CursorLocation** равно **adUseClient**. И наоборот поставщик не поддерживает оптимистической блокировки пакета, когда курсор находится на сервере. Следует использовать пакетного обновления с набором ключей или статическом курсоре только.  
  
 **UpdateBatch** метод используется для отправки **записей** изменения содержатся в буфер копирования на сервер для обновления источника данных. В следующем разделе будет открыта **записей** в пакетном режиме, внести изменения в буфер копирования и отправьте изменения в источник данных, с помощью вызова **UpdateBatch**.  
  
 В этом разделе рассматриваются следующие вопросы.  
  
-   [Отправка обновлений: метод UpdateBatch](../../../ado/guide/data/sending-the-updates-updatebatch-method.md)  
  
-   [Фильтрация обновленных записей](../../../ado/guide/data/filtering-for-updated-records.md)  
  
-   [Работа с ошибками обновлений](../../../ado/guide/data/dealing-with-failed-updates.md)  
  
-   [Обнаружение и разрешение конфликтов](../../../ado/guide/data/detecting-and-resolving-conflicts.md)  
  
-   [Отключение и повторное подключение набора записей](../../../ado/guide/data/disconnecting-and-reconnecting-the-recordset.md)  
  
-   [Обновление результатов объединения JOIN: уникальная таблица](../../../ado/guide/data/updating-joined-results-unique-table.md)
