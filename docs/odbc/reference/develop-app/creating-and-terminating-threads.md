---
title: "Создание и завершение работы с потоками | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- terminating threads [ODBC]
- threads [ODBC]
- multithreaded applications [ODBC]
ms.assetid: a2cf98ef-1c71-4742-8ee2-b53fd8e04333
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1035c59acfaa8c28582751b7c4d97b1d02cce920
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="creating-and-terminating-threads"></a>Создание и завершение работы с потоками
Многопоточные приложения, использующие ODBC следует вызывать функции библиотеки времени выполнения Visual C++® для Microsoft® **_beginthread** и **_endthread** (или **_beginthreadex** и **_endthreadex**), чтобы создать и завершить потоки, которые вызывают диспетчер драйверов ODBC. Если приложения вызывают функции Microsoft Windows NT® **CreateThread** и **EndThread** вместо этого, функционирует в память, утечки будет происходить, поскольку диспетчер драйверов и некоторые драйверы ODBC вызовите времени выполнения C не будут работать на поток, созданный путем вызова **CreateThread**. Дополнительные сведения см. в документации Microsoft Windows®.
