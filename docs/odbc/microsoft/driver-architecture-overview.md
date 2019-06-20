---
title: Обзор архитектуры драйвера | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0fdb1789c6640c072ec013c341bd4889b28bb469
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63128098"
---
# <a name="driver-architecture-overview"></a>Обзор архитектуры драйвера
Драйвер ODBC Microsoft Visual FoxPro является 32-разрядный драйвер, который позволяет открыть и запроса базы данных Microsoft Visual FoxPro или таблицы FoxPro через интерфейс откройте Database Connectivity (ODBC). Вы сможете использовать данные FoxPro, используя следующие типы приложений:  
  
-   Приложения Microsoft Office, например Microsoft Excel или Microsoft Word, который использует Microsoft Query для взаимодействия с ODBC.  
  
-   Приложения, написанного в Microsoft Visual C++ или C, которое использует ODBC SDK API.  
  
-   Приложения, написанного в Microsoft Visual Basic или Microsoft Visual Basic для приложений.  
  
 В каждом случае запрос данных использует ODBC API. Диспетчер драйверов ODBC работает с помощью драйвера ODBC для Visual FoxPro для открытия и получения данных из таблицы FoxPro и базы данных.  
  
 Архитектура представлена на следующей схеме:  
  
 ![Архитектура драйвера ODBC](../../odbc/microsoft/media/vfparch.gif "vfparch")  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Терминология Visual FoxPro](../../odbc/microsoft/visual-foxpro-terminology.md)  
  
-   [Установка и настройка драйвера ODBC для Visual FoxPro](../../odbc/microsoft/installing-and-configuring.md)  
  
-   [Использование драйвера ODBC для Visual FoxPro](../../odbc/microsoft/using-the-visual-foxpro-odbc-driver.md)
