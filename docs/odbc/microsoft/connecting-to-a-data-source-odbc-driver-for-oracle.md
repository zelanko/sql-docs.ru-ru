---
title: Подключение к источнику данных (драйвер ODBC для Oracle) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connecting to data source [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], connecting to data sources
ms.assetid: f724a9c5-342a-4f4e-a030-ec34f7378eaf
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: adee8d8dd8d6db0d79b37ff853c41e7604fe21de
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63302130"
---
# <a name="connecting-to-a-data-source-odbc-driver-for-oracle"></a>Подключение к источнику данных (драйвер ODBC для Oracle)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Приложение ODBC можно передать сведения о подключении несколькими способами. Например приложение может занимать драйвер всегда запрашивать сведения о соединении. Или приложение может ожидать, что строки подключения, указывающее соединение с источником данных. Способ подключения к источнику данных зависит от метода подключения, используемой приложением ODBC.  
  
 В диалоговом окне источник данных — один из способов подключения к источнику данных. Если приложение ODBC используйте диалоговое окно, окно отображается и запрашивает сведения о соединении источника данных.  
  
 Можно также подключиться к источнику данных с помощью [строку подключения](../../odbc/microsoft/connection-string-format-and-attributes.md).  
  
### <a name="to-connect-to-a-data-source-using-a-dialog-box"></a>Для подключения к источнику данных, используя диалоговое окно  
  
1.  В открывшемся диалоговом окне источника данных выберите источник данных Oracle и нажмите кнопку ОК. Будет открыто диалоговое окно Connect.  
  
2.  Заполните соответствующими сведениями об этом диалоговом окне подключение и нажмите кнопку ОК.  
  
 После подключения проверяются данные, приложение может использовать драйвер ODBC для Oracle для доступа к информации, которую источник данных.
