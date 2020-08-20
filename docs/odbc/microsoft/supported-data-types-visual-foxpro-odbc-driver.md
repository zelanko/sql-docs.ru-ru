---
description: Поддерживаемые типы данных (драйвер ODBC для Visual FoxPro)
title: Поддерживаемые типы данных (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
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
ms.openlocfilehash: 04f2039d18f134fe2c48397f6c0dc987e97bf47d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471526"
---
# <a name="supported-data-types-visual-foxpro-odbc-driver"></a>Поддерживаемые типы данных (драйвер ODBC для Visual FoxPro)
Список типов данных, поддерживаемых драйвером, представлен в API ODBC и в Microsoft Query.  
  
## <a name="data-types-in-c-applications"></a>Типы данных в приложениях на языке C  
 Список типов данных, поддерживаемых драйвером ODBC для Visual FoxPro, можно получить с помощью функции [SQLGetTypeInfo](../../odbc/microsoft/sqlgettypeinfo-visual-foxpro-odbc-driver.md) в приложениях C или C++.  
  
## <a name="data-types-in-applications-using-microsoft-query"></a>Типы данных в приложениях, использующих Microsoft Query  
 Если приложение использует Microsoft Query для создания новой таблицы в источнике данных Visual FoxPro, Microsoft Query выводит диалоговое окно **новое определение таблицы** . В поле " **Описание поля**" в поле " **тип** " перечислены [типы данных полей Visual FoxPro](../../odbc/microsoft/visual-foxpro-field-data-types.md), представленные отдельными символами.
