---
title: MSSQLSERVER_137 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 137 (Database Engine error)
ms.assetid: 47fb4212-2165-4fec-bc41-6d548465d7be
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4e780d6afaddc5ac3af0e87e6b629fb39c987879
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305039"
---
# <a name="mssqlserver_137"></a>MSSQLSERVER_137
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
Эта ошибка происходит, если переменная используется в скрипте SQL без предварительного объявления этой переменной. В следующем примере происходит возврат ошибки 137 применительно к обеим инструкциям, SET и SELECT, поскольку переменная **\@mycol** не объявлена.  
  
SET @mycol = 'ContactName';  
  
SELECT @mycol;  
  
Одной из трудноуловимых причин этой ошибки является использование переменной, которая объявлена вне инструкции EXECUTE. В следующем примере переменная **\@mycol**, указанная в инструкции SELECT, является локальной по отношению к инструкции SELECT и поэтому находится вне инструкции EXECUTE.  
  
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
  
## <a name="see-also"></a>См. также:  
[EXECUTE (Transact-SQL)](~/t-sql/language-elements/execute-transact-sql.md)  
[Инструкции SET (Transact-SQL)](~/t-sql/statements/set-statements-transact-sql.md)  
[DECLARE @local_variable (Transact-SQL)](~/t-sql/language-elements/declare-local-variable-transact-sql.md)  
  
