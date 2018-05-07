---
title: Поддерживаемые типы данных (драйвер ODBC для Visual FoxPro) | Документы Microsoft
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
- Visual FoxPro ODBC driver [ODBC], data types
- FoxPro ODBC driver [ODBC], data types
- data types [ODBC], Visual FoxPro ODBC driver
ms.assetid: ab529cc6-d157-4b35-b6f9-6ffd09af098c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 030bcc12bb8790f133af3e265cf26ffba2d23573
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="supported-data-types-visual-foxpro-odbc-driver"></a>Поддерживаемые типы данных (драйвер ODBC для Visual FoxPro)
Список типов данных, поддерживаемых драйвером представляются с помощью ODBC API и в Microsoft Query.  
  
## <a name="data-types-in-c-applications"></a>Типы данных в приложениях C  
 Можно получить список типов данных, поддерживаемых драйвером ODBC для Visual FoxPro с помощью [SQLGetTypeInfo](../../odbc/microsoft/sqlgettypeinfo-visual-foxpro-odbc-driver.md) функции в приложениях C или C++.  
  
## <a name="data-types-in-applications-using-microsoft-query"></a>Типы данных в приложениях с помощью Microsoft Query  
 Если приложение использует Microsoft Query для создания новой таблицы в источнике данных Visual FoxPro, Microsoft Query выводит **новое определение таблицы** диалоговое окно. В разделе **описание поля**, **тип** поле списки [типы данных полей Visual FoxPro](../../odbc/microsoft/visual-foxpro-field-data-types.md), представленный отдельных символов.
