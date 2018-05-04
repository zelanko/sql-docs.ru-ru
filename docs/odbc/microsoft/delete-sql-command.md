---
title: УДАЛИТЬ - команда SQL | Документы Microsoft
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
- DELETE [ODBC]
ms.assetid: 0d5bd477-626f-4f22-a05a-f531d9f8c5e7
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ea0b09d77b6d2df8ddd525df17526573b6a1e1be
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="delete---sql-command"></a>Удаление - команды SQL
Помечает записи для удаления.  
  
 Драйвер ODBC для Visual FoxPro поддерживает собственный синтаксис языка Visual FoxPro для этой команды. Дополнительные сведения см.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DELETE FROM [DatabaseName!]TableName  
   [WHERE FilterCondition1 [AND | OR FilterCondition2 ...]]  
```  
  
## <a name="arguments"></a>Аргументы  
 ИЗ [ *DatabaseName!*] *TableName*  
 Указывает таблицу, в котором записи, помечаются для удаления.  
  
 *Имя базы данных.* Указывает имя базы данных, содержащую таблицу, если содержащая базу данных не базы данных, указанной в источнике данных. Необходимо включить имя базы данных, содержащую таблицу, если база данных не является база данных, указанная с источником данных. Включить в разделители восклицательный знак (!), имя базы данных и имя таблицы.  
  
 ГДЕ *FilterCondition1*[AND &#124; или *FilterCondition2*...]  
 Указывает, что Visual FoxPro пометить определенные записи для удаления.  
  
 *FilterCondition* указывает критерии, которые должны удовлетворять записи помечена для удаления. Можно включить столько условий фильтрации, сколько требуется, подключив их с AND или оператор OR. Оператор NOT можно использовать и для отмены значения логического выражения, или можно использовать **пустой**() для проверки пустого поля.  
  
## <a name="remarks"></a>Замечания  
 Если НАБОР УДАЛЕН имеет значение ON, помеченные на удаление записи игнорируются все команды, включающие области.  
  
 Удалите - SQL, использующая блокировки записей, когда несколько записей для удаления в таблицах открыт для общего доступа. Это уменьшает конфликты записи в многопользовательских ситуациях, но может привести к снижению производительности. Для максимальной производительности откройте таблицу для монопольного использования.  
  
## <a name="driver-remarks"></a>Драйвер примечания  
 Когда приложение отправляет инструкции ODBC SQL DELETE в источнике данных, драйвер ODBC для Visual FoxPro преобразует команды в команды Visual FoxPro DELETE без трансляции.  
  
## <a name="see-also"></a>См. также  
 [Команда SET DELETED](../../odbc/microsoft/set-deleted-command.md)
