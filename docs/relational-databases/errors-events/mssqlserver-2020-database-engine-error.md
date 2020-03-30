---
title: MSSQLSERVER_ 2020 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2020 (Database Engine error)
ms.assetid: 4a8bf90f-a083-4c53-84f0-d23c711c8081
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 112ba12a568190967a31789ca6cd69d2056d9e8c
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "67896761"
---
# <a name="mssqlserver_2020"></a>MSSQLSERVER_2020
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|2020|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя||  
|Текст сообщения|Зависимости для сущности "%.*ls" не содержат ссылок на столбцы. Это происходит либо оттого, что сущности ссылаются на несуществующий объект, либо из-за ошибки в одной или нескольких инструкциях сущности.  Перед повторным выполнением запроса убедитесь, что отсутствуют ошибки в сущности и существуют все объекты, упоминаемые в сущности.|  
  
## <a name="explanation"></a>Объяснение  
Системная функция **sys.dm_sql_referenced_entities** отобразит любую зависимость на уровне столбцов для ссылок, привязанных к схемам. Например, функция отобразит все зависимости на уровне столбцов для индексированного представления, поскольку для индексированного представления необходима привязка к схеме. Однако если упоминаемая сущность, на которую дается ссылка, не привязана к схеме, зависимости столбцов отображаются только в том случае, если можно привязать все инструкции, в которых имеются ссылки на столбцы. Инструкции можно успешно привязать только при наличии всех объектов в момент синтаксического анализа инструкций. Если инструкцию, определенную в сущности, привязать не удается, зависимости столбцов не будут отображаться и столбец **referenced_minor_id** возвратит значение 0. Если не удается разрешить зависимости столбцов, возникает ошибка 2020. Эта ошибка не препятствует возврату запросом зависимостей на уровне объектов.  
  
## <a name="user-action"></a>Действие пользователя  
Устраните ошибки, определенные в сообщении до возникновения ошибки 2020. Например, в следующем примере кода представление `Production.ApprovedDocuments` определяется в столбцах `Title`, `ChangeNumber` и `Status` в таблице `Production.Document`. Объекты и столбцы, от которых зависит представление **, запрашиваются через системную функцию** sys.dm_sql_referenced_entities`ApprovedDocuments`. Поскольку представление не создается при помощи предложения WITH SCHEMA_BINDING, столбцы, на которые имеются ссылки в представлении, можно изменять в ссылочной таблице. В примере изменяется столбец `ChangeNumber` в таблице `Production.Document` путем переименования его в `TrackingNumber`. Представление каталога вновь запрашивается для получения представления `ApprovedDocuments`; однако его нельзя привязать ко всем столбцам, определенным в представлении. Ошибки 207 и 2020 возвращаются с указанием проблемы. Для решения проблемы необходимо изменить представление так, чтобы отразить новое имя столбца.  
  
<pre>USE AdventureWorks2012;  
GO  
CREATE VIEW Production.ApprovedDocuments  
AS  
SELECT Title, ChangeNumber, Status  
FROM Production.Document  
WHERE Status = 2;  
GO  
SELECT referenced_schema_name AS schema_name  
,referenced_entity_name AS table_name  
,referenced_minor_name AS referenced_column  
FROM sys.dm_sql_referenced_entities ('Production.ApprovedDocuments', 'OBJECT');  
GO  
EXEC sp_rename 'Production.Document.ChangeNumber', 'TrackingNumber', 'COLUMN';  
GO  
SELECT referenced_schema_name AS schema_name  
,referenced_entity_name AS table_name  
,referenced_minor_name AS referenced_column  
FROM sys.dm_sql_referenced_entities ('Production.ApprovedDocuments', 'OBJECT');  
GO</pre>  
  
Результатом запроса будут следующие сообщения об ошибках.  
  
<pre>Msg 207, Level 16, State 1, Procedure ApprovedDocuments, Line 3  
Invalid column name 'ChangeNumber'.  
Msg 2020, Level 16, State 1, Line 1  
The dependencies reported for entity  
"Production.ApprovedDocuments" do not include references to  
columns. This is either because the entity references an  
object that does not exist or because of an error in one or  
more statements in the entity. Before rerunning the query,  
ensure that there are no errors in the entity and that all  
objects referenced by the entity exist.</pre>  
  
В следующем примере исправляется имя столбца в представлении.  
  
<pre>USE AdventureWorks2012;  
GO  
ALTER VIEW Production.ApprovedDocuments  
AS  
SELECT Title,TrackingNumber, Status  
FROM Production.Document  
WHERE Status = 2;  
GO</pre>  
  
## <a name="see-also"></a>См. также:  
[Функция динамического управления sys.dm_sql_referenced_entities (Transact-SQL)](~/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md)  
  
