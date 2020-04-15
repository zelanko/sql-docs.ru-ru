---
title: Источник данных по умолчанию (ru) Документы Майкрософт
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
ms.openlocfilehash: 978362b7dfe92d1333f83be684f6326cf25dd69b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305995"
---
# <a name="default-data-source"></a>Источник данных по умолчанию
В некоторых случаях, когда приложение явно не указывает один из источников данных, называемый источником данных по умолчанию, в некоторых случаях, когда приложение явно не указывает один из них:  
  
-   При вызове в **S'LConnect,** где аргумент *ServerName* представляет собой строку нулевой длины, указатель нулевой или DEFAULT.  
  
-   При звонке в **S'LDriverConnect,** где *InConnectionString* либо указывает **DSN**по-делу, либо указывает с ключевым словом **DSN** источник данных, который не содержится в информации о системе.  
  
 Определяется драйвером, как указан источник данных по умолчанию. Это может повлечь за собой административные действия и может зависеть от пользователя.
