---
title: Прямое подключение к драйверам | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], SqlDriverConnect
- SQLDriverConnect function [ODBC], connecting directly to drivers
- connecting to driver [ODBC], drivers
ms.assetid: f86e198f-a088-4401-9106-aa62a0eb8f6e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3f5818d67659769ae104b3e98248c26f5b9fe8a7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63151245"
---
# <a name="connecting-directly-to-drivers"></a>Прямое подключение к драйверам
Как было описано в [Выбор источника данных или драйвера](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)ранее в этом разделе, некоторые приложения не требуется вообще использовать источник данных. Вместо этого они хотят подключиться непосредственно к драйверу. **SQLDriverConnect** позволяет приложению подключаться непосредственно к драйвер без указания источника данных. По существу источник временных данных создается во время выполнения.  
  
 Для подключения непосредственно к драйвером, приложение указывает **ДРАЙВЕР** ключевое слово в строке подключения вместо **DSN** ключевое слово. Значение **ДРАЙВЕР** ключевое слово представляет собой описание драйвера, возвращенная **SQLDrivers**. Например предположим, описание драйвер для Paradox драйвер и необходимо указать имя каталога, содержащего файлы данных. Чтобы подключиться к этот драйвер, в приложении можно использовать любой из следующих строк подключения:  
  
```  
DRIVER={Paradox Driver};Directory=C:\PARADOX;  
DRIVER={Paradox Driver};  
```  
  
 С первой строки драйвер не потребуется никаких дополнительных сведений. Со строки второго драйвер должен запрашивать имя каталога, содержащего файлы данных.
