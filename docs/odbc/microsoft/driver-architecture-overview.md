---
description: Обзор архитектуры драйвера
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d71a2c28825ee8c7d4e12e047234f3e336b339e0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466446"
---
# <a name="driver-architecture-overview"></a>Обзор архитектуры драйвера
Драйвер ODBC для Microsoft Visual FoxPro — это 32-разрядный драйвер, который позволяет открывать и запрашивать базы данных Microsoft Visual FoxPro или таблицы FoxPro через интерфейс ODBC. Доступ к данным FoxPro можно получить с помощью следующих типов приложений:  
  
-   Microsoft Office приложение, например Microsoft Excel или Microsoft Word, которое использует Microsoft Query для взаимодействия с ODBC.  
  
-   Приложение, написанное на Microsoft Visual C++ или C, использующее API-интерфейс ODBC SDK.  
  
-   Приложение, написанное на Microsoft Visual Basic или Microsoft Visual Basic для приложений.  
  
 В каждом случае запрос сведений использует API ODBC. Диспетчер драйверов ODBC работает с драйвером ODBC для Visual FoxPro, чтобы открывать и получать данные из таблиц и баз данных FoxPro.  
  
 Архитектура представлена на следующей схеме:  
  
 ![Показывает архитектуру драйвера ODBC](../../odbc/microsoft/media/vfparch.gif "вфпарч")  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Терминология Visual FoxPro](../../odbc/microsoft/visual-foxpro-terminology.md)  
  
-   [Установка и Настройка драйвера ODBC для Visual FoxPro](../../odbc/microsoft/installing-and-configuring.md)  
  
-   [Использование драйвера ODBC для Visual FoxPro](../../odbc/microsoft/using-the-visual-foxpro-odbc-driver.md)
