---
title: Обзор ODBC (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC]
- ODBC [ODBC], about ODBC
ms.assetid: 233315bd-2b7f-4b20-9978-e920e1ea9a07
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0a0515a882cd7d1c97a60e9262942bd7c397b0b2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298294"
---
# <a name="odbc-overview"></a>Общие сведения об ODBC
Open Database Connectivity (ODBC) — это широко признанный интерфейс программирования приложений (API) для доступа к базе данных. Он основан на спецификациях интерфейса Call-Level (CLI) от Open Group и ISO/IEC для AI базы данных и использует язык структурированного запроса (S'L) в качестве языка доступа к базе данных.  
  
 ODBC предназначен для максимальной *совместимости,* т.е. способности одного приложения получить доступ к различным системам управления базами данных (DBMS) с одним и тем же исходным кодом. Приложения баз данных вызывают функции в интерфейсе ODBC, которые реализованы в модулях, называемых *драйверами,* которые используются в определенных базах данных. Использование драйверов изолирует приложения от вызовов, связанных с базой данных, таким же образом, что драйверы принтеров изолируют программы обработки текстов из команд, специфичных для принтеров. Поскольку драйверы загружаются во время выполнения, пользователю достаточно добавить новый драйвер для доступа к новому DBMS; нет необходимости перекомпилировать или переувязывать приложение.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Зачем создали ODBC?](../../odbc/reference/why-was-odbc-created.md)  
  
-   [Что такое ODBC?](../../odbc/reference/what-is-odbc.md)  
  
-   [ODBC и стандартная инфраструктура CLI](../../odbc/reference/odbc-and-the-standard-cli.md)
