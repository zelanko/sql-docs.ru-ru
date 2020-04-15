---
title: Поддерживаемые типы данных (Визуальный драйвер FoxPro ODBC) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], data types
- FoxPro ODBC driver [ODBC], data types
- data types [ODBC], Visual FoxPro ODBC driver
ms.assetid: ab529cc6-d157-4b35-b6f9-6ffd09af098c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3fc28464a7c14f9801473cc125b0e90c50247d68
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301104"
---
# <a name="supported-data-types-visual-foxpro-odbc-driver"></a>Поддерживаемые типы данных (драйвер ODBC для Visual FoxPro)
Список типов данных, поддерживаемых драйвером, представлен через API ODBC и в Запросе Майкрософт.  
  
## <a name="data-types-in-c-applications"></a>Типы данных в C-приложениях  
 Вы можете получить список типов данных, поддерживаемых Visual FoxPro ODBC Driver, используя функцию [S'LGetTypeInfo](../../odbc/microsoft/sqlgettypeinfo-visual-foxpro-odbc-driver.md) в приложениях C или C.  
  
## <a name="data-types-in-applications-using-microsoft-query"></a>Типы данных в приложениях с использованием запроса Майкрософт  
 Если приложение использует запрос Майкрософт для создания новой таблицы в источнике данных Visual FoxPro, Microsoft Query отображает **диалоговый** ящик нового определения таблицы. Под **полем Описание**, **Тип** поле списки [Визуальные Типы полей FoxPro типов данных](../../odbc/microsoft/visual-foxpro-field-data-types.md), представленных отдельными символами.
