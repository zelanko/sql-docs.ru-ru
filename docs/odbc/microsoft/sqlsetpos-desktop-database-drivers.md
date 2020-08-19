---
description: SQLSetPos (драйверы для баз данных на настольном компьютере)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4aa126514bc84f5546e1f4a022d8d3e6235b2e7c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421668"
---
# <a name="sqlsetpos-desktop-database-drivers"></a>SQLSetPos (драйверы для баз данных на настольном компьютере)
Поддерживается семантика с массовыми моделями для вызовов **SQLSetPos** с аргументом *IRow* , равным 0.  
  
 SQL_LOCK_NO_CHANGE поддерживается для *флокк*. SQL_LOCK_EXCLUSIVE и SQL_LOCK_UNLOCK не поддерживаются.  
  
 **SQLSetPos** поддерживает обновляемые объединения. (Дополнительные сведения см. в *справочнике программиста по Microsoft Jet ядро СУБД*.)
