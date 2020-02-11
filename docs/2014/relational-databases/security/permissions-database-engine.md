---
title: Разрешения (ядро СУБД) | Документация Майкрософт
ms.custom: ''
ms.date: 10/14/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseuser.permissions.database.f1--May use common.permissions
- sql12.swb.databaseuser.permissions.object.f1--May use common.permissions
helpviewer_keywords:
- REFERENCES permission
- permissions [SQL Server]
- security [SQL Server], permissions
- naming conventions [SQL Server]
ms.assetid: f28e3dea-24e6-4a81-877b-02ec4c7e36b9
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 746d547b680817868de33759983dc908e9806bb6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63128766"
---
# <a name="permissions-database-engine"></a>Разрешения (ядро СУБД)
  С каждым защищаемым объектом в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] связаны разрешения, которые могут быть предоставлены участнику. В данном подразделе содержатся следующие сведения.  
  
-   [Соглашения об именовании разрешений](#_conventions)  
  
-   [Разрешения, относящиеся к конкретным защищаемым объектам](#_securables)  
  
-   [Разрешения SQL Server](#_permissions)  
  
-   [Алгоритм проверки разрешений](#_algorithm)  
  
-   [Примеры](#_examples)  
  
##  <a name="_conventions"></a>Соглашения об именовании разрешений  
 Ниже описаны общие соглашения, которые соблюдаются при задании имен разрешениям.  
  
-   CONTROL  
  
     Предоставляет возможности, схожие с владением. Имеющий это разрешение получает все установленные разрешения на защищаемую сущность. Участник, получивший разрешение CONTROL, может также предоставлять разрешения на защищаемую сущность другим участникам. Так как в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используется иерархическая модель безопасности, разрешение CONTROL на определенную область неявно включает разрешение CONTROL на все защищаемые объекты в пределах данной области. Например, разрешение CONTROL на базу данных неявно предполагает все разрешения на базу данных, все разрешения на все сборки в базе данных, все разрешения на все схемы в базе данных, а также все разрешения на объекты в пределах всех схем базы данных.  
  
-   ALTER  
  
     Предоставляет возможность изменения свойств определенной защищаемой сущности, кроме ее владельца. При предоставлении разрешения ALTER на ту или иную область также предоставляется возможность изменения, создания или удаления любой защищаемой сущности, содержащейся в пределах данной области. Например, разрешение ALTER на схему включает возможность создания, изменения и удаления объектов этой схемы.  
  
-   ALTER ANY \<*Защищаемый объект сервера*>, где *Защищаемый объект сервера* может быть любым защищаемым объектом на уровне сервера.  
  
     Предоставляет возможность создавать, изменять и удалять отдельные экземпляры *Защищаемой сущности сервера*. Например, разрешение ALTER ANY LOGIN предоставляет возможность создания, изменения и удаления любого имени входа в экземпляре.  
  
-   ALTER ANY \<*Защищаемый объект базы данных*>, где *Защищаемый объект базы данных* может быть любым защищаемым объектом на уровне базы данных.  
  
     Предоставляет возможность СОЗДАВАТЬ, ИЗМЕНЯТЬ и УДАЛЯТЬ отдельные экземпляры *Защищаемой сущности базы данных*. Например, разрешение ALTER ANY SCHEMA предоставляет возможность создания, изменения и удаления любой схемы в базе данных.  
  
-   TAKE OWNERSHIP  
  
     Позволяет получать во владение защищаемую сущность, на которую предоставлено разрешение.  
  
-   \<Олицетворять *имя входа*>  
  
     Позволяет олицетворять имя входа.  
  
-   \<Олицетворять *пользователя*>  
  
     Позволяет олицетворять пользователя.  
  
-   Создание \< *защищаемого объекта сервера*>  
  
     Предоставляет возможность создавать *Защищаемую сущность сервера*.  
  
-   Создать \< *защищаемую сущность базы данных*>  
  
     Предоставляет возможность создавать *Защищаемую сущность базы данных*.  
  
-   Создание \< *защищаемой сущности, содержащейся в схеме*>  
  
     Предоставляет возможность создавать защищаемую сущность, содержащуюся в схеме. Однако для создания защищаемой сущности в той или иной схеме на эту схему требуется разрешение ALTER.  
  
-   VIEW DEFINITION  
  
     Разрешает доступ к метаданным.  
  
-   REFERENCES  
  
     Разрешение REFERENCES для таблицы необходимо для создания ограничения FOREIGN KEY, которое ссылается на эту таблицу.  
  
     Разрешение REFERENCES для объекта необходимо для создания FUNCTION или VIEW с предложением 2 `WITH SCHEMABINDING` , которое ссылается на этот объект.  
  
## <a name="chart-of-sql-server-permissions"></a>Диаграмма разрешений SQL Server  
 Для получения диаграммы с размером афиши [!INCLUDE[ssDE](../../includes/ssde-md.md)] всех разрешений в формате PDF см [https://go.microsoft.com/fwlink/?LinkId=229142](https://go.microsoft.com/fwlink/?LinkId=229142). раздел.  
  
##  <a name="_securables"></a>Разрешения, применимые к конкретным защищаемым объектам  
 В следующей таблице перечислены главные классы разрешений и защищаемых объектов, к которым эти разрешения могут применяться.  
  
|Разрешение|Применяется к|  
|----------------|----------------|  
|SELECT|Синонимы<br /><br /> Таблицы и столбцы<br /><br /> Функции [!INCLUDE[tsql](../../includes/tsql-md.md)] с табличным значением и среды CLR, а также столбцы<br /><br /> Представления и столбцы|  
|VIEW CHANGE TRACKING|Таблицы<br /><br /> Схемы|  
|UPDATE|Синонимы<br /><br /> Таблицы и столбцы<br /><br /> Представления и столбцы<br /><br /> Объекты последовательности|  
|REFERENCES|Скалярные и агрегатные функции (языка[!INCLUDE[tsql](../../includes/tsql-md.md)] и среды CLR)<br /><br /> [!INCLUDE[ssSB](../../includes/sssb-md.md)]очереди<br /><br /> Таблицы и столбцы<br /><br /> Функции с табличным значением ([!INCLUDE[tsql](../../includes/tsql-md.md)] и CLR) и столбцы<br /><br /> Типы<br /><br /> Представления и столбцы<br /><br /> Объекты последовательности|  
|INSERT|Синонимы<br /><br /> Таблицы и столбцы<br /><br /> Представления и столбцы|  
|DELETE|Синонимы<br /><br /> Таблицы и столбцы<br /><br /> Представления и столбцы|  
|EXECUTE|Процедуры (языка[!INCLUDE[tsql](../../includes/tsql-md.md)] и среды CLR)<br /><br /> Скалярные и агрегатные функции (языка[!INCLUDE[tsql](../../includes/tsql-md.md)] и среды CLR)<br /><br /> Синонимы<br /><br /> Типы CLR|  
|RECEIVE|[!INCLUDE[ssSB](../../includes/sssb-md.md)]очереди|  
|VIEW DEFINITION|Группы доступности<br /><br /> Процедуры (языка[!INCLUDE[tsql](../../includes/tsql-md.md)] и среды CLR)<br /><br /> [!INCLUDE[ssSB](../../includes/sssb-md.md)]очереди<br /><br /> Скалярные и агрегатные функции (языка[!INCLUDE[tsql](../../includes/tsql-md.md)] и среды CLR)<br /><br /> Имена входа, пользователи и роли<br /><br /> Синонимы<br /><br /> Таблицы<br /><br /> Функции с табличным значением ([!INCLUDE[tsql](../../includes/tsql-md.md)] и CLR)<br /><br /> Представления<br /><br /> Объекты последовательности|  
|ALTER|Группы доступности<br /><br /> Процедуры (языка[!INCLUDE[tsql](../../includes/tsql-md.md)] и среды CLR)<br /><br /> Скалярные и агрегатные функции (языка[!INCLUDE[tsql](../../includes/tsql-md.md)] и среды CLR)<br /><br /> Объекты последовательности<br /><br /> Имена входа, пользователи и роли<br /><br /> [!INCLUDE[ssSB](../../includes/sssb-md.md)]очереди<br /><br /> Таблицы<br /><br /> Функции с табличным значением ([!INCLUDE[tsql](../../includes/tsql-md.md)] и CLR)<br /><br /> Представления|  
|TAKE OWNERSHIP|Группы доступности<br /><br /> Роли<br /><br /> Процедуры (языка[!INCLUDE[tsql](../../includes/tsql-md.md)] и среды CLR)<br /><br /> Скалярные и агрегатные функции (языка[!INCLUDE[tsql](../../includes/tsql-md.md)] и среды CLR)<br /><br /> роли сервера;<br /><br /> Синонимы<br /><br /> Таблицы<br /><br /> Функции с табличным значением ([!INCLUDE[tsql](../../includes/tsql-md.md)] и CLR)<br /><br /> Представления<br /><br /> Объекты последовательности|  
|CONTROL|Группы доступности<br /><br /> Процедуры (языка[!INCLUDE[tsql](../../includes/tsql-md.md)] и среды CLR)<br /><br /> Скалярные и агрегатные функции (языка[!INCLUDE[tsql](../../includes/tsql-md.md)] и среды CLR)<br /><br /> Имена входа, пользователи и роли<br /><br /> [!INCLUDE[ssSB](../../includes/sssb-md.md)]очереди<br /><br /> Синонимы<br /><br /> Таблицы<br /><br /> Функции с табличным значением ([!INCLUDE[tsql](../../includes/tsql-md.md)] и CLR)<br /><br /> Представления<br /><br /> Объекты последовательности|  
|IMPERSONATE|Имена входа и пользователи|  
  
> [!CAUTION]  
>  Разрешения по умолчанию, которые предоставляются системным объектам во время установки, тщательно оцениваются на предмет возможных угроз, и их не нужно будет изменять для защиты установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Любые изменения разрешений в системных объектах могут ограничить или нарушить функциональность, а также перевести установку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в неподдерживаемое состояние.  
  
##  <a name="_permissions"></a>SQL Server и разрешения базы данных SQL  
 В следующей таблице приведен полный список разрешений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Разрешения[!INCLUDE[ssSDS](../../includes/sssds-md.md)] доступны только для поддерживаемых базовых защищаемых объектов. В [!INCLUDE[ssSDS](../../includes/sssds-md.md)]невозможно предоставлять разрешения на уровне сервера, но в некоторых случаях вместо них доступны разрешения базы данных.  
  
|Базовая защищаемая сущность|Гранулярные разрешения на базовую защищаемую сущность|Код типа разрешения|Защищаемая сущность, содержащая базовую сущность|Разрешение на защищаемую сущность контейнера, неявно предоставляющее гранулярное разрешение на базовую сущность|  
|--------------------|--------------------------------------------|--------------------------|--------------------------------------------|------------------------------------------------------------------------------------------|  
|APPLICATION ROLE|ALTER|AL|DATABASE|ALTER ANY APPLICATION ROLE|  
|APPLICATION ROLE|CONTROL|CL|DATABASE|CONTROL|  
|APPLICATION ROLE|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|ASSEMBLY|ALTER|AL|DATABASE|ALTER ANY ASSEMBLY|  
|ASSEMBLY|CONTROL|CL|DATABASE|CONTROL|  
|ASSEMBLY|REFERENCES|RF;|DATABASE|REFERENCES|  
|ASSEMBLY|TAKE OWNERSHIP|В|DATABASE|CONTROL|  
|ASSEMBLY|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|ASYMMETRIC KEY|ALTER|AL|DATABASE|ALTER ANY ASYMMETRIC KEY|  
|ASYMMETRIC KEY|CONTROL|CL|DATABASE|CONTROL|  
|ASYMMETRIC KEY|REFERENCES|RF;|DATABASE|REFERENCES|  
|ASYMMETRIC KEY|TAKE OWNERSHIP|В|DATABASE|CONTROL|  
|ASYMMETRIC KEY|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|AVAILABILITY GROUP|ALTER|AL|SERVER|ALTER ANY AVAILABILITY GROUP|  
|AVAILABILITY GROUP|CONTROL|CL|SERVER|CONTROL SERVER|  
|AVAILABILITY GROUP|TAKE OWNERSHIP|В|SERVER|CONTROL SERVER|  
|AVAILABILITY GROUP|VIEW DEFINITION|VW|SERVER|VIEW ANY DEFINITION|  
|CERTIFICATE|ALTER|AL|DATABASE|ALTER ANY CERTIFICATE|  
|CERTIFICATE|CONTROL|CL|DATABASE|CONTROL|  
|CERTIFICATE|REFERENCES|RF;|DATABASE|REFERENCES|  
|CERTIFICATE|TAKE OWNERSHIP|В|DATABASE|CONTROL|  
|CERTIFICATE|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|CONTRACT|ALTER|AL|DATABASE|ALTER ANY CONTRACT|  
|CONTRACT|CONTROL|CL|DATABASE|CONTROL|  
|CONTRACT|REFERENCES|RF;|DATABASE|REFERENCES|  
|CONTRACT|TAKE OWNERSHIP|В|DATABASE|CONTROL|  
|CONTRACT|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|DATABASE|ALTER|AL|SERVER|ALTER ANY DATABASE|  
|DATABASE|ALTER ANY APPLICATION ROLE|ALAR|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY ASSEMBLY|ALAS|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY ASYMMETRIC KEY|ALAK|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY CERTIFICATE|ALCF|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY CONTRACT|ALSC|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY DATABASE AUDIT|ALDA|SERVER|ALTER ANY SERVER AUDIT|  
|DATABASE|ALTER ANY DATABASE DDL TRIGGER|ALTG|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY DATABASE EVENT NOTIFICATION|ALED|SERVER|ALTER ANY EVENT NOTIFICATION|  
|DATABASE|ALTER ANY DATABASE EVENT SESSION|AADS<br /><br /> Примечание. применяется только к [!INCLUDE[ssSDS](../../includes/sssds-md.md)].|SERVER|ALTER ANY EVENT SESSION|  
|DATABASE|ALTER ANY DATASPACE|ALDS|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY FULLTEXT CATALOG|ALFT|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY MESSAGE TYPE|ALMT|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY REMOTE SERVICE BINDING|ALSB|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY ROLE|ALRL|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY ROUTE|ALRT|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY SCHEMA|ALSM|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY SECURITY POLICY|ALSP<br /><br /> Примечание. применяется только к [!INCLUDE[ssSDS](../../includes/sssds-md.md)].|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY SERVICE|ALSV|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY SYMMETRIC KEY|ALSK|SERVER|CONTROL SERVER|  
|DATABASE|ALTER ANY USER|ALUS|SERVER|CONTROL SERVER|  
|DATABASE|AUTHENTICATE|AUTH|SERVER|AUTHENTICATE SERVER|  
|DATABASE|BACKUP DATABASE|BADB|SERVER|CONTROL SERVER|  
|DATABASE|BACKUP LOG|BALO|SERVER|CONTROL SERVER|  
|DATABASE|CHECKPOINT|CP|SERVER|CONTROL SERVER|  
|DATABASE|CONNECT.|CO|SERVER|CONTROL SERVER|  
|DATABASE|CONNECT REPLICATION|CORP|SERVER|CONTROL SERVER|  
|DATABASE|CONTROL|CL|SERVER|CONTROL SERVER|  
|DATABASE|CREATE AGGREGATE|CRAG|SERVER|CONTROL SERVER|  
|DATABASE|CREATE ASSEMBLY|CRAS|SERVER|CONTROL SERVER|  
|DATABASE|CREATE ASYMMETRIC KEY|CRAK|SERVER|CONTROL SERVER|  
|DATABASE|CREATE CERTIFICATE|CRCF|SERVER|CONTROL SERVER|  
|DATABASE|CREATE CONTRACT|CRSC|SERVER|CONTROL SERVER|  
|DATABASE|CREATE DATABASE|CRDB|SERVER|CREATE ANY DATABASE|  
|DATABASE|CREATE DATABASE DDL EVENT NOTIFICATION|CRED|SERVER|CREATE DDL EVENT NOTIFICATION|  
|DATABASE|CREATE DEFAULT|CRDF|SERVER|CONTROL SERVER|  
|DATABASE|CREATE FULLTEXT CATALOG|CRFT|SERVER|CONTROL SERVER|  
|DATABASE|CREATE FUNCTION|CRFN|SERVER|CONTROL SERVER|  
|DATABASE|CREATE MESSAGE TYPE|CRMT|SERVER|CONTROL SERVER|  
|DATABASE|CREATE PROCEDURE|CRPR|SERVER|CONTROL SERVER|  
|DATABASE|CREATE QUEUE|CRQU|SERVER|CONTROL SERVER|  
|DATABASE|CREATE REMOTE SERVICE BINDING|CRSB|SERVER|CONTROL SERVER|  
|DATABASE|CREATE ROLE|CRRL|SERVER|CONTROL SERVER|  
|DATABASE|CREATE ROUTE|CRRT|SERVER|CONTROL SERVER|  
|DATABASE|CREATE RULE|CRRU|SERVER|CONTROL SERVER|  
|DATABASE|CREATE SCHEMA|CRSM|SERVER|CONTROL SERVER|  
|DATABASE|CREATE SERVICE|CRSV|SERVER|CONTROL SERVER|  
|DATABASE|CREATE SYMMETRIC KEY|CRSK|SERVER|CONTROL SERVER|  
|DATABASE|CREATE SYNONYM|CRSN|SERVER|CONTROL SERVER|  
|DATABASE|CREATE TABLE|CRTB|SERVER|CONTROL SERVER|  
|DATABASE|CREATE TYPE|CRTY|SERVER|CONTROL SERVER|  
|DATABASE|CREATE VIEW|CRVW|SERVER|CONTROL SERVER|  
|DATABASE|CREATE XML SCHEMA COLLECTION|CRXS|SERVER|CONTROL SERVER|  
|DATABASE|DELETE|DL|SERVER|CONTROL SERVER|  
|DATABASE|EXECUTE|EX|SERVER|CONTROL SERVER|  
|DATABASE|INSERT|IN|SERVER|CONTROL SERVER|  
|DATABASE|KILL DATABASE CONNECTION|KIDC<br /><br /> Примечание. применяется только к [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Использование ALTER ANY CONNECTION в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|SERVER|ALTER ANY CONNECTION|  
|DATABASE|REFERENCES|RF;|SERVER|CONTROL SERVER|  
|DATABASE|SELECT|SL|SERVER|CONTROL SERVER|  
|DATABASE|SHOWPLAN|SPLN|SERVER|ALTER TRACE|  
|DATABASE|SUBSCRIBE QUERY NOTIFICATIONS|SUQN|SERVER|CONTROL SERVER|  
|DATABASE|TAKE OWNERSHIP|В|SERVER|CONTROL SERVER|  
|DATABASE|UPDATE|РАБОТАЕТ|SERVER|CONTROL SERVER|  
|DATABASE|VIEW DATABASE STATE|VWDS|SERVER|VIEW SERVER STATE|  
|DATABASE|VIEW DEFINITION|VW|SERVER|VIEW ANY DEFINITION|  
|ENDPOINT|ALTER|AL|SERVER|ALTER ANY ENDPOINT|  
|ENDPOINT|CONNECT.|CO|SERVER|CONTROL SERVER|  
|ENDPOINT|CONTROL|CL|SERVER|CONTROL SERVER|  
|ENDPOINT|TAKE OWNERSHIP|В|SERVER|CONTROL SERVER|  
|ENDPOINT|VIEW DEFINITION|VW|SERVER|VIEW ANY DEFINITION|  
|FULLTEXT CATALOG|ALTER|AL|DATABASE|ALTER ANY FULLTEXT CATALOG|  
|FULLTEXT CATALOG|CONTROL|CL|DATABASE|CONTROL|  
|FULLTEXT CATALOG|REFERENCES|RF;|DATABASE|REFERENCES|  
|FULLTEXT CATALOG|TAKE OWNERSHIP|В|DATABASE|CONTROL|  
|FULLTEXT CATALOG|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|FULLTEXT STOPLIST|ALTER|AL|DATABASE|ALTER ANY FULLTEXT CATALOG|  
|FULLTEXT STOPLIST|CONTROL|CL|DATABASE|CONTROL|  
|FULLTEXT STOPLIST|REFERENCES|RF;|DATABASE|REFERENCES|  
|FULLTEXT STOPLIST|TAKE OWNERSHIP|В|DATABASE|CONTROL|  
|FULLTEXT STOPLIST|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|Имя_для_входа|ALTER|AL|SERVER|ALTER ANY LOGIN|  
|Имя_для_входа|CONTROL|CL|SERVER|CONTROL SERVER|  
|Имя_для_входа|IMPERSONATE|IM|SERVER|CONTROL SERVER|  
|Имя_для_входа|VIEW DEFINITION|VW|SERVER|VIEW ANY DEFINITION|  
|MESSAGE TYPE|ALTER|AL|DATABASE|ALTER ANY MESSAGE TYPE|  
|MESSAGE TYPE|CONTROL|CL|DATABASE|CONTROL|  
|MESSAGE TYPE|REFERENCES|RF;|DATABASE|REFERENCES|  
|MESSAGE TYPE|TAKE OWNERSHIP|В|DATABASE|CONTROL|  
|MESSAGE TYPE|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|OBJECT|ALTER|AL|SCHEMA|ALTER|  
|OBJECT|CONTROL|CL|SCHEMA|CONTROL|  
|OBJECT|DELETE|DL|SCHEMA|DELETE|  
|OBJECT|EXECUTE|EX|SCHEMA|EXECUTE|  
|OBJECT|INSERT|IN|SCHEMA|INSERT|  
|OBJECT|RECEIVE|RC|SCHEMA|CONTROL|  
|OBJECT|REFERENCES|RF;|SCHEMA|REFERENCES|  
|OBJECT|SELECT|SL|SCHEMA|SELECT|  
|OBJECT|TAKE OWNERSHIP|В|SCHEMA|CONTROL|  
|OBJECT|UPDATE|РАБОТАЕТ|SCHEMA|UPDATE|  
|OBJECT|VIEW CHANGE TRACKING|VWCT|SCHEMA|VIEW CHANGE TRACKING|  
|OBJECT|VIEW DEFINITION|VW|SCHEMA|VIEW DEFINITION|  
|REMOTE SERVICE BINDING|ALTER|AL|DATABASE|ALTER ANY REMOTE SERVICE BINDING|  
|REMOTE SERVICE BINDING|CONTROL|CL|DATABASE|CONTROL|  
|REMOTE SERVICE BINDING|TAKE OWNERSHIP|В|DATABASE|CONTROL|  
|REMOTE SERVICE BINDING|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|ROLE|ALTER|AL|DATABASE|ALTER ANY ROLE|  
|ROLE|CONTROL|CL|DATABASE|CONTROL|  
|ROLE|TAKE OWNERSHIP|В|DATABASE|CONTROL|  
|ROLE|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|ROUTE|ALTER|AL|DATABASE|ALTER ANY ROUTE|  
|ROUTE|CONTROL|CL|DATABASE|CONTROL|  
|ROUTE|TAKE OWNERSHIP|В|DATABASE|CONTROL|  
|ROUTE|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|SEARCH PROPERTY LIST|ALTER|AL|SERVER|ALTER ANY FULLTEXT CATALOG|  
|SEARCH PROPERTY LIST|CONTROL|CL|SERVER|CONTROL|  
|SEARCH PROPERTY LIST|REFERENCES|RF;|SERVER|REFERENCES|  
|SEARCH PROPERTY LIST|TAKE OWNERSHIP|В|SERVER|CONTROL|  
|SEARCH PROPERTY LIST|VIEW DEFINITION|VW|SERVER|VIEW DEFINITION|  
|SCHEMA|ALTER|AL|DATABASE|ALTER ANY SCHEMA|  
|SCHEMA|CONTROL|CL|DATABASE|CONTROL|  
|SCHEMA|CREATE SEQUENCE|CRSO|DATABASE|CONTROL|  
|SCHEMA|DELETE|DL|DATABASE|DELETE|  
|SCHEMA|EXECUTE|EX|DATABASE|EXECUTE|  
|SCHEMA|INSERT|IN|DATABASE|INSERT|  
|SCHEMA|REFERENCES|RF;|DATABASE|REFERENCES|  
|SCHEMA|SELECT|SL|DATABASE|SELECT|  
|SCHEMA|TAKE OWNERSHIP|В|DATABASE|CONTROL|  
|SCHEMA|UPDATE|РАБОТАЕТ|DATABASE|UPDATE|  
|SCHEMA|VIEW CHANGE TRACKING|VWCT|DATABASE|VIEW CHANGE TRACKING|  
|SCHEMA|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|SERVER|ADMINISTER BULK OPERATIONS|ADBO|Не применяется|Не применяется|  
|SERVER|ALTER ANY CONNECTION|ALCO|Не применяется|Не применяется|  
|SERVER|ALTER ANY CREDENTIAL|ALCD|Не применяется|Не применяется|  
|SERVER|ALTER ANY DATABASE|ALDB|Не применяется|Не применяется|  
|SERVER|ALTER ANY ENDPOINT|ALHE|Не применяется|Не применяется|  
|SERVER|ALTER ANY EVENT NOTIFICATION|ALES|Не применяется|Не применяется|  
|SERVER|ALTER ANY EVENT SESSION|AAES|Не применяется|Не применяется|  
|SERVER|ALTER ANY LINKED SERVER|ALLS|Не применяется|Не применяется|  
|SERVER|ALTER ANY LOGIN|ALLG|Не применяется|Не применяется|  
|SERVER|ALTER ANY SERVER AUDIT|ALAA|Не применяется|Не применяется|  
|SERVER|ALTER ANY SERVER ROLE|ALSR|Не применяется|Не применяется|  
|SERVER|ALTER AVAILABILITY GROUP|ALAG|Не применяется|Не применяется|  
|SERVER|ALTER RESOURCES|ALRS|Не применяется|Не применяется|  
|SERVER|ALTER SERVER STATE|ALSS|Не применяется|Не применяется|  
|SERVER|ALTER SETTINGS|ALST|Не применяется|Не применяется|  
|SERVER|ALTER TRACE|ALTR|Не применяется|Не применяется|  
|SERVER|AUTHENTICATE SERVER|AUTH|Не применяется|Не применяется|  
|SERVER|CONNECT ANY DATABASE|CADB|Не применяется|Не применяется|  
|SERVER|CONNECT SQL|COSQ|Не применяется|Не применяется|  
|SERVER|CONTROL SERVER|CL|Не применяется|Не применяется|  
|SERVER|CREATE ANY DATABASE|CRDB|Не применяется|Не применяется|  
|SERVER|CREATE AVAILABILTITY GROUP|CRAC|Неприменимо|Не применяется|  
|SERVER|CREATE DDL EVENT NOTIFICATION|CRDE|Неприменимо|Не применяется|  
|SERVER|CREATE ENDPOINT|CRHE|Неприменимо|Не применяется|  
|SERVER|CREATE SERVER ROLE|CRSR|Неприменимо|Не применяется|  
|SERVER|CREATE TRACE EVENT NOTIFICATION|CRTE|Неприменимо|Не применяется|  
|SERVER|EXTERNAL ACCESS ASSEMBLY|XA|Неприменимо|Не применяется|  
|SERVER|IMPERSONATE ANY LOGIN|IAL|Неприменимо|Не применяется|  
|SERVER|SELECT ALL USER SECURABLES|SUS|Неприменимо|Не применяется|  
|SERVER|SHUTDOWN|SHDN|Неприменимо|Не применяется|  
|SERVER|UNSAFE ASSEMBLY|XU|Неприменимо|Не применяется|  
|SERVER|VIEW ANY DATABASE|VWDB|Неприменимо|Не применяется|  
|SERVER|VIEW ANY DEFINITION|VWAD|Неприменимо|Не применяется|  
|SERVER|VIEW SERVER STATE|VWSS|Неприменимо|Не применяется|  
|SERVER ROLE|ALTER|AL|SERVER|ALTER ANY SERVER ROLE|  
|SERVER ROLE|CONTROL|CL|SERVER|CONTROL SERVER|  
|SERVER ROLE|TAKE OWNERSHIP|В|SERVER|CONTROL SERVER|  
|SERVER ROLE|VIEW DEFINITION|VW|SERVER|VIEW ANY DEFINITION|  
|SERVICE|ALTER|AL|DATABASE|ALTER ANY SERVICE|  
|SERVICE|CONTROL|CL|DATABASE|CONTROL|  
|SERVICE|SEND|SN|DATABASE|CONTROL|  
|SERVICE|TAKE OWNERSHIP|В|DATABASE|CONTROL|  
|SERVICE|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|SYMMETRIC KEY|ALTER|AL|DATABASE|ALTER ANY SYMMETRIC KEY|  
|SYMMETRIC KEY|CONTROL|CL|DATABASE|CONTROL|  
|SYMMETRIC KEY|REFERENCES|RF;|DATABASE|REFERENCES|  
|SYMMETRIC KEY|TAKE OWNERSHIP|В|DATABASE|CONTROL|  
|SYMMETRIC KEY|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|TYPE|CONTROL|CL|SCHEMA|CONTROL|  
|TYPE|EXECUTE|EX|SCHEMA|EXECUTE|  
|TYPE|REFERENCES|RF;|SCHEMA|REFERENCES|  
|TYPE|TAKE OWNERSHIP|В|SCHEMA|CONTROL|  
|TYPE|VIEW DEFINITION|VW|SCHEMA|VIEW DEFINITION|  
|Пользователь|ALTER|AL|DATABASE|ALTER ANY USER|  
|Пользователь|CONTROL|CL|DATABASE|CONTROL|  
|Пользователь|IMPERSONATE|IM|DATABASE|CONTROL|  
|Пользователь|VIEW DEFINITION|VW|DATABASE|VIEW DEFINITION|  
|XML SCHEMA COLLECTION|ALTER|AL|SCHEMA|ALTER|  
|XML SCHEMA COLLECTION|CONTROL|CL|SCHEMA|CONTROL|  
|XML SCHEMA COLLECTION|EXECUTE|EX|SCHEMA|EXECUTE|  
|XML SCHEMA COLLECTION|REFERENCES|RF;|SCHEMA|REFERENCES|  
|XML SCHEMA COLLECTION|TAKE OWNERSHIP|В|SCHEMA|CONTROL|  
|XML SCHEMA COLLECTION|VIEW DEFINITION|VW|SCHEMA|VIEW DEFINITION|  
  
##  <a name="_algorithm"></a>Сводка по алгоритму проверки разрешений  
 Проверка разрешений может оказаться сложной задачей. Алгоритм проверки разрешений учитывает перекрывающееся членство в группах и цепочки владения, явные и неявные разрешения. На его работу могут влиять разрешения на защищаемые классы, содержащие защищаемые сущности. Общая процедура алгоритма состоит в сборе всех применимых разрешений. Если не обнаружена блокирующая инструкция DENY, алгоритм выполняет поиск инструкции GRANT, которая предоставляет достаточные права доступа. Алгоритм содержит три необходимых элемента: **контекст безопасности**, **область разрешения**и **требуемое разрешение**.  
  
> [!NOTE]  
>  Невозможно предоставить, запретить или отменить разрешения sa, dbo, владельцу сущности, information_schema, sys или самому себе.  
  
-   **Контекст безопасности**  
  
     Это группа участников, разрешения которых используются в проверке доступа. Сюда входят разрешения, связанные с текущим именем входа или пользователем, если контекст безопасности не изменился на другое имя входа или другого пользователя с помощью инструкции EXECUTE AS. В контекст безопасности входят следующие участники.  
  
    -   Имя входа.  
  
    -   Пользователь  
  
    -   Членство в ролях.  
  
    -   Членство в группах Windows.  
  
    -   Любое имя входа или учетная запись пользователя для сертификата, используемого для подписания модуля (если применяются подписи модулей), который выполняется пользователем в данный момент, и членство этого участника в соответствующих ролях.  
  
-   **Пространство разрешений**  
  
     Это защищаемая сущность и все защищаемые классы, содержащие защищаемый объект. Например, таблица (защищаемая сущность) содержится в защищаемом классе схемы и в защищаемом классе базы данных. На доступ могут влиять разрешения на уровне таблицы, схемы, базы данных и сервера. Дополнительные сведения см. в разделе [Иерархия разрешений (ядро СУБД)](permissions-hierarchy-database-engine.md).  
  
-   **Требуемое разрешение**  
  
     Тип требуемого разрешения. Например, INSERT, UPDATE, DELETE, SELECT, EXECUTE, ALTER, CONTROL и т. д.  
  
     Для доступа может требоваться несколько разрешений, как в следующих примерах.  
  
    -   Хранимой процедуре может быть необходимо разрешение EXECUTE на хранимую процедуру и разрешение INSERT на несколько таблиц, на которые ссылается хранимая процедура.  
  
    -   Для динамического административного представления могут быть одновременно необходимы разрешения VIEW SERVER STATE и SELECT на представление.  
  
### <a name="general-steps-of-the-algorithm"></a>Общие шаги алгоритма  
 Когда алгоритм определяет, следует ли предоставлять доступ к защищаемому объекту, конкретные используемые шаги могут различаться в зависимости от того, какие участники и защищаемые объекты вовлечены в процесс. Однако в любом случае алгоритм выполняет следующие общие шаги.  
  
1.  Пропустить проверку разрешений, если имя входа является членом предопределенной роли сервера sysadmin или если пользователь является пользователем dbo в текущей базе данных.  
  
2.  Разрешить доступ, если применима цепочка владения и проверка доступа к объекту, расположенному ранее в цепочке, завершилась успешно.  
  
3.  Выполнить статистическую обработку удостоверений на уровне сервера, базы данных и подписанных модулей, относящихся к вызывающей стороне, чтобы создать **контекст безопасности**.  
  
4.  Собрать для полученного **контекста безопасности**все разрешения, которые предоставлены или запрещены в **области разрешения**. Разрешение может задаваться в явном виде в составе инструкций GRANT, GRANT WITH GRANT или DENY (либо быть неявным или покрывающим разрешением GRANT или DENY). Например, из разрешения CONTROL на схему следует разрешение CONTROL на таблицу, а из разрешения CONTROL на таблицу следует разрешение SELECT. Таким образом, если предоставлено разрешение CONTROL на схему, то неявно предоставляется разрешение SELECT на таблицу. Если разрешение CONTROL на таблицу запрещается, то неявно запрещается разрешение SELECT на таблицу.  
  
    > [!NOTE]  
    >  Инструкция GRANT для разрешения на уровне столбцов имеет приоритет над инструкцией DENY на уровне объектов.  
  
5.  Определить **требуемое разрешение**.  
  
6.  Завершить проверку разрешений с отрицательным результатом, если **требуемое разрешение** явно или неявно запрещено в любом из удостоверений из **контекста безопасности** для объектов в **области разрешения**.  
  
7.  Пропустить проверку разрешения, если **обязательное разрешение** было отклонено, при этом **обязательное разрешение** содержит разрешение GRANT или GRANT WITH GRANT, прямое или неявное по отношению к любому из удостоверений в **контексте безопасности** для любого объекта в **области разрешений**.  
  
##  <a name="_examples"></a> Примеры  
 В примерах этого раздела показано, как получить сведения о разрешениях.  
  
### <a name="a-returning-the-complete-list-of-grantable-permissions"></a>A. Получение полного списка разрешений, которые могут быть предоставлены  
 Следующая инструкция возвращает все разрешения компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] с помощью функции `fn_builtin_permissions` . Дополнительные сведения см. в разделе [sys.fn_builtin_permissions (Transact-SQL)](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql).  
  
```  
SELECT * FROM fn_builtin_permissions(default);  
GO  
```  
  
### <a name="b-returning-the-permissions-on-a-particular-class-of-objects"></a>Б. Получение разрешений на определенный класс объектов  
 В следующем примере функция `fn_builtin_permissions` используется для просмотра всех разрешений, доступных для категории защищаемых объектов. В примере возвращаются разрешения на сборки.  
  
```  
SELECT * FROM fn_builtin_permissions('assembly');  
GO    
```  
  
### <a name="c-returning-the-permissions-granted-to-the-executing-principal-on-an-object"></a>В. Получение разрешений, предоставленных исполняющему участнику на объект  
 В следующем примере функция `fn_my_permissions` возвращает список действующих разрешений вызывающего участника в отношении указанного защищаемого объекта. В примере возвращаются разрешения на объект с именем `Orders55`. Дополнительные сведения см. в разделе [sys.fn_my_permissions (Transact-SQL)](/sql/relational-databases/system-functions/sys-fn-my-permissions-transact-sql).  
  
```  
SELECT * FROM fn_my_permissions('Orders55', 'object');  
GO  
```  
  
### <a name="d-returning-the-permissions-applicable-to-a-specified-object"></a>Г. Получение разрешений, применимых к конкретному объекту  
 В следующем примере возвращаются применимые разрешения на объект с именем `Yttrium`. Обратите внимание, что для получения идентификатора объекта `OBJECT_ID` используется встроенная функция `Yttrium`.  
  
```  
SELECT * FROM sys.database_permissions   
    WHERE major_id = OBJECT_ID('Yttrium');  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Иерархия разрешений &#40;ядро СУБД&#41;](permissions-hierarchy-database-engine.md)   
 [sys. database_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql)  
  
  
