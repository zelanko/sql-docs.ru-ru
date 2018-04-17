---
title: Создание и завершение работы с потоками | Документы Microsoft
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
ms.topic: article
helpviewer_keywords:
- terminating threads [ODBC]
- threads [ODBC]
- multithreaded applications [ODBC]
ms.assetid: a2cf98ef-1c71-4742-8ee2-b53fd8e04333
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6f78b0e2b210385e9ffe32427145ba03395188a3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="creating-and-terminating-threads"></a>Создание и завершение работы с потоками
Многопоточные приложения, использующие ODBC следует вызывать функции библиотеки времени выполнения Visual C++® для Microsoft® **_beginthread** и **_endthread** (или **_beginthreadex** и **_endthreadex**), чтобы создать и завершить потоки, которые вызывают диспетчер драйверов ODBC. Если приложения вызывают функции Microsoft Windows NT® **CreateThread** и **EndThread** вместо этого, функционирует в память, утечки будет происходить, поскольку диспетчер драйверов и некоторые драйверы ODBC вызовите времени выполнения C не будут работать на поток, созданный путем вызова **CreateThread**. Дополнительные сведения см. в документации Microsoft Windows®.
