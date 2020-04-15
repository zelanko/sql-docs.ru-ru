---
title: ВСТАВКА - Командование СЗЛ Документы Майкрософт
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
ms.openlocfilehash: ce00005fb1aa0ca9732fc5e9cfeacd6faf6ef9e1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300013"
---
# <a name="insert---sql-command"></a>INSERT (команда SQL)
Придаток записи к концу таблицы, содержащей указанные значения поля.  
  
 Visual FoxPro ODBC Driver поддерживает родной визуальный синтаксис языка FoxPro для этой команды. Для получения информации о конкретной для водителей см.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
INSERT INTO dbf_name [(fname1 [, fname2, ...])]  
   VALUES (eExpression1 [, eExpression2, ...])  
```  
  
## <a name="arguments"></a>Аргументы  
 INSERT INTO *dbf_name*  
 Упоняет название таблицы, к которой приложена новая запись. *dbf_name* может включать путь и может быть выражением имени.  
  
 Если таблица, которую вы указываете, не открыта, она открывается исключительно в новой рабочей области и новая запись прилагается к таблице. Новая рабочая область не выбрана; текущая рабочая область остается выбранной.  
  
 Если указанная таблица открыта, INSERT привносит новую запись к таблице. Если таблица открыта в рабочей области, кроме текущей рабочей области, она не выбрана после придатка записи; текущая рабочая область остается выбранной.  
  
 *(fname1*, *fname2*, ...)  
 В новой записи указывается имена полей, в которые вставляются значения.  
  
 VALUES *(eExpression1*, *eExpression2*, ...)  
 Определяет значения поля, вставленные в новую запись. При опущении названий полей необходимо указать значения поля в порядке, определяемом структурой таблицы.  
  
## <a name="remarks"></a>Remarks  
 Новая запись содержит данные, перечисленные в оговорке VALUES.  
  
## <a name="driver-remarks"></a>Замечания водителя  
 Когда приложение отправляет заявление ODBC S'L INSERT в источник данных, водитель Visual FoxPro ODBC преобразует команду в команду Visual FoxProINSERT без перевода.  
  
## <a name="see-also"></a>См. также:  
 [CREATE TABLE - Командование СЗЛ](../../odbc/microsoft/create-table-sql-command.md)   
 [SELECT (команда SQL)](../../odbc/microsoft/select-sql-command.md)
