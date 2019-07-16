---
title: SQLSpecialColumns (драйверы для настольных систем баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSpecialColumns function [ODBC], Desktop Database Drivers
ms.assetid: 3de66fdf-053b-4354-979d-e76a5a5e975f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e530d0b16811cdf25a5bc1d99f5386efdb55ccd4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67905319"
---
# <a name="sqlspecialcolumns-desktop-database-drivers"></a>SQLSpecialColumns (драйверы для баз данных на настольном компьютере)
Уникальный индекс будет возвращаться (если он существует) SQL_BEST_ROWID флажка в *fColType*. Результирующий набор не возвращается для флага SQL_ROWVER.  
  
 Все идентификаторы строк имеют область SQL_SCOPE_CURROW.  
  
 Сопоставление шаблонов не поддерживается для либо *szTableQualifier* или *szTableName* аргумент.
