---
title: Обзор архитектуры драйверов (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], architecture
- FoxPro ODBC driver [ODBC], architecture
ms.assetid: ef5a91cd-158e-40bf-b5a8-8ba535c4705e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cd55290e09fbd35f5a1559ce4209693ef8eaaf73
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303465"
---
# <a name="driver-architecture-overview"></a>Обзор архитектуры драйвера
Microsoft Visual FoxPro ODBC Driver — это 32-разрядный драйвер, позволяющий открывать и заготавлив запрос на базу данных Microsoft Visual FoxPro или таблицы FoxPro через интерфейс Open Database Connectivity (ODBC). Вы можете получить доступ к данным FoxPro, используя следующие типы приложений:  
  
-   Приложение Microsoft Office, такое как Microsoft Excel или Microsoft Word, которое использует запрос Майкрософт для связи с ODBC.  
  
-   Приложение, написанное в Microsoft Visual C или C, использующее API ODBC SDK.  
  
-   Приложение, написанное в Microsoft Visual Basic или Microsoft Visual Basic для приложений.  
  
 В каждом случае запрос на информацию использует API ODBC. Менеджер драйвера ODBC работает с Visual FoxPro ODBC Driver, чтобы открыть и получить данные из таблиц и баз данных FoxPro.  
  
 Архитектура представлена на следующей диаграмме:  
  
 ![Показывает архитектуру драйвера ODBC](../../odbc/microsoft/media/vfparch.gif "vfparch")  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Терминология Visual FoxPro](../../odbc/microsoft/visual-foxpro-terminology.md)  
  
-   [Установка и настройка визуального драйвера FoxPro ODBC](../../odbc/microsoft/installing-and-configuring.md)  
  
-   [Использование драйвера ODBC для Visual FoxPro](../../odbc/microsoft/using-the-visual-foxpro-odbc-driver.md)
