---
title: "Диагностические записи | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- handles [ODBC], diagnostic records
- header records [ODBC]
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 92c73f9b-3ed7-410d-9cec-2771004aae60
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: df08adfc15a2ad80bac007a65ce4ed9304194f20
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="diagnostic-records"></a>Диагностические записи
Связанный с каждой среды, подключения, инструкции и дескриптора, *диагностические записи*. Эти записи содержат диагностическую информацию о последней функция, вызываемая используемой определенного дескриптора. Записи заменяются только в том случае, если будет вызвана другая функция, с помощью данного дескриптора. Не ограничено число диагностических записях, которые могут храниться в любой момент времени.  
  
 Существует два типа диагностических записей: *запись заголовка* и ноль или более *записи состояния*. Заголовочная запись имеет номер 0; Состояние записи являются записями 1 и выше. Диагностические записи состоят из нескольких отдельных полей, которые различны для записи заголовка и записи состояния. Кроме того компоненты ODBC можно определить собственные поля диагностических записей.  
  
 Несмотря на то, что диагностические записи можно рассматривать как структуры, нет необходимости их фактически структуры; хранением драйвером диагностических сведений зависит от конкретного драйвера.  
  
 Поля диагностических записей, извлекаются с помощью **SQLGetDiagField**. SQLSTATE, номер внутренней ошибки и диагностическое сообщение поля записи состояния можно получить в рамках одного вызова с **SQLGetDiagRec**.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Запись заголовка](../../../odbc/reference/develop-app/header-record.md)  
  
-   [Записи состояния](../../../odbc/reference/develop-app/status-records.md)
