---
title: Соединение с источником данных (драйвер ODBC для Oracle) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connecting to data source [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], connecting to data sources
ms.assetid: f724a9c5-342a-4f4e-a030-ec34f7378eaf
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7c12472544fd843214cab4294311889d0a84010d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="connecting-to-a-data-source-odbc-driver-for-oracle"></a>Соединение с источником данных (драйвер ODBC для Oracle)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Приложения ODBC можно передать сведения о соединении несколькими способами. Например приложение может иметь драйвер всегда запрашивать у пользователя сведения о соединении. Или приложение предположить, что строка подключения указывает соединение с источником данных. Способ подключения к источнику данных зависит от метода подключения, используемого приложением ODBC.  
  
 В диалоговом окне источник данных — один распространенный способ подключения к источнику данных. Если приложение ODBC использовать диалоговое окно, окно отображается и запрашивает сведения о соединении источника данных.  
  
 Можно также подключиться к источнику данных с помощью [строка подключения](../../odbc/microsoft/connection-string-format-and-attributes.md).  
  
### <a name="to-connect-to-a-data-source-using-a-dialog-box"></a>Для подключения к источнику данных с помощью диалогового окна  
  
1.  В открывшемся диалоговом окне источника данных выберите источник данных Oracle и нажмите кнопку ОК. Появится диалоговое окно подключение.  
  
2.  Введите соответствующие сведения в диалоговое окно «подключение» и нажмите кнопку ОК.  
  
 После установления соединения осуществляется, приложение может использовать драйвер ODBC для Oracle, доступ к сведениям, содержащиеся в источнике данных.
