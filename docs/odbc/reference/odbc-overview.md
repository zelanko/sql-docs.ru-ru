---
title: Общие сведения об ODBC | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6b064436dae6cb2f3d5f37fa02ab57a1e4a3f015
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47801542"
---
# <a name="odbc-overview"></a>Общие сведения об ODBC
Open Database Connectivity (ODBC) — широко применяемый прикладной программный интерфейс (API) для доступа к базе данных. Он основан на спецификации интерфейс уровня вызова (CLI) из Open Group и ISO/IEC для функций API базы данных и использует язык структурированных запросов (SQL) в качестве языка доступа базы данных.  
  
 ODBC предназначен для максимально *взаимодействие* — то есть возможность одного приложения для доступа к систем управления другой базе данных (СУБД) с помощью того же исходного кода. База данных приложения вызывают функции через интерфейс ODBC, которые реализованы в конкретной базе данных модулей, которые называются *драйверы*. Драйверы изолирует приложения из вызовов конкретной базы данных так же, что драйверы принтера изолировать обработки текстов программ из команды конкретного принтера. Поскольку драйверы загружаются во время выполнения, пользователь должен только добавить новый драйвер для доступа к новой СУБД; Это не нужно повторно компилировать или связывать приложения.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Зачем создали ODBC?](../../odbc/reference/why-was-odbc-created.md)  
  
-   [Что такое ODBC?](../../odbc/reference/what-is-odbc.md)  
  
-   [ODBC и стандартная инфраструктура CLI](../../odbc/reference/odbc-and-the-standard-cli.md)
