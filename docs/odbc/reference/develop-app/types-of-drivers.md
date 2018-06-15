---
title: Типы драйверов | Документы Microsoft
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
- driver compatibility issues [ODBC]
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], application and driver compatibility
- compatibility [ODBC], application and driver compatibility
ms.assetid: 864c53c1-b68a-48b6-b6bc-5ecb520bb9dc
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e75e5827becd5457d0e310ca5ec0cc2a13259be5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32914689"
---
# <a name="types-of-drivers"></a>Типы драйверов
Драйверы ODBC можно классифицировать следующим образом:  
  
-   **32-разрядное ODBC 2.**  
     ***x* драйвер** 32-разрядный драйвер:  
  
    -   Экспортирует только ODBC 2 *.x* функции.  
  
    -   Демонстрирует ODBC 2. *x* поведение для изменения поведения.  
  
-   **ISO и откройте соответствующие группы драйверов** 32-разрядный драйвер:  
  
    -   Экспортирует все функции, которые описаны в документах Open Group или ISO CLI. Сюда входят некоторые функции, которые являются устаревшими в ODBC.  
  
    -   Поведение ODBC 3.0 для изменения поведения.  
  
    -   Не обязательно проходят через диспетчер драйверов ODBC 3.0.  
  
-   **Драйвер ODBC 3.0** 32-разрядный драйвер:  
  
    -   Экспортирует только функции, которые находятся в ODBC 3.0 минус устаревания функций.  
  
    -   Способен обнаружены ODBC 2. *x* поведение или поведение ODBC 3.0 по отношению к изменениям, в зависимости от атрибута SQL_ATTR_APP_ODBC_VERSION среды.  
  
-   **Драйвер ODBC 3.5 (или более поздней версии) ANSI** 32-разрядный драйвер:  
  
    -   Экспортирует только функции, которые находятся в ODBC 3.5 минус устаревания функций.  
  
    -   Способен обнаружены ODBC 2. *x* поведение или поведение ODBC 3.0 или ODBC 3.5 поведение по отношению к изменения поведения на основе SQL_ATTR_APP_ODBC_VERSION среды атрибута.  
  
-   **Драйвер ODBC 3.5 (или более поздней версии) Юникода** 32-разрядный драйвер:  
  
    -   Поддерживает все возможности драйвера ODBC 3.5 ANSI.  
  
    -   Экспортирует все строки ODBC API-интерфейсы версии Юникода.  
  
    -   Можно хранить и обрабатывать данные в Юникоде в источнике данных.  
  
> [!NOTE]  
>  16-разрядные драйверы ODBC, не будут работать непосредственно с ODBC 3. *x* диспетчера драйверов. Тем не менее возможно, что 16-разрядные драйверы для работы с 2.0 диспетчера драйвера ODBC, который впоследствии преобразователи до 3. *x* диспетчера драйверов.
