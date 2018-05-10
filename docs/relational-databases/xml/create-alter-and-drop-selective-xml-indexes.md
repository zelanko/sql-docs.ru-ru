---
title: Создание, изменение и удаление селективных XML-индексов | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: xml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c398f396-f630-4a2d-a264-f243c5346de1
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c3d819ce2d83df4be1337129b9425dfe0c21498f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="create-alter-and-drop-selective-xml-indexes"></a>Создание, изменение и удаление селективных XML-индексов
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Описывает способы создания нового селективного XML-индекса, изменения или удаления существующего селективного XML-индекса.  
  
 Дополнительные сведения о селективных XML-индексах см. в разделе [Выборочный XML-индекс (SXI)](../../relational-databases/xml/selective-xml-indexes-sxi.md).  
  
##  <a name="create"></a> Создание селективного XML-индекса  
  
### <a name="how-to-create-a-selective-xml-index"></a>Инструкции. Создание селективного XML-индекса  
 **Создание нового селективного XML-индекса с помощью Transact-SQL**  
 Создание селективного XML-индекса путем вызова инструкции CREATE SELECTIVE XML INDEX. Дополнительные сведения см. в разделе [CREATE SELECTIVE XML INDEX (Transact-SQL)](../../t-sql/statements/create-selective-xml-index-transact-sql.md).  
  
 **Пример**  
  
 В следующем примере показан синтаксис для создания селективного XML-индекса. Он также содержит несколько вариантов синтаксиса для описания индексируемых путей с указаниями по оптимизации.  
  
```sql  
CREATE SELECTIVE XML INDEX sxi_index  
ON Tbl(xmlcol)  
  
FOR(  
    pathab   = '/a/b' as XQUERY 'node()'  
    pathabc  = '/a/b/c' as XQUERY 'xs:double',   
    pathdtext = '/a/b/d/text()' as XQUERY 'xs:string' MAXLENGTH(200) SINGLETON  
    pathabe = '/a/b/e' as SQL NVARCHAR(100)  
)  
```  
  
  
##  <a name="alter"></a> Изменение селективного XML-индекса  
  
### <a name="how-to-alter-a-selective-xml-index"></a>Инструкции. Изменение селективного XML-индекса  
 **изменить селективный XML-индекс с помощью Transact-SQL**  
 Измените существующий селективный XML-индекс с помощью инструкции ALTER INDEX. Дополнительные сведения см. в разделе [ALTER INDEX (селективные XML-индексы)](../../t-sql/statements/alter-index-selective-xml-indexes.md).  
  
 **Пример**  
  
 В следующем примере показана инструкция ALTER INDEX. Эта инструкция добавляет путь `'/a/b/m'` в часть XQuery индекса и удаляет путь `'/a/b/e'` из части SQL индекса, созданного в примере в разделе [CREATE SELECTIVE XML INDEX (Transact-SQL)](../../t-sql/statements/create-selective-xml-index-transact-sql.md). Путь для удаления определяется по имени, указанному при его создании.  
  
```sql  
ALTER INDEX sxi_index  
ON Tbl  
FOR   
(  
    ADD pathm = '/a/b/m' as XQUERY 'node()' ,  
    REMOVE pathabe  
)  
```  
  
  
##  <a name="drop"></a> Удаление селективного XML-индекса  
  
### <a name="how-to-drop-a-selective-xml-index"></a>Инструкции. Удаление селективного XML-индекса  
 **Удаление селективного XML-индекса с помощью Transact-SQL**  
 Удалите селективный XML-индекс с помощью инструкции DROP INDEX. Дополнительные сведения см. в разделе [DROP INDEX (селективные XML-индексы)](../../t-sql/statements/drop-index-selective-xml-indexes.md).  
  
 **Пример**  
  
 В следующем примере показана инструкция DROP INDEX.  
  
```sql  
DROP INDEX sxi_index ON tbl  
```  
  
  
  
