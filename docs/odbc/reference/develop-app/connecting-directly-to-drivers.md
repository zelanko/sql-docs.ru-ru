---
title: Прямое подключение к драйверы | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], SqlDriverConnect
- SQLDriverConnect function [ODBC], connecting directly to drivers
- connecting to driver [ODBC], drivers
ms.assetid: f86e198f-a088-4401-9106-aa62a0eb8f6e
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f85b319ec264f9784953f12f93100660db614cbb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="connecting-directly-to-drivers"></a>Прямое подключение к драйверы
Как было описано в [Выбор источника данных или драйвер](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)ранее в этом разделе, некоторые приложения не требуется вообще использовать источник данных. Вместо этого их нужно подключиться непосредственно к драйверу. **SQLDriverConnect** позволяет приложению подключаться непосредственно к драйвер без указания источника данных. По существу источник временных данных создается во время выполнения.  
  
 Для подключения непосредственно к драйверу приложение указывает **ДРАЙВЕР** ключевое слово в строке подключения вместо **DSN** ключевое слово. Значение **ДРАЙВЕР** ключевое слово является Описание драйвера, возвращенный **SQLDrivers**. Предположим, например, с описанием драйвера Paradox драйвер и необходимо указать имя каталога, содержащего файлы данных. Для подключения к драйверу в приложении можно использовать любой из следующих строк подключения:  
  
```  
DRIVER={Paradox Driver};Directory=C:\PARADOX;  
DRIVER={Paradox Driver};  
```  
  
 С первой строки драйвер не потребуется любых дополнительных сведений. Второй строкой драйвер потребуется запросить имя каталога, содержащего файлы данных.
