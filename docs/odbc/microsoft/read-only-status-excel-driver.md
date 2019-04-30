---
title: Состояние только для чтения (драйвер для Excel) | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 17425e76814a8397b9d2e6167248f35e52ac6cfa
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63316739"
---
# <a name="read-only-status-excel-driver"></a>Состояние только для чтения (драйвер для Excel)
При использовании драйвера Microsoft Excel таблицы источника данных открыта только для чтения, по умолчанию и можно открыть только один пользователь одновременно. Несмотря на то, что таблицы имеют состояние только для чтения, тем не менее, приложения могут выполнять операции вставки и обновления для таблиц Microsoft Excel.  
  
 Когда приложение выполняет команду Сохранить как данным Microsoft Excel, используя драйвер Microsoft Excel, приложение должно создать новую таблицу и вставки данных, которые необходимо сохранить в новой таблице. Операции вставки привести Добавление в таблицу. До его закрытия и повторном открытии, в таблице могут выполняться никакие другие операции. После закрытия таблицы не последующие операции вставки можно выполнить, поскольку таблица является затем только для чтения.  
  
 Можно обновить значения, при использовании драйвера Microsoft Excel, но нельзя удалить строку из таблицы, основанной на электронную таблицу Microsoft Excel, поэтому обновления не считаются официально поддерживается драйвером Microsoft Excel.
