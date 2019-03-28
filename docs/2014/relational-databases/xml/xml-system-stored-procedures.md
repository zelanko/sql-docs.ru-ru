---
title: Системные хранимые процедуры XML | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- system stored procedures [SQL Server], XML
- sp_xml_removedocument
- OPENXML statement, system stored procedures
- sp_xml_preparedocument
- XML [SQL Server], system stored procedures
ms.assetid: e60c7f85-6823-4d28-93d6-b053d08cc830
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 20ea97f50592c6d8abc51e64acb4a164ad0b95b3
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58530006"
---
# <a name="xml-system-stored-procedures"></a>Системные хранимые процедуры XML
  СУБД SQL Server предоставляет следующие системные хранимые процедуры, которые используются вместе с инструкцией OPENXML:  
  
-   [sp_xml_preparedocument (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-xml-preparedocument-transact-sql)  
  
-   [sp_xml_removedocument (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-xml-removedocument-transact-sql)  
  
 Чтобы составлять запросы с помощью OPENXML, нужно сначала создать внутреннее представление XML-документа, вызвав процедуру **sp_xml_preparedocument**. Эта хранимая процедура возвращает дескриптор внутреннего представления XML-документа. Затем этот дескриптор передается инструкции OPENXML. Инструкция OPENXML предоставляет представления наборов строк документа, основанные на выражениях XPaths. Точнее, это одна комбинация для строк и одна или несколько для столбцов.  
  
> [!NOTE]  
>  Дескриптор документа, возвращаемый процедурой **sp_xml_preparedocument** , действителен в течение сеанса.  
  
 Внутреннее представление XML-документа можно удалить из памяти вызовом системной хранимой процедуры **sp_xml_removedocument** .  
  
## <a name="see-also"></a>См. также  
 [OPENXML (Transact-SQL)](/sql/t-sql/functions/openxml-transact-sql)   
 [OPENXML (SQL Server)](../xml/openxml-sql-server.md)  
  
  
