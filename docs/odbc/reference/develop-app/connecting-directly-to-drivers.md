---
title: Подключение непосредственно к драйверам (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], SqlDriverConnect
- SQLDriverConnect function [ODBC], connecting directly to drivers
- connecting to driver [ODBC], drivers
ms.assetid: f86e198f-a088-4401-9106-aa62a0eb8f6e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d6aacb5d3df985949e04cdd47a9fe460cddbde6a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299084"
---
# <a name="connecting-directly-to-drivers"></a>Прямое подключение к драйверам
Как обсуждалось в [разделе «Выбор источника данных или драйвера»,](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)ранее в этом разделе некоторые приложения вообще не хотят использовать источник данных. Вместо этого они хотят подключиться непосредственно к водителю. **SLDriverConnect** предоставляет возможность для приложения, чтобы подключиться непосредственно к драйверу без указания источника данных. Концептуально временный источник данных создается во время выполнения.  
  
 Чтобы подключиться непосредственно к драйверу, приложение определяет ключевое слово **DRIVER** в строке соединения вместо ключевого слова **DSN.** Значение ключевого слова **DRIVER** — это описание драйвера, возвращенное **S'LDrivers.** Например, предположим, что драйвер имеет описание Paradox Driver и требует название каталога, содержащего файлы данных. Для подключения к драйверу приложение может использовать одну из следующих строк соединения:  
  
```  
DRIVER={Paradox Driver};Directory=C:\PARADOX;  
DRIVER={Paradox Driver};  
```  
  
 С первой строкой водителю не потребуется дополнительная информация. При всякой строки водителю необходимо будет подсказать название каталога, содержащего файлы данных.
