---
title: Создание и завершение потоков | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- terminating threads [ODBC]
- threads [ODBC]
- multithreaded applications [ODBC]
ms.assetid: a2cf98ef-1c71-4742-8ee2-b53fd8e04333
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b97f29ad06c4ed961f3cee571b0ca7b8d9c0b774
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68002081"
---
# <a name="creating-and-terminating-threads"></a>Создание и завершение потоков
Многопоточные приложения, использующие ODBC должны вызывать Microsoft® Visual C++® функции библиотеки времени выполнения **_beginthread** и **_endthread** (или **_beginthreadex**и **_endthreadex**) для создания и завершения потоков, которые вызывают диспетчер драйверов ODBC. Если приложения вызывают функции Microsoft Windows NT® **CreateThread** и **EndThread** вместо этого функции памяти, утечек произойдет в том случае, так как диспетчер драйверов и некоторые драйверы ODBC вызовите времени выполнения C, не будет работать в потоке, созданном путем вызова **CreateThread**. Дополнительные сведения см. в документации Microsoft Windows®.
