---
title: С помощью служб компонентов Microsoft | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], component services
- component services [ODBC]
ms.assetid: 06450562-d8f3-4987-b7bd-4a70223ff937
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c28df0cd6000a4ae0b2cb500a9521dc32facc6c9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="using-microsoft-component-services"></a>С помощью служб компонентов Microsoft
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Базы данных Oracle для работы с транзакционной службы компонентов (или MTS, если вы используете Windows NT) можно включить в Microsoft Windows NT, Windows 2000 и Microsoft Windows 95/98. Для включения базы данных Oracle для работы с компонентом службы, поддерживающие транзакции, системные администраторы должны создать представление V$ XATRANS$. Для создания этого сценария, необходимо запустить сценарий, предоставляемый Oracle. Дополнительные сведения см. в разделе справке служб компонентов или документации Oracle.
