---
title: Системные хранимые процедуры XML | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- system stored procedures [SQL Server], XML
- sp_xml_removedocument
- OPENXML statement, system stored procedures
- sp_xml_preparedocument
- XML [SQL Server], system stored procedures
ms.assetid: e60c7f85-6823-4d28-93d6-b053d08cc830
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d2e89e934fc8e1a476b7333ffe0c622465cabfe1
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43888880"
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
  
  
