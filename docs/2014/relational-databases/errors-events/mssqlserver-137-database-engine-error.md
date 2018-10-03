---
title: MSSQLSERVER_137 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 137 (Database Engine error)
ms.assetid: 47fb4212-2165-4fec-bc41-6d548465d7be
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2eaaadc4e1cc1f2f360fe3d45e2dea4c082b7b76
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48214134"
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
  
 Перепишите скрипт так, чтобы в инструкции EXECUTE не применялись ссылки на переменные, которые объявлены вне этой инструкции. Пример:  
  
 USE AdventureWorks2012;  
  
 GO  
  
 DECLARE @mycol nvarchar(20) ;  
  
 SET @mycol = 'Name';  
  
 EXECUTE ('SELECT ' + @mycol + ' FROM Production.Product';) ;  
  
## <a name="see-also"></a>См. также  
 [EXECUTE (Transact-SQL)](/sql/t-sql/language-elements/execute-transact-sql)   
 [Инструкции SET (Transact-SQL)](/sql/t-sql/statements/set-statements-transact-sql)   
 [DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql)  
  
  
