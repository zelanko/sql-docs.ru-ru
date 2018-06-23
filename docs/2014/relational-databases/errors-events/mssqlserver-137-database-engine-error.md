---
title: MSSQLSERVER_137 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 137 (Database Engine error)
ms.assetid: 47fb4212-2165-4fec-bc41-6d548465d7be
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 443418b5b01af527dd93b31625ca1fee9284836c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100008"
---
# <a name="mssqlserver137"></a>MSSQLSERVER_137
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|137|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|P_SCALAR_VAR_NOTFOUND|  
|Текст сообщения|Должна быть объявлена скалярная переменная «%.*ls».|  
  
## <a name="explanation"></a>Объяснение  
 Эта ошибка происходит, если переменная используется в скрипте SQL без предварительного объявления этой переменной. Следующий пример возвращает ошибку 137 для обеих инструкций (SET и SELECT), так как переменная **@mycol** не объявлена.  
  
 SET @mycol = 'ContactName';  
  
 SELECT @mycol;  
  
 Одной из трудноуловимых причин этой ошибки является использование переменной, которая объявлена вне инструкции EXECUTE. Например, переменная **@mycol**, указанная в инструкции SELECT, является локальной по отношению к инструкции SELECT и поэтому находится вне инструкции EXECUTE.  
  
 USE AdventureWorks2012;  
  
 GO  
  
 DECLARE @mycol nvarchar(20);  
  
 SET @mycol = 'Name';  
  
 EXECUTE ('SELECT @mycol FROM Production.Product;');  
  
## <a name="user-action"></a>Действие пользователя  
 Убедитесь в том, что все переменные, используемые в скрипте SQL, объявляются перед их применением в любом месте скрипта.  
  
 Перепишите скрипт так, чтобы в инструкции EXECUTE не применялись ссылки на переменные, которые объявлены вне этой инструкции. Например:  
  
 USE AdventureWorks2012;  
  
 GO  
  
 DECLARE @mycol nvarchar(20) ;  
  
 SET @mycol = 'Name';  
  
 EXECUTE ('SELECT ' + @mycol + ' FROM Production.Product';) ;  
  
## <a name="see-also"></a>См. также  
 [EXECUTE (Transact-SQL)](/sql/t-sql/language-elements/execute-transact-sql)   
 [Инструкции SET (Transact-SQL)](/sql/t-sql/statements/set-statements-transact-sql)   
 [DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql)  
  
  
