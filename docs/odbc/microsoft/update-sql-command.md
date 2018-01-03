---
title: "Команда SQL UPDATE - | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: update [ODBC]
ms.assetid: ff1e0331-c060-4304-b280-039725b45f63
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6fb2e4d3e3010eaba53b36de383c3365d82db289
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="update---sql-command"></a>Обновление - команд SQL
Обновляет записи в таблицу с новыми значениями.  
  
 Драйвер ODBC для Visual FoxPro поддерживает собственный синтаксис языка Visual FoxPro для этой команды. Относящиеся к драйверу сведения см. в разделе **примечания драйвер**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
UPDATE [DatabaseName1!]TableName1  
SET Column_Name1 = eExpression1  
   [, Column_Name2 = eExpression2 ...]  
   WHERE FilterCondition1 [AND | OR FilterCondition2 ...]  
```  
  
## <a name="arguments"></a>Аргументы  
 Обновление [ *DatabaseName1!*] *TableName1*  
 Указывает таблицу, в котором записи обновляются с новыми значениями.  
  
 *DatabaseName1!* Указывает имя базы данных, кроме базы данных, указанной в источнике данных, содержащей таблицу. Необходимо включить имя базы данных, содержащую таблицу, если база данных не является текущей. Включить в разделители восклицательный знак (!), имя базы данных и имя таблицы.  
  
 ЗАДАТЬ *Column_Name1*= *eExpression1*[, *Column_Name2*= *eExpression2*  
 Указывает столбцы, которые обновляются и новые значения. Если не указан в предложении WHERE, каждая строка в столбце обновляется с тем же значением.  
  
 ГДЕ *FilterCondition1*[и &#124; ИЛИ *FilterCondition2*...]  
 Указывает записей, которые обновляются новыми значениями.  
  
 *FilterCondition* указывает критерии, которым должны соответствовать записи для обновления с новыми значениями. Можно включить столько условий фильтрации, сколько вам нравится, подключив их с AND или оператор OR. Оператор NOT можно использовать и для отмены значения логического выражения, или можно использовать **пустой**() для проверки пустого поля.  
  
## <a name="remarks"></a>Remarks  
 ОБНОВЛЕНИЕ - SQL можно обновить только записи в одной таблице.  
  
 В отличие от ЗАМЕНЫ обновление - SQL использует блокировки записей, когда обновление нескольких записей в таблицах открыт для общего доступа. Это уменьшает конфликты записи в многопользовательских ситуациях, но может привести к снижению производительности. Для максимальной производительности, откройте таблицу эксклюзивным используйте или **FLOCK**() для блокировки таблицы.  
  
## <a name="driver-remarks"></a>Драйвер примечания  
 Когда приложение отправляет инструкции ODBC SQL обновления в источник данных, драйвер ODBC для Visual FoxPro преобразует команды в команду Visual FoxProUPDATE без преобразования.  
  
## <a name="see-also"></a>См. также:  
 [Удаление - команды SQL](../../odbc/microsoft/delete-sql-command.md)   
 [INSERT (команда SQL)](../../odbc/microsoft/insert-sql-command.md)
