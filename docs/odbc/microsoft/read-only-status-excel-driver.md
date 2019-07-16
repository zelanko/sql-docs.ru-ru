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
ms.openlocfilehash: 39f9d2e7ba40ba067659a86f45d2006c83594f3e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67988047"
---
# <a name="read-only-status-excel-driver"></a>Состояние только для чтения (драйвер для Excel)
При использовании драйвера Microsoft Excel таблицы источника данных открыта только для чтения, по умолчанию и можно открыть только один пользователь одновременно. Несмотря на то, что таблицы имеют состояние только для чтения, тем не менее, приложения могут выполнять операции вставки и обновления для таблиц Microsoft Excel.  
  
 Когда приложение выполняет команду Сохранить как данным Microsoft Excel, используя драйвер Microsoft Excel, приложение должно создать новую таблицу и вставки данных, которые необходимо сохранить в новой таблице. Операции вставки привести Добавление в таблицу. До его закрытия и повторном открытии, в таблице могут выполняться никакие другие операции. После закрытия таблицы не последующие операции вставки можно выполнить, поскольку таблица является затем только для чтения.  
  
 Можно обновить значения, при использовании драйвера Microsoft Excel, но нельзя удалить строку из таблицы, основанной на электронную таблицу Microsoft Excel, поэтому обновления не считаются официально поддерживается драйвером Microsoft Excel.
