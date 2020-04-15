---
title: Типы драйверов Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: de6d8e1473f127d28c69969e0fc298afd69d3023
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304875"
---
# <a name="types-of-drivers"></a>Типы драйверов
Драйверы ODBC можно классифицировать следующим образом:  
  
-   **32-битный ODBC 2.**  
     ** _x_ Драйвер** A 32-битный драйвер, который:  
  
    -   Экспортирует только функции ODBC *2.x.*  
  
    -   Экспонаты ODBC *2.x* поведение для поведенческих изменений.  
  
-   **ISO и открытый групповой драйвер** 32-разрядный драйвер, который:  
  
    -   Экспортируйте все функции, которые задокументированы в документах Open Group или ISO CLI. Это будет включать в себя некоторые функции, которые являются deprecated в ODBC.  
  
    -   Экспонаты ODBC 3.0 поведение для поведенческих изменений.  
  
    -   Не обязательно проходить через ODBC 3.0 Менеджер драйвера.  
  
-   **Водитель ODBC 3.0** 32-разрядный драйвер, который:  
  
    -   Экспорт только функции, которые находятся в ODBC 3.0 минус амортизированные функции.  
  
    -   Способен демонстрировать поведение ODBC *2.x* или поведение ODBC 3.0 в отношении поведенческих изменений, основанных на атрибуте SQL_ATTR_APP_ODBC_VERSION среды.  
  
-   **ODBC 3.5 (или позже) водитель ANSI** 32-разрядный драйвер, который:  
  
    -   Экспорт только функции, которые находятся в ODBC 3.5 минус амортизированные функции.  
  
    -   Способен проявлять поведение ODBC *2.x* или поведение ODBC 3.0, или поведение ODBC 3.5 в отношении поведенческих изменений, основанных на атрибуте SQL_ATTR_APP_ODBC_VERSION среды.  
  
-   **ODBC 3.5 (или позже) Драйвер Unicode** 32-разрядный драйвер, который:  
  
    -   Поддерживает все функции драйвера ODBC 3.5 ANSI.  
  
    -   Экспортирует версии Unicode всех AIS строкod ODBC.  
  
    -   Можно хранить и обрабатывать данные Unicode на источнике данных.  
  
> [!NOTE]  
>  16-битные драйверы ODBC не будут работать напрямую с менеджером драйверов ODBC *3.x.* Тем не менее, это возможно для 16-битных водителей для работы с 2.0 ODBC Driver Manager, который впоследствии thunks до *3.x* Driver Manager.
