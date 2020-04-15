---
title: S'LSetCursorName (Драйверы базы данных для рабочей стола) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetCursorName function [ODBC], Desktop Database Drivers
ms.assetid: 9bd7c87b-d99d-4e23-b2db-868d3b461c94
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5d618a7f845a87394c2fc3c7978a7aef5716e21f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301485"
---
# <a name="sqlsetcursorname-desktop-database-drivers"></a>SQLSetCursorName (драйверы для баз данных на настольном компьютере)
Поскольку драйвер не поддерживает позиционированное обновление или удаление синтаксисом WHERE CURRENT of *cursorname,* **S'LSetCursorName** поддерживается, но не может быть использован для позиционных обновлений. Он может быть использован только в том случае, если библиотека Cursor включена и приложение использует **S'LExtendedFetch.**
