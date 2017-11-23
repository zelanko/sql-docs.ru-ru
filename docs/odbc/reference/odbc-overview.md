---
title: "Общие сведения об ODBC | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC [ODBC]
- ODBC [ODBC], about ODBC
ms.assetid: 233315bd-2b7f-4b20-9978-e920e1ea9a07
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 607e516c8654631ab032dfc6159a8990d464a023
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="odbc-overview"></a>Общие сведения об ODBC
Open Database Connectivity (ODBC) — широко применяемый прикладной программный интерфейс (API) для доступа к базе данных. Он основан на спецификации интерфейс уровня вызова (CLI) из Open Group и ISO/IEC для API базы данных и использует язык SQL (Structured Query) как его язык базы данных access.  
  
 ODBC предназначен для более *взаимодействие* — то есть возможность одним приложением для доступа к другой базе данных системы управления (СУБД) с одного исходного кода. Приложения баз данных вызывать функции в интерфейсе ODBC, которые реализованы в конкретной базе данных модулей, вызываемых *драйверы*. Использовать драйверы изолирует приложения из вызовов конкретной базе данных так же, что драйверы принтера изолировать текстовых файлов с помощью команд конкретного принтера. Так как драйверы будут загружаться во время выполнения, пользователь имеет только для добавления нового драйвера для доступа к новой СУБД; не нужно повторно компилировать или связывать приложения.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Зачем создали ODBC?](../../odbc/reference/why-was-odbc-created.md)  
  
-   [Что такое ODBC?](../../odbc/reference/what-is-odbc.md)  
  
-   [ODBC и стандартная инфраструктура CLI](../../odbc/reference/odbc-and-the-standard-cli.md)
