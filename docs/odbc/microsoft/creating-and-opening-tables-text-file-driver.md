---
title: Создание и открытие таблиц (драйвера текстового файла) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], creating and opening tables
ms.assetid: e6a07dda-a665-4f5b-a8d6-9ff479700513
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b836fa5144ffb59a155eed150f3372385d808343
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32899629"
---
# <a name="creating-and-opening-tables-text-file-driver"></a>Создание и открытие таблиц (драйвера текстового файла)
При использовании драйвера текстового новая таблица создается с использованием формат, указанный в Odbcinst.ini. Если не указан, они создаются в формате CSVDELIMITED. По умолчанию ЦЕЛОЧИСЛЕННЫХ столбцах по умолчанию 11 символов и FLOAT столбцов по умолчанию 22 символов. Столбцы даты используется формат гггг-мм-дд. CHAR и LONGCHAR столбцы имеют ширину, указанный в инструкции CREATE.
