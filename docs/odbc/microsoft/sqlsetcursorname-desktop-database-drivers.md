---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 53ef01423ad14cb5606e14ca004ca614e68101e4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67905503"
---
# <a name="sqlsetcursorname-desktop-database-drivers"></a>SQLSetCursorName (драйверы для баз данных на настольном компьютере)
Поскольку драйвер не поддерживает позиционированное обновление или удаление с помощью синтаксиса *курсорнаме* , **SQLSetCursorName** поддерживается, но не может использоваться для позиционированных обновлений. Его можно использовать, только если включена библиотека курсоров и приложение использует **SQLExtendedFetch**.
