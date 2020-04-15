---
title: Статус только для чтения (Excel Driver) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- read-only status for Excel driver [ODBC]
- Excel driver [ODBC], read-only status
ms.assetid: ef5d773b-4f8f-4005-b985-84b53d8e9f9b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: eb585d4712b6cac5e09b65ee8e13604763cd0164
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304025"
---
# <a name="read-only-status-excel-driver"></a>Состояние только для чтения (драйвер для Excel)
При использовании драйвера Microsoft Excel таблицы исходных данных по умолчанию открываются как только для чтения, и могут быть открыты только одним пользователем одновременно. Несмотря на то, что таблицы имеют статус только для чтения, приложения могут выполнять вставки и обновления для таблиц Microsoft Excel.  
  
 Когда приложение выполняет команду Save As на данных Microsoft Excel через драйвер Microsoft Excel, приложение должно создать новую таблицу и вставить данные, которые будут сохранены в новую таблицу. Вставки приводят к придатку к столу. Никакие другие операции не могут быть выполнены на столе до тех пор, пока он не будет закрыт и вновь открыт. После закрытия таблицы последующая вставка не может быть выполнена, поскольку таблица является таблицей только для чтения.  
  
 При использовании драйвера Microsoft Excel можно обновлять значения, но строка не может быть удалена из таблицы, основанной на таблице Microsoft Excel, поэтому обновления не считаются официально поддерживаемыми драйвером Microsoft Excel.
