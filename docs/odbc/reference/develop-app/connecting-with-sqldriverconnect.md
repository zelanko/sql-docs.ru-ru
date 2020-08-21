---
title: Подключение с помощью SQLDriverConnect | Документация Майкрософт
description: SQLDriverConnect предоставляет дополнительные функции подключения по сравнению с SQLConnect, включая параметры, предлагающие пользователю получить дополнительные сведения.
ms.custom: ''
ms.date: 08/20/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], connection functions
- functions [ODBC], data source or driver connections
- connecting to data source [ODBC], SQLDriverConnect
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- SQLDriverConnect function [ODBC], connecting
- connection functions [ODBC]
- ODBC drivers [ODBC], connection functions
ms.assetid: e46e959f-d3c5-4ddb-810a-107bfcb83fd2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 78186e903405aa1b59cfac185e62646dbda6e77a
ms.sourcegitcommit: dc8a30a4a27e15fc6671ca2674da9b7c637ec255
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/21/2020
ms.locfileid: "88746174"
---
# <a name="connecting-with-sqldriverconnect"></a>Подключение с помощью SQLDriverConnect

**SQLDriverConnect** используется для подключения к источнику данных с помощью строки подключения. **SQLDriverConnect** используется вместо **SQLConnect** в следующих сценариях:  
  
- Установите соединение, используя строку подключения, содержащую имя источника данных, один или несколько идентификаторов пользователей, один или несколько паролей и другие сведения, необходимые для источника данных.  
  
- Установите соединение с помощью частичной строки подключения или без дополнительных сведений. в этом случае диспетчер драйверов и драйвер могут запрашивать у пользователя сведения о подключении.  
  
- Установите соединение с источником данных, который не определен в сведениях о системе. Если приложение предоставляет строку частичного подключения, драйвер может запросить у пользователя сведения о подключении.  
  
- Установите соединение с источником данных, используя строку подключения, созданную на основе информации в DSN-файле.  
  
После установки соединения **SQLDriverConnect** возвращает строку завершенного подключения. Приложение может использовать эту строку для последующих запросов на подключение.

Этот раздел содержит следующие подразделы.  
  
- [Сведения о подключении для конкретного драйвера](driver-specific-connection-information.md)  
  
- [Запрос сведений о подключении у пользователя](prompting-the-user-for-connection-information.md)  
  
- [Подключение с использованием файловых источников данных](connecting-using-file-data-sources.md)  
  
- [Прямое подключение к драйверам](connecting-directly-to-drivers.md)
