---
title: Команда SQL UPDATE - | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- update [ODBC]
ms.assetid: ff1e0331-c060-4304-b280-039725b45f63
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3fbd5ec98791d782fe7ad1fdb1e1884b646dcf9f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47818312"
---
# <a name="update---sql-command"></a>UPDATE (команда SQL)
Обновляет записи в таблицу с новыми значениями.  
  
 Драйвер ODBC для Visual FoxPro поддерживает собственный синтаксис языка Visual FoxPro для этой команды. Сведения, см. в разделе **"Примечания" драйвер**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
UPDATE [DatabaseName1!]TableName1  
SET Column_Name1 = eExpression1  
   [, Column_Name2 = eExpression2 ...]  
   WHERE FilterCondition1 [AND | OR FilterCondition2 ...]  
```  
  
## <a name="arguments"></a>Аргументы  
 Обновление [ *DatabaseName1!*] *TableName1*  
 Указывает таблицу, в котором записи обновляются новыми значениями.  
  
 *DatabaseName1!* Указывает имя базы данных, отличных от базы данных, указанной в источнике данных, содержащей таблицу. Необходимо включить имя базы данных, содержащей таблицу, если база данных не является текущей. Включить в разделители восклицательный знак (!), после имени базы данных и перед именем таблицы.  
  
 ЗАДАЙТЕ *Column_Name1*= *eExpression1*[, *Column_Name2*= *eExpression2*  
 Указывает столбцы, которые обновляются и их новые значения. Если опустить предложение WHERE, каждая строка в столбце обновляется с одинаковым значением.  
  
 ГДЕ *FilterCondition1*[AND &#124; или *FilterCondition2*...]  
 Задает записей, которые обновляются новыми значениями.  
  
 *FilterCondition* указывает критерии, которым должны соответствовать записи в него новые значения. Можно включить столько условий фильтрации, сколько вам нравится, подключая их к AND или оператор OR. Оператор NOT можно использовать и для отмены значения логического выражения или воспользоваться **пустой**() на наличие пустого поля.  
  
## <a name="remarks"></a>Примечания  
 ОБНОВЛЕНИЕ – SQL можно обновить только записи, в одной таблице.  
  
 В отличие от ЗАМЕНЫ обновления - SQL используется Блокировка записей, когда обновление нескольких записей в таблицах открыт для общего доступа. Это уменьшает конфликты записи в многопользовательских ситуациях, но может снизить производительность. Для достижения максимальной производительности, откройте таблицу эксклюзивным используйте или **FLOCK**() для блокировки таблицы.  
  
## <a name="driver-remarks"></a>Драйвер "Примечания"  
 Когда приложение отправляет инструкции ODBC SQL обновления к источнику данных, драйвер ODBC для Visual FoxPro преобразует команды в команду Visual FoxProUPDATE без перевода.  
  
## <a name="see-also"></a>См. также  
 [Команда SQL - DELETE](../../odbc/microsoft/delete-sql-command.md)   
 [INSERT (команда SQL)](../../odbc/microsoft/insert-sql-command.md)
