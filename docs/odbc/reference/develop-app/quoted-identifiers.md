---
title: "Заключенные в кавычки идентификаторы | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], quoted identifiers
- quoted identifiers [ODBC]
ms.assetid: 729ba55f-743b-4a04-8c39-ac0a9914211d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 07a0c8299fc4063e72353025465309c426a3a251
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="quoted-identifiers"></a>Заключенные в кавычки идентификаторы
В инструкции SQL идентификаторы, содержащие специальные символы или соответствия ключевые слова должны быть заключены в *символов кавычек идентификатор*; идентификаторы, заключенные в такие символы называются *заключенные в кавычки идентификаторы*(также известный как *идентификаторов с разделителями* в SQL-92). Например, идентификатор Расчеты с двух сторон окружена ниже **ВЫБЕРИТЕ** инструкции:  
  
```  
SELECT * FROM "Accounts Payable"  
```  
  
 Причина для заключения в кавычки идентификаторов — сделать непригодными для синтаксического анализа инструкции. Например если расчеты не заключено в кавычки в приведенной выше инструкции, средство синтаксического анализа следует предполагается, что две таблицы, учетные записи и с поставщиками и возвращают синтаксическую ошибку, которая не были, разделенные запятой. Знак кавычек идентификатор драйвера и извлекаются с параметром SQL_IDENTIFIER_QUOTE_CHAR в **SQLGetInfo**. Список специальных символов и ключевых слов, извлекаются с помощью параметров SQL_SPECIAL_CHARACTERS и SQL_KEYWORDS в **SQLGetInfo**.  
  
 В целях безопасности взаимодействующие приложения часто Квота все идентификаторы, за исключением тех, для псевдостолбцов, например столбец ROWID в Oracle. **SQLSpecialColumns** возвращает список псевдостолбцов. Кроме того при наличии ограничений конкретного приложения для отображения специальных символов в имени объекта, наилучшим образом подходит для взаимодействия приложений не будет использовать специальные символы в этих местах.

