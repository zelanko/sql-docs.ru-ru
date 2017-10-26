---
title: "Прямое подключение к драйверы | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], SqlDriverConnect
- SQLDriverConnect function [ODBC], connecting directly to drivers
- connecting to driver [ODBC], drivers
ms.assetid: f86e198f-a088-4401-9106-aa62a0eb8f6e
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bacb659cb6986f86151502998523ade468f7cedd
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="connecting-directly-to-drivers"></a>Прямое подключение к драйверы
Как было описано в [Выбор источника данных или драйвер](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)ранее в этом разделе, некоторые приложения не требуется вообще использовать источник данных. Вместо этого их нужно подключиться непосредственно к драйверу. **SQLDriverConnect** позволяет приложению подключаться непосредственно к драйвер без указания источника данных. По существу источник временных данных создается во время выполнения.  
  
 Для подключения непосредственно к драйверу приложение указывает **ДРАЙВЕР** ключевое слово в строке подключения вместо **DSN** ключевое слово. Значение **ДРАЙВЕР** ключевое слово является Описание драйвера, возвращенный **SQLDrivers**. Предположим, например, с описанием драйвера Paradox драйвер и необходимо указать имя каталога, содержащего файлы данных. Для подключения к драйверу в приложении можно использовать любой из следующих строк подключения:  
  
```  
DRIVER={Paradox Driver};Directory=C:\PARADOX;  
DRIVER={Paradox Driver};  
```  
  
 С первой строки драйвер не потребуется любых дополнительных сведений. Второй строкой драйвер потребуется запросить имя каталога, содержащего файлы данных.

