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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0adedfb69cd4a7b5cf195916747687826805e8bf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67905393"
---
# <a name="sqlsetscrolloptions-desktop-database-drivers"></a>SQLSetScrollOptions (драйверы для баз данных на настольном компьютере)
Для SQL_CONCUR_READ_ONLY поддерживаются однонаправленные и статические курсоры.  
  
 Только курсоры, управляемые набором ключей, поддерживаются для аргумента *фконкурренци* SQL_CONCUR_LOCK.  
  
 Аргумент *фконкурренци* SQL_CONCUR_ROWVER не поддерживается.  
  
 Динамические курсоры и смешанные курсоры не поддерживаются.
