---
title: Создание и прекращение нитей Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301695"
---
# <a name="creating-and-terminating-threads"></a>Создание и завершение потоков
Многопоточные приложения, которые используют ODBC, должны вызывать функции Microsoft® Visual C-® Run-Time Library **_beginthread** и **_endthread** (или **_beginthreadex** и **_endthreadex)** для создания и прекращения потоков, которые называются менеджером драйверов ODBC. Если вместо этого приложения называют Microsoft Windows NT® функции **CreateThread** и **EndThread,** утечки памяти произойдут из-за того, что менеджер драйверов и некоторые драйверы ODBC вызывают функции c run-time, которые не будут работать на потоке, созданном **вызывая CreateThread.** Для получения дополнительной информаци®и см.
