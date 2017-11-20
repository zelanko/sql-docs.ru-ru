---
title: "Значение NULL команды SET | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- set nullSET NULL
ms.assetid: 410c5a6e-e957-4ecc-9e2d-e591cbc0bc4f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 14cade223de7014dd4a0c27295d3ff742d18af17
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="set-null-command"></a>Значение NULL команды SET
Определяет, как значения null поддерживаются при помощи инструкции ALTER TABLE - SQL, CREATE TABLE - SQL и вставки - команд SQL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET NULL ON | OFF  
```  
  
## <a name="arguments"></a>Аргументы  
 ON  
 (По умолчанию для драйвера, значение по умолчанию для Visual FoxPro — OFF). Указывает, что все столбцы в таблице, созданных с помощью инструкции ALTER TABLE и CREATE TABLE будет разрешать значения null. Поддержка значение null для столбцов в таблице можно переопределить, включая предложение NOT NULL в определениях столбцов.  
  
 Также указывает, вставка - SQL будет вставлять значения null в любые столбцы, не включенные в инструкции INSERT - предложения значение SQL. INSERT - SQL будет вставлять значения null только на столбцы, допускающие значения null.  
  
 OFF  
 Указывает, что все столбцы в таблице, созданных с помощью инструкции ALTER TABLE и CREATE TABLE не разрешает значения null. Можно назначить поддержка значение null для столбцов в инструкции ALTER TABLE и CREATE TABLE, включая предложение NULL в определениях столбцов.  
  
 Также указывает, вставка - SQL будет вставлять пустые значения в любые столбцы, не включенные в инструкции INSERT - предложения значение SQL.  
  
## <a name="remarks"></a>Замечания  
 SET NULL затрагивает только влияние значений null поддерживаются инструкции ALTER TABLE, CREATE TABLE и INSERT - SQL. Другие команды не затрагивают SET NULL.  
  
## <a name="see-also"></a>См. также:  
 [ALTER TABLE - команда SQL](../../odbc/microsoft/alter-table-sql-command.md)   
 [Создание таблицы - команда SQL](../../odbc/microsoft/create-table-sql-command.md)   
 [Вставка - команды SQL](../../odbc/microsoft/insert-sql-command.md)

