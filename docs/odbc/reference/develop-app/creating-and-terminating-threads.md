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
ms.topic: conceptual
helpviewer_keywords:
- terminating threads [ODBC]
- threads [ODBC]
- multithreaded applications [ODBC]
ms.assetid: a2cf98ef-1c71-4742-8ee2-b53fd8e04333
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 92f69906811791a56134094fb4b05859763d1624
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="creating-and-terminating-threads"></a>Создание и завершение работы с потоками
Многопоточные приложения, использующие ODBC следует вызывать функции библиотеки времени выполнения Visual C++® для Microsoft® **_beginthread** и **_endthread** (или **_beginthreadex** и **_endthreadex**), чтобы создать и завершить потоки, которые вызывают диспетчер драйверов ODBC. Если приложения вызывают функции Microsoft Windows NT® **CreateThread** и **EndThread** вместо этого, функционирует в память, утечки будет происходить, поскольку диспетчер драйверов и некоторые драйверы ODBC вызовите времени выполнения C не будут работать на поток, созданный путем вызова **CreateThread**. Дополнительные сведения см. в документации Microsoft Windows®.
