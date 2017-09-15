---
title: "Создание и открытие таблиц (драйвера текстового файла) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text file driver [ODBC], creating and opening tables
ms.assetid: e6a07dda-a665-4f5b-a8d6-9ff479700513
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 41190a0a3eabda2f73c8f6046a64b7b7db929fa1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="creating-and-opening-tables-text-file-driver"></a>Создание и открытие таблиц (драйвера текстового файла)
При использовании драйвера текстового новая таблица создается с использованием формат, указанный в Odbcinst.ini. Если не указан, они создаются в формате CSVDELIMITED. По умолчанию ЦЕЛОЧИСЛЕННЫХ столбцах по умолчанию 11 символов и FLOAT столбцов по умолчанию 22 символов. Столбцы даты используется формат гггг-мм-дд. CHAR и LONGCHAR столбцы имеют ширину, указанный в инструкции CREATE.
