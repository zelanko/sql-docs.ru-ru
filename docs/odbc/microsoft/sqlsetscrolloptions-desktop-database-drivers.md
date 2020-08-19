---
description: SQLSetScrollOptions (драйверы для баз данных на настольном компьютере)
title: SQLSetScrollOptions (драйверы баз данных для настольных систем) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], Desktop Database Drivers
ms.assetid: 51d643ed-015b-4639-969a-9491d9875aca
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 57237aca0a68119f6ab8f967b9641f2a2a52fc8c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421648"
---
# <a name="sqlsetscrolloptions-desktop-database-drivers"></a>SQLSetScrollOptions (драйверы для баз данных на настольном компьютере)
Для SQL_CONCUR_READ_ONLY поддерживаются однонаправленные и статические курсоры.  
  
 Только курсоры, управляемые набором ключей, поддерживаются для аргумента *фконкурренци* SQL_CONCUR_LOCK.  
  
 Аргумент *фконкурренци* SQL_CONCUR_ROWVER не поддерживается.  
  
 Динамические курсоры и смешанные курсоры не поддерживаются.
