---
title: "Создание ТИПА сообщений (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 04/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_MESSAGE_TSQL
- MESSAGE_TSQL
- MESSAGE
- CREATE MESSAGE
- CREATE_MESSAGE_TYPE_TSQL
- MESSAGE TYPE
- MESSAGE_TYPE_TSQL
- CREATE MESSAGE TYPE
dev_langs:
- TSQL
helpviewer_keywords:
- XML [Service Broker]
- validation [Service Broker]
- message types [Service Broker], creating
- empty messages [SQL Server]
- binary [SQL Server], message types
- CREATE MESSAGE TYPE statement
ms.assetid: 98fe0fff-1a2e-4ca2-b37f-83a06fdf098e
caps.latest.revision: 41
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f8869a53cf18a58ba58b02e6faf8a42231e971e5
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-message-type-transact-sql"></a>CREATE MESSAGE TYPE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает новый тип сообщений. Тип сообщений определяет имя сообщения и проверку, выполняемую компонентом [!INCLUDE[ssSB](../../includes/sssb-md.md)] для сообщений с этим именем. Обе стороны диалога должны определить одинаковые типы сообщений.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
CREATE MESSAGE TYPE message_type_name  
    [ AUTHORIZATION owner_name ]  
    [ VALIDATION = {  NONE  
                    | EMPTY   
                    | WELL_FORMED_XML  
                    | VALID_XML WITH SCHEMA COLLECTION schema_collection_name  
                   } ]  
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *message_type_name*  
 Имя создаваемого типа сообщений. Создается новый тип сообщений в текущей базе данных, которой владеет участник, указанный в предложении AUTHORIZATION. Не могут быть указаны имена сервера, базы данных и схемы. *Message_type_name* может иметь длину до 128 символов.  
  
 АВТОРИЗАЦИЯ *owner_name*  
 Устанавливает указанного пользователя или роль базы данных в качестве владельца типа сообщений. Если текущий пользователь является **dbo** или **sa**, *owner_name* может быть именем любого допустимого пользователя или роли. В противном случае *owner_name* должен быть именем текущего пользователя, имя пользователя, у которого у текущего пользователя есть разрешение IMPERSONATE для или имя роли, к которой принадлежит текущий пользователь. Если это предложение опущено, тип сообщений будет принадлежать текущему пользователю.  
  
 VALIDATION  
 Указывает, как компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] производит проверку текста сообщения этого типа. Если это предложение не указано, то по умолчанию проверке присваивается значение NONE.  
  
 None  
 Указывает, что проверка не выполняется. Текст сообщения может содержать любые данные или иметь значение NULL.  
  
 EMPTY  
 Указывает, что текст сообщения должен быть NULL.  
  
 WELL_FORMED_XML  
 Указывает, что текст сообщения должен содержать корректные XML-данные.  
  
 VALID_XML WITH SCHEMA COLLECTION *данные*  
 Указывает, что текст сообщения должен содержать XML, который соответствует схеме в указанной коллекции схем *данные* должно быть именем существующей коллекции схем XML.  
  
## <a name="remarks"></a>Замечания  
 Компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] проверяет входящие сообщения. Если сообщение содержит текст, который не соответствует указанному типу проверки, компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] удаляет неправильное сообщение и возвращает службе, которая его отправила, сообщение об ошибке.  
  
 Обе стороны диалога должны задать одинаковые имена типа сообщений. В целях оказания помощи при поиске и устранении неполадок, обе стороны диалога обычно указывают одинаковые проверки для типа сообщений, хотя компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] не требует использования обеими сторонами одинаковой проверки.  
  
 Тип сообщений не может быть временным объектом. Начиная с имена типов сообщений  **#**  разрешены, но являются постоянными объектами.  
  
## <a name="permissions"></a>Permissions  
 Разрешение на создание типа сообщений по умолчанию имеют члены **db_ddladmin** или **db_owner** предопределенных ролей базы данных и **sysadmin** предопределенной роли сервера.  
  
 По умолчанию используется разрешение REFERENCES для типа сообщений обладает владелец типа сообщений, члены **db_owner** фиксированной роли базы данных, а также члены **sysadmin** предопределенной роли сервера.  
  
 Если инструкция CREATE MESSAGE TYPE задает коллекцию схемы, выполняющий инструкцию пользователь должен иметь разрешения REFERENCES для указанной коллекции схем.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-a-message-type-containing-well-formed-xml"></a>A. Создание типа сообщений, содержащего XML-документ правильного формата  
 Этот пример создает новый тип сообщений, который содержит корректный XML.  
  
```  
CREATE MESSAGE TYPE  
  [//Adventure-Works.com/Expenses/SubmitExpense]  
  VALIDATION = WELL_FORMED_XML ;     
```  
  
### <a name="b-creating-a-message-type-containing-typed-xml"></a>Б. Создание типа сообщений, содержащего типовой XML  
 Этот пример создает тип сообщений для отчета о затратах, закодированного в XML. Пример создает коллекцию XML-схем, которая содержит схему для простого отчета о затратах. Затем пример создает новый тип сообщений, который сверяет сообщения со схемой.  
  
```  
CREATE XML SCHEMA COLLECTION ExpenseReportSchema AS  
N'<?xml version="1.0" encoding="UTF-16" ?>  
  <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
     targetNamespace="http://Adventure-Works.com/schemas/expenseReport"  
     xmlns:expense="http://Adventure-Works.com/schemas/expenseReport"  
     elementFormDefault="qualified"  
   >   
    <xsd:complexType name="expenseReportType">  
       <xsd:sequence>  
         <xsd:element name="EmployeeName" type="xsd:string"/>  
         <xsd:element name="EmployeeID" type="xsd:string"/>  
         <xsd:element name="ItemDetail"  
           type="expense:ItemDetailType" maxOccurs="unbounded"/>  
      </xsd:sequence>  
    </xsd:complexType>  
  
    <xsd:complexType name="ItemDetailType">  
      <xsd:sequence>  
        <xsd:element name="Date" type="xsd:date"/>  
        <xsd:element name="CostCenter" type="xsd:string"/>  
        <xsd:element name="Total" type="xsd:decimal"/>  
        <xsd:element name="Currency" type="xsd:string"/>  
        <xsd:element name="Description" type="xsd:string"/>  
      </xsd:sequence>  
    </xsd:complexType>  
  
    <xsd:element name="ExpenseReport" type="expense:expenseReportType"/>  
  
  </xsd:schema>' ;  
  
  CREATE MESSAGE TYPE  
    [//Adventure-Works.com/Expenses/SubmitExpense]  
    VALIDATION = VALID_XML WITH SCHEMA COLLECTION ExpenseReportSchema ;  
```  
  
### <a name="c-creating-a-message-type-for-an-empty-message"></a>В. Создание типа сообщений для пустого сообщения  
 Этот пример создает новый тип сообщений с пустой кодировкой.  
  
```  
CREATE MESSAGE TYPE  
    [//Adventure-Works.com/Expenses/SubmitExpense]  
    VALIDATION = EMPTY ;  
```  
  
### <a name="d-creating-a-message-type-containing-binary-data"></a>Г. Создание типа сообщений, содержащего двоичные данные  
 Этот пример создает новый тип сообщений, который может содержать двоичные данные. Так как сообщение будет хранить данные, отличные от XML, в типе сообщений задается тип проверки `NONE`. Обратите внимание, что в таком случае приложение, которое принимает сообщение этого типа, должно проверить, имеются ли в этом сообщении данные, и относятся ли эти данные к ожидаемому типу.  
  
```  
CREATE MESSAGE TYPE  
    [//Adventure-Works.com/Expenses/ReceiptImage]  
    VALIDATION = NONE ;  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER MESSAGE TYPE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-message-type-transact-sql.md)   
 [DROP MESSAGE TYPE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-message-type-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

