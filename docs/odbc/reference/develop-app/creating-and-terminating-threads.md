---
description: Создание и завершение потоков
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
ms.openlocfilehash: c0100b85bc596149d809dee7e6c4cb3547dbd081
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465856"
---
# <a name="creating-and-terminating-threads"></a>Создание и завершение потоков
Многопоточные приложения, использующие ODBC, должны вызывать Visual C++ Microsoft®® функции библиотеки времени выполнения **_beginthread** и **_endthread** (или **_beginthreadex** и **_endthreadex**) для создания и завершения потоков, вызывающих диспетчер драйверов ODBC. Если приложения вызывают функцию Microsoft Windows NT® функции **CreateThread** и **ендсреад** , то происходит утечка памяти, поскольку диспетчер драйверов и некоторые драйверы ODBC вызывают функции времени выполнения C, которые не будут работать в потоке, созданном путем вызова функции **CreateThread**. Дополнительные сведения см. в документации по Microsoft Windows®.
