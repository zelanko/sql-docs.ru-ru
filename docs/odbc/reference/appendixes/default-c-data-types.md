---
title: Типы данных по умолчанию C Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], pseudo-type identifiers
- pseudo-type identifiers [ODBC], about pseudo-type identifiers
- pseudo-type identifiers [ODBC]
ms.assetid: 229140ae-af8f-4ec8-9ccf-1e92360e0bac
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fdb787580e1c79df805f468416ab8993a1d32a26
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307055"
---
# <a name="default-c-data-types"></a>Типы данных C по умолчанию
Если приложение указывает SQL_C_DEFAULT в **S'LBindCol,** **S'LGetData**, или **S'LBindParameter**, драйвер предполагает, что тип данных C вывода или ввода буфера соответствует типу данных s'L столбца или параметра, к которому буфер привязан.  
  
> [!IMPORTANT]  
>  Совместимые приложения не должны использовать SQL_C_DEFAULT. Вместо этого они всегда должны указывать тип C буфера, который они используют. Это связано с тем, что драйверы не всегда могут правильно определить тип C по умолчанию по следующим причинам:  
  
-   Если DBMS продвигает тип данных столбца или параметра, драйвер не может определить исходный тип данных столбца или параметра. Таким образом, он не может определить соответствующий тип данных C по умолчанию.  
  
-   Если драйвер не может определить, подписан ли определенный столбец или параметр, как это часто бывает, когда это обрабатывается DBMS, драйвер не может определить, должен ли быть подписан или не подписан соответствующий тип данных по умолчанию C.  
  
     Поскольку SQL_C_DEFAULT предоставляется только в качестве удобства программирования, приложение не теряет никакой функциональности, когда он определяет фактический тип данных C.  
  
 Таблица, показывающая тип данных по умолчанию C для каждого типа данных S'L, включена в [преобразование данных от S'L к типам данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md), позже в этом приложении.
