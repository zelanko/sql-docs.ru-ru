---
title: "Создание и открытие таблиц (драйвера текстового файла) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text file driver [ODBC], creating and opening tables
ms.assetid: e6a07dda-a665-4f5b-a8d6-9ff479700513
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 65288e34df82aa6e37c8be04e3fd2aae7b57e472
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="creating-and-opening-tables-text-file-driver"></a>Создание и открытие таблиц (драйвера текстового файла)
При использовании драйвера текстового новая таблица создается с использованием формат, указанный в Odbcinst.ini. Если не указан, они создаются в формате CSVDELIMITED. По умолчанию ЦЕЛОЧИСЛЕННЫХ столбцах по умолчанию 11 символов и FLOAT столбцов по умолчанию 22 символов. Столбцы даты используется формат гггг-мм-дд. CHAR и LONGCHAR столбцы имеют ширину, указанный в инструкции CREATE.
