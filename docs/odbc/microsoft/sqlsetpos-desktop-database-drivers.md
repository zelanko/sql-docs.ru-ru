---
title: SQLSetPos (драйверы базы данных для настольных систем) | Документация Майкрософт
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
ms.openlocfilehash: d35a282acf3b672113ec71b534b4087aa3549285
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67905466"
---
# <a name="sqlsetpos-desktop-database-drivers"></a>SQLSetPos (драйверы для баз данных на настольном компьютере)
Поддерживается семантика с массовыми моделями для вызовов **SQLSetPos** с аргументом *IRow* , равным 0.  
  
 SQL_LOCK_NO_CHANGE поддерживается для *флокк*. SQL_LOCK_EXCLUSIVE и SQL_LOCK_UNLOCK не поддерживаются.  
  
 **SQLSetPos** поддерживает обновляемые объединения. (Дополнительные сведения см. в *справочнике программиста по Microsoft Jet ядро СУБД*.)
