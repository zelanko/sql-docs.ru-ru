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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68002081"
---
# <a name="creating-and-terminating-threads"></a>Создание и завершение потоков
Многопоточные приложения, использующие ODBC, должны вызывать Visual C++ Microsoft®® функции библиотеки времени выполнения **_beginthread** и **_endthread** (или **_beginthreadex** и **_endthreadex**) для создания и завершения потоков, вызывающих диспетчер драйверов ODBC. Если приложения вызывают функцию Microsoft Windows NT® функции **CreateThread** и **ендсреад** , то происходит утечка памяти, поскольку диспетчер драйверов и некоторые драйверы ODBC вызывают функции времени выполнения C, которые не будут работать в потоке, созданном путем вызова функции **CreateThread**. Дополнительные сведения см. в документации по Microsoft Windows®.
