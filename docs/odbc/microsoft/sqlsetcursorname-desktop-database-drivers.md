---
description: SQLSetCursorName (драйверы для баз данных на настольном компьютере)
title: SQLSetCursorName (драйверы баз данных для настольных систем) | Документация Майкрософт
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
ms.openlocfilehash: 14fe15c6cdbdf50e6d28ca7e9a1168f54626e83b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88411559"
---
# <a name="sqlsetcursorname-desktop-database-drivers"></a>SQLSetCursorName (драйверы для баз данных на настольном компьютере)
Поскольку драйвер не поддерживает позиционированное обновление или удаление с помощью синтаксиса *курсорнаме* , **SQLSetCursorName** поддерживается, но не может использоваться для позиционированных обновлений. Его можно использовать, только если включена библиотека курсоров и приложение использует **SQLExtendedFetch**.
