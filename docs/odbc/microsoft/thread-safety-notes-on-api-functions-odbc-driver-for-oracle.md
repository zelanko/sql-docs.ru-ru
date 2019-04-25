---
title: Заметки о потокобезопасности функций API (драйвер ODBC для Oracle) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], threading
- threading options [ODBC]
- multiple concurrent statements [ODBC]
ms.assetid: f0c9bdfd-f79d-4088-9ecb-afcd8ca7fb73
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2d1faa7dfd8873b8c11cda5cb3e67d5408c35474
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62633219"
---
# <a name="thread-safety-notes-on-api-functions-odbc-driver-for-oracle"></a>Замечания о потокобезопасности функций API (драйвер ODBC для Oracle)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Драйвер Microsoft ODBC для Oracle является поточно ориентированной; Тем не менее Oracle не поддерживает несколько параллельных инструкций в одном соединении. Это требование драйвера. Другими словами в многопоточных приложениях, несмотря на то, что драйвер ODBC для Oracle в любое время можете вызывать любой поток драйвер блоков любого другого потока в драйвере, в том же соединении пока исходный поток не драйвер.  
  
 Драйвер не блокируется, если имеются две инструкции для двух разных подключений. Тем не менее если имеется одно подключение с помощью двух инструкций, существует угроза для блокировки.
