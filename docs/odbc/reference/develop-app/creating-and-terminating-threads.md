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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3536deef604d7dbf645903e7d171a58cd9fec96a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301695"
---
# <a name="creating-and-terminating-threads"></a>Создание и завершение потоков
Многопоточные приложения, использующие ODBC, должны вызывать Visual C++ Microsoft®® функции библиотеки времени выполнения **_beginthread** и **_endthread** (или **_beginthreadex** и **_endthreadex**) для создания и завершения потоков, вызывающих диспетчер драйверов ODBC. Если приложения вызывают функцию Microsoft Windows NT® функции **CreateThread** и **ендсреад** , то происходит утечка памяти, поскольку диспетчер драйверов и некоторые драйверы ODBC вызывают функции времени выполнения C, которые не будут работать в потоке, созданном путем вызова функции **CreateThread**. Дополнительные сведения см. в документации по Microsoft Windows®.
