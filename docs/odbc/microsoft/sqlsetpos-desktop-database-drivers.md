---
title: SQLSetPos (драйверы для настольных систем баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetPos function [ODBC], Desktop Database Drivers
ms.assetid: 8ef027ec-8512-48fe-8fe2-2ff7cd81e331
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 95117c82c213851d2e0600e65d8061ce532d9933
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63200453"
---
# <a name="sqlsetpos-desktop-database-drivers"></a>SQLSetPos (драйверы для баз данных на настольном компьютере)
Семантика модель массовой для **SQLSetPos** вызывает с *irow* поддерживаются аргумента равно 0.  
  
 Обеспечивается поддержка SQL_LOCK_NO_CHANGE *fLock*. SQL_LOCK_EXCLUSIVE и SQL_LOCK_UNLOCK не поддерживаются.  
  
 **SQLSetPos** поддерживает обновляемые соединения. (Дополнительные сведения см. в разделе *Microsoft Jet Database Engine Programmer's Guide*.)
