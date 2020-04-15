---
title: Общие приложения Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], generic applications
- interoperability [ODBC], levels
- generic applications [ODBC]
ms.assetid: dda2a3c4-76ef-40a6-b3a1-9e95bed61618
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 607676d5370f02ee1d39196bff9261bc897521ee
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305555"
---
# <a name="generic-applications"></a>Универсальные приложения
Общие приложения иногда выполняют задачу с жестким кодом, например электронную таблицу, извлекающую данные из базы данных. Они также могут выполнять различные задачи, определяемые пользователями, такие как общее приложение запроса, позволяющее пользователю вводить и выполнять выписку по S'L. Что общего имеет общие приложения, так это то, что они должны работать с различными DBMS и что разработчик не знает заранее, что эти DBMSs будет.  
  
 Таким образом, общие приложения должны быть высокосовместимыми. Разработчик должен сделать много вариантов, торгуя совместимостью с функциями, и должен написать код, который ожидает, что драйверы будут поддерживать широкий спектр функциональных возможностей. Хотя универсальные приложения могут быть настроены на работу с популярными DBMS, они редко содержат код, специфичный для драйверов или DBMS.
