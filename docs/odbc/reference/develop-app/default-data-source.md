---
title: По умолчанию источник данных | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], connection functions
- connecting to data source [ODBC], default data source
- functions [ODBC], data source or driver connections
- data sources [ODBC], default
- default data source [ODBC]
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], default data source
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- ODBC drivers [ODBC], connection functions
ms.assetid: dd473cc6-f051-4aa0-ab14-3dd1b37fe99e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 909f9b3e7c8087add8eb66ca2f5c15253026304c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63267659"
---
# <a name="default-data-source"></a>Источник данных по умолчанию
Драйвер может выбрать источник данных, с именем источника данных по умолчанию, в некоторых случаях, где приложение явно не задают:  
  
-   При вызове **SQLConnect** где *ServerName* аргумент является пустой строкой, является пустым указателем или по умолчанию.  
  
-   При вызове **SQLDriverConnect** где *InConnectionString* либо указывает **DSN**= значение по умолчанию или задает с **DSN** ключевое слово источник данных, не содержится в сведениях о системе.  
  
 Это определенное драйвером как указывается источник данных по умолчанию. Это может включать в себя действия администратора и может зависеть от пользователя.
