---
description: INSERT (команда SQL)
title: Команда INSERT-SQL | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 92c4b2068149164716d52fd3693e56164ab788ab
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449506"
---
# <a name="insert---sql-command"></a>INSERT (команда SQL)
Добавляет запись в конец таблицы, содержащей указанные значения полей.  
  
 Драйвер ODBC для Visual FoxPro поддерживает для этой команды собственный синтаксис языка Visual FoxPro. Сведения, относящиеся к драйверу, см. в разделе Примечания.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
INSERT INTO dbf_name [(fname1 [, fname2, ...])]  
   VALUES (eExpression1 [, eExpression2, ...])  
```  
  
## <a name="arguments"></a>Аргументы  
 ВСТАВИТЬ в *dbf_name*  
 Указывает имя таблицы, к которой добавляется новая запись. *dbf_name* может содержать путь и может быть выражением имени.  
  
 Если указанная таблица не открыта, она открывается исключительно в новой рабочей области, а новая запись добавляется в таблицу. Новая Рабочая область не выбрана. Текущая рабочая область остается выбранной.  
  
 Если указанная таблица открыта, инструкция INSERT добавляет новую запись в таблицу. Если таблица открыта в рабочей области, отличной от текущей рабочей области, она не будет выбрана после добавления записи. Текущая рабочая область остается выбранной.  
  
 [( *fname1*[, *fname2*[,...]])]  
 Указывает в новой записи имена полей, в которые вставляются значения.  
  
 ЗНАЧЕНИЯ ( *eExpression1*[, *eExpression2*[,...]])  
 Задает значения полей, вставляемых в новую запись. Если имена полей не указаны, необходимо указать значения полей в порядке, определенном в структуре таблицы.  
  
## <a name="remarks"></a>Remarks  
 Новая запись содержит данные, перечисленные в предложении VALUES.  
  
## <a name="driver-remarks"></a>Примечания к драйверам  
 Когда приложение отправляет инструкцию SQL ODBC INSERT в источник данных, драйвер ODBC для Visual FoxPro преобразует команду в команду Visual Фокспроинсерт без перевода.  
  
## <a name="see-also"></a>См. также:  
 [Команда CREATE TABLE-SQL](../../odbc/microsoft/create-table-sql-command.md)   
 [SELECT (команда SQL)](../../odbc/microsoft/select-sql-command.md)
