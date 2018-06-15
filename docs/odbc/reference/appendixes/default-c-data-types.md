---
title: Типы данных C по умолчанию | Документы Microsoft
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
- data types [ODBC], pseudo-type identifiers
- pseudo-type identifiers [ODBC], about pseudo-type identifiers
- pseudo-type identifiers [ODBC]
ms.assetid: 229140ae-af8f-4ec8-9ccf-1e92360e0bac
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ec05e58cd651497b07e131d4c3dcfe2e70baa04f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32906419"
---
# <a name="default-c-data-types"></a>Типы данных C по умолчанию
Если приложение указывает SQL_C_DEFAULT в **SQLBindCol**, **SQLGetData**, или **SQLBindParameter**, драйвер предполагает, что тип данных C выходных данных или входного буфера соответствует типу данных SQL столбца или параметра, к которому привязан буфера.  
  
> [!IMPORTANT]  
>  Взаимодействующие приложения, не следует использовать SQL_C_DEFAULT. Вместо этого они должны всегда указывать тип C буфера, который они используют. Это обусловлено драйверов не всегда правильно определить тип C по умолчанию, по следующим причинам.  
  
-   Если тип данных SQL столбца или параметра выполняется повышение уровня СУБД, драйвер не может определить исходный тип данных SQL столбца или параметра. Таким образом он не может определить соответствующий тип данных C по умолчанию.  
  
-   Если драйвер не может определить является ли конкретный столбец или параметр подписан, как ситуация часто возникает, когда это может быть обработано СУБД, драйвер не может определить ли введите соответствующие данные C по умолчанию должны быть подписанные или не подписанные.  
  
     Поскольку SQL_C_DEFAULT предоставляется для удобства программирования, приложение не приводит к потере любые функции, если он задает фактический тип данных C.  
  
 Таблица, показывающая тип данных C по умолчанию для каждого типа данных SQL включается в [преобразование данных из SQL в типы данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)далее в этом приложении.
