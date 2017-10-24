---
title: "Запрет разрешения на коллекции схем XML (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server (starting with 2008)
dev_langs:
- TSQL
helpviewer_keywords:
- denying permissions [SQL Server], XML schema collections
- XML schema collections [SQL Server], permissions
- DENY statement, XML schema collections
- schema collections [SQL Server], permissions
ms.assetid: 159969a7-8313-41bc-bb19-c55af76597e6
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d50f055c6dbc419c8a979160f45a884f46f795d6
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="deny-xml-schema-collection-permissions-transact-sql"></a>DENY, запрет разрешения на коллекцию XML-схем (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Отказывает в предоставлении разрешений на коллекцию схем XML.  
  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DENY permission  [ ,...n ] ON   
    XML SCHEMA COLLECTION :: [ schema_name . ]  
    XML_schema_collection_name  
    TO <database_principal> [ ,...n ]  
        [ CASCADE ]  
    [ AS <database_principal> ]   
  
<database_principal> ::=   
        Database_user   
    | Database_role   
    | Application_role   
    | Database_user_mapped_to_Windows_User   
    | Database_user_mapped_to_Windows_Group   
    | Database_user_mapped_to_certificate   
    | Database_user_mapped_to_asymmetric_key   
    | Database_user_with_no_login  
```  
  
## <a name="arguments"></a>Аргументы  
 *разрешение*  
 Определяет разрешение, которое можно запретить для коллекции XML-схем. Список разрешений см. в подразделе «Примечания» далее в этом разделе.  
  
 КОЛЛЕКЦИИ СХЕМ XML ON:: [ *имя_схемы***.** ] *XML_schema_collection_name*  
 Определяет коллекцию XML-схем, на которую будет запрещено разрешение. Требуется квалификатор области (::). Если *schema_name* не указан, используется схема по умолчанию. Если *schema_name* указано, требуется квалификатор области схемы (.).  
  
 Чтобы \<database_principal >  
 Задает участника, для которого запрещается разрешение, —  
  
 CASCADE  
 Указывает, что запрещаемое разрешение также запрещается для других участников, которым оно было предоставлено данным участником.  
  
 AS \<database_principal >  
 Задает участника, от которого участник, выполняющий данный запрос, получает право на запрет разрешения.  
  
 *Пользователь_базы_данных*  
 Указывает пользователя базы данных.  
  
 *Database_role*  
 Указывает роль базы данных.  
  
 *Application_role*  
 Указывает роль приложения.  
  
 *Database_user_mapped_to_Windows_User*  
 Указывает пользователя базы данных, сопоставленного с пользователем Windows.  
  
 *Database_user_mapped_to_Windows_Group*  
 Указывает пользователя базы данных, сопоставленного с группой Windows.  
  
 *Database_user_mapped_to_certificate*  
 Указывает пользователя базы данных, сопоставленного с сертификатом.  
  
 *Database_user_mapped_to_asymmetric_key*  
 Указывает пользователя базы данных, сопоставленного с асимметричным ключом.  
  
 *Database_user_with_no_login*  
 Указывает пользователя базы данных, не сопоставленного с субъектом серверного уровня.  
  
## <a name="remarks"></a>Замечания  
 Сведения о коллекции XML-схем можно увидеть в [sys.xml_schema_collections](../../relational-databases/system-catalog-views/sys-xml-schema-collections-transact-sql.md) представления каталога.  
  
 Коллекция XML-схем представляет собой защищаемую сущность уровня схемы, содержащуюся в родительской схеме иерархии разрешений. Наиболее специфичные и ограниченные разрешения, которые можно запретить для коллекции XML-схем, перечислены в следующей таблице вместе с более общими разрешениями, неявно содержащими их.  
  
|Разрешение коллекции XML-схем|Содержится в разрешении коллекции схем XML|Содержится в разрешении схемы|  
|--------------------------------------|-------------------------------------------------|----------------------------------|  
|ALTER|CONTROL|ALTER|  
|CONTROL|CONTROL|CONTROL|  
|Выполните|CONTROL|Выполните|  
|REFERENCES|CONTROL|REFERENCES|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение CONTROL на коллекцию XML-схем. При использовании аргумента AS указанный участник должен быть владельцем коллекции XML-схем.  
  
## <a name="examples"></a>Примеры  
 В следующем примере запрещается разрешение `EXECUTE` на коллекцию XML-схем `Invoices4` для пользователя `Wanida`. Коллекция XML-схем `Invoices4` размещена внутри схемы `Sales` базы данных `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
DENY EXECUTE ON XML SCHEMA COLLECTION::Sales.Invoices4 TO Wanida;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [ПРЕДОСТАВЬТЕ разрешения на коллекцию схем XML &#40; Transact-SQL &#41;](../../t-sql/statements/grant-xml-schema-collection-permissions-transact-sql.md)   
 [ОТОЗВАТЬ разрешения на коллекцию схем XML &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-xml-schema-collection-permissions-transact-sql.md)   
 [sys.xml_schema_collections &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-xml-schema-collections-transact-sql.md)   
 [Создание КОЛЛЕКЦИИ XML-СХЕМ &#40; Transact-SQL &#41;](../../t-sql/statements/create-xml-schema-collection-transact-sql.md)   
 [Разрешения (компонент Database Engine)](../../relational-databases/security/permissions-database-engine.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  

