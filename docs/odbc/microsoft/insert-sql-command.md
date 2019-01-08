---
title: INSERT - команда SQL | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- INSERT [ODBC]
ms.assetid: 9b648198-349f-46f6-b869-13d129945971
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 44e773248cd2d61e211f6de98d5a0f81acc78bd1
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2018
ms.locfileid: "53215550"
---
# <a name="insert---sql-command"></a>INSERT (команда SQL)
Добавляет запись в конец таблицы, содержащий указанные значения полей.  
  
 Драйвер ODBC для Visual FoxPro поддерживает собственный синтаксис языка Visual FoxPro для этой команды. Сведения см. в разделе "Примечания".  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
INSERT INTO dbf_name [(fname1 [, fname2, ...])]  
   VALUES (eExpression1 [, eExpression2, ...])  
```  
  
## <a name="arguments"></a>Аргументы  
 INSERT INTO *dbf_name*  
 Указывает имя таблицы, к которому добавляется новая запись. *dbf_name* можно включить путь и может быть выражение с именем.  
  
 Если таблицы не открыт, он открывается исключительно в новой рабочей области и в таблицу добавляется новая запись. Не выбрана новой рабочей области; текущей рабочей области остается выбранным.  
  
 Если открыт указанную таблицу, инструкция INSERT добавляет новую запись в таблицу. Если таблица является открытым в рабочей области, отличной от текущего рабочая область, он не выбран, после добавления записи; текущей рабочей области остается выбранным.  
  
 [( *fname1*[, *fname2*[,...]])]  
 Задает имена полей в новой записи в которой вставляются значения.  
  
 ЗНАЧЕНИЯ ( *eExpression1*[, *eExpression2*[,...]])  
 Указывает поле значениях, вставляемых в новой записи. Если опустить имена полей, необходимо указать значения полей в порядке, определяемом структуру таблицы.  
  
## <a name="remarks"></a>Примечания  
 Новая запись содержит данные, перечисленные в предложении VALUES.  
  
## <a name="driver-remarks"></a>Драйвер "Примечания"  
 Когда приложение отправляет инструкцию ODBC SQL INSERT с источником данных, драйвер ODBC для Visual FoxPro преобразует команды в команду Visual FoxProINSERT без перевода.  
  
## <a name="see-also"></a>См. также  
 [Создание таблицы - команда SQL](../../odbc/microsoft/create-table-sql-command.md)   
 [SELECT (команда SQL)](../../odbc/microsoft/select-sql-command.md)
