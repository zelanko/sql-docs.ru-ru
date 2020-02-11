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
ms.openlocfilehash: 44b9de304069849e965fc335e130ae57d9ec8bad
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68083166"
---
# <a name="connecting-directly-to-drivers"></a>Прямое подключение к драйверам
Как было сказано при [выборе источника данных или драйвера](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md), ранее в этом разделе некоторые приложения не хотят использовать источник данных. Вместо этого они хотят напрямую подключаться к драйверу. **SQLDriverConnect** предоставляет приложению возможность напрямую подключаться к драйверу, не указывая источник данных. По сути, во время выполнения создается временный источник данных.  
  
 Для прямого подключения к драйверу приложение указывает в строке подключения ключевое слово **Driver** , а не ключевое слово **DSN** . Значением ключевого слова **Driver** является описание драйвера, возвращаемое функцией **SQLDrivers**. Например, предположим, что драйвер содержит описание драйвера Paradox и требует указания имени каталога, содержащего файлы данных. Для подключения к этому драйверу приложение может использовать одну из следующих строк подключения:  
  
```  
DRIVER={Paradox Driver};Directory=C:\PARADOX;  
DRIVER={Paradox Driver};  
```  
  
 При использовании первой строки драйверу не понадобятся дополнительные сведения. Во второй строке драйверу потребуется запросить имя каталога, содержащего файлы данных.
