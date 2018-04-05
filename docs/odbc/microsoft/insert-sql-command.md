---
title: Вставка - команды SQL | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- INSERT [ODBC]
ms.assetid: 9b648198-349f-46f6-b869-13d129945971
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c78b10cece63014d10d131446d9f43b154e91d7a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="insert---sql-command"></a>Вставка - команды SQL
Добавляет запись в конец таблицы, содержащий указанные значения полей.  
  
 Драйвер ODBC для Visual FoxPro поддерживает собственный синтаксис языка Visual FoxPro для этой команды. Дополнительные сведения см.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
INSERT INTO dbf_name [(fname1 [, fname2, ...])]  
   VALUES (eExpression1 [, eExpression2, ...])  
```  
  
## <a name="arguments"></a>Аргументы  
 INSERT INTO *dbf_name*  
 Указывает имя таблицы, к которому добавляется новая запись. *dbf_name* может содержать путь, и может быть выражение с именем.  
  
 Если таблицы, указываемые еще не открыт, он открыт исключительно в новой рабочей области и новая запись добавляется к таблице. Не выбрана новой рабочей области; текущей рабочей области остается установленным.  
  
 Если таблицы, указываемые открыт, инструкция INSERT добавляет новую запись в таблицу. Если таблица является открытым в рабочей области, отличного от текущей рабочей области, он не выбран, после добавления записи; текущей рабочей области остается установленным.  
  
 [( *fname1*[, *fname2*[,...]])]  
 Указывает в новой записи имена полей, в который вставляются значения.  
  
 ЗНАЧЕНИЯ ( *eExpression1*[, *eExpression2*[,...]])  
 Указывает поле, вставляемые в новой записи. Если опустить имена полей, необходимо указать значения полей в том порядке, определенные структурой таблицы.  
  
## <a name="remarks"></a>Remarks  
 Новая запись содержит данные, перечисленные в предложении VALUES.  
  
## <a name="driver-remarks"></a>Драйвер примечания  
 Когда приложение отправляет инструкции ODBC SQL вставки в источник данных, драйвер ODBC для Visual FoxPro преобразует команды в команду Visual FoxProINSERT без трансляции.  
  
## <a name="see-also"></a>См. также:  
 [Создание таблицы - команда SQL](../../odbc/microsoft/create-table-sql-command.md)   
 [SELECT (команда SQL)](../../odbc/microsoft/select-sql-command.md)
