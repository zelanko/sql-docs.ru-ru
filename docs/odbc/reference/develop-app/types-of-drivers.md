---
title: Типы драйверов | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver compatibility issues [ODBC]
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], application and driver compatibility
- compatibility [ODBC], application and driver compatibility
ms.assetid: 864c53c1-b68a-48b6-b6bc-5ecb520bb9dc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 445fe3a0b87e6ad8e35dbc585981d874f8e357bf
ms.sourcegitcommit: bfa10c54e871700de285d7f819095d51ef70d997
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2019
ms.locfileid: "54256959"
---
# <a name="types-of-drivers"></a>Типы драйверов
Драйверы ODBC можно классифицировать следующим образом:  
  
-   **32-разрядный ODBC 2.**  
     **_x_ драйвер** 32-разрядный драйвер:  
  
    -   Экспортирует только ODBC 2 *.x* функции.  
  
    -   Демонстрирует ODBC 2. *x* поведение для изменения поведения.  
  
-   **ISO и откройте группу-совместимые драйвера** 32-разрядный драйвер:  
  
    -   Экспортирует все функции, которые описаны в документах Open Group или интерфейса командной строки ISO. Это позволит включить некоторые из функций, которые являются устаревшими в ODBC.  
  
    -   Поведение ODBC 3.0 для изменения поведения.  
  
    -   Не обязательно проходят через диспетчер драйверов ODBC 3.0.  
  
-   **Драйвер ODBC 3.0** 32-разрядный драйвер:  
  
    -   Экспортирует только функции, которые находятся в ODBC 3.0 минус устаревшей функции.  
  
    -   Возможна с ODBC 2.*x* поведение или поведение ODBC 3.0 по отношению к изменениям, в зависимости от атрибута SQL_ATTR_APP_ODBC_VERSION среды.  
  
-   **Драйвер ODBC 3.5 (или более поздней версии) ANSI** 32-разрядный драйвер:  
  
    -   Экспортирует только функции, которые находятся в ODBC 3.5 минус устаревшей функции.  
  
    -   Возможна с ODBC 2. *x* поведение или поведение ODBC 3.0 или ODBC 3.5 поведение по отношению к изменениям, на основе SQL_ATTR_APP_ODBC_VERSION среды атрибута.  
  
-   **Драйвер ODBC 3.5 (или более поздней версии) Юникода** 32-разрядный драйвер:  
  
    -   Поддерживает все функции драйвера ODBC 3.5 ANSI.  
  
    -   Экспортирует все строки ODBC API-интерфейсов версии Юникода.  
  
    -   Можно хранить и обрабатывать данные в Юникоде в источнике данных.  
  
> [!NOTE]  
>  16-разрядные драйверы ODBC не будет работать непосредственно с ODBC 3. *x* диспетчера драйверов. Тем не менее это возможно для 16-разрядные драйверы для работы с 2.0 Диспетчер драйверов ODBC, который впоследствии преобразователи до 3. *x* диспетчера драйверов.
