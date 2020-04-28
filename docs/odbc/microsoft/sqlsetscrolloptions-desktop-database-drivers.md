---
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
ms.openlocfilehash: 5c47255b455354c49133d61c3546be63ab2380a1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299442"
---
# <a name="sqlsetscrolloptions-desktop-database-drivers"></a>SQLSetScrollOptions (драйверы для баз данных на настольном компьютере)
Для SQL_CONCUR_READ_ONLY поддерживаются однонаправленные и статические курсоры.  
  
 Только курсоры, управляемые набором ключей, поддерживаются для аргумента *фконкурренци* SQL_CONCUR_LOCK.  
  
 Аргумент *фконкурренци* SQL_CONCUR_ROWVER не поддерживается.  
  
 Динамические курсоры и смешанные курсоры не поддерживаются.
