---
title: SLParamOptions (Визуальный водитель FoxPro ODBC) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLParamOptions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 7f94a6e2-9c34-405c-b2b0-304d94269715
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: dd714ce7774265a2afd00d42894d644a516bc402
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299474"
---
# <a name="sqlparamoptions-visual-foxpro-odbc-driver"></a>SQLParamOptions (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Эта тема содержит Visual FoxPro ODBC Драйвер-специфической информации. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
 Поддержка: Полная  
  
 Соответствие API ODBC: Уровень 1  
  
 Позволяет приложению указать несколько значений для набора параметров, назначенных [S'LBindParameter.](../../odbc/microsoft/sqlbindparameter-visual-foxpro-odbc-driver.md) Возможность указать несколько значений для набора параметров полезна для оптовых вставок и другой работы, которая требует, чтобы источник данных обрабатывал одну и ту же выписку СЗЛ несколько раз с различными значениями параметров. Например, приложение может указать три набора значений для набора параметров, связанных с заявлением **INSERT,** а затем выполнить заявление **INSERT** один раз для выполнения трех операций вставки.  
  
 Для получения более подробной информации, *ODBC Programmer's Reference* [см.](../../odbc/reference/syntax/sqlparamoptions-function.md)
