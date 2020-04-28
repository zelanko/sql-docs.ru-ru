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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d6aacb5d3df985949e04cdd47a9fe460cddbde6a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299084"
---
# <a name="connecting-directly-to-drivers"></a>Прямое подключение к драйверам
Как было сказано при [выборе источника данных или драйвера](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md), ранее в этом разделе некоторые приложения не хотят использовать источник данных. Вместо этого они хотят напрямую подключаться к драйверу. **SQLDriverConnect** предоставляет приложению возможность напрямую подключаться к драйверу, не указывая источник данных. По сути, во время выполнения создается временный источник данных.  
  
 Для прямого подключения к драйверу приложение указывает в строке подключения ключевое слово **Driver** , а не ключевое слово **DSN** . Значением ключевого слова **Driver** является описание драйвера, возвращаемое функцией **SQLDrivers**. Например, предположим, что драйвер содержит описание драйвера Paradox и требует указания имени каталога, содержащего файлы данных. Для подключения к этому драйверу приложение может использовать одну из следующих строк подключения:  
  
```  
DRIVER={Paradox Driver};Directory=C:\PARADOX;  
DRIVER={Paradox Driver};  
```  
  
 При использовании первой строки драйверу не понадобятся дополнительные сведения. Во второй строке драйверу потребуется запросить имя каталога, содержащего файлы данных.
