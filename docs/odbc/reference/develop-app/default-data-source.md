---
title: "По умолчанию источник данных | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c27bbdf1bf188ba29fc6ddbb98d1c48ab8a4de7e
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="default-data-source"></a>Источник данных по умолчанию
Драйвер может выбрать источник данных, называется источник данных по умолчанию, в некоторых случаях, когда приложение не задает явным образом:  
  
-   При обращении к **SQLConnect** где *ServerName* аргументом является строка нулевой длины, является пустым указателем или по умолчанию.  
  
-   При обращении к **SQLDriverConnect** где *InConnectionString* либо указывает **DSN**= значение по умолчанию или задает с **DSN** ключевое слово источник данных, не содержится сведений о системе.  
  
 Это определяемые драйвером как указывается источник данных по умолчанию. Это может привести к административным действием и может зависеть от пользователя.
