---
title: Состояние только для чтения (драйвер Excel) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- read-only status for Excel driver [ODBC]
- Excel driver [ODBC], read-only status
ms.assetid: ef5d773b-4f8f-4005-b985-84b53d8e9f9b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d885124c9e4274d402bfa504b975f089d333af95
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="read-only-status-excel-driver"></a>Состояние только для чтения (драйвер Excel)
При использовании драйвера Microsoft Excel таблицы источника данных открыта только для чтения по умолчанию и можно открыть только один пользователь одновременно. Несмотря на то, что таблицы имеют состояние только для чтения, тем не менее, приложения могут выполнять операции вставки и обновления для таблицы Microsoft Excel.  
  
 Когда приложение выполняет команды Сохранить как на данных Microsoft Excel с помощью драйвера Microsoft Excel, приложение должно создать новую таблицу и вставка данных, которые необходимо сохранить в новой таблице. Операции вставки приведут запроса на добавление в таблицу. Никакие другие операции можно выполнить в таблице пока не будет закрыт и открыт повторно. После закрытия таблицы не последующие операции вставки может выполняться, поскольку таблица затем таблица только для чтения.  
  
 Можно обновить значения, при использовании драйвера Microsoft Excel, но не может удалить строку из таблицы, основанной на таблице Microsoft Excel, поэтому обновления не считаются официально поддерживается драйвером Microsoft Excel.
