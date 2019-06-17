---
title: Команда SET NULL | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- set nullSET NULL
ms.assetid: 410c5a6e-e957-4ecc-9e2d-e591cbc0bc4f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b6f0e23abd31661210282967fa35080376eaaaf3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63159301"
---
# <a name="set-null-command"></a>Команда SET NULL
Определяет, как значения null поддерживаются инструкции ALTER TABLE - SQL, CREATE TABLE - SQL и INSERT - команд SQL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET NULL ON | OFF  
```  
  
## <a name="arguments"></a>Аргументы  
 ON  
 (По умолчанию для драйвера по умолчанию для Visual FoxPro имеет значение OFF.) Указывает, что все столбцы таблицы, созданные с помощью инструкции ALTER TABLE и CREATE TABLE будет разрешать значения null. Поддержка значение null для столбцов в таблице можно переопределить, включая предложение NOT NULL в определениях столбцов.  
  
 Также указывает, что INSERT - SQL будет вставлять значения null в любые столбцы, не включенные в инструкции INSERT - предложение значение SQL. INSERT - SQL будет вставлять значения null только в столбцы, допускающие значения null.  
  
 OFF  
 Указывает, что все столбцы таблицы, созданные с помощью инструкции ALTER TABLE и CREATE TABLE не разрешает значения null. Вы можете назначить поддержка значение null для столбцов в инструкции ALTER TABLE и CREATE TABLE, включив предложение NULL в определениях столбцов.  
  
 Также указывает, что INSERT - SQL будет вставлять пустые значения в любой столбцов, отсутствующих в инструкции INSERT - предложение значение SQL.  
  
## <a name="remarks"></a>Примечания  
 Поддерживает SET NULL как значение null значения влияет на инструкции ALTER TABLE, CREATE TABLE и INSERT - SQL. Другие команды не затрагиваются, SET NULL.  
  
## <a name="see-also"></a>См. также  
 [ALTER TABLE - команда SQL](../../odbc/microsoft/alter-table-sql-command.md)   
 [Создание таблицы - команда SQL](../../odbc/microsoft/create-table-sql-command.md)   
 [INSERT (команда SQL)](../../odbc/microsoft/insert-sql-command.md)
