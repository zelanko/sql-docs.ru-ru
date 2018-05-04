---
title: Заключенные в кавычки идентификаторы | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], quoted identifiers
- quoted identifiers [ODBC]
ms.assetid: 729ba55f-743b-4a04-8c39-ac0a9914211d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3af402bd63bf1892b1906da34114d5515e6dfa30
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="quoted-identifiers"></a>Заключенные в кавычки идентификаторы
В инструкции SQL идентификаторы, содержащие специальные символы или соответствия ключевые слова должны быть заключены в *символов кавычек идентификатор*; идентификаторы, заключенные в такие символы называются *заключенные в кавычки идентификаторы*(также известный как *идентификаторов с разделителями* в SQL-92). Например, идентификатор Расчеты с двух сторон окружена ниже **ВЫБЕРИТЕ** инструкции:  
  
```  
SELECT * FROM "Accounts Payable"  
```  
  
 Причина для заключения в кавычки идентификаторов — сделать непригодными для синтаксического анализа инструкции. Например если расчеты не заключено в кавычки в приведенной выше инструкции, средство синтаксического анализа следует предполагается, что две таблицы, учетные записи и с поставщиками и возвращают синтаксическую ошибку, которая не были, разделенные запятой. Знак кавычек идентификатор драйвера и извлекаются с параметром SQL_IDENTIFIER_QUOTE_CHAR в **SQLGetInfo**. Список специальных символов и ключевых слов, извлекаются с помощью параметров SQL_SPECIAL_CHARACTERS и SQL_KEYWORDS в **SQLGetInfo**.  
  
 В целях безопасности взаимодействующие приложения часто Квота все идентификаторы, за исключением тех, для псевдостолбцов, например столбец ROWID в Oracle. **SQLSpecialColumns** возвращает список псевдостолбцов. Кроме того при наличии ограничений конкретного приложения для отображения специальных символов в имени объекта, наилучшим образом подходит для взаимодействия приложений не будет использовать специальные символы в этих местах.
