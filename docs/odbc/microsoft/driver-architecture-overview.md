---
title: Общие сведения об архитектуре драйвер | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], architecture
- FoxPro ODBC driver [ODBC], architecture
ms.assetid: ef5a91cd-158e-40bf-b5a8-8ba535c4705e
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f2b51c07e6c0b0cbff386ae80ec7ccec519e5316
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="driver-architecture-overview"></a>Общие сведения об архитектуре драйвера
Драйвер ODBC Microsoft Visual FoxPro является 32-разрядный драйвер, который позволяет открыть и запрос базы данных Microsoft Visual FoxPro или FoxPro таблиц с помощью интерфейса откройте Database Connectivity (ODBC). Вы можете использовать данные FoxPro, с помощью следующих типов приложений:  
  
-   Приложения Microsoft Office, таких как Microsoft Excel или Microsoft Word, Microsoft Query, использует для взаимодействия с ODBC.  
  
-   Приложения, написанного на языке Microsoft Visual C++ или C, которое использует ODBC SDK API.  
  
-   Приложения, написанного на языке Microsoft Visual Basic или Microsoft Visual Basic для приложений.  
  
 В каждом случае запрос данных использует ODBC API. Диспетчер драйверов ODBC работает с Visual FoxPro драйвер ODBC для открытия и получения данных из FoxPro таблиц и баз данных.  
  
 На следующей диаграмме представлены архитектуры:  
  
 ![Архитектура драйвера ODBC](../../odbc/microsoft/media/vfparch.gif "vfparch")  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Терминология Visual FoxPro](../../odbc/microsoft/visual-foxpro-terminology.md)  
  
-   [Установка и настройка драйвера ODBC Visual FoxPro](../../odbc/microsoft/installing-and-configuring.md)  
  
-   [Использование драйвера ODBC для Visual FoxPro](../../odbc/microsoft/using-the-visual-foxpro-odbc-driver.md)
