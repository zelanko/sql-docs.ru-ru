---
title: Типы данных C по умолчанию | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b9e0a9b8e85967ce46344e824c03e74fe3552e7c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68130005"
---
# <a name="default-c-data-types"></a>Типы данных C по умолчанию
Если приложение указывает SQL_C_DEFAULT в **SQLBindCol**, **SQLGetData**или **SQLBindParameter**, драйвер предполагает, что тип данных C выходного или входного буфера соответствует типу данных SQL столбца или параметра, к которому привязан буфер.  
  
> [!IMPORTANT]  
>  В приложениях, поддерживающих взаимодействие, не следует использовать SQL_C_DEFAULT. Вместо этого они всегда должны указывать тип C буфера, который они используют. Это обусловлено тем, что драйверы не всегда могут правильно определить тип C по умолчанию по следующим причинам.  
  
-   Если СУБД додвигает тип данных SQL для столбца или параметра, драйвер не может определить исходный тип данных SQL для столбца или параметра. Поэтому он не может определить соответствующий тип данных C по умолчанию.  
  
-   Если драйвер не может определить, подписан ли определенный столбец или параметр, как правило, если он обрабатывается СУБД, драйвер не может определить, должен ли соответствующий тип данных C по умолчанию быть знаком или без знака.  
  
     Поскольку SQL_C_DEFAULT предоставляется только в качестве удобства программирования, приложение не теряет никаких функциональных возможностей, если оно указывает фактический тип данных C.  
  
 Таблица, показывающая тип данных C по умолчанию для каждого типа данных SQL, включается в [Преобразование данных из SQL в типы данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)в дальнейшем в этом приложении.
