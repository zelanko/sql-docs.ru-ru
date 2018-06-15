---
title: SQLSetPos (драйверы для настольных баз данных) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLSetPos function [ODBC], Desktop Database Drivers
ms.assetid: 8ef027ec-8512-48fe-8fe2-2ff7cd81e331
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 38b1e2578e6cb4a3e337d43211dd9497cc302518
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32904909"
---
# <a name="sqlsetpos-desktop-database-drivers"></a>SQLSetPos (драйверы для настольных баз данных)
Семантика модель массовой **SQLSetPos** вызовы с *irow* поддерживаются аргумент равен 0.  
  
 Поддержка SQL_LOCK_NO_CHANGE *fLock*. SQL_LOCK_EXCLUSIVE и SQL_LOCK_UNLOCK не поддерживаются.  
  
 **SQLSetPos** поддерживает обновляемые соединения. (Дополнительные сведения см. в разделе *Microsoft Jet базы данных подсистемы Руководство программиста*.)
