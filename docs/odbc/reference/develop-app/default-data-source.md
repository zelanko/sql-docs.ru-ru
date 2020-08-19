---
description: Источник данных по умолчанию
title: Источник данных по умолчанию | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0aecd2ec64926a9d1a38d8e3d603124d45223004
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424719"
---
# <a name="default-data-source"></a>Источник данных по умолчанию
Драйвер может выбрать источник данных, называемый источником данных по умолчанию, в некоторых случаях, когда приложение явно не укажет его.  
  
-   В вызове **SQLConnect** , где аргумент *ServerName* является строкой нулевой длины, пустым указателем или значением по умолчанию.  
  
-   При вызове **SQLDriverConnect** , где *onconnectionstring* указывает **DSN**= Default или указывает ключевому слову **DSN** источник данных, не содержащийся в системной информации.  
  
 Он определяется драйвером, определяющим, как задается источник данных по умолчанию. Это может привести к административному действию и может зависеть от пользователя.
