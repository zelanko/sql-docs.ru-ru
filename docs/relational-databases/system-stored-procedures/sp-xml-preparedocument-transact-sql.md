---
title: "sp_xml_preparedocument (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_xml_preparedocument_TSQL
- sp_xml_preparedocument
dev_langs:
- TSQL
helpviewer_keywords:
- sp_xml_preparedocument
ms.assetid: 95f41cff-c52a-4182-8ac6-bf49369d214c
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 86d05a3148d84622fb454bd83d25fee7875c1eb5
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="spxmlpreparedocument-transact-sql"></a>sp_xml_preparedocument (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Считывает входной XML-текст, проводит его синтаксический анализ при помощи средства синтаксического анализатора MSXML (Msxmlsql.dll) и выдает проанализированный документ, готовый к потреблению. Проанализированный документ является древовидным представлением различных узлов в XML-документе: элементов, атрибутов, текста, комментариев и т. д.  
  
 **sp_xml_preparedocument** возвращает дескриптор, который может использоваться для доступа к вновь созданного внутреннего представления XML-документа. Этот дескриптор действителен в течение сеанса или пока не будет аннулирован путем выполнения **sp_xml_removedocument**.  
  
> [!NOTE]  
>  Проанализированный документ хранится во внутреннем кэше [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Средство синтаксического анализа MSXML использует одну восьмую всей памяти, доступной [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Чтобы избежать нехватки памяти, запустите **sp_xml_removedocument** для освобождения памяти.  
  
> [!NOTE]  
>  Для обеспечения обратной совместимости, **sp_xml_preparedocument** символы возврата каретки (char(13)) и перевода строки (char(10)) из атрибутов, даже если эти символы существенны.  
  
> [!NOTE]  
>  Средство синтаксического анализа XML, вызываемых **sp_xml_preparedocument** можно анализировать внутренние DTD и объявления сущностей. Так как злонамеренно созданные DTD и сущностей объявления можно использовать для выполнения атаки отказа в обслуживании, мы настоятельно рекомендуется, чтобы не передавать напрямую XML-документы из сомнительных источников в **sp_xml_preparedocument**.  
>   
>  Чтобы избежать атак методом расширения рекурсивных сущностей, **sp_xml_preparedocument** ограничивает до 10 000 число сущностей, которые можно развернуть сущность на верхнем уровне документа. Это ограничение не применяется к символьным и числовым сущностям. Ограничение позволяет хранить документы с большим количеством ссылок на сущности, но предотвращает рекурсивное расширение отдельной сущности в цепочку длиннее 10 000 расширений.  
  
> [!NOTE]  
>  **sp_xml_preparedocument** ограничивает количество элементов, которые могут быть открыты одновременно до 256.  

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_xml_preparedocument  
hdoc   
OUTPUT  
[ , xmltext ]  
[ , xpath_namespaces ]   
```  
  
## <a name="arguments"></a>Аргументы  
 *hdoc*  
 Дескриптор только что созданного документа. *hdoc* должно быть целым числом.  
  
 [ *xmltext* ]  
 Исходный XML-документ. Средство синтаксического анализа MSXML анализирует этот XML-документ. *XmlText* является текстовым параметром: **char**, **nchar**, **varchar**, **nvarchar**, **текст**, **ntext** или **xml**. Значение по умолчанию равно NULL. В этом случае создается внутреннее представление пустого XML-документа.  
  
> [!NOTE]  
>  **sp_xml_preparedocument** может обрабатывать только текст или нетипизированный XML. Если значение экземпляра, передающееся в качестве входного параметра, уже является типизированным XML, его сначала необходимо привести к новому нетипизированному экземпляру XML или к строке, после чего его можно передавать в качестве входного параметра. Дополнительные сведения см. в статье [Сравнение типизированного и нетипизированного XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md).  
  
 [ *xpath_namespaces* ]  
 Указывает объявления пространств имен, которые используются в выражениях XPath строк и столбцов в OPENXML. *xpath_namespaces* является текстовым параметром: **char**, **nchar**, **varchar**, **nvarchar**, **текста** , **ntext** или **xml**.  
  
 Значение по умолчанию —  **\<корневой xmlns:mp = "urn: schemas-microsoft-com: XML-metaprop" >**. *xpath_namespaces* предоставляет URI пространств имен для префиксов, используемых в выражениях XPath в OPENXML посредством XML-документа правильного формата. *xpath_namespaces* объявляет префикс, который должен использоваться для обращения к пространству имен **urn: schemas-microsoft-com: XML-metaprop**; таким образом предоставляются метаданные о проанализированных элементах XML. Хотя с помощью данного приема можно переопределить префикс пространства имен для пространства имен метасвойства, это пространство имен не будет потеряно. Префикс **mp** все еще действует для **urn: schemas-microsoft-com: XML-metaprop** даже в том случае, если *xpath_namespaces* не содержит такого объявления.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или >0 (неуспешное завершение)  
  
## <a name="permissions"></a>Permissions  
 Необходимо быть членом роли **public** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-preparing-an-internal-representation-for-a-well-formed-xml-document"></a>A. Подготовка внутреннего представления для XML-документа правильного формата  
 В следующем примере возвращается дескриптор вновь созданного внутреннего представления XML-документа, который передается как входной аргумент. При вызове процедуры `sp_xml_preparedocument` используется сопоставление префикса пространства имен по умолчанию.  
  
```  
DECLARE @hdoc int;  
DECLARE @doc varchar(1000);  
SET @doc ='  
<ROOT>  
<Customer CustomerID="VINET" ContactName="Paul Henriot">  
   <Order CustomerID="VINET" EmployeeID="5" OrderDate="1996-07-04T00:00:00">  
      <OrderDetail OrderID="10248" ProductID="11" Quantity="12"/>  
      <OrderDetail OrderID="10248" ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" ContactName="Carlos Gonzlez">  
   <Order CustomerID="LILAS" EmployeeID="3" OrderDate="1996-08-16T00:00:00">  
      <OrderDetail OrderID="10283" ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>';  
--Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @hdoc OUTPUT, @doc;  
-- Remove the internal representation.  
exec sp_xml_removedocument @hdoc;  
```  
  
### <a name="b-preparing-an-internal-representation-for-a-well-formed-xml-document-with-a-dtd"></a>Б. Подготовка внутреннего представления для XML-документа правильного формата с DTD  
 В следующем примере возвращается дескриптор вновь созданного внутреннего представления XML-документа, который передается как входной аргумент. Хранимая процедура проверяет корректность загруженного документа с помощью DTD, включенного в документ. При вызове процедуры `sp_xml_preparedocument` используется сопоставление префикса пространства имен по умолчанию.  
  
```  
DECLARE @hdoc int;  
DECLARE @doc varchar(2000);  
SET @doc = '  
<?xml version="1.0" encoding="UTF-8" ?>   
<!DOCTYPE root   
[<!ELEMENT root (Customers)*>  
<!ELEMENT Customers EMPTY>  
<!ATTLIST Customers CustomerID CDATA #IMPLIED ContactName CDATA #IMPLIED>]>  
<root>  
<Customers CustomerID="ALFKI" ContactName="Maria Anders"/>  
</root>';  
  
EXEC sp_xml_preparedocument @hdoc OUTPUT, @doc;  
```  
  
### <a name="c-specifying-a-namespace-uri"></a>В. Указание URI пространства имен  
 В следующем примере возвращается дескриптор вновь созданного внутреннего представления XML-документа, который передается как входной аргумент. Вызов `sp_xml_preparedocument` сохраняет `mp` префикс для сопоставления пространства имен метасвойств и добавляет `xyz` префикс сопоставления для пространства имен `urn:MyNamespace`.  
  
```  
DECLARE @hdoc int;  
DECLARE @doc varchar(1000);  
SET @doc ='  
<ROOT>  
<Customer CustomerID="VINET" ContactName="Paul Henriot">  
   <Order CustomerID="VINET" EmployeeID="5"   
           OrderDate="1996-07-04T00:00:00">  
      <OrderDetail OrderID="10248" ProductID="11" Quantity="12"/>  
      <OrderDetail OrderID="10248" ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" ContactName="Carlos Gonzlez">  
   <Order CustomerID="LILAS" EmployeeID="3"   
           OrderDate="1996-08-16T00:00:00">  
      <OrderDetail OrderID="10283" ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>'  
--Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @hdoc OUTPUT, @doc, '<ROOT xmlns:xyz="urn:MyNamespace"/>';  
```  
  
## <a name="see-also"></a>См. также:  
 [XML хранимые процедуры &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/xml-stored-procedures-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_xml_removedocument (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-xml-removedocument-transact-sql.md)   
 [OPENXML (Transact-SQL)](../../t-sql/functions/openxml-transact-sql.md)  
  
  
