---
title: По умолчанию типы данных C | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 9c4147b1bfa5ffb1e379c3aa8be2c9ea2a9d2775
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47854112"
---
# <a name="default-c-data-types"></a>Типы данных C по умолчанию
Если приложение указывает SQL_C_DEFAULT в **SQLBindCol**, **SQLGetData**, или **SQLBindParameter**, драйвер предполагает, что тип данных C выходных данных или входного буфера соответствующий тип данных SQL столбца или параметра, к которому привязан буфера.  
  
> [!IMPORTANT]  
>  Взаимодействующие приложения, не следует использовать SQL_C_DEFAULT. Вместо этого они всегда должны указывать тип C буфера, который они используют. Это потому, что драйверы не всегда правильно определить тип C по умолчанию, по следующим причинам:  
  
-   Если СУБД обеспечивает тип данных SQL столбца или параметра, драйвер не может определить исходный тип данных SQL столбца или параметра. Таким образом он не может определить соответствующий тип данных C по умолчанию.  
  
-   Если драйвер не может определить ли подписан определенного столбца или параметра, как это обычно бывает при это обрабатывается СУБД, драйвер не может определить ли введите соответствующие данные C по умолчанию должны быть подписанные или не подписанные.  
  
     Потому что SQL_C_DEFAULT предоставляется только для удобства программирования, приложение не потеряете все функции, когда он задает фактический тип данных C.  
  
 Таблица, показывающая тип данных C по умолчанию для каждого типа данных SQL включен в [преобразование данных из SQL в типы данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)далее в этом приложении.
