---
title: Основные сведения об ошибках ядра СУБД | Документация Майкрософт
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
- errors [SQL Server], about errors
- errors [SQL Server], Database Engine
- errors [SQL Server]
- Database Engine [SQL Server], errors
ms.assetid: ddaca9d3-956f-46a5-8cd3-a7a15ec75878
caps.latest.revision: 26
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 13efa173edf55d35ce701a2594ede4cc30e4abf5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188688"
---
# <a name="understanding-database-engine-errors"></a>Основные сведения об ошибках компонента Database Engine
  Ошибки, возникшие в компоненте [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , имеют атрибуты, описанные в следующей таблице.  
  
|attribute|Описание|  
|---------------|-----------------|  
|Номер ошибки|Каждое сообщение имеет уникальный номер ошибки.|  
|Строка сообщения об ошибке|Сообщение об ошибке содержит диагностические сведения о причине ошибки. Многие сообщения об ошибках имеют подстановочные переменные, в которые заносятся сведения, например имя объекта, вызвавшего ошибку.|  
|Severity|Степень серьезности ошибки указывает, насколько она значительна. Ошибки с низкой степенью серьезности, например 1 или 2, являются информационными сообщениями или предупреждениями низкого уровня. Ошибки с высокой степенью серьезности указывают на проблемы, которые должны быть решены как можно быстрее. Дополнительные сведения о степенях серьезности см. в разделе [Степени серьезности ошибок компонента Database Engine](database-engine-error-severities.md).|  
|Состояние|Некоторые сообщения об ошибках могут возникнуть в нескольких точках кода компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Например, ошибка 1105 может возникнуть при различных условиях. Каждое условие, которое вызывает ошибку, присваивает уникальный код состояния.<br /><br /> При просмотре баз данных со сведениями об известных неполадках, таких как база знаний [!INCLUDE[msCoName](../../includes/msconame-md.md)] , можно использовать номер состояния, чтобы определить, является ли записанная неполадка возникшей ошибкой. Например, если статья базы знаний описывает ошибку 1105 с состоянием 2, а получена ошибка 1105 с состоянием 3, ошибка, вероятно, возникла не по той причине, которая описана в статье.<br /><br /> Инженер поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] также может использовать код состояния, содержащийся в сообщении об ошибке, чтобы найти место в исходном коде, где эта ошибка возникла. Эти данные могут предоставить дополнительные сведения для диагностики проблемы.|  
|Имя процедуры|Имя хранимой процедуры или триггера, в которых произошла ошибка.|  
|Номер строки|Указывает на инструкцию в пакете, хранимой процедуре, триггере или функции, которая сформировала ошибку.|  
  
 Все системные и пользовательские сообщения об ошибках в экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] содержатся в представлении каталога **sys.messages** . Инструкцию RAISERROR можно использовать для возвращения пользовательских ошибок приложению.  
  
 Все API-интерфейсы базы данных, например пространство имен [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] **SQLClient** , ActiveX Data Objects (ADO), OLE DB и Open Database Connectivity (ODBC), сообщают основные атрибуты ошибки. Эти сведения включают номер ошибки и строку сообщения. Однако не все API-интерфейсы сообщают остальные атрибуты ошибки.  
  
 Сведения об ошибке, которая появляется внутри области TRY конструкции TRY…CATCH, могут быть получены в коде [!INCLUDE[tsql](../../includes/tsql-md.md)] при использовании таких функций, как ERROR_LINE, ERROR_MESSAGE, ERROR_NUMBER, ERROR_PROCEDURE, ERROR_SEVERITY и ERROR_STATE, внутри области соответствующего блока CATCH. Дополнительные сведения см. в разделе [TRY...CATCH (Transact-SQL)](/sql/t-sql/language-elements/try-catch-transact-sql).  
  
## <a name="examples"></a>Примеры  
 Следующий пример обращается с запросом к представлению каталога `sys.messages` , возвращающим список всех системных и пользовательских сообщений об ошибках в компоненте [!INCLUDE[ssDE](../../includes/ssde-md.md)] , содержащих английский текст (`1033`).  
  
```  
SELECT  
    message_id,  
    language_id,  
    severity,  
    is_event_logged,  
    text  
  FROM sys.messages  
  WHERE language_id = 1033;  
```  
  
 Дополнительные сведения см. в разделе [sys.messages (Transact-SQL)](/sql/relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages).  
  
## <a name="see-also"></a>См. также  
 [sys.messages (Transact-SQL)](/sql/relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages)   
 [RAISERROR (Transact-SQL)](/sql/t-sql/language-elements/raiserror-transact-sql)   
 [@@ERROR (Transact-SQL)](/sql/t-sql/functions/error-transact-sql)   
 [TRY...CATCH (Transact-SQL)](/sql/t-sql/language-elements/try-catch-transact-sql)   
 [ERROR_LINE (Transact-SQL)](/sql/t-sql/functions/error-line-transact-sql)   
 [ERROR_MESSAGE (Transact-SQL)](/sql/t-sql/functions/error-message-transact-sql)   
 [ERROR_NUMBER (Transact-SQL)](/sql/t-sql/functions/error-number-transact-sql)   
 [ERROR_PROCEDURE (Transact-SQL)](/sql/t-sql/functions/error-procedure-transact-sql)   
 [ERROR_SEVERITY (Transact-SQL)](/sql/t-sql/functions/error-severity-transact-sql)   
 [ERROR_STATE (Transact-SQL)](/sql/t-sql/functions/error-state-transact-sql)  
  
  
